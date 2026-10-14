---
date: 2026-08-28
tags:
  - "#faculdade"
---
# Algoritmos de busca em grafos não ponderados
 BFS busca em largura
 ideal para encontrar o caminho mais curto
 usa fila

 DFS busca em profundidade 
 usa pilha ou recusao
 explora caminhos mais longos

BFS
explora sistematicamente um grafo nivel por nivel
BFS visita primeiros todos seus vizinhos imediatos e dps os vizinhos destes
tempo = o(v + e)
espaco = 0(v)

DFS
percorre um caminho mais profundamente possivel antes de voltar e tentar um caminho diferente
caminha por um labiritinho, chega num beco sem saida e volta pra tentar um caminho diferente
tempo = O(v + e)
espaco = O(v) -> em arvores equilibradas chega a o(log v) ou O(profundidade)

