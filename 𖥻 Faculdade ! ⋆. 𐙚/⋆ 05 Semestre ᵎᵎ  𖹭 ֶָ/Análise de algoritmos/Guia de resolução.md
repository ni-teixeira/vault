---
date:
tags:
  - faculdade
  - algoritmos
  - complexidade
  - guia-de-revisao
---
1. Como Dominar Questões de Taxa de Crescimento Assintótico

Essas questões exigem que você ordene funções da **menor para a maior taxa de crescimento** (da mais rápida/eficiente para a mais lenta/ineficiente)1.

O Roteiro de Resolução

Decore a **"Fila de Dominância"** da computação (da melhor para a pior complexidade)23: $$O(1) < O(\log n) < O(n) < O(n \log n) < O(n^2) < O(n^3) < O(2^n) < O(n!)$$

- **Constante** $O(1)$**:** Não depende de $n$. O tempo é sempre o mesmo (ex: acessar um índice de array)2.
- **Logarítmica** $O(\log n)$**:** Extremamente eficiente; divide o problema ao meio (ex: busca binária)2.
- **Linear** $O(n)$**:** O tempo cresce junto com a entrada (ex: um único loop simples)2.
- **Linearítmica** $O(n \log n)$**:** Algoritmos eficientes de ordenação (Merge Sort, Quicksort)24.
- **Quadrática** $O(n^2)$**:** Dois loops aninhados (Selection Sort, Bubble Sort)24.
- **Polinomial Geral** $O(n^k)$**:** Variável na base, constante no expoente (ex: $n^{100}$)3.
- **Exponencial** $O(2^n)$**:** Constante na base, variável no expoente (ex: Torres de Hanói)25. **Cresce infinitamente mais rápido que qualquer polinômio**3.
- **Fatorial** $O(n!)$**:** O pior caso absoluto (ex: Caixeiro Viajante por força bruta)36.

💡 Truque para a Prova: "Substitua o $n$"

Se você esquecer quem cresce mais rápido entre duas funções na hora do aperto, imagine um número muito grande, como $n = 1000$:

- Comparando $n \log n$ vs $n^2$:
    - $1000 \cdot \log_2(1000) \approx 1000 \cdot 10 = 10.000$
    - $1000^2 = 1.000.000$
    - **Conclusão:** Como $1.000.000 > 10.000$, então $n^2$ cresce muito mais rápido que $n \log n$3.

---

2. Como Resolver Qualquer Questão de Teorema Mestre

O Teorema Mestre serve para dar a resposta em Big-O de equações recursivas de divisão e conquista no formato78: $$T(n) = aT(n/b) + f(n)$$

O Roteiro de Resolução

1. **Extraia as variáveis da fórmula**8:
    - $a$ = número de ramificações (chamadas recursivas)8.
    - $b$ = fator de divisão da entrada8.
    - $f(n)$ = custo extra (trabalho para dividir/juntar)8.
2. **Calcule o "Expoente Crítico" (Trabalho das folhas)**:
    - Calcule $\log_b(a)$910.
    - Isso nos dá o termo $n^{\log_b(a)}$811.
3. **Compare o peso do Trabalho das Folhas (**$n^{\log_b(a)}$**) com o Custo Extra (**$f(n)$**)**8:

|Cenário de Comparação|Caso do Teorema Mestre|Complexidade Final $T(n)$|Explicação Visual|
|---|---|---|---|
|**Folhas dominam:** $n^{\log_b(a)} > f(n)$|**Caso 1**89|$\Theta(n^{\log_b(a)})$89|A maior parte do trabalho ocorre na base da árvore de recursão.|
|**Equilíbrio perfeito:** $n^{\log_b(a)} == f(n)$|**Caso 2**89|$\Theta(n^{\log_b(a)} \log n)$89|O trabalho é igual em todos os níveis, então multiplicamos por $\log n$8.|
|**Trabalho extra domina:** $n^{\log_b(a)} < f(n)$|**Caso 3**89|$\Theta(f(n))$89|O trabalho de divisão/conquista no topo domina a execução.|

---

3. Como Resolver Questões de Gerenciamento de Memória & Big Data

Este bloco mistura teoria conceitual de sistemas operacionais com otimizações práticas em Python, Pandas e Spark.

Conceitos de Memória (C vs Python vs Rust)

- **Stack (Pilha):** Alocação rápida $O(1)$, estática, automática e muito limitada (gera _stack overflow_ se estourar)1213. Guarda variáveis locais1314.
- **Heap (Monte):** Dinâmica, grande, porém mais lenta e sujeita a fragmentação13. Guarda objetos persistentes1314.
- **Estratégias de Limpeza do Heap**12:
    - **Manual (C/C++):** Usar `malloc`/`free`15. Causa vazamentos de memória (_memory leaks_) ou ponteiros soltos (_dangling pointers_) se errar15.
    - **Contagem de Referências (Python/Swift):** Liberação imediata quando o contador chega a zero, mas falha em ciclos de referência (A aponta para B que aponta para A)1316.
    - **Coletor de Lixo / Tracing GC (Java/C#):** Rastreia o grafo de objetos em background16. Causa pausas indesejadas no sistema (_stop-the-world_)16.
    - **Modelo de Posse (Rust):** O compilador checa regras de posse estaticamente17. Sem pausas e sem coletor de lixo17.

Técnicas de Otimização em Python

- `__slots__`: Remove o dicionário padrão de atributos (`__dict__`) das instâncias de classes, reduzindo o custo de memória RAM de objetos repetitivos drasticamente18.
- `NumPy`: Substitui listas do Python por arrays de tamanho fixo em memória contígua, consumindo até 4.5 vezes menos bytes em grandes volumes de dados1819.
- `memoryview`: Permite fatiar (_slice_) buffers de dados e strings sem criar cópias adicionais na RAM2021.

Raciocínio de Big Data (Pandas vs PySpark)

- **Pandas Memory Overhead:** O Pandas carrega toda a planilha em memória de uma vez22. Ele consome muita RAM por carregar índices, metadados e strings como objetos genéricos2324.
    - _O truque da categoria:_ Para colunas redundantes (como "Estado" ou "ID_Sensor"), mudar de `string` para `category` substitui strings repetidas por códigos numéricos, reduzindo imensamente o consumo de memória24.
- **tracemalloc e PySpark:** O `tracemalloc` do Python **não é suficiente** para medir o Spark25. Ele só monitora o processo Python do driver, enquanto o processamento pesado do Spark ocorre em máquinas ou processos separados baseados em **JVM** (Java Virtual Machine) — os executores2526.
- `maxPartitionBytes` e `inferSchema`:
    - `maxPartitionBytes` define o tamanho das partições geradas pelo Spark, impactando diretamente o paralelismo da leitura de arquivos2728.
    - Usar `inferSchema=True` faz com que o Spark realize uma leitura completa extra do arquivo grande apenas para deduzir os tipos, o que é um enorme desperdício de tempo; definir o `schema` manualmente é essencial para otimização2930.