---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - linux
  - comandos
---
## Diretórios

**`cd`** → te leva ao diretório raiz

**`cd name`** → te leva ao diretório q vc quer

**`cd ..`** → sai de todas as pastas

**`mkdir name`** → cria um diretório

**`ls`** ou **`ls -l`** → lista tudo que esta dentro do diretório

**`rmdir name`** → deleta o diretorio vazio

**`rmdir -r name`** → deleta o diretorio com outros diretorios e arquivos dentro

## Arquivos

**`touch name.txt`** → cria um arquivo

**`nano name.txt`** → edita o arquivo (ctrl+o salva, ctrl+x fecha)

**`cat name.txt`** → printa na tela o conteúdo dentro do arquivo

**`mv name.txt dirname`** → move o arquivo

**`rm name`** → deleta o arquivo

**`cp name.txt`** → copia o arquivo para outro diretório

**`mv name.txt name2.txt`** → renomeia o arquivo

## Gerenciamento de usuários e grupos

**`id user`** → mostra o uid, gid e grupos que esse usuario esta

**`sudo adduser name`** → adiciona um usuario

**`sudo passwd name`** → troca a senha do usuario

**`sudo userdel name`** → deleta o usuario

**`su name`** → entra no usuario

**`exit`** → sai da sessao

**`sudo addgroup name`** → cria um novo grupo

**`sudo usermod -aG name username`** → adiciona um usuario a um grupo

**`sudo groupdel name`** → deleta o grupo

**`sudo gpasswd -d user grupo`** → tira o usuário de um grupo

## Permissões de arquivos e grupos

**`sudo chmod 777 name.txt`** → define as permissões do arquivo com octal, onde cada rwx é um numero em octal (7 é a permissão total, 6 é de ler e escrever apenas etc.)

**`sudo chown user:grupo name.txt`** → muda o dono ou o grupo a qual esse arquivo pertence
