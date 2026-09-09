---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - estruturas-de-dados
  - arvores-binarias
---
# Estruturas de Dados: Árvores Binárias e suas Evoluções

## Sumário Executivo

Este documento sintetiza os fundamentos, a lógica de funcionamento e as aplicações práticas das árvores binárias no desenvolvimento de software e sistemas de armazenamento. Diferente de estruturas lineares como listas ou matrizes, as árvores organizam dados de forma hierárquica, permitindo buscas e manipulações extremamente eficientes com complexidade logarítmica (O(\log n)). O ponto central para a eficiência dessa estrutura é o **balanceamento**: uma árvore desbalanceada perde sua vantagem de performance, assemelhando-se a uma lista ligada. O briefing aborda desde a anatomia básica e implementação em Java até evoluções sofisticadas como Árvores Rubro-Negras (Red-Black) e Árvores B+, que são fundamentais para o funcionamento de bancos de dados modernos e sistemas de arquivos.

## 1. Anatomia e Conceitos Fundamentais

As árvores são estruturas de dados não lineares formadas por elementos chamados **Nós (Nodes)**, organizados em níveis.

### Componentes de uma Árvore

- **Raiz (Root):** O nó principal no topo; toda busca se inicia por ele. Não possui pai.
- **Pai (Parent):** Um nó que se conecta a nós em níveis inferiores.
- **Filho (Child):** Nó posicionado imediatamente abaixo de outro na hierarquia.
- **Folhas (Leaves):** Nós que não possuem filhos, localizados nas extremidades.
- **Subárvore:** Uma parte da árvore que, isoladamente, forma outra estrutura de árvore completa.

### Métricas e Distância

A medição da eficiência e do caminho dentro de uma árvore utiliza métricas específicas:

- **Profundidade (Depth):** Distância da raiz até o nó (Raiz tem profundidade 0).
- **Altura (Height):** Distância de um nó até a folha mais distante abaixo dele.
- **Distância entre Nós:** O número mínimo de arestas para sair do Nó A e chegar ao Nó B. É calculada identificando o **LCA (Lowest Common Ancestor)** — o ancestral comum mais próximo entre os dois nós.

## 2. Árvore Binária de Busca (Binary Search Tree - BST)

A árvore binária tradicional permite que cada nó tenha, no máximo, dois filhos (esquerda e direita). No entanto, sua eficácia é maximizada na forma de uma **BST**, que segue uma regra de ordenação rigorosa:

1. **Valores menores** que o pai vão para a esquerda.
2. **Valores maiores** que o pai vão para a direita.

### Vantagem de Performance

Em uma busca linear em uma lista de 1 milhão de itens, o pior cenário exige 1 milhão de comparações. Em uma BST bem balanceada, o mesmo processo leva cerca de **20 passos**, pois a cada movimento, metade das opções restantes é eliminada.

### Implementação em Java

A estrutura básica de um nó e a lógica de inserção recursiva são fundamentais:

```text
class Node {
    int valor;
    Node esquerda, direita;

    public Node(int valor) {
        this.valor = valor;
        esquerda = direita = null;
    }
}
```

## 3. Tipologias e o Desafio do Balanceamento

A forma como uma árvore é preenchida determina sua eficiência. Uma árvore **desbalanceada ou degenerada** (onde os nós crescem apenas para um lado) perde sua característica logarítmica e torna-se ineficiente.

|   |   |
|---|---|
|Tipo de Árvore|Descrição|
|**Cheia (Full)**|Cada nó tem exatamente 0 ou 2 filhos.|
|**Completa (Complete)**|Todos os níveis preenchidos (o último deve estar preenchido da esquerda para a direita).|
|**Perfeita (Perfect)**|Todos os nós internos têm dois filhos e todas as folhas estão no mesmo nível.|
|**Balanceada**|A diferença de altura entre as subárvores esquerda e direita de qualquer nó é de, no máximo, 1.|

### Árvores Rubro-Negras (Red-Black Trees)

Para evitar a degeneração, foram criadas árvores com auto-balanceamento. As Red-Black Trees utilizam regras de cores e operações de **recoloração** e **rotação** para garantir que a árvore permaneça aproximadamente balanceada sem a necessidade de cálculos constantes de altura.

## 4. Travessias: Métodos de Navegação

As travessias definem a ordem em que os nós são visitados, sendo escolhidas com base no objetivo da operação:

1. **In-Order (Em-Ordem):** Visita Esquerda → Raiz → Direita. Resulta em valores em ordem crescente numa BST.
2. **Pre-Order (Pré-Ordem):** Visita Raiz → Esquerda → Direita. Útil para exibir a estrutura ou serialização.
3. **Post-Order (Pós-Ordem):** Visita Esquerda → Direita → Raiz. Ideal para remover nós ou liberar memória.
4. **Level-Order (Por Níveis):** Visita nó a nó, nível a nível. Usada para buscar o menor caminho.

## 5. Aplicações no Mundo Real e Evolução para Discos

As árvores estão presentes em organogramas, menus de aplicativos, árvores de decisão e na estrutura **DOM** de páginas web. Contudo, seu uso mais crítico é em **Índices de Bancos de Dados**.

### O Problema do Disco Rígido

Árvores binárias simples são muito "altas". Para 1 milhão de registros, seriam necessárias até 20 leituras no disco (HD/SSD), o que é lento.

### A Solução: Árvore B e B+ (B-Tree / B+ Tree)

Projetadas especificamente para armazenamento em disco, estas são árvores "gordas" e "baixas":

- **Múltiplos Filhos:** Um único nó pode conter centenas de chaves, reduzindo a altura da árvore para apenas 3 ou 4 níveis, mesmo com milhões de dados.
- **Dados nas Folhas:** Na B+ Tree, os dados reais ficam apenas nas folhas; os níveis superiores servem apenas como sinalização.
- **Folhas Conectadas:** As folhas são ligadas entre si por uma lista ligada. Isso permite que buscas por intervalos (Ex: `BETWEEN 35 AND 48`) sejam feitas horizontalmente após encontrar o primeiro elemento, sem precisar retornar ao topo da árvore.
