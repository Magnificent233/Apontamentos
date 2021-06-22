# Lógica Computacional

##### Atualizado em 11-06-2021
###### A partir de: apontamentos das aulas teóricas

## Aula Teórica 1

**Lógica:** análise e teoria do pensamento válido; estudo e determinação dos modos de pensamento discursivo que permitem evitar contradições e erros. Utilizada em desenho de _hardware_, linguagens de programação, inteligência artificial e, em especial, na verificação de programas. A maioria dos sistemas críticos são controlados por _software_, que é extremamente importante que funcione bem. Testar um programa mostra a existência de erros, não a ausência deles.

Na **lógica proposicional**, valores booleanos estão na base da lógica (verdadeiro, falso). Proposições são afirmações passíveis de serem verdadeiras ou falsas. Proposições atómicas não podem ser simplificadas; proposições compostas são formadas por proposições atómicas ligadas por conetivos (não [¬], e [∧], ou [∨], se [→], se e só se [↔]). O objetivo é determinar se a combinação de proposições atómicas resulta numa conclusão válida - **raciocínio** -, focando nas regras que manipulam os conetivos lógicos.

Um sistema formal de raciocínio é composto por:
* Sintaxe:
  * Alfabeto (símbolos):
    * símbolo ⊥ → falso/absurdo;
    * proposições atómicas → Pp = p, q, r...
    * conetivos (ordenados da maior precedência para a menor) → ¬, ∧, ∨, →, ↔;
      * Conjunção e disjunção são associativas à esquerda; implicação é associativa à direita;
    * parêntesis → (, );
  * Linguagem (fórmulas [Fp]):
    *  ⊥ : `⊥ ∈ Fp`;
    *  PROP : se `p ∈ Pp`, então `p ∈ Fp`;
    *  NEG : se `p ∈ Fp`, então `¬p ∈ Fp`;
    *  DIS : se `p, q ∈ Fp`, então `p ∨ q ∈ Fp`;
    *  CON : se `p, q ∈ Fp`, então `p ∧ q ∈ Fp`;
    *  IMP : se `p, q ∈ Fp`, então `p → q ∈ Fp`.
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

**Propriedades da Álgebra de Boole** (assumindo `p, q ∈ {V, F}`; provas nos diapositivos 25-26):
* `¬(¬p) = p`;
* `p ∧ p = p` e `p ∨ p = p`;
* `p ∨ ¬p = V`;
* `p ∧ ¬p = F`;
* `¬(p ∨ q) = (¬p) ∧ (¬q)`;
* `¬(p ∧ q) = (¬p) ∨ (¬q)`.

**Extensão da Valoração para Fp:** função `v: Fp → {V, F}`, definida indutivamente da seguinte forma, `P, Q ∈ Fp`:
* `v(⊥) = F`;
* `∀ p ∈ Pp`, se `P = p` então `v(P) = p`;
* `v(P ∧ Q) = v(P) ∧ v(Q)`;
* `v(P ∨ Q) = v(P) ∨ v(Q)`;
* `v(P → Q) = (¬v(P)) ∨ v(Q)`.

---

## Aula Teórica 3

**Proposição** (satisfazibilidade): `v ⊩ P` se `v ⊮ ¬P` e `v ⊮ P` se `v ⊩ ¬P`.

Dado `S ⊆ Fp`, se `v ⊩ Q` para todo o `Q ∈ S`, então `v ⊩ S`. `S ⊆ Fp` diz-se _possível_ se existe uma valoração v que satisfaz todas as fórmulas de S, caso contrário, diz-se _contraditório_. Uma fórmula `Q ∈ Fp` é:
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

A consequência semântica é _reflexiva_ (`A ⊨ A`) e _transitiva_ (`A ⊨ B` e `B ⊨ C` então `A ⊨ C`, `A, B, C ∈ Fp`), logo, é uma **pré-ordem**.

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

