# Algoritmos e Estruturas de Dados

## Estruturas Abstratas de Dados - Listas

**Listas com arrays:**

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

**Listas ligadas:**

100500 | 100800  |  L
  ...  |   ...   | ...
100600 |    3    | p.valor
100604 | 100940  | p.proximo
  ...  |   ...   | ...
100800 |    9    | p.valor (ou L.valor se não houver p)
100804 | 100600  | p.proximo (ou L.proximo se não houver p)
100808 |         |
100812 | 100500  | p  (o valor de p atualiza a cada valor encontrado ao longo da lista)
100816 |         |
100820 |    4    | p.valor
100824 |  NULL   | p.proximo
  ...  |   ...   | ...
100940 |    7    |
100944 | 100820  | 
  ...  |   ...   | ...