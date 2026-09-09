---
date:
tags:
  - faculdade
  - infraestrutura-em-nuvem
  - nuvem
  - alta-disponibilidade
---
# High Availability

É a capacidade de um sistema se manter acessível e operacional de forma continua, mesmo diante de falhas em hardware ou software.

Para garantir o HA, são utilizados sistemas de redundância, fazendo com que, se um componente falhar, o outro componente que atua paralelamente assuma sua função automaticamente.

## Como escalar a infraestrutura?

**Vertical:**

Aumenta a potência de um único servidor adicionando mais CPU, RAM ou armazenamento

→ É mais simples para um único servidor, mas tem um limite físico e pode exigir que o servidor fique indisponível para atualizações

**Horizontal:**

Adiciona mais servidores para distribuir a carga de trabalho, aumento a capacidade e a tolerância a falhas.

→ Oferece maior capacidade, escalabilidade teórica ilimitada e geralmente é mais resiliente, mas pode exigir atualizações no código para distribuir o trabalho corretamente

# Balanceamento de carga

É o processo de distribuição eficiente do tráfego de rede entre vários servidores para otimizar a disponibilidade de aplicativos e garantir uma experiência positiva paro o usuário final.

Um balanceador de carga é um dispositivo/serviço que fica entre o usuário e o grupo de servidores e atua como um facilitador invisível, garantindo que todos os servidores de recursos sejam usados igualmente.

![[Pasted image 20260909152733.png]]

![[Pasted image 20260909152746.png]]


