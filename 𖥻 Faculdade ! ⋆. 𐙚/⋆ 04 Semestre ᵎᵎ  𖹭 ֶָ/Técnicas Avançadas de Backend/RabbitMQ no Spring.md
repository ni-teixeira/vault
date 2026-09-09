---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - mensageria
  - rabbitmq-spring-boot
---
## **1. Visão Geral do RabbitMQ**

O RabbitMQ é um software _open-source_ que atua como **message broker** (intermediador de mensagens), implementando originalmente o protocolo **AMQP** (Advanced Message Queuing Protocol).

- **Tecnologia:** Desenvolvido em Erlang, focado em alta disponibilidade e ambientes distribuídos.
- **Função:** Atua como mediador entre sistemas produtores (_producers_) e consumidores (_consumers_).
- **Benefício:** Permite que a comunicação entre sistemas seja assíncrona e desacoplada, garantindo que a origem não dependa do estado imediato do destino para processar informações.

---

## **2. Preparação do Ambiente e Infraestrutura**

A configuração descrita utiliza tecnologias de ponta para garantir um ambiente de desenvolvimento isolado e replicável.

### **2.1. Pré-Requisitos de Software**

Para a execução do projeto, são necessários:

- **JDK 25** (Java Development Kit).
- **Docker** (Docker Engine para Linux ou Docker Desktop para Windows/macOS).
- **Docker Compose**.

### **2.2. Inicialização do Projeto Spring**

A estrutura recomendada via **Spring Initializr** deve conter:

- **Projeto:** Maven.
- **Linguagem:** Java (versão 25).
- **Versão Spring Boot:** 4.0.3 (conforme metadados da fonte).
- **Dependências Críticas:**
    - _Spring Web_: Para criação de endpoints de teste.
    - _Spring for RabbitMQ_: Driver e abstrações de mensageria.
    - _Docker Compose Support_: Para automação do contêiner.
    - _Lombok_: Opcional, para redução de código boilerplate.

### **2.3. Orquestração com Docker Compose**

O uso da dependência `Docker Compose Support` permite que o Spring execute automaticamente o arquivo `compose.yaml` na raiz do projeto. A configuração padrão do serviço RabbitMQ é:

|Parâmetro|Valor Configurado|
|---|---|
|**Imagem**|rabbitmq:4.2.4-management|
|**Usuário**|myuser|
|**Senha**|secret|
|**Porta RabbitMQ**|5672|
|**Porta Interface (UI)**|15672|

---

## **3. Estratégias de Configuração em Java**

O guia preconiza a centralização de valores no `application.yaml` para facilitar a manutenção e a transição entre ambientes (dev, homolog, prod).

### **3.1. Mapeamento de Propriedades**

Utiliza-se um **Java Record** anotado com `@ConfigurationProperties(prefix = "broker")` para refletir a hierarquia do YAML. Isso transforma as chaves de configuração em objetos tipados dentro da aplicação.

### **3.2. Beans de Configuração (`RabbitTemplateConfiguration`)**

Nesta classe, definem-se os componentes gerenciados pelo Spring:

- **Declarables:** Bean que agrupa a instância da _Exchange_, da _Queue_ e o _Binding_ (vínculo).
- **MessageConverter:** Implementação do `JacksonJsonMessageConverter` para converter automaticamente objetos Java em JSON e vice-versa durante o tráfego na fila.

---

## **4. Implementação de Tipos de Exchange**

O documento detalha três modelos principais de troca de mensagens:

### **4.1. Fanout Exchange**

Neste modelo, a mensagem é enviada para todas as filas vinculadas à exchange, ignorando chaves de roteamento.

- **Configuração:** O _Binding_ é feito diretamente entre a fila e a exchange sem necessidade de uma _routing key_.
- **Consumo:** Realizado através da anotação `@RabbitListener(queues = "${broker.queue.name}")`.

### **4.2. Direct Exchange**

O roteamento baseia-se em uma correspondência exata entre a _routing key_ da mensagem e a chave configurada no _binding_ da fila.

- **Configuração:** Exige a definição de uma `routingKey` tanto no `application.yaml` quanto no bean de _Binding_.
- **Produção:** O `RabbitTemplate` envia a mensagem especificando a `exchangeName` e a `routingKey`.

### **4.3. Topic Exchange**

Permite roteamento seletivo baseado em padrões (curingas).

- **Curingas:** O guia exemplifica o uso do caractere `#` (ex: `example.#`), que permite a correspondência de uma ou mais palavras na chave de roteamento.
- **Diferenciação:** O mapeamento de propriedades deve separar a chave usada para o _binding_ (com curinga) da chave específica usada pelo produtor para enviar a mensagem.

---

## **5. Fluxo de Produção e Teste**

Para validar a integração, o guia sugere um fluxo completo de teste:

1. **Publicação via Interface Gráfica:** Acesso ao `http://localhost:15672` para enviar mensagens manualmente via payload JSON e validar o consumo no console da IDE.
2. **Publicação via Endpoint REST:**

- Criação de um `BrokerController` com um método `POST`.
- Retorno de **Status Code 202 Accepted**, indicando que o processamento assíncrono foi iniciado com sucesso.

3. **Ferramentas de Teste:** Uso de clientes HTTP como o **Insomnia** para disparar requisições para a aplicação Spring, que então encaminha a mensagem ao RabbitMQ.

## **6. Observações Técnicas Importantes**

- **Interface de Gerenciamento:** Ferramenta crucial para monitorar o tráfego, visualizar gráficos de consumo e verificar se os consumidores estão ativos e vinculados corretamente.
- **Confiabilidade:** O uso de filas declaradas como `durable` (duráveis) garante que as mensagens e a estrutura da fila sobrevivam a reinicializações do broker.
- **Conversão de Dados:** É mandatório que o objeto de envio (ex: `MessageDto`) seja um record ou classe compatível com a estrutura JSON enviada/recebida para evitar erros de desserialização.
