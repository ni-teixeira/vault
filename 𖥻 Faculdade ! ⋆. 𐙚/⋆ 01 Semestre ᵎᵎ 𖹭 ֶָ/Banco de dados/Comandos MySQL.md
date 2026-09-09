---
date:
tags:
  - faculdade
  - banco-de-dados
  - sql
  - comandos-mysql
---
**CREATE DATABASE …**

Criar um novo banco de dados

**USE …**

Usar o banco de dados criado ou de sua preferencia

**CREATE TABLE …**

Criar a tabela com o nome

```sql
CREATE TABLE Atleta(
idAtleta INT PRIMARY KEY,
nome varchar(40),
modalidade varchar(40),
qtdMedalha INT
);
```

**INSERT INTO … VALUES**

Inserir dentro da tabela criada os valores que você quiser definir, deixar na ordem das colunas criadas na tabela

```sql
INSERT INTO Atleta VALUES
	(102030, 'Amanda', 'Natação', 2),
    (112030, 'Gabriella', 'Ginastica Artistica', 2),
    (122030, 'Vinicius', 'Judo', 2),
    (132030, 'Laiza', 'Esgrima', 3),
    (142030, 'Laysa', 'Surfe', 2);
```

**SELECT … FROM …**

Para selecionar e mostrar toda a tabela, precisa usar SELECT *

Para demonstrar somente a coluna de um campo, precisa usar SELECT …

Para mostrar a tabela de forma ordenada, só utilizar o ORDER BY

Para mostrar de forma ordenada, só utilizar o ORDER BY desc

Também pode ser mostrada ordenada por alguma coluna, como ORDER BY …

```sql
-- exibir todos os dados da tabela
SELECT * FROM Atleta;

-- exibir apenas os nomes e quantidade de medalhas
SELECT nome, qtdMedalha FROM Atleta;

-- exibir apenas os dados de um atleta de certa modalidade
SELECT * FROM Atleta
	WHERE modalidade = 'Esgrima';
    
-- exibir os dados da tabela ordenados por modalidade
SELECT * FROM Atleta ORDER BY modalidade;

-- Exibir os dados da tabela, ordenados pela quantidade de medalhas, em ordem decrescente.
SELECT * FROM Atleta ORDER BY qtdMedalha desc;
```

**WHERE … LIKE …**

Tem possibilidade de utilizar para exibir somente os dados da tabela que tenham uma condição

Pode se usar % para ignorar o restante da condição e deixar só o que importa

Pode se usar _ para ignorar somente 1 caractere

```sql
-- Exibir os dados da tabela, dos atletas cujo nome contenha a letra s
SELECT * FROM Atleta
	WHERE nome LIKE '%s%';
    
-- Exibir os dados da tabela, dos atletas cujo nome comece com uma determinada letra.
SELECT * FROM Atleta
	WHERE nome LIKE 'A%';
    
-- Exibir os dados da tabela, dos atletas cujo nome termine com a letra o.
SELECT * FROM Atleta
	WHERE nome LIKE '%o';
    
-- Exibir os dados da tabela, dos atletas cujo nome tenha a penúltima letra r.
SELECT * FROM Atleta
	WHERE nome LIKE '%r_';
```

Para ser algo diferente usamos **<> ou NOT LIKE.**

**DROP TABLE**

Excluir a tabela

**DESCRIBE …**

Descrever todas as colunas criadas na tabela

**AUTO_INCREMENT**

Faz o número ser incrementado com um número a mais do que o anterior

```sql
CREATE TABLE Revista(
	idrevista int primary key auto_increment,
	nome varchar(40),
	categoria varchar(30)
);
```

**Variação:**

Para começar de determinado número:

```sql
CREATE TABLE Revista(
	idrevista int primary key auto_increment,
	nome varchar(40),
	categoria varchar(30)
); auto_increment(10)
```

**VARCHAR E CHAR**

CHAR() você define um número fixo de caracteres e VARCHAR() os caracteres podem se alterar entre o numero definido

