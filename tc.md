# Teoria da Computação

##### Atualizado em 02-12-2021
###### A partir de: sebenta

## Aulas Teóricas

### Aula 01

A **computação** é a procura de soluções para um problema a partir de entradas (_inputs_) para se obter resultados (_outputs_) através de um algoritmo. As **ciências da computação** estudam algoritmos, suas aplicações e implementação e estruturas matemáticas basais. A **teoria da computação** debruça-se sobre:
* _Linguagens formais e autómatos_:
    * Linguagens formais são definidas por um conjunto de formalismos matemáticos abstratos e podem ser "faladas" por autómatos (algo que compreende e sabe interpretar uma dada linguagem). Compõem o edifício formal que sustenta o desenvolvimento de processadores de texto, compiladores, _hardware_ e linguagens de programação, tratando das definições e propriedades de diferentes tipos de **modelos de computação** (autómatos finitos, gramáticas livres de contexto, máquinas de Turing);
* _Computabilidade_:
    * Os problemas são definidos como **resolúveis** ou **irresolúveis**; se forem de decisão, então são **decidíveis** ou **indecidíveis**. Se um problema não pode ser solucionado por uma _máquina universal_, então não existe uma solução computável para ele;
    * Um **programa** é um conjunto estruturado de instruções que capacitam uma máquina a aplicar sucessivamente certas operações básicas e testes sobre dados fornecidos ao início, com o objetivo de os transformar numa forma desejável. Uma **máquina** dá significado aos identificadores de operações e testes e a **computação** é um histórico do funcionamento da máquina para o programa, considerando um valor inicial. Uma **função computada** é o resultado obtido após o término da computação (finita);
    * Se dois programas possuem a mesma função computada (resultado) então são equivalentes, o que permite eliminar instruções desnecessárias. Se duas máquinas se simulam mutuamente, são equivalentes (com o mesmo poder computacional). Uma máquina é universal se toda função computável (que pode ser processada) puder ser executada nela;
* _Complexidade_:
    * Um problema diz-se computacionalmente "fácil" se é resolvido de forma eficiente ou computacionalmente "difícil" se não pode ser resolvido de forma eficiente, ou não se conhece se pode ser resolvido de forma eficiente.

**Alfabeto**, `Ʃ`, representa o conjunto não vazio de símbolos ao qual pode pertencer qualquer objeto.

**Cadeia**, `w`, é uma sequência finita de símbolos do alfabeto, podendo ser vazia. Podem ser concatenadas, `w, v`, ou reversas `w^R`. O **comprimento** de uma cadeia, `|w|`, é o número de símbolos da cadeia. **Cadeia vazia**, `λ`, não tem quaisquer símbolos. **Palíndromos** são cadeias tais que `w = w^R`. **Subcadeia** de `w` é qualquer cadeia composta por carateres sucessivos de `w` (`w = uv`, em que `u` é prefixo e `v` é prefixo de `w`). **Potências** de `w`, `w^n`, é a cadeia obtida pela autoconcatenação `n` vezes da cadeia `w`.

`Ʃ*` é o conjunto de todas as cadeias que se podem obter pela concatenação de zero ou mais símbolos de `Ʃ`, contendo a cadeia vazia `λ`. `Ʃ+ = Ʃ* - {λ}`. São sempre infinitas, mesmo quando `Ʃ` é finito.

**Linguagem L** é qualquer subconjunto de `Ʃ*` e **Sentença** é qualquer sequência na linguagem L. Uma linguagem é um conjunto, logo, aplicam-se operações sobre conjuntos: **união**, **interseção**, **diferença**, **complemento**, **reversa**, **concatenação**, **potência**, **fecho estrela** (todas as cadeias que se podem obter por concatenação da linguagem com ela própria, incluindo a cadeia vazia) e **fecho positivo** (todas as cadeias que se podem obter por concatenação da linguagem com ela própria incluindo a cadeia vazia se pertencer à linguagem).

---

### Aula 02

**Gramáticas** são ferramentas para estudar matematicamente linguagens que ultrapassam as limitações da notação de conjuntos anterior (diapositivo 14). Começa-se no conceito mais complexo (frase) e reduz-se sucessivamente até se obterem os elementos irredutíveis com que se constrói a linguagem.

