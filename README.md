# Resumo - Curso de Banco de Dados MySQL
Por: SECTI

Objetivo: Ensinar o básico do SQL e da SGBD MySQL.

## O que são Bancos de Dados, e SGBDs SQL

**Bancos de Dados**: São *Agrupadores de dados*, à disposição de vários sistemas.

**SGBDs**(Sistemas de Gerenciamento de Banco de Dados): Ferramentas que são usadas para *gerenciar* os bancos de dados, permitindo a *implementação* de linguagens de gerenciamento(DDL, DML e DQL, do SQL, por exemplo).

**SQL**(Structured Query Language): Linguagem feita para dialogar com *SGBDs relacionais*, proporcionando *ações de gerenciamento* como as descritas abaixo.

## Linguagens SQL

### DDL(Linguagem de Definição de Dados)

DDLs mexem exclusivamente com a estrutura do banco de dados, ele define a estrutura.

##### CREATE
**Função**: Criar bancos de dados e tabelas

* `CREATE DATABASE` -> Cria um ***banco de dados***

	```
	CREATE DATABASE [nome_do_banco];
	```


* `CREATE TABLE` -> Cria uma ***tabela*** e suas ***colunas***

	```
	CREATE TABLE [Nome](
	[nomeColuna1] [tipo] [restrições],
	[nomeColuna2] [tipo] [restrições],
	...
	);
	```

##### DROP
**Função**: Excluir.

* `DROP DATABASE` -> Exclui o ***banco de dados***
	```
	DROP DATABASE [nome_do_banco]
	```


* `DROP TABLE` -> Exclui a ***tabela***
	```
	DROP TABLE [NomeDaTabela]
	```

##### ALTER TABLE
**Função**: Faz alterarções em elementos de uma tabela escolhida(nas *tabelas* altera: nome; nas *colunas* altera: nome, restrições e tipo).

* `ALTER TABLE ADD COLUMN` -> adiciona uma ***coluna*** na tabela escolhida.
	```
	ALTER TABLE [Nome]
	ADD COLUMN [nomeDaColuna] [tipo];
	```


* `ALTER TABLE DROP COLUMN` -> exclui a ***coluna*** escolhida na tabela escolhida.
	```
	ALTER TABLE [Nome]
	DROP COLUMN [nomeDaColuna];
	```


* `ALTER TABLE RENAME TABLE` -> renomeia a ***tabela*** escolhida
	```
	ALTER TABLE [Nome]
	RENAME TO 	[NovoNome];
	```


* `ALTER TABLE RENAME COLUMN` -> renomeia a ***coluna*** escolhida
	```
	ALTER TABLE [Nome]
	RENAME COLUMN [nomeVelho] TO [nomeNovo];
	```


* `ALTER TABLE ADD CONSTRAINT` -> adicionar ***restrição***
	
	```
	ALTER TABLE [Nome]
	ADD CONSTRAINT [nome_da_restrição] [restrição];
	```
	
	
* `ALTER TABLE MODIFY	DATATYPE` -> modifica o ***tipo de dado*** da ***coluna***
	```
	ALTER TABLE [Nome]
	MODIFY column_name new_datatype constraint;
	```
	
### DML(Linguagem de Manipulação de Dados)
DML serve para inserir, modificar e remover dados, distribuidos em seus devidos lugares.


* `INSERT INTO TABLE` -> insere ***valores*** nas colunas escolhidas de uma ***tabela*** escolhida
	```
	INSERT INTO [Nome] ([coluna1], [coluna2], [coluna3], ...)
	VALUES ([valor1], [valor2], [valor3], ...);
	```


* `UPDATE` -> troca um ***valor*** específico(onde a ***condição*** for verdadeira), em uma ***coluna*** específica, por outro.
	```
	UPDATE [Nome]
	SET [coluna1] = [valor1], ...
	WHERE [condição];
	```
	
	
* `DELETE` -> Exclui ***valores***(onde a ***condição*** for verdadeira) de uma ***tabela*** específica.
	```
	DELETE FROM [Nome]
	WHERE [condição];
	```

#### DQL(Linguagem de Consulta de Dados)
DQL é usada para retornar dados, seguindo condições específicas, permitindo uma análise detalhada.

* `ALIASES`

	ALIAS são ferramentas que criam ***atalhos*** palavra-comando.

	```
	[comando] AS [Nome]
	```


* `SELECT` -> retorna todos os ***valores*** inseridos em ***colunas*** escolhidas.
	```
	SELECT [coluna1], [coluna2]...
	FROM [Nome];
	```


* `SELECT DISTINCT` -> retorna apenas valores não duplicados de uma coluna
	```
	SELECT DISTINCT [coluna] FROM [Nome];
	```


* `SELECT ALL` -> retorna todos os ***valores*** de todas as ***colunas***.
	```
	SELECT *
	FROM [Nome];
	```


