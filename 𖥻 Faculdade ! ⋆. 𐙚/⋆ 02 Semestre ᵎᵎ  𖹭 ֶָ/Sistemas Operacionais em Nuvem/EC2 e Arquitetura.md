---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - ec2
---
## Arquitetura

![[Pasted image 20260909152033.png]]

→ Quanto menos controle da infraestrutura você tem, é mais fácil de ocorrer problemas

→ Para escolher a melhor arquitetura, depende do negocio e do quanto de controle e financeiro você tem

→ Menos controle = menos liberdade, menos customização e menos segurança

→ É importante mesclar os tipos de ativos e operacional

## O que é a EC2

→ Amazon Elastic Computer Cloud

→ É projetado para fazer computação em nuvem web escalável e facil para desenvolvedores

→ É uma interface que permite obter e configurar a capacidade de máquina. Fornece um completo controle de recursos computacionais e deixa você rodar no ambiente AWS

### Diferença de instancia e AMI

→ AMI é um modelo que contem uma configuração de software (SO)

→ É possível executar uma instancia, que é uma copia da ami que roda como um servidor virtual na nuvem

→ As instancias são executadas ate que você as interrompa, encerre ou que elas falhem

→ A instancia é um servidor virtual na nuvem

![[Pasted image 20260909152040.png]]

### Conceitos gerais

→ Uma região é um local fisico onde ficam os datacenters

→ Cada grupo de data centers é chamado de zona de disponibilidade (AZ)

→ Cada região tem no minimo 3 AZ’s isoladas

![[Pasted image 20260909152044.png]]

### Conexões SSH + CLI + EC2

![[Pasted image 20260909152048.png]]

### Fluxo da criação de uma instância

![[Pasted image 20260909152052.png]]
