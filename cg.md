# Computação Gráfica

##### Atualizado em 13-12-2021
###### A partir de: sebenta

## Aulas Teóricas

### Aula 01

**CRT (_Cathode Ray Tube_)** (diapositivo de exibição de vídeo)
* **Píxel** - conjunto (triângulo) de três pontos de fósforo, um para cada cor primária (vermelho, verde, azul);
* **Fósforo** - qualquer material que emita luz visível quando exposto a radiação;
* **_Dot Pitch_** - distância física entre dois fósforos vizinhos da mesma cor;
* **Resolução** - número de píxeis que representam uma imagem dispostos em linhas e colunas (matriz), determinando nível de detalhe e requisitos de armazenamento;
* **_Scan_ Progressivo** - o feixe de eletrões excita os fósforos (feixe ligado). Horizontalmente, o feixe reposiciona-se no lado esquerdo da tela (retorno horizontal com feixe desligado); verticalmente, quando o feixe chega ao final da última linha do ecrã e retorna para a primeira linha (retorno vertical);
* **_Frame_** - imagem formada pelo feixe de eletrões após o _scan_ completo da camada de fósforo do ecrã;
* **_Refresh rate_** - número de _frames_ por segundo geradas pelo ecrã, medido em Hertz (Hz).
* **_Flickering_** - quando o _refresh rate_ não é alto o suficiente.

**LCD (_Liquid Crystal Display_)** (diapositivo de exibição de vídeo) - tecnologia de transmissão, que funciona pela variação da quantidade de luz branca de intensidade fixa através de um filtro.

**Barramento** (_bus_) é a coleção de fios condutores num circuito impresso através da qual a informação é transmitida entre partes de um computador.

Um _frame buffer_ é uma parte grande e contígua da memória do computador (no mínimo, um bit de memória para cada píxel no _raster_ (plano de bits)). A imagem é construída no _frame buffer_ bit a bit.

Ficheiros de imagem podem ser: _raster_ (criados em programas baseados em píxeis e capturados por câmara ou _scanner_, que permitem a mistura de cor para suavizar a transição entre cores); ou vetoriais (baseados em fórmulas matemáticas de formas, que permitem desenhar as formas (objetos) com cores únicas).

Com **VGA** (_Video Graphics Array_, IBM, 1987), todo o processamento era realizado apenas pela CPU (_Central Processing Unit_) e o VGA era apenas utilizado como _frame buffer_. Com **GPU** (_Graphics Processing Unit_, nVidia, 1990):
* Primeira geração - **interpolação** (capacidade para calcular os píxeis a partir dos vértices de um triângulo e aplicar texturas);
* Segunda geração - transformação de vértices e cálculo de iluminação (por vértice);
* Terceira geração - programação ao nível dos vértices;
* Quarta geração - programação ao nível do píxel;
* Quinta geração - programação ao nível da criação de geometria.

---

### Aula 02

**Escalar** - quantidade.

**Ponto** - uma localização no espaço, definida por um k-tuplo com respeito a um sistema de coordenadas.

**Vetor** - segmento de linha direcionado entre pontos.

**Espaço Vetorial** - conjunto de vetores com multiplicações escalares e adições de vetores.

**Espaço Afim** - espaço vetorial com pontos, que permite multiplicações escalares, adições de vetores, adição de pontos e vetores. Um **espaço euclidiano** é um espaço afim que permite distâncias e vetores normais.

`Operações básicas de vetores e pontos: diapositivos 7 a 11`.

A câmara está colocada na origem do eixo, centrada na origem, e percorre usualmente o eixo dos `z`. Para visualizar um objeto, é necessário ter uma câmara e uma fonte luminosa que ilumine as faces. O vetor normal à face é calculado pelo produto vetorial. Com base na normal e na intensidade da luz, é possível calcular a intensidade de cor de cada píxel.

**Casco convexo** é um conjunto de pontos de combinação convexa entre eles; ou seja, é o menor objeto convexo que contém o conjunto dos pontos.

