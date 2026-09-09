---
date:
tags:
  - faculdade
  - sistemas-operacionais
  - nuvem
  - armazenamento
---
# Topologias de armazenamento

❑ DAS –Direct AttachedStorage: dispositivos atachados diretamente ao computador como HD,  
SSD, HD externo e Pen Drives  
❑ NAS –Network Area Storage: é um dispositivo (aplicação) com sistema operacional próprio e  
discos com ampla capacidade de armazenamento. São conectados à rede através de uma conexão  
Ethernet padrão.  
❑ SAN –StorageArea Network:o acesso é através de uma estrutura de rede dedicada oferecendo  
flexibilidade e alto desempenho, porém maior complexidade de administração  
Uma NAS aparece para um sistema operacional cliente como um servidor de arquivos, enquanto uma  
SAN aparece como um disco e existe como sua própria rede separada de dispositivos de  
armazenamento

# Serviços de armazenamento da AWS

![[Pasted image 20260909152249.png]]

## EBS (Amazon Elatisc Block Storage)

Projetado para armazenar dados em um volume dedicado conectado a uma instância do Amazon EC2, assim como uma unidade de disco local em sua máquina física.

### Principais Características:

1. **Persistência e Velocidade**: O EBS é adequado para armazenar dados de aplicativos que exigem alta velocidade de leitura e gravação, oferecendo persistência mesmo quando a instância é desligada.
2. **Conectividade Direta:** É conectado diretamente a instâncias EC2, permitindo que o armazenamento seja tratado como um disco físico.

### S3 (Amazon S3)

Armazena dados como objetos em um ambiente simples (sem hierarquia) que são associados a um identificador único (chave), para que possam ser acessados por meio de solicitações da web de qualquer lugar. Aceita GET e POST.

## Principais Características:

1. Durabilidade e Confiabilidade: O Amazon S3 oferece uma durabilidade excepcional, tornando-o ideal para armazenar backups, arquivos estáticos, e dados críticos que precisam ser preservados a longo prazo.
2. Escalabilidade Automática: Sua capacidade de escalar automaticamente faz do S3 uma escolha sólida para armazenamento de objetos em grande escala.

# O que é um datalake?

→ Data lake é um repositório de armazenamento de dados que suporta grandes quantidades de  
dados, podendo ser estruturados e não estruturados.

→ É um repositório centralizado que ingere e armazena grandes volumes de dados em sua forma  
original. Os dados podem ser processados e usados como base para uma variedade de  
necessidades analíticas.

→ Pode acomodar todos os tipos de dados de qualquer fonte, desde dados estruturados (tabelas de  
banco de dados, planilhas do Excel) até semiestruturados (arquivos XML, páginas da Web) e não  
estruturados (imagens, arquivos de áudio, tweets)

→ Os arquivos normalmente são armazenados em zonas preparadas – raw, trusted, curated - para  
que diferentes tipos de usuários possam usar os dados em suas várias formas para atender às suas  
necessidades.

# Datalake vs Datawarehouse

→ Embora ambos armazenem dados, cada repositório tem seus próprios requisitos de  
armazenamento, o que os torna escolhas ideais para cenários diferentes.

→ Os data warehouses exigem um esquema definido para atender a requisitos específicos de análise  
de dados para saídas de dados, como dashboards, visualizações de dados e outras tarefas de  
business intelligence. Esses requisitos são geralmente especificados pelos usuários corporativos  
que utilizarão os resultados do relatório regularmente. A estrutura de um data warehouse é  
normalmente organizada como um sistema relacional, obtendo dados de bancos de dados  
transacionais.

→ Os data lakes, por outro lado, incorporam dados de sistemas relacionais e não relacionais,  
permitindo que os cientistas de dados incorporem dados estruturados e não estruturados em mais  
projetos de ciência de dados.

→ Cada sistema também tem seu próprio conjunto de vantagens e desvantagens. Por exemplo, os data warehouses tendem a ter melhor desempenho, mas têm um custo mais elevado.

→ Os data lakes podem ser mais lentos no retorno dos resultados das consultas, mas têm custos de  
armazenamento mais baixos. Além disso, a capacidade de armazenamento dos data lakes os torna  
ideais para dados corporativos.

# Desafios de um datalake

→ **Desempenho:** Conforme a quantidade de dados inseridos em um data lake aumenta, isso afeta o  
desempenho, que já é mais lento do que outros sistemas alternativos de armazenamento de dados.

→ **Governança:** Ele também requer uma forte governança para gerenciar adequadamente os dados.  
Os dados devem ser marcados e classificados com metadados relevantes para evitar pântanos de  
dados, e essas informações devem ser facilmente acessíveis por meio de um catálogo de dados,  
permitindo a funcionalidade de autoatendimento para uma equipe menos técnica, como analistas  
de negócios. Por fim, as proteções também devem ser implementadas para atender aos padrões  
regulatórios e de privacidade; isso pode incluir controles de acesso, criptografia de dados e muito  
mais.
