# Bases de Dados

##### Atualizado em 28-06-2021
###### A partir de: apontamentos das aulas teóricas, _Database Systems - A Practical Approach to Design, Implementation, and Management_; aulas práticas (incompleto)

## Aulas Teóricas

### Semana 1

Uma **base de dados** é uma coleção de dados partilhados, interrelacionados e usados para múltiplos objetivos. Num **sistema de ficheiros**, cada aplicação cria e mantém os ficheiros com os dados necessários para a sua execução. Problemas: alto nível de redundância, inconsistência da informação, inflexibilidade, acessos concorrentes, isolamento e integridade dos dados, elevados custos de manutenção.

Um sistema de base de dados pretende que um programa possa ser modificado, sem que isso implique alterações nos restantes programas que usam os mesmos dados, baixando os custos de manutenção. Os dados são integrados num **sistema de gestão de base de dados**: conjunto de programas que permitem armazenar e manipular dados, fornecendo-os aos programadores e utilizadores finais tal como são pedidos. O sistema de gestão de base de dados reserva para si os privilégios de acesso físico às bases de dados, sendo quase independente do sistema operativo, tal como os dados consultados e alterados.

**Níveis de abstração**:
* _Interno_ (menor) - representação física da base de dados no computador. Descreve como os dados são armazenados na base de dados, otimizando o desempenho e o armazenamento;
* _Concetual_ (intermédio) - visão comunitária da base de dados. Descreve quais dados são armazenados na base de dados e as relações entre eles. Contém a estrutura lógica de toda a base de dados, independente de quaisquer restrições de armazenamento;
* _Externo_ ou _de Visualização_ (maior) - visão de cada utilizador da base de dados. Descreve qual parte da base de dados é relevante para cada utilizador.

A **independência dos dados** pode ser:
* _Física_ - alterar aspetos relativos à implementação física da base de dados (otimizar desempenho ou segurança, alterar estruturas de armazenamento) sem alterar o esquema concetual;
* _Lógica_ - alterar o modelo concetual, adicionando atributos a entidades já existentes ou criando entidades sem alterar a visão de utilizador.

Arquitetura **ANSI-SPARC** (_American National Standards Institute - Standards Planning And Requirements Committee_):
* **Base de Dados** (organização de dados físicos) **→ Esquema Interno → Esquema Concetual → Visão 1, ..., Visão N**

Um sistema de gestão de base de dados é um sistema de gestão e armazenamento de dados, capaz de aceder eficientemente a grandes quantidades de dados. Serve de intermediário entre o servidor e o cliente, sendo a única entidade responsável pela segurança, integridade e validade dos dados armazenados. Possui:
* Suportes para modelos de dados e linguagens de alto nível:
  * _Data Definition Language_ (DDL) - define a estrutura da base de dados e a informação a armazenar;
  * _Data Manipulation Language_ (DML, _query language_) - obtém, armazena, altera ou elimina informação da base de dados, podendo ser autónoma ou integrada numa linguagem hospedeira de alto nível;
* Gestão de transações - conjuntos de operações perfeitamente delimitadas em que garantidamente são executadas todas as instruções ou então nenhuma produzirá efeito sobre a base de dados, seguindo as propriedades ACID:
  * _Atomicidade_ - as instruções cliente-servidor são indivisíveis (ou são todas executadas (`COMMIT`) ou nenhuma (`ROLLBACK`));
  * _Consistência_ - após uma transação, a base de dados deve manter-se consistente;
  * _Isolamento_ - devem evitar-se interferências múltiplas, dando a ilusão de que cada instrução é a única a ser executada num dado momento;
  * _Durabilidade_ (Persistência) - após um `COMMIT`, os seus efeitos são duráveis/persistentes/não-voláteis na base de dados e só podem ser desfeitos/alterados por outras transações;
* Controlo de acesso;
* Capacidade de recuperação de falhas.

Um sistema de gestão de base de dados deve ser **seguro** (protegendo os dados e controlando privilégios de acesso), **íntegro** (todos os dados são válidos e não se contradizem mutuamente) e **tolerante a falhas** (repondo a informação para um estado válido anterior à falha no _hardware_/_software_ através de _back-ups_ e registos).

Numa arquitetura cliente-servidor,
1. Cliente estabelece a ligação com o servidor;
2. Autenticação pelo sistema de gestão de base de dados (não pela máquina);
3. Cliente envia pedido ao servidor em SQL (_Structured Query Language_);
4. Servidor recebe pedido, verifica privilégios de utilizador;
5. Servidor responde a cliente (acesso aceite/negado).

O desenvolvimento dos sistemas de bases de dados compreende as seguintes etapas: _information system_, _database planning_, _system definition and user view_, _requirements collection and analysis_, _centralized and view integration approaches_, _database design_, _conceptual database design_, _logical database design_, _physical database design_, _database management system selection_, _application design_, _transaction_, _prototyping_, _implementation_, _data conversion and loading_, _testing_, _operational maintenance_. Segue os seguintes critérios de produção: validade estrutural, simplicidade, expressabilidade, não-redundância, partilhabilidade, extensibilidade, integridade, representação diagramática.

Uma **aplicação de base de dados** é um programa que interage com a base de dados. Um **sistema de base de dados** é uma coleção de aplicações que interagem com o sistema de gestão de base de dados e a própria base de dados. **Ficheiros** são coleções de registos com dados ordenados logicamente. **Metadados**/**Dicionário de Dados**/**Catálogo do Sistema** correspondem à descrição dos dados. **Abstração de Dados** implica poder alterar a definição interna de um objeto sem afetar os seus utilizadores, desde que a definição externa se mantenha. Uma **entidade** é um objeto distinto na organização representada na base de dados, um **atributo** é uma propriedade que descreve algum aspeto do objeto, uma **relação** é uma associação entre entidades. A **SQL** é uma DML que permite acesso controlado à base de dados através de sistemas de segurança, integridade, controlo de concorrência, recuperação de dados e catálogo.

Um sistema de gestão de base de dados é constituído por:
* **_Hardware_**:
  * _Backend_ - parte do sistema de gestão de base de dados que acede à base de dados;
  * _Frontend_ - parte do sistema de base de dados que faz interface com o utilizador;
* **_Software_**;
* **Dados** - ponte entre os componentes tecnológicos e humanos;
* **Procedimentos** - instruções e regras que definem o desenho e o uso da base de dados;
* **Pessoas**:
  * Administrador de Dados - responsável pela gestão do recurso de dados, incluindo planeamento da base de dados, desenvolvimento e manutenção de padrões, políticas e procedimentos;
  * Administrador de Base de Dados - resposável pelo desenvolvimento da base de dados com desempenho satisfatório;
  * _Designers_ de Base de Dados:
    * Lógicos (o quê) - identificam os dados e as relações/restrições entre eles;
    * Físicos (como) - decidem como implementar a base de dados;
  * Criadores de Aplicações - desenvolvem programas que possam ser usados pelos utilizadores para aceder à base de dados;
  * Utilizadores - ingénuos (se desconhecem o sistema de gestão de base de dados) ou sofisticados (se conhecem o sistema de gestão de base de dados).

