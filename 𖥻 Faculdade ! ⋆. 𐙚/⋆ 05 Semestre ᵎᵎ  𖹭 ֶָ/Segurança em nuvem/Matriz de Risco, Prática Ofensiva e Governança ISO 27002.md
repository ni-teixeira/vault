---
date:
tags:
  - faculdade
  - seguranca
  - nuvem
  - matriz-de-risco
---
# Guia de Briefing: Matriz de Risco, Prática Ofensiva e Governança ISO 27002

## Sumário Executivo

Este documento sintetiza as diretrizes para gestão de riscos cibernéticos, metodologias de análise e controles de segurança baseados na norma ISO/IEC 27002:2022. Os pontos centrais incluem:

- **Modelo de Cálculo PSR:** A avaliação de riscos é baseada no produto de Probabilidade (P), Severidade (S) e Relevância (R), permitindo uma classificação quantitativa de criticidade.
- **Vulnerabilidades Críticas em Nuvem:** A exposição pública de Buckets S3 e falhas em credenciais de API representam os riscos de maior impacto e probabilidade em ambientes de infraestrutura cloud.
- **Prática Ofensiva (Hardening):** A simulação de ataques (Reconhecimento, Injeção e Exfiltração) demonstra que a ausência de controles básicos, como validação de entrada e firewalls de rede, leva ao comprometimento total da integridade e confidencialidade dos dados.
- **Estrutura ISO 27002:** A norma estabelece uma taxonomia de controles (Organizacionais, Pessoas, Físicos e Tecnológicos) apoiada por atributos que definem o tipo de controle (Preventivo, Detectivo, Corretivo) e as propriedades de segurança (Confidencialidade, Integridade e Disponibilidade).

## 1. Metodologia de Análise de Risco (Modelo PSR)

A análise identifica vulnerabilidades em ativos tecnológicos e processos organizacionais através do cruzamento de três variáveis fundamentais, pontuadas de 1 a 5:

- **Probabilidade (P):** Grau de exposição ao risco, variando de "Rara" (P < 5%) a "Quase Certa" (P > 95%).
- **Severidade (S):** Consequência para o ativo caso a vulnerabilidade seja explorada (de "Quase não afeta" a "Afeta extremamente").
- **Relevância (R):** Grau de impacto e importância do ativo para o escopo em análise (ex: serviços que garantem a saúde da população possuem relevância máxima).

**Fórmula de Cálculo:** `PSR = P x S x R`

### Classificação de Risco e Níveis de Impacto

Conforme a Matriz de Calor, os riscos são categorizados para direcionar estratégias de correção:

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Item|Ativo / Processo|Ameaça / Vulnerabilidade|Impacto (1-5)|Prob. (1-5)|Nível de Risco|
|1|Bucket S3|Exposição pública / Vazamento de dados|5|5|25 (Crítico)|
|2|Acesso VNC/SSH|Senha padrão (urubu100) / Brute Force|4|5|20 (Alto)|
|3|Credenciais API|Chaves estáticas no script (TESTKEYID)|5|3|15 (Alto)|
|4|Logs de Sistema|Falta de centralização / Dificulta forense|3|4|12 (Médio)|
|5|Privilégios Sudo|Configuração de sudo sem restrição (ALL)|4|3|12 (Médio)|
|6|Tráfego de Rede|Comunicação via HTTP sem TLS|3|4|12 (Médio)|
|7|Software Desatualizado|Uso de Kali/Docker com CVEs conhecidas|4|2|8 (Médio)|
|8|Integridade de Disco|Ausência de hashes (MD5/SHA)|2|3|6 (Baixo)|

## 2. Prática Ofensiva e Laboratório de Segurança

O processo de exploração simulada é dividido em uma "Master Plan Sprint 1", composta por três estágios de scripts:

### Fase 1: Reconhecimento ("O que existe aqui?")

- **Ação:** Varredura de portas (Network Scan) usando `nmap -sV localstack-lab -p 4566`.
- **Conclusão:** A porta 4566 aberta revela um endpoint de serviço sem proteção de firewall.
- **Impacto:** Identificação de vulnerabilidade de exposição (Estado: Crítico).

