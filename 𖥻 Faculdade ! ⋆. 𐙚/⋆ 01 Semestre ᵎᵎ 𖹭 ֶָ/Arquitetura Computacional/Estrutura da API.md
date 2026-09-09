---
date:
tags:
  - faculdade
  - arquitetura-computacional
  - arduino
  - api
---
## **Data Acquisition Arduino API**

API Arduino para Aquisição de Dados

### Arquivos:

![[Pasted image 20260909150803.png]]

**.gitignore:** dentro desse arquivo e pedido ao git que quando fossemos atualizar o projeto, ele ignorasse os git_modules (pasta criada quando damos o npm install com as bibliotecas instaladas);

**main.js:** esta toda a configuração da api e operações de habilitar inserção no banco de dados, e onde mexemos para configurar as portas;

**package-lock.json:** instrui o programa a instalar as dependências necessárias para seu funcionamento;

**package.json:** mostra uma descrição da api, sua versão, licenças e as dependências necessárias;

**index.html:** utilizaremos para ver a api funcionando dentro de um gráfico feito pela biblioteca do chart.js.

### Demonstre no main.js como as variáveis do servidor de serviço foram definidas:

![[Pasted image 20260909150811.png]]

Criando constantes (valores que não vão se alterar) e chamando as bibliotecas necessárias para o funcionamento. São as **variáveis** do servidor de serviço sendo definidas.

**Configuração do nosso Banco de dados**. Criamos uma conexão com permissões de inserção e colocamos as informações como senha, usuário e a porta necessária ai dentro. Se estivermos usando um usuário da **Maquina Virtual** iremos utilizar a porta **3307**.

### Qual é a distinção entre as portas 3300 e 3306?

A porta **3306** é a nossa **porta padrão do servidor** MySQL

A porta **3300** é a porta do servidor onde vamos exibir os dados coletados pelo Arduino/api

### No index.html, como é feita a chamada à API externa chart.js? Onde é

realizada essa chamada e onde um novo gráfico é criado?
![[Pasted image 20260909150821.png]]

Nesta parte estamos chamando um **novo gráfico** pelo chart.js

![[Pasted image 20260909150824.png]]

Dentro do script estamos **criando um novo** gráfico

### Onde é possível ajustar o tamanho e o tipo de gráfico gerado?

![[Pasted image 20260909150830.png]]

Conseguimos alterar o tamanho por meio do **style da div**

![[Pasted image 20260909150833.png]]

Definimos o tipo do gráfico **dentro do script, em type: line**

### O que é representado pelo método 'get' no código main.js?

![[Pasted image 20260909150838.png]]

Esse método dentro do nosso código serve para **obter uma informação**, no caso  
ele está sendo usado juntamente ao app para obter as informações do sensor.

Resumidamente, você esta fazendo uma **requisição GET para um endpoint (url),** você estará pedindo ao seu servidor para te dar os dados associados a aquele endereço (endpoint).

O servidor, ao receber essa requisição, **processa e retorna uma resposta**. No caso, essa resposta poderia ser as variáveis de valores do sensor analógico ou digital.

### Por que é gerado um arquivo JSON e para que ele é utilizado?

É criado o response.json porque ele vai ser utilizado na **conversão da resposta do servidor** (pelo get). Vai ser pego a resposta em .json e ele vai ser convertido a um objeto Javascript. Permitindo que esses dados sejam mais fáceis de manipular e receber.

### Considerando que no código.ino a saída é:

**→ DHTH_temp; DHTH_umid; Luminosidade; LM35_temp; chave;**  
**Explique como essa estrutura de dados (na forma de lista) é  
adicionada como um vetor na APINode. Demonstre como o código  
captura essa lista e a divide ordenadamente dentro de um vetor.**

![[Pasted image 20260909150846.png]]

Essa parte do código é responsável por **receber os dados** do Arduino e **trata-los dentro de um vetor**, cada vetor assume uma **posição que se inicia no 0**, e todos os dados **são divididos por um split** (no caso, o ponto e virgula).

Na segunda parte, o código esta **pegando os dados** que foram recebidos e tratados e **colocando (push) eles dentro de um array (vetor)**. A cada nova leitura, os **valores mais recentes são adicionados ao final** dos arrays correspondentes.
