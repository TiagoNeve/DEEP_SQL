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
);
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