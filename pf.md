# Programação Funcional

##### Atualizado em 10-06-2021
###### A partir de: https://ocaml.org/learn/tutorials/

**Tipos de variáveis:**
* `unit`   -> tem um só elemento: `()` (equivalente a `void` em C)
* `bool`   -> tem dois elementos:  `true`, `false`
* `char`   -> caratere de 8 bits
* `string` -> cadeia imutável de carateres
* `int`    -> número inteiro
* `float`  -> número real

**Declaração de variáveis:**
* `let n = valor in` -> variável imutável de tipo indefinido 
* `let (n:tipo) = valor in` -> variável imutável de tipo definido pelo programador
* `let m = ref valor in` -> variável de tipo indefinido que aponta para 'valor' mas cujo valor pode ser alterado
  * `m := !m + 1` -> atribuição de um novo valor a m, recebendo o seu valor atual
* `let const = 10` -> variável constante de valor 10

**Declaração de funções:**
* `let const () = 10` -> função constante de valor 10
* `let fun x -> x * 2` -> função sem nome (que no caso devolve o dobro do número passado em parâmetro)
* `let rec contar = ...` -> função recursiva
  * As instruções dentro de uma função / ciclo são separadas por `;`, o final de uma função ou instrução simples é assinalado por `;;`
  * `let year = read_int ()` <==> `let year = int_of_string Sys.argv.(1)` (execução durante o programa / passagem como argumento)


**Ciclos:**
* `while condicao do instrucoes done`
* `if condicao then instrucoes else instrucoes` -> as instruções do `then` e do `else` devem ser sempre do mesmo tipo
  * Para encapsular `if-then-else`'s entre si, usam-se as cláusulas `begin` e `end` (ou apenas `(` e `)`)
* `for i = valor-minimo to valor-maximo do instrucoes done`
* `for i = valor-maximo downto valor-minimo do instrucoes done`

**_Pattern-Matching_:**
* `let rec fatorial n = if n <= 1 then 1 else n * fatorial (n - 1);;` é equivalente a:
  * `let rec fatorial n = match n with` ou `let rec fatorial n = function`
  * `| 0 | 1 -> 1`
  * `| x -> x * fatorial (x - 1);;` ou `| _ -> x * fatorial (x - 1);;`, em que `_` simboliza qualquer outro símbolo 

**Listas:**
* `[];;` -> cria uma lista vazia
* `[[1; 2]; [3; 4]; [5; 6]];;` -> cria uma lista de listas (inicializada para exemplo)
  * Cada lista tem uma cabeça (primeiro elemento) e uma cauda (último elemento)
  * O símbolo `::` adiciona um elemento ao início de uma lista (`1 :: [2; 3];;` == `[1; 2; 3]`)
  * O símbolo `@` concatena duas listas (`[1] @ [2; 3]` == `[1; 2; 3]`)
  * **Funções**
    * `List.iter` -> chama uma função para cada elemento de uma lista
    * `List.map` -> chama uma instrução para cada elemento de uma lista
    * `List.filter` -> devolve apenas os elementos de uma lista que satisfazem uma dada condição
    * `List.mem` -> verifica a existência de um dado elemento numa lista
    * `List.fold` (`left` e `right`) -> aplica uma operação (+, -, /, *) a todos os elementos de uma lista a partir da cabeça ou da cauda

**Outros tipos:**
* `let arr = [|1; 2; 3|];;` -> arrays (espécie de lista de tamanho fixo)
* `let t = (1, "one", '1');;` -> tuplos (armazenamento de elementos de diferentes tipos)
* `type person = {first_name : string; surname : string; mutable age : int};;` -> define um tipo criado pelo utilizador para ser usado ao longo do programa
  * A cláusula `mutable` define um valor que pode ser alterado ao longo do programa
  * `let frank = {first_name = "Frank"; surname = "Smith"; age = 40};;`

**Exceções:**
* `failwith` -> inicia uma exceção específica (`Failure`) com parâmetro único de tipo `string`
* `raise` -> levanta exceções escolhidas pelo programador com parâmetro duplo de tipo de exceção e de tipo `string`
* `try ... with` -> tenta realizar algo, se não conseguir, lança uma exceção
* `type 'a option = None | Some of 'a` -> retorna valores de um tipo (resultado correto ou erro)
  * `let f a b = if b = 0 then None else Some (a / b);;`
  * `let list_find_opt p l = try Some (List.find p l) with Not_found -> None;;`
  * `let list_find_opt p l = match List.find p l with`
    * `| v -> Some v`
    * `| exception Not_found -> None;;`

**Símbolos / Cláusulas:**
* `.` -> diferença entre valores de tipo inteiro e flutuante
* `=` / `<>` -> igualdade / diferença de valores (estrutural)
* `==` / `!=` -> igualdade / diferença física
* `^` -> concatenação de _strings_ (equivalente a `+` em Java)
* `not` / `||` / `&&` -> operadores lógicos (negação, disjunção, conjunção)
  * O operador `not` tem a prioridade mais forte; a ordem de avaliação para os operadores `&` e `|` é da esquerda para a direita, sendo que o segundo argumento de ambos só é avaliado se for necessário
* `when` -> 'guarda' de _pattern-match_ que só permite uma instrução se o padrão é semelhante e a condição é satisfeita
* `and` -> declaração de variáveis mutuamente recursivas
* `~` -> rótulo de variáveis, permitindo a troca de ordem na passagem de argumentos
* `?` -> passagem de argumentos facultativos para uma função
* `!^` / `^:=` -> atribuição / dereferenciação de ponteiros

**Orientação a Objetos:**
* `class name = object (self) ... end` -> definição de uma classe '_name_'
* `val mutable variable = ...` -> definição de variável de instância
* `method metodo [variaveis] = ...` -> definição de métodos
* `object#method` -> atribuição de um método a um objeto

**Outros:**
* O `scanf` é 'guloso' porque guarda todo o _buffer_ para si, apropriando-se de todo o _stdin_; se se fizer um _read_int_ após, lê-se o final do ficheiro - e não um valor
* Quando uma função é chamada com o prefixo do módulo (por exemplo, `Printf.printf`), diz-se que tem um nome **qualificado** - está-se a qualificar a função `printf` pelo módulo `Printf`. Também se pode abrir o módulo com a instrução `open <nome-do-módulo>`, utilizando as suas funções sem prefixação ao longo do programa
* A ordem de avaliação de uma lista de expressões em OCaml **não é especificada**, no entanto, os mais recentes escolheram avaliar da esquerda para a direita. Regra de ouro: **nunca implementar programas que dependem de mecanismos com comportamento não especificado**. Os parâmetros de uma função são sempre avaliados antes da avaliação da função (**avaliação ansiosa**; existe também a **avaliação preguiçosa**, quando a função é avaliada primeiro que os parâmetros [linguagem Haskell])
* Instrução para compilar gráficos: `ocamlfind ocamlopt -package graphics graphics.cmxa mandelbrot-ml -o mandel` (mais instruções no final de '_A first hour with OCaml_')

**Exemplos Práticos:**
* Cópia de ficheiros:
  * `let copy_file f1 f2 =`
    * `let c1 = open_in f1 in`
    * `let c2 = open_out f2 in`
    * `try while true do output_char c2 (input_char c1) done with End_of_file -> close_in c1; close_out c2`
  * `let () = copy_file Sys.argv.(1) Sys.argv.(2)`