```
O Luís compra um livro.
<frase> → <sintagma nominal><sintagma verbal>
        → <determinante><nome><sintagma verbal>
        → <O><nome><sintagma verbal>
        → <O><Luís><sintagma verbal>
        → <O><Luís><verbo><sintagma nominal>
        → <O><Luís><compra><sintagma nominal>
        → <O><Luís><compra><determinante><nome>
        → <O><Luís><compra><um><nome>
        → <O><Luís><compra><um><livro> → logo, derivável

Chove.
<frase> → <sintagma nominal><sintagma verbal>
        → <vazio><sintagma verbal>
        → <verbo><sintagma nominal>
        → <Chove><sintagma nominal>
        → <Chove><vazio>
        → <Chove> → logo, derivável
```

**G = (V, T, S, P)**, em que G é a gramática, V é _variáveis_ (conjunto finito de objetos não vazio), T é _símbolos terminais_ (conjunto finito de objetos não vazio), S ∈ V é _variável de inicialização_, P é conjunto finito de _produções_.

As **regras de produção** são o cerne da gramática, pois é através delas que se forma uma cadeia e uma cadeia se transforma noutra - definem uma linguagem única associada à gramática. Todas as regras são da forma `x → y`, em que x não inclui a cadeia vazia e y pode incluir ou não. Dada `w = uxv` e `x → y`, `z = uyv`, ou seja, `w ⇒ z`. As regras podem ser aplicadas numa ordem qualquer, qualquer número de vezes, produzindo uma cadeia terminal. O conjunto de todas as cadeias terminais que se podem obter pela gramática forma a linguagem gerada pela gramática, **L(G)**.

---

### Aula 03

**Formas sentenciais** da derivação de `w` são as cadeias derivadas `S, w_1, w_2, ..., w_n`, que contêm variáveis e símbolos terminais (podem conter só variáveis).

```
Exemplo - diapositivo 23
G = ({S}, {a, b}, S, P)
P1: S → a S b   ;   P2: S → λ
S =1=> a S b   =2=> a b
               =1=> aa S bb = a^2 S b^2   =2=> a^2 b^2
                                          =1=> a^2 a S b^2 b = a^3 S b^3 (...)
L(G) = {λ, ab, a^2 b^2, ...} = {w ∈ T*: w = a^n b^n, n >= 0} =
     = {w ∈ T*: w = a^n b^n, n >= 1} ∪ {λ}
```

```
Exemplo - diapositivo 25
L(G) = {a^(n + 1) b^n, n >= 0} =  {a, aab, aaabb, aaaabb, ...}
P1: S → a S   ;   P2: S → a S b   ;   P3: S → λ =>
=> P1: S → a A   ;   P2: S → a S b   ;   P3: A → λ

S =2=> a S b =2=> ... =2=> a^n S b^n =1=> a^n a A b^n =3=> a^n a b^n
S =1=> a A =3=> a
           =2=> aa A b =3=> aa b
                       =2=> aaa A bb (...)
 (sendo A uma variável e a, b carateres terminais)
```

Para demonstrar que uma dada linguagem L é gerada por uma certa gramática G, tem de se mostrar que: toda a cadeia `w ∈ L` pode ser derivada a partir de S usando as produções P da gramática G; qualquer cadeia gerada pela gramática G pertence à linguagem L.

**Autómatos** são modelos abstratos de um computador digital cujo estado pode mudar segundo determinadas regras, compostos por:
* **Ficheiro de entrada** (cadeia num objeto);
* Mecanismo para leitura de entradas;
* **Memória temporária** (pode ler e alterar o conteúdo dos registos de memória);
* **Unidade de controlo** (interno a um número finito de estados internos);
* **Ficheiro de saída**.

Chama-se **passo** ou **movida** à transição do autómato de uma configuração para a configuração seguinte. Os autómatos distinguem-se por:
* **Forma de produzir a saída**:
    * _Aceitadores_ - reconhecem ou não a cadeia de entrada;
    * _Transdutores_ - produzem cadeias de carateres à saída;
* **Natureza da memória temporária**:
    * _Autómatos finitos_ - sem memória temporária;
    * _Autómatos de pilha_ - de memória em pilha;
    * _Máquinas de Turing_ - de memória em fita infinita que pode ser lida ou alterada em qualquer ordem;
* **Natureza da função de transição**:
    * _Determinísticos_ - dada uma configuração, existe apenas um comportamento futuro possível;
    * _Não determinísticos_ - dada uma configuração, o próximo passo pode ter várias alternativas.

**Paradigmas da Computação** respondem ao _princípio da inter-redutibilidade_ (qualquer instância de um dos três paradigmas pode ser olhada como uma instância de outros dois paradigmas):
* Computação do valor de funções numéricas;
* Reconhecimento de linguagens (ou classificação de cadeias de símbolos);
* Transdução (transformação) de cadeias de símbolos.

