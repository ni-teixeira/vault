---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - arquitetura-de-software
  - arquitetura-orientada-a-eventos
---
## **1. Evolução das Arquiteturas de Software**

A escolha da arquitetura impacta diretamente a manutenção, o custo e a capacidade de expansão do sistema.

### **1.1. Arquitetura Monolítica ("Conversa Sozinho")**

- **Estrutura:** UI, regras de negócio e bancos de dados operam no mesmo processo.
- **Vantagens:** Comunicação interna simples (funções chamam funções); baixo custo de manutenção por não haver rede entre módulos.
- **Limitações:** Alta dependência; qualquer alteração exige a modificação de todo o sistema.

### **1.2. Microserviços ("Falam Demais")**

- **Estrutura:** Cada serviço é independente, possui sua própria lógica e banco de dados.
- **Vantagens:** Escalabilidade, autonomia para evoluir e usar tecnologias diferentes sem impacto colateral.
- **Desafios:** Toda comunicação ocorre via rede, gerando latências, falhas e a necessidade de padronização.
- **Fragilidade Síncrona:** Chamadas em cadeia (ex: API 01 depende da API 02) aumentam o tempo de resposta; se um serviço cai, toda a cadeia quebra.

---

## **2. O Teorema de CAP em Sistemas Distribuídos**

Em sistemas distribuídos, é impossível garantir simultaneamente os três pilares abaixo; deve-se priorizar dois dependendo do contexto do negócio:

|Pilar|Descrição|Contexto de Uso|
|---|---|---|
|**Consistência (C)**|Garantia de que erros de dados são inaceitáveis.|Financeiro, estoque crítico.|
|**Disponibilidade (A)**|Foco na experiência contínua do usuário sobre a consistência imediata.|Redes sociais, streaming, e-commerce.|
|**Tolerância a Partições (P)**|Capacidade de operar apesar de falhas de comunicação entre nós.|Essencial em qualquer sistema de rede.|

---

## **3. Fundamentos da Arquitetura Orientada a Eventos (EDA)**

Eventos representam fatos que já ocorreram e podem disparar efeitos colaterais (ex: "Pedido Aprovado" dispara uma notificação).

- **Tipos de Eventos:** Podem ser internos (dentro de um domínio/monólito) ou externos (publicados para outros serviços).
- **Domain Events (DDD):** Mudanças significativas no estado de um agregado (ex: `PedidoCriado`).
- **Quando utilizar:** Em sistemas distribuídos grandes que demandam alta flexibilidade e escalabilidade, tolerando consistência eventual.
- **Quando evitar:** Processos críticos que exigem consistência imediata, transações complexas ou latência mínima.

---

## **4. Modelagem e Padrões de Eventos**

Existem diferentes formas de estruturar como a informação trafega entre os serviços:

### **4.1. Formas de Modelagem**

- **Event Notification:** O evento apenas avisa que algo mudou. É leve e barato, mas obriga o receptor a buscar dados extras.
- **Event Carried State Transfer:** O evento carrega o estado completo (ex: dados do pedido e do comprador). Evita consultas extras, mas é mais pesado.
- **Event Sourcing:** O estado da aplicação é reconstruído pela sequência de eventos. Útil para auditoria e histórico financeiro, pois o banco armazena todo o histórico e não apenas o último estado.

### **4.2. CQRS (Command Query Responsibility Segregation)**

Este padrão separa as responsabilidades de escrita e leitura:

- **Write Model:** Aplica regras de negócio e emite Domain Events.
- **Read Model:** Projeções materializadas para consultas rápidas, podendo usar tecnologias diferentes (SQL, NoSQL, Cache).
- **Dinâmica:** Eventos trafegam via broker e atualizam múltiplas visões em paralelo, aceitando a **consistência eventual** (atraso de milissegundos na leitura).

---

## **5. Message Brokers: Infraestrutura de Mensageria**

Brokers funcionam como mediadores que recebem, armazenam e entregam mensagens, permitindo que produtores e consumidores atuem de forma independente.

### **5.1. RabbitMQ vs. Kafka**

- **RabbitMQ:** Broker padrão de mercado (open source), implementa protocolos como AMQP e MQTT. É focado em desacoplamento rápido e poderoso.
- **Kafka:** Projetado para grandes volumes de dados contínuos (logs, métricas, IoT). As mensagens são gravadas em log distribuído e podem ser consumidas em tempo real.

### **5.2. Conceitos-Chave de Operação**

- **Amortecimento:** Filas fazem buffer/backpressure para nivelar picos de tráfego.
- **Confiabilidade:** Garantida por persistência de mensagens, ACKs (sucesso) e NACKs (erro/reentrega).
- **DLQ (Dead Letter Queue):** Fila para gerenciar "mensagens mortas" (erros, expiração de TTL).
- **Prefetch (QoS):** Controla quantas mensagens cada consumidor recebe por vez para evitar sobrecarga.

---

## **6. Componentes e Terminologia Técnica**

Para a implementação prática de mensageria (especialmente RabbitMQ), os seguintes termos são fundamentais:

- **Producer:** Cria e publica mensagens em uma **Exchange** usando uma **Routing Key**.
- **Consumer:** "Escuta" a fila e processa os dados. Deve ser **idempotente** (processar a mesma mensagem duas vezes não deve causar erro).
- **Exchange (Roteador):** Decide o destino da mensagem com base em regras:
    - **Direct:** Correspondência exata da Routing Key.
    - **Fanout:** Envia para todas as filas ligadas (broadcast), ignorando a chave.
    - **Topic:** Roteamento por padrões (curingas: `*` substitui um termo; `#` substitui vários).
    - **Headers:** Baseado nos atributos do cabeçalho.
- **Queue (Fila):** Armazenamento temporário. Atributos incluem `Durable` (sobrevive ao reinício), `TTL` (tempo de vida) e `Max-length`.
- **Binding:** Regra que conecta uma Exchange a uma Queue. Sem binding, a mensagem não chega ao destino.
- **Connection / Channel:** Uma conexão TCP pode suportar múltiplos canais (threads) para otimizar o tráfego.
