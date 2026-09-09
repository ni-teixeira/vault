---
date:
tags:
  - faculdade
  - computacao-em-nuvem
  - nuvem
  - automacao-de-testes
---
# Briefing de Infraestrutura em Nuvem e Automação de Testes

## Resumo Executivo

Este documento sintetiza as diretrizes técnicas e práticas de implementação para infraestrutura em nuvem, utilizando Terraform e AWS, e automação de testes de software. Os pontos centrais incluem a configuração de ambientes segregados (redes públicas e privadas), o provisionamento automatizado de recursos e containers, e a aplicação de frameworks de teste como Selenium para validação de sistemas. A estratégia de infraestrutura foca na segurança via Security Groups e NAT Gateways, enquanto a automação de testes abrange desde testes de unidade (caixa branca) até testes de sistema (caixa preta).

--------------------------------------------------------------------------------

## 1. Infraestrutura como Código (IaC) com Terraform

O uso do Terraform é centralizado na automação do ciclo de vida dos recursos em nuvem. A gestão é realizada através de comandos específicos e arquivos de configuração que definem o estado desejado da infraestrutura.

### Comandos Essenciais do Terraform

- `terraform init`: Inicializa o diretório de trabalho com os provedores necessários.
- `terraform apply`: Aplica as configurações para criar ou alterar a infraestrutura. O argumento `-auto-approve` pode ser utilizado para evitar a confirmação manual ("yes").
- `terraform destroy`: Remove todos os recursos gerenciados pelo Terraform.
- `terraform taint`: Utilizado para forçar a recriação de um recurso específico (ex: uma instância EC2) no próximo `apply`.

### Provedor e Configuração Global

As configurações documentadas utilizam o provedor **AWS** na região `us-east-1`, exigindo a versão do Terraform `1.2` ou superior e a versão do provedor AWS próxima a `5.92`.

--------------------------------------------------------------------------------

## 2. Arquitetura de Rede e Segurança na AWS

A arquitetura de rede é estruturada para garantir a segregação de funções e a segurança dos dados.

### Configuração de VPC e Sub-redes

A infraestrutura utiliza uma VPC com o bloco CIDR `10.0.0.0/24`. Esta rede é dividida em:

- **Sub-rede Pública:** Bloco `10.0.0.0/25`. Destinada a instâncias que precisam de acesso direto à internet via Internet Gateway.
- **Sub-rede Privada:** Bloco `10.0.0.128/25`. Onde residem instâncias sem IP público, protegendo o backend e bancos de dados.

### Conectividade e Acesso à Internet

|   |   |   |
|---|---|---|
|Recurso|Função|Observação|
|**Internet Gateway (IGW)**|Permite tráfego entre a VPC e a internet.|Essencial para a sub-rede pública.|
|**NAT Gateway**|Permite que instâncias privadas acessem a internet (ex: atualizações).|Requer um **Elastic IP** e possui custo elevado.|
|**Route Tables**|Direcionam o tráfego de saída (`0.0.0.0/0`) para o IGW ou NAT Gateway.|Associadas a sub-redes específicas.|

### Segurança e Acesso SSH

- **Security Groups:** Atuam como firewalls virtuais. O acesso SSH (porta 22) é restrito à sub-rede pública para o mundo externo, enquanto a instância privada só aceita conexões SSH originadas de dentro da própria VPC.
- **Chaves de Acesso:** Para acessar instâncias privadas, as chaves (`.pem`) devem ter permissão configurada via `chmod 400`.
- **Proxy de IP:** Utilizado para comunicação entre FrontEnd e BackEnd.

--------------------------------------------------------------------------------

## 3. Provisionamento de Instâncias EC2 e Armazenamento S3

As instâncias EC2 utilizam o tipo `t2.micro` com imagem Ubuntu (`ami-0ec10929233384c7f`).

### Automação de Provisionamento (Provisioners)

O Terraform é utilizado para configurar as instâncias após a criação:

1. **Conexão:** Via SSH com o usuário `ubuntu` e chave privada.
2. **Criação de Diretórios:** Scripts, docker e frontend são organizados remotamente.
3. **Transferência de Arquivos:** Pastas locais de scripts e docker são enviadas para a instância.
4. **Execução Remota:** Comandos para instalar dependências e iniciar containers via **Docker Compose** (ex: `docker compose -f compose-ngnix.yml up -d`).

### Armazenamento S3

- **Bucket S3:** Configurado para acesso público (`PublicReadGetObject`).
- **Políticas:** É necessário desativar as travas de "Block Public Access" e definir uma política JSON para permitir a leitura pública de objetos.
- **Custo:** A cobrança no S3 é realizada por acesso aos arquivos.

--------------------------------------------------------------------------------

## 4. Automação de Testes de Software

A validação do software é dividida por metodologias de acesso ao código e ferramentas de automação de navegador.

### Metodologias de Teste

- **Caixa Preta:** Zero acesso ao código fonte; foca na funcionalidade externa.
- **Caixa Branca:** Acesso total ao código; foca em testes unitários.
- **Caixa Cinza:** Acesso parcial ao sistema.

### Frameworks e Ferramentas

- **Selenium:** Framework de código aberto para automação de navegadores. Suporta múltiplas linguagens e permite a captura de prints de tela.
- **Playwright:** Ferramenta que segue conceitos similares ao Selenium para automação web.

### Comandos e Seletores Selenium (Python)

Para interagir com elementos web, utilizam-se diversos métodos:

- **Seletores:** `text` (conteúdo visível), `ID` ou `xpath` (padrão de caminho do elemento).
- **Ações e Verificações:**
    - `send_keys`: Digita valores em campos, mantendo o conteúdo anterior.
    - `is_displayed()`: Verifica visibilidade.
    - `is_enable`: Verifica se o elemento está habilitado.
- **Espera Explícita:** Uso de `WebDriverWait` e `expected_conditions` (EC) para aguardar a visibilidade de elementos (ex: um timeout de 5 segundos) antes de interagir.

### Configuração do WebDriver

A automação pode ser configurada para rodar em modo **Headless** (sem interface gráfica) para maior eficiência em servidores. O gerenciamento de drivers é facilitado pelo `ChromeDriverManager` (ou equivalentes para Firefox, Edge e Opera), garantindo a compatibilidade das versões do navegador.
