---
date: 2026-08-27
tags:
  - faculdade
  - algoritmos
  - complexidade
  - notacao-big-o
---
# Fundamentos
A medição de eficiencia dos algoritmos é uma preocução geral da ciencia da computação, que procura otimizar custo em termos de poder e tempo de processamento

Ao comparar dois algoritmos, existem alguns criterios qu ajudam a medir, mas são dependentes da plataforma e implementação

## Criterios de medição
Ao comparar algoritmos, métricas dependentes de plataforma (hardware, linguagem, implementação) são evitadas. Em vez disso, busca-se uma análise que descreva o custo real no pior caso através de funções matemáticas.

## Exemplo Selection Sort

```
function SelectionSort(A, N) 

	for i from 0 to N-2 
		minIndex = i 
		
		for j from i+1 to N-1 
		
			if A[j] < A[minIndex] then 
				minIndex = j 
			end if 
			
		end for 
		
		if minIndex != i then 
			temp = A[i] A[i] = A[minIndex] 
			A[minIndex] = temp 
		end if 
		
	end for 

end function

```

![[Pasted image 20260827230707.png]]

![[Pasted image 20260827230729.png|383]]

A análise detalhada do algoritmo **Selection Sort** demonstra como o custo é calculado:

1. **Custo Real:** Soma-se o tempo de execução de cada linha multiplicado pelo número de vezes que ela é executada.
2. **Expressão Matemática:** Resulta em uma função como $(c3+c4+c5) n^2 + (c1+c2+c6+c7+c8+c9) n$.
3. **Simplificação Assintótica:** Como o termo dominante é $n^2$, o comportamento para grandes entradas é definido como $O(n^2)$, ignorando-se as constantes $c$ e o termo linear $n$.

---

# Analise Assintotica
A análise assintótica descreve o comportamento de limites. 

Ela permite comparar a eficiência de dois algoritmos observando como o tempo de execução cresce conforme a entrada ($n$) aumenta.

![[Pasted image 20260827233033.png|624]]

(c3 + c4 + c5)n² + (c1 + c2 + c6 + c7 + c8 + c9)n 

Como o termo dominante da função é n² podemos dizer que o Selection Sort tem complexidade assintótica: O (n² )

## Notações

| Caso   | Foco                      | Notação Tipica |
| ------ | ------------------------- | -------------- |
| Melhor | Cenário mais favorável    | Ω (Omega)      |
| Médio  | Cenário típico/esperado   | Θ (Theta)      |
| Pior   | Cenário mais desfavorável | 𝑂 (Big-O)     |

## Complexidades mais comuns

| Notação     | Nome         | Exemplo                               |
| ----------- | ------------ | ------------------------------------- |
| O (1)       | Constante    | Acessar um índice de um array         |
| O (log n)   | Logaritmica  | Busca binária                         |
| O (n)       | Linear       | Percorrer uma lista simples (um for)  |
| O (n log n) | Linearitmica | Algoritmos eficientes de ordenação    |
| O (n²)      | Quadratica   | Dois loops aninhados (Selection Sort) |
| O (2^n)     | Exponencial  | Algoritmos de força bruta             |

![[Pasted image 20260827233541.png|532]]

---

# Estrategias para redução de complexidade
## Troca de tempo por espaço (Space-time Trade-off)
* Memoization (cache): salvar resultados de funções caras para não precisar calcula-las novamente (comum em programacao dinamica)
* hash maps (dicionarios): transforma uma busca de o(n) em busca de o(1)

## Dividir para conquistar (divide and conquer)
* Se o problema é muito grande, quebre ao meio várias vezes. Isso move o algoritmo de uma complexidade linear o(n) ou quadratica o(n²) para uma logaritmica o(log n) ou linearimitica o(n log n)
* busca binaria vs busca linear

## Outras estrategias
* Algoritmos gananciosos ou gulosos (greedy algorithms)
* programacao dinamica (dp)
* programacao linear (lp)

