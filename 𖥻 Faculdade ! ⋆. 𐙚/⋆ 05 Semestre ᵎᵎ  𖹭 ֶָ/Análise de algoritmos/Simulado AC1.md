---
date:
tags:
  - faculdade
  - algoritmos
  - complexidade
  - simulado
---
## Questão 1 — Taxa de crescimento assintótico
**Enunciado:**  
Observe o gráfico que compara a taxa de crescimento de quatro funções em relação ao tamanho da entrada `n`.
Com base no comportamento assintótico dessas funções, assinale a alternativa que as ordena corretamente da **menor para a maior taxa de crescimento**.

### Alternativas
- [ ] **a.** `log n < n < n log n < n²`
- [ ] **b.** `log n < n² < n log n`
- [ ] **c.** `n < log n < n² < n log n`
- [ ] **d.** `n² < n log n < n < log n`

### Resposta
**A —** `**log n < n < n log n < n²**`

**Explicação:**  
A ordem de crescimento assintótico é:  
`log n < n < n log n < n²`.

---


---
## Questão 2 — Teorema Mestre
**Enunciado:**  
Aplique o Teorema Mestre à recorrência:
```
T(n) = 4T(n/2) + n²
```
Qual é o resultado correto?

### Alternativas
- [ ] **a.** O Teorema Mestre não pode ser aplicado a essa recorrência.
- [ ] **b.** `log_b(a) = log_2(4) = 2 > grau de f(n)` → Caso 1 → `T(n) = Θ(n²)`
- [ ] **c.** `log_b(a) = log_2(4) = 2 < grau de f(n)` → Caso 3 → `T(n) = Θ(n²)`
- [ ] **d.** `log_b(a) = log_2(4) = 2 = grau de f(n)` → Caso 2 → `T(n) = Θ(n² log n)`

### Resposta
**D —** `**T(n) = Θ(n² log n)**`
**Explicação:**  
Temos `a = 4`, `b = 2` e `f(n) = n²`.
```
log_b(a) = log_2(4) = 2
```
Como `f(n) = n²`, o grau também é `2`. Portanto, estamos no **Caso 2**:
```
T(n) = Θ(n² log n)
```

---

---
## Questão 3 — Busca binária e Teorema Mestre
**Enunciado:**  
A recorrência da busca binária é:
```
T(n) = T(n/2) + 1
```
Aplicando o Teorema Mestre (`a = 1`, `b = 2`, `f(n) = 1 = Θ(n⁰)`), qual é a complexidade resultante?

### Alternativas
- [ ] **a.** `Θ(log n)`
- [ ] **b.** `Θ(1)`
- [ ] **c.** `Θ(n log n)`
- [ ] **d.** `Θ(n)`

### Resposta
**A —** `**Θ(log n)**`
**Explicação:**  
Temos:
```
log_b(a) = log_2(1) = 0
```
Como `f(n) = Θ(n⁰)`, temos o **Caso 2**:
```
T(n) = Θ(n⁰ log n)
T(n) = Θ(log n)
```

---


---
## Questão 4 — Comparação de taxas de crescimento
**Enunciado:**  
Considere as funções:
- `log n`
- `n log n`
- `n¹⁰⁰`
- `2ⁿ`
- `n!`

Assinale a alternativa que ordena corretamente essas funções da **menor para a maior taxa de crescimento assintótico**.

### Alternativas
- [ ] **a.** `n log n < log n < 2ⁿ < n¹⁰⁰ < n!`
- [ ] **b.** `log n < n¹⁰⁰ < n log n < n! < 2ⁿ`
- [ ] **c.** `n! < 2ⁿ < n¹⁰⁰ < n log n < log n`
- [ ] **d.** `log n < n log n < n¹⁰⁰ < 2ⁿ < n!`

### Resposta
**D —** `**log n < n log n < n¹⁰⁰ < 2ⁿ < n!**`

**Explicação:**  
A ordem assintótica é:
```
log n < n log n < n¹⁰⁰ < 2ⁿ < n!
```

- Logarítmica cresce mais lentamente que qualquer crescimento polinomial.
- `n log n` cresce mais que `log n`.
- Qualquer polinômio `n^k` cresce mais lentamente que uma exponencial `2ⁿ`.
- O fatorial `n!` cresce mais rapidamente que `2ⁿ`.

---


---
## Questão 6 — `tracemalloc` e PySpark
**Enunciado:**  
No exercício de gerenciamento de memória, a Parte C (PySpark) afirma que `**tracemalloc**` **não é suficiente para medir corretamente o consumo de memória do pipeline**, ao contrário do que ocorre nas Partes A e B.
Por que isso acontece?

### Alternativas
- [ ] **a.** Porque o `tracemalloc` só funciona com pandas, sendo incompatível com qualquer outra biblioteca de processamento de dados.
- [ ] **b.** Porque o `tracemalloc` mede apenas o tempo de execução, não sendo capaz de medir memória em nenhum cenário.
- [ ] **c.** Porque o `tracemalloc` mede apenas alocações dentro do processo Python do driver, enquanto a maior parte do processamento do Spark ocorre em processos JVM separados (os executores), mesmo em modo local.
- [ ] **d.** Porque o Spark desabilita automaticamente qualquer profiler de memória Python por motivos de segurança.