**DEFAULT**

Quando se tem o auto_increment, precisa por default no valor da tabela para que o auto_increment crie o número automaticamente.

```sql
INSERT INTO Revista VALUES
	(default, 'Vogue', null),
	(default, 'Wired', null),
	(default, 'Claudia Cozinha', null),
	(default, 'National Geographic', null),
	(default, 'Superinteressante', null);    
```

**NULL**

No valor da tabela conta como um valor nulo que o banco de dados não irá preencher

```sql
INSERT INTO Revista VALUES
	(default, 'Vogue', null),
	(default, 'Wired', null),
	(default, 'Claudia Cozinha', null),
	(default, 'National Geographic', null),
	(default, 'Superinteressante', null);    
```

**UPDATE … SET … WHERE …**

UPDATE é um comando serve pra atualizar a tabela com os dados que você precisa.

SET serve pra definir o que iremos atualizar

WHERE nos definimos onde e qual o local que será alterado

```sql
UPDATE Revista SET categoria = 'Moda' WHERE idRevista = 1;
UPDATE Revista SET categoria = 'Tecnologia' WHERE idRevista = 2;
UPDATE Revista SET categoria = 'Receitas' WHERE idRevista = 3;
UPDATE Revista SET categoria = 'Geografia' WHERE idRevista = 4;
UPDATE Revista SET categoria = 'Ciencia' WHERE idRevista = 5;
```

**ALTER TABLE …**

Para modificar a estrutura da tabela, não altera os valores

Para modificar uma coluna, usamos o MODIFY COLUMN

Podemos usar o ADD COLUMN para adicionar uma nova coluna

```sql
-- Alterar a tabela para que a coluna categoria possa ter no máximo 40 caracteres.
ALTER TABLE Revista MODIFY COLUMN categoria varchar(40);

-- Acrescentar a coluna periodicidade à tabela, que é varchar(15).
ALTER TABLE Revista ADD COLUMN periodicidade varchar(15);

-- Deletar uma coluna
ALTER TABLE Revista DROP COLUMN periodicidade;
```

**DROP DATABASE …**

Exclui todo o banco de dados

TRUNCATE TABLE …

Retira todos os dados da tabela

ADD CONSTRAINT

Podemos adicionar um tipo de checagem para que não seja inserido outros tipos de dados além do que queremos.

**Primeira forma:**

```sql
CREATE TABLE desenhos(
	id int primary key auto_increment,
    titulo char(50),
    lancamento date,
    emissora char(50),
    classificacao int,
    statusDesenho char(15),
    nota int, CONSTRAINT chkNota CHECK (nota between 1 and 5)
) auto_increment = 10; -- autoincrement aq p comeca a partir do 10

```

**Segunda forma:**

```sql
ALTER TABLE Professor2 ADD CONSTRAINT chkFuncao
	CHECK (funcao in('monitor','assistente','titular'));
```

DATE

Criar dentro da tabela um campo para data, sempre estará como string e no formato YYYY-MM-DD

```sql
CREATE TABLE MisteriosSa(
	id int primary key auto_increment,
    nome varchar(60),
    dataCompra date,
    preco dec(5,2),
    peso int,
    dataRetirada date
);

INSERT INTO MisteriosSa (nome, dataCompra, preco, peso) VALUES
	('Uva','2024-08-08', 30.00, 1000),
	('Banana','2024-08-10', 30.20, 1800),
	('Maça','2024-08-29', 15.50, 900),
	('Goiaba','2024-08-08', 9.99, 800),
	('Mirtilo','2024-08-12', 35.99, 300);
```

RENAME

Renomear alguma coluna

```sql
ALTER TABLE misteriossa RENAME COLUMN id TO idComida;
```

ALIAS

Para escrever uma mensagem diferente na coluna

SELECT MisteriosSa.dataCompra AS 'data da compra', MisteriosSa.dataRetirada AS 'data de retirada', MisteriosSa.nome FROM MisteriosSa WHERE nome = 'Biscoitos Scooby' ;
