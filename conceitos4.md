# Relacionamentos

O conceito de relacionamentos depende muitas vezes da existência de chaves (primárias e estrangeiras) em um banco de dados. Na verdade, é o uso das funcionalidades de chaves primárias e estrangeiras que formam os relacionamentos. Outra caractéristica é que essas propriedades (chaves e relacionamentos) pertencem ao modelo de bancos relacionais.

Um relacionamento pode ser definido pelos elos (ou ligações) existentes entre duas tabelas. Quando se liga um , ou mais , campos de uma tabela com um, ou mais, campos de outra tabela forma-se um relacionamento, sendo normalmente o campo da primeira tabela uma chave primária e o campo da segunda uma chave estrangeira, pois repetem os valores da primeira tabela.

Para exemplificar melhor esta situação, pode-se mencionar um caso de uso de cadastro de clientes  e suas compras. Suponha uma tabela chamada de **CLIENTE** que tenha os seguintes campos:

* **CODIGO**   : Número único que identifica um cliente.
* **NOME**     : Texto que contém o nome do cliente.
* **ENDEREÇO** : Texto que contém o endereço do cliente.

Suponha também a existência de tabelas **COMPRAS**, com os seguintes campos:

* **CODIGO_CLIENTE**   : Número do cliente comprador.
* **PRODUTO**          : Texto com a discrição do produto comprado.
* **VALOR**            : Número moeda contendo o valor total da compra.
 
## Arquitetura de um Banco de Dados Relacional

**Tabela**

Os banco de dados realcionais, os dados são organizados em formato de tabela, onde cada coluna é um campo e cada linha um resgistro.

| Codigo | Fornecedor | Endereco | Telefone |
| :----: | :----      | :-----   | :------  |
| 1 | Dutra Esquadria | Rua XV de Novembro | 1123-4545 |
| 2 | Alfa Aluminios  | Rua Nunes Machado  | 1263-9598 |
| 3 | Lider dos Metais | Rua Des. Mota     | 1397-8426 |
| 4 | Nobre Siderurgica | Avenida dos Estados | 1637-4916 |

**Registro**

As linhas de uma tabela são chamadas de registro. Cada registro é formado por um conjuto de campos, os mesmos que formam a tabela. 

| 1 | Dutra Esquadria | Rua XV de Novembro | 1123-4545 |
| :----: | :----      | :-----   | :------  |


**Campo**

Cada coluna da tabela está representando um campo, o qual armazena as informaçãoes sobre um tipo de dado
| Codigo | Fornecedor | Endereco | Telefone |
| :----: | :----      | :-----   | :------  |

**Chave**

Chave é a coluna da tabela resposável por identificar os registros. O não uso de chave pode tornar o banco de dados vulnerável a diversos problemas: redundância de dados e inconsistência em relacionamento entre tabelas.


>Seja um cadastros de clientes, não se deve relacionar um cliente diretamente apenas por seu nome, pois há a possibilidade de haver dois clientes com exatamente o mesmo nome completo. Na situação de um sorteio de um prêmio e cliente o nome do cliente sorteado é Mário Anônio, porém no cadastro há dois clientes distintos com esse nome. Qual deles ficará com o prêmio? >Uma solução seria realizar um sorteio com base no número e no telefone do cliente (solução conhecida como chave composta), além disso >poderia ser usado o CPF do cliente, uma vez que o CPF é exclusivo para cada cliente (solução conhecida como chave primária). 



Chave Primaira: A chave primária  (do inglês, PK - Primary Key) é o caracterizada pelo fato de conter valores únicos. Por exemplo o CPF, na tabela seguinte:

| CPF | Nome |
| :----: | :----  |
| 001.001.001-01 | Carlos Drummond de Andrade    |
| 002.002.002-02 | Machado de Assis  |
| 003.003.003-03 | Erico Verissimo  |
| 004.004 004-04 | Machado de Assis   |

Chave Composta: A chave composta tanbém é caracterizada por conter um valor único, porém é formada por dois ou mais campos. Há chave composta pode admitir valores repetidos em suas colunas, mas as se considerar as duas simultaneamente essa possibilidade não pode ocorrer.   


| Telefone|Nome |
| :----: | :----  |
| (41)1123-4456| Carlos Drummond de Andrade    |
| (47)1223-2345 | Machado de Assis  |
| (21)1212-2123 | Erico Verissimo  |
| (11)1321-3213 | Machado de Assis   |

A chave composta é utilizada para suprir a necessidade do uso de chave primária em um banco de dados não-normalizados. É aconselhavél o uso de chaves primárias simples, tanto por questões de performance quato pela facilidade de relacionamento de tabelas.


Chave Estrangeira: A chave estrangeira (FK - Foreing Key) é uma coluna que armazena a chave primária de outra tabela. A Chave estrangeira e a chave primaria forma o relacionamento entre tabelas.


**Tabela CLIENTES** 

|Codigo |Nome |
| :----: | :----  |
| 1 | Carlos Drummond de Andrade    |
| 2 | Machado de Assis  |
| 3 | Erico Verissimo  |

**Tabela VENDAS**

|Nota Fiscal | Cliente | Produto |
| :----: | :----  | :----- |
| 239 | 1  | dvd player    |
| 240 | 1  | home theater  |
| 241 | 2  | som           |

>Neste caso, a coluna **Cliente** da tabela **VENDAS** está encarregada somente de armazenar o número do código do cliente responsável pela compra. Nessa tabela **VENDAS**, esse campo é chave estrangeira, pois tem origem em outra tabela, além de ser possível cadastrá-lo em mais de um registro, tendo em vista que um cliente pode realizar mais de uma compra na loja. A coluna **Codigo** na tabela **CLIENTEs** é a chave primária, pois o cliente é dadstrado uma única vez. Assim, o campo **Cliente** é uma chave estrangeira em **VENDAS** e o campo **Codigo** é a chave primária em **CLIENTE**