**Superfície Implícita** - conjunto zero de uma função. Implícitos podem representar sólidos, cuja superfície se chama fronteira (separa o interior do exterior do sólido). Superfícies quádricas e de bolha de Gauss são superfícies implícitas particulares.

**_Display Raster_** - grelha discreta de elementos em que as formas são desenhadas ao definir os elementos "certos" e o _frame buffer_ é digitalizado, uma linha de cada vez, para atualizar a imagem. Torna difícil desenhar linhas suaves, exibe apenas uma aproximação discreta de cada forma e requer a atualização de um _frame buffer_ inteiro. Terminologia:
* Píxel - elemento mais pequeno acessível numa imagem, retangular ou circular;
* Proporção de Aspeto - rácio entre dimensões físicas do píxel;
* Gama Dinâmica - rácio entre intensidades mínima e máxima de luz emitidas pelo píxel ativado;
* Resolução - número de linhas e colunas distinguíveis num diapositivo medidas em valores absolutos (`n x m`) ou relativos (`dpi`), retangular ou circular;
* Espaço do Ecrã - sistema cartesiano discreto em duas dimensões de coordenadas de píxeis do ecrã;
* Espaço do Objeto - sistema cartesiano discreto em três dimensões de coordenadas do domínio ou cena dos objetos.

**Rasterização** é o processo de conversão de geometria (coordenadas do ecrã, _float_) em píxeis (_int_)), em que _shading_ determina a cor para cada píxel preenchido no _frame buffer_.

**Taxonomia Primitiva do OpenGL**, a partir da qual outros objetos geométricos devem ser descritos:
* _Pontos_: `POINTS`;
* _Linhas_: `LINES`, `LINE_STRIP`, `LINE_LOOP`;
* _Triângulos_: `TRIANGLES`, `TRIANGLE_STRIP`, `TRIANGLE_FAN`;
* _Polígonos_: `QUADS`, `QUAD_STRIP`, `POLYGON`.

**Transformações Geométricas** permitem: operações de modelação de objetos em duas ou três dimensões, definindo um objeto no seu próprio sistema de coordenadas locais com possibilidade de multiplicação; operações de posicionamento de objetos em duas ou três dimensões; operações de visualização de objetos em duas ou três dimensões de diferentes pontos de vista:
* _Geometria Euclidiana_ - translação, rotação, reflexão;
* _Geometria Afim_ - escala (multiplicar cada componente de um objeto por um escalar, idêntico ou não), deformação;
* _Geometria Projetiva_ - projeção ortogonal, projeção de perspetiva.

**Translação** significa mover um ponto `(x, y)` para uma nova localização pela quantidade de movimento linear `(Δx, Δy)`. **Rotação** de um ponto `P = (x, y)` por um ângulo `θ` sobre a origem significa encontrar um ponto `Q = (x', y')` na mesma circunferência centrada na origem que contém `P`, com `θ = ∡POQ`.

**Coordenadas homogéneas** são necessárias para formular a translação, que não é possível definir em combinações lineares, em que um ponto único pode ser representado por muitos conjuntos de coordenadas homogéneas.

Um **grupo** é composto por um conjunto `C` e uma operação `o`, `(C, o)`, se:
* Axioma de fecho: `∀c_1, c_2 ∈ C, c_1 o c_2 ∈ C`;
* Axioma da identidade: `∃i ∈ C tal que c o i = i o c, ∀c ∈ C`;
* Axioma do elemento inverso: `∀c ∈ C, ∃c^-1 ∈ C tal que c o c^-1 = i = c^-1 o c`;
* Axioma da associatividade: `∀c_1, c_2, c_3 ∈ C, c_1 o (c_2 o c_3) = (c_1 o c_2) o c_3`.

A **geometria afim** é uma generalização da geometria euclidiana representada pelo grupo `Gl(n) = (A(n), o)`, em que `A(n)` é o conjunto de transformações afins (translação, rotação, escala, deformação) e `o` o operador de concatenação.

