# Lógica Computacional

## Aula Teórica 1

**Lógica:** análise e teoria do pensamento válido; estudo e determinação dos modos de pensamento discursivo que permitem evitar contradições e erros. Utilizada em desenho de _hardware_, linguagens de programação, inteligência artificial e, em especial, na verificação de programas. A maioria dos sistemas críticos são controlados por _software_, que é extremamente importante que funcione bem. Testar um programa mostra a existência de erros, não a ausência deles.

Na **lógica proposicional**, valores booleanos estão na base da lógica (verdadeiro, falso). Proposições são afirmações passíveis de serem verdadeiras ou falsas. Proposições atómicas não podem ser simplificadas; proposições compostas são formadas por proposições atómicas ligadas por conetivos (não [¬], e [∧], ou [∨], se [→], se e só se [↔]). O objetivo é determinar se a combinação de proposições atómicas resulta numa conclusão válida - **raciocínio** -, focando nas regras que manipulam os conetivos lógicos.

Um sistema formal de raciocínio é composto por:
* Sintaxe:
  * Alfabeto (símbolos):
    * símbolo ⊥ -> falso/absurdo;
    * proposições atómicas -> Pp = p, q, r...
    * conetivos (ordenados da maior precedência para a menor) -> ¬, ∧, ∨, →, ↔;
      * Conjunção e disjunção são associativas à esquerda; implicação é associativa à direita;
    * parêntesis -> (, );
  * Linguagem (fórmulas [Fp]):
    * _BOT_: `⊥ ∈ Fp`;
    * _PROP_: se `p ∈ Pp`, então `p ∈ Fp`;
    * _NEG_: se `p ∈ Fp`, então `¬p ∈ Fp`;
    * _DIS_: se `p, q ∈ Fp`, então `p ∨ q ∈ Fp`;
    * _CON_: se `p, q ∈ Fp`, então `p ∧ q ∈ Fp`;
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
    * Assumir que a propriedade é válida para `A, B ∈ Fp` e provar que é válida para `A op B` (`op ∈ {∨, ∧, →}`.

**Semântica da lógica proposicional -** define o significado das fórmulas; a cada proposição atómica é atribuído um valor de verdade (verdadeiro, V; falso, F) de forma a determinar o valor de verdade da fórmula. Uma **valoração** (ou estrutura de interpretação) é uma função `v : Pp → {V, F}` que atribui um valor de verdade a cada proposição atómica. Há uma **relação de satisfação**, sendo `v` uma valoração e `P, Q ∈ Fp`, de `⊩` definida por:
* `v ⊮ ⊥` (`v ⊩ ⊥` não se verifica);
* `v ⊩ p`, `p ∈ Pp` se `v(p) = V`;
* `v ⊩ ¬p` se `v ⊮ p`;
* `v ⊩ P ∧ Q` se `v ⊩ P` ou `v ⊩ Q`;
* `v ⊩ P ∨ Q` se `v ⊩ P` ou `v ⊩ Q`;
* `v ⊩ P → Q` se `v ⊮ P` ou `v ⊩ Q`.
Diz-se que `v` satisfaz `P` se `v ⊩ P`; se esta valoração existir, a fórmula `P ∈ Fp` é satisfazível. Dada uma fórmula `P ∈ Fp` e uma valoração `v`, tem-se: `v ⊩ P` se `v(P) = V` e `v ⊮ P` se `v(P) = F`.

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

**Extensão da Valoração para Fp:** função `v: Fp -> {V, F}`. definida indutivamente da seguinte forma, `P, Q ∈ Fp`:
* `v(⊥) = F`;
* `∀ p ∈ Pp`, se `P = p` então `v(P) = p`;
* `v(P ∧ Q) = v(P) ∧ v(Q)`;
* `v(P ∨ Q) = v(P) ∨ v(Q)`;
* `v(P → Q) = (¬v(P)) ∨ v(Q)`.

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
* `p ∧ q`: verdadeira se e só se `p` e `q` são verdadeiras, caso contrário, é falsa;
* `p ∨ q`: falsa se e só se `p` e `q` são falsas, caso contrário, é verdadeira;
* `p → q`: falsa se e só se `p` é verdadeira e `q` é falsa, caso contrário, é verdadeira;
* `p ↔ q`: verdadeira se e só se `p` e `q` têm o mesmo valor de verdade, caso contrário, é falsa.

---

## Aula Teórica 4

**Lema (Símbolos Omissos):** sejam `A ∈ Fp` e `v1`, `v2` duas valorações. Se para todo o `a ∈ Sb(a)` se tem que `v1(a) = v2(a)`, então `v1(A) = v2(A)`.

**Consequência Semântica:** sejam `S ⊆ Fp` e `A ∈ Fp`. `A` é uma consequência semântica (ou lógica) de `S` (`S ⊨ A`) se para toda a valoração `v` tal que `v ⊩ s` se tem `v ⊩ A`.

Um conjunto S diz-se contraditório (`S ⊨ ⊥`) quando, para todo `s ∈ S`, não existe qualquer valoração tal que `v ⊩ s`. Se `S ⊆ Fp` é contraditório, então para qualquer `A ∈ Fp` tem-se `S ⊨ A`. A partir de conjuntos contraditórios pode obter-se qualquer conclusão.

* Se `S = ∅`, então `∅ ⊨ A` é equivalente a `⊨ A`.
* Tem-se que `⊨ A` se e só se A é uma tautologia.
* Se `S = {Q}`, `Q ∈ Fp` e `S ⊨ A`, então diz-se que A é uma consequência semântica de Q e escreve-se `Q ⊨ A`.

**Proposição:** sejam `Q, A ∈ Fp`, `{Q} ⊨ A` se e só se `⊨ Q → A`.

**Proposição:** `{s1, ..., sn} ⊨ A`, `n ∈ N`, se e só se `⊨ (s1 ∧ ... ∧ sn) → A`.

**Proposição:** `{s1, ..., sn} ⊨ A` se e só se `s1 ∧ ... ∧ sn ⊨ A`.

**Proposições:** sejam `A, B, Q ∈ Fp` e `S, S' ⊆ Fp`. `{Q, ¬Q} ⊨ ⊥`. `S ⊨ ⊥` e `S' ⊆ S'` então `S' ⊨ ⊥`. `S ⊨ A` se e só se `S, ¬A ⊨ ⊥`. `S ⊨ ¬A` se e só se `S, A ⊨ ⊥`. `{A ∧ B} ⊨ A` e `{A ∧ B } ⊨ B`. `{A} ⊨ A ∨ B` e `{B} ⊨ A ∨ B.`. `∀ A ∈ S, S ⊨ A`. `S ⊨ A` então `S, B ⊨ A`. Se `S ⊨ A` e `S, A ⊨ B` então `S ⊨ B`. `S ⊨ A → B` se e só se `S, A ⊨ B`. `S ⊨ A ∧ B` se e só se `S ⊨ A` e `S ⊨ B`. `S ⊨ A ∨ B` se e só se `S ⊨ A` ou `S ⊨ B`.

A consequência semântica é *reflexiva* (`A ⊨ A`) e *transitiva* (`A ⊨ B` e `B ⊨ C` então `A ⊨ C`, `A, B, C ∈ Fp`), logo, é uma **pré-ordem**.

---

## Aula Teórica 5

**Equivalência Lógica:** sejam `A, B ∈ Fp`. Diz-se que A e B são logicamente (ou semanticamente) equivalentes se e só se `A ⊨ B` e `B ⊨ A`, e escreve-se `A ≡ B`. Se para todas as valorações v se tem que `v(A) = v(B)` então A e B são logicamente equivalentes, e escreve-se `A ≡ B`. A e B são logicamente equivalentes (`A ≡ B`) se e só se `⊨ (A → B) ∧ (B → A)`.

A equivalência `↔` é um operador booleano da lógica proposicional (linguagem objeto, usada em fórmulas). A equivalência lógica `≡` é uma notação para pares de fórmulas em lógica proposicional (metalinguagem). No entanto, `A ≡ B` se e só se `⊨ A ↔ B`. A equivalência lógica é *reflexiva* (`A ≡ A`), *simétrica* (se `A ≡ B` então `B ≡ A`) e *transitiva* (se `A ≡ B` e `B ≡ C`, então `A ≡ C`, `A, B, C ∈ Fp`), logo, é uma **relação de equivalência**.

**Caracterização da Igualdade por Leibniz:** dois termos são o mesmo (eadema) se um pode ser substituído pelo outro sem alterar a validade de qualquer afirmação (_salva veritate_). A **substituição de igual por igual** diz que, se duas fórmulas A e B são logicamente equivalentes (`A ≡ B`), então A pode ser substituído por B (ou B por A) em qualquer fórmula.

Algumas leis da lógica proposicional:
* *Dupla Negação:* `¬¬P ≡ P`
* *Idempotência da ∧:* `P ∧ P ≡ P`
* *Idempotência da ∨:* `P ∨ P ≡ P`
* *Terceiro excluído:* `P ∨ ¬P ≡ T`
* *Contradição:* `P ∧ ¬P ≡ ⊥`
* *De Morgan:* `¬(P ∨ Q) ≡ (¬P) ∧ (¬Q)`
* *De Morgan:* `¬(P ∧ Q) ≡ (¬P) ∨ (¬Q)`
* *Contrapositiva da →:* `P → Q ≡ ¬Q → ¬P`
* *Contrapositiva da ↔:* `P ↔ Q ≡ ¬P ↔ ¬Q`
* *Comutatividade da ∧:* `P ∧ Q ≡ Q ∧ P`
* *Comutatividade da ∨:* `P ∨ Q ≡ Q ∨ P`
* *Associatividade da ∧:* `(P ∧ Q) ∧ R ≡ P ∧ (Q ∧ R) ≡ P ∧ Q ∧ R`
* *Associatividade da ∨:* `(P ∨ Q) ∨ R ≡ P ∨ (Q ∨ R) ≡ P ∨ Q ∨ R`
* *Associatividade da ↔:* `(P ↔ Q) ↔ R ≡ P ↔ (Q ↔ R) ≡ P ↔ Q ↔ R`
* *Distributividade da ∧:* `P ∧ (Q ∨ R) ≡ (P ∧ Q) ∨ (P ∧ R)`
* *Distributividade da ∨:* `P ∨ (Q ∧ R) ≡ (P ∨ Q) ∧ (P ∨ R)`
* *Fórmula normal disjuntiva:* `P → Q = ¬P ∨ Q`
* *Elemento neutro da ∧:* `P ∧ T = P`
* *Elemento absorvente da ∧:* `P ∧ ⊥ = ⊥`
* *Elemento neutro da ∨:* `P ∨ ⊥ = P`
* *Elemento absorvente da ∨:* `P ∨ T = T`

Um **monoide** é um conjunto equipado com uma operação binária associativa e um elemento neutro (`(Fp, ∧, T)`, `(Fp, ∨, ⊥)`).

Um **literal** é uma proposição atómica (literal positivo) ou a sua negação (literal negativo). Uma disjunção de literais (`(n)∨_(i = j) Li`) é uma tautologia se e só se existirem `1 ≤ i`, `j ≤ n`, `Li = T` ou `Li = ¬Lj`.

Uma fórmula A diz-se em **forma normal conjuntiva** (FNC(A)) se é uma conjunção de disjunções de literais: `(l_11 ∨ ... ∨ l_1k1) ∧ ... ∧ (l_n1 ∨ ... ∨ l_nkn)`, onde cada `l_ij` é um literal. Uma fórmula `A ∈ Fp` tal que FNC(A), é:
* uma tautologia, se todas as disjunções são tautologias;
* contraditória, se pelo menos uma das disjunções é contraditória;
* possível, se nenhum dos anteriores se verificar.

Uma fórmula A diz-se em **forma normal disjuntiva** (FND(A)) se é uma disjunção de conjunções de literais: `(l_11 ∧ ... ∧ l_1k1) ∨ ... ∨ (l_n1 ∧ ... ∧ l_nkn)`, onde cada `l_ij` é um literal. Uma fórmula `A ∈ Fp` tal que FND(A), é:
* uma tautologia, se pelo menos uma das conjunções é tautologia;
* contraditória, se todas as conjunções são contraditória;
* possível, se nenhum dos anteriores se verificar.

Considere-se `A1, B1 ∈ Fp` tal que FNC(A1) e FND(B1). Existem `A2, B2 ∈ Fp` tais que `A2 ≡ ¬A1` e `B2 ≡ ¬B1` e FND(A2) e FNC(B2), ou seja, para uma FNC existe sempre uma FND que lhe é logicamente equivalente e vice-versa.

**Lema:** para toda a fórmula `A ∈ Fp` existem fórmulas `A1, A2 ∈ Fp` tais que `A ≡ A1` e FNC(A1) e `A ≡ A2` e FND(A2). Toda a fórmula tem uma forma normal equivalente.

---

## Aula Teórica 6

Uma fórmula `A ∈ Fp`, na qual não existem ocorrências de `→`, diz-se em **forma normal negativa** (FNN(A)) se todas as negações que ocorrem na fórmula se aplicam apenas a proposições atómicas. As FND, FNC e FNN não são únicas.

**Conversão para FNC:**
* Tabelas de verdade - para cada linha da tabela onde o valor é `F`, cria-se uma disjunção que nega as proposições atómicas que têm o valor `V`;
* Algoritmo Ƭ - algoritmo determinístico que verifica a validade de uma fórmula, que usa as seguintes regras (`Ƭ(s) = CNF (NNF (IMPL_FREE (S)))`):
  * `IMPL_FREE` - remove todas as implicações (`P → Q = ¬P ∨ Q`);
  * `NNF` - remove negações duplas (`¬¬`) e negações de fórmulas não atómicas pelas regras de De Morgan, transformando em FNN;
  * `CNF`
    * Se `S` é um literal, `CNF(S) = S`;
    * Se `S = S1 ∧ S2`, então `CNF(S1) ∧ CNF(S2)`;
    * Se `S = S1 ∨ S2`, então `CNF(S1) ∨ CNF(S2)` e define-se `DISTR`, que aplica as leis da distributividade de forma apropriada.
* Algoritmo de Horn (H) - fórmula em FNC em que em cada disjunção existe no máximo um literal positivo, que verifica a satisfazibilidade de uma fórmula:
  * **Lema:** `L ≡ T → L`; `n^∨_i=1 ¬L_i ≡ (n^∧_i=1 L_i) → ⊥`; `n^∨_i=1 ¬L_i ∨ L ≡ (n^∧_i=1 L_i) → L` - transforma uma fórmula de Horn em forma de Horn;
  * **Teorema:** `H(S) = V` se e só se S é possível; `H(S) = F` se e só se S é contraditória;
  * **Lema:** sejam `C0, C1 ⊆ Pp ∪ {⊥, ⊤}` e F uma fórmula em forma de Horn. `A` é **monótona** se `C0 ⊆ C1 → A(F, C0) ⊆ A(F, C1)`. `A` é **crescente** se `C0 ⊆ A(F, C0) ⊆ C0 ∪ n^∪_i=1 L_i`;
    * A negação de uma fórmula válida é contraditória (e vice-versa);
    * Determina-se `T = Ƭ(¬S)`. Se T é forma de Horn, calcula-se Ƭ: se for `F`, então S é válida dado que T é contraditória e `T ≡ ¬S`.

---

## Aula Teórica 7

**Proposição:** considere-se uma fórmula de Horn, Q, que é satisfazível e tal que `A(Q, ⊤) = S` e `⊥ ∉ S`. Tem-se que `v ⊩ Q` quando `v(p) = V` para todo o `p ∈ S` e `v(q) = F` para todo o `q ∉ S`.

Um sistema de prova é:
* **Correto (_Soundness_)** se tudo o que se consegue provar é de facto verdade:
  * **Teorema:** para uma fórmula Q em forma de Horn, tem-se que `H(Q) = V` se e só se Q é possível (**SAT**); `H(Q) = F` se e só se Q é contraditória (**UNSAT**);
* **Completo (_Completeness_)** se tudo o que é verdade tem uma prova.

---

## Aula Teórica 8

Uma **cláusula** é uma disjunção de literais em que o conjunto vazio representa o `⊥` (elemento neutro da disjunção). A cláusula `{p ∨ ⊥ ∨ q}` é representada por `{p, q}`. Uma fórmula em FNC é um conjunto de cláusulas e pode ser representada por um conjunto de conjuntos que representam cláusulas, em que o conjunto vazio representa o `T` (elemento neutro da conjunção).

A **resolução** consiste em manipulações simbólicas de fórmulas em FNC, que segue a regra da resolução e permite determinar se uma fórmula é contraditória (não satisfazível) ou possível (satisfazível). A **regra da resolução** diz que a partir de duas clásulas `C1` e `C2` tal que para um literal `p` se tem `p ∈ C1` e `¬p ∈ C2` pode-se inferir uma cláusula composta por todos os literais de `C1` e `C2` exceto o `p` e o `~p`. Ou seja, obtêm-se a fórmula `R = (C1 \ {p}) ∪ (C2 \ {¬p})` (cláusula **resolvente**). Uma FNC é contraditória se e só se o `∅` é derivado apenas usando a regra da resolução.

A **dedução natural** consiste num conjunto de regras de inferência que permitem inferir fórmulas a partir de outras fórmulas, permitindo inferir conclusões a partir de um conjunto de hipóteses, determinando a validade de fórmulas ou raciocínio por manipulação sintática das fórmulas. Quer-se saber se a partir de um conjunto de hipóteses (premissas), ∑, é possível construir uma prova para uma fórmula 𝛙 (conclusão) usando as regras de inferência; se possível, então `∑ ⊢ 𝛙`. Se existe uma prova de `∑ ⊢ 𝛙` então 𝛙 é uma **consequência** do conjunto de premissas ∑. Se existe uma prova `⊢ 𝛙`, então 𝛙 é um **teorema** do sistema dedutivo. Dadas duas fórmulas `𝛙, ɸ ∈ Fp`, diz-se que 𝛙 e ɸ são **dedutivamente equivalentes** se e só se `𝛙 ⊢ ɸ` e `ɸ ⊢ 𝛙`, e denota-se por `𝛙 ⊣⊢ ɸ`.

**Teorema:** para uma fórmula C (conclusão) e um conjunto de fórmulas P (premissas), tem-se: **correção**, se P ⊢ C então P ⊨ C; **completude**, se P ⊨ C, então P ⊢ C.

---

## Exercícios

### Aula Teórica 1

#### Diapositivo 34

**Considerando `Pp = {p, q, r}`, calcule `Sf (p ∨ (q → p))`.**

  Sf (p ∨ (q → p)) =
= {p ∨ (q → p)} Sb (p) ∪ Sb (q → p) =
= {p ∨ (q → p)} ∪ {p} ∪ {q → p} ∪ Sb (q) ∪ Sb (p) =
= {p ∨ (q → p), p} ∪ {q → p} ∪ {q} ∪ {p} =
= {p ∨ (q → p), q → p, p, q}

### Aula Teórica 2

#### Diapositivo 14

**Prove que qualquer que seja A € Fp, A contém um número par de parêntesis (0 é um número par).**

Casos Base: A = ⊥ : tem 0 parêntesis (0 é par)
            A = p, p ∈ Pp : tem 0 parêntesis (0 é par)
Passos de Indução: A = ¬Q, Q ∈ Fp
                   H.I.: Q tem um número par de parêntesis, n.
                         Se Q tem n parêntesis, então (¬Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.
                   A = P ∧ Q, P,Q ∈ Fp
                   H.I.: P ∧ Q tem um número par de parêntesis, n.
                         Se P ∧ Q tem n parêntesis, então (P ∧ Q) tem n + 2 parêntesis.
                         Por H.I., n é par, portanto n + 2 também é.
                   A = P ∨ Q, P,Q ∈ Fp
                   H.I.: P ∨ Q tem um número par de parêntesis, n.
                         Se P ∨ Q tem n parêntesis, então (P ∨ Q) tem n + 2 parêntesis.
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

* `(p ↔ q) ∧ (p ↔ r)`
  * `p | q | r | p ↔ q | p ↔ r | (p ↔ q) ∧ (p ↔ r)`
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

### Aula Teórica 4

#### Diapositivo 34

**Determine se `{p, ¬q} ⊨ (p ∨ r) ∧ (¬q ∨ ¬r)`.**

* v(p) = V
* v(¬q) = V ⇔ {definição de valoração}
  * ⇔ ¬v(q) = V ⇔ {¬V = F}
  * ⇔ v(q) = F
* v((p ∨ r) ∧ (¬q ∨ ¬r)) ⇔ {definição de valoração}
  * ⇔ v(p ∨ r) ∧ v(¬q ∨ ¬r) ⇔ {definição de valoração}
  * ⇔ (v(p) ∨ v(r)) ∧ (v(¬q) ∨ v(¬r) ⇔ {v(p) = V; v(¬q) = V}
  * ⇔ (V ∨ v(r)) ∧ (V ∨ v(¬r)) ⇔ {V é o elemento absorvente da disjunção}
  * ⇔ V ∧ V ⇔ {V é o elemento neutro da conjunção}
  * ⇔ V , logo, `{p, ¬q} ⊨ (p ∨ r) ∧ (¬q ∨ ¬r)`

### Aula Teórica 6

#### Diapositivo 55

**Determine a natureza de `ɸ = p ∧ ¬q ∧ (q ∨ ¬p)`.**

### Aula Teórica 7

#### Diapositivo 15

**Utilizando o algoritmo Ƭ, determine a validade de `{p → q, p} ⊨ p ∧ q`.**