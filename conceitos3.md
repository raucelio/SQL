# Formas normais

As formas normais são úteis para resolver as anomalias de insersão, alteração, exclusão e garantir a melhor estrutura para o banco de dados.

A normalização de banco de dados é composta por algumas etapas denominadas formas normais (FN), as quais foram descritas por E. F. Cood, inicialmente em 1970, e, mais tarde, outras formas normais foram adicionadas. Atualmente, há cinco formas normais, contudo apenas as três primeiras são utilizadas, tendo em vista que os seus usos ja garantem a qualidade e integridade relacional desejada para os bancos de dados atuais.


## Primeira forma normal (1FN)

A primeira forma normal (1FN) irá traduzir os dados de um sistema qualquer para tabelas. Além disso, irá organizar para que cada tabela seja composta por linhas e colunas, de forma que a ordem das mesmas seja irrelevante, além de cada célula, interseção de linha com coluna, tenha apenas um valor dentro de si.

Para está na 1FN, a tabela deve respeitar duas regras básicas. A primeira é que cada cada célula deve possuir apenas um valor e a segunda é que cada coluna deve armazenar registros únicos, a menos que esteja referenciando valores-chaves  de outras tabelas (caracterizando-se uma chave estrangeira).

A tabela que gerencia as locações de filmes de uma locadora que não está na 1FN, pois o campo **LOCACOES** está armazenando mais de um valor em um único registro. Outro problema é o armazenamento do contato do cliente, campo **TELEFONE** na mesma tabela de **LOCACOES**. Se o cliente alterar os seu telefone, haverá registros com dados antigos no sistema, causando inconsistências.

**Tabelas não normalizadas em nenhuma FN**

|CLIENTE|LOCACOES|TELEFONE|SALDO|
|:---   |:---    |:---    |:--- |
|Carlos | Alien, A caverna  | 1223-4231 | 0,00|
|Maria  | O Predador, Alien | 1333-8765 | 2,50|
|Carlos |Dick Trace         | 1223-4231 |-1,00|

A solução para este problema seria incluir um registro para cada locação e separar os dados dos clientes desta tabela, relacionando-se por meio de códigos únicos, como mostras as tabelas seguintes. Vale ressaltar que a tabela **LOCACOES** é formada por uma chave composta pelos campos **CLI** (chave estrangeira referente a clientes) e **FILME** (chave estrangeira referente a filmes).

**Tabela na 1FN**

**Tabela LOCACOES**

|CLI    |FILME  |SALDO|
|:---   |:---   |:--- |
|1 | 1  | 0,00 |
|1 | 2  | 0,00 |
|2 | 3  | 2,50 |
|2 | 1  | 2,50 |
|1 | 4  | -1,00 |

**Tabela FILMES**

|COD| FILME|
|:---   |:---    |
|1 | Alien             |
|2 | A caverna         |
|3 | O Predador        |     
|4 | Dick Trace        |

**Tabela CLIENTE**

|COD|CLIENTE|TELEFONE|
|:---   |:---    |:---    |
|1  | Carlos  | 1223-4231 |
|2  | Maria   | 1333-8765 |

Neste caso especifico, a tabela **LOCACOES** utiliza uma chave composta para gerar o valor único. Contudo se o cliente locar duas vezes o mesmo filme, haverá dois registros idênticos na tabelas.

## Segunda Forma Normal (2FN)

A segunda forma norma (2FN) irá tratar mais a fundo a relação entre os atributos de uma tabela. Para entender os requisitos da 2FN, é necessári obrigatóriamente esta na 1FN, e ainda cada atributo não chave da tabela deverá depender exclusivamente de todas as chaves da tabela.

Utilizando o mesmo exemplo da primeira forma normal, nota-se que o campo **SALDO** depende exclusivamente da chave estrangeira **CLIENTE** e não possui nenhum vínculo com outra chave estrangeira **FILME**.

**Tabela na 1FN**

**Tabela LOCACOES**

|CLI    |FILME  |
|:---   |:---   |
|1 | 1  | 
|1 | 2  | 
|2 | 3  |
|2 | 1  | 
|1 | 2  | 

**Tabela FILMES**

|COD| FILME|
|:---   |:---    |
|1 | Alien             |
|2 | A caverna         |
|3 | O Predador        |     
|4 | Dick Trace        |

**Tabela CLIENTE**

|COD|CLIENTE|TELEFONE|SALDO|
|:---   |:---    |:---    | :--- |
|1  | Carlos  | 1223-4231 | -1,00|
|2  | Maria   | 1333-8765 |  2,50|

## Terceira Forma Normal (3FN)

A terceira forma normal (3FN) requer que cada atributo de uma tabela dependa exclusivamente de suam chave primária da mesma, alem que requerer que a tabela já esteja na 2FN.

Basicamente, é uma regra semelhante a 2FN, normalmente sendo seguida intuitivamente pelos administradores de banco de dados ao separar os atrbutos de cada tabela de acordo com os assuntos que gerenciam.

Para ilustrar um um exemplo de correção para a 3FN, considere as tabelas de um sistema de vendas de produtos. Considere os campos **COD** como chaves primárias.  

**Tabela PRODUTO**

|COD|PRODUTO|COR|
|:---   |:---    |:---    |
|1  | CADERNO  | AZUL  |
|2  | LAPIS    | VERDE |
|3  | LAPIS    | AZUL  |

**Tabela VENDA**

|COD|CLIENTE|PRODUTO|COR|
|:---   |:---    |:---    | :--- |
|235  | Maria   | 2 | VERDE|
|236  | Maria   | 1 | AZUL |
|237  | Maria   | 3 | AZUL |

Neste caso, as tabelas estão na 2FN, mas não na 3FN. Isso se o campo **COR** da tabela **VENDA** for um campo não-chave que depende exclusivamente de outro campo não-chave, no caso **PRODUTO** da tabela **VENDA**. As tabelas organizadas desta forma geram uma redundaância de dados que poderá trazer inconvenientes para o sistema, como, por exemplo, se houver atualizações nas cores dos produtos  da tabela **PRODUTO**, e não atualizar a tabela **VENDA** com as novas informações.

Comom o campo **COR** da tabela **VENDA** pode ser obtido automatcamente por meio de uma consulta  na tabela **PRODUTO**, passando o código do produto, a coluna deve ser excluída da tabela **VENDA**. Desta forma as tabelas estarão na 3FN.