Um **literal** é uma proposição atómica (literal positivo) ou a sua negação (literal negativo). Uma disjunção de literais (`(n)∨ (i = j) L_i`) é uma tautologia se e só se existirem `1 ≤ i`, `j ≤ n`, `L_i = T` ou `L_i = ¬L_j`.

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
* Algoritmo Ƭ - algoritmo determinístico que verifica a validade de uma fórmula, que usa as seguintes regras (`Ƭ(S) = CNF (NNF (IMPL FREE (S)))`):
  * `IMPL FREE` - remove todas as implicações (`P → Q = ¬P ∨ Q`);
  * `NNF` - remove negações duplas (`¬¬`) e negações de fórmulas não atómicas pelas regras de De Morgan, transformando em FNN;
  * `CNF`
    * Se `S` é um literal, `CNF(S) = S`;
    * Se `S = S_1 ∧ S_2`, então `CNF(S_1) ∧ CNF(S_2)`;
    * Se `S = S_1 ∨ S_2`, então `CNF(S_1) ∨ CNF(S_2)` e define-se `DISTR`, que aplica as leis da distributividade de forma apropriada.
* Algoritmo de Horn (Ɦ) - fórmula em FNC em que em cada disjunção existe no máximo um literal positivo, que verifica a satisfazibilidade de uma fórmula:
  * **Lema:** `L ≡ T → L`; `n^∨_i=1 ¬L_i ≡ (n^∧_i=1 L_i) → ⊥`; `n^∨_i=1 ¬L_i ∨ L ≡ (n^∧_i=1 L_i) → L` - transforma uma fórmula de Horn em forma de Horn;
  * **Teorema:** `Ɦ(S) = V` se e só se S é possível; `Ɦ(S) = F` se e só se S é contraditória;
  * **Lema:** sejam `C_0, C_1 ⊆ P_p ∪ {⊥, ⊤}` e F uma fórmula em forma de Horn. `A` é **monótona** se `C_0 ⊆ C_1 → A(F, C_0) ⊆ A(F, C_1)`. `A` é **crescente** se `C_0 ⊆ A(F, C_0) ⊆ C_0 ∪ n^∪_i=1 L_i`;
    * A negação de uma fórmula válida é contraditória (e vice-versa);
    * Determina-se `T = Ƭ(¬S)`. Se T é forma de Horn, calcula-se Ƭ: se for `F`, então S é válida dado que T é contraditória e `T ≡ ¬S`.

---

## Aula Teórica 7

**Proposição:** considere-se uma fórmula de Horn, Q, que é satisfazível e tal que `A(Q, ⊤) = S` e `⊥ ∉ S`. Tem-se que `v ⊩ Q` quando `v(p) = V` para todo o `p ∈ S` e `v(q) = F` para todo o `q ∉ S`.

Um sistema de prova é:
* **Correto (_Soundness_)** se tudo o que se consegue provar é de facto verdade:
  * **Teorema:** para uma fórmula Q em forma de Horn, tem-se que `Ɦ(Q) = V` se e só se Q é possível (**SAT**); `Ɦ(Q) = F` se e só se Q é contraditória (**UNSAT**);
* **Completo (_Completeness_)** se tudo o que é verdade tem uma prova.

---

## Aula Teórica 8

Uma **cláusula** é uma disjunção de literais em que o conjunto vazio representa o `⊥` (elemento neutro da disjunção). A cláusula `{p ∨ ⊥ ∨ q}` é representada por `{p, q}`. Uma fórmula em FNC é um conjunto de cláusulas e pode ser representada por um conjunto de conjuntos que representam cláusulas, em que o conjunto vazio representa o `T` (elemento neutro da conjunção).

A **resolução** consiste em manipulações simbólicas de fórmulas em FNC, que segue a regra da resolução e permite determinar se uma fórmula é contraditória (não satisfazível) ou possível (satisfazível). A **regra da resolução** diz que a partir de duas clásulas `C_1` e `C_2` tal que para um literal `p` se tem `p ∈ C_1` e `¬p ∈ C_2` pode-se inferir uma cláusula composta por todos os literais de `C_1` e `C_2` exceto o `p` e o `¬p`. Ou seja, obtêm-se a fórmula `R = (C_1 \ {p}) ∪ (C_2 \ {¬p})` (cláusula **resolvente**). Uma FNC é contraditória se e só se o `∅` é derivado apenas usando a regra da resolução.

