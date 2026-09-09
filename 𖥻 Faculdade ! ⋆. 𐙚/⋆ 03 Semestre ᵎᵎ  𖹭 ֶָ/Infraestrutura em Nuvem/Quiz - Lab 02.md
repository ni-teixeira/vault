---
date:
tags:
  - faculdade
  - infraestrutura-em-nuvem
  - nuvem
  - vpc-aws
---
1. Escolha a opção correta sobre a criação de Subnets em uma VPC:

- [x] a. Cada Subnet em uma VPC deve estar associada a uma única zona de disponibilidade (Availability Zone)
    
- [ ] b. Subnets podem abranger várias zonas de disponibilidade
    
- [ ] c. Subnets são criadas automaticamente ao criar uma VPC
    
- [ ] d. Não há limite para o número de Subnets que podem ser criadas em uma VPC
    
- Resposta:
    
    a. Cada Subnet em uma VPC deve estar associada a uma única zona de disponibilidade (Availability Zone)
    

1. Em um ambiente AWS, qual componente é responsável por direcionar o tráfego de rede para fora da VPC?

- [x] a. Internet Gateway
    
- [ ] b. Security Group
    
- [ ] c. Network ACL
    
- [ ] d. Route Table
    
- Resposta:
    
    a. Internet Gateway
    

1. Qual das seguintes opções NÃO é um componente de uma VPC?

- [ ] a. Route Tables
    
- [x] b. Auto Scaling Group
    
- [ ] c. Subnets
    
- [ ] d. Security Groups
    
- Resposta:
    
    b. Auto Scaling Group
    

1. Marque a opção correta sobre o que define uma Subnet como pública ou privada:

- [x] a. Se a Subnet está associada a um Internet Gateway
    
- [ ] b. Se a Subnet contém um serviço de banco de dados
    
- [ ] c. Se a Subnet possui um NAT Gateway
    
- [ ] d. Se a Subnet está configurada para um serviço de cache
    
- Resposta:
    
    a. Se a Subnet está associada a um Internet Gateway
    

1. Qual é o propósito de um Security Group em uma VPC?

- [ ] a. Gerenciar a atribuição de endereços IP públicos
    
- [ ] b. Armazenar logs de acesso de rede
    
- [ ] c. Definir políticas de backup para instâncias EC2
    
- [x] d. Controlar o tráfego de entrada e saída para instâncias dentro da VPC
    
- Reposta:
    
    d. Controlar o tráfego de entrada e saída para instâncias dentro da VPC
    

1. O que ocorre se uma tabela de rotas associada a uma sub-rede pública não tiver uma rota para 0.0.0.0/0?

- [ ] a. As instâncias dentro da sub-rede não conseguirão acessar a internet
    
- [ ] b. A AWS adicionará automaticamente uma rota padrão para corrigir o problema
    
- [ ] c. Apenas tráfego de entrada será bloqueado, mas o tráfego de saída continuará funcionando
    
- [ ] d. As instâncias continuarão acessando a internet se tiverem IPs públicos
    
- Resposta:
    
    a. As instâncias dentro da sub-rede não conseguirão acessar a internet
    

1. Um Security Group em uma VPC é:

- [ ] a. Um conjunto de regras que controlam o tráfego de entrada e saída para recursos na VPC
    
- [ ] b. Um serviço de monitoramento de segurança de rede
    
- [ ] c. Uma ferramenta para configurar VPNs na VPC
    
- [ ] d. Um método para conectar subnets privadas à Internet
    
- Resposta:
    
    a. Um conjunto de regras que controlam o tráfego de entrada e saída para recursos na VPC
    

1. Marque a opção correta:

- [ ] a. Cada subnet deve estar associada a uma única zona de disponibilidade
    
- [ ] b. Uma subnet pode abranger várias zonas de disponibilidade
    
- [ ] c. As subnets são automaticamente distribuídas em todas as zonas de disponibilidade
    
- [ ] d. Subnets não estão relacionadas às zonas de disponibilidade
    
- Resposta:
    
    a. Cada subnet deve estar associada a uma única zona de disponibilidade
    

1. Qual é a principal função do Internet Gateway em uma VPC na AWS?

- [ ] a. Definir rotas privadas dentro da VPC
    
- [ ] b. Filtrar tráfego de entrada e saída para instâncias EC2
    
- [ ] c. Permitir a comunicação entre a VPC e a internet
    
- [ ] d. Criar sub-redes adicionais dentro da VPC
    
- Resposta:
    
    c. Permitir a comunicação entre a VPC e a internet
    

1. Qual das opções abaixo é um requisito para que uma instância EC2 possa acessar a internet?

- [ ] a. Ser associada a uma Network ACL personalizada
    
- [ ] b. Estar associada a uma Route Table com uma rota apontando para um Internet Gateway
    
- [ ] c. Ter um endereço IP privado alocado manualmente
    
