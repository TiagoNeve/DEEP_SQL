# DEEP SQL

## INTRODUÇÃO

SQL = Structured Query Language, linguagem padrão de gerenciamento de banco de dados relationais.
É com essa linguagem que podemos nos comunicar com os bancos de dados da aplicação.
É uma linguagem declarativa, onde informamos o que queremos fazer ou receber e a linguagem trás 
para nós o resultado.

DDL -> Data Definition Language - São utilizados para criar banco de dados, esquemas, tabelas, campos, etc

DML -> Data Manipulation Language - São utilizados para manipular os dados no banco de dados

DQL -> Data Query Language - São utilizados para consultar o banco de dados e retornar os valores
de acordo com a declaração que for solicitado pelo consultor.

DTL -> Data Transaction Language - Utilizadas para fazer transações de dados.

DCL -> Data Control Language - Utilizadas para controlar o acesso ao banco de dados e restringir 
quais dados podem ser entregue ao usuários.

Dentre essas os que mais são utilizados são o DDL (Para criar campos e tabelas)
DML (Para manipular dados no banco) e DQL (Para consultar dados)

### DDL 

Principais comandos utilizados no DDL
```sql
    CREATE TABLE  #Cria uma tabela no banco de dados

    CREATE TABLE Contato ( Id int, Nome varchar(255), Telefone varchar(11));
    # É inserido dentro dos parênteses as colunas da tabela e suas propriedades, como
    # tipo e tamanho de caracteres permitidos.

    DROP TABLE # Destroi uma tabela.

    DROP TABLE Contato;
    #Irá destruir a tabela contato. Logo, todos os dados nela.

    ALTER TABLE # Altera as colunas e as propriedades da tabela, modifica a estrutura.

    ALTER TABLE Contato ADD email VARCHAR(255);
    # Altera a tabela Contato, adicionando a coluna email com a restrição de caracteres.


    TRUNCATE # Apaga os registros da tabela, mas ela fica ativa ainda.

    TRUNCATE TABLE Contato;
    #Irá apagar os registros nessa tabela.
```
### DML/DQL

-> Principais comandos agrupados em DML e DQL: 

```sql
INSERT # Utilizado para inserir dados em uma coluna da tabela.

INSERT INTO Cliente(nome, telefone) VALUES ('Tiago', '99999-9999');
# Irá inserir dentro da tabela Cliente, nas colunas nome, telefone, os valores 
# correspondentes logo após.
===============================================================
DELETE # Utilizado para excluir dados em uma tabela.

DELETE FROM Cliente WHERE id = 2;
# Irá excluir da tabela Cliente onde o id = 2

DELETE FROM Cliente;
# Irá deletar todos os dados da tabela cliente.
================================================================
UPDATE # Utilizado para atualizar um valor na tabela.

UPDATE Cliente SET telefone = '00000-0000' WHERE id = 3;
# Irá atualizar na tabela Cliente a coluna telefone, onde o id é igual a 3;

UPDATE Cliente SET telefone = '00000-0000';
# Irá atualizar todos os valores da coluna telefone.
=================================================================
SELECT # Recupera os valores que estão contidos na tabela.

SELECT nome, telefone FROM Cliente;
# Irá retornar os valores da coluna nome, telefone da tabela Cliente.

SELECT nome, telefone FROM Cliente WHERE nome = 'Tiago';
# Irá trazer os valores da coluna nome, telefone da tabela Cliente, onde o nome = 'Tiago'.
==================================================================
```
### EXERCICIO
```sql
    DELETE FROM produtos; # Apaga todos os dados da tabela;
    SELECT nome, idade FROM usuarios; # Forma correta de utilizar um select.
    UPDATE produtos SET produto = 'Galaxy Note 20 Ultra' WHERE id = 2;
    # Irá atualizar da tabela produtos, a coluna produto com o valor tal, onde o id é tal.
    INSERT INTO mangas(titulo, estoque) VALUES('Boruto', 1);
    # Irá adicionar os valores correspondentes nas colunas correspondentes.
    DELETE FROM usuarios WHERE id = 1; 
    # Deleta a linha onde o id é igual a 1.
    SELECT titulo FROM jogos WHERE classificacao = 'L';
    # Irá retornar os valores da coluna titulo, da tabela jogos, onde a classificacao é L.
    INSERT INTO usuarios (nome, idade) VALUES ('Lucas', 17);
    SELECT loja FROM lojas WHERE aberta = 0;
    UPDATE usuarios SET status = 1;
    INSERT INTO lojas(loja, aberta) VALUES ('Shoptime', 1);
    INSERT INTO jogos(titulo, classificacao) VALUES ('Tetris Effect Connect', 'L');
    UPDATE jogos SET classificacao = 18 WHERE id = 1;
    SELECT id, nome, preco FROM produtos;
    SELECT nome, telefone, email FROM contatos WHERE id = 3;
    SELECT nome, telefone FROM contatos;
    DELETE FROM mangas WHERE id = 3;
    DELETE FROM contatos WHERE id = 4;
    INSERT INTO produtos(nome, preço) VALUES ('Atari VCS', 2400);
    DELETE FROM usuarios WHERE id = 2;
    DELETE FROM jogos WHERE id = 6;
    UPDATE funcionarios SET nome = 'Roberto' WHERE id = 3;
    INSERT INTO produtos(produto, fabricante) VALUES ('Moto Z', 'Motorola');
    UPDATE lojas SET loja = 'Casa e Video' WHERE id = 3;
    INSERT INTO montadoras(nome, pais) VALUES ('Dodge', 'EUA');
    DELETE FROM jogos WHERE classificacao = 10;
    SELECT nome, pais FROM montadoras;
    SELECT nome, pais FROM montadoras;
    SELECT titulo FROM mangas;
    SELECT produto FROM produtos;
    DELETE FROM produtos WHERE id = 4;
    INSERT INTO produtos(produto, fabricante) VALUES('IPhone 12', 'Apple');
    UPDATE mangas SET estoque = 1 WHERE estoque = 0;
    SELECT loje FROM lojas WHERE aberta = 1;
    
```