A **dedução natural** consiste num conjunto de regras de inferência que permitem inferir fórmulas a partir de outras fórmulas, permitindo inferir conclusões a partir de um conjunto de hipóteses, determinando a validade de fórmulas ou raciocínio por manipulação sintática das fórmulas. Quer-se saber se a partir de um conjunto de hipóteses (premissas), ∑, é possível construir uma prova para uma fórmula 𝛙 (conclusão) usando as regras de inferência; se possível, então `∑ ⊢ 𝛙`. Se existe uma prova de `∑ ⊢ 𝛙` então 𝛙 é uma **consequência** do conjunto de premissas ∑. Se existe uma prova `⊢ 𝛙`, então 𝛙 é um **teorema** do sistema dedutivo. Dadas duas fórmulas `𝛙, φ ∈ Fp`, diz-se que 𝛙 e φ são **dedutivamente equivalentes** se e só se `𝛙 ⊢ φ` e `φ ⊢ 𝛙`, e denota-se por `𝛙 ⊣⊢ φ`.

**Teorema:** para uma fórmula C (conclusão) e um conjunto de fórmulas P (premissas), tem-se: **correção**, se `P ⊢ C` então `P ⊨ C`; **completude**, se `P ⊨ C`, então `P ⊢ C`.

---

## Aula Teórica 9

Em **lógica de primeira ordem** existem:
* **Termos**, que denotam entidades/objetos em estudo:
  * _Variáveis_ - representadas por letras minúsculas, denotam elementos não especificados e podem ser vistas como _placeholders_ para valores concretos;
  * _Constantes_ (C) - denotam elementos concretos;
  * _Funções_ (F) - denotam transformações sobre elementos (variáveis ou constantes), representadas por letras ou nomes com letra minúscula;
* **Fórmulas**, que denotam valores de verdade:
  * _Predicados_ - expressam propriedades/relações;
  * _Fórmulas com quantificadores_ - `∃`, quantificador existencial (existe pelo menos um elemento do domínio considerado que satisfaz a propriedade); `∀`, quantificador universal (todos os elementos do domínio considerado satisfazem a propriedade).

Um sistema formal de raciocínio é composto por **sintaxe** (alfabeto, conjunto de símbolos; linguagem, conjunto de fórmulas), **semântica** (significado de termos e fórmulas) e **cálculo** (sistema de prova e raciocínio). Uma assinatura de primeira ordem consiste num par de conjuntos distintos, `Σ = (SF, SP)`, onde `SF = {SF_i}, i ≥ 0` é um conjunto de conjuntos disjuntos de símbolos de função (se `i = 0` as funções são constantes) e `SP = {SP_i}, i ≥ 0` é um conjunto de conjuntos disjuntos de símbolos de predicado.

**Definição:** o conjunto de variáveis num termo `Vars^T_∑`, denotado por V(t), é definido indutivamente como: `V(x) = {x}` para todo o `x ∈ Vars`; `V(c) = ∅` para todo o `c ∈ SF_0`; se `t_1, ..., t_n ∈ Vars^T_∑` e `f ∈ SF_n, n ≥ 0`, então `V(f(t_1, ..., t_n)) = n^∪_i=1 V(t_i)`. Um termo diz-se **fechado** se não contém variáveis ou **aberto** caso contrário.

As **variáveis livres** de uma fórmula φ (`FV(φ)`) são as que ocorrem em φ sem estarem quantificadas; as **variáveis ligadas** de uma fórmula φ (`BV(φ)`) são as que ocorrem quantificadas em φ. Uma fórmula diz-se **fechada** se não contém variáveis livres ou **aberta** caso contrário (definição formal nos diapositivo 54 e 55). **Definição:** o conjunto das variáveis ligadas numa fórmula `φ ∈ Vars^F_Σ` define-se como `V(φ) = FV(φ) ∪ BV(φ)`.

**Definições:** seja `φ ∈ Vars^F_Σ` e `FV() = {x_1, ..., x_n}, n ≥ 0`. Então, `∀ x_1 ... ∀ x_n φ` é o **fecho universal** de φ e `∃ x_1 ... ∃ x_n φ` é o **fecho existencial** de φ.

A **substituição** de variáveis por termos (`{t/x}`) só pode ser aplicada a variáveis livres, definida indutivamente por:
* `x{t/x} = t` para todo `x ∈ Vars`;
* `c{t/x} = c` para todo `c ∈ SF_0`;
* se `t_1, ..., t_n ∈ Vars^T Σ` e `f ∈ SF n`, `n >= 0`, então `f(t_1, ..., t_n){t/x} = f(t_1{t/x}, ..., t_n{t/x})`.

