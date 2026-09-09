---
date: 2026-08-22
tags:
  - faculdade
  - algoritmos
  - gerenciamento-de-memoria
  - stack-heap
---
# Introdução
Gerenciamento de memória é um conjunto de regras, técnicas e mecanismos que determinam como um programa de computador vai alocar, utilizar e liberar memoria RAM do sistema durante a execução de um programa

Toda linguagem de programação precisa fazer esse gerenciamento. Independentemente de como seja feito, elas precisam garantir que as informações necessárias sejam guardadas com segurança e o espaço seja liberado quando elas não forem mais uteis

---
# Stack vs Heap
O sistema operacional disponibiliza um espaço endereçado para a execução de programas, organizado em duas estruturas principais
A escolha de onde alocar os dados impacta na performance e segurança do software

## Tabela comparativa

| Característica    | Stack (Estática)                          | Heap (Dinâmica)                         |
| ----------------- | ----------------------------------------- | --------------------------------------- |
| **Velocidade**    | Muito rápida (Alocação O(1))              | Mais lenta (Busca por espaço livre)     |
| **Tamanho**       | Limitado (MBs, risco de _stack overflow_) | Grande (Limitado pela RAM/Swap)         |
| **Gerenciamento** | Automático (Escopo de função)             | Manual, GC ou Runtime                   |
| **Uso Típico**    | Variáveis locais, endereços de retorno    | Objetos dinâmicos, estruturas variáveis |
| **Fragmentação**  | Não ocorre                                | Pode ocorrer                            |

### Stack
Estática
Extremamente rapida mas com tamanho limitado
Gerenciamento automatico de variaveis locais a medida que entram e saem do escopo

### Heap
Dinamica
Maior (limitado por ram fisica ou swap)
Acesso e alocação mais lentas
Armazena objetos criados dinamizamente e estrutura de dados de tamanho variavel

![[Pasted image 20260823001533.png|512]]
![[Pasted image 20260823001545.png|513]]

---
# Ponteiros
Ponteiro é uma variavel especial que guarda o endereco da memoria ram onde outro dado esta armazenado

Em linguagens de programação, os ponteiros funcionam como um "atalho" ou "endereço" que aponta para o local exato onde a informação está guardada

## Como funcionam?
Quando você escreve o seguinte código em C:

```
int *ptr = (int *)malloc(sizeof(int));
```

- O `malloc` solicita ao sistema operacional um espaço livre na memória **Heap** de tamanho suficiente para guardar um número inteiro (`int`).
- O sistema operacional reserva esse espaço e devolve o seu **endereço físico** na memória RAM.
- O asterisco em `int *ptr` avisa ao compilador que a variável `ptr` é um ponteiro. Ela agora guarda esse endereço físico e, portanto, **"aponta"** para aquele bloco de memória.

### Desreferenciamento
Para ler ou modificar o valor que está dentro daquele endereço, nós usamos o ponteiro de forma direta:

```
*ptr = 42;
```

- O caractere `*` colocado antes do nome do ponteiro realiza o processo de **desreferenciamento**. Ele diz ao computador: _"Siga o endereço que está guardado em_ _ptr_ _e, no local de destino, guarde o valor 42"_.
- Ao ler `*ptr` (como em um `printf`), o computador faz o caminho inverso: vai até o endereço guardado pelo ponteiro e traz o valor que está lá (neste caso, o número 42).

### Liberação
Como o gerenciamento na memória Heap de linguagens como C é **manual**, o sistema não limpa a memória sozinho. O programador precisa liberar o espaço explicitamente:

```
free(ptr);
ptr = NULL;
```

- O comando `free(ptr)` devolve o bloco de memória ao sistema operacional.
- Em seguida, define-se o ponteiro como `NULL` (nulo) para garantir que ele não guarde mais aquele endereço que agora está inválido.

## C vs Python
**Em Python:** Quando você faz `b = a` (como na Imagem 6), você não está copiando o conteúdo de `a` para `b`. Em vez disso, você está criando uma nova **referência**. Isso significa que tanto `a` quanto `b` agora "apontam" para o exato mesmo objeto na memória Heap.

