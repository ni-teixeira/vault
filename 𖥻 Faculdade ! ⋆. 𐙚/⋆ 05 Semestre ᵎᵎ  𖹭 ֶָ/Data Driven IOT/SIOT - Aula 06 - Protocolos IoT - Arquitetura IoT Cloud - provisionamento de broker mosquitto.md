---
date: 2026-10-13
tags:
  - "#faculdade"
---
# O Que É MQTT e a Arquitetura Publish/Subscribe
A história do MQTT começou em 1999, quando **Andy Stanford-Clark** (da IBM) e **Arlen Nipper** (da Arcom, atual Cirrus Link) precisaram de um protocolo capaz de conectar sensores ao longo de oleodutos via satélite. 
As premissas originais continuam atuais: baixo consumo de energia, uso mínimo de largura de banda, facilidade de implementação e dependência zero da infraestrutura subjacente.

Posteriormente, a especificação foi aberta e padronizada pela **OASIS**, culminando nas versões **MQTT 3.1.1** (2014) e **MQTT 5** (2019).

## **O Panoramas dos Protocolos de Aplicação em IoT**
Para entender o sucesso do MQTT, vale compará-lo a outros protocolos da camada de aplicação:

- **HTTP:** O pilar da Web tradicional. Opera no modelo requisição/resposta (cliente/servidor) sobre TCP. Embora amplamente conhecido, gera alta sobrecarga de cabeçalhos e exige conexões constantes, resultando em alto consumo de energia.
- **CoAP (Constrained Application Protocol):** Projetado para microcontroladores extremamente restritos. Opera sobre UDP (com segurança DTLS), oferecendo requisições/respostas leves e descobertas dinâmicas de dispositivos, porém com cargas úteis (_payloads_) reduzidas.
- **AMQP (Advanced Message Queuing Protocol):** Voltado para cenários empresariais e sistemas financeiros (ex: RabbitMQ). Oferece arquitetura flexível sobre TCP, mas apresenta maior complexidade de configuração e cabeçalhos mais pesados.
- **DDS (Data Distribution Service):** Focado em comunicação P2P (ponto a ponto) de alta performance e tempo real. É muito poderoso, contudo consome mais largura de banda do que o MQTT.
- **MQTT (Message Queue Telemetry Transport):** Baseado em TCP/IP, utiliza um padrão orientado a eventos centrado na figura de um **Broker** intermediário.

## **Os Três Níveis de Desacoplamento no Pub/Sub**
Diferente do modelo tradicional de requisição/resposta, a arquitetura **Publish/Subscribe (Pub/Sub)** do MQTT conecta emissores (Publicadores) e receptores (Assinantes) de forma completamente independente por meio de três dimensões de desacoplamento:

1. **Desacoplamento Espacial:** Publicadores e assinantes não precisam se conhecer. Nenhum dispositivo precisa armazenar o endereço IP ou a porta do outro; todos interagem exclusivamente com o Broker.
2. **Desacoplamento Temporal:** Publicador e assinante não precisam estar ativos ou conectados simultaneamente. O broker pode armazenar mensagens para entregá-las assim que o assinante retornar à rede.
3. **Desacoplamento de Sincronização:** A publicação e o recebimento ocorrem de maneira totalmente assíncrona. O dispositivo publicador envia o dado e continua seu ciclo de processamento sem bloquear o sistema aguardando uma resposta.

## **MQTT vs. Filas de Mensagens Tradicionais**
Apesar do nome conter "Queue", o MQTT **não é uma fila de mensagens tradicional:

- Em uma **fila tradicional**, cada mensagem retida é consumida por apenas **um único** cliente (distribuição de carga entre consumidores). Se nenhum cliente ler, a mensagem permanece travada na fila.
- No **MQTT**, as mensagens são enviadas a **todos** os assinantes registrados naquele tópico específico. Além disso, os tópicos do MQTT são dinâmicos e criados em tempo de execução, sem necessidade de pré-alocação rígida.