A substituição também pode ser aplicada a fórmulas. Dadas `𝛙, φ ∈ Vars^F_Σ`, `x ∈ Vars`, `t ∈ Vars^T_Σ`, a fórmula `φ{t/x}` é definida indutivamente por:
* `⊥{t/x} = ⊥` e `Q{t/x} = Q` se `Q ∈ SP_0`;
* se `t_1, ..., t_n ∈ Vars^T_Σ` e `P(t_1, ..., t_n) ∈ Vars^F_Σ` para todo `P ∈ SP_n`, `n >= 0`, então `P(t_1, ..., t_n) = P(t_1{t/x}, ..., t_n{t/x})`;
* `(¬φ){t/x} = ¬(φ{t/x})`;
* `(φ ◇ 𝛙){t/x} = φ{t/x} ◇ 𝛙{t/x}`, para `◇ ∈ {∧, ∨, →}`;
* `(∀x φ){t/x} = ∀x φ` e `(∃x φ){t/x} = ∃x φ`;
* `(∀y φ){t/x} = ∀y (φ{t/x})` e `(∃x φ){t/x} = ∃x (φ{t/x})`, com `y ∈ Vars\{x}`.

Dadas `𝛙, φ ∈ Vars^F_Σ`, `x ∈ Vars`, `t ∈ Vars^T_Σ`, o termo t diz-se **livre para x** em φ se:
* φ é uma fórmula atómica (predicado ou ⊥);
* `φ = ¬𝛙` e t é livre para x em φ;
* `φ = 𝛙_1 ◇ 𝛙_2`, para `◇ ∈ {∧, ∨, →}`, t é livre para x em 𝛙_1 e 𝛙_2;
* `φ = ∀x 𝛙` e `φ = ∃x 𝛙`;
* `φ = ∀y 𝛙` e `φ = ∃y 𝛙`, com `y ∈ Vars\{x}`, `y ∉ V(t)` e t livre para x em φ.

---

## Aula Teórica 10

A lógica proposicional é **decidível** por tabelas de verdade ou problema de decisão SAT (programa que determina a satisfazibilidade de uma fórmula e a valoração que a satisfaz) ou SMT (_Satisfiability Modulo Theories_, uma extensão de SAT).

A lógica de primeira ordem é **indecidível**. A avaliação de uma fórmula depende do significado de variáveis, quantificadores e símbolos de função e predicado num dado universo. Uma **estrutura de interpretação** sobre `Σ = (SF, SP)` é um par `Ɱ = (U, I)` onde:
* `U` é um conjunto não vazio - **universo**, ou domínio, da estrutura;
* `I` é uma **função de interpretação** tal que:
  * associa a cada `c ∈ SF_0` uma constante `I(c) ∈ U`;
  * associa a cada símbolo de função `f` em cada `SF_n`, `n > 0`, uma função n-ária `I(f) : U^n → U`;
  * associa a cada símbolo de predicado `P` em cada `SP_n`, `n >= 0`, um predicado n-ário `I(P) : U^n → {V, F}` (predicados `P` 0-ários (`P ∈ SP_0`) são interpretados como valores de verdade (V, F)).

Uma **atribuição** em `Ɱ = (U, I)` é uma função `ρ: Vars → U` que associa a cada variável em `Vars` um elemento do domínio `U`, denotando-se `ρ [x → a]` a atribuição que mapeia `x` para `a` e todas as outras variáveis `y` para `ρ(y)`.

Dada uma estrutura de interpretação `Ɱ = (U, I)` sobre uma assinatura `Σ = (SF, SP)` e uma atribuição `ρ ∈ Vars^ATR_Ɱ`, a **interpretação dos termos** em `Ɱ` com `ρ` é dada por uma função `ρ^⟦.⟧_Ɱ : Vars^T_Σ → U` definida indutivamente por:
* `ρ^⟦x⟧_Ɱ = ρ(x)`, para `x ∈ Vars`;
* `ρ^⟦c⟧_Ɱ = I(c)`, para `c ∈ SF_0`;
* `ρ^⟦f(t_1, ..., t_n⟧_Ɱ = I(f)(ρ^⟦t_1⟧_Ɱ, ..., ρ^⟦t_n⟧,_Ɱ`, para `t ∈ SF_n` e `t_1, ..., t_n ∈ Vars^T_Σ`, com `n > 0`.

