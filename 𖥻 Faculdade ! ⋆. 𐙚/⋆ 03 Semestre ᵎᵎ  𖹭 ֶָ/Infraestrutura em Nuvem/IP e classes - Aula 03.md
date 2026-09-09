---
date:
tags:
  - faculdade
  - infraestrutura-em-nuvem
  - nuvem
  - ip-e-classes
---
# Divisão de endereço / classe C

![[Pasted image 20260909152632.png]]

**Network:** identifica a rede (o “bairro”).

**Host:** identifica a máquina dentro dessa rede (a “casa”).

**Máscara de sub-rede (ex.: 255.255.255.0):** define quantos bits do endereço pertencem à rede e quantos pertencem aos hosts.

**CIDR (ex.: /24 ou /16):** é a forma simplificada de escrever essa divisão (quantos bits são reservados para a rede).

- Classe C: geralmente **/24** → 256 endereços.
- Classe B: geralmente **/16** → 65.536 endereços.

→ Você pode configurar subnets de formas diferentes

# Gateway de rede

É o meio de comunicação entre redes distintas, serve como **portal de acesso** entre as redes.

Encaminha o tráfego para outras redes (como a internet).

→ Ponte da VLAN para a internet

→ Internet Gateway é a internet usada

# Arquitetura de referência
![[Pasted image 20260909152638.png]]