- [ ] d. Utilizar um Elastic Load Balancer configurado na sub-rede privada
    
- Resposta:
    
    b. Estar associada a uma Route Table com uma rota apontando para um Internet Gateway
    

1. É possível associar múltiplas Route Tables a uma única subnet?

- [ ] a. Não, Route Tables são apenas para instâncias EC2
    
- [ ] b. Sim, em qualquer tipo de subnet
    
- [ ] c. Sim, mas apenas em subnets públicas
    
- [ ] d. Não, uma subnet pode ter apenas uma Route Table associada
    
- Resposta:
    
    d. Não, uma subnet pode ter apenas uma Route Table associada
    

1. Um Internet Gateway em uma VPC é:

- [ ] a. Um componente que permite a comunicação entre a VPC e a Internet
    
- [ ] b. Uma conexão privada entre uma VPC e outra rede
    
- [ ] c. Um serviço de armazenamento de dados
    
- [ ] d. Uma ferramenta para gerenciar logs de rede
    
- Resposta:
    
    a. Um componente que permite a comunicação entre a VPC e a Internet
    

1. Qual das seguintes opções descreve corretamente a relação entre uma VPC e uma subnet na AWS?

- [ ] a. Uma subnet pode abranger múltiplas VPCs
    
- [ ] b. Uma VPC é uma divisão lógica de uma subnet
    
- [ ] c. Uma subnet pode ser criada sem estar associada a uma VPC
    
- [ ] d. Uma VPC pode conter múltiplas subnets, cada uma em uma faixa de CIDR específica
    
- Resposta:
    
    d. Uma VPC pode conter múltiplas subnets, cada uma em uma faixa de CIDR específica
    

1. Quais tipos de subnets geralmente são usadas para hospedar instâncias de banco de dados em uma VPC?

- [ ] a. Subnets públicas
    
- [ ] b. Subnets NAT
    
- [ ] c. Subnets de alta disponibilidade
    
- [ ] d. Subnets privadas
    
- Resposta:
    
    d. Subnets privadas
    

1. Marque a opção correta:

- [ ] a. Security Groups funcionam no nível de instância, enquanto ACLs funcionam no nível de subnet
    
- [ ] b. Security Groups controlam o tráfego de entrada e saída em subnets, enquanto ACLs controlam o tráfego em instâncias específicas
    
- [ ] c. Security Groups são específicos para VPC, enquanto ACLs podem ser usados em várias VPCs
    
- [ ] d. Security Groups são baseados em regras de negação, enquanto ACLs são baseados em regras de permissão
    
- Resposta:
    
    a. Security Groups funcionam no nível de instância, enquanto ACLs funcionam no nível de subnet
    

1. Como uma Route Table determina para onde enviar pacotes dentro de uma VPC?

- [ ] a. Direcionando pacotes exclusivamente para outras instâncias dentro da mesma sub-rede
    
- [ ] b. Utilizando um DNS interno da AWS que redireciona automaticamente os pacotes
    
- [ ] c. Por meio de um conjunto de regras que definem destinos e alvos específicos
    
- [ ] d. Através da configuração automática de peering entre sub-redes
    
- Resposta:
    
    c. Por meio de um conjunto de regras que definem destinos e alvos específicos
    

1. Como uma Route Table pode ser utilizada para controlar o tráfego entre sub-redes dentro de uma mesma VPC?

- [ ] a. Aplicando regras de firewall diretamente dentro da Route Table
    
- [ ] b. Associando uma Network ACL a cada rota criada na tabela
    
- [ ] c. Criando rotas específicas direcionando o tráfego de uma sub-rede para outra
    
- [ ] d. Configurando um Internet Gateway para permitir comunicação entre sub-redes
    
- Resposta:
    
    c. Criando rotas específicas direcionando o tráfego de uma sub-rede para outra
    

1. Qual é o propósito principal de uma VPC?

- [ ] a. Criar uma rede privada na nuvem para isolar recursos
    
- [ ] b. Armazenar arquivos grandes
    
- [ ] c. Automatizar backups de banco de dados
    
- [ ] d. Gerenciar usuários e permissões
    
- Resposta:
    
    a. Criar uma rede privada na nuvem para isolar recursos
    

1. Qual é a vantagem de dividir uma VPC em várias subnets

- [ ] a. Aumento da capacidade de armazenamento
    
- [ ] b. Maior velocidade de processamento
    
- [ ] c. Melhor controle sobre o tráfego de rede e segurança
    
- [ ] d. Redução dos custos de manutenção
    
- Resposta:
    
    c. Melhor controle sobre o tráfego de rede e segurança
    

1. O que define se uma instância EC2 recebe automaticamente um endereço IPv4 público ao ser criada?

- [ ] a. A escolha de um AMI (Amazon Machine Image) que tenha suporte a IP público
- [ ] b. A configuração do atributo "atribuição automática do endereço IPv4 público" na sub-rede
- [ ] c. O uso de um Elastic Load Balancer associado à instância
- [ ] d. A presença de um NAT Gateway na sub-rede
- Resposta:
    - [ ] b. A configuração do atributo "atribuição automática do endereço IPv4 público" na sub-rede

