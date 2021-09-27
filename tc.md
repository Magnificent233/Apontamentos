# Teoria da Computação

##### Atualizado em 27-09-2021
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