Dada uma estrutura de interpretação `Ɱ = (U, I)` sobre uma assinatura `Σ = (SF, SP)` e uma atribuição `ρ ∈ Vars^ATR_Ɱ`, a **avaliação de uma fórmula** em `Ɱ` com `ρ` é dada por uma função `ρ^⟦.⟧_Ɱ : Vars^T_Σ → U` definida indutivamente por:
* `ρ^⟦⊥⟧_Ɱ = F`;
* `ρ^⟦P⟧_Ɱ = I(P)`, para todo `P ∈ SP_0`;
* `ρ^⟦P(t_1, ..., t_n)⟧_Ɱ = I(P)(ρ^⟦t_1⟧_Ɱ, ..., ρ^⟦t_n⟧_Ɱ)`, para todo `P ∈ SP_0` e `t_1, ..., t_n ∈ Vars^T_S`, com `n > 0`;
* `ρ^⟦¬φ⟧_Ɱ = ¬ρ^⟦φ⟧_Ɱ`;
* `ρ^⟦φ ∧ 𝛙⟧_Ɱ = ρ^⟦φ⟧_Ɱ ∧ ρ^⟦𝛙⟧_Ɱ`;
* `ρ^⟦φ ∨ 𝛙⟧_Ɱ = ρ^⟦φ⟧_Ɱ ∨ ρ^⟦𝛙⟧_Ɱ`;
* `ρ^⟦φ → 𝛙⟧_Ɱ = ¬ρ^⟦φ⟧_Ɱ ∨ ρ^⟦𝛙⟧_Ɱ`;
* `ρ^⟦∀x φ⟧_Ɱ = V` se `ρ[x → u]^⟦φ⟧_Ɱ = V` para todo o `u ∈ U` e `ρ^⟦∀x φ⟧_Ɱ = F` se `ρ[x → u]^⟦φ⟧_Ɱ = F` para todo o `u ∈ U`;
* `ρ^⟦∃x φ⟧_Ɱ = V` se `ρ[x → u]^⟦φ⟧_Ɱ = V` para todo o `u ∈ U` e `ρ^⟦∃x φ⟧_Ɱ = F` se `ρ[x → u]^⟦φ⟧_Ɱ = F` para todo o `u ∈ U`.

Diz-se que uma fórmula `𝛙` é **satisfeita** por `Ɱ` com `ρ` (`Ɱ, ρ ⊩ 𝛙`) se `ρ^⟦𝛙⟧_Ɱ = V` e **não satisfeita** por `Ɱ` com `ρ` (`Ɱ, ρ ⊮ 𝛙`) se `ρ^⟦𝛙⟧_Ɱ = F`. Diz-se que uma fórmula `𝛙` é **satisfeita** por `Ɱ` (`Ɱ ⊩ 𝛙`) se para toda a atribuição `ρ` se tem `Ɱ, ρ ⊩ 𝛙` - `Ɱ` é chamado um **modelo** de `𝛙`. `Ɱ, ρ ⊩ ¬𝛙` se e só se `Ɱ ⊮ 𝛙`, e `Ɱ ⊩ ¬𝛙` se e só se `Ɱ ⊮ 𝛙`.

Uma fórmula `𝛙` diz-se **satisfazível** ou **possível** se existir uma estrutura de interpretação `Ɱ` e uma atribuição `ρ` tal que `Ɱ, ρ ⊩ 𝛙`; **contraditória** se não é possível; **válida** ou **tautologia** se para toda a estrutura de interpretação `Ɱ` e toda a atribuição `ρ` se tem `Ɱ, ρ ⊩ 𝛙`, ou seja, `Ɱ ⊩ 𝛙` (`⊨ 𝛙`).

