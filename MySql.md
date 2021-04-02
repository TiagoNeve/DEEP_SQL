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

```sql
create table `bd_devmedia`.`telefone` (
    `idTelefone` INT(11) NOT NULL auto_increment,
    `ddd` int(2) not null,
    `telefone` int(9) not null,
    `idCliente` int not null,
    primary key (`idTelefone`)
) ;
```

Para criar uma foreign key, depois que a tabela for construida basta executar
o seguinte comando: 
```sql
alter table `bd_devmedia`.`telefone`
add index `FK_Cliente_idx` (`idcliente` ASC)
alter table `bd_devmedia`.`telefone`
add constraint `FK_Cliente`
    foreign key ('idcliente')
    references `bd_devmedia`.`cliente` (`idCliente`)
    on delete no action
    on update on action; 
```

### Otimização de consultas no MySql

Basicamente utilizar index's pode ajudar bastante na consulta no banco de dados
mas como construir esses index buscando uma melhora significativa?
Sem os index's a consulta pela tabela se dá de linha a linha, no caso todo o banco
de dados é varrido para buscar os itens que o usuário deseja.

Na bsuca de valores utilizando index's se um usuário solicitar os valores de um
id com o número 13 e se esse id estiver com index, o mesmo terá uma ordem ascendente
e desta forma o banco vai começar do 1 até o 13 e quando chegar no 14 o mesmo irá
parar de procurar, pois ele sabe que a coluna id é indexada em ascendência.

