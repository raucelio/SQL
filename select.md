# SQL - Structure Query Language

O SQL é a linguagem responsável pela interação com os dados armazenados, em sua maioria, em bancos relacionais. Essa linguagem permite:

+ **Consulta** : recuperar informações armazenadas em um banco de dados.
+ **Atualização** : Atualiza informação armazenada em um banco de dados de três formas: **inclusão**, **atualização** e **exclusão**.
+ **Filtros** e **Ordenação** : Permite ordenar e selecionar os dados de uma consulta.

## Instrução SELECT

A instrução mais importante no SQL é o SELECT, pois, é a partir dele, que será possível visualizar os resultados das aplicações das demais instruções como inserção, alteração e remoção de conteúdos.

O comando SELECT é utilizado na realização de consultas ao banco de dados, retornando  sempre os dados em formato de tabelas.

### Parâmetro WHERE

O parãmetro WHERE é um argumento opcional da instrução SELECT e de outras instruções. O seu objetivo é filtrar o conjunto de resultados para que somente  os registros que atendam a determinadas condições sejam visualizados.

Geralmente as condições de uma expressão que utiliza WHERE testam uma comparação de valores  entre um campo da tabela de um valor predeterminado ou até mesmo de outra tabela.

### Parâmetro ORDER BY


### Parãmetro JOIN

### Parãmetro AS

## Instrução INSERT

## Instrução UPDATE

A instrução UPDATE é utilizada para atualizar para alterar dados dos registros armazenados no banco de dados. Seu uso pode estar combinado com parãmetro WHERE para filtrar quais registros serão alterados:

```
UPDATE tabela SET campo = valor [, campo2 = valor2, ...] [WHERE condicao] 
```

## Instrução DELETE

A instrução DELETE exclui um ou mais registros de uma tabela. É possível filtra os registros a serem excluídos por meio da claúsula WHERE. Se não for aplicado nenhum filtro, a instrução DELETE exclui todos os registros da tabela.

```
DELETE FROM tabela [WHERE condicao]