**Escala** significa multiplicar cada componente dos pontos de um objeto `(x, y)` por um escalar, idêntido ou não para cada componente. **Deformação** consiste em deformar linearmente um objeto no sentido do eixo do x ou do y.

**Composição de afinidades em duas dimensões** - o operador da composição é o produto da matriz; a ordem da composição importa, o produto da matriz não é comutativo, não se satisfaz o axioma da comutatividade.

---

### Aula 03

**Sistema de coordenadas global** é associado com o domínio contínuo da cena (ou aplicação), onde estão objetos geométricos e a geometria de cada objeto é definida. O subdomínio é a **janela de cena**, subdomínio retangular da cena cujo conteúdo é representado no ecrã. **Sistema de coordenadas de imagem** é associado à janela da cena onde a imagem raster é representada, com várias _viewports_ que se podem sobrepôr, num domínio discreto (píxel). O subdomínio é a **_viewport_**, parte da janela do ecrã onde a imagem é renderizada.

A mesma cena pode ser mapeada para diferentes _viewports_, pertencentes à mesma janela de cena ou não. Esta operação é feita automaticamente pelo sistema de gráficos e envolve três transformações geométricas: translação em coordenadas globais, escala e translação em coordenadas de imagem.

Gerar uma **vista de uma cena** requer uma cena (descrição geométrica), uma câmara ou observador e um plano de projeção. A localização _default_ da câmara está na origem orientada na direção negativa do eixo z. A projeção pode ser **ortogonal** (preserva paralelismo das linhas), **de perspetiva** (1, 2 ou 3 pontos) ou **oblíqua ortogonal**. Uma câmara clássica permite profundidade infinita do campo (tudo é focado); uma lente _Double Gauss_ modela a profundidade do campo e óticas não lineares; uma câmara de renderização foto-realista aplica o modelo físico do olho humano para renderizar imagens.

A matriz `MODELVIEW` é o produto da matriz de modelação (sistema de coordenadas da cena) e da matriz de visão (sistema de coordenadas de câmara), que altera o sistema de coordenadas da cena para o sistema de coordenadas da câmara. A matriz `PROJECTION` aplica a matriz de projeção para mapear coordenadas da câmara para as coordenadas do plano de projeção.

A `glm::ortho (left, right, bottom, top)` define o domínio em duas dimensões da cena em duas linhas verticais (`left` e `right`) e duas linhas horizontais (`bottom` e `top`), que definem a matriz de projeção ortogonal. Por defeito, o domínio da cena é `(-1, 1, -1, 1)`.

A `glViewport (x, y, width, height)` mapeia coordenadas de janela para coordenadas de ecrã, ou seja, define a _viewport_ na janela de cena, em que `(x, y)` representa o canto inferior esquerdo e `(width, height)` o seu tamanho. Por defeito, ocupa a totalidade do domínio da janela da cena.

A **projeção** depende da localização do observador e da localização e orientação do plano de projeção:
* Projeção de perspetiva - o observador está localizado a uma localização finita do objeto/cena, os raios visuais não são paralelos e convergem de 1, 2 ou 3 pontos para 1 ponto (centro de projeção, COP);
* Projeção paralela - o utilizador está no infinito e os raios visuais ou de projeção são paralelos:
    * Ortogonal - mais simples, raios visuais perpendiculares ao plano de projeção, que está usualmente alinhado com os eixos coordenados;
    * Axonométrica - se o plano de projeção interseta os eixos à mesma distância relativa da origem;
    * Isométrica - se o plano de projeção interseta os eixos XYZ à mesma distância da origem;
    * Oblíqua.

A **multiprojeção** em _viewports_ distintos é conseguida pelo reposicionamento da câmara ou do objeto/cena.

Para especificar um `glm::frustum (xmin, xmax, ymin, ymax, zmin, zmax)`, todos os pontos pertencentes à linha definida pelo centro de projeção e `(xmin, ymin, -zmin)` são mapeados no canto inferior esquerdo da janela; todos os pontos pertencentes à linha definida pelo centro de projeção e `(xmax, ymax, -zmax)` são mapeados no canto superior direito da janela; `zmin` e `zman` são distâncias positivas sobre o eixo dos z; a direção da visão é pararela ao eixo dos z; um `frustum` não simétrico origina obliquidade na projeção.