Um sistema de gestão de base de dados permite: controlo de dados redundantes, consistência de dados, maior informação num menor conjunto de dados, partilha de dados, maior integridade de dados, maior segurança, aplicação de padrões, economia de escala, equilíbrio de requisitos conflituosos, fácil acesso e responsividade, maior produtividade, manutenção melhorada pela independência dos dados (alterações nas aplicações não afetam os dados), maior concorrência, melhores serviços de _back-up_ e recuperação. No entanto, é mais complexo, ocupa mais espaço, tem custos maiores (_hardware_, _software_ e conversão de dados), desempenho mutável, maior impacto em caso de falha.

Um **sistema de gestão de base de dados relacional** aceita comandos SQL gerados a partir de uma variedade de interfaces com o utilizador, produz planos de avaliação de consulta, executa-os e devolve os resultados:
* Otimizador de consultas - usa a informação de como os dados estão guardados para produzir um plano de execução eficiente;
* Plano de execução - plano para avaliar uma consulta, geralmente apresentado como uma árvore de operadores relacionais, que avaliam as consultas submetidas sobre os dados;
* Gestão de _buffers_ - traz as páginas de disco para a memória principal conforme necessário;
* Gestor de espaço em disco - aloca, desaloca, lê e escreve páginas trazidas pelo _buffer_;
* Gestor de transações - garante que as transações solicitam e libertam os trincos segundo um protocolo de bloqueio apropriado e agenda a execução das transações;
* Gestor de trincos - mantém um registo de pedidos de trincos e de concessões destes sobre objetos da base de dados;
* Gestor de recuperações - responsável por manter um _log_ e restaurar o sistema para um estado consistente após uma falha;
* Processamento de consultas - transformar uma consulta escrita numa linguagem de alto nível numa estratégia de execução correta e eficiente e executá-la para aceder e obter os dados pretendidos;
* Tempo de execução da consulta - soma dos tempos de execução de todas as operações individuais que compõem a consulta.

O processamento de uma consulta segue as seguintes fases:
* **Decomposição**:
  * _Análise_ - verifica se as relações e os objetos especificados na consulta estão definidos no catálogo do sistema e se as operações sobre os objetos são viáveis;
  * _Normalização_ - torna a consulta facilmente manipulável;
  * _Análise Semântica_ - rejeita consultas mal formuladas (componentes não contribuem para a geração do resultado) ou contraditórias (se as suas instruções não puderem ser satisfeitas);
  * _Simplificação_ - torna a consulta mais fácl e eficiente pela eliminação de redundâncias e instruções desnecessárias;
  * _Reestruturação da Consulta_ - implementação mais eficiente;
* **Otimização** - encontrar um bom plano de avaliação (mais eficiente, com menor custo) para uma determinada consulta:
  * _Plano de avaliação_ - árvore com anotações adicionais em cada nó, indicando os métodos de acesso a usar para cada relação e o método de implementação para cada operador relacional;
* **Geração de Código**;
* **Execução**.

Um sistema de gestão de base de dados relacional mantém informação de todas as tabelas e índices que contém. O **catálogo** tem dados globais ao sistema, estatísticas sobre tabelas e índices (cardinalidade, tamanho, altura, gama), informação sobre utilizadores e privilégios e o próprio catálogo. Segue as doze regras de Codd:
1. Todos os dados, incluindo o próprio dicionário de dados, são representados de uma só forma;
2. Cada elemento é bem determinado pela combinação do nome da tabela onde está armazenado, valor da chave primária e respetiva coluna (atributo);
3. Valores nulos (`NULL`) são suportados para representar informação não disponível ou não aplicável;
4. Os metadados são representados e acedidos da mesma forma que os próprios dados;
5. Deve existir pelo menos uma linguagem que: manipule dados; defina dados, _views_, restrições de integridade, acessos/autorizações; manipule transações;
6. Numa _view_, todos os dados atualizáveis que forem modificados devem ver essas modificações traduzidas nas tabelas-base;
7. Capacidade de tratar uma tabela como se fosse um simples operando;
8. Independência física - alterações na organização física dos ficheiros da base de dados ou nos métodos de acesso a esses ficheiros (nível interno) não devem afetar o nível concetual;
9. Independência lógica - alterações no esquema da base de dados (nível concetual), que não envolvam remoção de elementos, não devem afetar o nível externo;
10. As restrições de integridade devem poder ser especificadas numa linguagem relacional e armazenadas no dicionário de dados;
11. O facto de uma base de dados estar centralizada ou dispersa não deve repercutir-se na manipulação dos dados;
12. Se existir no sistema uma linguagem de mais baixo-nível, esta não pode permitir ultrapassar as restrições de integridade e segurança.

A SQL é uma linguagem não procedimental, ou seja, especifica-se a informação desejada, mas não o modo de obtenção desta. Um _query block_ é um bloco-base de interrogação que permite a implementação das operações de seleção, projeção e junção da álgebra relacional, mas não especifica a ordem pela qual as operações são executadas. Linguagens de quarta geração são geradores de formulários, relatórios, gráficos e aplicações.

### Semana 2

Um **modelo de dados** é uma coleção integrada de conceitos para descrever e manipular dados, relações e restrições entre dados, constituída por três componentes:
* **Parte Estrutural** - conjunto de regras a partir das quais uma base de dados pode ser construída;
* **Parte Manipulável** - tipo de operações que são permitidas sobre os dados (atualização e recuperação de dados, alteração estrutural da base de dados);
* **Conjunto de Restrições de Integridade** - assegura a precisão dos dados.

Os **modelos de dados baseados em objetos** usam conceitos como **entidade** (objeto distinto a representar numa base de dados), **atributo** (propriedade que descreve aspetos do objeto que se pretende guardar) e **relação** (associação entre entidades): entidade-relação, semântica, funcional, orientado a objetos. Os **modelos de dados baseados em registos** usam um número de registos de formato fixo, possivelmente de tipos diferentes, que definem um número fixo de campos, e são usados para especificar a estrutura geral da base de dados e uma descrição de alto nível da implementação, com o inconveniente de não providenciar instalações adequadas para especificar restrições sobre os dados:
* _Modelo de dados relacional_ - baseado no conceito de relações matemáticas, em que dados e relações são representados como tabelas independentes entre si;
* _Modelo de dados de rede_ - os dados são representados como coleções de registos e as relações como conjuntos, organizados em estruturas gráficas gerais como nós/segmentos (registos) e arestas (relações);
* _Modelo de dados hierárquico_ - tipo restrito de modelo de dados de rede, em que os registos e as relações são representados num gráfico em árvore.

**Sistemas relacionais** adotam uma abordagem declarativa (especificam _quaus_ dados devem ser recuperados); **sistemas de rede e hierárquicos** adotam uma abordagem navegacional (especificam _como_ os dados devem ser recuperados).

Um **modelo de dados físico** descreve como os dados são armazenados no computador (modelo de uniformização, memória de quadro). A **modelação/_design_ concetual** de base de dados descreve o processo de construir um modelo de informação usado numa organização, independente de detalhes de implementação. O **modelo de dados** é independente de quaisquer detalhes de implementação, enquanto o **modelo lógico** assume conhecimento do modelo de dados subjacente do sistema de gestão de base de dados de destino.

