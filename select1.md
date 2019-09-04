# SQL - Structure Query Language

O SQL é a linguagem responsável pela interação com os dados armazenados, em sua maioria, em bancos relacionais. Essa linguagem permite:

+ **Consulta** : recuperar informações armazenadas em um banco de dados.
+ **Atualização** : Atualiza informação armazenada em um banco de dados de três formas: **inclusão**, **atualização** e **exclusão**.
+ **Filtros** e **Ordenação** : Permite ordenar e selecionar os dados de uma consulta.

## Instrução SELECT

A instrução mais importante no SQL é o SELECT, pois, é a partir dele, que será possível visualizar os resultados das aplicações das demais instruções como inserção, alteração e remoção de conteúdos.

O comando SELECT é utilizado na realização de consultas ao banco de dados, retornando  sempre os dados em formato de tabelas.

```
SELECT campo FROM tabela
```

### Parâmetro WHERE

O parãmetro WHERE é um argumento opcional da instrução SELECT e de outras instruções. O seu objetivo é filtrar o conjunto de resultados para que somente  os registros que atendam a determinadas condições sejam visualizados.

```
SELECT campo FROM tabela WHERE condicao
```

### Parâmetro ORDER BY

O parãmetro **ORDER BY** é utilizado para ordenar os registros de uma consuta de acordo com um campo ou critério utilizado.

```
SELECT campo FROM tabela  ORDER BY criterio [ASC|DESC]
```

**Observação:**

+ Recomenda-se que o  **ORDER BY** seja empregado após as claúsulas WHERE e HAVING.
+ O valor DESC após a a um critério torna possível a ordenação em ordem decrescente.


### Parãmetro JOIN

O parãmetro **JOIN** e suas varições  permite unir duas ou mais tabelas a partir de campos correspondentes entre as mesmas. 

```
SELECT campo FROM tabela1 JOIN tabela2 ON tabela1.campo = tabela2.campo [WHERE condicao]
```

### Parãmetro AS

Durante a utilização de um comando SQL, em caso de utilizar campos cujos nomes sejam muito longos, ou por outros motivos, é possível atribuir um apelido (alias) para um campo especifico para uso na expressão SQL e na visualização dos resultados.

```
SELECT campo AS alias FROM tabela [WHERE condicao]
```

## Instrução INSERT

A instrução INSERT é utilizada para incluir dados em uma tabela.

```
INSERT INTO tabela [(campo1 [, campo2, ...)] VALUES (valor1 [, valor2, ...])
```

A utilização do comando INSERT requer cuidados especiais. Sempre que possível todos os campos da tabela  sejam identificados e valorados, isso porque é posível incluir registros sem informar os valores de campos que usem valores padrão criados na tabela.


## Instrução UPDATE

A instrução UPDATE é utilizada para atualizar para alterar dados dos registros armazenados no banco de dados. Seu uso pode estar combinado com parãmetro WHERE para filtrar quais registros serão alterados:

```
UPDATE tabela SET campo = valor [, campo2 = valor2, ...] [WHERE condicao] 
```

## Instrução DELETE

A instrução DELETE exclui um ou mais registros de uma tabela. É possível filtra os registros a serem excluídos por meio da claúsula WHERE. Se não for aplicado nenhum filtro, a instrução DELETE exclui todos os registros da tabela.

```
DELETE FROM tabela [WHERE condicao]
```


