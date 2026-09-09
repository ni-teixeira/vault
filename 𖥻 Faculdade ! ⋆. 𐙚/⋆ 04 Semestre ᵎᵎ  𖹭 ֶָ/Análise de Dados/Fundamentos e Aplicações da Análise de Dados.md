---
date:
tags:
  - faculdade
  - analise-de-dados
  - tipos-de-analise
  - fundamentos-e-aplicacoes
---
# Fundamentos e Aplicações da Análise de Dados: Do Passado à Prescrição de Ações

## Sumário Executivo

Este documento sintetiza os quatro pilares fundamentais da análise de dados — Descritiva, Diagnóstica, Preditiva e Prescritiva — com base nos princípios da São Paulo Tech School. A compreensão clara desses estágios é essencial para transformar dados brutos em decisões estratégicas.

A análise evolui de uma visão retrospectiva ("O que aconteceu?") para uma investigação de causalidade ("Por que aconteceu?"), avançando para a projeção de cenários futuros ("O que provavelmente acontecerá?") e, finalmente, para a recomendação de ações otimizadas ("O que deve ser feito?"). Tentar prever o futuro sem compreender o passado é classificado como um exercício de adivinhação; portanto, a estrutura analítica deve ser progressiva e fundamentada em evidências históricas e métodos estatísticos rigorosos.

## 1. Análise Descritiva: O Ponto de Partida

A análise descritiva foca em responder à pergunta: **"O que aconteceu?"**. Seu principal objetivo é simplificar grandes volumes de dados brutos para fornecer uma visão clara da situação atual ou passada, sem realizar inferências ou previsões.

### Características Principais

- **Sumarização:** Redução de dados a formatos sintéticos através de estatísticas.
- **Organização:** Estruturação para facilitar a visualização e comparação (ex: vendas por região).
- **Simplicidade:** Uso de medidas de fácil interpretação.
- **Foco no Passado:** Ligada exclusivamente a dados históricos já coletados.

### Medidas Numéricas Utilizadas

|   |   |
|---|---|
|Categoria|Exemplos|
|**Tendência Central**|Média, Mediana, Moda.|
|**Dispersão**|Desvio Padrão, Variância, Intervalo (máximo - mínimo).|
|**Posição**|Percentis, Quartis.|

## 2. Análise Diagnóstica: Identificação de Causas-Raiz

Dedicada a responder **"Por que isso aconteceu?"**, a análise diagnóstica mergulha nos dados históricos para explicar anomalias, tendências ou padrões revelados pela fase descritiva.

### Técnicas e Métodos

- **Desagregação de Dados (Drill-Down):** Quebrar dados agregados em componentes menores (ex: analisar queda de vendas por produto específico).
- **Análise de Causa-Raiz (RCA):** Uso de métodos como "Os 5 Porquês" e Análise de Regressão.
- **Análise de Cohort (Coorte):** Agrupamento de entidades com características comuns para monitorar o comportamento ao longo do tempo.
    - _Exemplo:_ Comparação da incidência de câncer de pulmão entre fumantes e não fumantes ao longo de 20 anos.
- **Análise de Sensibilidade:** Determina como a incerteza nas variáveis de entrada afeta o resultado final.
    - _Exemplo:_ Em uma lanchonete, identificou-se que o lucro é mais sensível a variações no preço de venda do que no volume de vendas.

## 3. Análise Preditiva: Projeções e Probabilidades

A análise preditiva utiliza estatística e lógica para responder: **"O que provavelmente vai acontecer?"**. Ela ensina máquinas a identificar padrões em dados históricos para projetar o futuro.

### Características e Técnicas

Esta modalidade é inerentemente iterativa, exigindo que os modelos sejam constantemente reajustados com novos dados. Os resultados são expressos em termos de probabilidade, risco ou pontuação.

**Técnicas de Modelagem:**

- **Árvore de Decisão (Básico):** Decisões visuais e lógicas (ex: aprovado/reprovado).
- **KNN - K-Nearest Neighbors (Básico):** Previsão baseada em vizinhos mais parecidos.
- **Random Forest (Intermediário):** Combinação de várias árvores para previsões robustas.
- **Redes Neurais (Avançado):** Utilizadas para padrões não lineares e aplicações de IA (imagens, voz).

## 4. Análise Prescritiva: O Ápice da Tomada de Decisão

A análise prescritiva é a fase mais avançada, focada em responder: **"O que deve ser feito?"**. Ela utiliza modelagem matemática e algoritmos para recomendar o melhor curso de ação, considerando restrições e objetivos.

### Elementos Fundamentais

- **Otimização:** Busca do melhor resultado possível (ex: rota de entrega mais curta).
- **Variáveis de Decisão:** Identificação de fatores controláveis para influenciar o futuro (ex: alocação de orçamento de marketing).
- **Sistemas de Regra (Business Rules):** Automatização de decisões baseada em dados (ex: "Se estoque < X, então gerar pedido").

### Ferramentas Avançadas

- **Programação Linear:** Resolução de problemas de máximo e mínimo (ex: mix de produtos para maximizar lucro).
- **Algoritmos Genéticos:** Para problemas complexos com vastas possibilidades de solução.
- **Aprendizado por Reforço (Reinforcement Learning):** O sistema aprende a maximizar recompensas em ambientes dinâmicos (ex: robótica, negociação de ações).

**Exemplo de Aplicação Prática:** Serviços de transporte por aplicativo utilizam a análise prescritiva para o **preço dinâmico**, equilibrando simultaneamente o lucro da empresa, a disponibilidade de motoristas e a satisfação do cliente em tempo real.

## Conclusão

A transição da análise reativa para a proativa representa a realização do valor real do Big Data. Enquanto as análises descritiva e diagnóstica preparam o terreno compreendendo o passado, as análises preditiva e prescritiva capacitam as organizações a evitar problemas e capitalizar oportunidades de forma otimizada.
