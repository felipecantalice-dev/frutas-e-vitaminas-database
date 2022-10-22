# Modelagem Frutas e suas vitaminas
Modelagem simples para relacionar quais vitaminas uma fruta possui.

1. Existem várias frutas
2. Existem várias vitaminas
3. Várias frutas contém mais de uma Vitamina
4. Várias Vitaminas podem ser encontrada em várias Frutas


## Entidade 

Frutas 

Vitaminas

## Comando

```sql
###############################
# Criando tabela frutas
###############################
CREATE TABLE frutas(
	id int primary key auto_increment,
  nome varchar(40) NOT NULL
);

###############################
# Criando tabela vitaminas
###############################
CREATE TABLE vitaminas(
	id int primary key auto_increment,
  nome varchar(40) NOT NULL
);

################################
###############################
# Criando tabela para referenias quais vitaminas uma fruta possui
###############################
CREATE TABLE frutas_vitaminas(
  id int primary key auto_increment,
  idFruta int, 
  idVitamina int,
  
  foreign key (idFruta)
  		REFERENCES frutas(id),
  
  foreign key (idVitamina) 
  		REFERENCES vitaminas(id)
);
```


```sql
INSERT INTO frutas(nome) VALUES("Banana");
INSERT INTO frutas(nome) VALUES("Maca");
INSERT INTO frutas(nome) VALUES("Pera");
INSERT INTO frutas(nome) VALUES("Uva");


INSERT INTO vitaminas(nome) VALUES("A");
INSERT INTO vitaminas(nome) VALUES("B");
INSERT INTO vitaminas(nome) VALUES("C");
INSERT INTO vitaminas(nome) VALUES("E");
INSERT INTO vitaminas(nome) VALUES("K");


INSERT INTO frutas_vitaminas(idFruta, idVitamina)
	VALUES
    	(1,1),
        (1,2),
        (1,3),
        (2,1),
        (2,3),
        (2,4),
        (3,1),
        (3,2),
        (3,3),
        (4,1),
        (4,2),
        (4,3),
        (4,5)
```


```sql
# Selecionar todas as frutas
SELECT * FROM frutas;

# Selecionar todas as vitaminas
SELECT * FROM vitaminas;

# Selecionar todas as vitaminas que a banana possui
SELECT nome FROM vitaminas v
JOIN frutas_vitaminas fv on  v.id = fv.idVitamina
WHERE idFruta = 1;
```
