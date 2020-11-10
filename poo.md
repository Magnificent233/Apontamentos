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

Um _argumento_ é um valor passado para uma função quando esta é chamada; um _parâmetro_ é um valor passado para uma função quando esta é definida. Uma _classe_ define a estrutura, propriedades e comportamento de um objeto; uma _instância_ é a referência a um determinado objeto.

`class Contador { <instruções> }`

Por omissão, toda a classe possui um construtor, que atribui o valor `null` a todas as variáveis do objeto que sejam do tipo referenciado e arrays (inicializados de acordo com o seu tipo). Um construtor permite inicializar o estado (valores) das instâncias da classe.

Deve garantir-se que nenhum objeto faz acesso direto às variáveis de instância de outro objeto, de modo a garantir que se estão a definir objetos independentes e reutilizáveis). Um objeto genérico não deve ter instruções de _input_/_output_ no seu código.

_Assinatura de um método:_ constituída pelo identificador do método e pelo número, tipo e ordem dos seus parâmetros. `<tipo do resultado> <identificador> (pares tipo e nome do parâmetro)`.

Um valor do tipo _String_ é uma sequência de zero ou mais carateres entre aspas, com um valor imutável. O operador `+` permite a concatenação de _strings_ e cria implicitamente uma nova instância da classe String.

Métodos que façam __acesso de leitura__ ao valor de uma variável X designam-se por _getters_ e devolvem um resultado do tipo da variável X (`getX`). Métodos que __alterem__ o valor de uma variável X designam-se por _setters_, têm parâmetros de entrada e não devolvem qualquer resultado (`setX`).

A abordagem da comunicação por mensagens pode ser usada uniformemente para interação com outros objetos e invocação de métodos locais. Para que um objeto possa enviar uma mensagem a si próprio, tem de se autorreferenciar: `this` é um identificador especial que contém o endereço do próprio objeto em cujo contexto é utilizado.

Mecanismos de controlo de acesso especificam 'quem' tem acesso a cada entidade (classe, dados e métodos): `public`, `protected`, `private`.

Regras de acesso a classes:
* Uma classe é sempre acessível a todas as outras classes do mesmo _package_ independentemente do modificador de acesso.
* Se nenhum modificador de acesso é usado, a classe apenas pode ser acedida dentro do seu _package_.
* Quando uma classe é declarada como `public`, pode ser acedida por qualquer classe que tenha acesso ao seu _package_.
* Quando uma classe não é pública, é apenas acessível dentro do seu _package_.

Regras de acesso a variáveis e métodos:
* Variáveis e métodos auxiliares são privados; métodos de interface são públicos.
* Um método declarado como `public` é acessível de qualquer ponto de qualquer programa.
* Um método sem modificador de acesso é acessível a qualquer classe do mesmo _package_.
* Métodos ou variáveis declarados como `private` são apenas acessíveis dentro da própria classe.
* Métodos ou variáveis declarados como `protected` são acessíveis na própria classe, de outra classe dentro do mesmo _package_ e nas subclasses da classe.

<br/><br/>

## Aula 04 - Variáveis de Classe e Composição de Classes

**Variáveis de classe** representam a estrutura interna de uma dada classe e armazenam valores que identifiquem todos os objetos da classe. Podem ser usadas mesmo que nunca tenha sido instanciado um objeto da classe. Exemplo: `private static String texto;`.

**Variável de instância** Exemplo: `private int numero;`.

**Métodos de classe** implementam o comportamento da classe. São acessíveis às instâncias da classe, ou seja, um método de instância pode invocar um método de classe, mas não o contrário. Exemplo: `public static int metodoA()`.
 
Tanto as variáveis como os métodos de classe são invocados através de mensagens enviadas à classe e declaradas com o identificador `static`.

**Classes Não Instanciáveis** só têm variáveis e métodos de classe; não especificam a estrutura nem o comportamento de qualquer instância.

Em Java os parâmetros são passados por valor: é criada uma variável local com valor igual a uma cópia do argumento. Se o parâmetro é um tipo referenciado, equivale à passagem por referência - argumento.

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

## Aula 06 - Herança

