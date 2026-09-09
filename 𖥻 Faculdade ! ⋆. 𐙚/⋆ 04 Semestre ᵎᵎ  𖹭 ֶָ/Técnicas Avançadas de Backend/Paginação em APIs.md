---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - api
  - paginacao
---
## **1. A Necessidade Técnica da Paginação**

O processamento de dados em massa sem restrições de parcelamento representa um risco crítico para a estabilidade do backend. Plataformas de larga escala, como o Twitter, que processam milhares de postagens por segundo, dependem intrinsecamente deste conceito para viabilizar a exibição de dados.

### **Riscos de Consultas Abertas**

- **Sobrecarga do Servidor:** O processamento de milhares de registros simultaneamente consome memória e CPU de forma ineficiente.
- **Latência:** Respostas lentas degradam a experiência do usuário.
- **Custo Financeiro:** O tráfego e o processamento de dados redundantes geram custos desnecessários em provedores de nuvem.

---

## **2. Consistência e a Estratégia de Tiebreaker**

Para que qualquer sistema de paginação funcione, os dados **precisam ser ordenados**. A ordenação por colunas com valores repetidos (ex: nomes de usuários) pode causar inconsistências, onde a ordem dos registros muda entre requisições sucessivas.

### **O Papel do Tiebreaker**

O _Tiebreaker_ é um critério de desempate utilizado na cláusula `ORDER BY` para garantir uma ordem lógica e consistente.

- **Implementação:** Utiliza-se uma coluna de identificador único (ID, `created_at`, `updated_at`) como segundo critério de ordenação.
- **Exemplo de Consulta:** `SELECT * FROM people ORDER BY first_name, id LIMIT 10;`
- **Benefício:** Garante que o mesmo conjunto de dados retorne na mesma ordem para consultas repetidas.

---

## **3. Identificadores e Ordenação Temporal**

A escolha do tipo de identificador impacta diretamente a capacidade de ordenação do banco de dados. Nem todos os identificadores são ideais para fins de auditoria ou ordenação cronológica.

### **Comparativo de Identificadores**

|Identificador|Tamanho|Estrutura|Caso de Uso|Ordenável por Tempo?|
|---|---|---|---|---|
|**UID**|Variável|Números ou strings|Identificação geral de itens|Depende da implementação|
|**UUID v4**|36 chars|Aleatório (128 bits)|Segurança em sistemas globais|**Não**|
|**UUID v7**|36 chars|Inclui Timestamp|Sistemas que exigem ordem e segurança|**Sim**|
|**GUID**|36 chars|Padrão Microsoft|Aplicações Windows / SQL Server|Não (geralmente)|
|**CUID**|~25 chars|Timestamp + contador + digital|Sistemas distribuídos e web|**Sim**|
|**Nano ID**|~21 chars|String Base-64|IDs curtos e seguros para URLs|**Não**|

**Destaque:** O **UUID v7** é a alternativa recomendada quando se busca a segurança de um UUID com a vantagem de manter registros em ordem cronológica (time-sortable).

---

## **4. Paginação Baseada em Limit / Offset**

Este é o método mais comum, onde se utiliza um deslocamento (_offset_) para pular um número específico de registros.

- **Fórmula:** `OFFSET [tamanho] * [página - 1]`
- **Exemplo:** Página 15 com tamanho 10 resulta em `OFFSET 140`.

### **Vantagens e Desvantagens**

|Vantagens|Desvantagens|
|---|---|
|Fácil implementação.|Lenta em páginas muito distantes (lê linha a linha até o ponteiro).|
|Amplamente suportada por frameworks.|**Problema do Limbo:** Se registros forem inseridos/deletados durante a navegação, o usuário verá dados duplicados ou pulará registros.|
|**Stateless:** Requisições independentes.|Custo computacional aumenta linearmente com o deslocamento.|
|Permite acesso direto a qualquer página.||

---

## **5. Paginação Baseada em Cursor**

Diferente do deslocamento numérico, este método utiliza um marcador único (cursor) — geralmente o ID do último registro da página anterior — para ancorar a busca pelos próximos itens.

- **Lógica da Consulta:** `SELECT * FROM people WHERE id &gt; 10 ORDER BY id LIMIT 10;`
- **Codificação:** Frequentemente, o cursor é enviado ao cliente codificado em Base64 para ocultar detalhes da implementação.

### **Vantagens e Desvantagens**

|Vantagens|Desvantagens|
|---|---|
|**Alta Performance:** Escala melhor com grandes volumes de dados.|**Stateful:** Depende de guardar a posição atual para pedir a próxima.|
|**Resiliência:** Evita registros duplicados ou pulados (sem efeito de "limbo").|Difícil implementar a navegação para uma página específica (salto direto).|
|Resultados consistentes mesmo com alterações frequentes na base.|Implementação mais complexa (cursores podem ser compostos).|

---

## **Conclusão**

A escolha da técnica de paginação deve ser guiada pelo volume de dados e pela volatilidade do banco de dados. Para sistemas simples com poucos usuários, o modelo **Limit/Offset** atende pela facilidade de implementação. Contudo, para sistemas distribuídos de alta performance e grande escala (como catálogos virtuais ou redes sociais), a paginação **Cursor Based** aliada a identificadores ordenáveis (como **UUID v7** ou **CUID**) é a estratégia técnica superior para garantir consistência e escalabilidade.
