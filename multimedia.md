# Multimédia

* Texto e imagem fixa são independentes do tempo; imagem animada, vídeo e som são dependentes do tempo e obrigam a uma sincronização temporal.

---

## Digitalização - Representação Digital de Dados

* Digitalizar uma informação significa representar essa informação usando representação binária.
* Som / Sinal acústico: variação da pressão do ar ao longo do tempo, definido por:
  * Frequência: número de vibrações por unidade de tempo, ou seja, definição física da altura e timbre do som (baixa frequência: som grave; alta frequência: som agudo);
  * Amplitude: valor máximo do desvio em relação ao ponto central do movimento vibratório, ou seja, definição da potência do som (baixa amplitude: som fraco; alta amplitude: som forte).
* Imagem: conjunto de pontos coloridos ou em níveis de cinzento (bitmap) ou conjunto de objetos predefinidos ou definidos pelas suas numerosas características (vetorial).
* Processo de digitalização:
  * _Amostragem:_ passagem de uma variação contínua para elementos descontínuos ou discretos em valores numéricos;
    * No som, a imagem elétrica da onda sonora é partida em amostras, definindo intervalos constantes cujo número condiciona a qualidade de restituição final;
    * Na imagem, separam-se os pixeis por unidade de largura.
  * _Quantificação:_ atribuição de um valor numérico a cada amostra e definir uma escala de medição;
    * No som, mede-se a amplitude do sinal;
    * Na imagem, mede-se a informação quantitativa associada a cada pixel;
    * Quanto mais pequeno é o passo de quantificação, menor é a distância entre duas graduações e mais precisa é a medição;
    * Erro de quantificação: quando o valor da amostragem se situa entre duas graduações e é aumentado ou diminuído de forma a corresponder ao valor de graduação mais próximo. Quanto maior é a profundidade da graduação, mais fino é o passo de quantificação e menor é o erro de quantificação.
  * _Codificação:_ estabeler uma correspondência entre um conjunto de partida (conjunto de pontos na escala de medição) e um conjunto de chegada composto de valores código (sequências binárias de tamanho uniforme).

---

## Representação de Áudio Digital

* _Pulse Code Modulation (PCM):_ fases de amostragem e quantização de áudio. O teorema de Nyquist determina a frequência de amostragem mínima de modo a poder reconstruir o som original.
* Algoritmos de Compressão de Som
  * Modulações Diferenciais - reduzir o número de bits necessário à quantização de cada amostra codificando apenas a diferença entre duas amostras sucessivas.
    * Modulação Delta: substituir o valor que define uma amplitude de uma amostra por um único sinal, positivo ou negativo, representando a variação do sinal em relação ao seu valor precedente;
    * _Differential Pulse Code Modulation (DPCM):_ codificar o sinal de variação e alguns bits suplementares à expressão da diferença entre o valor de uma amostra com o valor da amostra precedente;
    * _Adaptative Differential Pulse Code Modulation (ADPCM):_ codificar a diferença entre duas amostras sucessivas, tomando em consideração a evolução do sinal sobre as amostras precedentes.
  * Algoritmos Generalistas Não Destrutivos - procurar ocorrências múltiplas de uma mesma série de bytes, guardando-as num dicionário com os códigos mais curtos possíveis de modo a substituir no ficheiro comprimido as longas séries de bytes do ficheiro original, fazendo que, após a descompressão, o ficheiro original permaneça íntegro (sem perda de informação).
  * Algoritmos Destrutivos: Codificação PsicoAcústica - suprimir as modulações "inúteis" (não audíveis pelo ouvido humano), reduzindo o tamanho do ficheiro sem degradar a qualidade de reprodução;
    * A banda das frequências audíveis máxima e ótima é de 20 Hz a 20 kHz; o ouvido humano é mais sensível a frequências próximas de 3000 Hz e é inútil codificar sons fora do intervalo 500 Hz - 10 kHz;
    * Efeito de máscara: se, num grupo de frequências idênticas ou vizinhas, algumas têm amplitude muito superior às outras, apenas elas serão percebidas.
* MP3 - utiliza todas as técnicas descritas, começando com uma codificação RLC e terminando com o algoritmo de Huffman.

---

## Cor e Codificação da Cor

