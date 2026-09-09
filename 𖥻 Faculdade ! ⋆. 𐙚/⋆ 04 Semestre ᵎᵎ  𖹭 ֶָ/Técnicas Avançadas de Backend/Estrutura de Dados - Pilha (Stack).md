---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - estruturas-de-dados
  - pilha-stack
---
## **1. Definição e Características Fundamentais**

A pilha é uma estrutura de dados linear projetada para armazenar elementos do mesmo tipo. Suas propriedades distintivas incluem:

- **LIFO (Last-In First-Out):** O último elemento a entrar na sequência é o primeiro a ser retirado.
- **Acesso Restrito:** Existe visibilidade e acesso direto apenas ao elemento que está no topo da lista. Para acessar a base (o primeiro elemento inserido), é necessário remover todos os elementos acima dele.
- **Manipulação pelo Topo:** Tanto a inserção quanto a remoção ocorrem exclusivamente no final da sequência, referido tecnicamente como o "Topo".
- **Analogias Comuns:** O comportamento é comparável a uma pilha de livros ou de pratos, onde novos itens são colocados em cima e apenas o item do topo pode ser removido sem desmoronar a estrutura.

## **2. Operações Essenciais**

As operações em uma pilha são padronizadas para garantir a integridade do modelo LIFO.

### **Principais Métodos**

|Operação|Descrição|
|---|---|
|**Push (Empilhar)**|Adiciona um novo elemento ao topo da pilha. Este novo elemento passa a ser o novo topo.|
|**Pop (Desempilhar)**|Remove o elemento que está no topo da lista. É obrigatório retirar o elemento do topo antes de qualquer outro.|
|**Peek (Verificar)**|Retorna o elemento que está no topo da lista sem removê-lo (funciona como um "get").|
|**isEmpty**|Retorna um valor booleano (true ou false) indicando se a pilha está vazia.|
|**isFull**|Utilizado em implementações baseadas em vetores para indicar se a capacidade total foi atingida.|

## **3. Implementação em Java**

A linguagem Java oferece suporte nativo e flexibilidade para a criação de pilhas.

### **3.1. Classe Stack Nativa**

O Java fornece a classe `Stack` dentro do pacote `java.util`.

- **Herança:** A classe `Stack` é herdeira da classe `Vector`.
- **Instanciação:** `Stack
