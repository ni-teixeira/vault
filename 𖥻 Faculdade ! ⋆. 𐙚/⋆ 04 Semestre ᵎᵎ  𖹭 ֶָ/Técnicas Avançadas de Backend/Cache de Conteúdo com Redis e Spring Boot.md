---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - cache
  - redis-e-spring-boot
---
# 1. Conceitos Fundamentais e Estratégias de Armazenamento

O cache atua como uma camada intermediária que evita consultas repetitivas a bancos de dados ou cálculos complexos.

### Vantagens Principais

- **Desempenho:** Respostas aceleradas para o usuário final.
- **Redução de Carga:** Menos estresse nos bancos de dados relacionais.
- **Escalabilidade:** Capacidade de suportar um volume maior de usuários simultâneos.
- **Eficiência:** Reaproveitamento de processamentos já realizados.

### Estratégias de Cache

|   |   |   |
|---|---|---|
|Estratégia|Descrição|Caso de Uso|
|**Read-Through**|O cache busca no banco se o dado não existir e o salva.|Leitura de dados raramente alterados.|
|**Cache-Aside**|A aplicação gerencia a gravação/remoção (Padrão Spring).|Flexibilidade total para a aplicação.|
|**Write-Through**|Escrita simultânea no cache e no banco.|Consistência imediata de dados.|
|**Write-Behind**|Grava no cache primeiro e persiste no banco depois.|Alta performance; risco de inconsistência.|

## 2. Preparação do Ambiente e Infraestrutura

A implementação requer um ambiente padronizado para garantir a consistência entre desenvolvimento e produção.

### Pré-requisitos Técnicos

- **Java 21+** e **Maven/Gradle**.
- **Docker 24.x+** para orquestração do Redis e RedisInsight.
- **Dependências Spring Boot:** `spring-boot-starter-cache`, `spring-boot-starter-data-redis` e `spring-boot-starter-data-jpa`.

### Configuração via Docker Compose

O uso do Docker Compose facilita a criação de um ambiente isolado com limites de recursos definidos. Uma configuração recomendada inclui:

- **Imagem:** `redis:7-alpine`.
- **Limite de Memória:** Configurado para 512MB.
- **Política de Substituição:** `allkeys-lfu` (mantém os itens mais acessados).
- **Ferramenta Visual:** RedisInsight acessível via porta 5540 para inspeção de dados em tempo real.

## 3. Implementação Técnica no Spring Boot

A integração é realizada através de configurações declarativas e anotações que abstraem a complexidade do gerenciamento de chaves.

### Configuração da Aplicação (`application.yml`)

As propriedades principais definem o comportamento global do cache:

- `spring.cache.type: redis`: Define o provedor.
- `spring.cache.redis.time-to-live`: Define o TTL padrão (ex: `PT5M` para 5 minutos).
- `spring.cache.redis.cache-null-values`: Recomendado como `false` para economizar memória.

### Anotações de Cache (Camada Service)

O Spring utiliza anotações para interceptar chamadas de métodos:

- `**@Cacheable**`**:** Consulta o cache antes de executar o método. Se houver um _hit_, retorna o dado; se houver um _miss_, executa o método e armazena o resultado.
- `**@CachePut**`**:** Atualiza o conteúdo no cache, garantindo que a próxima leitura obtenha o dado mais recente.
- `**@CacheEvict**`**:** Remove entradas do cache (geralmente usada em operações de exclusão).

### Personalização com `RedisCacheManager`

Permite definir comportamentos específicos por nome de cache, como serialização em JSON (usando `GenericJacksonJsonRedisSerializer`) e TTLs distintos para diferentes entidades (ex: 10 minutos para produtos, 30 segundos para listas).

## 4. Gerenciamento de Chaves e SpEL

O uso de **Spring Expression Language (SpEL)** é fundamental para criar chaves únicas e evitar colisões.

- `**#id**`**:** Usa o parâmetro do método como chave.
- `**#root.methodName**`**:** Inclui o nome do método na chave.
- `**#root.targetClass.simpleName**`**:** Adiciona o nome da classe para maior precisão.
- **Chaves Combinadas:** Exemplo: `T(java.util.Objects).hash(#id, #nome)`.

## 5. Monitoramento e Boas Práticas

A manutenção de um sistema de cache performático exige vigilância sobre métricas de uso e comportamento da memória.

### Políticas de Expiração e Substituição (_Eviction_)

|   |   |
|---|---|
|Política|Funcionamento|
|**TTL (Time To Live)**|Expira após tempo fixo.|
|**LRU (Least Recently Used)**|Remove o menos acessado recentemente.|
|**LFU (Least Frequently Used)**|Remove o menos acessado com frequência.|
|**No Eviction**|Retorna erro se a memória lotar (para dados críticos).|

### Diretrizes de Qualidade

1. **Saúde do Cache:** Uma taxa de _hits_ acima de **80%** é considerada saudável.
2. **Volatilidade:** Dados que mudam muito devem ter TTLs curtos.
3. **Dados Nulos:** Evite armazená-los para não desperdiçar memória.
4. **Granularidade:** Evite cachear listas massivas; prefira resultados parciais ou paginados.
5. **Segurança:** Sempre utilize senhas para o Redis em ambientes produtivos.
6. **Inspeção:** Utilize o painel **Analytics** do RedisInsight para monitorar _evictions_ e consumo de memória.