Um sistema de gestão de bases de dados tem as seguintes funções:
* Armazenamento, recuperação e atualização de dados;
* Possui um catálogo acessível pelo utilizador, permitindo recolher e armazenar informação sobre dados centralmente, definir significados dos dados, simplificar comunicações, identificar redundâncias e inconsistências mais facilmente, gravar mudanças sobre a base de dados, determinar impactos de alterações antes de serem implementadas, reforçar segurança, assegurar integridade de dados, providenciar informação auditorial;
* Suporte de transações - ou todas as atualizações são relativas a uma dada transação são feitas, ou nenhuma;
* Serviços de controlo de concorrência, assegurando que a base de dados é atualizada corretamente quando vários utilizadores a estão a usar ao mesmo tempo;
* Serviços de recuperação de dados em caso de falha;
* Serviços de autorização de acesso (_segurança_: proteção da base de dados contra acesso não autorizado, intencional ou acidental);
* Suporte para comunicação de dados - o sistema de gestão de bases de dados recebe pedidos como mensagens de comunicação e responde de forma similar, o que não implica que a base de dados tenha de estar distribuída através da rede, mas sim que os utilizadores devem ser capazes de aceder a uma base de dados centralizada a partir de localizações remotas;
* Serviços de integridade, assegurando que tanto os dados da base de dados tanto as alterações feitas seguem determinadas regras que não podem ser realizadas (_restrições_);
* Serviços para promover a independência de dados;
* Serviços de utilidade - importação/exportação de dados, monitorização, análise de estatísticas, reorganização de índices, recolha e realocação de lixo.

Os objetivos da SQL são criar a base de dados e estruturas da relação, realizar tarefas básicas de gestão de dados (inserção, modificação e eliminação), realizar _queries_ simples e complexos, devendo ser uniforme para diferentes sistemas de gestão de bases de dados. Uma declaração em SQL consiste em palavras reservadas (de formato e significado fixos predefinidos (_literais_)) e palavras definidas pelo utilizador. A maioria dos comandos SQL são _case-insensitive_. **Literais** são constantes utilizadas declarações de SQL, cujos valores não numéricos devem estar entre aspas simples:
* `SELECT` - recupera e mostra dados de uma ou mais tabelas da base de dados;
  * `*` - simboliza todos os atributos de uma tabela (quando há junção de várias);
  * `DISTINCT` - impede a repetição de dados, embora possa aumentar o tempo de execução;
* `FROM` - especifica a(s) tabela(s) a ser(em) usada(s);
* `WHERE` - filtra as linhas de acordo com uma certa condição, com cinco predicados (comparação, alcance, pertença a um conjunto, padronização, ausência de valores):
  * Operadores: `=`, `<>`, `!=`, `<`, `<=`, `>`, `>=`, `AND`, `OR`, `NOT`, `IN`, `LIKE`;
    * `IN` - testa se o valor de um dado é compatível com uma lista de valores;
    * `%` - representa qualquer sequência de zero ou mais carateres;
    * `_` - representa um único caratere;
* `GROUP BY` - forma grupos de colunas com o mesmo valor;
* `HAVING` - filtra o grupo de acordo com uma certa condição;
* `ORDER BY` - especifica a ordem do _output_, permitindo ordenar por ordem ascendente (`ASC`) ou descendente (`DESC`);
* `COUNT` - retorna o número de valores de uma coluna específica;
* `SUM` - retorna a soma dos valores de uma coluna específica;
* `AVG` - retorna a média dos valores de uma coluna específica;
* `MIN` - retorna o mínimo dos valores de uma coluna específica;
* `MAX` - retorna o máximo dos valores de uma coluna específica;
* `ANY` - a condição é verdadeira se é satisfeita por pelo menos um valor;
* `ALL` - a condição é verdadeira se é satisfeita por todos os valores;
* `JOIN` - combina informação de duas tabelas ao formar pares de linhas relacionadas;
* `OUTER JOIN` - mantém linhas que não satisfazem a condição de `JOIN`;
* `LEFT OUTER JOIN` - inclui as linhas comuns e as da primeira tabela que não são compatíveis com a segunda;
* `RIGHT OUTER JOIN` - inclui as linhas comuns e as da segunda tabela que não são compatíveis com a primeira;
* `FULL OUTER JOIN` - inclui as colunas comuns e as que não são compatíveis entre as duas tabelas;
* `ALIAS` - qualifica o nome de uma coluna sempre que haja ambiguidade quanto ao seu nome original;
* `EXISTS` - verdadeiro se existe pelo menos uma linha correspondente, falso se não;
* `UNION` - contém todas as colunas presentes em ambas as tabelas;
* `INTERSECT` - contém todas as colunas comuns entre as duas tabelas;
* `EXCEPT` - contém todas as colunas que estão na primeira tabela, mas que não estão na segunda;
* `INSERT INTO <tabela> VALUES <valores>` - insere novos valores numa tabela;
* `UPDATE <tabela> SET <coluna>` - atualiza uma tabela com um novo valor;
* `DELETE FROM <tabela>` - elimina uma tabela. 

