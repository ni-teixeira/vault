---
date:
tags:
  - faculdade
  - banco-de-dados
  - sql
  - funcoes-matematicas
---
ABS (absoluto)

Retorna o valor absoluto de um número. Remove o sinal negativo.

`select abs(-1);`

CEIL (teto)

Arredonda o número para cima.

`select ceil(4.3)`

FLOOR (chão)

Arredonda o número para baixo.

`select floor(4.7)`

ROUND (arredonda)

Arredonda o número para inteiro mais próximo.

`select round(1.5)`

Empate → joga pra cima

Pode dar um segundo parâmetro para ter uma quantidade de casas decimais que você quer manter.

`select round(1.305, 2)`

TRUNCATE (truncar)

Corta as casas decimais para a quantidade solicitada

`select truncate(1307, 2);`

Funções de calculo

SQRT (raiz quadrada)

Retorna a raiz quadrada de um determinado numero.

`select SQRT(81);`

POW (potenciação)

Retorna o primeiro numero elevado pelo segundo.

`select POW(9, 2);`

MOD (resto da divisão)

Pega o restante da divisão entre dois números.

`select mod(11, 5);`

SUM (soma)

Soma dos valores de uma coluna.
