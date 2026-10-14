---
date: 2026-10-13
tags:
  - "#faculdade"
---
# Estratégias de Processamento em IoT: Hot, Warm e Cold Path 
Em um ecossistema de IoT, sensores, gateways e dispositivos de borda (_edge devices_) produzem dados sem parar. No entanto, um alerta de superaquecimento de uma máquina exige reação imediata, enquanto o cálculo da média mensal de consumo de energia pode aguardar horas sem qualquer prejuízo operacional.

Para resolver o dilema entre tempo de resposta e custo de processamento, as arquiteturas de dados dividem o fluxo em três caminhos principais:

- **Hot Path (Caminho Quente):** Focado no processamento quase em tempo real (latência de milissegundos a poucos segundos). É utilizado para detecção de anomalias, alertas críticos e decisões automatizadas imediatas. Exige alta disponibilidade e baixo overhead computacional por evento. Tecnologias comuns incluem **MQTT**, **Apache Kafka**, **Redis** e motores de _stream processing_.

- **Warm Path (Caminho Morno):** Focado no processamento intermediário (latência de segundos a minutos). É ideal para agregações recentes, análise operacional de curto prazo e dashboards de monitoramento contínuo. Equilibra velocidade e custo. Tecnologias comuns incluem **Telegraf**, **InfluxDB**, **TimescaleDB** e **Apache IoTDB**.

- **Cold Path (Caminho Frio):** Focado no armazenamento e processamento histórico de grande volume (latência de minutos a horas ou dias). Seu objetivo é dar suporte a relatórios, ciência de dados, _machine learning_ (como manutenção preditiva) e auditorias. Possui o menor custo de armazenamento por Gigabyte. Tecnologias comuns incluem **Data Lakes**, **Object Storage (S3/Azure Blob)**, arquivos **Parquet**, **Apache Spark** e **DuckDB**.

## **Caso Prático: Telemetria de Antenas Wi-Fi no Campus**
Imagine uma rede de antenas Wi-Fi distribuídas pelos blocos de uma faculdade enviando dados via MQTT. Uma única mensagem enviada pela antena contém status, temperatura, quantidade de clientes conectados e localização (`campus-centro/bloco-a/andar-2/antena/ap-014/telemetria`). Essa mesma mensagem pode alimentar os três caminhos em paralelo:

1. **Hot Path:** Se `status = offline` ou `temperatura &gt; 75°C`, dispara imediatamente um alerta para a equipe de TI.
2. **Warm Path:** A cada 5 minutos, calcula a média de clientes conectados por andar para exibir no dashboard operacional da faculdade.
3. **Cold Path:** Grava o evento bruto em arquivos particionados por data, campus e bloco para análise histórica anual e planejamento de compra de novas antenas.

> **Regra prática de arquitetura:** Quanto menor a latência exigida, maior tende a ser o custo operacional. Trate no _Hot Path_ apenas o que realmente exige resposta imediata!

---
# Arquitetura do Laboratório: A Stack TIG e a Comunicação MQTT
Para implementar o _Warm Path_ e visualizações em tempo quase real com eficiência, uma das combinações mais populares da indústria é a **Stack TIG** (Telegraf, InfluxDB e Grafana), combinada a um broker de mensagens leve como o **Eclipse Mosquitto (MQTT)**.

## **Divisão da Infraestrutura em Máquinas Virtuais**
Em uma topologia típica em nuvem (como na Microsoft Azure ou AWS), separamos as responsabilidades em duas máquinas virtuais (VMs) para garantir isolamento e escalabilidade:

- **VM-1 (Broker):** Uma máquina mais leve (ex: 2 vCPUs, 1 GiB RAM) dedicada exclusivamente a rodar o **Mosquitto MQTT Broker**. Ela atua como ponto central de ingestão de mensagens enviadas pelos sensores ou simuladores na porta `1883`.
- **VM-2 (Worker):** Uma máquina com mais recursos computacionais (ex: 2 vCPUs, 4 GiB RAM) encarregada de rodar a **Stack TIG** e o proxy reverso containerizados via **Docker Compose**.

