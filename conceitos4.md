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


Neste caso, na tabela **CLIENTE**, o campo **CODIGO** é definido como chave primária, pois o seu valor não se repetirá ao longo desta tabela, ou seja, será unido. Já na tabela **COMPRAS**, o campo **CODIGO_CLIENTE**é definido como como chave estrangeira, pois contonterá valores do campo **CODIGO** da tabela  **CLIENTE**. O relacionamento está definido no fato de que em  cada compra é obrigatório existir um cliente. Ainda, como um cliente poderá fazer realizar várias compras, o seu código poderá aparecer em mais de um registro na tabela **COMPRAS**, caracteristica estas de chave estrangeiras.

Outro objetivo dos realcionamentos é auxiliar nas consistências dos dados armazenados no banco. No exemplo citado anteriormente, uma consitência possível de ser aplicada é validar o côdigo do cliente inserido na tabela **COMPRA** é um código valido, isto é, se existe, podendo ocasionar um erro tipo **COMPRA NÃO-REALIZADA PELO MOTIVO: CLIENTE NÃO CADASTRADO**, caso o código seja invalido.

## Relacionamento 1 para 1

o tipo de relacionameto de 1 para 1 diz respeito às ligações entre tabelas em que para cada registro da primeira tabela pode existit até um ná segunda segunda tabela.

um exemplo para esse tipo de relacionamento é a ligação entre o RG, carteira de identidade,  e o CPF, cadastro de pessoa fisica, de uma pessoa. Cada cidadão brasileiro possui um único RG, que, por sua vez, pode estar vinculado a um único CPF ativo, assim como cada CPF ativo obrigatoriamento estará ligado a um único número de RG, como abaixo:

**Tabela de RG***

| RG | Nome |
| :----: | :----  |
| 1.222.333-4 | Carlos Drummond de Andrade    |
| 1.234.432-5 | Machado de Assis  |
| 1.112.313-6 | Erico Verissimo  |

**Tabela de CPF***

| RG | CPF |
| :----: | :----  |
| 1.222.333-4 | 122.223.334-45   |
| 1.234.432-5 | 121.232.234-34   |

## Relacionamento de 1 para N

Já os relacionamentos 1 para N permitem que possa existir mais de um registro na segunda tabela, para cada registro da primeira tabela.

Neste relacionamento, um exemplo que pode ser citado é a ligação entre o cliente e as compras realizadas em uma loja. Informalmente, um cliente pode realizar uma ou mais (N) compras em uma loja. Contudo para cada compra da loja, ou seja, cada nota fiscal emitida, estará exclusivamente em um cliente. Formalmente, a tabela **CLIENTE** possuirá uma coluna como chave primária, CPF, por exemplo, que estará realcionada com a tabela **COMPRA**, na qual essa chave poderá aparecer em mais de um registro. Ademais, cada compra estará representada em um único registro da tabela **COMPRA**, pois a nota fiscal é um documento único na transação, o número da nota fiscal pode ser uma chave primária na tabela **COMPRA**, como mostra a tabela seguinte. 

**Tabela CLIENTE***

| Codigo | Nome |
| :----: | :----  |
| 1 | Carlos Drummond   |
| 2 | Machado de Assis  |
| 3 | Erico Verissimo  |

**Tabela COMPRA***

| Nota Fiscal | Cliente | Produto |
| :----: | :----  | :---- |
| 239 | 1   | DVD Player |
| 240 | 1   | Home Theater |
| 241 | 2   | Som        |

# Relacionamentos N para N

De todos tipos de relacionamentos, o tipo N para N, muitos para muitos, é, sem dúvida, o mais amplo de todos. Pode-se dizer que este  relacionamento é a combinação do tipo de 1 para N nos dois sentidos, da primeira para a segunda tabela e vice-versa. Neste caso, pode haver um ou mais registros na segunda tabela ligados a um registro da primeira, assim como pode haver um ou mais registros na primeira tabela  para cada registro da segunda.

Um exemplo para este caso é o controle de matrícula de alunos nos cursos de um treinamento oferecidos por uma escola qualquer. Não há restrições de que o aluno não possa assistir a mais de um curso. Portanto, um aluno pode está matriculado em um ou mais cursos da escola. Do outro lado da ligação, um curso pode ser frequentado por um ou mais alunos. Supondo as tabelas **ALUNO** com o campo Codigo como chave primária dos alunos, que será a chave estrangeira em **MATRICULA** , como também da coluna responsável pelo nome do curso, pois, pois vários alunos poderão estar matriculados no mesmo curso, conforme as tabelas abaixo. 

**Tabela ALUNO***

| Codigo | Nome |
| :----: | :----  |
| 1 | Carlos Drummond   |
| 2 | Machado de Assis  |
| 3 | Erico Verissimo  |

**Tabela MATRICULA***

| Aluno | Curso |
| :----: | :----  |
| 1 | Digitacao   | 
| 1 | Planilha   | 
| 2 | Digitacao   | 
| 3 | Digitacao   |

Note que a coluna Curso poderia ser uma chave estrangeira, caso os cursos fossem cadastrados em uma tabela à parte denomeinada **CURSO**. 

**Tabela ALUNO***

| Codigo | Nome |
| :----: | :----  |
| 1 | Carlos Drummond   |
| 2 | Machado de Assis  |
| 3 | Erico Verissimo  |

**Tabela MATRICULA***

| Aluno | Curso |
| :----: | :----  |
| 1 | 1   | 
| 1 | 2   | 
| 2 | 1   | 
| 3 | 1   |

**Tabela CURSO***

| Codigo | Curso |
| :----: | :----  |
| 1 | Digitacao  | 
| 1 | Planilha   | 