---
# Estrutura de Tópicos, Coringas e Boas Práticas
No MQTT, o **Tópico** é uma string UTF-8 usada pelo Broker para filtrar e rotear mensagens para os assinantes certos. Pense em um tópico como um caminho de diretórios hierárquico, onde os níveis são separados por uma barra (`/`).

Por exemplo, em um sistema predial inteligente, um tópico bem estruturado seria: `predioA/andar2/sala18/temperatura`

## **Tipos de Coringas (_Wildcards_)**
Ao criar uma assinatura, os clientes podem usar dois tipos de coringas para receber mensagens de múltiplos tópicos em um único comando. **Atenção:** Coringas só podem ser usados na _assinatura_ (`SUBSCRIBE`), nunca na _publicação_ (`PUBLISH`).

- **Coringa de Nível Único (** **+** **):** Substitui exatamente um nível da hierarquia de tópicos.
    - _Exemplo:_ A assinatura `predioA/+/sala18/temperatura` receberá dados de `predioA/andar1/sala18/temperatura` e `predioA/andar2/sala18/temperatura`, mas não de `predioA/andar2/blocoB/sala18/temperatura`.
- **Coringa Multi-nível (** **#** **):** Substitui múltiplos níveis subsequentes na hierarquia. Ele deve obrigatoriamente ser colocado como o **último caractere** da string, precedido por uma barra.
    - _Exemplo:_ A assinatura `predioA/#` receberá todas as mensagens cujos tópicos iniciem com `predioA/`, independentemente da profundidade do caminho.

## **Tópicos Especiais de Sistema (`$SYS/`)**
Tópicos iniciados com o símbolo `$` são reservados exclusivamente para o broker expor estatísticas internas e métricas de desempenho. Eles são omitidos quando um cliente assina apenas o coringa `#` isolado. 

Alguns exemplos comuns incluem:
- `$SYS/broker/clients/connected`: Quantidade de clientes conectados no momento.
- `$SYS/broker/messages/sent`: Total de mensagens trafegadas pelo broker.
- `$SYS/broker/uptime`: Tempo em que o broker está em execução.

## **Boas Práticas na Criação de Tópicos**
1. **Evite a barra inicial (** **/** **):** Tópicos como `/casa/temperatura` criam um nível nulo desnecessário no início (`""/casa/temperatura`), consumindo bytes adicionais sem utilidade.
2. **Não use espaços nem caracteres não-ASCII:** Espaços dificultam a leitura e a depuração de código.
3. **Mantenha os tópicos concisos, porém específicos:** Cada byte da string do tópico é transmitido no cabeçalho fixo/variável do pacote MQTT. Economize banda em redes restritas.
4. **Incorpore o ID do Dispositivo no tópico:** Facilita a aplicação de regras de segurança e autorização (ex: `dispositivos/sensor-18/telemetria`).
5. **Evite assinar o coringa** **#** **em produção:** Em cenários de alta vazão, assinar tudo no lado do cliente pode sobrecarregar a CPU e a memória do dispositivo. Para salvar dados no banco, prefira plugins ou extensões executadas nativamente no broker.

---
# Qualidade de Serviço (QoS) e Gestão de Sessões
O MQTT oferece garantias flexíveis de entrega através dos seus três níveis de **Qualidade de Serviço (QoS)**, permitindo que cada dispositivo equilibre confiabilidade e consumo de recursos.

## **Os Níveis de Qualidade de Serviço (QoS)**
- **QoS 0 - At Most Once (No máximo uma vez):** Também conhecido como _"dispara e esquece"_ (_fire and forget_). A mensagem é transmitida sem qualquer confirmação de recebimento (ACK). Se houver oscilação de rede, o dado é perdido. É o nível mais rápido e com menor consumo de largura de banda.
- **QoS 1 - At Least Once (Pelo menos uma vez):** Garante que a mensagem chegue ao destino, mas admite duplicatas. O emissor guarda a mensagem até receber um pacote de confirmação `PUBACK`. Caso o tempo limite expire sem o ACK, o emissor reenvia a mensagem com a flag de duplicata habilitada (`DUP = 1`).
- **QoS 2 - Exactly Once (Exatamente uma vez):** É o nível mais seguro e complexo, garantindo que a mensagem chegue exatamente uma única vez, sem perdas nem duplicatas. Para isso, realiza um _handshake_ de 4 vias:
    1. O cliente envia `PUBLISH` (QoS 2).
    2. O broker responde informando que recebeu: `PUBREC` (Publish Received).
    3. O cliente solicita a liberação da mensagem: `PUBREL` (Publish Release).
    4. O broker confirma o encerramento da transação: `PUBCOMP` (Publish Complete).

## **O Fenômeno do Rebaixamento de QoS (_QoS Downgrade_)**
O nível de QoS é estabelecido de forma independente em dois trechos: entre o publicador e o broker, e entre o broker e o assinante. 
Se um sensor publica com QoS 2, mas um aplicativo assina o tópico declarando QoS 1, o broker rebaixará a entrega final para QoS 1.

## **Sessões Persistentes vs. Clean Sessions**
No pacote inicial de conexão (`CONNECT`), o cliente envia parâmetros críticos:

- **ClientId:** Identificador único da máquina ou microcontrolador.
- **CleanSession (ou CleanStart no MQTT 5):**
    - Se configurado como `true`, a conexão será não-persistente. Ao desconectar, todos os estados e assinaturas são destruídos.
    - Se configurado como `false`, o broker estabelece uma **Sessão Persistente**. O broker mantém armazenados o cadastro de assinaturas, as mensagens de QoS 1 e 2 pendentes de confirmação e todas as mensagens que o cliente perdeu enquanto esteve offline.
- **Last Will and Testament (LWT):** Mensagem de "testamento" configurada pelo cliente no momento da conexão. Caso o dispositivo sofra uma queda abrupta (perda de energia ou queda de sinal sem envio do pacote `DISCONNECT`), o broker publica automaticamente essa mensagem em seu nome para alertar o sistema.
- **Keep Alive:** Intervalo máximo (em segundos) que o cliente pode ficar em silêncio. Caso não haja tráfego de dados, o cliente envia um pacote `PINGREQ` e aguarda o `PINGRESP` do broker para manter o canal ativo.

---
# Laboratório Prático: Mosquitto, Simulações e Análise com tcpdump
Para consolidar o conhecimento, vamos acompanhar a implantação de um ambiente real de comunicação IoT utilizando o broker **Eclipse Mosquitto**, scripts em **Python** e a ferramenta de captura de pacotes **tcpdump**.

## **1. Configuração do Broker Mosquitto no Linux/Azure**
No servidor Linux (por exemplo, em uma Máquina Virtual na nuvem Azure), inicia-se o serviço do broker e habilita-se sua execução automática:

```
sudo apt update
sudo apt install -y mosquitto
sudo systemctl start mosquitto
sudo systemctl enable mosquitto
sudo systemctl status mosquitto --no-pager

```

Para permitir conexões externas e testes no laboratório, edita-se o arquivo de configuração `/etc/mosquitto/conf.d/default.conf` adicionando as seguintes diretivas:

```
listener 1883 0.0.0.0
allow_anonymous true

```

## **2. Simulação de Sensores com Python (paho-mqtt)**
Através de um script Python (`simulador_temp.py`), conecta-se ao broker publicando leituras simuladas de temperatura formatadas em JSON:

```
import json
import random
import time
import paho.mqtt.client as mqtt

BROKER = "172.209.209.40"
PORT = 1883
TOPIC = "iot/lab/temperatura"
QOS = 1

client = mqtt.Client(mqtt.CallbackAPIVersion.VERSION2)
client.connect(BROKER, PORT, keepalive=60)
client.loop_start()

try:
    while True:
        payload = {
            "sensor": "sala-01
```