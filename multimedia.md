# Multimédia

## Digitalização

Representação digital de dados (texto, som, imagem, vídeo).

**Processo de Digitalização**
* _Amostragem_ - transformação do contínuo ao discreto;
* _Quantificação / Quantização_ - definição e atribuição de uma escala de medição;
* _Codificação_ - correspondência entre um conjunto de pontos na escala de medição e o conjunto de valores de código (sequências binárias de tamanho uniforme).

A digitalização de texto limita-se a uma codificação.
  
_Na imagem:_
* relação: número de amostras - qualidade - espaço ocupado e tempo de tratamento;
* profundidade de quantificação - qualidade - espaço ocupado e tempo de tratamento;
* a qualidade é influenciada pela frequência de amostragem e a profundidade da quantificação.

_No som:_
* a imagem elétrica da onda sonora é partida em amostras segundo o eixo do tempo.
* o número de amostras / segundo define a frequência de amostragem:
	* 8 Khz (telefone numérico, frequência por defeito); 44.1 Khz (CD de música);
	* um CD tem uma codificação sobre 16 bits => 2¹⁶ níveis distintos de amplitude.

## Operações Sobre Imagem e Áudio

**Operações de Imagem**

_Edição de Imagem_ - alteração de pixels numa imagem.
* retoque, airbrushing, texturing, corte, cópia e colagem.

_Operações Sobre Pontos_ - aplicação de uma função a cada pixel, produzindo um novo valor para este.
* thresholding, correção de cor / brilho / contraste; atenuação de cor.

_Transformações Geométricas:_ rotação; escala; inversão.

_Operações de Filtragem:_ aplicação de uma função a cada pixel utilizando informação de pixels vizinhos.
* blur, sharpen, distorção.

_Operações de Composição:_ composição de grupos de pixels de duas ou mais imagens.

**Operações de Áudio**

_Edição de Áudio:_ cortar, copiar e colar segmentos de áudio diferentes.

_Filtragem_ - redução de ruído; atrasos (adição de ecos ou reverberações); equalização (enfatizar, reduzir, alterar várias bandas de frequências); normalização (mantendo um pico máximo); compressão / expansão temporal; alteração de tom...

<br/>

## Representação de Áudio

**Pulse Code Modulation** (PCM) - designação para as fases de amostragem e quantização.

_Teorema de Nyquist:_ para uma amostragem correta, deve usar-se uma frequência de amostragem duas vezes igual à máxima frequência do sinal.

**Algoritmos de Compressão de Som**

**Modulações Diferenciais** - reduzir o número de bits necessário à quantização de cada amostra codificando apenas a diferença de duas amostras sucessivas, e não cada amostra individual.

*Modulação delta:* substituir o valor que define a amplitude de uma amostra por um único sinal (positivo ou negativo), representaando a variação do sinal em relação ao seu valor precedente de mais ou menos 1 incremento de quantização. Um único bit por amostra (1: diferença positiva; 0: diferença negativa). Provoca saturação de declive.

*Differencial Pulse Code Modulation (DPCM):* codificar o sinal da variação e consagrar alguns bits suplementares à expressão da diferença entre o valor de uma amostra com o valor da amostra precedente. Não provoca saturação de declive.

*Adaptative Differencial Pulse Code Modulation:* codificar a diferença entre duas amostras sucessivas, tomando em consideração a evolução do sinal sobre as amostras precedentes para prever o valor ótimo do passo de quantização a utilizar de modo a aumentar as capacidades de codificação do modulador e evitar a saturação do declive. Torna-se necessário guardar as variações dos passos de quantização numa tabela. Este método permite uma boa reprodução sonora.

**Algoritmos Destrutivos: Codificação PsicoAcústica:** como existe em todo o registo sonoro uma quantidade não negligenciável de sons que o auditor não pode perceber e ruídos que não se quer ouvir, pode-se suprimir as modulações 'inúteis' e reduzir o peso dos ficheiros sem afetar a qualidade de reprodução.