## **O Papel de Cada Componente no Fluxo de Dados**
1. **Mosquitto (MQTT Broker):** Recebe os dados em formato JSON publicados pelos dispositivos IoT no tópico `sensores/#`.
2. **Telegraf:** Atua como um consumidor do broker MQTT. Ele assina o tópico do Mosquitto, faz a leitura do JSON, transforma e formata as tags (como `dispositivo_id`, `bloco`, `sala`) e os campos (_fields_, como `temperatura` e `umidade`), enviando-os para o banco temporal.
3. **InfluxDB:** Banco de dados de séries temporais (_Time-Series Database_ - TSDB) otimizado para gravação ultrarrápida de métricas com carimbo de data/hora (_timestamp_). Oferece mecanismos nativos de _downsampling_ e retenção automatizada de dados.
4. **Grafana:** Interface gráfica interativa que consulta os dados armazenados no InfluxDB para montar gráficos, medidores e painéis de controle.
5. **Nginx:** Atua como **Proxy Reverso** na VM-2, protegendo e roteando as requisições HTTP externas na porta `80` para os serviços internos do InfluxDB e Grafana.

---
# Implementação Prática e Cuidados de Configuração
A construção dessa infraestrutura exige alguns passos sequenciais de configuração no ecossistema Linux e Docker.

## **1. Configurando o Broker MQTT (VM-1)**
Na primeira máquina virtual, instalamos o serviço do Mosquitto e configuramos o arquivo `/etc/mosquitto/conf.d/default.conf` para permitir conexões remotas ouvindo na porta `1883`:

```
listener 1883 0.0.0.0
allow_anonymous true

```

Após reiniciar o serviço (`sudo systemctl restart mosquitto`), o broker estará pronto para receber mensagens publicadas por simuladores Python ou dispositivos de borda real.

## **2. Configurando o Worker e Docker Compose (VM-2)**
Na segunda máquina, utilizamos o **Docker Compose** para orquestrar quatro containers interconectados em uma rede interna dedicada (`iot-network`):

- **InfluxDB 2.7:** Definindo credenciais iniciais, organização (`Faculdade`), bucket (`sensores`) e um token estático de autenticação para gravação.
- **Telegraf 1.30:** Configurado via `telegraf.conf` com o plugin `inputs.mqtt_consumer` apontando para o IP da VM-1, e o plugin `outputs.influxdb_v2` direcionando a saída para o container do InfluxDB.
- **Grafana (Latest):** Configurado para ler a fonte de dados do InfluxDB.
- **Nginx (Alpine):** Roteando `/` para a API do InfluxDB e `/grafana/` para a interface do Grafana.

## **3. Consultando Dados no Grafana com Flux**
Com a estrutura rodando (`docker compose up -d`), as métricas gravadas no InfluxDB podem ser consultadas no Grafana utilizando a linguagem **Flux**:

```
from(bucket: "sensores")
  |&gt; range(start: -15m)
  |&gt; filter(fn: (r) =&gt; r["_measurement"] == "telemetria_iot")
  |&gt; filter(fn: (r) =&gt; r["_field"] == "temperatura")
  |&gt; filter(fn: (r) =&gt; r["bloco"] == "A")

```

## **Cuidados Essenciais de Implementação**
- **Evite duplicidade sem controle:** Se uma mensagem alimenta os três caminhos (Hot, Warm e Cold), garanta que cada evento possua um identificador único (`mensagem_id` ou `uuid`).
- **Defina políticas de retenção:** Dados quentes e mornos podem ter expiração automática curta (ex: 30 dias no InfluxDB), enquanto dados frios são armazenados indefinidamente no Data Lake.
- **Padronize os timestamps:** Todos os caminhos e conectores devem utilizar a mesma precisão (ex: milissegundos) e o mesmo fuso horário (preferencialmente UTC).
- **Planeje o reprocessamento:** Mantenha os dados brutos gravados de forma imutável no _Cold Path_. Caso uma regra de agregação no _Warm Path_ esteja errada, você poderá reprocessar todo o histórico facilmente.