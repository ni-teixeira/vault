---
date:
tags:
  - faculdade
  - programacao-web-backend
  - protocolos-web
  - dns-e-ip
---
# Consumidores e servidores

### Client side

→ Qualquer aplicação que opera no computador do usuário e realiza busca ou trocas de informações na web.

### Server side

→ Máquinas que apenas hospedam aplicativos ou arquivos estáticos como HTML/CSS/JS

→ Não precisa ser necessariamente Cloud

A cada clique ou acesso do usuário a uma página, acontece uma requisição ao servidor, que devolve uma resposta.

![[Pasted image 20260909152850.png]]

Ainda que o servidor tenha problemas, a resposta pode chegar em formatos variados como timeout, bad request, serviço indisponível. Sempre terá alguma resposta!
![[Pasted image 20260909152854.png]]

# IP e DNS

Para encontrar um recurso na web, precisamos de um endereço IP (Internet Protocol) e um DNS (nome de dominio)

### IP

Endereço único na web, como:

54.239.26.72

### DNS

Texto que identifica um site na web, como: [pudim.com.br](http://pudim.com.br)

Existem 2 tipos de IP

_**→ IP privado:**_

- Exemplos: `192.168.0.1`, `192.168.64.1`
- É usado **dentro** da sua rede (em casa, escritório) e pode repetir em outras redes — por exemplo, você e seu vizinho podem ter o mesmo IP interno.
- Não é "roteável" na internet; para acessar sites, ele precisa ser traduzido para um ip público.

_**→ IP público:**_

- Exemplo: `131.72.61.70`
- É único no mundo e fornecido pelo provedor de internet (ISP).
- Usado para identificar sua rede na internet.
- Seu vizinho **não pode** ter o mesmo IP público que você.

Então, você tem um IP privado (que pode ser o mesmo que o seu vizinho), e quando você faz uma requisição seu roteador vai traduzir esse ip privado para um ip publico (fornecido pela operadora e único no mundo) para ser rastreável na internet e enviar a requisição ao servidor.  
O processo de tradução é feito pelo **NAT (Network Address Translation)**.

![[Pasted image 20260909153056.png]]

O DNS funciona como uma lista de contatos gigantes onde ele tem o nome do contato (domínio do site) e seu telefone (endereço de ip). Ele vai traduzir o domínio para um endereço de ip numérico porque os computadores e servidores somente se comunicam assim.

![[Pasted image 20260909153101.png]]

Depois que o DNS descobre o IP, ele armazena isso em cache por um certo tempo para não precisar realizar outra requisição.

Ele vai enviar requisições HTTP como Post, Get, Delete etc para o servidor, que irá ter uma resposta 200, 400 e 500.

![[Pasted image 20260909153105.png]]

### TCP, UDP e Servidores Web

Existem dois principais tipos de serviços:

### Orientados a conexão

TCP (Transmission Control Protocol)

→ Navegação na web como um todo

→ Antes de enviar dados, ele estabelece uma conexão entre computador A e computador B.

→ Garante que os dados cheguem corretamente e na ordem certa.

### Não orientados a conexão

UDP (User Datagram Protocol)

→ Streaming de vídeo, jogos online, chamadas para servidores DNS

→ Envia os dados sem garantir que chegaram.

→ Mais rápido e leve que TCP, mas **menos confiável**.
