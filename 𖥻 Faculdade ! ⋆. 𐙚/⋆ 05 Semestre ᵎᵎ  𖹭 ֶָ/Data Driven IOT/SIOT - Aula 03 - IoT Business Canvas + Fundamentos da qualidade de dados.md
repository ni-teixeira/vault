---
date:
tags:
  - faculdade
  - iot
  - qualidade-de-dados
  - business-canvas
---
# O IoT Business Model Canvas

O framework proposto para o desenvolvimento de projetos de IoT divide-se em componentes técnicos e de negócio, visando alinhar a viabilidade operacional à estratégia comercial.

### Componentes Técnicos e de Desenvolvimento

- **Caso de Uso IoT:** Identificação clara do problema, perfil do cliente (B2B ou B2C) e características do caso (massivo ou crítico).
- **Dados Coletados:** Definição do que será medido, tipos de sensores e frequência de envio.
- **Dados Trafegados:** Especificação do que passará pela rede e as opções de conectividade utilizadas.
- **Dados Apresentados:** Formatos de visualização para o usuário, regras de negócio aplicadas e definição de alarmes.
- **Roadmap de Desenvolvimento:** Planejamento da evolução do hardware e da aplicação, incluindo soluções de software.

### Componentes de Estratégia e Negócio

- **Usuários e Necessidades:** Identificação de usuários internos, parceiros e clientes, mapeando suas demandas específicas.
- **Escala:** Estimativas de crescimento e objetivos para horizontes de 1, 3 e 5 anos.
- **Receita:** Definição das fontes de receita e modelos de monetização da solução.

# Casos de Uso e Métricas Data-Driven

A implementação de IoT deve ser pautada por métricas que gerem valor real. Abaixo, detalham-se cinco cenários exemplares:

|   |   |   |
|---|---|---|
|Caso de Uso|Aplicação Prática|Métricas Principais|
|**Monitoramento de Ativos Críticos**|Redução de _downtime_ em geradores de Data Centers bancários.|MTBF (_Mean Time Between Failures_); Desvio padrão da vibração.|
|**Logística de Cadeia de Frio**|Transporte de vacinas ou alimentos de alto valor (Compliance).|Tempo de excursão térmica; Integridade da carga.|
|**Smart Building**|Otimização de ar-condicionado e iluminação em escritórios.|kWh por m² ocupado; Correlação temperatura externa vs. setpoint.|
|**Smart Retail**|Otimização de conversão em lojas físicas.|Tempo de permanência por corredor; Heatmap de ocupação.|
|**Gestão de Frotas**|Detecção de furto de combustível e ineficiência de condução.|Consumo específico (L/km) ajustado pelo terreno; _Idling Time_.|

# Fundamentos da Qualidade de Dados

A qualidade de dados é a função que mensura se a informação reflete com precisão o estado real do que está sendo monitorado. Ela é o primeiro estágio de qualquer programa de análise robusto.

### Desafios na Coleta de Sensores

Diferente de aplicações tradicionais, sensores apresentam desafios inerentes:

- **Ruído:** Dados do mundo real são inerentemente ruidosos. Fluxos estáveis e consistentes são fundamentais para que o processamento _downstream_ possa remover _outliers_.
- **Modos de Falha:** Sensores podem falhar sem gerar erros explícitos, enviando valores irreais ou cessando o envio. É necessário monitorar o volume de dados e o diferencial de tempo (\Delta t) entre lotes.
- **Latência vs. Volume:** Para tarefas de aprendizado de máquina, o volume é crítico. Para tarefas de inferência e alertas (ex: detecção de movimento), a latência é a variável prioritária.

### Ciclo de Vida e a Pirâmide DIKW

A transformação de sinais brutos em decisões segue a hierarquia DIKW:

1. **Dados (Data):** O sinal elétrico bruto (ex: 20mA). Fato sem contexto.
2. **Informação (Information):** O dado convertido em unidade de engenharia (ex: 25°C). Requer metrologia correta.
3. **Conhecimento (Knowledge):** O cruzamento de dados de múltiplos sensores (ex: aumento de temperatura relacionado ao aumento de corrente).
4. **Sabedoria/Decisão (Wisdom):** Intervenção humana ou automação baseada em padrões históricos e preditivos.

# Métricas de Desempenho (KPIs)

A gestão de uma infraestrutura de IoT exige o acompanhamento de indicadores técnicos e de impacto no negócio.

### Métricas de Fidelidade de Dado (Técnicas)

- **Sensor Drift:** Desvio da medição em relação ao valor real ao longo do tempo (indica necessidade de recalibração).
- **Signal-to-Noise Ratio (SNR):** Relação entre sinal e ruído, vital em ambientes industriais com interferência eletromagnética.
- **Data Completeness:** Percentual de pacotes recebidos com sucesso; essencial para algoritmos de interpolação.
- **Sampling Jitter:** Variação no intervalo entre leituras, que pode invalidar análises de frequência (como FFT).

### Métricas de Impacto no Negócio

- **OEE (Overall Equipment Effectiveness):** Mede disponibilidade, performance e qualidade em tempo real.
- **RUL (Remaining Useful Life):** Estimativa de vida útil restante de um componente antes da falha.
- **Cost per Data Point:** Avaliação do custo de infraestrutura (bateria, rede) vs. o benefício do insight gerado.
- **MTTD (Mean Time to Detect):** Tempo decorrido até o sistema identificar uma anomalia.

# Considerações sobre a Camada Física e Borda

O documento enfatiza que a fidelidade da camada física e o processamento de borda (_Edge_) são os pilares da IoT. Variáveis como calor nos cabos, oxidação de contatos e interferências de rádio podem corromper o dado antes mesmo de sua transmissão.

Um pipeline eficiente de pré-processamento na borda deve incluir:

1. Leitura Bruta.
2. Filtro de Média Móvel.
3. Detecção de _Outliers_.
4. Conversão para Unidade de Engenharia.
5. Envio por Exceção (transmitir apenas se houver variação percentual significativa).

A máxima fundamental é: **se o dado nasce errado no sensor, a nuvem não é capaz de gerar resultados milagrosos.**