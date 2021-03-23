# Programação Funcional

TIPOS:
* `unit`   -> tem um só elemento: `()` (equivalente a `void` em C)
* `bool`   -> tem dois elementos:  `true`, `false`
* `string` -> cadeia de carateres
* `int`    -> número inteiro
* `float`  -> número real

`let const () = 10` -> função constante de valor 10

`let const = 10` -> variável constante de valor 10

`utop` ~> _top level_
 -> ler uma expressão    |
 -> executar a expressão | -> instrução marcada por `;;`
 -> imprimir resultado   |
 -> repetir

`=` / `<>` -> igualdade / diferença de valores (estrutural)

`==` / `!=` -> igualdade / diferença física

`^` -> símbolo de concatenação (equivalente a `+` em Java)

`let` -> declaração de variáveis
* `let variavel = expressao inicial`
* `let (variavel:tipo) = expressao inicial`

`let year = read_int ()` <==> `let year = int_of_string Sys.argv.(1)` (execução durante o programa / passagem como argumento)

O operador `not` tem a prioridade mais forte; a ordem de avaliação para os operadores `&&` e `||` é da esquerda para a direita, sendo que o segundo argumento de ambos só é avaliado se for necessário.

O `scanf` é 'guloso' porque guarda todo o _buffer_ para si, apropriando-se de todo o _stdin_; se se fizer um _read_int_ após, lê-se o final do ficheiro - e não um valor.

Quando uma função é chamada com o prefixo do módulo (por exemplo, `Printf.printf`), diz-se que tem um nome **qualificado** - está-se a qualificar a função `printf` pelo módulo `Printf`. Também se pode abrir o módulo com a instrução `open <nome-do-módulo>`, utilizando as suas funções sem prefixação ao longo do programa.

A ordem de avaliação de uma lista de expressões em OCaml **não é especificada**, no entanto, os mais recentes escolheram avaliar da esquerda para a direita. Regra de ouro: **nunca implementar programas que dependem de mecanismos com comportamento não especificado**. Os parâmetros de uma função são sempre avaliados antes da avaliação da função (**avaliação ansiosa**; existe também a **avaliação preguiçosa**, quando a função é avaliada primeiro que os parâmetros [linguagem Haskell]).

`failwith` - inicia uma exceção específica (`Failure`) com parâmetro único de tipo `string`.

`raise` - levanta exceções escolhidas pelo programador com parâmetro duplo de tipo de exceção e de tipo `string`.

C:
int soma (int x) {
  int i = 0, res = 0;
  for (i = 0; i < x; i++) {
    res += i;
  }
  return res;
}

int soma_rec (int x) {
  return (x <= 0) ? 0 : x + soma_rec (x - 1);
}

OCAML:
let soma x =
  let res = ref 0 in (* res = ref 0 -> implica que o primeiro valor de res é 0, mas que pode ser mutável; ref == referência *)
  for i = 1 to x do
    res := !res + i (* atribui-se o valor de !res + i à variável res, embora res continue sempre a apontar para 0 *)
  done; !res

let rec soma_rec x = if x <= 0 then 0 else x + soma_rec (x - 1)