### Resposta
**C**
**Explicação:**  
O `tracemalloc` monitora alocações de memória feitas pelo **processo Python**.
No PySpark, porém, o processamento não fica limitado ao Python. O Spark utiliza a **JVM**, e os executores podem realizar grande parte do processamento e consumir memória fora do processo Python monitorado pelo `tracemalloc`.
Assim, medir apenas com `tracemalloc` pode dar uma visão incompleta do consumo total de memória do pipeline Spark.

---


---
## Questão 7 — `spark.sql.files.maxPartitionBytes`
**Enunciado:**  
O exercício configura a `SparkSession` com:
```
spark.sql.files.maxPartitionBytes = "128mb"
```
e pede para registrar `df.rdd.getNumPartitions()` para cada tamanho de arquivo testado.
Qual é o efeito dessa configuração?

### Alternativas
- [ ] **a.** Ela limita o número máximo de linhas que podem ser lidas do arquivo CSV, descartando o restante.
- [ ] **b.** Ela define a quantidade máxima de memória RAM que o driver Spark pode usar durante toda a execução.
- [ ] **c.** Ela define o tamanho máximo do arquivo de saída gerado pelo `.write()`, dividindo-o em partes menores.
- [ ] **d.** Ela define o tamanho máximo (em bytes) de cada partição criada ao ler o arquivo, controlando quantas partições o Spark vai gerar e, consequentemente, o grau de paralelismo na leitura.

### Resposta
**D**
**Explicação:**  
`maxPartitionBytes = "128mb"` define o tamanho máximo em bytes de cada partição durante a leitura dos arquivos.
Na prática, arquivos maiores podem ser divididos em várias partições. Isso influencia a quantidade de partições e, consequentemente, o paralelismo do processamento.

---


---
## Questão 8 — `inferSchema=True` no PySpark
**Enunciado:**  
Ao ler `leituras_sensores.csv` com PySpark, é recomendado definir o `schema` manualmente com `StructType`/`StructField`, em vez de usar `inferSchema=True`.
Qual é a principal razão dessa recomendação para arquivos com milhões de linhas?

### Alternativas
- [ ] **a.** Porque um schema definido manualmente permite que o Spark ignore colunas com valores nulos automaticamente.
- [ ] **b.** Porque `inferSchema=True` só funciona corretamente com arquivos Parquet, nunca com arquivos CSV.
- [ ] **c.** Porque `inferSchema=True` exige uma passada completa extra sobre o arquivo apenas para descobrir os tipos das colunas, o que é custoso para arquivos com milhões de linhas; definir o schema manualmente evita essa leitura adicional.
- [ ] **d.** Porque `inferSchema=True` desabilita o particionamento automático do arquivo, forçando leitura em uma única partição.

### Resposta
**C**
**Explicação:**  
`inferSchema=True` faz o Spark analisar os dados para descobrir automaticamente o tipo de cada coluna. Em arquivos CSV grandes, essa etapa adiciona custo de leitura e processamento.
Ao definir o `schema` manualmente, o Spark já conhece os tipos das colunas e evita a etapa de inferência.




---
## Questão 9 — Memória no pandas
**Enunciado:**  
O exercício pede para discutir por que o **pandas** pode consumir mais memória por linha do que uma estrutura manual simples (ex.: lista de dicionários/tuplas), mesmo sendo mais rápido, e como o tipo de dado escolhido para colunas como `id_sensor` ou `estacao` (`string` vs. `category`) afeta esse consumo.
Qual alternativa melhor explica essa questão?

### Alternativas
- [ ] **a.** O DataFrame do pandas possui overhead estrutural (index, metadados, tipos de dados como `float64`/`int64` e armazenamento de strings como objetos Python), e usar dtype `"category"` para colunas repetitivas como `id_sensor` e `estacao` pode reduzir bastante esse consumo em comparação ao tipo string padrão.
- [ ] **b.** O pandas sempre consome menos memória por linha do que qualquer estrutura manual, independentemente do tipo de dado escolhido para as colunas.
- [ ] **c.** O tipo de dado das colunas (`string` vs. `category`) não tem nenhum impacto no consumo de memória de um DataFrame pandas.
- [ ] **d.** O pandas consome mais memória apenas porque é escrito em Python puro, ao contrário do módulo `csv` da biblioteca padrão, que é escrito em C.

### Resposta
**A**
**Explicação:**  
O **pandas possui overhead estrutural**, como índice, metadados e estruturas internas para armazenar os dados. Strings também podem consumir bastante memória quando armazenadas como objetos Python.
Para colunas com muitos valores repetidos, como `id_sensor` e `estacao`, o dtype `category` pode reduzir significativamente o consumo de memória, pois os valores únicos são armazenados uma vez e as linhas utilizam códigos para representá-los.