Uma **_subquery_**/**_query_ aninhada** utiliza os resultados de um `SELECT` interno como condição para o `SELECT` externo. Pode ser **escalar** (retorna um valor único (linha ou coluna)), **de linhas** (retorna múltiplas colunas e uma única linha) ou **de tabela** (retorna múltiplas linhas e colunas).

### Semana 3

**Modelos de dados** são ferramentas de comunicação. Veem dados ao invés de aplicações, eliminam redundâncias, favorecem a partilha de dados entre aplicações. São constituídos pela identificação, análise e registo de políticas da organização acerca dos dados e definidos a três níveis:
* _Concetual_ - representação fiel da realidade, sem atender a quaisquer constrangimentos;
* _Lógico_ - adaptação do modelo concetual a um modelo de dados específico independente de qualquer sistema de gestão de bases de dados;
* _Físico_ - adaptação do modelo lógico às características do sistema informático.

As **técnicas de modelação** seguem: do particular para o geral (_bottom-up_, abordagem da Teoria da Normalização (Codd, 1970), adequada a pequenos projetos); do geral para o particular (_top-down_, abordagem do Modelo Entidade-Associação, adequada a grandes projetos).

O **modelo entidade-associação** é especificado a nível gráfico (através de um diagrama entidade-associação) e a nível descritivo (pela especificação de cada componente do modelo). Uma _entidade_ é qualquer objeto ou conceito com interesse para a organização a respeito de qual é guardada informação, representada por substantivos inequívocos. Um _atributo_ é qualquer propriedade de uma entidade, indivisível, representada por verbos, que pode ser identificador (chaves) ou descritor. Uma _associação_ relaciona duas entidades entre si (associação binária), várias entidades entre si (associação complexa) ou uma entidade consigo própria (associação unária). Um **diagrama entidade-associação** é um grafo que representa entidades, associações e associações com atributos, com notação de Chen (1976) ou notação pé-de-galinha.

Uma associação pode ter diferentes graus:
* **1:1** - a cada ocorrência da entidade A está associada apenas uma ocorrência da entidade B (ou nenhuma); a cada ocorrência da entidade B está associada apenas uma ocorrência da entidade A (ou nenhuma);
* **1:N** - a cada ocorrência da entidade A está associada uma, várias ou nenhuma ocorrência da entidade B; a cada ocorrência da entidade B está associada apenas uma ocorrência da entidade A (ou nenhuma);
* **N:M** - a cada ocorrência da entidade A está associada uma, várias ou nenhuma ocorrência da entidade B; a cada ocorrência da entidade B está associada uma, várias ou nenhuma ocorrência da entidade A. Estas associações não são suportadas pelo sistema de gestão de base de dados, pelo que devem ser decompostas em associações 1:N.

Uma entidade pode participar de forma **obrigatória** (todas as ocorrências dessa entidade têm de estar associadas a alguma ocorrência de outra entidade que participe na associação) ou de forma **não-obrigatória** (a entidade pode ter ocorrências não associadas a qualquer ocorrência de outra entidade que participe na organização).

**Associações complexas** relacionam mais do que duas entidades entre si e devem ser usadas apenas quando o conceito inerente à associação não pode ser representado por um conjunto de associações binárias. Pode ter diferentes graus:
* **1:1:1** - a cada par de ocorrências das entidades B e C está associada apenas uma ocorrência da entidade A (ou nenhuma). Análogo para B e C;
* **1:1:N** - a cada par de ocorrências das entidades B e C está associada uma, várias ou nenhuma ocorrência da entidade A; a cada par de ocorrências A e B/C está associada apenas uma ocorrência de C/B (ou nenhuma). Análogo para **1:N:M** e **N:M:P**.

A decomposição de associações M:N em 1:N permite: ressaltar a existência de entidades não identificadas no início; facilitar a análise do diagrama em termos de consistência; dar ao modelo uma forma adequada para passos subsequentes do método. Não há transitividade, logo, só se aceitam as leituras diretamente representadas no diagrama entidade-associação. A não compreensão/definição de uma associação levam a armadilhas de ligação: _chasm trap_ (ausência de informação, quando um modelo sugere a existência de uma relação entre entidades, mas não existe uma associação entre ocorrências de certas entidades) e _fan trap_ (ambiguidade de informação, onde o modelo apresenta uma relação entre entidades, mas a associação entre ocorrências de certas entidades é ambígua).

A simplicidade e capacidade de representação do modelo entidade-associação contribuíram de forma significativa para o sucesso do modelo relacional. As associações são identificadas por concatenação dos identificadores das entidades associadas, exceto nos casos em que as entidades se associam várias vezes entre si. No geral, evitar ocorrências em que os identificadores de outras entidades tenham valores nulos, evitar repetição de identificadores, criar tabelas para associações apenas quando estritamente necessário. O modelo entidade-associação tem uma abordagem _top-down_ pois começa por identificar os dados importantes (entidades e associações) a serem representados antes de adicionar detalhes, como informação sobre os dados (atributos) e restrições sobre estes. Uma **rede semântica** é um modelo orientado a objetos que representa entidades e associações com símbolos específicos.

Um **domínio de atributo** é o conjunto de valores possíveis para cada atributo; vários atributos podem partilhar um domínio e domínios podem conter subdomínios. Atributos podem ser: _simples_/_atómicos_ (um único componente independente, que não pode ser dividido); _compostos_ (vários componentes independentes que podem ser divididos); _de valor único_ (possuem um valor único para cada ocorrência); _de valor múltiplo_ (possuem vários valores para cada ocorrência); _derivados_ (representam um valor derivável de outro atributo ou conjunto de atributos, não necessariamente do mesmo tipo). Atributos podem ser **chaves**, que podem ser: _candidatas_ (conjunto mínimo de atributos que identifica de modo único cada ocorrência de entidades, não suportando o valor nulo); _primárias_ (identifica cada ocorrência de entidades de modo único); _compostas_ (contém dois ou mais atributos).

Uma entidade pode ser **forte** (não depende da existência de outra, cada ocorrência é facilmente identificável) ou **fraca** (depende da existência de outra e não é possível identificá-la apenas com os seus atributos).

### Semana 4

Cada tabela deve estar **normalizada**: não conter grupos repetitivos; ter atributos totalmente dependentes da chave, se esta for composta; não ter dependências entre atributos não chave. Se uma tabela contiver apenas uma lista de nomes associados ao mesmo atributo, esta pode ser removida. Se, no futuro, os atributos dessa tabela forem dependências necessárias, então a tabela deve permanecer como uma entidade. Se a lista inclui valores não possuídos por nenhuma entidade, a tabela deve manter-se. Se não é necessário representar a entidade como uma tabela, deve colocar-se `*` na tabela correspondente e redesenhar o diagrama entidade-associação.

**Subentidades** são entidades mais particulares dependentes de uma entidade geral que, em conjunto com a entidade-mãe, fornecem toda a informação disponível.

**Análise dos dados** é o estudo das propriedades dos dados independentemente das transações a operar.

Os passos para o desenho de primeiro nível da conceção final do esquema relacional são:
1. Esboçar um primeiro esquema para ganhar sensibilidade ao problema;
2. Elaborar uma lista de transações que o modelo terá de suportar;
3. Elaborar uma lista de atributos;
4. Elaborar uma lista preliminar de entidades obrigatórias com respetivos identificadores;
5. Desenhar um diagrama entidade-associação, incluindo o grau das associações e os tipos de participação;
6. Verificar se o diagrama suporta as transações, alterando-o se necessário; olhar para os possíveis erros de interpretação e decidir o seu impacto;
7. Construir o esquema relacional correspondente ao diagrama entidade-associação, retirando todos os atributos usados da lista de atributos;
8. Adicionar os atributos às tabelas de modo a mantê-las normalizadas; se tal criar dependências funcionais, remover os atributos e tornar a adicioná-los à lista de atributos inicial;
9. Se algum atributo não puder ser adicionado às tabelas existentes, expandir o modelo e, se necessário, voltar ao passo 5;
10. Decidir se alguns outros atributos ou transações deverão ser incluídos (e.g., para permitir futuros desenvolvimentos); para transações, passo 6; para atributos, passo 8;
11. Verificar se a escolha de entidades, associações e atributos permanece apropriada, se as tabelas estão normalizadas, se todas as transações são suportadas; se forem necessárias alterações, repetir o processo;
12. Apagar entidades supérfluas.

### Semana 5

O **modelo concetual de dados** é a representação de um conjunto de objetos e das suas associações, resultado de um processo de abstração em que objetos relevantes, associações entre eles e atribuos (características) são selecionados. A relevância de um objeto, associação ou atributo é definida de acordo com os objetivos do modelo. Os atributos têm valores específicos que pertencem a domínimos e que, mesmo podendo variar de valor, pertencem sempre a esse domínio.

O **modelo relacional** pressupõe que os dados podem ser tratados da mesma forma que as relações matemáticas. Entidades são objetos e respetivas associações, caracterizadas por terem um conjunto de atributos denotado por `E(A_1, A_2, ..., A_n)` onde `A_i: E → D_i` é uma função cujo contradomínio `D_i` é denominado domínio do atributo `A_i`. Diferentes entidades são representadas por tuplos diferentes, Dois tuplos são diferentes se têm valores diferentes em pelo menos um atributo. Uma **base de dados relacional** é uma coleção de relações cujo conteúdo varia ao longo do tempo. Um **esquema relacional** é uma destrição da estrutura das relações numa base de dados relacional.

Para realizar interrogações acerca das propriedades das entidades representadas num modelo precisa-se de uma linguagem apropriada: **álgebra relacional**. Uma interrogação (_query_) em álgebra relacional consiste numa coleção de operações sobre relações. Cada operador aceita um ou dois operandos (relações) e devolve como resultado uma relação. A álgebra relacional é uma linguagem teórica com operações que atuam em uma ou mais relações para definir outra relação sem alterar as relações originais. Como os operandos e os resultados são relações, a saída de uma operação pode tornar-se a entrada de outra, permitindo que as expressões sejam aninhadas - fecho. Cada _query_ descreve um procedimento passo a passo para calcular a resposta desejada, baseado na ordem em que operadores são aplicados:
* **Projeção** (`π_x (R)`) - se a relação `R` é representada como uma tabela, a operação de projeção de `R` sobre o conjunto de atributos `x` é interpretada como a seleção das colunas de `R` que correspondem aos atributos de `x` e a eliminação das linhas duplicadas na tabela obtida;
* **Restrição**/**Seleção** (`σ_p (R)`) - sendo `R` interpretada como uma tabela, a operação de restrição poe ser interpretada como a eliminação das linhas da tabela `R` que não satisfazem a condição `p`;
* **Operações com Conjuntos** - sejam `R1` e `R2` com igual número de atributos e mesmos domínios de atributos correspondentes (esquemas relacionais compatíveis):
  * **União** - `R1 ∪ R2` é o conjunto dos tuplos de `R1` e `R2`;
  * **Diferença** - `R1 - R2` é o conjunto dos tuplos de `R1` que não pertencem a `R2`;
  * **Interseção** - `R1 ∩ R2` é o conjunto dos tuplos comuns a `R1` e a `R2`;
  * **Produto Cartesiano** - `R1 x R2` é a concatenação dos atributos de `R1` e `R2`;
  * **Junção Natural** - relação cujo conjunto de atributos são os atributos de `A` e os atributos de `B` que não aparecem na condição de junção. Os tuplos da tabela são obtidos pela concatenação dos tuplos de `A` com os tuplos de `B` sempre que os valores de `x` sejam iguais;
  * **Equijunção** - relação cujo conjunto de atributos é formado pelos atributos de `A` e `B`. Os tuplos da tabela são obtidos pela concatenação dos tuplos de `A` com os tuplos de `B` sempre que os valores dos atributos de `x` são iguais aos atributos de `y`;
  * **Junção com Condições** - relação que contém os tuplos do produto cartesiano de `R` e `S` que satisfazem a condição `F`. Quando a condição `F` contém apenas igualdades, obtém-se a _equijunção_;
  * **Junção Externa** - a _junção externa à esquerda_ de duas relações `R` e `S`, `R ⟕ S`, é uma junção onde os tuplos de `R` que não tenham correspondência em `S` também são incluídos na relação resultado e os valores em falta na segunda relação são colocados a `null`. Analogamente para _junção externa à direita_ (`R ⟖ S`) e _junção externa à esquerda e à direita_ (`R ⟗ S`);
