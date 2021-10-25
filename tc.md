# Teoria da Computação

##### Atualizado em 25-10-2021
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
     = {w ∈ T*: w = a^n b^n, n >= 1} U {λ}
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