A teoria dos autómatos finitos é útil para: _software_ de projeto e implementação de circuitos digitais (transdutores); análise lexical em compiladores; _software_ para análise de grandes quantidades de texto; _software_ para verificação de protocolos de comunicação e segurança ou qualquer tipo de sistemas com um número finito de estados.

---

### Aula 04

Dada uma cadeia de carateres, é possível saber se pertence a uma dada linguagem através de um autómato chamado **aceitador**: tem um estado 'aceitar' ao qual é levado por qualquer cadeia de uma dada linguagem que se apresente à sua entrada. Um **aceitador determinístico** DFA (_Deterministic Finite Accepter_) é definido por `M = (Q, Σ, δ, q_0, F)`, em que `Q` é o conjunto finito de estados internos, `Σ` é o alfabeto de entrada, `δ = Q x Σ → Q` é a função total (função de transição), `q_0 ∈ Q` é o estado inicial e `F ⊆ Q` é o conjunto de estados finais. 

A **função de transição estendida** `δ* : Q x Σ* → Q` tem como segundo argumento uma cadeia (e não um caratere). O seu valor de saída dá o estado do autómato depois de ler a cadeia toda, numa forma compacta de descrever um conjunto de transições resultantes da leitura de uma cadeia de entrada.

A linguagem aceite por um DFA `M = (Q, Σ, δ, q_0, F)` é o conjunto de todas as cadeias em `Σ` aceites por `M`, isto é, `L(M) = {w ∈ Σ*: δ*(q_0, w) ∈ F}`. As funções de transição `δ` e `δ*` são funções totais. Como a cada passo se define um único movimento, o autómato é **determinístico**.

Uma linguagem diz-se **regular** se só existir um DFA `M` que a aceite: `L = L(M)`. O conjunto das linguagens regulares constitui uma **família**.

---

### Aula 05

Um **aceitador não determinístico** NFA (_Nondeterministic Finite Accepter_) é definido por `M = (Q, Σ, δ, q_0, F)` em que a função de transição `δ` é definida por `δ = Q * (Σ U {λ}) → 2^Q`. Diferenças para o DFA:
* O contradomínio de `δ` é a potência de conjuntos de `Q`, porque o resultado de `δ` pode ser um subconjunto de `Q`;
* `λ` pode ser um argumento de `δ`, ou seja, pode dar-se uma transição sem consumir um símbolo de entrada;
* O conjunto `δ (q_i, a)` pode ser vazio, significando que não há transição.

Os NFA também podem ser representados por grafos, sendo que do mesmo vértice podem partir diversas arestas com a mesma etiqueta, algumas arestas podem ser etiquetadas por `λ` e nem todas as transições de um vértice são definidas.

Uma entrada é aceite se houver para ela um caminho que leva a um estado final. Uma cadeia é aceite se houver alguma sequência de movimentos possíveis que coloquem o autómato num estado final no fim da cadeia.

A **função de transição estendida** `δ* (q_i, w) = Q_j`, sendo `Q_j` o conjunto de todos os estados em que o autómato se pode encontrar, partindo de `q_i` e tendo lido a cadeia `w`.

A linguagem aceite por um NFA `M = (Q, Σ, δ, q_0, F)` é o conjunto de todas as cadeias em `Σ*` aceites por `M`, isto é, `L(M) = {w ∈ Σ*: δ*(q_0, w) ∩ F ≠ Ø}`. Uma cadeia `w` pode levar a vários estados depois de lida; se pelo menos um deles é final, a cadeia é aceite.

O não-determinismo permite: modelizar algoritmos em que se tem de fazer escolhas (_search-and-backtracking_); definir linguagens compostas por conjuntos bastante diferentes; descrever de forma simples e concisa linguagens complicadas; simplificar argumentos formais sem afetar a generalidade da conclusão.

Dois aceitadores `M1` e `M2` são **equivalentes** se `L(M1) = L(M2)`, ou seja, ambos aceitam a mesma linguagem. Se uma linguagem é aceite por um DFA, então existe um NFA que também a aceita - e o contrário também é válido. Se no NFA existem no total `Q` estados, o número máximo de estados que se podem obter no DFA é igual à potência de conjuntos de `Q` (`2^|Q|`), logo, finito.

---

### Aula 06