### Fase 2: Ingestão e Envenenamento ("Vou colocar dados")

- **Ação:** Criação de buckets S3 (Raw, Trusted, Client) sem chaves de acesso.
- **Vulnerabilidade:** _Broken Access Control_ (Controle de Acesso Quebrado) e _Poisoning_.
- **Falha Identificada:** Ausência de filtros de entrada (_Input Validation_), permitindo a inserção de dados anômalos (ex: telemetria de 999.99°C).
- **Impacto:** Risco de integridade e disponibilidade (Estado: Alto).

### Fase 3: Coleta e Exfiltração ("Vou ler os dados")

- **Ação:** Execução de script automatizado para extração de conteúdo.
- **Conclusão:** Exfiltração bem-sucedida. O atacante obtém acesso total ao payload sem disparar alertas ou bloqueios.
- **Impacto:** Perda de confidencialidade (Estado: Crítico).

## 3. Estratégias de Mitigação (Hardening)

As ações corretivas são estruturadas em três pilares principais:

1. **Implementar Princípio do Menor Privilégio:**
    - Restringir comandos `sudo`.
    - Migrar chaves estáticas para tokens temporários (IAM Roles e STS).
2. **Autenticação e Criptografia:**
    - Adotar MFA (Autenticação de Múltiplos Fatores) para acessos remotos.
    - Implementar certificados SSL/TLS nos endpoints de API.
    - Alterar ACLs de buckets para _private_ e aplicar _Bucket Policies_.
3. **Gestão de Patch e Integridade:**
    - Atualizar softwares mensalmente (Patch Management).
    - Utilizar ferramentas de _Checksum_ (hashes) antes e depois da perícia para validar a integridade de arquivos.
    - Configurar centralização de logs (CloudWatch ou Syslog).

## 4. Framework ISO/IEC 27002:2022

A norma fornece um conjunto de controles genéricos de segurança da informação para serem usados no contexto de um SGSI (Sistema de Gestão de Segurança da Informação) baseado na ISO/IEC 27001.

### Definições Chave

- **Ativo:** Qualquer coisa que tenha valor para a organização (informação, processos, hardware, pessoal).
- **Ataque:** Tentativa não autorizada de destruir, alterar, desabilitar ou ganhar acesso a um ativo.
- **Controle:** Medida que mantém ou modifica o risco (processos, políticas, dispositivos, práticas).
- **Vulnerabilidade:** Fraqueza de um ativo ou controle que pode ser explorada por uma ou mais ameaças.

### Estrutura de Temas e Atributos

Os controles são categorizados em quatro temas:

- **Organizacionais (Cláusula 5):** Ex: Políticas de segurança, papéis e responsabilidades.
- **Pessoas (Cláusula 6):** Ex: Trabalho remoto, termos de emprego.
- **Físicos (Cláusula 7):** Ex: Perímetros de segurança, monitoramento físico.
- **Tecnológicos (Cláusula 8):** Ex: Autenticação segura, gerenciamento de vulnerabilidades técnicas.

#### Atributos de Controle (Exemplo: Controle 5.1 - Políticas)

|   |   |
|---|---|
|Atributo|Valor|
|**Tipo de Controle**|#Preventivo|
|**Propriedades de Segurança**|#Confidencialidade #Integridade #Disponibilidade|
|**Conceitos de Cibersegurança**|#Identificar|
|**Capacidades Operacionais**|#Governança|
|**Domínios de Segurança**|#Governança_e_Ecossistema #Resiliência|

### Governança de Políticas (Controle 5.1)

As políticas devem ser aprovadas pela gestão, publicadas, comunicadas e revisadas em intervalos planejados. A norma distingue entre:

- **Política de Segurança da Informação:** Documento de alto nível que define a abordagem da organização.
- **Políticas de Tópicos Específicos:** Detalhadas e focadas em grupos ou áreas específicas (ex: controle de acesso, criptografia, desenvolvimento seguro).