---

### Aula 04

O `glm::perspective(fov, aspect, near, far)` apenas permite _frusta_ simétrica, com o centro de projeção na origem e vista na direção do eixo dos `z`, ângulo `fov ∈ [0, 180]` (radianos), o `aspect` permite a um `frustum` com o mesmo rácio de aspeto como o _viewport_ para evitar distorção de imagem.

Tanto `glm::frustum` como `glm::perspective` têm direção de projeção fixa, pelo que a posição e orientação arbitrárias da câmara podem ser alteradas pela manipulação da matriz `MODELVIEW` antes da geração da objetos da cena (por `glm::translate(x, y, z)`, `glm::rotate(theta, x, y, z)`, `glm::rotate(phi, x, y, z)` ou `glm::lookAt(eyex, eyey, eyez, lookx, looky, lookz, upx, upy, upz)` (equivalentes)).

**Transformação janela-_viewport_**: a matriz de projeção define uma transformação do sistema de coordenadas do domínio da cena em três dimensões para um sistema de coordenadas de janela de duas dimensões pertencente ao plano de projeção. A projeção de uma cena em três dimensões obriga à renderização em duas dimensões, tornando-se necessário mapear pontos da janela para píxeis de _viewport_ para determinar o píxel associado a cada vertex dos objetos da cena. Cada ponto `(x_p, y_p)` da projeção é transformado em `(x_n, y_n)` do dispositivo normalizado de output. O _pipeline_ gráfico mapeia coordenadas normalizadas em duas dimensões para um ou mais _viewports_, redefinindo-se depois o tamanho da janela.

---

### Aula 05

`GLSL`

---

`Fim de matéria para frequência 1.`

---

### Aula 06

A **visão** é a perceção da energia eletromagnética. O olho humano é uma câmara biológica dinâmica que possui lente e distância focal (equivalente a uma película), que deve focar diretamente na retina para uma visão perfeita. Possui células sensíveis à luz que a convertem em impulsos eletroquímicos: **cones** (capacidade de reconhecer cores (RGB)) e **bastonetes** (capacidade de reconhecer a luminosidade).

As sensações visuais causadas pela luz **cromática** são mais ricas que as causadas pela luz **acromática**. A perceção de cor envolve **tom** (definição da cor), **saturação** (puricidade da cor) e **luminosidade** (quantidade de luz). Duas cores especificadas em sistemas diferentes só serão as mesmas se são reproduzidas com uma calibração cuidadosa dos ecrãs e se são vistas em condições idênticas. O **diagrama CIE** define as três cores primárias que permitem obter qualquer cor através da adição de quantidades positivas desses primários.

Modelos de cor:
* **RGB** - cor natural como combinação aditiva de três canais (_Red_, _Green_, _Blue_); zonas claras denotam elevadas concentrações de tinta ou pigmentação, ao passo que zonas escuras denotam baixas concentrações de tinta;
    * Cor indexada - submodelo RGB em que as cores de cada imagem são armazenadas numa paleta;
* **CMYK** - cor como combinação  subtrativa (cores obtidas pela redução do efeito de outras) de quatro canais (_Cyan_, _Magenta_, _Yellow_, _Black_ (ausência de cor)), baseada na reflexão e absorção de partes do espetro luminoso; zonas em branco indicam inexistência de tinta ou pigmentação, zonas escuras indicam concentrações de tinta;
* **HSB** - cor definida por três valores distintos (_Hue_ (tom), _Saturation_ (vivacidade da cor), _Brightness_ (brilho da cor)), baseada na perceção humana da cor;
* **HLS** - cor definida por três valores distintos (_Hue_ (tom), _Lightness_ (luminosidade), _Saturation_ (saturação));
* **YIQ**;
* **YCbCr**.

