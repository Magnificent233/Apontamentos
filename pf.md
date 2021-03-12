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