---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - gerenciamento-de-recursos
---
→ Refere-se a **técnicas para gerenciar recursos** (componentes com disponibilidade imediata)

→ **Programas podem gerenciar seus próprios recursos** usando os recursos pelas linguagens de programação ou por um host (SO ou VM)

O _**gerenciamento baseado em host**_ é conhecido como rastreamento de recursos e consiste em  
“limpar”/liberar recursos: encerrar o acesso aos recursos que foram iniciados, mas não liberados  
após o uso, ou seja, ficaram ativos, mas inoperantes

Pode-se também, esperar pelo recurso que está tomado por outro processo. E assim usá-lo por  
outro após sua finalização, denominada _**fuga de recursos**_.  
Deste modo, a _**recuperação de recursos**_ é análoga à _**coleta de registros para memória**_. Em muitos  
sistemas, o sistema operacional recupera recursos após o processo fazer a chamada do sistema  
de saída, finalizando-o.

## O que são recursos?

Os recursos dentro de um sistema computacional **são seu hardware e software**, tudo o que precisa ser referenciado em um computador para funcionar e ser utilizado pelo usuário.

Portanto, **cada um desses recursos possui funcionalidades e regras específica**s que permitem o seu gerenciamento.

### Principais recursos gerenciados pelo SO:

→ Interação entrada e saída

→ Suporte a rede

→ Gerência

→ Interface

→ Processador

→ Dispositivos

→ Memória

→ Arquivos

![[Pasted image 20260909151940.png]]

![[Pasted image 20260909151944.png]]

### Processador

→ Distribuir a capacidade de processamento entre as aplicações, evitando que uma aplicação  
monopolize seu recurso.  
→ Sincronização de processos interdependentes e prover formas de comunicação entre elas  
→ Garantir que cada processo e aplicativo recebam tempo suficiente do processador para funcionar  
corretamente;  
→ Usar quantos ciclos de processador seja possível para realizar as tarefas.

### Memória e armazenamento

→ Fornece a cada aplicação um espaço de memória próprio, independente dos demais, inclusive do  
núcleo do sistema.  
→ Caso a memória RAM não seja suficiente, o sistema provê armazenamento secundário como  
complemento de memória, de forma transparente as aplicações. (Memória Virtual - SWAP).  
→ Cada processo deve ter memória suficiente para ser executado. Ele não pode utilizar a memória de  
outro processo e outro processo também não pode utilizar a sua memória.  
Os diferentes tipos de memória no sistema devem ser bem utilizados para que cada processo seja  
executado de forma eficaz.

### Dispositivos

→ Interage com cada dispositivo por meio de drivers e cria modelos que agrupam vários dispositivos na mesma interface

→ O caminho entre o sistema operacional e todo hardware passa por um programa especial chamado driver. A função principal do driver é funcionar como tradutor entre o hardware e a linguagem de programação de alto nível do sistema operacional e dos aplicativos.

→ O funcionamento dos drivers depende do tipo de hardware, mas a maioria dos drivers é executada  
quando o dispositivo é acionado, eles funcionam de maneira semelhante a qualquer outro processo.  
O sistema operacional dá prioridade aos drivers para que o recurso do hardware seja liberado e  
disponibilizado o mais rápido possível

→ O gerenciamento de entrada/saída está relacionado com o gerenciamento das filas e buffers.

### Arquivos

→ Cria arquivos e diretórios, definindo também sua interface de acesso e as regras para seu uso  
→ Cria sistema hierárquicos de diretório  
→ Define os caminhos de acesso  
→ Implementa o sistema de arquivos para gerenciamento  
→ Cria os arquivos de journaling e cópias de segurança  
→ Permite a desfragmentação de disco