**Meios tons**:
* ***Dithering***: píxeis adjacentes de cores diferentes são usados para simular cores e sombras que não existem na paleta de cores da imagem. Utilizado quando uma imagem _true color_ é reduzida a uma imagem indexada para compensar a perda de cor;
* **Padrões**;
* **Modulação**.

---

### Aula 07

**Modelo de iluminação** é uma aproximação da iluminação do mundo real. O modelo de Phong dá uma boa aproximação ao mundo real e é eficiente em termos de consumo de tempo. Modelos podem ser:
* Independentes da luz:
    * _Shading_ em profundidade: a cor (ou a sua intensidade) é apenas determinada pela profundidade do triângulo, evitando computações complexas de modelos dependentes de luz;
    * _Cueing_ em profundidade: reduzir a intensidade do píxel com a distância do observador, ou seja, a imagem desvanece com a distância;
* Dependentes da luz - a visualização do objeto depende das propriedades da fonte de luz, dos materiais do objeto e da localização do observador:
    * Iluminação direta (local): interação simples entre luz e objetos;
    * Iluminação indireta (global): interações múltiplas entre luz e objetos.

A **luz ambiente** (sensação da cor principal do ambiente) vem e espalha-se em todas as direções quando o raio de luz atinge a superfície, sem depender da localização do observador. A **luz difusa** (aproximação da cor do objeto) vem de uma única direção e espalha-se igualmente em todas as direções quando o raio de luz atinge a superfície, sem depender da localização do observador. A **luz especular** (aproximação da luz unidirecional) vem de uma direção e tende a refletir numa direção quando o raio de luz atinge a superfície, dependendo da localização do observador.

Uma **fonte de luz** pode emitir diferentes quantidades de luz para cada localização, direção e comprimento de onda. **Fontes de luz de ponto** têm uma localização e são omnidirecionais; usualmente resultam em imagens de alto constraste, não consegue criar sombras parciais. **Fontes de luz direcionais** são semelhantes a luz de ponto, mas sem atenuação baseada na distância e diferença de direção; a direção é importante para computar a luz refletida. **Fontes _spotlight_** são direcionais, com a luz emitida numa gama de ângulos.

O modelo de reflexão de luz, `R(θ, φ, γ, ψ, λ)`, é a quantidade de energia incidente na superfície do objeto vinda da direção `(θ, φ)` refletida na direção `(γ, ψ)` com o comprimento de luz `(λ)`.

Na **reflexão ambiente**, um objeto tem um coeficiente de refletividade `K_A` e uma fonte de luz liberta uma quantidade de luz ambiente `I_A`. A luz ambiente refletida representa a luz ambiente refletida pelos objetos do cenário.

Na **reflexão difusa**, um efletor difuso ideal a nível microscópico é uma superfície muito áspera, em que o raio de luz incidente é refletido igualmente em todas as direções sobre o hemisfério definido à superfície. A luz refletida depende do ângulo `θ` do raio incidente: quanto maior, menor a quantidade de luz refletida - que depende da posição da fonte de luz e da localização do objeto.

Na **reflexão especular** acrescentam-se destaques na direção da reflexão; quanto mais liso e brilhante o objeto, mais rigoroso e brilhante será o destaque. A **reflexão emissiva** é produzida por uma fonte de luz de superfície e representa a luz emitida diretamente por um polígono ou disco, que é uniforme (e.g., lâmpada).

---

### Aula 08

**Iluminação direta** (ou local) é uma interação simples entre luz e objetos, num processo em tempo real suportado pelo `OpenGL`. **Iluminação indireta** (ou global) é múltiplas interações entre luz e objetos, em tempo real para cenas pequenas.

