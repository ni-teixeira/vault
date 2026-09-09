---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - linux
---
### **Monitoramento e informação**

`df`

Exibe informações sobre o uso do sistema de arquivos.  
Exemplo: df -h (exibe o uso do sistema de arquivos em formato legível por humanos).

`du`

Estima o uso de espaço em disco por arquivos e diretórios.  
Exemplo: du -sh /path/to/directory (exibe o uso total de espaço de /path/to/directory em  
formato legível por humanos).

`lsblk`

Lista informações sobre dispositivos de bloco e partições.  
Exemplo: lsblk (exibe uma lista dos dispositivos de bloco e suas partições).

`mount`

Exibe os sistemas de arquivos atualmente montados.  
Exemplo: mount (mostra todos os sistemas de arquivos montados no momento)

`stat`

Exibe informações detalhadas sobre arquivos e sistemas de arquivos.  
Exemplo: stat /path/to/file (mostra detalhes sobre o arquivo ou diretório especificado).

`ls -l`

Exibe detalhes sobre arquivos e diretórios, incluindo permissões e informações de sistema  
de arquivos.  
Exemplo: ls -l /path/to/directory (mostra informações detalhadas sobre os arquivos e  
diretórios em /path/to/directory).

`findmnt`

Exibe uma lista dos sistemas de arquivos montados ou monta pontos.  
Exemplo: findmnt (mostra a árvore de sistemas de arquivos montados).

`xfs_info`

Exibe informações sobre sistemas de arquivos XFS.  
Exemplo: sudo xfs_info /mnt (mostra informações sobre o sistema de arquivos XFS montado em /mnt)

### **Gerenciamento**

`mkfs`

Cria um sistema de arquivos em uma partição ou disco.  
Exemplo: sudo mkfs.ext4 /dev/sdX1 (cria um sistema de arquivos ext4 em /dev/sdX1).

`fsck`

Verifica e corrige erros no sistema de arquivos.  
Exemplo: sudo fsck /dev/sdX1 (verifica o sistema de arquivos em /dev/sdX1).

`mount`

Monta um sistema de arquivos em um ponto de montagem.  
Exemplo: sudo mount /dev/sdX1 /mnt (monta /dev/sdX1 em /mnt).

`umount`

Desmonta um sistema de arquivos.  
Exemplo: sudo umount /mnt (desmonta o sistema de arquivos montado em /mnt).

`tune2fs`

Ajusta parâmetros de sistemas de arquivos ext2/ext3/ext4.  
Exemplo: sudo tune2fs -l /dev/sdX1 (exibe informações sobre o sistema de arquivos ext2/ext3/ext4 em /dev/sdX1)

`resize2fs`

Redimensiona sistemas de arquivos ext2/ext3/ext4.  
Exemplo: sudo resize2fs /dev/sdX1 (redimensiona o sistema de arquivos ext2/ext3/ext4  
em /dev/sdX1).

`e2fsck`

Ferramenta de verificação e reparo para sistemas de arquivos ext2/ext3/ext4.  
Exemplo: sudo e2fsck -f /dev/sdX1 (força a verificação do sistema de arquivos ext2/ext3/ext4 em /dev/sdX1).

`mkswap`

Cria uma área de troca (swap) em uma partição ou arquivo.  
Exemplo: sudo mkswap /dev/sdX2 (cria uma partição de swap em /dev/sdX2).

`swapon`

Ativa uma partição ou arquivo de swap.  
Exemplo: sudo swapon /dev/sdX2 (ativa a partição de swap em /dev/sdX2).

`swapoff`

Desativa uma partição ou arquivo de swap.  
Exemplo: sudo swapoff /dev/sdX2 (desativa a partição de swap em /dev/sdX2)
