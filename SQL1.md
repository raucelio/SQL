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

**Exemplo:**

```
SELECT capital, populacao FROM brasil
```

### Parâmetro WHERE

O parãmetro WHERE é um argumento opcional da instrução SELECT e de outras instruções. O seu objetivo é filtrar o conjunto de resultados para que somente  os registros que atendam a determinadas condições sejam visualizados.

```
SELECT campo FROM tabela WHERE condicao
```

**Exemplo:**

```
SELECT capital, populacao FROM brasil WHERE regiao = 'Norte'

```


### Parâmetro ORDER BY

O parãmetro **ORDER BY** é utilizado para ordenar os registros de uma consuta de acordo com um campo ou critério utilizado.

```
SELECT campo FROM tabela  ORDER BY criterio [ASC|DESC]
```

**Exemplo:**

```
SELECT capital, populacao FROM brasil ORDER BY populacao 
```


**Observação:**

+ Recomenda-se que o  **ORDER BY** seja empregado após as claúsulas WHERE e HAVING.
+ O valor DESC após a a um critério torna possível a ordenação em ordem decrescente.


### Parãmetro JOIN

O parãmetro **JOIN** e suas varições  permite unir duas ou mais tabelas a partir de campos correspondentes entre as mesmas. 

```
SELECT campo FROM tabela1 JOIN tabela2 ON tabela1.campo = tabela2.campo [WHERE condicao]
```

**Exemplo:**

```
SELECT basil.capital, basil.populacao, economia.empresa 
FROM brasil  JOIN economia ON brasil.uf = economia.uf 
```

### Parãmetro AS

Durante a utilização de um comando SQL, em caso de utilizar campos cujos nomes sejam muito longos, ou por outros motivos, é possível atribuir um apelido (alias) para um campo especifico para uso na expressão SQL e na visualização dos resultados.

```
SELECT campo AS alias FROM tabela [WHERE condicao]
```

**Exemplo:**

```
SELECT sg_unidade_federacao AS uf, nr_populacao_ativa AS populacao FROM brasil 
```


## Instrução INSERT

A instrução INSERT é utilizada para incluir dados em uma tabela.

```
INSERT INTO tabela [(campo1 [, campo2, ...)] VALUES (valor1 [, valor2, ...])
```

A utilização do comando INSERT requer cuidados especiais. Sempre que possível todos os campos da tabela  sejam identificados e valorados, isso porque é posível incluir registros sem informar os valores de campos que usem valores padrão criados na tabela.

**Exemplo:**

```
INSERT INTO consumo  (capital, populacao) VALUES ('PALMAS', 500.000) 
```


## Instrução UPDATE

A instrução UPDATE é utilizada para atualizar para alterar dados dos registros armazenados no banco de dados. Seu uso pode estar combinado com parãmetro WHERE para filtrar quais registros serão alterados:

```
UPDATE tabela SET campo = valor [, campo2 = valor2, ...] [WHERE condicao] 
```

**Exemplo:**

```
UPDATE INTO consumo SET  populacao = 456.345 WHERE capital = 'PALMAS' 
```

## Instrução DELETE

A instrução DELETE exclui um ou mais registros de uma tabela. É possível filtra os registros a serem excluídos por meio da claúsula WHERE. Se não for aplicado nenhum filtro, a instrução DELETE exclui todos os registros da tabela.

```
DELETE FROM tabela [WHERE condicao]
```

**Exemplo:**

```
DELETE  FROM aluno WHERE nota <= 7.00
```

## Exercícios

> O banco de dados **SQL_EXC_1** apresenta as tabelas **tb_cargo** e **tb_funcionário**. Execute os solicitado:

1. Selecione todas observações e todas as colunas da tb_cargo.
2. Selecione todas observações e todas as colunas da tb_funcionários.
3. Qual o nome e o cargo dos funcionários com mestrado.
4. Apresente a lista com o nome e o salário de todos os funcionários.
5. Qual o nome, o cargo e o sálario de todos os servidores que recebem mais de 1000 unidades monetárias (u.m)
6. Foi contratado o servidor abaixo, insira os seu registro na tb_funcionario.
  +nome : Joseph 
  +cargo : Analista de BI
  +salario : 23000
  +escolaridade : Graduado
7. O salário de Joseph foi inserido com valor incorreto. O verdadeiro valor é 1230, atualize tb_funcionario.
8. O funcionário Joseph pediu demissão. Retire o se registro da tb_funcionário.
9. Gere uma lista de todas as informações de todos os funcionários ordenada em ordem decrescente de salários.