Conceito em que uma classe pode herdar operações de uma superclasse (classe base) e as suas operações podem ser herdadas por subclasses (classes derivadas). O _mecanismo de herança_ permite definir uma nova classe em termos de uma classe existente, com modificações e/ou extensões de comportamento.

Todos os métodos e atributos da superclasse são herdados pela subclasse, à qual podem ser adicionados novos métodos e atributos no processo de especialização sucessiva. Dada uma hierarquia de classes, a instância de uma subclasse contém: as variáveis de instância da superclasse e as variáveis de instância declaradas na classe derivada. O comportamento dessa instância está definido na sua classe e no conjunto das suas superclasses.

Quando um método é invocado, ou seja, quando é enviada uma mensagem a um objeto, torna-se necessário ligar a mensagem à implementação correspondente. Por exemplo:
* Uma _fila_ pode ser implementada a partir de uma _lista ligada_ desde que se imponham as restrições adequadas à manipulação dos seus elementos.
* Redefinem-se os métodos da _lista ligada_ para refletir a semântica da _fila_.
* Para execução, primeiro pesquisa-se a subclasse e só após a superclasse onde o método é encontrado.

A hierarquia é pesquisada na direção subclasse > superclasse, com início na classe do objeto que recebe a mensagem. É executado o método mais próximo.

**Tipos de ligação** - ligação do nome de um método a uma implementação:
* Em tempo de compilação - _ligação estática_
  * Abordagem mais simples, em que o compilador constrói uma tabela de classes e métodos associados, produzindo um código com as ligações entre os métodos e correspondentes implementações.
  * _Vantagem:_ ligações erradas (chamadas a métodos não existentes) são detetadas em tempo de compilação.
  * _Desvantagem:_ para introduzir alterações na ligação é necessário recompilar todo o código.
* Em tempo de execução - _ligação dinâmica_
  * A correspondência entre o método e a implementação é feita a cada invocação: a hierarquia é pesquisada e, se o método não existir, devolve `Método Desconhecido`.
  * _Vantagem:_ alterações na hierarquia não implicam necessidade de recompilação de todas as classes.
  * _Desvantagens:_ a pesquisa na hierarquia provoca alguma degradação no desempenho do sistema; necessidade de manipular mensagens `Método Desconhecido` em tempo de execução.

Declaração de B como subclasse de A: `public class B extends A`. Um objeto do tipo B também é do tipo A.

Cada classe possui uma só superclasse direta, e apenas esta é identificada na cláusula `extends`. A classe de topo da hierarquia é a classe **Object**; que é superclasse quando não é usada a cláusula `extends`.

A classe **Object** define o comportamento comum a todas as classes através de métodos genéricos que normalmente necessitam de ser redefinidos. Qualquer instância de qualquer classe pode responder às mensagens correspondentes aos métodos da classe.
* `public final Class getClass ()` - devolve a classe do objeto.
* `public String toString ()` - representação textual do objeto.
* `public boolean equals (Object obj)` - igualdade de referências.
* `protected Object clone ()` - clona um objeto.

Dadas uma classe A e uma subclasse B,
* B tem acesso direto a todas as variáveis e métodos de A que não sejam declaradas como `private`.
* B pode definir novas variáveis e métodos e redefinir variáveis e métodos herdados.
* Uma instância de B pode responder a mensagens que correspondam a todos os métodos públicos de B e A.
* Os atributos de uma instância de B são atributos definidos nas classes A e B.

**Princípio da substitutividade:** declarada uma variável como sendo de uma dada classe, é permitido atribuir-lhe um valor de sua classe ou de qualquer sua subclasse.

**Método `equals`** - compara a referência de um objeto que recebe como argumento com a referência do objeto recetor. Devolve `true` se as referências forem iguais, `false` caso contrário.

**Método `clone`** - cria e devolve a cópia do objeto recetor, tal que o objeto criado e o que recebe a mensagem:
* São diferentes: `y = x.clone (); // y != x;`.
* São instâncias da mesma classe: `x.clone().getClass() == x.getClass();`.
* Têm o mesmo valor nas variáveis de instância: `x.clone().equals(x) == true`.

<br/><br/>