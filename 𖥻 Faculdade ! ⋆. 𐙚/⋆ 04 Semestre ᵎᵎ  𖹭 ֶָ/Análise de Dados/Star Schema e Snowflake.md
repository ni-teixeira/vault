---
date:
tags:
  - faculdade
  - analise-de-dados
  - arquitetura-de-dados
  - star-schema-e-snowflake
---
# Modelagem de Dados para Analytics: Star Schema e Snowflake

Este documento apresenta uma análise técnica detalhada das arquiteturas de modelagem de dados voltadas para ambientes analíticos (OLAP), contrastando as abordagens de **Star Schema** e **Snowflake**, além de detalhar os componentes fundamentais das tabelas de Fato e Dimensão.

## Sumário Executivo

A transição de sistemas transacionais (OLTP) para ambientes analíticos (OLAP) exige uma mudança de paradigma na modelagem de dados. Enquanto o OLTP foca na integridade e normalização para suportar múltiplas operações, o OLAP prioriza a eficiência na leitura e análise de grandes volumes de dados. Os principais modelos identificados são:

- **Star Schema:** O modelo mais comum, caracterizado pela desnormalização. Foca na alta performance e simplicidade de consultas, sendo ideal para conceitos de LakeHouse e dashboards de alto desempenho.
- **Modelo Snowflake:** Uma variação que aplica a normalização às tabelas de dimensão. Prioriza a economia de espaço e a redução da redundância, ao custo de maior complexidade e lentidão nas consultas devido ao aumento de operações de _JOIN_.
- **Fluxo de Dados:** O processo de ETL (Extração, Transformação e Carga) atua como a ponte necessária para converter dados brutos relacionais em informações prontas, removendo regras de negócio complexas das consultas finais.

## Comparativo de Modelagens OLAP

A escolha entre Star Schema e Snowflake depende das prioridades do ambiente analítico (espaço em disco versus velocidade de resposta).

|   |   |   |
|---|---|---|
|Característica|Modelo Star Schema|Modelo Snowflake|
|**Estrutura**|Tabela Fato centralizada com Dimensões ao redor.|Dimensões divididas em sub-tabelas (sub-dimensões).|
|**Normalização**|Desnormalizado (permite redundância).|Normalizado (evita repetição de dados).|
|**Performance**|Alta velocidade; consultas mais rápidas.|Mais lento; exige múltiplos _JOINs_.|
|**Complexidade**|Simplicidade técnica nas _queries_.|Maior complexidade estrutural.|
|**Uso Principal**|LakeHouse; Dashboards performáticos.|Ambientes de análise de grande escala com restrição de espaço.|

## Análise do Modelo Star Schema

O Star Schema é a arquitetura predominante para ambientes OLAP devido ao seu foco incisivo em performance. Sua estrutura assemelha-se a uma estrela, onde a Tabela Fato ocupa o centro.

### Implicações e Vantagens

- **Alta Velocidade:** A redundância de dados permitida pela desnormalização é um compromisso assumido para garantir que as consultas de leitura sejam rápidas.
- **Simplicidade Técnica:** As _queries_ são mais fáceis de escrever e compreender, reduzindo a curva de aprendizado para analistas.
- **Informação Pronta:** O usuário final acessa dados já preparados, o que minimiza erros de interpretação e elimina a necessidade de cálculos pesados no momento da consulta.
- **Otimização de Processos:** Por ter as regras de negócio tratadas previamente no processo de ETL, o modelo elimina a complexidade do código SQL no nível de aplicação.

## Análise do Modelo Snowflake

O modelo Snowflake é uma evolução ou variação do OLAP, projetado especificamente para cenários onde a economia de armazenamento é crítica ou o volume de dados em dimensões é massivo.

### Características Estruturais

- **Normalização de Dimensões:** A principal característica é a decomposição das tabelas de dimensão em sub-tabelas menores.
- **Estrutura de Floco de Neve:** A ramificação das dimensões em sub-dimensões cria um visual que remete a um floco de neve.

### Trade-offs (Compromissos)

- **Eficiência de Espaço:** Reduz significativamente a redundância de dados.
- **Custo de Processamento:** Torna as consultas inerentemente mais lentas, pois o sistema precisa realizar mais conexões (_JOINs_) entre diversas tabelas para entregar o resultado final.

## Componentes do Modelo: Fato vs. Dimensão

Independentemente do modelo escolhido, a estrutura baseia-se na distinção clara entre dados quantitativos e descritivos.

### Tabela Fato

Localizada no centro do modelo, é o repositório dos dados quantitativos e métricas.

- **Conteúdo:** Contém valores numéricos (ex: valor de vendas, quantidade, descontos).
- **Volume:** É a maior tabela do esquema, com crescimento contínuo e acelerado.
- **Relacionamentos:** Possui chaves estrangeiras (FKs) que conectam cada registro às suas respectivas dimensões.

### Tabela Dimensão

Tabelas menores e mais estáveis que orbitam a Tabela Fato, fornecendo o contexto necessário para a análise.

- **Conteúdo:** Informações descritivas, categóricas ou textuais.
- **Função:** Utilizadas para filtrar, agrupar e detalhar os dados da Tabela Fato.
- **Exemplos de Contexto:** Dados de tempo (dia, mês, ano), localização (cidade, região), empresa ou tipo de problema/produto.

## Fluxo de Transformação de Dados

O documento destaca a ineficiência de realizar análises diretamente em bancos OLTP (transacionais).

1. **Problemas no OLTP:** Consultas lentas, excesso de regras de negócio complexas nos comandos `SELECT`, dificuldade de escrita e manutenção, além de alto impacto em grandes volumes.
2. **Processo ETL:**
    - **Extração:** Coleta dados do banco relacional (OLTP).
    - **Transformação:** Limpeza e aplicação de regras de negócio.
    - **Carga:** Envio para o banco analítico (OLAP).
3. **Resultado Final:** A criação de um ambiente OLAP (como um LakeHouse) permite a geração de dashboards "Super Performáticos", onde a informação já está pronta para o consumo estratégico.