

### Dado e Informação

Tendo como base um sistema de computador, dados podem ser definidos como um conjunto de bits (ou de caracteres em uma macro visão) para armazenamento de caracteres e textos no formato alfanumérico ou, até mesmo, de arquivos e imagens.

Basicamente, um dado é um conjunto alfanumérico ou de imagem, que não está agregado a nenhum conhecimento específico, tornando-o inutilizável para quem não souber em qual contexto está contido e o que exatamente representa, não podendo interpretá-lo.

Exemplo:

**Informação**

A informação é um dado agregado a um conhecimento. A informação pode ser interpretada e o conhecimento apenas pode ser visualizado.


### Banco de Dados

**Banco de Dados**

Banco de dados é uma coleção de dados referentes a um assunto ou propósito específico. 

>Banco de dados manuais: os dados armazenados em papel.
>Banco de dados automaticos: os dados amazenados em computadores.
>Banco de dados relacionais: há relações entre os seus dados (tabelas e entidades).


Todos os bancos de de dados relacionais mantêm algumas semelhaças entre si no que diz respeito às suas arquiteturas. Suas formas de armazenamento, componentes para criação de relacionamentos, estruturas para indexação de seus dados e organização interna, entre outras caractérsticas, são alguns dos benefícios gerados pela arquitetura de um banco relacional.

### Arquitetura de um Banco de Dados Relacional

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

**Campo**

Cada coluna da tabela está representando um campo, o qual armazena as informaçãoes sobre um tipo de dado.

| Codigo | Fornecedor | Endereco | Telefone |
| :----: | :----      | :-----   | :------  |

**Chave**

Chave é a coluna da tabela resposável por identificar os registros. O não uso de chave pode tornar o banco de dados vulnerável a diversos problemas: redundância de dados e inconsistência em relacionamento entre tabelas.


    Seja um cadastros de clientes, não se deve relacionar um cliente diretamente apenas por seu nome, pois há a possibilidade de haver dois clientes com exatamente o mesmo nome completo. Na situação de um sorteio de um prêmio e cliente o nome do cliente sorteado é Mário Anônio, porém no cadastro há dois clientes distintos com esse nome. Qual deles ficará com o prêmio?

    Uma solução seria realizar um sorteio com base no número e no telefone do cliente (solução conhecida como chave composta), além disso poderia ser usado o CPF do cliente, uma vez que o CPF é exclusivo para cada cliente (solução conhecida como chave primária). 



Chave Primaira: A chave primária  (do inglês, PK - Primary Key) é o caracterizada pelo fato de conter valores únicos. Por exemplo o CPF, na tabela seguinte:

| CPF | Nome |
| :----: | :----  |
| 001.001.001-01 | Carlos Drummond de Andrade    |
| 002.002.002-02 | Machado de Assis  |
| 003.003.003-03 | Erico Verissimo  |
| 004.004 004-04 | Machado de Assis   |

Chave Composta: A chave composta tanbém é caracterizada por conter um valor único, porém é formada por dois ou mais campos. Há chave composta pode admitir valores repetidos em suas colunas, mas as se considerar as duas simultaneamente essa possibilidade não pode ocorrer.   

