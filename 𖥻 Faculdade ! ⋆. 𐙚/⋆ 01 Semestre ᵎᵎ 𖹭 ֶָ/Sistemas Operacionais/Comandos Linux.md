---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - linux
  - comandos
---

```jsx
**lsb_release -a** *(ver a versão que vc ta)*
**ls** *(listar as pastas, mostra tudo que estiver lá dentro)

**Diretorios e arquivos:***
**cd** [nome da pasta] *(entrar na pasta)*
**mkdir** [nome da pasta] *(criar pasta)
pwd comprova o caminho que voce ta*

**touch** [nome do arquivo] *(criar arquivos)*
**nano** [nome do arquivo] *(criar e editar arquivos)*
**cat** [nome do arquivo] *(ver o que tem dentro da pasta)*

**df -h** mostra o espaço disponível no disco.

**mv** [nome do arquivo] [nome da pasta]/ *(para mover o arquivo)*
**ls** [nome da pasta]/
**cd** [nome da pasta]/
**cd ..** é usado para navegar para o diretório pai do atual
**rm -r** [nome da pasta]/
**cd /home** vai para o diretório /home
**rm nomedodir/nomedoarq** excluir arquivos e dir (eh ruim usar isso pra excluir dir, nao e boa pratica)
**rmdir nomedodir/** exclui diretorio VAZIO
**rm -r nomedodir/** excluir dir com todos os arquivos nel

***Criar um usuário:***

**sudo**
**sudo adduser [nome]**
*criar senha*
**su [user]** *(para trocar de usuario)*
**sudo passwrd** *(para trocar a senha do usuario)*
**exit** *(para sair do usuário)*
**sudo deluser nomedousuario** *apaga o usuario, nao exclui tds as coisas*
**sudo deluser -r nomedousuario**  *apaga o usuario com tds as coisas*
**sudo rm -rf /caminho/caminho/** *tomar cuidado pq pode apagar todo seu so → faz a msm coisa q o comando anterior*

***Monitoramento de recursos:***
top : monitoramento de processos e recursos
```