* **Divisão** - valores de `x` tais que o par `(x, y)` ocorre em `A` para todos os valores de `y` que ocorrem em `B`;
* **Renomeação**/**Rebatização** - usar o operador `ρ` para explicitamente renomear relações ou atribuir um nome ao resultado de uma operação;
* **Operações de Agregação** - não são operações de álgebra relacional, mas são usados pelo operador de agrupamento. Aplicam-se aos atributos (colunas) e são usados para sumarizar ou agregar os valores de um atributo da relação (`COUNT`, `MAX`, `MIN`, `AVG`, `SUM`);
* **Operação de Agrupamento** - o operador `γ` permite formar grupos numa relação e/ou agregar colunas. Tem um índice, uma lista `L`, em que cada elemento é um atributo da relação `R` ao qual é aplicado `γ` ou um operador de relação aplicado a um atributo da relação.

No **modelo relacional**, toda a informação é logicamente estruturada em relações (tabelas). Os objetivos do modelo relacional são: permitir um elevado grau de independência de dados; providenciar bases substanciais para lidar com problemas de semântica, consistência e redundância de dados, introduzindo o conceito de _relações normalizadas_ (relações sem grupos repetidos); permitir a expansão de linguagens de manipulação de dados orientadas a conjuntos. Terminologia:
* _Relação_ - tabela com colunas e linhas, usada para armazenar informação sobre os objetos a serem representados numa base de dados;
* _Atributo_ - coluna nomeada de uma relação, cujas linhas correspondem a registos individuais, podendo surgir em qualquer ordem sem alterar a relação;
* _Domínio_ - conjunto de valores permitidos para um ou mais atributos, permitindo ao utilizador definir num local central o significado e origem dos valores que um atributo pode possuir;
* _Tuplo_ - linha de uma relação, podendo aparecer em qualquer ordem sem alterar a relação. A estrutura de uma relação, em conjunto com a espeficiação dos domínios e restrições de valores possíveis, usualmente fixa, é conhecida como _intenção_. Os tuplos são alteráveis ao longo do tempo e conhecidos como _extensão_ ou _estado_ de uma relação;
* _Grau_ - número de atributos de uma relação (um, relação unária; dois, relação binária; três, relação ternária; quatro ou mais, relação n-ária);
* _Cardinalidade_ - número de tuplos de uma relação, que altera de cada vez que se acrescentam/eliminam tuplos;
* _Base de Dados Relacional_ - coleção de relações normalizadas com nomes distintos.

O **produto cartesiano** de dois conjuntos é o conjunto de todos os pares tais que o primeiro elemento é membro do primeiro conjunto e o segundo elemento é membro do segundo conjunto. Qualquer subproduto de um produto cartesiano é uma relação. Um **esquema de relação** é uma relação nomeada constituída por pares de conjuntos de atributos e nomes de domínios. Um **esquema de base de dados relacional** é um conjunto de esquemas de relação, cada um com nomes distintos. As relações integram as seguintes propriedades:
* Cada relação num esquema relacional tem um nome único;
* Cada célula de uma relação tem um valor único (atómico);
* Cada atributo tem um nome distinto;
* Todos os valores de um atributo pertencem ao mesmo domínio;
* Cada tuplo é único;
* A ordem dos atributos não tem significado;
* A ordem dos tuplos não tem significado, teoricamente.

**Chaves relacionais** identificam um ou mais atributos que identificam de modo único cada tuplo numa relação:
* _Superchave_ - atributo ou conjunto de atributos que identifica de modo único um tuplo interno a uma relação;
* _Chave Candidata_ - superchave de forma que nenhum subconjunto próprio seja uma superchave dentro da relação, devendo ser única e irredutível. Quando a chave consiste em mais que um atributo, dá-se o nome de _chave composta_;
* _Chave Primária_ - chave candidata que é selecionada para identificar tuplos exclusivamente dentro da relação. As outras chaves candidatas são chamadas de _chaves alternativas_;
* _Chave Estrangeira_ - atributo ou conjunto de atributos internos a uma relação que corresponde(m) à chave candidata de outra relação.

Representação de esquemas de bases de dados relacionais: dar o nome de uma relação seguida dos respetivos atributos entre parêntesis, com a chave primária sublinhada.

**Restrições de Integridade** - como cada atributo tem um domínio associado, existem restrições (restrições de domínio) que formam restrições ao conjunto de valores permitidos para os atributos de relações:
* _Null_ - representa um valor para um atributo que é desconhecido no momento ou não aplicável a um tuplo;
* _Integridade de Entidade_ - numa relação de base, nenhum atributo de uma chave primária pode ser _null_;
* _Integridade Referencial_ - se numa relação existe uma chave estrangeira, ou o valor da chave estrangeira corresponde a um valor da chave candidata de algum tuplo da relação inicial ou o valor da chave estrangeira é _null_ na sua totalidade;
* _Restrições Gerais_ - regras adicionais especificadas por utilizadores ou administradores da base de dados que definem ou restringem algum aspeto da organização.

### Semana 7

**Teoria da Normalização** - obtenção de um modelo que garanta redundância mínima, facilidade de manutenção e estabilidade face a futuras alterações. É um processo de estruturação de tabelas de uma base de dados de modo a minimizar a redundância dos dados nela armazenados.

**Dados redundantes** - podem existir dados repetidos úteis (duplicados) em que, removendo-os, há perda de informação. Dados repetidos redundantes são dados que, sendo apagados de determinado tuplo, podem ser obtidos a partir de outro. Relações que possuem dados redundantes podem vir a ter _anomalias_ de:
* _Inserção_ - tem de se inserir toda a informação duplicada, comcuidado para não criar inconsistências com a informação já existente; não é possível criar novos tuplos com informação necessária se a chave da relação for nula;
* _Eliminação_ - um tuplo que possua informação única, se for removido, leva à perda desses mesmos dados;
* _Modificação_ - para alterar um atributo de um dado tuplo, devem atualizar-se todos os outros tuplos que possuam o mesmo atributo.

**Dependências Lógicas** - associações lógicas descritas entre os atributos de uma relação. Podem ser funcionais, multivalor ou de junção.

**Dependências Funcionais** - seja `R(A_1, A_2, ..., A_n)` um esquema de relação e `X` e `Y` subconjuntos de `{A_1, A_2, ..., A_n}` não vazios. Há uma dependência funcional entre `X` e `Y` (`X → Y` (X determina Y)) se em qualquer instante `t` quaisquer tuplos de `R` com o mesmo valor de `X` têm necessariamente o mesmo valor de `Y`.

**Chave Candidata** - seja a relação `R(A_1, A_2, ..., A_n)` e `x` um conjunto de atributos de `R` (`x ⊆ {A_1, A_2, ..., A_n}`). `x` é chave de `R` se:
* `∀i x → A_i, i = 1, 2, ..., n` - determina funcionalmente todos os atributos de `R`;
* `∄(y ⊊ x): ∀y → A_i, i = 1, 2, ..., n` - não existe um subconjunto próprio de `x` que determine todos os atributos de `R`.

**Superchave** - qualquer conjunto de atributos `x` que determine funcionalmente todos os atributos de `R`.

**Chave Primária** - chave candidata escolhida em que nenhuma das ocorrências pode ter valor nulo.

Toda a relação tem uma chave.

Propriedades básicas das dependências funcionais - **axiomas de Armstrong**:
* _Unicidade_ - se `f: X → Y` e `g: X → Y`, então `f = g`;
* _Reflexibilidade_ - se `X ⊇ Y`, então `X → Y`;
* _Transitividade_ - se `X → Y` e `Y → Z`, então `X → Z`;
* _Aumento_ - se `X → Y`, então `XZ → YZ`, para qualquer `Z`.

Propriedades derivadas das dependências funcionais:
* _Distributividade_ (decomposição) - se `X → YZ`, então `X → Y` e `X → Z`;
* _União_ - se `X → Y` e `X → Z`, então `X → YZ`;
* _Pseudotransitividade_ - se `X → Y` e `YW → Z`, então `XW → Z`.

**Dependência Funcional Trivial** - todo o conjunto de atributos determina todos os seus subconjuntos. Se `X` determina `Y` (`Y` depende de `X`) então também `Y` determina `X` e `X` depende de `Y`. Se o atributo dependente não pertence ao determinadte, a dependência é não trivial.

Diz-se que uma dependência funcional `f` é **implicada** por um dado conjunto `F` de dependências funcionais se `f` é válida em cada instância da relação que satisfaz as dependências de `F`, ou seja, `f` é válida sempre que todas as dependências funcionais de `F` se verificam. O conjunto das dependências funcionais implicadas por um dado conjunto `F` de dependências funcionais chama-se **fecho de F**, `F+`. Este conjunto de dependências funcionais aplicadas é obtido pela aplicação repetitiva dos axiomas de Armstrong.

Os axiomas de Armstrong são **sólidos**, pois só geram dependências funcionais válidas (pertencentes a `F+`) quando aplicados a um conjunto `F` de dependências funcionais. São também **completos**, pois a aplicação repetida das regras gera todas as dependências funcionais de `F+`.

O **fecho de um conjunto de atributos `X+`**, tendo em conta o conjunto `F` de dependências funcionais, é o conjunto de atributos `A` tais que `X → A` pode ser inferido aplicando os axiomas de Armstrong.

Sejam `S1` e `S2` dois conjuntos de dependências funcionais. Se qualquer dependência funcional implicada por `S1` também é implicada por `S2` (`S1+` é um subconjunto de `S2+`) diz-se que `S2` é uma **cobertura** de `S1`. Se `S2` é uma cobertura de `S1` e `S1` é uma cobertura de `S2` (`S1+ = S2+`), diz-se que `S1` e `S2` são **equivalentes**.

Um conjunto `S` de dependências funcionais diz-se **irredutível** se e só se: o lado dependente de qualquer dependência funcional em `S` tem apenas um atributo; o lado determinante não pode ser alterado sem alterar `S+`; nenhuma das dependências funcionais de `S` pode ser removida de `S` sem alterar o fecho de `S`.

O conjunto `{A_1, A_2, ..., A_n}+` é o conjunto de todos os atributos de uma relação se e só se `A_1, A_2, ..., A_n` for uma superchave da relação.

**Decomposição Sem Perdas** - seja a relação `R` com `X`, `Y`, `Z` atributos. Se `X → Y` ou `X → Z`, então `R(X, Y, Z) = π X,Y (R) ⨝ π X, Z (R)`

**Normalização** - estudo das relações (dependências funcionais) entre atributos de modo a identificar o agrupamento ótimo para estes atributos para identificar um conjunto de relações adequado para satisfazer os requisitos da base de dados. Este grupo deve: possuir o mínimo de atributos possível; possuir na mesma relação atributos com uma relação lógica próxima (dependência funcional); possuir mínima redundância, com cada atributo a ser representado uma única vez.

Agrupar atributos em relações para minimizar redundância de dados permite atualizações com um número mínimo de operações e redução de inconsistência de dados e redução do espaço de armazenamento necessário e utilizado e de custos. Relações com dados redundantes podem vir a ter **anomalias de atualização** (inserção, eliminação, modificação). Duas propriedades importantes relacionadas com decomposição de uma relação maior noutras mais pequenas: _junção sem perdas_ (qualquer instância da relação original pode ser identificada pelas instâncias correspondentes nas relações menores) e _preservação de dependência_ (uma restrição na relação original pode ser mantida ao reforçar restrições em cada relação menor).

**Dependência Funcional** - `B` é funcionalmente dependente de `A` (`A ® B`) se cada valor de `A` é associado a apenas um valor de `B`. A dependência é especificada como uma **restrição** entre os atributos. Uma dependência funcional é propriedade de um esquema relacional, não de uma instância particular do esquema.

**Determinante** - atributo ou grupo de atributos no lado esquerdo da seta de uma dependência funcional.

Uma **dependência funcional completa** implica que `B` é total e funcionalmente dependente de `A` se `B` é funcionalmente dependente de `A`, mas não dos seus subconjuntos (a eliminação de qualquer atributo de `A` implica a perda da dependência). Uma **dependência parcial** existe quando há atributos de `A` que podem ser removidos sem quebrar a relação. Uma dependência funcional é permanente; tem uma relação de 1:1 entre os atributos determinantes e determinados; tem o determinante com o mínimo número de atributos necessário para manter a dependência (funcional total).

**Dependência Transitiva** - se `A ® B` e `B ® C`, então `C` é transitivamente dependente de `A` por `B`.

Identificar o conjunto de dependências funcionais especifica o conjunto de restrições de integridade que devem existir numa relação.

### Semana 8

A normalização de uma relação é obtida pela sua decomposição em duas ou mais relações. Uma relação numa forma normal mais avançada tem menos dados redundantes; se uma relação está numa forma normal mais avançada, também está nas formas normais anteriores:
* **Primeira Forma Normal (1FN)** - uma relação `R(A_1, A_2, ..., A_n)` é designada por _relação universal_ se contiver todos os atributos relevantes da organização, cada um com um nome distinto. Uma relação está na primeira forma normal se: cada atributo contém apenas valores atómicos; não há conjuntos de atributos repetidos descrevendo a mesma característica;
* **Segunda Forma Normal (2FN)** - seja `R(X, Y, Z)` com `X`, `Y`, `Z` conjuntos de atributos, a dependência funcional `X → Y` é _elementar_ se `∀ X' ⊂ X : X' ↛ Y`. Se `X → Y` e `X' → Y` (com `X' ⊂ X`), diz-se que `X → Y` é uma _dependência funcional parcial_. Seja `R(A_1, A_2, ..., A_n)`, `R` está na segunda forma normal se `∀ A_i ∉ chaves`, `∀ x chave`, se verifica que `X → A_i` é elementar, ou seja, se está na primeira forma normal e os atributos que não são chave dependem totalmente da chave. Um atributo pertencente a uma chave diz-se um _atributo primo_; casos especiais se todos os atributos de uma relação são primos; se a chave da relação consiste num único atributo. Para verificar se uma relação está na segunda forma normal, identifica-se a chave da tabela: se a chave for apenas um atributo ou for constituída por todos os atributos da relação, pode concluir-se que está na segunda forma normal; se a chave for composta, verifica-se se há atributos que não são chave e dependem apenas de parte da chave, se não houver, então está na segunda forma normal;
* **Terceira Forma Normal (3FN)** - seja `R(X, Y, Z)`, `X → Z` é _direta_ se e só se `∄ Y ∈ R: Y ↛ X, X → Y, Y → Z` (não trivial). Seja `R(A_1, A_2, ..., A_n)`, `R` está na terceira forma normal se `∀ A_i ∉ chaves`, `∀ x chave`, se verifica que `X → A_i` é direta, ou seja, se está na segunda forma normal e nenhum dos atributos não chave depende de outro também não chave;
* **Forma Normal de Boyce-Codd** - seja `R(A_1, A_2, ..., A_n)`, `R` está na forma normal de Boyce-Codd se, para qualquer dependência funcional `X → Y` (não trivial), `X` e `Y` conjuntos de atributos de `R`, `X` é chave candidaaa de `R`, ou seja, se todo o determinante da relação for uma chave candidata. A forma normal de Boyce-Codd só é diferente da terceira forma normal se a relação tem mais do que uma chave. Se uma relação está na forma normal de Boyce-Codd, está na terceira forma normal.

As dependências funcionais representam restrições de integridade e, portanto, devem ser mantidas nas relações resultantes da decomposição. Seja `R` um esquema de relação que é decomposto em dois esquemas de relação com conjuntos de atributos `X` e `Y` e seja `F` um conjunto de dependências funcionais em `R`. A **projeção de `F` sobre `X` é o conjunto de dependências funcionais no fecho `F+` que contém apenas atributos em `X - Fx`. Uma dependência funcional `U → V` em `F+` só pertence a `Fx` se todos os atributos em `U` e `V` pertencem a `X`. A decomposição da relação `R` com dependências funcionais `F` em esquemas de relação com conjuntos `X` e `Y` preserva as dependências se `(Fx ∪ Fy)+ = F+`, ou seja, se se tomarem as dependências em `Fx` e `Fy` e se calcular o fecho da sua união se obtêm todas as dependências do fecho de `F`. Uma aplicação direta da definição dá um algoritmo direto para testar quando é que uma decomposição preserva as dependências funcionais.

---

## Aulas Práticas

### Folha 1

```SQL
1. SELECT * FROM Empregado
2. SELECT * FROM Empregado WHERE Categoria = 'Artista'
3. SELECT Nome, Categoria FROM Empregado
4. a) SELECT Nome FROM Empregado WHERE Salario >= 150000 AND DepNum = 1
   b) SELECT Nome FROM Empregado WHERE Salario BETWEEN 250000 AND 300000
5. SELECT * FROM Empregado WHERE Categoria LIKE 'A%'
6. SELECT * FROM Empregado WHERE DepNum LIKE '1'
7. SELECT DISTINCT Nome, Categoria FROM Empregado
8. SELECT DepNum FROM Empregado WHERE Nome = ALL (SELECT Nome FROM Empregado WHERE DepNum = 2)
9. SELECT * FROM Empregado, Departamento
10. SELECT Empregado.*, Departamento.Nome, Departamento.Local FROM Empregado, Departamento WHERE Empregado.DepNum = Departamento.DepNum
11. SELECT Empregado.*, Departamento.Local, Departamento.Nome FROM Empregado INNER JOIN Departamento ON Empregado.DepNum = Departamento.DepNum
12. INSERT INTO Departamento (DepNum, Nome, Local) VALUES (5, 'Vendas', 'Covilha')
    SELECT Departamento.*, Empregado.EmpNum, Empregado.Nome, Empregado.Categoria, Empregado.Salario FROM Departamento LEFT JOIN Empregado ON Departamento.DepNum = Empregado.DepNum
13. SELECT EmpNum FROM Atribuicao WHERE Funcao = 'Coordenador' OR Funcao = 'Colaborador'
14. SELECT EmpNum FROM Atribuicao WHERE Funcao = 'Colaborador' INTERSECT SELECT EmpNum FROM Atribuicao WHERE Funcao = 'Coordenador'
15. SELECT EmpNum FROM Atribuicao WHERE Funcao = 'Coordenador' EXCEPT SELECT EmpNum FROM Atribuicao WHERE Funcao != 'Coordenador'
16.
17. SELECT Designacao FROM Projecto WHERE ProjNum IN (SELECT ProjNum FROM Atribuicao WHERE EmpNum IN (SELECT EmpNum FROM Empregado WHERE DepNum IN (SELECT DepNum FROM Departamento WHERE Departamento.Local IN (SELECT Departamento.Local FROM Departamento GROUP BY Departamento.Local HAVING COUNT (Departamento.Local) = 1))))
18. SELECT Nome FROM Empregado INNER JOIN Atribuicao ON Empregado.EmpNum = Atribuicao.EmpNum GROUP BY Empregado.Nome HAVING COUNT(*) >= 2
19. SELECT COUNT(*) AS NumeroEmpregados FROM Empregado
20. SELECT COUNT(*) AS EmpregadosDepartamento1 FROM Empregado WHERE DepNum = 1
21. SELECT COUNT(*) AS EmpregadosCovilha FROM Empregado JOIN Departamento ON Empregado.DepNum = Departamento.DepNum WEHRE Departamento.Local LIKE 'Covilha'
22. SELECT Departamento.Nome FROM Departamento WHERE NOT EXISTS (SELECT * FROM Empregado WHERE Empregado.DepNum = Departamento.DepNum)
23. SELECT SUM(Salario) AS SalariosDepartamento1 FROM Empregado WHERE Empregado.DepNum = 1
24. SELECT SUM(Salario) FROM Empregado WHERE EmpNum IN (SELECT EmpNum FROM Atribuicao WHERE ProjNum = 1)
25. SELECT COUNT(DISTINCT Categoria) FROM Empregado
26. SELECT MAX(Salario) FROM Empregado
27. SELECT Nome FROM Empregado WHERE Salario = (SELECT MIN(Salario) FROM Empregado)
28. SELECT AVG(Salario) AS SalarioMedio FROM Empregado WHERE Empregado.DepNum = 1
29. SELECT Designacao FROM Projecto WHERE Fundos = (SELECT MAX(Fundos) FROM Projecto)
30. SELECT Nome FROM Empregado WHERE EmpNum IN (SELECT EmpNum FROM Atribuicao WHERE ProjNum IN (SELECT ProjNum FROM Projecto WHERE Fundos = (SELECT MAX(Fundos) FROM Projecto)))
31. SELECT Nome, DepNum, Salario FROM Empregado WHERE Salario > (SELECT AVG(Salario) FROM Empregado)
32. SELECT DepNum, COUNT(*) AS NumeroEmpregados FROM Empregado GROUP BY DepNum
33. SELECT DepNum, COUNT(*) AS Programadores FROM Empregado WHERE Categoria = 'Programador' GROUP BY DepNum
34. SELECT Departamento.Nome, COUNT(Empregado.EmpNum) FROM Empregado INNER JOIN Departamento ON Empregado.DepNum = Departamento.DepNum GROUP BY Departamento.Nome
35. SELECT Departamento.Nome, AVG(Salario) AS SalarioMedio, MIN(Salario) AS SalarioMinimo, MAX(Salario) AS SalarioMaximo FROM Departamento INNER JOIN Empregado ON Departamento.DepNum = Empregado.DepNum GROUP BY Departamento.Nome
36. SELECT Departamento.Nome, AVG(Salario) AS SalarioMedio, MIN(Salario) AS SalarioMinimo, MAX(Salario) AS SalarioMaximo FROM Departamento INNER JOIN Empregado ON Departamento.DepNum = Empregado.DepNum GROUP BY Departamento.Nome ORDER BY AVG(Salario) DESC
37. SELECT Departamento.Nome, COUNT(Empregado.EmpNum) AS NumeroEmpregados FROM Empregado INNER JOIN Departamento ON Empregado.DepNum = Departamento.DepNum GROUP BY Departamento.Nome HAVING COUNT(Empregado.EmpNum) >= 2
38. SELECT Departamento.Nome, COUNT(Empregado.EmpNum) AS NumeroEmpregados FROM Empregado INNER JOIN Departamento ON Empregado.DepNum = Departamento.DepNum GROUP BY Departamento.Nome HAVING COUNT(Empregado.EmpNum) >= 2 ORDER BY COUNT(Empregado.EmpNum) DESC
39. SELECT Nome FROM Departamento WHERE DepNum IN (SELECT DepNum FROM Empregado WHERE Salario > (SELECT AVG(Salario) FROM Empregado)) GROUP BY Departamento.Nome
40. SELECT AVG(Salario) AS SalarioMedio FROM Empregado WHERE DepNum IN (SELECT DepNum FROM Empregado WHERE Categoria = 'Programador') GROUP BY DepNum
41. SELECT AVG(Salario) AS SalarioMedio FROM Empregado WHERE DepNum IN (SELECT DepNum FROM Empregado WHERE Categoria = 'Programador') GROUP BY DepNum
42. SELECT Nome FROM Departamento WHERE DepNum IN (SELECT DepNum FROM Empregado WHERE Salario > (SELECT AVG(Salario) FROM Empregado WHERE DepNum IN (SELECT DepNum FROM Empregado WHERE Categoria = 'Programador'))) GROUP BY Nome
43. (versão 1, só nome)
    SELECT NomeEmpregado.Nome FROM (SELECT Nome, COUNT(*) AS NumeroProjectos FROM Empregado, Atribuicao WHERE Empregado.EmpNum = Atribuicao.EmpNum GROUP BY Empregado.EmpNum, Nome) AS NomeEmpregado WHERE NomeEmpregado.Nome.NumeroProjectos = (SELECT TOP 1 COUNT(*) AS NumeroProjectos FROM Empregado, Atribuicao WHERE Empregado.EmpNum = Atribuicao.EmpNum GROUP BY Empregado.EmpNum, Nome ORDER BY COUNT(*) DESC)
    (versão 2, nome e número de projeto)
    SELECT * FROM (SELECT Empregado.Nome, COUNT(*) AS NumeroProjectos FROM Empregado, Atribuicao WHERE Empregado.EmpNum = Atribuicao.EmpNum GROUP BY Empregado.Nome) AS NomeEmpregado WHERE NomeEmpregado.NumeroProjectos = (SELECT MAX(MaximoProjectos.NumeroProjectos FROM (SELECT COUNT(*) AS NumeroProjectos FROM Atribuicao GROUP BY EmpNum) AS MaximoProjectos))
44. SELECT DepNum, COUNT(DISTINCT Categoria) FROM Empregado GROUP BY DepNum ORDER BY COUNT(DISTINCT Categoria) DESC
```