Uma estrutura de interpretação `Ɱ` com uma atribuição `ρ` satisfaz um conjunto de fórmulas `Γ ⊆ Vars^F_∑` se satisfizer todas as fórmulas de `Γ` (`Ɱ, ρ ⊩ Γ`). Uma fórmula `𝛙` é uma **consequência semântica** de `Γ` se para toda a estrutura de interpretação `Ɱ` e toda a atribuição `ρ` tal que `Ɱ, ρ ⊩ Γ` se tem `Ɱ, ρ ⊩ 𝛙` (`Γ ⊨ 𝛙`). Duas fórmulas `𝛙` e `φ` dizem-se **logicamente equivalentes** se para toda a estrutura de interpretação `Ɱ` e toda a atribuição `ρ` se tem `Ɱ, ρ ⊩ 𝛙` se e só se `Ɱ, ρ ⊩ φ` (`𝛙 ≡ φ`).

---

## Aula Teórica 11

Uma fórmula de primeira ordem diz-se na **Forma Normal Prenex** (FNP) quando todos os quantificadores ocorrem no exterior da fórmula. Considere-se uma fórmula `A` na forma normal prenex `A ≡ Q_1 x_1 ... Q_n x_n B` onde cada `Q_i` é um quantificador, com `1 <= i <= n`; se `FNC(B)` então diz-se que `A` está na Forma Normal Conjuntiva Prenex (FNCP). A conversão para FNP segue os seguintes passos:
* Eliminação dos símbolos de implicação (`𝛙 → φ ≡ ¬𝛙 ∨ φ`) ;
* Aplicação das leis de De Morgan até não existirem quantificadores negados (`¬∀x φ ≡ ∃x ¬φ`; `¬∃x φ ≡ ∀x ¬φ`);
* Passagem dos quantificadores para o início da fórmula, com `x' ∉ FV(𝛙)`, renomeando variáveis com o mesmo símbolo mas ligadas a quantificadores diferentes para que todos os quantificadores utilizem variáveis distintas:
  * `𝛙 ∧ (∀x φ) ≡ ∀x' (𝛙 ∧ φ{x'/x}`;
  * `𝛙 ∨ (∀x φ) ≡ ∀x' (𝛙 ∨ φ{x'/x}`;
  * `𝛙 ∧ (∃x φ) ≡ ∃x' (𝛙 ∧ φ{x'/x}`;
  * `𝛙 ∨ (∃x φ) ≡ ∃x' (𝛙 ∨ φ{x'/x}`.

Uma fórmula na forma prenex diz-se **universal** quando só contém quantificadores universais. Uma fórmula `A` de primeira ordem encontra-se na **Forma Normal de Skolem** (FNS) se `A ≡ ∀x_1 ... ∀x_n B` e `B` se encontra na forma normal conjuntiva. A skolemização consiste em:
* Converter a fórmula em forma normal conjunta prenex;
* Substituir todas as ocorrências de variáveis existencialmente quantificadas por novas funções das variáveis quantificadas universalmente que as precedem (`∀x_1 ... ∀x_n ∃y B ⇝ ∀x_1 ... ∀x_n B{f(x_1, ..., x_n)/y}`).

Para executar a **resolução**, para além da skolemização, deve-se concluir a transformação da fórmula inicial em conjuntos de cláusulas através dos seguintes passos:
* Circunscrever os quantificadores aos conjuntos FNC (`∀x (P(x) ∧ Q(x)) ≡ ∀x P(x) ∧ ∀x Q(x)`);
* Renomear as variáveis universalmente quantificadas (`∀x (P(x) ∧ Q(x)) ≡ ∀x P(x) ∧ ∀y Q(y)`);
* Separar as cláusulas;
* Eliminar os quantificadores.

Um conjunto de literais `L` diz-se **unificável** se existe uma substituição que aplicada a `L` torna o conjunto singular (em que os vários literais ficam todos iguais), sendo que as unificações não são necessariamente únicas. Uma variável não pode ser unificada com uma função que a contém.

