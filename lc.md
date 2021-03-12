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

---

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
Diz-se que `v` satisfaz `P` se `v ⊩ P`; se esta valoração existir, a fórmula `P ∈ Fp` é satisfazível. Dada uma fórmula `P ∈ Fp` e uma valoração `v`, tem-se: `v ⊩ P` se `v(P) = V` e `v ⊮ P` se `v(P) = F`.

**Àlgebra de Boole:** considere-se o conjunto de valores de verdade `{V, F}` e as operações `∧, ⋁, ¬`:
* `∧ : {V, F} × {V, F} → {V, F}`:
  * `V ∧ p = p` (V ́e o elemento neutro de `∧`);
  * `F ∧ p = F` (F ́e o elemento absorvente de `∧`);
* `⋁ : {V,F } × {V, F} → {V, F}`:
  * `V ⋁ p = V` (V ́e o elemento absorvente de `⋁`);
  * `F ⋁ p = p` (F ́e o elemento neutro de `⋁`);
* `¬ : {V, F} → {V, F}`:
  * `¬V = F`;
  * `¬F = V`.
**Propriedades da Álgebra de Boole** (assumindo `p, q ∈ {V, F}`; provas nos diapositivos 25-26)
* `¬(¬p) = p`;
* `p ⋀ p = p` e `p ⋁ p = p`;
* `p ⋁ ¬p = V`;
* `p ⋀ ¬p = F`;
* `¬(p ⋁ q) = (¬p) ⋀ (¬q)`;
* `¬(p ⋀ q) = (¬p) ⋁ (¬q)`.

**Extensão da Valoração para Fp:** função `v: Fp -> {V, F}`. definida indutivamente da seguinte forma, `P, Q ∈ Fp`:
* `v(⊥) = F`;
* `∀ p ∈ Pp`, se `P = p` então `v(P) = p`;
* `v(P ⋀ Q) = v(P) ⋀ v(Q)`;
* `v(P ⋁ Q) = v(P) ⋁ v(Q)`;
* `v(P → Q) = (¬v(P)) ⋁ v(Q)`.

---

## Aula Teórica 3

**Proposição** (satisfazibilidade): `v ⊩ P` se `v ⊮ ¬P` e `v ⊮ P` se `v ⊩ ¬P`.