O _shading_ é de três tipos em renderização poligonal:
* **_Shading_ constante** (por polígono) - computa a cor num único ponto de cada polígono e usa-a em todos os seus píxeis. É um processo rápido (uma sombra por polígono), usa uma normal por polígono; mas é impreciso, tem descontinuidades nas fronteiras dos polígonos e falta de realismo;
* **_Shading_ de Gouraud** (por vertex) - ilumina ou sombreia diretamente cada vertex usando a sua posição e vetor normal, interpolando linearmente a cor em cada face: primeiro ao longo das arestas, depois por linhas internas. Permite cálculos incrementais durante a rasterização e que um vetor normal seja usado para cada vertex partilhado para obter continuidade entre faces; os polígonos parecem irregulares e monótonos e tende a eliminar a componente especular da luz (problema: **distorção de perspetiva**, **bandas _mash_**);
* **_Shading_ de Phong** (por píxel) - interpola linearmente a normal em qualquer face, aplicando a iluminação de Phong a cada píxel. Computa as equações de iluminação em píxel, permite o uso do componente especular, torna difícil distinguir polígonos; mantém bandas _mash_, silhuetas poligonais, vértices partilhados versus não partilhados, distorção de perspetiva, interpolação depende da orientação dos polígonos.

**Distorção de perspetiva** complica interpolação linear (a interpolação do espaço de ecrã não está alinhada com a do espaço do domínio da cena). A relação entre a distância no espaço de ecrã e distância de espaço de visão não é linear, logo, a relação entre a interpolação de ambos os espaços é não linear e a interpolação linear de espaço de ecrã de cores resulta em valores incorretos.

**Bandas _mash_** descrevem o aumento de contraste de cores adjacentes causadas pela interação de neurónios retinais vizinhos. Atuam como um filtro, acentuando descontinuidades da primeira derivada (causada pela interpolação linear). O _shading_ de Gourard sugere interpolação de alta ordem para aliviar as bandas _mash_ - o que se traduz num maior custo de _performance_.

---

### Aula 09

**Textura** é uma imagem com componentes RGBA (*Red Green Blue Alpha*). Objetos renderizados pelo modelo de reflexão de Phong e pelo sombreamento interpolado de Gouraud ou Phong podem aparecer plastificados e a levitar, pelo que os efeitos de textura adicionam maior realismo à superfície visível.
* **Mapeamento de texturas** é um método para criar complexidade numa imagem sem necessitar de criar modelos geométricos grandes, utilizando um padrão que é colocado na superfície de um objeto. Explicitam-se as coordenadas paramétricas dos vértices dos polígonos e interpolam-se dentro do triângulo na conversão para espaço de ecrã;
* **Mapeamento de luz** combina textura e luminosidade por um processo de modulação. Cria-se uma parede como um único polígono, aplica-se iluminação por vertex e mapeamento de texturas e aplica-se o mapeamento da luz à parede na segunda passagem de renderização;
* **Mapeamento de *bump*** distorce uma superfície lisa para obter uma superfície variável. A superfície mantém-se, mas a verdadeira normal é alterada para dar a ilusão de covas e rugas;
* **Mapeamento de ambiente** usa textura para representar cor refletida, produzindo reflexões em objetos brilhantes. A textura é transferida na direção do raio refletor do ambiente para o objeto.

Para adicionar detalhes, a solução óbvia é partir a cena em polígonos cada vez menores para aumentar o detalhe, o que é muito difícil de modelar e gasta muito tempo do renderizador. A solução preferível é então pintar uma imagem de duas dimensões em objetos.

Para mapear texturas para polígonos, define-se explicitamente as coordenadas `(u, v)` dos vértices do polígono. A interpolação da textura é feita durante a rasterização, mas em vez de se obter valores RGB, obtêm-se coordenadas que apontam para elementos do mapa de textura (no espaço de ecrã canónico). Cada píxel é associado a uma pequena região da superfície e a uma pequena área de textura: um texel para um píxel, **magnificação** (um texel para vários píxeis), **minificação** (vários téxeis para um píxel; *foreshortening* é uma técnica utilizada em perspetiva para criar a ilusão de um objeto a recuar para a distância).