*Propriedades do Ouvido Humano:*
* suprime os sinais situados em frequências consideradas inúteis - não pertencentes ao intervalo 20Hz - 20KHz, as frequências do limite de perceção.
  * permite remover os sons abaixo de 100 Hz e acima de 10/11 KHz.
* efeito de máscara - incapacidade de distinguir um som 'coberto' por um som de frequência vizinha e amplitude superior.
  * permite remover as frequências mascaradas.
* o cérebro é capaz de interpretar minúsculas diferenças que distinguem os sinais percebidos pelo ouvido esquerdo e pelo ouvido direito, limitado a determinadas frequências: _joint stereo_.

**Formatos de Ficheiros de Áudio Digital**

_MPEG - layer 3 (MP3):_ Alemanha, 1996. Usa primeiro usa codificação RLC (evita a codificação de dados sucessivos idênticos) e termina na aplicação aos dados finais do algoritmo de Huffman. A compressão ótima é obtida a uma taxa de 7 : 1, a 192 Kbits/s.

<br/>

## Cor e Codificação da Cor

_Luz:_ onda eletromagnética com espetro visível entre os 400nm e os 700nm. A cor corresponde ao comprimento de onda da luz.

_Olho:_ possui cones e bastonetes que codificam os três canais primários (vermelho, verde, azul).

**Modelos de Cor**

*Modelo RGB (Red, Green, Blue)*
* três cores primárias (três canais de cor): vermelho, verde, azul.
* usado em ecrãs.
* permite formar 2²⁴ cores (16 777 216) => imagem _true color_.
* origem: ponto onde os três valores são 0 -> preto.
* vértice oposto: ponto onde os três valores são máximos -> branco.
* vértices do cubo equidistantes de duas cores primárias: encontram-se as cores secundárias (amarelo, magenta, ciano).
* depende dos periféricos usados na aquisição e representação.

*Modelo CMY (Cyan, Magenta, Yellow)*
* próprio dos objetos que refletem luz, obtido através da subtração de cores refletidas por uma superfície branca.
* ciano (verde, azul): opõe-se à passagem do vermelho.
* magenta (vermelho, azul): opõe-se à passagem do verde.
* amarelo (verde, vermelho): opõe-se à passagem da cor azul.
* origem: ponto onde os três valores são 0 -> branco.
* vértice oposto: ponto onde os três valores são máximos -> preto.

*Modelo CMYK (Cyan, Magenta, Yellow, blacK)* - devido à dificuldade em criar preto, adiciona-se um quarto canal (preto) ao modelo CMY.

*Modelo HSV (Hue, Saturation, Value)*
* _Hue:_ tom.
* _Saturation:_ saturação da cor; mais baixa => mais cinzenta; 0 => cinzenta.
* _Value:_ intensidade luminosa determinada pelo grau de refletividade da superfície física que recebe a luz; maior brilho => cor mais clara.