**Algoritmo Martelli-Montanari:** seja `U` um conjunto de pares de termos (predicados, funções, variáveis) `s_1 ≈ t_1`; enquanto for possível, escolhe-se arbitrariamente um par de termos de `U` de um dos tipos e executa-se a ação correspondente. Se não abortar, o algoritmo termina e o `U` final é o **unificador mais geral** (umg):
* `f(s_1, ..., s_n) ≈ f(t_1, ..., t_n)` - substituir em `U` pelos pares `s_1 ≈ t_1, ..., s_n ≈ t_n`;
* `f(s_1, ..., s_n) ≈ g(t_1, ..., t_n)`, com `f != g` - abortar, não é possível unificar;
* `x ≈ x` - apagar, pois corresponde a uma substituição vazia (sem qualquer efeito);
* `t ≈ x` em que `t` não é uma variável - substituir por `x ≈ t`;
* `x ≈ t` em que `x` não ocorre em `t` - substituir por `t/x` e aplicar a substituição `{t/x}` em todos os outros pares de `U`;
* `x ≈ t` em que `x` ocorre em `t` - abortar, não é possível unificar.

---

## Exercícios

### Aula Teórica 1

#### Diapositivo 34

**Considerando `Pp = {p, q, r}`, calcule `Sf (p ∨ (q → p))`.**

```
  Sf (p ∨ (q → p)) =
= {p ∨ (q → p)} Sb (p) ∪ Sb (q → p) =
= {p ∨ (q → p)} ∪ {p} ∪ {q → p} ∪ Sb (q) ∪ Sb (p) =
= {p ∨ (q → p), p} ∪ {q → p} ∪ {q} ∪ {p} =
= {p ∨ (q → p), q → p, p, q}
```

### Aula Teórica 2

#### Diapositivo 14

**Prove que qualquer que seja A ∈ Fp, A contém um número par de parêntesis (0 é um número par).**
```
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
```

### Aula Teórica 3

#### Diapositivo 38

**Construa a tabela de verdade das seguintes proposições:**

```
1. (p ↔ q) ↔ r
  p | q | r | p ↔ q | (p ↔ q) ↔ r
  V | V | V |   V   |    V
  V | V | F |   V   |    F
  V | F | V |   F   |    F
  V | F | F |   F   |    V
  F | V | V |   F   |    F
  F | V | F |   F   |    V
  F | F | V |   V   |    V
  F | F | F |   V   |    F

2. (p ↔ q) ∧ (p ↔ r)
  p | q | r | p ↔ q | p ↔ r | (p ↔ q) ∧ (p ↔ r)
  V | V | V |   V   |   V   |       V
  V | V | F |   V   |   F   |       F
  V | F | V |   F   |   V   |       F
  V | F | F |   F   |   F   |       F
  F | V | V |   F   |   F   |       F
  F | V | F |   F   |   V   |       F
  F | F | V |   V   |   F   |       F
  F | F | F |   V   |   V   |       V
```

#### Diapositivo 44

**Verifique se `(a → b) ↔ (¬b → ¬a)` é válida, contraditória ou possível.**

```
A fórmula é válida:
  a | b | ¬a | ¬b | (a → b) | (¬b → ¬a) | (a → b) ↔ (¬b → ¬a)
  V | V |  F |  F |    V    |     V     |         V
  V | F |  F |  V |    F    |     F     |         V
  F | V |  V |  F |    V    |     V     |         V
  F | F |  V |  V |    V    |     V     |         V
```

### Aula Teórica 4

#### Diapositivo 34

**Determine se `{p, ¬q} ⊨ (p ∨ r) ∧ (¬q ∨ ¬r)`.**

```
v(p) = V
v(¬q) = V ⇔ {definição de valoração}
  ⇔ ¬v(q) = V ⇔ {¬V = F}
  ⇔ v(q) = F
v((p ∨ r) ∧ (¬q ∨ ¬r)) ⇔ {definição de valoração}
  ⇔ v(p ∨ r) ∧ v(¬q ∨ ¬r) ⇔ {definição de valoração}
  ⇔ (v(p) ∨ v(r)) ∧ (v(¬q) ∨ v(¬r) ⇔ {v(p) = V; v(¬q) = V}
  ⇔ (V ∨ v(r)) ∧ (V ∨ v(¬r)) ⇔ {V é o elemento absorvente da disjunção}
  ⇔ V ∧ V ⇔ {V é o elemento neutro da conjunção}
  ⇔ V , logo, `{p, ¬q} ⊨ (p ∨ r) ∧ (¬q ∨ ¬r)`
```

### Aula Teórica 6

#### Diapositivo 55