**Funções de mistura** modificam atributos do polígono ou da superfície depois do valor de uma textura ser obtido: `GL_REPLACE` (substitui cor da superfície por cor da textura); `GL_DECAL` (substitui cor da superfície por cor da textura, misturando-a com um valor alfa de textura subjacente); `GL_MODULATE` (multiplica a cor da superfície pela cor da textura); `GL_BLEND` (similar à modulação, adiciona *alpha* de mistura).

---

### Aula 10

*Shaders* são pequenos programas que executam em paralelo na GPU, que processa múltiplas unidades de processamento, e que podem substituir as funcionalidades "fixas" do OpenGL por código gerado por utilizador. Os *shaders* do OpenGL dão controlo ao utilizador sobre cada vertex e fragmento (píxel) interpolado entre vértices. Após o processamento dos vértices, os polígonos são **rasterizados** e valores como posição, cor, profundidade, entre outros, são interpolados através do polígono e passados a cada fragmento.

Ao instalar um *shader*, todas as funcionalidades fixas são anuladas e devem ser substituídas: transformar cada vertex em coordenadas de vista manualmente, iluminar cada vertex manualmente e aplicar a cor interpolada atual para cada fragmento manualmente.

---
---

### Aula Teórico-Prática de Introdução a C++

**Variável** - nome/identificador que representa um valor armazenado em memória.

**Variável Ponteiro** - nome/identificador que representa um endereço de memória armazenado em memória.

**Variável de Referência** - variável ponteiro que serve também como _alias_ para a variável a apontar, podendo ser usada como uma variável normal e devendo ser inicializada na declaração.

**Função**:
* _Protótipo_ - permite verificação de erros pelo compilador, assegurando conversão de todos os argumentos passados à função quando esta é chamada. É o _cabeçalho_ seguido de `;`, em que os nomes dos argumentos não são necessários;
* _Cabeçalho_ - define o que faz a função, pode conter parâmetros formais;
* _Corpo_ - descreve como a função faz o que é pedido.

`std::cout` <=> `printf` ;; `std::cin` <=> `scanf`

A chamada de **funções por referência** usa-se para funções que "retornem" mais que um valor, em que o valor formal se torna um _alias_ para o parâmetro real; esta pode alterar os valores dos parâmetros reais. Um parâmetro de referência é um _ponteiro constante_, referências são _desreferenciadas automaticamente_. Chamar por referência faz-se com o modificador `const`.

A **sobreposição de funções** é possível em C++ se as funções tiverem o mesmo nome mas parâmetros diferentes (quer em número, quer em tipo).

Uma **estrutura** é um tipo de dados composto com elementos de diversos tipos, que exige a declaração de todos os membros e dos seus tipos individuais, sendo depois declaradas como variáveis de qualquer outro tipo. Cada elemento é acedido por `.` (variáveis e referências) ou por `->` (ponteiros). Também é possível criar funções que operam sobre os dados da estrutura, cujo protótipo aparece dentro da definição da estrutura, mas cuja implementação é feita fora da estrutura num ficheiro `.cpp` com `tipo estrutura::função () { ... }`.

As especificações de acesso costumam ser `public` (acessível a todas as funções) ou `private` (apenas podem ser acedidas por funções-membro).

**Classes** e **estruturas** apenas diferem porque, por _default_, estruturas têm todos os seus membros públicos e classes têm todos os seus membros privados. Uma classe pode ter objetos de outras classes como membros.

Um **construtor** é uma função que inicializa uma instância (ou objeto) da classe, possuindo o mesmo nome da classe e sem tipo de retorno. É chamado automaticamente quando uma nova instância da classe é criada e, se não for especificado, é criado por defeito pelo compilador. É possível ter vários construtores na mesma classe (desde que com parâmetros diferentes).

Um **destrutor** que destrói um objeto, chamado automaticamente quando a função termina, o programa termina, um bloco de variáveis temporais termina ou um operador `delete` é chamado. Tem o mesmo nome que a classe precedido por um `~`, sem argumentos e tipos de retorno.

Um **construtor de cópia** é uma função-membro que inicializa um objeto usando outro objeto da mesma classe (definido pelo programador ou por _default_ pelo compilador).