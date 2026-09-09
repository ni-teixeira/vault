---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - linux
---
## Usuais

`ls:` Lista todos os arquivos do diretório (list)  
`ls-l:` Lista o tipo de arquivo e permissões  
`df`: Mostra quantidade de espaço usada no disco rígido (disk file)  
`top`: Mostra os processos consumindo memória  
`cd:` Acessa uma determinada pasta (diretório) como por exemplo cd diretório, cd.., cd /  
`mkdir:` Cria um diretório  
`rm:` Remove um arquivo/diretório (rm–r para remover de forma recursiva)  
`cat`: Abre um arquivo  
`vim:` Abre o editor vim para editar/criar arquivos

## Ajuda e documentação

`apropos`: Localiza comandos por pesquisa de palavra-chave  
`info:` Abre o explorador de informações  
`man`: Manual muito completo, pesquisa informação acerca de todos os comandos que necessitemos de saber, como por exemplo man find  
`whatis(o que é)`: Descreve o que um determinado comando é/faz  
`whereis(onde é):` Localizar a página de ajuda (man page), código fonte, ou arquivos binários, de um determinado programa

## Gestão de arquivo e diretório

`chmod:` Mudar a proteção de um arquivo ou diretório  
• r = leitura.  
• w = gravação.  
• x = execução (para arquivos) ou autorização de acesso (para diretórios).  
• u = as permissões do dono do arquivo. (user owner)*  
• g = as permissões do grupo. (group)*  
• o= as permissões dos outros usuários do sistema. (others)*  
• a = todos os usuários do sistema. (all)

`cp:` Copia arquivos, como o copy do MS-DOS  
`diff:` Compara o conteúdo de dois arquivos ASCII  
`grep:` Procura um arquivo por um padrão, sendo um filtro muito útil e usado, por exemplo um cat a.txt | grep ola irá mostrar-nos apenas as linhas do arquivo a.txt que contenham a palavra “ola” – ex: grep “texto” arquivo.txt O comando grep imprime na tela as linhas que correspondem a um padrão em cada arquivo. Um bom argumento para se utilizar (man grep) é o “-i” que ignora a distinção de letras maiúsculas e minúsculas.  
`mkdir:` Cria uma diretório, vem de make directory”  
`mv:` Move ou renomeia arquivos ou diretórios

`tar:` O 'tar' do Linux significa arquivo em fita (tape archive), que é usado para criar o  
arquivo e extrair os arquivos do arquivo. Podemos usar o comando tar do Linux para criar  
arquivos compactados ou descompactados e também mantê-los e modificá-los.  
`zip:` O comando zip compacta arquivos. Cada arquivo é compactado em um único arquivo. Se receber um arquivo como argumento, o zip compacta o arquivo e adiciona o .zip como extensão  
`sudo apt install zip zip nome_arquivo.zip arquivo1 arquivo2 arquivo3 zip –r nome_arquivo.zip diretório1 sudo apt install unzip unzip nome_arquivo.zip`

## Comandos de rede

`ip:` Manipulação do roteamento para atribuir e configurar parâmetros de rede  
`traceroute:` Identificar a rota tomada pelos pacotes para chegar ao host  
`tracepath:`Obtém a unidade de transmissão máxima ao rastrear o caminho para o host de rede  
`ping`: Frequentemente usado para verificar a conectividade entre o host e o servidor  
`ss:` Obtém detalhes sobre soquetes de rede  
`dig:` Fornece todas as informações necessárias sobre o servidor de nomes DNS  
`host:` Imprime o endereço IP de um domínio específico e vísceras  
`hostname:`Usado principalmente para imprimir e alterar o nome do host  
`curl:` Transfere dados pela rede, suportando vários protocolos

`mtr:` Uma combinação de ping e traceroute é usada para diagnosticar a rede  
`whois:` Obtém informações sobre domínios registrados, endereços IP, servidores de nomes  
`nmap:` Usado principalmente para auditar a segurança da rede speedtest-cli: Utilitário CLI de [speedtest.net](http://speedtest.net/) para verificar as velocidades da Internet

## Kill

Utilizando o terminal Linux, vamos ver como matar um ou vários processos que estão em  
funcionando na nossa máquina. O comando kill necessita de argumentos para podermos  
encerrar um processo kill –l, nos lista esses argumentos  
mansignal: nos dá o manual de sinais no Linux com a descrição de cada tipo de sinal  
`kill –nº <processo>:` aplica o sinal de kill em algum processo (9 e 15 mais comuns)

## Ccrypt

Utilizando o terminal Linux, vamos ver como proteger um arquivo usando criptografia.  
Iremos criptografar um arquivo utilizando o comando ccrypt que utiliza a cifra Rijndael, a  
mesma cifra usada na criptografia padrão AES. Embora o padrão AES use um tamanho de  
bloco de 128 bits, o ccrypt usa um tamanho de bloco de 256 bits. Uma vez criptografados  
os arquivos por ccrypt, uma extensão .cpt é adicionada aos arquivos.  
`ccrypt (nome do arquivo):` para criptografar um arquivo  
`ccrypt-c (nome do arquivo.cpt):` para ler umarquivocriptografado  
`ccrypt-d (nome do arquivo.cpt):`descriptografa um arquivo  
`ccrypt-r (nome do diretório.cpt):` criptografa um diretório e todos os arquivos  
`ccrypt–d -r (nome do arquivo.cpt):` descriptografa o diretório
