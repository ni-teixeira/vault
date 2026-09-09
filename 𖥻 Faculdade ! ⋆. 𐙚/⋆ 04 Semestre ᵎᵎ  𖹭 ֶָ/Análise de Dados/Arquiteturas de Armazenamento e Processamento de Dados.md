---
date:
tags:
  - faculdade
  - analise-de-dados
  - arquitetura-de-dados
  - oltp-olap-lakehouse
---
# Briefing: Arquiteturas de Armazenamento e Processamento de Dados

## Sumário Executivo

Este documento analisa as principais arquiteturas e metodologias de processamento de dados, fundamentais para a transição de operações transacionais para a tomada de decisão analítica. O ecossistema de dados é estruturado a partir do fluxo onde o **OLTP (Online Transaction Processing)** alimenta os dados, que são então processados em um **Data Warehouse** ou **Data Lake** para, finalmente, serem consumidos via **OLAP (Online Analytical Processing)**.

Enquanto o Data Warehouse foca em dados estruturados, consistência e governança (schema-on-write), o Data Lake oferece flexibilidade e baixo custo para dados brutos e semiestruturados (schema-on-read). A evolução dessas tecnologias culmina no **LakeHouse**, uma arquitetura híbrida que organiza os dados em camadas (Bronze, Prata e Ouro) para unir o desempenho do Warehouse à flexibilidade do Lake.

## 1. Fundamentos de Processamento: OLTP vs. OLAP

A compreensão das arquiteturas de dados exige a distinção clara entre os dois tipos principais de processamento de dados:

### OLTP (Online Transaction Processing)

Focado na operação cotidiana e transacional do negócio.

- **Objetivo:** Suportar transações como inserções, atualizações e exclusões (CRUD).
- **Características:** Alto volume de acessos simultâneos (alta concorrência), operações rápidas e sem falhas.
- **Estrutura:** Utiliza bancos de dados normalizados (como o Relacional) e é otimizado para performance de escrita.
- **Exemplos:** Criação de pedidos, atualização de estoque, processamento de pagamentos e cadastro de clientes.

### OLAP (Online Analytical Processing)

Focado na análise de dados e suporte à tomada de decisão.

- **Objetivo:** Realizar consultas grandes e pesadas para gerar relatórios e dashboards de Business Intelligence (BI).
- **Características:** Menor volume de acessos em comparação ao OLTP, mas as consultas processam grandes volumes de dados e realizam agregações. O tempo de resposta não precisa ser em milissegundos.
- **Estrutura:** Utiliza modelos desnormalizados (como o Star Schema) e é otimizado para performance de leitura.
- **Exemplos:** Cálculo de faturamento mensal, identificação de produtos mais vendidos e análise de comportamento do usuário.

## 2. Data Warehouse: Estrutura e Governança

O Data Warehouse (DW) é um ambiente projetado especificamente para análise de dados em larga escala, focado em responder perguntas complexas de negócio.

- **Abordagem de Dados:** Utiliza o modelo **Schema-on-write**, onde a estrutura é definida antes ou durante o salvamento dos dados.
- **Processo de Carga (ETL):** Os dados são levados ao DW através de processos de Extração, Transformação e Carga.
- **Características Principais:**
    - Dados limpos, transformados e organizados.
    - Modelo dimensional baseado em tabelas de Fato (métricas) e Dimensões (contexto).
    - Alta confiabilidade, consistência e governança.
- **Cenários de Uso:**
    - Dashboards executivos (faturamento, ticket médio).
    - Indicadores de Negócio (KPIs) como CAC (Custo de Aquisição de Cliente), LTV (Lifetime Value) e taxas de conversão.
    - Relatórios oficiais e auditorias financeiras.

## 3. Data Lake: Flexibilidade e Escalabilidade

O Data Lake funciona como um grande depósito de dados em seu estado bruto, permitindo o armazenamento de informações que podem não ser utilizadas imediatamente.

- **Abordagem de Dados:** Utiliza o modelo **Schema-on-read**, salvando os dados primeiro para entender sua estrutura posteriormente.
- **Características Principais:**
    - **Diversidade:** Aceita arquivos CSV, JSON, imagens, logs e dados não estruturados.
    - **Baixo Custo:** Geralmente utiliza tecnologias de armazenamento mais baratas.
    - **Flexibilidade:** Ideal para exploração de dados por cientistas e treinamento de modelos de Machine Learning (LLMs).
- **Cenários de Uso:**
    - **Análise de comportamento:** Cliques, páginas visitadas, tempo no site e eventos de scroll/hover.
    - **Machine Learning:** Sistemas de recomendação baseados em histórico de navegação e compras.
    - **Dados Externos:** Integração com campanhas de Google Ads e dados de redes sociais (Facebook).

## 4. LakeHouse: A Convergência de Arquiteturas

O LakeHouse surge como uma arquitetura que combina o baixo custo e a flexibilidade do Data Lake com o desempenho e a estrutura organizada do Data Warehouse.

### Camadas do LakeHouse (Arquitetura de Medalhão)

Para garantir que os dados brutos se tornem úteis para o negócio, o LakeHouse organiza o fluxo em três camadas principais:

|   |   |   |
|---|---|---|
|Camada|Nome|Descrição|
|**1. RAW**|**Bronze**|Armazena os dados brutos exatamente como chegam da fonte, sem transformações.|
|**2. TRUSTED**|**Prata (Silver)**|Dados limpos, padronizados e validados. É a camada que garante a confiabilidade para análises.|
|**3. REFINED**|**Ouro (Gold)**|Dados agregados e preparados para gerar valor direto ao negócio, alimentando ferramentas de BI.|

### Benefícios Estratégicos

- **Análise Exploratória:** Permite que cientistas de dados testem hipóteses (ex: "usuários que ficam mais de 3 minutos compram mais?") usando os dados originais.
- **Eficiência:** Mantém o histórico completo (dados originais) enquanto fornece uma visão organizada para análises rápidas.
- **Unificação:** Elimina silos de dados ao permitir que uma única arquitetura atenda tanto a necessidades de BI quanto de Ciência de Dados.