Nas **máquinas de Mealy**, a saída depende do estado atual e da entrada atual: `y_k = f(s_k, q_k)`. Nas **máquinas de Moore**, a saída depende apenas do estado (e não da entrada). Ambas são definidas pelo sexteto `M = (Q, Σ, Λ, δ, γ, q_0)`, em que `Q` é um conjunto finito de estados internos, `Σ` é o alfabeto de entrada, `Λ` é o alfabeto de saída, `δ: Q x Σ → Q` é a função de transição de estado, `γ: Q x Σ → Λ` é a função de saída e `q_0 ∈ Q` é o estado inicial.

Dada uma máquina de Mealy é possível encontrar uma máquina de Moore que, para as mesmas entradas, dá as mesmas saídas e vice-versa.

**Expressões regulares** são formas de descrever linguagens regulares através de símbolos do alfabeto `Σ`, operadores de união (`∪`, `+`), concatenação (`·`), fecho-estrela (`*`) e parêntesis. Dado um alfabeto `Σ = {Ø, λ, a}`, se `r_1` e `r_2` são expressões regulares, também o serão: `r_1 + r_2` (união), `r_1 · r_2` (concatenação), `r_1*, r_2*` (fecho-estrela), `(r_1), (r_2)` (parêntesis). Uma cadeia é uma expressão regular se e só se puder ser derivada a partir das expressões regulares primitivas e pela aplicação de um número finito de vezes das regras.

**Regras algébricas para expressões regulares**: comutativas, associativas, distributivas, identidades e anuladores, de fecho. Para provar uma regra algébrica qualquer, tem de se provar que qualquer cadeia gerada pela expressão regular da esquerda também é gerada pela expressão regular da direita.

Se `r`, `r_1` e `r_2` são expressões regulares, `L(r)` denota a linguagem associada com `r` e é definida por:
1. `r = Ø` é uma expressão regular (conjunto vazio);
2. `r = λ` é uma expressão regular (conjunto `{λ}`);
3. `∀ a ∈ Σ, r = a` é uma expressão regular (conjunto `{a}`);
4. `L(r_1 + r_2) = L(r_1) ∪ L(r_2)`;
5. `L(r1 · r_2) = L(r_1)L(r_2)`;
6. `L((r_1)) = L(r_1)`;
7. `L(r_1*) = (L(r_1))*`.

As regras 4 a 7 reduzem `L` a expressões mais simples e as regras 1 a 3 são as condições terminais. Para se verificar qual a linguagem que corresponde a uma dada expressão regular, aplicam-se as regras tantas vezes quantas as necessárias. A **precedência dos operadores** é: fecho-estrela, concatenação, união.

Duas expressões regulares são **equivalentes** se denotam a mesma linguagem, que usualmente tem um número ilimitado de expressões regulares equivalentes. Para toda a linguagem regular existe uma expressão regular e vice-versa.

Uma linguagem é regular se for aceite por um DFA ou um NFA. Definem-se NFA para as expressões regulares primitivas; admitindo que se tem uma expressão regular `r` e que o NFA que aceita `L(r)` é representado por `M(r)`, tem-se NFA's `M(r_1)` e `M(r_2)` que aceitam as linguagens `L(r_1)` e `L(r_2)`.

---

### Aula 07

A toda a linguagem regular se pode associar um NFA, logo, um grafo de transições: partindo do estado `q_0`, procuram-se todos os caminhos possíveis até ao estado final e as suas etiquetas, que podem ser geridas por uma expressão regular. Em **grafos de transição generalizados**, as arestas podem ser etiquetadas por expressões regulares; a etiqueta de um caminho desde o estado inicial até um estado final é a concatenação das etiquetas das arestas do caminho; as cadeias expressas por cada expressão regular são um subconjunto da linguagem aceite pelo grafo de transição generalizado e a linguagem total será a união de todos os subconjuntos gerados.

Uma aresta etiquetada com um único caratere `a` interpreta-se como etiquetada pela expressão regular `a`, podendo assim afirmar-se que para toda a linguagem regular existe um grafo de transição generalizado que a aceita, por outro lado, toda a linguagem aceite por um grafo generalizado é uma linguagem regular. Dois grafos são **equivalentes** se aceitam a mesma linguagem.

Seja `L` uma linguagem regular, então existe uma expressão regular `r` tal que `L = L(r)`. Uma gramática diz-se **regular** se é linear à esquerda ou à direita: é **linear à esquerda** se todas as suas produções têm a forma `A → Bx`, `A → x` e **linear à direita** se todas as suas produções têm a forma `A → xB`, `A → x`. Seja `G = (V, T, S, P)` uma gramática linear à direita, então `L(G)` é uma linguagem regular.

