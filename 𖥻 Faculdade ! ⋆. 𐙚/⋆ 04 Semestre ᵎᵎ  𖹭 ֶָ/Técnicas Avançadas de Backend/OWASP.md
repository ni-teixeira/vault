---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - seguranca
  - owasp-top-10
---
## **1. O Panorama da Segurança em Aplicações Web**

Na era digital, os dados são comparados ao "novo petróleo", tornando as aplicações web — a principal porta de acesso a essas informações — alvos constantes de ataques. O cenário atual é caracterizado por:

- **Vulnerabilidades Críticas:** APIs expostas, validações frágeis e controles de acesso mal implementados são as principais causas de prejuízos milionários.
- **A Origem das Falhas:** Surpreendentemente, grande parte das brechas de segurança decorre de erros conhecidos e antigos.
- **Impacto Estatístico:**
    - **25% dos vazamentos de dados** são causados diretamente por vulnerabilidades em softwares e APIs.
    - **72% dessas falhas** são resultantes de erros simples de codificação.

### **Consequências Reais**

Os impactos de um incidente de segurança são imediatos e severos, incluindo a perda de dados confidenciais (clientes, parceiros e funcionários), danos à reputação da marca, perda de confiança e multas regulatórias severas, como as previstas pela LGPD.

---

## **2. Casos Reais de Prejuízos por Falhas (2021-2023)**

O documento apresenta evidências de como falhas listadas pelo OWASP afetaram grandes corporações globalmente:

|Ano|Empresa|Falha (OWASP ID)|Impacto|
|---|---|---|---|
|2023|MOVEit (Progress)|Injeção SQL (A03)|Vazamento de dados de mais de 15 milhões de pessoas (Ataque global).|
|2023|ResumeLooters|SQL Injection + XSS (A03 + A07)|Mais de 2 milhões de registros roubados e vendidos na dark web.|
|2022|Optus (Austrália)|Controle de Acesso Quebrado (A01)|Dados de 10 milhões de clientes; resultou em multas e CPI no Senado.|
|2021|T-Mobile (EUA)|Várias (Injeção e falhas lógicas)|76 milhões de afetados; acordo de US$ 350 milhões com as vítimas.|

---

## **3. OWASP: Referência Mundial em Segurança**

O **OWASP (Open Worldwide Application Security Project)** é uma comunidade global sem fins lucrativos dedicada à segurança de aplicações. Suas principais missões são:

- Promover boas práticas de desenvolvimento seguro.
- Auxiliar empresas e profissionais a identificar e corrigir vulnerabilidades.

O trabalho de maior destaque da organização é o **OWASP Top 10**, uma lista revisada regularmente que cataloga as dez falhas de segurança mais comuns e críticas em aplicações web.

---

## **4. Análise Detalhada do OWASP Top 10 (Versão 2021)**

Abaixo, detalham-se as categorias de risco que compõem a referência atual:

1. **Quebra de Controle de Acesso (Broken Access Control):** Restrições de acesso mal aplicadas permitem que usuários acessem dados ou funções sem permissão. _Exemplos: escalada de privilégios e manipulação de URLs._
2. **Falhas Criptográficas (Cryptographic Failures):** Dados sensíveis expostos por falta de criptografia adequada ou uso de algoritmos fracos. _Exemplos: senhas em texto claro e falta de HTTPS._
3. **Injeção (Injection):** Dados maliciosos enviados pelo usuário são interpretados como comandos pelo sistema. _Exemplos: SQL Injection e Cross-site Scripting (XSS)._
4. **Design Inseguro (Insecure Design):** Falhas na arquitetura que não consideram segurança desde o início. _Exemplo: redefinição de senha apenas por e-mail, sem MFA._
5. **Configuração Incorreta de Segurança (Security Misconfiguration):** Sistemas com configurações padrão, arquivos expostos ou painéis de administração acessíveis. _Exemplo: arquivos .env expostos._
6. **Componentes Vulneráveis e Desatualizados:** Uso de frameworks ou bibliotecas (como jQuery ou Log4j) com vulnerabilidades conhecidas e sem atualização.
7. **Falhas de Identificação e Autenticação:** Problemas como senhas fracas, tokens (JWT) sem expiração e ausência de autenticação multifator (MFA).
8. **Falhas na Integridade de Software e Dados:** Suposições inseguras sobre atualizações e pipelines de CI/CD. _Exemplo: uso de bibliotecas de fontes não confiáveis._
9. **Falhas de Log e Monitoramento de Segurança:** Falta de visibilidade que dificulta a detecção de incidentes e investigações forenses.
10. **Falsificação de Requisições no Lado do Servidor (SSRF):** O servidor é induzido a fazer requisições para destinos internos ou protegidos.

### **Evolução e Tendências**

O documento destaca a transição entre as versões de 2017 e 2021, observando a consolidação de certas falhas em novas categorias. Uma nova atualização do Top 10 estava prevista para o final de **2025**.

---

## **5. Ética e Responsabilidade Profissional**

O uso de ferramentas de segurança exige um compromisso ético inegociável. O documento estabelece diretrizes rigorosas:

- **Ambientes Autorizados:** Ferramentas de _pentest_, _sniffers_ ou escaneamento de rede **não devem** ser usadas fora de ambientes com permissão explícita.
- **Consequências do Uso Indevido:** O uso não autorizado pode resultar em demissão, processos judiciais e prisão.
- **Segurança Digital:** Exige ética e responsabilidade; testes só devem ser executados onde houver autorização prévia.

---

## **6. Protocolo para Relatório de Segurança**

Para a mitigação eficaz de riscos em projetos, propõe-se um fluxo de trabalho estruturado para a geração de evidências e correções:

- **Análise de Projeto:** Identificar riscos relacionados aos itens do Top 10, buscando ao menos **quatro vulnerabilidades** relevantes para avaliação.
- **Garantia de Correção:** Implementar boas práticas e correções, demonstrando como a solução adotada resolve o problema identificado.
- **Geração de Evidências:** Compilar um relatório detalhado contendo:
    - Resultados da análise.
    - Trechos de código corrigidos.
    - _Screenshots_ (prints) e logs.
    - Descrições claras das estratégias de mitigação aplicadas.
