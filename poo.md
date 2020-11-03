## Revisões / Bases

**Identificadores JAVA**

* Não podem começar por um dígito.
* Combinações de letras, dígitos e carateres `_` e `$`.
* Convenções: _classes_ começam com maiúscula; _subprogramas_ e _variáveis_ começam com minúscula; _constantes_ são escritas em maiúsculas.

**Tipos Primitivos:** boolean, char, byte, short, int, long, float, double.

**Declaração de variáveis**

`tipo variável1 [= valor1][, variável2 [= valor2]...];`

A declaração de constantes é semelhante à de variáveis, acrescida com a obrigatoriedade do atributo `final` e do valor da mesma: `final double PI = 3.14159273269`.

**Conversão Entre Tipos**

Os operadores aritméticos estão definidos para funcionar com operandos do mesmo tipo, logo, em expressões que contenham valores de vários tipos, o computador terá de fazer conversões de tipo automaticamente de modo a não haver perdas de informação. Nem todas as transformações são possíveis: é possível converter um valor para um tipo que ocupe mais espaço, mas não o inverso.

`byte > short > int > long > float > double`

A conversão de tipos com perda de informação é permitida usando o operador de coerção `cast` entre parêntesis antes da expressão a converter.

**Estruturas de Controlo Condicionais**

_Seleção simples:_ `if (condição) Instruções_Se_Condição_Verdadeira`

_Seleção em alternativa:_ `if (condição) ISCV else ISCF`

_Seleção múltipla:_ `switch (expressão) {case valor1: instruções1; [break;] ... case valorN: instruçõesN; [break;] default: InstruçõesCasoOmisso; [break]}`

O valor da expressão deve ser inteiro ou caratere, e a instrução `break` é necessária para que os ramos de instruções não sejam executados sequencialmente. Uma instrução `switch` pode ser substituída por `if-else`, mas não o contrário.

**Estruturas de Controlo Repetitivas**

_Ciclo for:_ `for (inicialização; condição_de_continuação; iteração) instruções;`

A `condição_de_continuação` é uma expressão booleana avaliada antes de cada iteração que determina a saída do ciclo assim que o seu valor seja `false`. O bloco `iteração` é executado após as `instruções` e serve para atualizar o valor da variável de controlo.

_Ciclo while:_ `while (condição_de_continuação) instruções;`

Enquanto a `condição_de_continuação` for verdadeira, as `instruções` são executadas.

_Ciclo do...while:_ `do {instruções;} while (condição_de_continuação);`

Usado quando as `instruções` devem ser executadas pelo menos uma vez. No final, a `condição_de_continuação` é testada e a iteração termina se o seu valor for `false`. 

<br/><br/>

## Aula 01 - Conceito de Objeto

