---
date:
tags:
  - faculdade
  - analise-de-dados
  - qualidade-de-dados
  - limpeza-e-enriquecimento
---
# Briefing: Limpeza, Padronização e Enriquecimento de Dados

## Sumário Executivo

A qualidade dos dados é o alicerce de qualquer iniciativa de análise ou Machine Learning bem-sucedida. O princípio "lixo entra, lixo sai" reflete a realidade de que modelos e decisões baseados em dados sujos resultam em previsões falhas e estratégias empresariais equivocadas. Este documento detalha os processos essenciais de limpeza, padronização e enriquecimento de dados, fundamentais para garantir a integridade, a conformidade e o valor estratégico das informações. A abordagem apresentada abrange desde o tratamento de valores ausentes e duplicados até técnicas avançadas de normalização e o uso de fontes externas para ampliar o contexto dos dados.

## 1. O Impacto da Baixa Qualidade dos Dados

Dados inconsistentes ou "sujos" geram uma cadeia de consequências negativas para as organizações:

- **Modelos de Machine Learning Imprecisos:** O aprendizado de padrões incorretos leva a previsões não confiáveis.
- **Decisões de Negócios Equivocadas:** Estratégias e investimentos podem ser desastrosos se baseados em análises errôneas.
- **Dificuldades Operacionais:** Inconsistências impedem a unificação de informações de diferentes fontes e consomem tempo valioso de equipes técnicas na depuração de problemas.
- **Riscos de Segurança e Conformidade:** Dados sensíveis podem ser expostos ou violar regulamentações vigentes.

## 2. Estratégias de Limpeza de Dados

O processo de limpeza visa identificar e corrigir erros para tornar os dados utilizáveis.

### Tratamento de Valores Ausentes (Missing Values)

Existem diversas abordagens para lidar com lacunas nos dados:

- **Valor Constante:** Preenchimento com valores fixos (ex: 0 ou "Desconhecido").
- **Remoção:** Eliminação de linhas ou colunas com dados faltantes.
- **Medidas Estatísticas:**
    - **Média:** Indicada para dados numéricos, porém sensível a _outliers_.
    - **Mediana:** Mais robusta contra valores extremos.
    - **Moda:** Utilizada para preencher dados categóricos com o valor mais frequente.
- **Interpolação:** Preenchimento baseado em valores adjacentes (ex: lógica linear).
- **Modelos Preditivos:** Treinamento de modelos (como Regressão Linear) para prever os valores faltantes com base em outras variáveis.

### Tratamento de Dados Duplicados

A identificação de linhas idênticas ou semanticamente semelhantes é crucial:

- **Métodos de Identificação:** Uso de funções como `df.duplicated().sum()` (Pandas) e comparação de subconjuntos de colunas identificadoras (ID, CPF, número do pedido).
- **Remoção:** Exclusão de duplicatas mantendo critérios específicos (primeira ou última ocorrência).
- **Exclusão Lógica:** Identificação de registros cancelados ou marcados para remoção.

## 3. Padronização de Dados (Standardization)

A padronização transforma entradas ambíguas em formatos uniformes baseados em regras definidas, facilitando a integração de fontes distintas.

### Datas e Horas

- **Problema:** Formatos variados (01/02/2023, 1º de fevereiro) e ambiguidades dia/mês.
- **Solução:** Adoção do padrão **ISO 8601 (YYYY-MM-DD)** e conversão de todos os campos para este formato, eliminando sufixos textuais.

### Categorias e Domínios

- **Padronização Semântica:** Mapear variações (ex: "M", "Masculino", "masc") para um padrão único definido em um dicionário de categorias válidas.
- **Label Encoding / Ordinal Encoding:** Atribuição de números inteiros a categorias (ex: Pequeno=0, Médio=1, Grande=2).
- **Discretização:** Transformação de variáveis numéricas contínuas em faixas categóricas (ex: Idade para Faixas Etárias).

### Espaços e Caracteres Especiais

- **Limpeza de Strings:** Remoção de espaços em branco (iniciais, finais, duplos ou invisíveis como TAB e ESC).
- **Tratamento de Acentos:** Uso de mapas de substituição ou normalização Unicode (NFD) para remover acentuações (ex: "João" → "Joao").

## 4. Técnicas Avançadas de Comparação e Normalização

Para lidar com variações complexas em nomes e textos, utilizam-se métodos matemáticos e fonéticos:

|   |   |
|---|---|
|Técnica|Descrição|
|**Fuzzy Matching**|Calcula a similaridade entre strings em uma escala de 0 a 100.|
|**Distância de Levenshtein**|Mede o número mínimo de edições necessárias para transformar uma string em outra.|
|**Jaro-Winkler**|Métrica de similaridade focada em variações de escrita.|
|**Expansão de Iniciais**|Mapeamento de abreviações para nomes completos (ex: "V" para "Vicente").|
|**Fonética**|Compara termos com base na similaridade de som.|

## 5. Fluxo de Trabalho de Qualidade de Dados

O processo deve seguir uma sequência lógica para garantir a eficácia:

1. **Entendimento dos Dados:** Exploração e identificação de tipos e colunas.
2. **Identificação de Problemas:** Detecção de ausentes, duplicatas e _outliers_.
3. **Tratamento de Dados:** Execução da limpeza (ausentes, duplicatas, _outliers_).
4. **Correção e Padronização:** Ajuste de inconsistências, erros de digitação e formatos.
5. **Codificação:** Transformação de variáveis categóricas em formatos numéricos.
6. **Validação:** Verificação final para garantir que nenhum erro novo foi introduzido.

## 6. Enriquecimento de Dados

O enriquecimento vai além da limpeza, adicionando novas dimensões e contexto aos registros existentes para tornar as análises mais profundas e precisas.

### Benefícios do Enriquecimento

- **Segmentação e Personalização:** Melhor compreensão do contexto do cliente para ofertas relevantes.
- **Detecção de Fraudes:** Identificação de atividades suspeitas através de dados adicionais.
- **Insights Profundos:** Novas variáveis permitem explorar padrões ocultos e melhorar modelos preditivos.

### Fontes de Dados para Enriquecimento

- **Internas:** Sistemas de CRM, ERP e histórico de interações ou fidelidade.
- **Externas Públicas:** Dados do IBGE, governamentais e meteorológicos.
- **Externas Comerciais:** APIs de terceiros que fornecem dados demográficos, socioeconômicos e de risco.

## 7. Ecossistema de Ferramentas e APIs

Diversas ferramentas facilitam a validação e o enriquecimento de dados:

- **Dados Pessoais e de Contato:** Clearbit, FullContact, People Data Labs e Serasa Experian (validação de CPF/CNPJ).
- **Geolocalização:** Google Maps Geocoding, ViaCEP e IBGE APIs.
- **Empresas e Comércio:** OpenCorporates, CNPJ.ws e dados financeiros da Boa Vista SCPC.
- **Estatísticas e Públicos:** IBGE SIDRA, Banco Central (SGS API) e DataSUS.
- **Validação de Contatos:** Hunter.io (e-mails corporativos) e NumVerify (telefones).
- **Bibliotecas Open Source:** Pandas, GeoPandas (geolocalização) e `textdistance` (métricas de comparação de texto).