* `SELECT WHERE` -> retorna todos os ***valores*** de uma ***tabela*** que são verdadeiros perante a ***condição***.
	```
	SELECT [coluna1], [coluna2]...|*
	FROM [Nome]
	WHERE [condição];
	```
	- **Operadores Lógicos**:
		* `a` **igual** a `b`:
		
			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a == b;
			```


		* **não** `a`:

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE NOT a;
			```


		* `a` **maior/menor** que `b`:

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a >|< b;
			```


		* `a` **maior/menor ou igual** a `b`

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a >=|<= b;
			```


		* `a` **ou** `b`

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a OR b;
			```


		* `a` **e** `b`

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a AND b;
			```


		* `a` **entre** `b` **e** `c`

			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a BEETWEEN b AND c;
			```
	
	- **Expressões Regulares**
	"padrões utilizados para selecionar combinações de caracteres em uma string." - Mozilla
	
		* `LIKE` -> exatamente `[char]`
		
			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a LIKE '[char]';
			```

		* `LIKE '[char]%/%[char]/[char1]%[char2]'` -> vários caracteres após o '[char]';vários caracteres antes do '[char]';vários caracteres entre '[char1]' e '[char2]'.
		
			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a LIKE '[char]%|%[char]|[char1]%[char2]';
			```
		
		* `LIKE [char]_.../..._[char]/_...[char]..._` -> quantidade específica de caracteres após '[char]'; quantidade especifica de caracteres antes de '[char]';'[char]' entre uma quantidade específica de caracteres.
			
			```
			SELECT [coluna1], [coluna2]...|*
			FROM [Nome]
			WHERE a LIKE '[char]_...|..._[char]|_...[char]..._';
			```

	- **Funções Agregadas**
	
	* `MIN()` -> retorna o menor valor da coluna selecionada
		
		```
		SELECT MIN([coluna1], [coluna2]...|*)...
		FROM [tabela]
		```

	
	* `MAX()` -> retorna o maior valor da coluna selecionada
	
		```
		SELECT MAX([coluna1], [coluna2]...|*)...
		FROM [tabela];
		```

	* `COUNT()` -> retorna o numero de linhas onde os valores(não nulos) se encaixam na condição.
	
		```
		SELECT COUNT([DISTINCT] [coluna1], [coluna2]...|*)...
		FROM [tabela]
		WHERE [condição];
		```
		
	* `SUM()` -> retorna a soma de todos os valores de uma coluna numérica.
	
		```
		SELECT SUM([coluna])
		FROM [tabela]
		WHERE [condição];
		```

	* `AVG()` -> retorna a média aritmética de uma coluna numérica.

		```
		SELECT AVG([[coluna1], [coluna2]...|*])
		FROM [tabela]
		WHERE [condição];
		```

			
* `SELECT ORDER BY` -> retorna todos os ***valores*** de uma ***tabela*** em ordem de colunas e/ou ordem ascendente ou descendente.

	```
	SELECT [coluna1], [coluna2]...|*
	FROM [nome]
	ORDER BY [coluna1] ASC|DESC, [coluna2] ASC|DESC...;
	```


* `SELECT INNER JOIN` -> retorna a combinação de dados interseccionados de duas ou mais tabelas.

	```
	SELECT [coluna1], [coluna2]...|*
	FROM [tabela1]
	INNER JOIN [tabela2]
	ON [tabela1].[coluna] = [tabela2].[coluna];
	```


* `SELECT LEFT/RIGHT JOIN` -> retorna a combinação de dados que se encaixam na tabela da esquerda/direita de duas ou mais tabelas.

	```
	SELECT [coluna1], [coluna2]...|*
	FROM [tabela1]
	LEFT|RIGHT JOIN [tabela2]
	ON [tabela1].[coluna] = [tabela2].[coluna];
	```

* `SELECT FULL JOIN` -> retorna a combinação de dados de todas as tabelas entre duas ou mais tabelas.
	
	```
	SELECT [coluna1], [coluna2]...|*
	FROM [tabela1]
	FULL JOIN [tabela2]
	ON [tabela1].[coluna] = [tabela2].[coluna]
	WHERE [condição];
	```

## Resumo:

**O que são Bancos de Dados, SGBDs e SQL:** *Banco de dados* é onde guarda os dados; *SGBDs* são interpretadores de código *SQL*, uma linguagem para BD's relacionais.

### **DDL**:

* `CREATE`
	- **CREATE** DATABASE -> cria ***banco de dados***
	- **CREATE** TABLE -> cria ***tabela***

* `DROP`
	- **DROP** DATABASE
	- **DROP** TABLE

* `ALTER TABLE`
	- **ALTER** TABLE `ADD/DROP` COLUMN -> add/rem ***colunas***
	- **ALTER** TABLE `RENAME` TABLE/COLUMN -> renomeia ***tabelas***/***colunas***
	- **ALTER** TABLE `ADD` CONSTRAINT -> adiciona ***restrição***
	- **ALTER** TABLE `MODIFY` DATATYPE -> muda o ***tipo de dado***

### **DML**:

* `INSERT` INTO TABLE -> insere ***valores*** numa ***coluna***
* `UPDATE` -> modifica ***valores*** de uma ***coluna***
* `DELETE` -> exclui ***valores*** de uma ***coluna***

### **DQL**:

* `ALIASES` -> palavras que representam conjuntos de ***comandos***

* `SELECT` -> retorna ***valores*** de ***colunas*** específicas.

* SELECT `DISTINCT` -> retorna ***valores*** não duplicados de ***colunas*** específicas

* SELECT `ALL` -> retorna todos os ***valores*** de uma ***tabela***

* SELECT `WHERE` -> retorna ***valores***, mas com uma ***condição***
	- **Operadores lógicos** -> operadores usados nas condições
	- **Expressões regulares** -> busca intligente de strings
	- **Funções agregadas** -> funções prontas para uso

* SELECT `ORDER BY` -> retorna ***valores***, mas em ordem especificada

* SELECT `INNER JOIN` -> retorna ***valores*** combinados por intersecção

* SELECT `LEFT/RIGHT JOIN` -> retorna ***valores*** combinados por lado

* SELECT `FULL JOIN` -> retorna todos os *valores* combinados
