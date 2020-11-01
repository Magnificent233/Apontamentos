# Multimédia

## Digitalização

Representação digital de dados (texto, som, imagem, vídeo)

**Processo de Digitalização**
* _Amostragem_ - transformação do contínuo ao discreto
* _Quantificação / Quantização_ - definição e atribuição de uma escala de medição
* _Codificação_ - correspondência entre um conjunto de pontos na escala de medição e o conjunto de valores de código (sequências binárias de tamanho uniforme)
  * a digitalização de texto limita-se a uma codificação
  
_Na imagem:_
* relação: número de amostras - qualidade - espaço ocupado e tempo de tratamento
* profundidade de quantificação - qualidade - espaço ocupado e tempo de tratamento
* a qualidade é influenciada pela frequência de amostragem e a profundidade da quantificação

_No som:_
* a imagem elétrica da onda sonora é partida em amostras segundo o eixo do tempo
* o número de amostras / segundo define a frequência de amostragem
	* 8 Khz (telefone numérico, frequência por defeito); 44.1 Khz (CD de música)
	* um CD tem uma codificação sobre 16 bits => 2¹⁶ níveis distintos de amplitude

<br/>

## Operações de Imagem

_Edição de Imagem_ - alteração de pixels numa imagem
* retoque, airbrushing, texturing, corte, cópia e colagem

_Operações Sobre Pontos_ - aplicação de uma função a cada pixel, produzindo um novo valor para este
* thresholding, correção de cor / brilho / contraste; atenuação de cor

_Transformações Geométricas:_ rotação; escala; inversão

_Operações de Filtragem:_ aplicação de uma função a cada pixel utilizando informação de pixels vizinhos
* blur, sharpen, distorção 

_Operações de Composição:_ composição de grupos de pixels de duas ou mais imagens

<br/>

## Operações de Áudio

_Edição de Áudio:_ cortar, copiar e colar segmentos de áudio diferentes

_Filtragem_ - redução de ruído; atrasos (adição de ecos ou reverberações); equalização (enfatizar, reduzir, alterar várias bandas de frequências); normalização (mantendo um pico máximo); compressão / expansão temporal; alteração de tom...

## Representação de Áudio

**Pulse Code Modulation** (PCM) - designação para as fases de amostragem e quantização

_Teorema de Nyquist:_ para uma amostragem correta, deve usar-se uma frequência de amostragem duas vezes igual à máxima frequência do sinal

**Algoritmos de Compressão de Som**

**Modulações Diferenciais** - reduzir o número de bits necessário à quantização de cada amostra codificando apenas a diferença de duas amostras sucessivas, e não cada amostra individual

*Modulação delta:* substituir o valor que define a amplitude de uma amostra por um único sinal (positivo ou negativo), representaando a variação do sinal em relação ao seu valor precedente de mais ou menos 1 incremento de quantização. Um único bit por amostra (1: diferença positiva; 0: diferença negativa). Provoca saturação de declive

*Differencial Pulse Code Modulation (DPCM):* codificar o sinal da variação e consagrar alguns bits suplementares à expressão da diferença entre o valor de uma amostra com o valor da amostra precedente. Não provoca saturação de declive

*Adaptative Differencial Pulse Code Modulation:* codificar a diferença entre duas amostras sucessivas, tomando em consideração a evolução do sinal sobre as amostras precedentes para prever o valor ótimo do passo de quantização a utilizar de modo a aumentar as capacidades de codificação do modulador e evitar a saturação do declive. Torna-se necessário guardar as variações dos passos de quantização numa tabela. Este método permite uma boa reprodução sonora

**Algoritmos Destrutivos: Codificação PsicoAcústica:** 

**Formatos de Ficheiros de Áudio Digital**