**Objetos:** representação de uma entidade sob a forma de um identificador único, um conjunto de atributos privados (_estado_ do objeto) e um conjunto de operações (_comportamento_ do objeto). Destas operações, algumas são invocáveis do exterior (_operações públicas_ - _interface_ do objeto [Application Programmer's Interface, API]), outras são apenas internas ao objeto (_operações privadas_). Aos identificadores que guardam os valores dá-se o nome de _variáveis de instância_. Às operações que representam o comportamento do objeto dá-se o nome de _métodos de instância_.

**Mensagens:** os objetos interatuam entre si através de um mecanismo de envio de mensagens. O _recetor_ é o identificador do objeto que recebe a mensagem, a _mensagem_ é o identificador do método:

* `recetor.mensagem();` - envio de mensagem sem argumentos a um objeto, sem retorno de resultado pelo método correspondente.
* `recetor.mensagem(arg1, arg2, ..., argn);` - envio de uma mensagem com argumentos, sem retorno de resultado.
* `resultado = recetor.mensagem();` - envio de uma mensagem sem argumentos, com retorno de resultado.
* `resultado = recetor.mensagem();` - envio de uma mensagem com argumentos e com retorno de resultado.

Os argumentos e o resultado de uma mensagem têm de ser compatíveis com o tipo dos parâmetros e do valor devolvido pelo método correspondente.

**Instâncias vs Classes**

Uma __classe__ é um objeto que contém a descrição da estrutura e comportamento de objetos do mesmo tipo e que cria objetos particulas que possuem igual estrutura e comportamento. Por __métodos de instanciação__, os objetos são _inicializados_, passando a existir e a poder receber mensagens de outros objetos.

Cada objeto tem as suas próprias variáveis de estado enquanto o código que implementa os métodos permanece armazenado na classe. Os objetos têm um comportamento comum, mas o seu estado é variável.

Quando um objeto é instanciado, a inicialização do seu estado é feita por invocação automática de um método de inicialização - __construtor da classe__.

<br/><br/>

## Aula 02 - Tecnologia Java e Tipos Referenciados

A tecnologia Java baseia-se na ideia de que qualquer programa deve poder ser executado sem ser alterado ou recompilado; o código-fonte é _compilado_ para uma representação intermédia, independente do sistema de execução e da arquitetura da máquina (_byte-code_), que depois é interpretado sobre o ambiente de cada máquina específica pela _Java Virtual Machine_ (JVM). A JVM recebe _byte-code_ e transforma-o em instruções executáveis na máquina onde o ambiente Java é instalado.

__Aplicações Java__ são programas que, após serem compilados, apenas requerem uma JVM para serem interpretados e executados.

__*Applets*__ são porções de código Java não executável por si próprio, requerendo a existência de um _browser_ que incorpore e execute a JVM.

Em Java os programas são constituídos por diversas __classes__, tipos de dados agrupados em pacotes (_packages_), que possuem __atributos__ (variáveis) e __métodos__ (funções). Um __construtor__ é uma operação especial da classe, com o mesmo nome da classe, identificado pela sua lista de parâmetros, para criar objetos, mas sem declarar o tipo do resultado.

__Tipos referenciados__ são entidades às quais se acede através de uma variável que contém o seu endereço; ou seja, o que é atribuído e manipulado são _referências_ (endereços).

__Arrays__ são entidades referenciadas, mas não são objetos. São criados dinamicamente em tempo de execução e o seu espaço é automaticamente reaproveitado quando deixam de estar referenciados.

<br/><br/>

## Aula 03 - Classes e Instanciação de Objetos

<br/><br/>

## Aula 04 - Variáveis de Classe e Composição de Classes

<br/><br/>

## Aula 05 - Comparação de _Strings_

* Valores constantes do tipo _String_ têm a mesma referência.
* _Strings_ construídas em tempo de compilação são tratadas como valores constantes do tipo _String_.
* _Strings_ construídas em tempo de execução - só são criadas quando se executa o programa - têm referências distintas.

Logo, o método recomendado para comparar _strings_ é `s1.equals(s2)`, que compara o conteúdo e não apenas o endereço (como no `==`).

**Listas Dinâmicas**

A classe `ArrayList` no pacote `java.util` distingue-se dos _arrays_ porque pode (de)crescer de tamanho e pode armazenar objetos de diferentes tipos. Implemente uma abstração de dados que representam uma estrutura linear indexada a partir do índice 0 sem limite de dimensão. Alguns métodos da classe:

(_Object_ é uma classe genérica, até sabermos melhor o que é)

* `ArrayList()` -> construtor vazio, dimensão inicial zero.
* `boolean add(Object element)` -> adiciona o elemento especificado ao final da lista.
* `void add(int index, Object element)` -> insere o elemento especificado na posição do índice.
* `Object remove (int index)` -> remove o elemento da posição index
* `boolean remove (Object element)` -> remove a primeira ocorrência do objeto dado como parâmetro.
* `Object set (int index, Object element)` -> substitui o elemento da posição index pelo elemento especificado.
* `Object get (int position)` -> devolve o elemento da posição index.
* `void clear()` -> remove todos os elementos da lista.
* `Object clone()` -> devolve uma cópia da lista.
* `boolean contains(Object element)` -> devolve _true_ se a lista contiver o elemento especificado.
* `boolean equals (Object element)` -> permite comparar duas listas.
* `int indexOf (Object element)` -> procura o índice da primeira ocorrência do elemento.
* `boolean isEmpty()` -> verifica se a lista está vazia.
* `int size()` -> devolve a dimensão atual da lista.
* `String toString()`.

A verificação de tipos pode ser feita durante a compilação, usando _tipos genéricos_ (tipo referenciado que usa na sua definição um ou mais tipos de dados como parâmetros). Seja o tipo `ArrayList<E>` em que E pode ser qualquer classe ou interface, a instanciação de um tipo genérico para um valor concreto de E dá origem a um _tipo parametrizado_.

<br/><br/>

## Aula 06 - 