Dado `S ⊆ Fp`, se `v ⊩ Q` para todo o `Q ∈ S`, então `v ⊩ S`. `S ⊆ Fp` diz-se *possível* se existe uma valoração v que satisfaz todas as fórmulas de S, caso contrário, diz-se *contraditório*. Uma fórmula `Q ∈ Fp` é:
* **Possível**, se existe alguma `v(Q) = V`;
* **Válida**/**Tautologia** (`⊨ Q`), se existe sempre `v(Q) = V` (uma tautologia é sempre uma fórmula possível);
* **Contraditória**, se não existe qualquer `v(Q) = V`;
* Se Q não é uma tautologia, então `⊭ Q`.

Uma fórmula que não é válida pode ser possível ou contraditória. Uma fórmula que não é contraditória pode ser possível ou válida. Uma fórmula que não é possível é contraditória.

**Lema:**
* A negação de uma fórmula válida é contraditória;
* A negação de uma fórmula contraditória é válida;
* A negação de uma fórmula possível (não tautológica) é possível.

**Sumário de Tabelas de Verdade**
* `¬p`: valor de verdade oposto ao de `p`;
* `p ⋀ q`: verdadeira se e só se `p` e `q` são verdadeiras, caso contrário, é falsa;
* `p ⋁ q`: falsa se e só se `p` e `q` são falsas, caso contrário, é verdadeira;
* `p → q`: falsa se e só se `p` é verdadeira e `q` é falsa, caso contrário, é verdadeira;
* `p ↔ q`: verdadeira se e só se `p` e `q` têm o mesmo valor de verdade, caso contrário, é falsa.

---

## Exercícios

### Aula Teórica 1

#### Diapositivo 34

**Considerando `Pp = {p, q, r}`, calcule `Sf (p ∨ (q → p))`.**

  Sf (p ⋁ (q → p)) =
= {p ⋁ (q → p)} Sb (p) ∪ Sb (q → p) =
= {p ⋁ (q → p)} ∪ {p} ∪ {q → p} ∪ Sb (q) ∪ Sb (p) =
= {p ⋁ (q → p), p} ∪ {q → p} ∪ {q} ∪ {p} =
= {p ⋁ (q → p), q → p, p, q}

### Aula Teórica 2

#### Diapositivo 14

**Prove que qualquer que seja A € Fp, A contém um número par de parêntesis (0 é um número par).**

Casos Base: A = ⊥ : tem 0 parêntesis (0 é par)
            A = p, p ∈ Pp : tem 0 parêntesis (0 é par)
Passos de Indução: A = ¬Q, Q ∈ Fp
                   H.I.: Q tem um número par de parêntesis, n.
                         Se Q tem n parêntesis, então (¬Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.
                   A = P ⋀ Q, P,Q ∈ Fp
                   H.I.: P ⋀ Q tem um número par de parêntesis, n.
                         Se P ⋀ Q tem n parêntesis, então (P ⋀ Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.
                   A = P ⋁ Q, P,Q ∈ Fp
                   H.I.: P ⋁ Q tem um número par de parêntesis, n.
                         Se P ⋁ Q tem n parêntesis, então (P ⋁ Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.
                   A = P → Q, P,Q ∈ Fp
                   H.I.: P → Q tem um número par de parêntesis, n.
                         Se P → Q tem n parêntesis, então (P → Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.

### Aula Teórica 3

#### Diapositivo 38

**Construa a tabela de verdade das seguintes proposições:**

* `(p ↔ q) ↔ r`
  * `p | q | r | p ↔ q | (p ↔ q) ↔ r`
  * `V | V | V | _ V _ | _ _ V`
  * `V | V | F | _ V _ | _ _ F`
  * `V | F | V | _ F _ | _ _ F`
  * `V | F | F | _ F _ | _ _ V`
  * `F | V | V | _ F _ | _ _ F`
  * `F | V | F | _ F _ | _ _ V`
  * `F | F | V | _ V _ | _ _ V`
  * `F | F | F | _ V _ | _ _ F`

* `(p ↔ q) ⋀ (p ↔ r)`
  * `p | q | r | p ↔ q | p ↔ r | (p ↔ q) ⋀ (p ↔ r)`
  * `V | V | V |  _ V _  | _ V _ | _ _ _ _ V`
  * `V | V | F |  _ V _  | _ F _ | _ _ _ _ F`
  * `V | F | V |  _ F _  | _ V _ | _ _ _ _ F`
  * `V | F | F |  _ F _  | _ F _ | _ _ _ _ F`
  * `F | V | V |  _ F _  | _ F _ | _ _ _ _ F`
  * `F | V | F |  _ F _  | _ V _ | _ _ _ _ F`
  * `F | F | V |  _ V _  | _ F _ | _ _ _ _ F`
  * `F | F | F |  _ V _  | _ V _ | _ _ _ _ V`

#### Diapositivo 44

**Verifique se `(a → b) ↔ (¬b → ¬a)` é válida, contraditória ou possível.**

* A fórmula é válida:
  * `a | b | ¬a | ¬b | (a → b) | (¬b → ¬a) | (a → b) ↔ (¬b → ¬a)`
  * `V | V | _F | _F | _ _ V _ | _ _ V _ _ | _ _ _ _ V`
  * `V | F | _F | _V | _ _ F _ | _ _ F _ _ | _ _ _ _ V`
  * `F | V | _V | _F | _ _ V _ | _ _ V _ _ | _ _ _ _ V`
  * `F | F | _V | _V | _ _ V _ | _ _ V _ _ | _ _ _ _ V`