* Bastonetes são sensíveis à intensidade luminosa em toda a gama do comprimento de onda a que o olho humano é sensível, mas não detetam cor; cones são sensíveis a apenas alguns comprimentos de onda, permitindo a interpretação de cor. A cor que provoca maior sensação visual é o verde, a menos, o azul. O olho é mais sensível à luminância do que à crominância.
* Modelos de Cor
  * RGB - cada cor é obtida por síntese aditiva das três cores primárias (vermelho, verde, azul), dependente dos periféricos utilizados na aquisição e representação;
  * CMY - ciano, magenta, amarelo; fundado sobre a capacidade de absorção da luz pela tinta de impressão depositada no papel, a síntese das cores é subtrativa;
    * CMYK - a junção das três cores com saturações máximas não é suficiente para produzir a cor preta, pelo que se adiciona um quarto plano para a representar;
  * HSV - _hue_ (tom, dependente das variações de comprimento de onda), _saturation_ (saturação, diferença entre uma cor com um cinzento com o mesmo nível de brilho), _value_ (valor, intensidade luminosa);
    * Modelos CIE (_Comission Internationale de l'Eclairage_)
      * CIE XYZ - espaço de cor onde se inscrevem todas as cores do espetro visível; não uniforme;
      * CIE xyY - para caracterizar a luminância, uma cor é sempre definida pelas suas coordenadas x, y e Y;
      * CIE LAB - escala uniforme de cor para a luminosidade; o CIELUV é utilizado para calibrar motores, o CIELAB quantifica as cores segundo classificações de Munsell.
* Paletes de Cor - subconjunto das gamas disponíveis num sistema particular. A indexação de cor é a técnica que relaciona cada cor da imagem com uma cor da palete do sistema.
  * Palete Exata - quando a imagem de origem não utiliza mais do que 256 cores;
  * Palete Sistema - palete por defeito de um sistema operativo;
  * Palete Uniforme - tomada uniforme de amostras de cor no cubo RGB (5 tomas == 5^3 = 125 cores);
  * Palete Percetiva - palete que favorece as cores às quais o olho humano é mais sensível;
  * Palete Seletiva - palete percetiva que preserva as cores web e garante maior fidelidade de reprodução;
  * Palete Adaptativa - favorece os tons dominantes na imagem;
  * Palete Web - constituída por 216 cores para representar imagens sobre um monitor limitado a 256 cores.

---

## Imagem Digital

* Imagem Bitmap - o ficheiro é constituído pelos dados da cor de cada ponto (pixel, elemento mais pequeno), alinhados horizontal e verticalmente como linhas e colunas de uma matriz.
  * Resolução de uma imagem: número de pontos digitalizados, afixados ou imprimidos por unidade de largura.
  * Entrelaçamento: visualização progressiva; consiste em reordenar as linhas das imagens, organizando-as em grupos que vão sendo apresentados e aumentando a qualidade e o número de detalhes.
  * Vantagens:
    * Produção de graduações de nuances e cores muito finas;
    * Constituídas por pixeis, permitindo o tratamento ponto a ponto;
    * Diretamente guardadas na memória, logo representadas rapidamente no ecrã.
  * Desvantagens:
    * Qualidade dependente do material de aquisição e reprodução;
    * Grande espaço ocupado na memória.
  * Formatos:
    * Formato GIF (_Graphic Interchange Format_) - utiliza compressão sem perdas LZW, máximo 256 cores. A versão 87a aceita entrelaçamento e a versão 89a transparência e animação.
    * Formato JPEG (_Joint Photographic Experts Group_) - utiliza compressão com perdas, permite adaptar qualidade de imagem e 'true color', permite representação sequencial (linha a linha) ou progressiva (passagens sucessivas); aceita entrelaçamento progressivo, mas não transparência ou animação.
    * Formato PNG (_Portable Network Graphics_) - utiliza compressão sem perdas, permite entrelaçamento e transparência por canal _alpha_, formato livre.
    * Formato TIFF (_Tagged Image File Format_) - utiliza compressão LZW, preserva a qualidade da imagem original.
* Imagem Vetorial - o ficheiro contém a descrição matemática das figuras elementares que o constituem.
  * Vantagens: 
    * Imagens descritas textualmente, logo fáceis de alterar, manipular e transformar e eficazmente comprimidas;
    * Tamanho de memória independente do tamanho de imagem;
    * Independentes dos periféricos e resolução.
  * Desvantagens:
    * Tamanho e tempo de representação dependentes da complexidade da imagem;
    * Difícil descrição de uma imagem complexa;
    * Qualquer perda ou corrupção no ficheiro leva à perda da imagem na totalidade.
  * Formatos:
    * Formato SVG (_Scalable Vector Graphic_) - linguagem de descrição de gráficos vetoriais bidimensionais para a web.

---

## Codificação Fonte

* Compressão - reduzir ao máximo o volume de armazenamento e transferência, mantendo a capacidade de restituir a integridade dessa informação (compressão sem perdas).
  * Taxa de Compressão: relação entre o tamanho do ficheiro original e o tamanho do ficheiro comprimido;
  * (As)Simetria: velocidade e qualidade de restituição do documento original;
  * Com ou Sem Perdas: no primeiro caso, o algoritmo de compressão é irreversível, pois não é possível recuperar na íntegra o ficheiro original a partir do ficheiro comprimido; no segundo caso, é reversível.
* Incerteza vs Informação
  * Uma experiência fornece informação se e só se o seu resultado elimina uma certa incerteza;
  * A quantidade de informação e o nível de incerteza são diretamente proporcionais.
    * Entropia: fórmula matemática que permite calcular a quantidade média de informação de uma experiência tendo em conta o seu nível de incerteza, exprimindo o número médio de bits por símbolo necessários para a codificação ideal de um determinado alfabeto. Se a repartição é uniforme, a entropia é máxima (codificação de comprimento fixo).
* Técnicas de Base
  * _Run Length Coding (RLC)_ - recuperar as sequências repetitivas de carateres e substitui-las por um caractere de controlo seguido do número de repetições.
    * aaaaaa -> #Na, em que `#` indica o início de uma repetição, `N` indica o número de repetições e `a` indica a sequência repetida.
  * Codificação Relativa - codificação de longas séries de valores próximos.
    * Um caratere especial (`#`) indica o início da codificação; um número define em seguida o número de bits idênticos; depois escrevem-se esses bits; indica-se o número de bytes afetados por essa codificação; por fim, inserem-se os bits não repetidos desses bytes.
  * Algoritmos de Codificação Estatística
    * Método de Huffman - obriga à criação de tabelas de frequências que terão de ser transmitidas, para a descodificação.
      * Codificar com o menor número de bits os símbolos em que a frequência de ocorrência é maior.
      * Regra da prefixação: os primeiros elementos de uma palavra de código não podem constituir outra palavra de código, o que permite garantir uma descodificação instantânea.
      * Os códigos obtidos não são únicos, mas são ótimos, pois não existe outro código de prefixo cuja largura média seja inferior.
    * Método de Huffman Canónico - necessita de cabeçalho para a descodificação.
      * Códigos mais pequenos têm numericamente valores superiores do que códigos mais longos; dentro do mesmo comprimento, os valores numéricos aumentam com o alfabeto.
    * Método de Shannon-Fano - necessita da leitura do ficheiro para cálculo das frequências e de guardar as tabelas de código.
        * O método de Huffman agrupa probabilidades; o método de Shannon-Fano separa probabilidades.
    * Largura Média - número de bits necessário para codificar uma determinada fonte; somatório da multiplicação da largura do código de cada símbolo pela probabilidade desse símbolo.
  * Codificação Aritmética - o código para uma sequência de símbolos é um intervalo cujo comprimento diminui à medida que se acrescentam mais símbolos à sequência. O _output_ final é um único número que não consiste em códigos para símbolos individuais.
  * Algoritmos do Tipo Dicionário - não necessitam de conhecer a estatística dos dados a comprimir, não usam códigos de comprimento variável, utilizam sequências de símbolos de comprimento variável.
    * Algoritmo de (Des)Codificação LZW - a criação do dicionário e a compressão do ficheiro são realizadas à medida que o ficheiro é lido, sem necessitar de leitura prévia e o dicionário não é adicionado ao ficheiro comprimido (menor tempo e maior taxa de compressão).

---

## Representação de Imagem Digital

* Medidas de Distorção - MSE (_Mean Square Error_, erro médio quadrado); SNR (_Signal to Noise Ratio_); PSNR (_Peak Signal to Noise Ratio_).
* Sistema de Compressão
  * Transformada - representar os dados da imagem de modo a eliminar redundâncias estatísticas, normalmente invertível;
  * Quantização - reduzir o número de valores de amplitude possíveis para codificação, não invertível;
  * Codificação - explorar a não uniformidade da distribuição de probabilidade dos índices de quantização.