1. O que acontece se uma instância EC2 for criada em uma sub-rede pública sem um endereço IP público atribuído?

- [ ] a. A instância não poderá acessar a internet nem receber tráfego externo
- [ ] b. A instância poderá ser acessada via SSH apenas por outras instâncias dentro da VPC
- [ ] c. A instância terá um IP público atribuído automaticamente pela AWS
- [ ] d. A instância poderá acessar a internet, mas não poderá receber tráfego externo
- Resposta:
    - [ ] a. A instância não poderá acessar a internet nem receber tráfego externo

1. O que acontece se uma Route Table em uma VPC não tiver uma rota definida para um determinado destino?

- [ ] a. O tráfego será descartado
- [ ] b. O tráfego será automaticamente roteado internamente na VPC
- [ ] c. O tráfego será redirecionado para o roteador principal da VPC
- [ ] d. O tráfego será enviado para a internet
- Resposta:
    - [ ] a. O tráfego será descartado

1. Ao criar uma subnet, você pode especificar:

- [ ] a. O CIDR Block e a zona de disponibilidade
    
- [ ] b. Apenas o nome da subnet
    
- [ ] c. Apenas a zona de disponibilidade
    
- [ ] d. Apenas o CIDR Block
    
- Resposta:
    
    a. O CIDR Block e a zona de disponibilidade
    

24. Qual das opções abaixo é verdadeira sobre a relação entre Internet Gateway e Route Table?

- [ ] a. O Internet Gateway adiciona automaticamente uma rota na Route Table para permitir acesso à internet
- [ ] b. A Route Table deve conter uma rota apontando para o Internet Gateway para permitir tráfego externo
- [ ] c. O Internet Gateway pode ser associado diretamente a uma instância EC2 sem necessidade de uma Route Table
- [ ] d. Uma Route Table pública pode funcionar sem um Internet Gateway se houver um NAT Gateway na VPC
- Resposta:
    - [ ] b. A Route Table deve conter uma rota apontando para o Internet Gateway para permitir tráfego externo

25. Qual é a finalidade de uma Route Table em uma VPC?

- [ ] a. Gerenciar permissões de usuário
- [ ] b. Controlar a criação de subnets
- [ ] c. Definir como o tráfego é roteado entre subnets e outros destinos
- [ ] d. Armazenar logs de eventos de rede
- Resposta:
    - [ ] c. Definir como o tráfego é roteado entre subnets e outros destinos

26. Uma VPC na AWS é:

- [ ] a. Uma rede virtual que permite o provisionamento de recursos em um ambiente de nuvem isolado
- [ ] b. Um serviço para armazenamento de objetos na nuvem
- [ ] c. Uma ferramenta para gestão de identidades
- [ ] d. Um serviço de banco de dados relacional
- Resposta:
    - [ ] a. Uma rede virtual que permite o provisionamento de recursos em um ambiente de nuvem isolado

27. O que acontece se você remover o Internet Gateway de uma VPC que possui instâncias configuradas para acesso à internet?

- [ ] a. A AWS criará automaticamente um novo Internet Gateway para substituir o removido
- [ ] b. Todas as instâncias perderão a conectividade com a internet imediatamente
- [ ] c. O tráfego de saída será bloqueado, mas as instâncias ainda poderão receber conexões externas
- [ ] d. O tráfego de saída continuará funcionando se as instâncias estiverem em uma sub-rede pública
- Resposta:
    - [ ] b. Todas as instâncias perderão a conectividade com a internet imediatamente

28. Como você aumentaria o espaço de endereçamento IP em uma VPC existente?

- [ ] a. Associando uma nova faixa de CIDR à VPC
    
- [ ] b. Redimensionando instâncias EC2
    
- [ ] c. Alterando a máscara de rede de subnets existentes
    
- [ ] d. Criando novas subnets
    
- Resposta:
    
    a. Associando uma nova faixa de CIDR à VPC
    

29. Se você tentar criar uma subnet com um CIDR Block que se sobrepõe a outra subnet na mesma VPC:

- [ ] a. A criação da subnet falhará
    
- [ ] b. O CIDR Block será ajustado automaticamente
    
- [ ] c. A subnet será criada com sucesso
    
- [ ] d. O CIDR Block será alterado para evitar a sobreposição
    
- Resposta:
    
    a. A criação da subnet falhará
    

30. A principal função de uma Subnet dentro de uma VPC é:

- [ ] a. Dividir uma VPC em segmentos menores de rede
    
- [ ] b. Armazenar dados de backup
    
- [ ] c. Gerenciar permissões de usuário
    
- [ ] d. Monitorar logs de rede
    
- Resposta:
    
    a. Dividir uma VPC em segmentos menores de rede