## Desafios
Como o gerenciamento manual dá controle total ao programador, erros de lógica com ponteiros geram falhas graves de sistema:
1. **Dangling Pointer (Ponteiro Solto):** Ocorre quando você libera um bloco de memória com `free(ptr)`, mas o ponteiro continua guardando aquele endereço antigo. Se você tentar acessar ou alterar `*ptr` depois disso, causará um comportamento imprevisível ou uma falha de segmentação no sistema.
2. **Double Free:** Acontece se você tentar chamar `free(ptr)` duas vezes na mesma região de memória, o que corrompe o controle do sistema de alocação.
3. **Buffer Overflow:** Ocorre ao tentar gravar informações além do limite de tamanho que o ponteiro recebeu originalmente, corrompendo as variáveis e os dados vizinhos na memória.

---
# Estratégias de gerenciamento automatico
Diferentes linguagens vão abordar diferentes formas de decidir quando liberar a memoria do heap

## 1. Contagem de referencias
- Python, Swift
- Cada objeto monitora a quantidade de referencias que apontam a ele
- É destruido quando a quantidade chega a 0
- Vantagem: liberação imediata
- Desvantagem: Não resolve ciclos de referencia de forma nativa

## 2. Coletor de lixo por rastreamento (garbage collector)
- Java, GO, C#
- Percorre periodicamente um grafo de objetos a partir de raizes
- Libera um processo de deletar objetos nao utilizados periodicamente
- Vantagem: Resolve ciclos de referencia
- Desvantagem: Pausas na execução (_stop-the-world_) e _overhead_ de CPU

## 3. Modelo de posse / ownership
- Rust
- Compilador rastreia estaticamente o dono do dado
- Quando o dono sai do escopo, libera memoria
- Vantagem: sem overhead em tempo de execucao e sem pausas
- Desvantagem: curva de aprendizado elevada

## 4. Gerenciamento manual
C, C++
O programador utiliza comandos explicitos para alocar e liberar memoria (malloc e free)
Vantagem: controle total e performance maxima
Desvantagem: alta propensao a bugs criticos

---
# Modelo de memoria do python
No Python, absolutamente tudo é um objeto
Cada objeto é uma struct em C (pyobject) que tem um cabecalgo contador de referencias (ob_refcnt)

## Custo de objetos em memoria
|Tipo de Objeto|Tamanho Base (Bytes)|Observações|
|---|---|---|
|**int**|28|—|
|**str**|49|+1 byte por caractere|
|**list**|56|+8 bytes por item adicional|
|**tuple**|40|+8 bytes por item adicional|
|**dict**|232|Aumenta em degraus (ex: 360 bytes após 5 itens)|
|**set**|216|Aumenta em degraus (ex: 728 bytes após 4 itens)|

---

# Tecnicas de otimização
Existem algumas ferramentas para mitigar o overhead de memoria e aumentar a eficiencia do software

## __slots__
- remove o dicionario de atributos padrao (__dict__)
- pode reduzir o consumo de uma instancia de 344 bytes para 48 bytes
![[Pasted image 20260823012336.png]]
## numpy
- oferece arrays multidimensionais e rotinas matematicas rapidas
- supera a eficiencia de listas nativas para grandes volumes de dados
![[Pasted image 20260823012345.png]]
## memory view
- permite acessar a memoria interna de objetos que suportam o protocolo de buffer sem copiar dados
- bom para o processo de arquivos grandes, programacao de rede e integracao com extensoes em c
- evita o esgotamento da ram por slicing repetido
![[Pasted image 20260823012353.png]]

---
# Desafios e impacto

## Falhas Comuns
- **Memory Leak (Vazamento):** Memória alocada nunca é liberada, fazendo o processo crescer continuamente.
- **Dangling Pointer / Use-after-free:** Acesso a uma referência cujo objeto já foi desalocado.
- **Buffer Overflow:** Escrita fora dos limites de um bloco alocado, corrompendo dados vizinhos.
- **Fragmentação:** Inexistência de blocos contíguos suficientes para novas alocações, apesar de haver memória total disponível.

## Aplicações Práticas
- **Backend Web:** Vazamentos em servidores de longa duração (Django, Flask, Node.js) levam ao encerramento do processo pelo orquestrador (ex: **OOMKilled** no Kubernetes).
- **Sistemas Embarcados:** Dispositivos com RAM limitada (Arduino Uno com 2 KB ou ESP32 com ~520 KB) não toleram alocação dinâmica ou pausas de GC.
- **Machine Learning:** A VRAM da GPU é escassa. Técnicas como **quantização** (float32 para int8), redução de _batch size_ e **mixed precision** (float16) são cruciais para viabilizar o treinamento e a execução de modelos.

ABdec

Abcedde