Para provar que toda a linguagem regular pode ser gerada por uma gramática linear à direita: constrói-se o DFA para a linguagem, os estados do DFA transformam-se nas variáveis da gramática, os símbolos produtores das transições são os terminais das produções. Se `L` é uma linguagem regular no alfabeto `Σ`, então existe uma gramática linear à direita `G = (V, Σ, S, P)` tal que `L = L(G)`. **Uma linguagem `L` é regular se e só se existir uma gramática regular `G` tal que `L = L(G)`.

---

### Aula 08

Se `L_1` e `L_2` são linguagens regulares, então também o são `L_1 ∪ L_2`, `L_1 ∩ L_2`, `L_1 L_2`, `Compl(L_1)`, `Compl(L_2)`, `L_1*`, `L_2*`, `L_1 - L_2 = L_1 ∩ Compl(L_2)`. A família das linguagens regulares é fechada em relação à reversão, a qualquer homomorfismo e ao quociente à direita por uma linguagem regular.

Autómatos finitos, expressões e gramáticas regulares são **formas padrão** de representar linguagens. Dada uma representação padrão de qualquer linguagem regular `L` em `Σ` e dada uma qualquer cadeia `w ∈ Σ*`, existe um algoritmo para determinar se `w` pertence ou não a `L`. Existe um algoritmo para verificar se uma linguagem dada numa forma padrão é vazia, finita ou infinita. Dadas duas linguagens regulares `L_1` e `L_2` numa forma padrão, existe um algoritmo para determinar se `L_1 = L_2`: `L = (L_1 - L_2) ∪ (L_2 - L_1)`, se `L` for vazia, `L_1` e `L_2` são iguais, se não, são diferentes.

**Autómatos finitos** têm memória limitada; não são capazes de distinguir prefixos de comprimentos arbitrários; num grafo de transição com `n` vértices, qualquer caminho de comprimento igual ou superior a `n` tem de repetir algum vértice (conter um ciclo); num autómato com `n` estados, qualquer cadeia mais longa do que `n` produz estados repetidos.

Seja `L` uma linguagem regular infinita, existe algum inteiro positivo `m` tal que toda a cadeia `w ∈ L` com `|w| >= m` se pode decompor em `x = xyz` com `|xy| <= m` e `|y| >= 1`, tal que `w_i = xy^iz` também pertence a `L` para todo `i ∈ IN`. Este lema serve para provar, por **contradição**, que uma linguagem não é regular: para qualquer valor `m` é possível encontrar (pelo menos) uma cadeia `|w| >= m` pertencente a `L` em que qualquer decomposição `xyz` produz, pela bombagem de `y`, `|xy| <= m` (pelo menos) uma cadeia que não pertence à linguagem.

---

### Aula 09

Uma gramática `G = (V, T, S, P)` diz-se **livre de contexto** (CFG) se todas as suas produções `P` têm a forma `A → x`, em que `A ∈ V` e `x ∈ (V ∪ T)*`, isto é, `x` é uma expressão qualquer composta por variáveis e/ou carateres terminais. Uma linguagem é **livre de contexto** (CFL) se e só se existir uma gramática livre de contexto tal que `L = L(G)`.

A **árvore de derivação** será de `G` se e só se: a raiz é etiquetada por `S`; todas as folhas têm uma etiqueta de `T ∪ {λ}` (símbolo terminal ou `λ`); todos os vértices interiores (não-folhas) têm uma etiqueta de `V`; se um vértice tem uma etiqueta `A ∈ V` e se os seus filhos são etiquetados da esquerda para a direita `a_1, a_2, ..., a_n`, então `P` deve conter a produção da forma `A → a_1 a_2 ... a_n`. Uma folha etiquetada `λ` não tem irmãs, isto é, um vértice com um filho `λ` não pode ter outros filhos.

A **árvore de derivação parcial** verifica as últimas três propriedades de uma árvore de derivação, não precisa necessariamente de verificar a primeira propriedade e todas as folhas têm etiquetas `V ∪ T ∪ {λ}`, isto é, uma variável ou um símbolo terminal ou `λ`.

Lendo as folhas da árvore da esquerda para a direita, omitindo quaisquer `λ` que se encontrem, obtém-se o **fruto** da árvore: cadeia de terminais que se obtém quando se percorre a árvore de cima para baixo, tomando sempre o ramo inexplorado mais à esquerda.

