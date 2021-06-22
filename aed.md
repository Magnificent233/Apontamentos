# Algoritmos e Estruturas de Dados

##### Atualizado em 10-06-2021
###### A partir de: exemplos das aulas teóricas

## Estruturas Abstratas de Dados - Listas

**Listas com arrays:**

```
  ...  |   ...   | ...
100100 |    3    |  N
  ...  |   ...   | ...
100200 | 100400  |  L
  ...  |   ...   | ...
100300 |         |     
  ...  |   ...   | ...
100400 |    9    | L[0]
100404 |    3    | L[1]
100408 |    7    | L[2]
100412 |    4    | L[3]
  ...  |   ...   | ...
```

Código de implementação:
N = 0;
L = (int *) malloc (sizeof(int));
N = N++;
L[0] = 9;
N = N++;
L = (int *) realloc (L, N * sizeof(int));
L[1] = 3;
N = N++;
L = (int *) realloc (L, N * sizeof(int));
L[2] = 7;
N = N++;
L = (int *) realloc (L, N * sizeof(int));
L[3] = 4;

**Listas Ligadas Simples:**

```
  ...  |   ...   | ...
100500 |  100800 |  L
  ...  |   ...   | ...
100600 |    3    | p.valor
100604 |  100940 | p.proximo
  ...  |   ...   | ...
100800 |    9    | p.valor (ou L.valor se não houver p)
100804 |  100600 | p.proximo (ou L.proximo se não houver p)
100808 |         |
100812 |  100500 | p  (o valor de p atualiza a cada valor encontrado ao longo da lista)
100816 |         |
100820 |    4    | p.valor
100824 |   NULL  | p.proximo
  ...  |   ...   | ...
100940 |    7    |
100944 |  100820 | 
  ...  |   ...   | ...
```

**Listas Ligadas Duplas**

```
  ...  |   ...   | ...                         ...  |   ...   | ...
100100 |  100504 | tail                      200100 |         | 
  ...  |   ...   | ...                         ...  |   ...   | ...
100200 |  100400 | head                      200200 |    4    | 
  ...  |   ...   | ...                       200204 |  200504 |
100300 |         |                           200208 |  100400 | 
  ...  |   ...   | ...                         ...  |   ...   | ...
100400 |    3    | head -> elemento          200300 |         | 
100404 | 200200  | head -> proximo             ...  |   ...   | ...
100408 |   NULL  | head -> anterior          200400 |         | 
  ...  |   ...   | ...                         ...  |   ...   | ...
100500 |         |                           200500 |         | 
100504 |    9    | ...                       200504 |    7    |
100508 |   NULL  |                           200508 |  100504 | 
100512 |  200504 |                           200512 |  200200 |
100516 |         |                           200516 |         | 
  ...  |   ...   |  ...                        ...  |   ...   | ...
```

**Exercício:** usando pilhas e filas, verificar se um número inteiro não nulo é capicua.
_Teoria_
N = 21365
Pilha: 5 - 6 - 3 - 1 - 2 (topo)
Fila : (frente) 5 - 6 - 3 - 1 - 2 (cauda)
Capicua ? se topo = frente, então Pop(Pilha) e Remover(Fila); se topo != frente, então não é capicua. Quando Pilha e Fila ficarem vazias, então conclui-se que N é capicua.

_Código_
```C=
#include <stdio.h>
#include <stdlib.h>
#include "EADPilha.h"
#include "EADFila.h"

int main () {
  int numero, auxiliar, digito;
  PNodoPilha pilha;
  PNodoFila fila;
  printf("Introduza um valor inteiro maior que zero: ");
  scanf("%i", &numero);
  auxiliar = numero;
  pilha = CriarPilha ();
  fila = CriarFila ();
  while (auxiliar != 0) {
    digito = auxiliar % 10;
    pilha = Push (digito, pilha);
    fila = Juntar (digito, fila);
    auxiliar = auxiliar / 10;
  }
  while (PilhaVazia (pilha) == 0 && Topo (pilha) == Frente (fila)) {
    pilha = Pop (pilha);
    fila = Remover (fila);
  }
  if (PilhaVazia (pilha) == 1) {
    printf("%i é capicua.\n", numero);
  else {
    printf("%i não é capicua.\n", numero);
  }
  return 0;
}
```