*Modelos CIE (*Comission Internationale de l'Eclairage**)* - descrevem a cor em termos de tom (_hue_), brilho (_value_) e saturação (_saturation_).
* CIE LUV - *standardização* da luminosidade; usado para calibrar monitores.
* CIE LAB - quantifica as cores segundo as classificações de Munsell; usado por vários _software_ de tratamento de imagem para conversão de espaços de cor, uma vez que é independente dos dispositivos.

*Modelo YCBCR (Iuma, Croma de diferença em azul (B) e vermelho (R))*

A _luminância_ é a soma das três componentes básicas (R, G, B) moduladas seguindo a sensibilidade da nossa perceção visual: Y = 0.2999R + 0.58G + 0.114B.

O _coeficiente de ponderação_ de cada cor é calculada por:
COEFF (cor X) = sensibilidade (cor X) / (sensibilidade (cor R) + sensibilidade (cor G) + sensibilidade (cor B)).

*Paletes de Cor* - subconjuntos das gamas disponíveis por um sistema particular. As cores da imagem original que não estão na palete de cores do sistema têm de ser aproximadas - _construção de tramas_, que consiste em criar pixels contíguos com a ajuda das diferentes cores disponíveis na palete para dar, por confusão, a impressão visual da cor de origem.
* _Palete exata:_ regista as cores originais exatas.
* _Palete sistema:_ palete por defeito de um sistema.
* _Palete uniforme:_ obtida por tomadas uniformes de amostras de cores no cubo RGB; o número total de cores é igual ao cubo do número de tomas
* _Palete web:_ seis tomas, ou seja, 6³ = 216 cores.
* _Palete percetiva:_ favorece as cores às quais o olho humano é mais sensível.
* _Palete seletiva:_ valoriza as zonas de cores mais importantes e preserva as cores web.
* _Palete adaptativa:_ favorece os tons dominantes da imagem.

*Imagens de Cor Indexada* - definem-se 256 cores, cada uma delas codificada sobre 8 bits por cor primária.

<br/>

## Imagem Bitmap VS Imagem Vetorial

**Imagem Bitmap** - todas as imagens reproduzidas num ecrã, obtidas através de um _scanner_ ou de um aparelho fotográfico numérico.
* Constituído pelos dados da cor de cada ponto, alinhados horizontal e verticalmente como linhas e colunas de uma matriz. O elemento mais pequeno da imagem é o _pixel_.
* Sabendo a altura e a largura (em pixels) e a profundidade de quantificação, pode calcular-se o tamanho de uma imagem bitmap não comprimida como $T(KB) = \frac{largura (pixel) * altura (pixel) * profundidade (bits/pixel)}{8 (bits/byte) * 1024 (bits/Kbyte)}$.
* A _resolução_, ppp, é o número de pontos digitalizados, afixados ou imprimidos por unidade de largura.
* Permitem uma visualização progressiva através da técnica de entrelaçamento - reordenar as linhas das imagens, organizando-as em vários grupos -, permitindo ao utilizador formar uma ideia da imagem após algumas das linhas serem transmitidas.
* Vantagens:
  * Capazes de produzir graduações de nuances e cores muito finas.
  * Constituídas por _pixels_, o que permite o tratamento ponto a ponto.
  * Guardadas diretamente na memória, logo são representadas com maior rapidez no ecrã.
* Desvantagens:
  * A qualidade está diretamente dependente do material de aquisição e reprodução.
  * O facto de serem imagens de pontos cujas características de cor são definidas individualmente exige uma grande quantidade de espaço em memória.

_GIF_ - utiliza compressão sem perdas LZW, com profundidade de pixel não superior a 8 bits. Otimizado para compressão de imagens com poucas cores diferentes e apresentando grandes quantidades de pixeis da mesma cor. Permite entrelaçamento em quatro passagens.

_PNG_ - utiliza compressão sem perdas, com codificações até 48 bpp e alto nível de compressão sem perdas. Permite transparência. De formato livre (sem algoritmos de domínio privado). Permite entrelaçamento em 7 passagens.

**Imagem Vetorial**
* Constituída por um conjunto de figuras elementares descrita por dados matemáticos, descreve as diferentes figuras como objetos gráficos independentes que podem ser manipulados e transformados de forma independente.
* Vantagens:
  * As informações são descritas textualmente, logo eficazmente comprimidas.
  * O tamanho da memória é independente do tamanho da imagem.
  * É possível aplicar facilmente e sem perda de precisão transformações geométricas (deslocamentos, translações, rotações, ...) a diferentes objetos independentes.
  * São independentes dos periféricos e da resolução, sendo colocadas automaticamente na escala de forma precisa.
* Desvantagens:
  * O tamanho do ficheiro varia de acordo com a complexidade da imagem.
  * Imagens complexas não podem ser descritas em formato vetorial.
  * O tempo de representação de uma imagem vetorial é superior em relação a uma imagem bitmap - aumenta com a complexidade da imagem.
  * Qualquer perda / corrupção no ficheiro leva à perda da totalidade da imagem.

<br/>

## Teoria da Codificação

**Codificação Fonte**

<br/>

## Representação de Imagem

<br/>

## Representação de Vídeo