Seja `G = (V, T, S, P)` numa CFG: para toda a cadeia `w ∈ L(G)` existe uma árvore de derivação total de G cujo fruto é `w`; inversamente, o fruto de qualquer árvore de derivação pertence a `L(G)`; se `t_G` é alguma árvore de derivação parcial de `G` cuja raiz é `S`, então o fruto de `t_G` é uma forma sentencial de `G`. As árvores de derivação não explicitam a ordem de aplicação das produções da gramática.

Problema de ***parsing*:** encontrar uma sequência de produções pelas quais se deriva `w ∈ L(G)`. No *parsing* por **pesquisa exaustiva**, na primeira volta, analisar as produções do tipo `S → x` encontrando todos os `x` que se podem obter de `S` num passo e verificar se algum é `w`; na segunda volta, aplicar todas as produções possíveis à variável mais à esquerda em cada `x`, obtendo-se um conjunto de formas sentenciais alcançáveis em dois passos e verificar se algum é `w`; aplicar todas as produções possíveis à variável mais à esquerda em cada forma sentencial, obtendo um novo conjunto de formas sentenciais alcançáveis em três passos e verificar se algum é `w`; e assim sucessivamente. O *parsing* exaustivo é fastidioso, ineficiente e pode nunca terminar se a cadeia não estiver na linguagem, a menos que se introduza um mecanismo de paragem.

A paragem do *parsing* pode ser feita ao eliminar produções do tipo `S → λ` (reduz o comprimento da FS) e `A → B` (mantém o comprimento das FS). Se todas as produções aumentarem o comprimento da FS, pode-se parar quando ela for maior que `w`. Seja `G` uma CFG que não tem qualquer regra de produção da forma `A → λ` ou `A → B`, com `A, B ∈ V`, o *parsing* exaustivo pode ser feito por um algoritmo que, para qualquer `w ∈ Σ*`, ou produz o *parsing* de `w` ou conclui que não é possível qualquer *parsing* para `w`.

Uma CFG `G = (V, T, S, P)` é uma **s-gramática** ou **gramática simples** se todas as suas produções `P` são da forma `A → ax` em que `A ∈ V`, `a ∈ T`, `x ∈ V*` e qualquer par `(A, a)` aparece no máximo uma vez em `P`. Em cada produção aumenta-se em uma só unidade o número de carateres terminais em cada forma sentencial. O *parsing* numa s-gramática pode ser feito em `|w|` voltas, pelo que o seu tempo é linear com o tamanho da cadeia.

Uma gramática livre de contexto é **ambígua** se existir alguma cadeia `w ∈ L(G)` que tem pelo menos duas árvores de derivação possíveis, implicando a existência de duas ou mais derivações de (extrema) esquerda ou de (extrema) direita. Se `L` é uma linguagem livre de contexto para a qual existe uma gramática não ambígua, então `L` diz-se não ambígua; se toda a gramática que gera `L` é ambígua, a linguagem diz-se inerentemente ambígua.

Seja `G = (V, T, S, P)` uma CFG. A variável `A ∈ V` diz-se **útil** se e só se existir pelo menos uma `w ∈ L(G)` tal que `S =*=> xAy =*=> w`, com `x, y` em `(V ∪ T)*`, ou seja, se ocorrer pelo menos numa derivação de uma cadeia. Uma variável pode ser **inútil** se não for alcançável a partir da variável de início ou se não puder gerar uma cadeia terminal.

Qualquer produção de uma CFG da forma `A → λ` é chamada **produção-λ**. Chama-se **anulável** a qualquer variável `A` para a qual é possível a derivação `A =*=> λ`. Qualquer produção de uma CFG da forma `A → B` em que `A, B ∈ V`, qualquer par `(A, B)` para o qual se possa encontrar `A =*=> B` usando apenas produções unidade é um **par unidade**. Seja `L` uma CFL que não contém `λ`, então, existe uma CFG que gera `L` e que não contém produções inúteis, produções-λ e produções-unidade.

Uma CFG está na **forma normalizada de Chomsky** se todas as produções são da forma `A → BC` ou `A → a`, em que `A, B, C ∈ V` e `a ∈ T`. Na forma normal de Chomsky, a parte direita de qualquer produção tem um ou dois símbolos.

Uma CFG está na **forma normalizada de Greibach** se todas as produções têm a forma `A → ax`, em que `a` é um símbolo terminal e `x` é uma cadeia de zero ou mais variáveis.