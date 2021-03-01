# Lógica Computacional

## Aula Teórica 1

**Lógica:** análise e teoria do pensamento válido; estudo e determinação dos modos de pensamento discursivo que permitem evitar contradições e erros. Utilizada em desenho de _hardware_, linguagens de programação, inteligência artificial e, em especial, na verificação de programas. A maioria dos sistemas críticos são controlados por _software_, que é extremamente importante que funcione bem. Testar um programa mostra a existência de erros, não a ausência deles.

Na **lógica proposicional**, valores booleanos estão na base da lógica (verdadeiro, falso). Proposições são afirmações passíveis de serem verdadeiras ou falsas. Proposições atómicas não podem ser simplificadas; proposições compostas são formadas por proposições atómicas ligadas por conetivos (não [¬], e [⋀], ou [⋁], se [→], se e só se [↔]). O objetivo é determinar se a combinação de proposições atómicas resulta numa conclusão válida - **raciocínio** -, focando nas regras que manipulam os conetivos lógicos.

Um sistema formal de raciocínio é composto por:
* Sintaxe:
  * Alfabeto (símbolos):
    * símbolo ⊥ -> falso/absurdo;
    * proposições atómicas -> Pp = p, q, r...
    * conetivos (ordenados da maior precedência para a menor) -> ¬, ⋀, ⋁, →;
      * Conjunção e disjunção são associatvas à esquerda; implicação é associativa à direita;
    * parêntesis -> (, );
  * Linguagem (fórmulas [Fp]):
    * _BOT_: ⊥ ∈ Fp;
    * _PROP_: se p ∈ Pp, então p ∈ Fp;
    * _NEG_: se p ∈ Fp, então ¬p ∈ Fp;
    * _DIS_: se p, q ∈ Fp, então p ⋁ q ∈ Fp;
    * _CON_: se p, q ∈ Fp, então p ⋀ q ∈ Fp;
    * _IMP_: se p, q ∈ Fp, então p → q ∈ Fp.
* Semântica: significado dos símbolos e fórmulas;
* Cálculo: sistema de prova.

Conjuntos definidos indutivamente são construídos a partir de regras que constroem elementos do conjunto à custa de outros elementos, num número finito de vezes. As regras podem definir os elementos básicos do conjunto e obter novos elementos a partir de elementos do conjunto. Para provar que uma fórmula pertence a Fp tem de se mostrar que existe uma regra ou uma sequência de fórmulas resultantes da aplicação das regras que produz a fórmula desejada (exemplo no diapositivo 29).

As **árvores de derivação (ou dedução)** são utilizadas para mostrar uma prova. A **forma construtiva** constrói-se a partir de árvores singulares (folhas) que correspondem às regras que definem os elementos básicos do conjunto, aplicando-se as regras até obter a fórmula desejada; a **forma destrutiva** constrói-se a partir da conclusão (raiz) utilizando as regras até que se atinjam as folhas (exemplo no diapositivo 31).

Na **lógica de predicados** (lógica de primeira ordem), expressões com uma ou mais incógnitas (variáveis) que são verdadeiras ou falsas dependendo do valor das suas variáveis.

## Exercícios

### Aula Teórica 1, diapositivo 34

**Considerando `Pp = {p, q, r}`, calcule `Sb (p ⋁ (q → p))`.**

  Sb (p ⋁ (q → p)) =
= {p ⋁ (q → p)} ∪ Sb (q → p) =
= {p ⋁ (q → p)} ∪ {q → p} ∪ Sb (q) ∪ Sb (p) =
= {p ⋁ (q → p)} ∪ {q → p} ∪ {q} ∪ {p} =
= {p ⋁ (q → p), q → p, q, p}