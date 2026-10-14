---
date: 2026-10-13
tags:
  - "#faculdade"
---
# O Sistema de Ingestão e a Camada Bronze: Capturando o Dado Bruto
Imagine um porto movimentado onde navios de diferentes partes do mundo descarregam contêineres sem qualquer padronização prévia. 

No ecossistema de dados, o subsistema **Data Ingestion** (Ingestão de Dados) atua exatamente como esse ponto de entrada universal.

![[Pasted image 20261013235419.png]]

Em nossa arquitetura, temos duas fontes principais de dados:
- **IoT Azure**: Uma nuvem especializada na coleta de dados telemétricos e eventos de dispositivos inteligentes em tempo real.
- **External data**: Servidores e sistemas externos que fornecem dados operacionais e arquivos de sistemas legados ou terceiros.

Ambas as fontes enviam suas informações diretamente para o repositório **Bronze**, localizado na **AWS Cloud**.

A camada **Bronze** representa o estágio inicial da arquitetura de dados (conhecida como _Medallion Architecture_). Sua principal função é armazenar os dados em seu estado bruto (_raw data_), exatamente como foram gerados. Não há preocupação imediata com limpeza ou transformação; a meta é garantir velocidade na captura e manter um histórico completo para auditorias futuras.

---
# A Camada de Integração: VPC, PySpark e a Refinação de Dados
Como transformar o volume bruto armazenado na camada Bronze em dados refinados de alto valor? É aqui que entra o subsistema **Data Integration** (Integração de Dados).

Toda a etapa de processamento ocorre em um ambiente isolado e controlado dentro da **AWS Cloud**:
- **VPC (Virtual Private Cloud)**: Definida no bloco CIDR `10.100.0.0/21`, garantindo isolamento lógico de rede.
- **Public subnet (Sub-rede Pública)**: Endereçada como `10.100.1.0/24`, onde reside a infraestrutura de computação.
- **Instância EC2**: Hospeda o motor de processamento distribuído **PySpark**.

O **PySpark** atua como uma refinaria central de dados, executando um fluxo em três etapas essenciais:
1. **Leitura**: O PySpark consome os dados brutos diretamente do bucket **Bronze**.
2. **Tratamento e Padronização**: Os dados são limpos, filtrados e estruturados, sendo gravados no repositório **Silver**.
3. **Enriquecimento e Agregação**: O PySpark aplica regras de negócio e agregações complexas sobre os dados da camada Silver, gerando a camada **Gold** — o nível mais alto de refinação, pronto para consumo por dashboards de Business Intelligence (BI) e modelos de Machine Learning.


