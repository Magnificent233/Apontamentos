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

<br/>

## Operações de Imagem

_Edição de Imagem_ - alteração de pixels numa imagem.
* retoque, airbrushing, texturing, corte, cópia e colagem.

_Operações Sobre Pontos_ - aplicação de uma função a cada pixel, produzindo um novo valor para este.
* thresholding, correção de cor / brilho / contraste; atenuação de cor.

_Transformações Geométricas:_ rotação; escala; inversão.

_Operações de Filtragem:_ aplicação de uma função a cada pixel utilizando informação de pixels vizinhos.
* blur, sharpen, distorção.

_Operações de Composição:_ composição de grupos de pixels de duas ou mais imagens.

<br/>

## Operações de Áudio

_Edição de Áudio:_ cortar, copiar e colar segmentos de áudio diferentes.

_Filtragem_ - redução de ruído; atrasos (adição de ecos ou reverberações); equalização (enfatizar, reduzir, alterar várias bandas de frequências); normalização (mantendo um pico máximo); compressão / expansão temporal; alteração de tom...

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