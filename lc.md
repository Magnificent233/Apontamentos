# Lógica Computacional

## Aula Teórica 1

**Lógica:** análise e teoria do pensamento válido; estudo e determinação dos modos de pensamento discursivo que permitem evitar contradições e erros. Utilizada em desenho de _hardware_, linguagens de programação, inteligência artificial e, em especial, na verificação de programas. A maioria dos sistemas críticos são controlados por _software_, que é extremamente importante que funcione bem. Testar um programa mostra a existência de erros, não a ausência deles.

Na **lógica proposicional**, valores booleanos estão na base da lógica (verdadeiro, falso). Proposições são afirmações passíveis de serem verdadeiras ou falsas. Proposições atómicas não podem ser simplificadas; proposições compostas são formadas por proposições atómicas ligadas por conetivos (não [¬], e [⋀], ou [⋁], se [→], se e só se [↔]). O objetivo é determinar se a combinação de proposições atómicas resulta numa conclusão válida - **raciocínio** -, focando nas regras que manipulam os conetivos lógicos.

Um sistema formal de raciocínio é composto por:
* Sintaxe:
  * Alfabeto (símbolos):
    * símbolo ⊥ -> falso/absurdo;
    * proposições atómicas -> Pp = p, q, r...
    * conetivos (ordenados da maior precedência para a menor) -> ¬, ⋀, ⋁, →, ↔;
      * Conjunção e disjunção são associatvas à esquerda; implicação é associativa à direita;
    * parêntesis -> (, );
  * Linguagem (fórmulas [Fp]):
    * _BOT_: `⊥ ∈ Fp`;
    * _PROP_: se `p ∈ Pp`, então `p ∈ Fp`;
    * _NEG_: se `p ∈ Fp`, então `¬p ∈ Fp`;
    * _DIS_: se `p, q ∈ Fp`, então `p ⋁ q ∈ Fp`;
    * _CON_: se `p, q ∈ Fp`, então `p ⋀ q ∈ Fp`;
    * _IMP_: se `p, q ∈ Fp`, então `p → q ∈ Fp`.
* Semântica: significado dos símbolos e fórmulas;
* Cálculo: sistema de prova.

Conjuntos definidos indutivamente são construídos a partir de regras que constroem elementos do conjunto à custa de outros elementos, num número finito de vezes. As regras podem definir os elementos básicos do conjunto e obter novos elementos a partir de elementos do conjunto. Para provar que uma fórmula pertence a Fp tem de se mostrar que existe uma regra ou uma sequência de fórmulas resultantes da aplicação das regras que produz a fórmula desejada (exemplo no diapositivo 29).

As **árvores de derivação (ou dedução)** são utilizadas para mostrar uma prova. A **forma construtiva** constrói-se a partir de árvores singulares (folhas) que correspondem às regras que definem os elementos básicos do conjunto, aplicando-se as regras até obter a fórmula desejada; a **forma destrutiva** constrói-se a partir da conclusão (raiz) utilizando as regras até que se atinjam as folhas (exemplo no diapositivo 31).

Na **lógica de predicados** (lógica de primeira ordem), expressões com uma ou mais incógnitas (variáveis) que são verdadeiras ou falsas dependendo do valor das suas variáveis.

## Aula Teórica 2

A **indução matemática** possui:
* *Caso Base* - mostrar que a propriedade é válida para o natural `0`;
* *Passo de Indução* - assumir que a propriedade é válida para um natural `n` e mostrar que é válida para o natural seguinte, `n + 1`.
Na **indução estrutural**, utilizada para provar propriedades sobre os elementos de conjuntos definidos indutivamente:
* *Caso Base* - mostrar que a propriedade `P` é válida para todos os elementos na base da definição do conjunto `S`;
* *Passo de Indução* - assumir que a propriedade `P` é válida para todos os argumentos de cada construtor de `S` e mostrar que é válida para os elementos construídos.
  * **Definição:** para mostrar que uma propriedade é válida para todas as fórmulas `A ∈ Fp`:
    * Provar que uma propriedade é válida para todas as fórmulas atómicas (`⊥` e `p ∈ Pp`);
    * Assumir que a propriedade é válida para `A ∈ Fp` e provar que é válida para `¬A`;
    * Assumir que a propriedade é válida para `A, B ∈ Fp` e provar que é válida para `A op B` (`op ∈ {⋁, ⋀, →}`.

**Semântica da lógica proposicional -** define o significado das fórmulas; a cada proposição atómica é atribuído um valor de verdade (verdadeiro, V; falso, F) de forma a determinar o valor de verdade da fórmula. Uma **valoração** (ou estrutura de interpretação) é uma função `v : Pp → {V, F}` que atribui um valor de verdade a cada proposição atómica. Há uma **relação de satisfação**, sendo `v` uma valoração e `P, Q ∈ Fp`, de `⊩` definida por:
* `v ⊮ ⊥` (`v ⊩ ⊥` não se verifica);
* `v ⊩ p`, `p ∈ Pp` se `v(p) = V`;
* `v ⊩ ¬p` se `v ⊮ p`;
* `v ⊩ P ⋀ Q` se `v ⊩ P` ou `v ⊩ Q`;
* `v ⊩ P ⋁ Q` se `v ⊩ P` ou `v ⊩ Q`;
* `v ⊩ P → Q` se `v ⊮ P` ou `v ⊩ Q`.
Diz-se que `v` satisfaz `P` se `v ⊩ P`; se esta valoração existir, a fórmula `P ∈ Fp` é satisfazível. Dada uma f ormula `P ∈ Fp` e uma valoração `v`, tem-se: `v ⊩ P` se `v(P) = V` e `v ⊮ P` se `v(P) = F`.

**Àlgebra de Boole:** considere-se o conjunto de valores de verdade `{V, F}` e as operações `∧, ∨, ¬`:
* `∧ : {V, F} × {V, F} → {V, F}`:
  * `V ∧ p = p` (V ́e o elemento neutro de `∧`);
  * `F ∧ p = F` (F ́e o elemento absorvente de `∧`);
* `∨ : {V,F } × {V, F} → {V, F}`:
  * `V ∨ p = V` (V ́e o elemento absorvente de `∨`);
  * `F ∨ p = p` (F ́e o elemento neutro de `∨`);
* `¬ : {V, F} → {V, F}`:
  * `¬V = F`;
  * `¬F = V`.
**Propriedades da Álgebra de Boole** (assumindo `p, q ∈ {V, F}`; provas nos diapositivos 25-26)
* `¬(¬p) = p`;
* `p ∧ p = p` e `p ∨ p = p`;
* `p ∨ ¬p = V`;
* `p ∧ ¬p = F`;
* `¬(p ∨ q) = (¬p) ∧ (¬q)`;
* `¬(p ∧ q) = (¬p) ∨ (¬q)`.

## Exercícios

### Aula Teórica 1, diapositivo 34

**Considerando `Pp = {p, q, r}`, calcule `Sf (p ⋁ (q → p))`.**

  Sf (p ⋁ (q → p)) =
= {p ⋁ (q → p)} Sb (p) ∪ Sb (q → p) =
= {p ⋁ (q → p)} ∪ {p} ∪ {q → p} ∪ Sb (q) ∪ Sb (p) =
= {p ⋁ (q → p), p} ∪ {q → p} ∪ {q} ∪ {p} =
= {p ⋁ (q → p), q → p, p, q}