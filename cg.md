# Computação Gráfica

##### Atualizado em 28-09-2021
###### A partir de: sebenta

## Aulas Teóricas

### Aula 1

**CRT (_Cathode Ray Tube_)**
* **Píxel** - conjunto (triângulo) de três pontos de fósforo, um para cada cor primária (vermelho, verde, azul).
* **Fósforo** - qualquer material que emita luz visível quando exposto a radiação.
* **_Dot Pitch_** - distância física entre dois fósforos vizinhos da mesma cor.
* **Resolução** - número de píxeis que representam uma imagem dispostos em linhas e colunas (matriz), determinando nível de detalhe e requisitos de armazenamento.
* **_Scan_ Progressivo** - o feixe de eletrões excita os fósforos (feixe ligado). Horizontalmente, o feixe reposiciona-se no lado esquerdo da tela (retorno horizontal com feixe desligado); verticalmente, quando o feixe chega ao final da última linha do ecrã e retorna para a primeira linha (retorno vertical).
* **_Frame_** - imagem formada pelo feixe de eletrões após o _scan_ completo da camada de fósforo do ecrã.
* **_Refresh rate_** - _frames_ por segundo geradas pelo ecrã, medido em Hertz (Hz).
* **Flickering** - quando o _refresh rate_ não é alto o suficiente.

**LCD (_Liquid Crystal Display_)**

**Barramento** (_bus_) é a coleção de fios condutores num circuito impresso através da qual a informação é transmitida entre partes de um computador.

Um _frame buffer_ é uma parte grande e contígua à memória do computador (no mínimo, um bit de memória para cada píxel no _raster_ (plano de bits)). A imagem é construída no _frame buffer_ bit a bit.

Ficheiros de imagem podem ser: _raster_ (criados em programas baseados em píxeis e capturados por câmara ou _scanner_, que permitem a mistura de cor para suavizar a transição entre cores); ou vetoriais (baseados em fórmulas matemáticas de fórmulas, que permitem desenhar as formas (objetos) com cores únicas).

**Interpolação** - capacidade para calcular os píxeis a partir dos vértices de um triângulo e aplicar texturas.

---