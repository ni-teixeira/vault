---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - aws
---
1. Realize a conexão SSH com sua EC2
    
2. Atualize os pacotes do sistema operacional com  
    `$ sudo apt update && sudo apt upgrade –y`
    
3. Instale a ferramenta AWS CLI, que serve para gerenciar a AWS console via linha de  
    comando (doc
    
    `$ curl "<https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip>" -o "awscliv2.zip" $ unzip awscliv2.zip $ sudo ./aws/install`
    
4. Utilize a instância para listar os buckets da S3 que você possui. A função IAM está  
    sendo utilizada nesse momento e podemos observar o bucket que criamos  
    `$ aws s3 ls`
    
5. Envie o arquivo para Bucket S3 com  
    `$ aws s3 cp ./nome_do_arquivo s3://nome_do_bucket/nome_do_arquivo`
    

`$ aws s3 mb s3://bucket-name` Criar um bucket  
`$ aws s3 ls s3://bucket-name` Listar buckets e objetos  
`$ aws s3 rb s3://bucket-name --force` Excluir um bucket  
`$ aws s3 rm s3://bucket-name/example/filename.txt` Excluir um arquivo  
`$ aws s3 rm s3://bucket-name/example --recursive` Excluir um diretório  
`$ aws s3 cp s3://bucket-name/file1.txt s3://my-bucket/` Copia um arquivo de um bucket a outro  
`$ aws s3 sync[--oprions]` Sincroniza o conteúdo de um bucket e/ou diretório ou entre dois buckets
