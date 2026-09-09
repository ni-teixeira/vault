---
date:
tags:
  - faculdade
  - arquitetura-computacional
  - arduino
  - codigo-ino
---
## → Definição das variáveis

![[Pasted image 20260909150907.png]]

![[Pasted image 20260909150911.png]]

Primeiramente, dentro do código nos **definimos as variáveis** constantes (que não irão mudar de valor), normalmente elas são **onde os pinos estão conectados** (como digital no pino 7, analógico no a4).

## → Inicialização

![[Pasted image 20260909150916.png]]

![[Pasted image 20260909150920.png]]

Na inicialização, sempre tem um serial.begin que **inicializa a comunicação serial** a 9600 bps.

## → Execução/exibição

![[Pasted image 20260909150925.png]]

![[Pasted image 20260909150928.png]]

Nesta parte, conseguimos notar que o código esta **criando um loop para estar sempre em execução**, **mostrando na tela** do usuário os **valores coletados** pelo sensor.

## → Delay

![[Pasted image 20260909150932.png]]

![[Pasted image 20260909150936.png]]

**Definindo um delay (demora para o tempo de execução novamente)** para cada print que será executado, no caso das imagens são delays de 2 segundos e 1 segundo respectivamente
