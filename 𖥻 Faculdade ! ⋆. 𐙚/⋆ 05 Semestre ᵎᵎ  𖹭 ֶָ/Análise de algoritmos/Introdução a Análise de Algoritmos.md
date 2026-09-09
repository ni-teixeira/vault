---
date: 2026-08-22
tags:
  - faculdade
  - algoritmos
  - complexidade
  - crescimento-exponencial
---
# Introdução
A analise de algoritmos tem como função determinar os recursos necessários para executar um dado algoritmo

A maior parte dos algoritmos são pensados para trabalhar com inputs de tamanho arbitrario

# Objetivo
A análise de algoritmos busca prever o comportamento de um código frente a diferentes volumes de dados (inputs)

O objetivo não é apenas "fazer funcionar", mas sempre buscar pela eficiencia do algoritmo

### Correto vs Eficiente
Existem alguns criterios de qualidade que a busca deve seguir:
* Correto -> O algoritmo deve resolver o problema proposto sem erros
* Eficiente -> Deve utilizar o mínimo de recursos (tempo e memória) possível.
* Facil de implementar -> A simplicidade de codificação é valorizada.

Mas dificilmente os três pontos são alcançados de forma simultanea. Com isso, o desenvolvedor deve ter escolhas estatégicas dependendo do problema 

![[Pasted image 20260822220420.png]]


## Algoritmo Torre de Hanoi
Esse problema envolve a transferencia de 64 discos entre tres bastoes, onde cada disco deve ser movido por vez e nunca um maior fica sob um menor

A relação entre o número de discos ($n$) e o número mínimo de movimentos ($m(n)$) segue uma progressão geométrica:
- **Fórmula:** $m(n) = 2^n - 1$

### Escala e inviabilidade
Progressão do esforço necessário conforme o aumento da entrada:

| Discos ($n$) | Movimentos Necessários ($m(n)$) |
| ------------ | ------------------------------- |
| 1            | 1                               |
| 10           | 1.023                           |
| 30           | 1.073.741.823                   |
| 64           | 18.446.744.073.709.551.615      |

Mesmo que cada movimento levasse um segundo, para concluir o movimento dos 64 discos, seria necesssario 585 bilhoes de ano

Isso demonstra que o crescimento exponencial pode derrotar qualquer capacidade de processamento

# Crescimento Exponencial vs Polinomial

Existem duas categorias da analise de um algoritmo baseadas na velocidade de crescimento de sua complexidade:

![[Pasted image 20260822221721.png]]

## Polinomial
Esse tipo de crescimento ocorre quando a complexidade é definida pela base variavel (tamanho da entrada, chamamos de n) elevada a uma potencia constante (como $n^2, n^3$, etc.)
### Eficiencia
Algoritmos com tempo polinomial sao considerados eficientes
### Exemplo
No gráfico, o crescimento polinomial é representado por uma curva que sobe mais suave em comparação a exponencial

## Exponencial
O crescimento exponencial ocorre quando a variavel (tamanho da entrada n) está na potencia em vez da base (como $2^n$)45

### Impacto
Esse tipo de crescimento é extremamente rapido e torna algoritmos inviaveis quando falamos de grandes quantidades de dados
Pequenos aumentos na entrada causam granddes aumentos no tempo de execucao

**O exemplo da Torre de Hanói:** para mover 64 discos, a fórmula de movimentos é $2^{64}-1$. Mesmo fazendo um movimento por segundo, seriam necessários **585 bilhões de anos** para terminar — o que é 42 vezes a idade do universo

### Problemas NP
Atualmente, não se conhece nenhum tipo de algoritmo polinomial que seja capaz de resolver problemas complexos, que são chamados de NP-Completos.
Eles são resolvidos em tempo exponencial ou fatorial, que exige um poder computacional gigante, que nem maquinas super potentes possuem para grandes instancias

## Comparação
Em resumo, enquanto o polinomial **cresce de forma que o computador consegue lidar**, o exponencial **"explode" tão rápido que se torna impossível de processar** em tempo útil
![[Pasted image 20260822222415.png]]


# Conclusão
“Um bom algoritmo, mesmo rodando em uma máquina lenta, sempre acaba derrotando (para instâncias grandes do problema) um algoritmo pior rodando em uma máquina rápida. Sempre.” — Steven S. Skiena