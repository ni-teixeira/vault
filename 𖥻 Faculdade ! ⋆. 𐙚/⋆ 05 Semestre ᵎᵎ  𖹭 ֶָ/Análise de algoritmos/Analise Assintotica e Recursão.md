---
date: 2026-08-27
tags:
  - faculdade
  - algoritmos
  - complexidade
  - recursao
---
# Recursão
Técnica onde uma função faz uma ou mais chamadas para si mesma durante a execução

Oferece uma alternativa elegante e poderosa em tarefas repetitivas

![[Pasted image 20260828002047.png]]

![[Pasted image 20260828002057.png]]

## 3 Leis
1. Deve possuir um caso base (para interromper as chamadas)
2. Deve mudar seu estado e mover em direção ao caso base
3. Deve chamar a si mesma

## Iterativo vs Recursivo
| Característica      | Iterativo                                    | Recursivo                                     |
| ------------------- | -------------------------------------------- | --------------------------------------------- |
| **Memória (Stack)** | Consumo constante (Stack fixa).              | Consumo linear $O(n)$ (Stack cresce).         |
| **Velocidade**      | Geralmente mais rápida (menos overhead).     | Mais lenta (custo de criar frames de função). |
| **Legibilidade**    | Pode ser complexa em estruturas ramificadas. | Muito mais limpa para "Dividir e Conquistar". |

# Teorema Mestre
Teorema mestre para recorrencias de divisao e conquista

Fornece uma analise assintotica (usa a notacao big o) para relacoes de recorrencia que ocorrem na alaise de algoritmos de divisao e conquista

## Fórmula de Recorrência
A relação é expressa como: **$T(n) = aT(n/b) + f(n)$**
- $a$**:** Quantidade de chamadas recursivas.
- $b$**:** Fator pelo qual o problema é dividido (em quantas vezes o problema é quebrado).
- $f(n)$**:** Trabalho extra realizado (ex: para juntar as partes).

### Regras de Decisão do Teorema Mestre
- Se $aT(n/b) > f(n)$, o resultado é dominado pelas chamadas recursivas: $O(aT(n/b))$.
- Se $aT(n/b) < f(n)$, o resultado é dominado pelo trabalho extra: $O(f(n))$.
- Se $aT(n/b) == f(n)$, há um equilíbrio: $O(f(n) \cdot \log n)$.

### Exemplo Prático de Árvore de Recorrência

**T(n) = 4T(n/2) + O(n)**

Ela descreve um algoritmo que, para processar uma entrada de tamanho \(n\):

1. **Divide o problema**: Ele faz **(a = 4) chamadas recursivas**.
2. **Reduz o tamanho**: Cada chamada resolve um subproblema que tem **metade do tamanho original (b = 2)**, ou seja, (n/2).
3. **Trabalho extra**: Para juntar as respostas, ele faz um "trabalho extra" linear, representado por f(n) = O(n) (como um loop simples que vai de 0 a n).

A árvore de recorrência nos ajuda a calcular o custo total de todas as chamadas recursivas geradas por esse processo.

#### Passo 1: Descobrir a Altura da Árvore b = 2
O valor de \(b = 2\) significa que, a cada nível que descemos na árvore, o tamanho do problema cai pela metade.

Se começamos com um problema de tamanho \(n\), no próximo nível ele será \(n/2\), depois \(n/4\), depois \(n/8\), até que chegue ao tamanho mínimo de **\(1\)** (que é o nosso caso base).

- **Pergunta:** Quantas vezes conseguimos dividir \(n\) por \(2\) até chegar em \(1\)?
- **Resposta:** A altura da árvore (número de níveis) será de **log2(n)**.
    - _Exemplo prático:_ Se $n = 8$, dividimos por 2: $8 \rightarrow 4 \rightarrow 2 \rightarrow 1$. Foram necessárias 3 divisões. Note que $\log_2(8) = 3$

#### Passo 2: Descobrir o Número de Nós por Nível (\(a = 4\))
O valor de \(a = 4\) significa que cada nó "pai" gera **4 nós "filhos"** (ou seja, 4 novas chamadas recursivas no próximo nível).

- **Nível 0 (topo):** Temos apenas \(1\) chamada (o problema original de tamanho \(n\)).
- **Nível 1:** Esse nó se divide em **\(4\)** chamadas.
- **Nível 2:** Cada uma das 4 chamadas anteriores gera mais 4 chamadas. Logo, temos $4 \times 4 =$ $16$ chamadas ($4^2$).
- **Nível \(k\):** No nível \(k\), teremos **\(4^k\)** chamadas.

#### Passo 3: O Total de Trabalho no Último Nível
Como a árvore tem sua base (último nível) na altura **k = log2(n)**, queremos descobrir quantas chamadas recursivas (folhas) existem lá embaixo.

Substituindo k pela altura da árvore na fórmula 4^k, temos:
$$\text{Total de chamadas no último nível} = 4^{\log_2(n)}$$

Aqui entra a propriedade matemática dos logaritmos citada no seu slide: **nós podemos trocar a base do expoente com o argumento do logaritmo** $x^{\log_y(z)} = z^{\log_y(x)}$).

Trocando o \(4\) e o \(n\) de lugar, temos:
$$4^{\log_2(n)} = n^{\log_2(4)}$$

Como $\log_2(4) = 2$ (pois $2^2 = 4$), a expressão simplifica para:
$$n^2$$

Isso significa que, no último nível da árvore, o algoritmo realiza **\(n^2\) chamadas recursivas**.

#### Passo 4: Definir a Complexidade Final (Teorema Mestre)
Agora comparamos as forças:
- O trabalho feito nas folhas da árvore (caso base das recursões) é de (n^2\).
- O trabalho extra para juntar as partes a cada nível é linear: f(n) = O(n).

Como o trabalho das folhas \(n^2\) cresce muito mais rápido do que o trabalho extra \(n\), as chamadas recursivas dominam a complexidade do algoritmo.

Portanto, a complexidade assintótica final deste algoritmo é **O(n²)**.

