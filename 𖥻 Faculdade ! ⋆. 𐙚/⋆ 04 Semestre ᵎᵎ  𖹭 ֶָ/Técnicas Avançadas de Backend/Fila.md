---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - mensageria
  - comunicacao-assincrona
---
## **1. A Evolução da Estrutura de Sistemas**

### **Do Monólito ao Labirinto**

O modelo tradicional de monólito centraliza interface de usuário (UI), regras de negócio e banco de dados em um único processo.

- **Vantagens:** Comunicação interna simples, direta e de baixo custo, pois funções chamam funções sem a necessidade de rede entre módulos.
- **Limitações:** Alta dependência; qualquer alteração exige a modificação e o deploy do sistema como um todo.

### **A Mudança para Microsserviços**

A arquitetura de microsserviços fragmenta o sistema em componentes independentes para ganhar escalabilidade e autonomia. Entretanto, isso gera um "labirinto" de comunicação onde cada serviço precisa interagir via rede, aumentando a complexidade operacional.

---

## **2. Comunicação Síncrona vs. Assíncrona**

A documentação enfatiza que "nem tudo deve esperar", contrastando dois modelos de interação entre APIs:

|Característica|Chamadas Síncronas (Sync)|Chamadas Assíncronas (Async)|
|---|---|---|
|**Mecanismo**|Chamadas diretas em cadeia (API 1 -> API 2).|Uso de um **Mediador** (Fila/Broker).|
|**Performance**|Tempo de resposta aumenta cumulativamente.|Melhora a escalabilidade; lida bem com picos de tráfego.|
|**Resiliência**|Frágil; se um serviço cai, a cadeia inteira quebra.|Resiliente; o mediador isola falhas pontuais.|

---

## **3. O Teorema CAP e a Tomada de Decisão**

Em sistemas distribuídos, é impossível garantir simultaneamente **Consistência (C)**, **Disponibilidade (A)** e **Tolerância a Partições (P)**. Diante de falhas, o arquiteto deve priorizar um dos pilares:

- **Consistência (C):** Prioritária quando erros de dados são inaceitáveis, como em sistemas financeiros ou controle crítico de estoque.
- **Disponibilidade (A):** Prioritária quando a experiência contínua do usuário é fundamental, como em redes sociais, streaming ou e-commerce de grande escala.

---

## **4. O Ecossistema RabbitMQ**

O RabbitMQ é apresentado como um _Message Broker_ de código aberto e padrão de mercado, desenvolvido em Erlang, que facilita o desacoplamento entre serviços.

### **Conceitos Chave do "Coelho"**

- **Producer / Consumer:** Quem publica e quem processa as mensagens, respectivamente.
- **Connection / Channel:** Uma conexão TCP que pode suportar múltiplos canais por aplicação.
- **Exchange (Roteador):** Recebe as publicações e decide o destino com base em regras.
- **Queue (Fila):** O local onde a mensagem aguarda o processamento. Possui atributos como _durable_ (persistência), _TTL_ (tempo de vida) e _max-length_.
- **Routing Key & Binding:** A etiqueta da mensagem e a regra que vincula a Exchange à Queue.
- **ACK / NACK / Requeue:** Mecanismos para confirmar, rejeitar ou reentregar mensagens para processamento.
- **DLX / DLQ (Dead Letter Exchange/Queue):** Estrutura para lidar com mensagens mortas (erros ou expiração).

### **Comparação Técnica: RabbitMQ vs. Kafka**

Enquanto o RabbitMQ foca em mensageria e roteamento flexível, o **Kafka** é projetado para gravar mensagens em logs distribuídos, ideal para grandes volumes de dados contínuos como métricas, telemetria (IoT) e _clickstream_.

---

## **5. Mecanismos de Roteamento (Exchanges)**

A forma como as mensagens são distribuídas depende do tipo de Exchange utilizado:

1. **Fanout:** Realiza um _broadcast_. Toda mensagem recebida é enviada para todas as filas conectadas, ignorando a _routing key_. Ideal para notificações simultâneas (ex: faturamento e estoque).
2. **Direct:** Roteamento específico e direto. A mensagem só vai para a fila cuja _binding key_ coincida exatamente com a _routing key_.
3. **Topic:** Roteamento flexível baseado em padrões. Utiliza curingas:

- `*` (asterisco): Substitui exatamente um termo.
- `#` (cerquilha): Substitui um ou mais termos.

---

## **6. Diretrizes para Implementação Prática**

A transição para esta arquitetura requer uma simulação controlada e a entrega de componentes funcionais:

- **Ambiente:** Recomenda-se o uso de Docker ou do simulador online disponível em `tryrabbitmq.com`.
- **Componentes do Entregável:**
    - **1 Producer:** Uma API existente convertida para publicar mensagens.
    - **1 Consumer:** Um microsserviço dedicado a processar as mensagens da fila.
    - **Infraestrutura:** Broker RabbitMQ provisionado e configurado (preferencialmente em nuvem).
- **Fluxo:** As aplicações devem estar conectadas pelo Broker, permitindo comunicação unidirecional (com possibilidade de expansão para bidirecional) e a integração de novos produtores (como AWS Lambda).
