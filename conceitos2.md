# Normalização de banco de dados

A ordem com que os dados são armazenados e a forma como são estruturados podem variar bastante. A má estruturação de um banco de dados pode gerar diversos problemas para a sua aplicação e lógica do négocio, com a possibilidade de tornar o sistema para o qual o banco de dados trabalha menos preciso, lento, incoerente ou até mesmo inconfiável.

Antes do estudo de como precaver-se de tais problemas, é necessário conhecE-los um pouco melhor. Esses problemas que podem ser gerados pelo maul planejamento de um banco de dados são conhecidos como anomalias, conforme são descritas a seguir. Podem ser de inserção, alteração ou exclusão, e suas soluções estão diretamente ligadas com o relacionamento entre as tabelas do banco.

## Anomálias de inserção

Uma anomalia de inserção ocorre quando o sistema fica impedido de realizar a criação de um registro devido a falta de dados.

A tabela seguinte é responsável pelo cadastro dos sócios  de um clube campestre e os respectivos planos nos quais estão cadastrados. A tabela em questão é responsável pelo gerenciamento de dois tipos de informações: usuários e planos. Caso a equipe de markenting desenvolva um novo plano para sócios deniminado 25, para atender usuários com menos de 25 anos com um desconto especial, esse plano somente poderia ser cadastrado no sitema somente quando houvesse o primeiro usuário o utilizando. Sem sócio em questão, o plano 25 não estaria visível no sistema.

**Cadastro de sócios e planos

|CODIGO|NOME |PLANO|VALOR  |
|:---- |:--- |:--- | :---- |
|1     |CARLOS DRUMMOND | SINGLE | 199 |
|2     |MACHADO DE ASSIS| SINGLE | 199 |
|3     |ERICO VERISSIMO | 25     | 129 |

Esse exemplo corresponde a uma planilha de inserção. O correto seria separar o gerenciamentos de usuários do gerenciamento de planos, criando uma tabela somente com os planos existentes e associando-a à tabela de usuários conforme a próxima tabela. Desta forma, mesmo que o sócio de código 3 não existisse no sistema, o novo plano estaria disponível na tabela de **PLANOS***.


**Tabela SOCIOS**

|CODIGO|NOME |PLANO|
|:---- |:--- |:--- |
|1     |CARLOS DRUMMOND | SINGLE |
|2     |MACHADO DE ASSIS| SINGLE |
|3     |ERICO VERISSIMO | 25     |

**Tabela PLANOS**

|PLANO|VALOR  |
|:--- | :---- |
| SINGLE | 199 |
| 25     | 129 |

## Anomalias de Alteração


As anomalias de alteração são caracterizadas por impedirem a alteração de registro devido ao relacionamento mal planejado entre duas tabelas.

Considere a tabela anterior. Suponha que o nome do plano 25 esteja gerando dúvida entre os usuários, em relação a se é  para maiores ou menores de 25, e que seja necessário alterar o nome para **Menor de 25**. Caso não haja nenhum cliente cadastrado, será fácil realizar a alteração. Mas caso já existam clientes este plano, se alteramos o nome dele apenas na tabela **PLANO**, as relações entre as tabelas de **SOCIOS** e **PLANOS** estará incoerente, pois os usuários do antigo plano 25 estarão ligados a um plano não existente, como mostra a tabela abaixo.

**Tabela SOCIOS**

|CODIGO|NOME |PLANO|
|:---- |:--- |:--- |
|1     |CARLOS DRUMMOND | SINGLE |
|2     |MACHADO DE ASSIS| SINGLE |
|3     |ERICO VERISSIMO | 25     |

**Tabela PLANOS**

|PLANO|VALOR  |
|:--- | :---- |
| SINGLE | 199 |
| Menor de 25     | 129 |

Para resolver esta situação, a tabela de planos de planos deveria ter um outro campo como chave primária, de uso interno, normalmente conhecido como **CODIGO** ou **ID**, representando um identificador único, tendo em vista que o nome do plano pode ser alterado. A alteração seguinte soluciona esse problema:

**Tabela SOCIOS**

|CODIGO|NOME |PLANO|
|:---- |:--- |:--- |
|1     |CARLOS DRUMMOND | 1 |
|2     |MACHADO DE ASSIS| 1 |
|3     |ERICO VERISSIMO | 2 |


**Tabela PLANOS**

|CODIGO|PLANO|VALOR  |
|:---- |:--- | :---- |
|1 | SINGLE | 199 |
|2 | Menor de 25     | 129 |


## Anomalias de exclusão

No caso de anomalias de exclusão, suas características é o impedimento do sistema excluir um determinado registro, a fim de evitat a exclusão de mais dados do que o desejado
 do ge
Seja uma locadora, onde o gerenciamento das locações é realizada na mesma tabela de gerenciamento de filmes, conforme a tabela abaixo:


**Tabela LOCAÇÃO/FILME**

|NOME|FILME |GENERO|
|:---- |:--- |:--- |
|JOAO CARLOS          | VELOCIDADE MAXIMA | AVENTURA |
|JOAO MARIA COSTA     | O PREDADOR        | FICCAO   |
|SAMUEL OLIVEIRA      | DICK TRACE        | POLICIAL |

Neste caso, a anomalia irar ocorrer quando ouver a necessidade de excluir o cliente João Carolos. Como neste exemplo não existe uma tabela própria para o gerencialmento de filmes, ao excluir o registro do cliente João Carlos, estará se perdendo a informação do gênero do filme, pois em nenhum outro cliente realizou a locação do mesmo, causando o impedimento da exclusão.

Para resolver este bloqueio de exclusão, assim como nas anomalias de inserção,  o gerenciamento  de clientes e filmes deve ser separado em duas tabelas, como em 


**Tabela LOCAÇÃO**

|NOME|FILME |
|:---- |:--- |
|JOAO CARLOS          | 1 | 
|JOAO MARIA COSTA     | 2 | 
|SAMUEL OLIVEIRA      | 3 | 

**Tabela FILME**

|CODIGO|FILME |GENERO|
|:---- |:--- |:--- |
|1     | VELOCIDADE MAXIMA | AVENTURA |
|2     | O PREDADOR        | FICCAO   |
|3     | DICK TRACE        | POLICIAL |

