---
date:
tags:
  - faculdade
  - infraestrutura-em-nuvem
  - nuvem
  - redes-de-computadores
---
# Revisão

→ Existem três pilares que sustentam um ambiente de TI:

Processamento

Armazenamento

Rede

Um datacenter tem a função de sustentar esses 3 pilares.

Quando levamos esse conceito para o ambiente remoto, ele é chamado de nuvem.

# Elementos de rede

![[Pasted image 20260909152532.png]]

Principais dispositivos que vamos trabalhar:

- Roteador sem fio
    
    fornecem conectividade para dispositivos moveis
    
- Roteador
    
    Direcionam pacotes de dados entre redes diferentes
    
- Switch LAN
    
    Conectam dispositivos dentro de uma mesma rede local (LAN)
    
- Dispositivo de firewall
    
    Dispositivo ou software que controla o trafego de rede, bloqueando acessos não autorizados
    
- Meios de rede
    
    São canais usados para transmitir dados entre dispositivos
    
    Meios sem fio: transmitem dados por sinais de rádio ou infravermelho sem cabos físicos.
    
    Meios de LAN: conectam dispositivos em redes locais com cabos (UTP, fibra) de curto alcance.
    
    Meios de WAN: interligam redes em grandes distâncias usando links dedicados, satélite ou fibras de longa distância.
    

# Características de uma rede confiável

![[Pasted image 20260909152543.png]]

# Topologia de rede

A topologia nada mais é que a arquitetura de uma rede

# Como é entregue um pacote?

Vamos colocar o IP como se fosse um CEP de uma rua.

O cliente faz a requisição no seu computador dentro de uma rede local, essa requisição vai para um roteador na nuvem que envia essa requisição ao servidor do site que o cliente acessou.

![[Pasted image 20260909152549.png]]

# Entendendo o IP

![[Pasted image 20260909152555.png]]

O endereço IP pode ser divido em três classes:

![[Pasted image 20260909152600.png]]

A classe A é classificada para uma rede de tamanho grande (até 16.777.214) , a classe B para média (até 65.534) e a classe C para pequena (até 254)

![[Pasted image 20260909152605.png]]

# Segmentação de redes

- Máscara de rede
    
    Parecido com um endereço de ip. É dividido em 4 octetos e vai se 0 a 255
    
    255.255.255.0
    
    Atraves dos conjuntos de bits conseguimos identificar qual porcao do ip representará a **rede** e qual porção representará o **host**
    
- CIDR
    
    ClassLess Inter-Domain Routing - Roteamento entre Domínios sem Classe
    
    192.168.1.0**/24**
    
    A máscara determina quantos hosts podemos ter dentro desta rede
    

### Sub-nets

É uma subdivisão lógica realizada dentro da rede, é importante pois ajuda a facilitar o gerenciamento, melhorar a performance, controlar o tráfego, apoiar na segurança e segmentar as redes.

### Ip fixo e ip dinamico

### Ip fixo

IP Configurado diretamente no HOST (Equipamento de Rede)

1. Dificuldade no gerenciamento
2. Conflitos de IP na Rede
3. Aplicável para servidores e/ou serviços que não podem mudar de IP
4. NAT permitir que vários dispositivos usem um único endereço IP público

### DHCP

Dynamic Host Configuration Protocol.

Trata-se de um protocolo utilizado em redes de computadores que permite a estes obterem um endereço IP automaticamente

1. Facilita o gerenciamento
2. Ausência de Conflitos de IP na Rede
3. Aplicável para grandes redes que não precisam de IP fixo

# Tabela para máscara de redes

![[Pasted image 20260909152611.png]]
