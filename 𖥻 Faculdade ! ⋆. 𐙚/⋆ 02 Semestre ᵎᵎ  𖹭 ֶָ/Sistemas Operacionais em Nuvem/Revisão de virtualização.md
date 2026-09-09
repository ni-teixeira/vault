---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - virtualizacao
---
### Kernel:

→ Coração do sistema operacional. Gerencia os recursos do hardware.

### Shell:

→ Atua como uma interface entre o usuário e o kernel. Interpreta os comandos e os traduz para o kernel executar.

### Comandos:

→ Comandos que o usuário digita no terminal, são processados pelo shell, que interage com o kernel para executar as operações.

## Arquitetura de um SO:

→ A forma como os componentes do SO são interligados e se relacionam varia

Essencialmente, gerenciamos 4 atributos principais:

- Memória RAM
- Processamento
- Armazenamento
- Rede

## Como funciona o hypervisor?

→ O hypervisor gerencia os recursos físicos do host para que as maquinas virtuais possam utiliza-los

### Tipos de hypervisor

### Tipo 01

**Acesso direto aos recursos do hardware.** O host não tem um SO instalado em uma configuração de hypervisor bare-metal. **Seu software atua como um SO leve.** É comum em data-centers e ambientes de servidores

→ Alta eficiência

→ Gerencia e aloca recursos direto para a vm

→ Não depende do SO host

→ Eficiência, escalabilidade e flexibilidade

→ Seguro e estável

### Tipo 02

**Programa de hypervisor instalado no SO do host.** Conhecido como hospedado ou integrado. **Esse tipo não tem controle completo dos recursos** do programador. O administrador do sistema aloca os recursos para o hypervisor que distribui para as vms.

→ Depende de um SO host

→ Latência ao ambiente

→ Não tem acesso ao hardware, solicita ao SO host

→ Facilidade ao instalar, configurar e operar

→ Flexibilidade depende do SO host

## Máquinas virtuais

→ Ambientes virtuais que simulam um computador físico em forma de software

→ Compreendem vários arquivos contendo a configuração da VM, armazenamento para o disco rígido virtual e capturas da vm para preservar seu estado