**Determine a natureza de `φ = p ∧ ¬q ∧ (q ∨ ¬p)`.**

```
φ = p ∧ ¬q ∧ (q ∨ ¬p) ≡ (⊤ → p) ∧ (q → ⊥) ∧ (p → q) = 𝛙
  A (𝛙, {⊤}) =
= A ((⊤ → p) ∧ (q → ⊥)  (p → q), {⊤}) =
= A ((q → ⊥)  (p → q), {⊤, p}) =
= A (q → ⊥, {⊤, p, q}) = 
= A (⊤, {⊤, p, q, ⊥}) =
= {⊤, p, q, ⊥}
Como ⊥ € A(𝛙, {⊤}), então Ɦ(𝛙) = F, logo, 𝛙 é contraditória. Como 𝛙 ≡ φ, então φ também é contraditória.
```


### Aula Teórica 7

#### Diapositivo 15

**Utilizando o algoritmo Ƭ, determine a validade de `{p → q, p} ⊨ p ∧ q`.**

```
φ = {p → q, p} ⊨ p ∧ q ≡ ⊨ ((p → q) ∨ p) → (p ∧ q) = 𝛙
Ƭ(𝛙) = CNF(NNF(IMPL_FREE(𝛙))) = CNF(NNF(IMPL_FREE(((p → q) ∨ p) → (p ∧ q))))
  IMPL_FREE(((p → q) ∨ p) → (p ∧ q)) =
= ¬IMPL_FREE((p → q) ∨ p) ∨ IMPL_FREE (p ∧ q) = (otimização)
= ¬((IMPL_FREE(p → q)) ∨ p) ∨ (p ∧ q) =
= ¬((¬IMPL_FREE(p) ∨ IMPL_FREE(q)) ∨ p) ∨ (p ∧ q) = (otimização)
= ¬((¬p ∨ q) ∨ p) ∨ (p ∧ q)
  NNF(¬((¬p ∨ q) ∨ p) ∨ (p ∧ q)) =
= (NNF(¬(¬p ∨ q)) ∧ NNF(¬p)) ∨ NNF(p ∧ q) = (otimização)
= ((NNF(¬¬p) ∧ NNF(¬q)) ∧ ¬p) ∨ (p ∧ q) = (otimização)
= ((p ∧ ¬q) ∧ ¬p) ∨ (p ∧ q)
  CNF(((p ∧ ¬q) ∧ ¬p) ∨ (p ∧ q)) =
= DISTR(CNF((p ∧ ¬q) ∧ ¬p), CNF(p ∧ q)) = (otimização)
= DISTR((p ∧ ¬q) ∧ ¬p, p ∧ q) =
= ((p ∧ ¬q) ∧ ¬p) ∧ (p ∧ q) = (associatividade, simetria, idempotência da conjunção)
= p ∧ ¬p ∧ q ∧ ¬q
Como, para qualquer valoração de p e q, 𝛙 é falsa, então também φ é falsa e, por isso, {p → q, p} ⊭ p ∧ q.
```

### Aula Teórica 9

#### Diapositivo 65

**Calcule as seguintes substituições:**
```
1. (∃x (P(x,y) ∧ ∀y (¬Q(x, y)))){s(z)/y} =
= ∃x (P(x,y){s(z)/y} ∧ (∀y (¬Q(x, y)){s(z)/y})) =
= ∃x (P(x{s(z)/y}, y{s(z)/y}) ∧ ∀y (¬Q(x, y){s(z)/y})) =
= ∃x (P(x, s(z)) ∧ ∀y (¬Q(x{s(z)/y}, y{s(z)/y})) =
= ∃x (P(x, s(z)) ∧ ∀y (¬Q(x, s(z))

2. (∃x (P(x,y) ∧ ∀y (¬Q(x, y)))){s(z)/x} =
= ∃x (P(x,y){s(z)/x} ∧ (∀y (¬Q(x, y)){s(z)/x})) =
= ∃x (P(x{s(z)/x}, y{s(z)/x}) ∧ ∀y (¬Q(x, y){s(z)/x})) =
= ∃x (P(s(z), y) ∧ ∀y (¬Q(x{s(z)/x}, y{s(z)/x})) =
= ∃x (P(s(z), y) ∧ ∀y (¬Q(s(z), y)
```