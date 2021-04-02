# DEEP MYSQL

## Tabelas e Índices

INstalar MySql -> Instalei no docker e foi fluído, partil.

Para criar um banco de dados execute o seguinte comando: 
```sql
CREATE SCHEMA `bd_devmedia` DEFAULT CHARACTER SET utf8 ;
# Cria um banco de dados com os caracteres padrões em utf8
```

Para criar uma tabela, execute o seguinte comando: 
```sql
CREATE TABLE `db_devmedia`.`cliente` (
    `idCliente` INT NOT NULL AUTO_INCREMENT,
    `Nome` VARCHAR(255) NOT NULL,
    `Sexo` CHAR(1) NULL DEFAULT 'M',
    `DataNascimento` DATE NULL,
    `Peso` REAL NULL,
    PRIMARY KEY (`idCliente`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 ;
```

Para insertar valores dentro da tabela basta utilizar esse comando: 
```sql
INSERT INTO cliente (
    nome,
    sexo,
    datanascimento,
    peso
)
VALUES ('Tiago', 'M', '1999-07-06', 60.50);
```

Para criar Index dentro da tabela basta utilizar esse comando: 
```sql
ALTER TABLE `bd_devmedia`.`cliente`
ADD INDEX `Index_nome` (`Nome` ASC);
```
O sql altera a tabela para poder adicionar o index. De forma ASC -> Ascendente.
Para deletar o Index, basta executar esse comando: 
```sql
ALTER TABLE `bd_devmedia`.`cliente`
DROP INDEX `Index_nome`;
```

Para criar Index's compostos, basta executar o comando: 
```sql
ALTER TABLE `bd_devmedia`.`cliente`
ADD INDEX `Index_Sexo_Peso` (`Sexo` ASC, `Peso` ASC);
```

Para atualizar os Index's compostos é necessário primeiro dropar o index e depois
criar com os valores corretos:
```sql 
ALTER TABLE `bd_devmedia`.`cliente`
DROP INDEX `Index_Sexo_Peso` ,
ADD INDEX `Index_Sexo_Peso` (`Sexo` ASC, `DataNascimento` ASC);
```