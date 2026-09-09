---
date: 2026-08-24
tags:
  - faculdade
  - algoritmos
  - gerenciamento-de-memoria
  - python
---
# Arquitetura e Funcionamento da Memória RAM
O sistema operacional disponibiliza um espaço endereçado para programas em execução. A alocação de memória segue uma estrutura padrão que organiza os dados conforme sua função e tempo de vida:

## Pilha de Funções (Stack)
Área que aloca variáveis locais e ponteiros (referências) quando uma função é chamada. É desalocada automaticamente ao término da função. Ocupa as faixas de endereçamento mais alto (high address).
## Área de Alocação Dinâmica (Heap)
Espaço reservado para dados criados durante o _runtime_ (execução). É onde as variáveis dinâmicas são alocadas e desalocadas.
## Outras Áreas:
- **BSS (****Block Started Symbol****):** Variáveis não inicializadas.
- **Dados de Inicialização:** Informações pré-definidas.
- **Texto (Código Fonte):** Localizado no endereçamento mais baixo (_low address_).

---
# Métricas de Armazenamento de Objetos em Python
Em Python, o tamanho de um objeto é uma função que retorna sua ocupação em bytes. O armazenamento varia significativamente entre tipos imutáveis e contêineres mutáveis.

## Tabela de Tamanhos por Tipo de Objeto

|Tipo de Objeto|Tamanho Real (Bytes)|Observações / Incrementos|
|---|---|---|
|`int`|28|Valor fixo para inteiros padrão.|
|`str`|49|+1 por caractere adicional (49 + comprimento total).|
|`tuple`|48|Tupla vazia. +8 por item adicional.|
|`lista`|56|Lista vazia. +8 por item adicional.|
|`set`|216|0-4 itens: 216; 5-16 itens: 728; 17+ itens: 2264, etc.|
|`dict`|232|0-5 itens: 232; 6-10 itens: 520; 11+ itens: 840, etc.|
|`func def`|136|Sem atributos e argumentos padrão.|

---
# Comportamento e Manipulação de Strings
Strings em Python são _arrays_ de bytes representando caracteres Unicode. A linguagem não possui um tipo específico para "caractere"; um único caractere é tratado como uma string de comprimento 1.

- **Indexação:** Utiliza colchetes para acessar elementos.
- **Indexação Reversa:** Permite acessar caracteres do final para o início (ex: `-1` é o último caractere, `-2` o penúltimo).
- **Imutabilidade:** Strings são imutáveis. Operações de concatenação resultam na criação de um **novo objeto** na memória, com um novo identificador (`id`), em vez de modificar o objeto original.

---

# Identidade de Objetos e Gerenciamento de Memória

A função `id()` é fundamental para rastrear a identidade de um objeto, retornando um inteiro único e constante durante sua vida útil.

- **Referência vs. Valor:** O valor de referência é alocado na _Stack_, enquanto o valor real (conteúdo) é armazenado no _Heap_.
- **Reatribuição:** Se uma variável `msg` recebe um valor e depois é concatenada (`msg = msg + " novo"`), o Python gera um novo ID para a segunda versão de `msg`. A identidade original é perdida, e o objeto antigo torna-se elegível para limpeza.
- **Garbage Collection (CPython):** O coletor de lixo é responsável por monitorar o `Ref Count` (contagem de referências). Quando o contador chega a zero (nenhuma variável aponta para o objeto), o espaço em memória é limpo.
- **PyObject:** Todos os objetos em Python são extensões do tipo `PyObject`, compartilhando campos básicos de cabeçalho, como o tipo do objeto e o contador de referências.

---

# Mutabilidade e Contêineres
A mutabilidade é determinada pelo tipo do objeto, impactando como a memória é gerida:

- **Objetos Imutáveis:** Números, strings e tuplas. Não podem ser alterados após a criação.
- **Objetos Mutáveis:** Dicionários e listas. Podem ser modificados _in-place_.
- **Contêineres:** Objetos que contêm referências a outros objetos (ex: listas, tuplas e dicionários).

Para análises avançadas, a classe `memoryview()` pode ser utilizada para expor o protocolo de _buffer_, permitindo acessar a localização e o espaço ocupado na memória sem copiar o conteúdo do objeto.
