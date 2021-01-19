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
    * Os componentes de baixa frequência (variações suaves) constituem a base de uma imagem e as altas frequências (_edges_) fornecem detalhe.
    * Pixeis numa imagem exibem um certo nível de correlação com os seus vizinhos, que podem ser exploradas para prever o seu valor, de modo a mapear os dados espaciais (correlacionados) em coeficientes transformados (não correlacionados);
    * DCT (_Discrete Cosine Transform_) - decomposição de uma função/sinal em componentes sinusoidais (ondas cosseno de diferentes tamanhos/formas, independentes), que quando adicionadas formam o sinal original;
      * Após a decorrelação em componentes DC (mais importantes, primeiro coeficiente da transformada, que corresponde ao valor médio da sequência tratada) e AC (menos importantes), cada coeficiente da transformada pode ser codificado independentemente sem perder a eficiência da compressão.
      * Propriedades:
        * Decorrelação - remoção da redundância entre pixeis vizinhos.
        * Compactação de Energia - capacidade de compactar dados de entrada no menor número de coeficientes possível.
        * Separabilidade - possibilidade de possibilitar o cálculo de `F(u,v)` em dois passos com uso sucessivo de operações 1D sobre as linhas e colunas de uma imagem.
        * Simetria - a matriz de transformação pode ser calculada previamente e depois aplicada à imagem, aumentando a eficiência da computação.
        * Ortogonalidade - a matriz da transformada é igual à matriz da inversa.
    * DWT (_Discrete Wavelet Transform_) - decomposição de uma imagem para separar as variações suaves dos detalhes, pelo uso de filtros de síntese _low-pass_ e _high-pass_.
  * Quantização - reduzir o número de valores de amplitude possíveis para codificação, não invertível;
    * Quantização Escalar - cada símbolo de _input_ é tratado separadamente na produção do _output_; se o _input_ for dividido em níveis iguais, é Quantizador Uniforme, se não, é Quantizador Não Uniforme. Função que mapeia cada elemento de um subconjunto de R a um valor particular desse subconjunto.
    * Quantização Vetorial - os símbolos de entrada são processados em grupos (vetores) para gerar o _output_.
  * Codificação - explorar a não uniformidade da distribuição de probabilidade dos índices de quantização;
    * Codificação Diferencial ou Preditiva: se amostras sucessivas estão próximas umas das outras, apenas se precisa de codificar a primeira amostra com um grande número de bits.
* Norma JPEG - método de compressão com perdas com codificação por transformada DCT.
  * Codificação Sequencial - cada componente é codificado numa única passagem da esquerda para a direita e de cima para baixo:
      * Transformação de Cor: passagem de imagens RGB para YIQ/YUV e fazer subamostragem dos planos de cor;
      * Transformação Espacial: execução da DCT em blocos da imagem;
      * Quantização: tabelas constituídas por valores inteiros que definem o passo de quantização, cujo crescimento é inverso à ordem de importância dos coeficientes DCT, que determinam a qualidade final da compressão;
      * Ordenação em Ziguezague e Codificação _Run-Length_;
      * Codificação Entrópica (Estatística): o valor DC é apenas codificado pela sua diferença pelo DC do bloco anterior (DPCM); os coeficientes AC são linearizados e lidos segundo uma sequência em ziguezague.
  * Codificação Progressiva - a imagem é codificada em várias passagens para aplicações em que o tempo de transmissão é longo:
    * Compressão semelhante à progressiva, mas em que primeiro são codificados os bits mais significativos de cada coeficiente, e nos passos seguintes se descodificam os outros.
  * Codificação Sem Perdas;
  * Codificação Hierárquica - a imagem é codificada com múltiplas resoluções para permitir o acesso a uma imagem sem descomprimir na sua resolução final.

---

## Representação de Vídeo Digital

* Vídeo Analógico - amostragem por linhas em modo progressivo ou entrelaçado, primeiro as linhas pares e depois as linhas ímpares. O número de frames por segundo (fps) e a resolução da imagem é determinada pelo _standard_ de distinção de imagem, serviços de sincronização e de posicionamento dos feixes de eletrões.
* Vídeo Digital - guardado quer em memória, quer em suportes digitais, possibilitando edição não linear, gravações sucessivas, fácil encriptação e tolerância a erros de transmissão.
* Compressão de Vídeo - tira-se proveito das redundâncias espaciais, psicosensoriais, estatísticas w temporais.
  * Compressão Temporal - exploração de semelhanças entre imagens sucessivas, identificando redundância no tempo, mesmo com alterações no espaço.
    * Compressão Temporal Unidirecional - diferença entre a imagem corrente e a imagem precedente. As que são codificadas apenas espacialmente são chamadas imagens _intra_ ou _key frame_, as obtidas por diferença são imagens _delta_, que podem ser submetidas a uma compressão espacial; descompressão espacial antes de juntar as diferenças à imagem precedente para obter a imagem corrente.
    * Compressão Temporal Bidirecional - diferença entre a imagem corrente e as imagens precedente e sequente, com compensação de movimento (não se calculam as diferenças de um bloco com o mesmo bloco da imagem anterior, mas com os blocos mais próximos).
  * Compressão Baseada nos Objetos de Vídeo (VOP) - envolve estimação do movimento, predição compensada em movimento seguida da codificação de texturas. Codificação baseada em conteúdos, onde a sequência de imagens de entrada pode ter uma forma e localização arbitrárias, estendida pela codificação da informação referente à forma e à transparência, que pode melhorar a eficiência da compressão.
* Norma MPEG - algoritmo de compressão híbrida e assimétrica (compressão mais complexa que descompressão): predição apenas aplicada para a compressão temporal, transformada DCT seguida da quantização dos coeficientes transformados assegura codificação espacial, codifição entrópica.
  * MPEG-1 
    * Define três tipos de imagem:
      * I (imagens _intra_ ou de referência) - comprimidas segundo um algoritmo JPEG, servem de referência para imagens P e B;
      * P (imagens preditas) - constituídas a partir da imagem I ou P precedente por vetores de movimento e cálculo de diferenças;
      * B (imagens bidirecionais) - constituídas a partir das imagens I ou P precedentes e seguintes.
    * No som, suprimem-se do sinal sonoro as redundâncias psicosensoriais (inaudíveis ou impercetíveis ao ouvido humano).
  * MPEG-2 - superior ao MPEG-1 pela qualidade superior de imagem e som.
    * Perfil Simples: dispõe apenas de imagens I e P;
    * Perfil Médio: esquema herdado de MPEG-1;
    * Perfil Escalável em SNR: receção sobre dois níveis graças à organização de duas tramas distintas de dados;
    * Perfil Escalável Espacialmente: idêntico ao anterior, com uma trama de dados suplementares;
    * Perfil Alto: dispõe de todas as técnicas dos perfis anteriores, com uma codificação 4:2:2.
  * MPEG-4 - permite a decomposição de uma cena em objetos (imagens fixas, objetos de vídeo ou áudio, texto, gráficos, sons, rostos), que permite que os vídeos possam ser compostos e manipulados com operações simples através de um descritor de objetos (identificaçao de todos os dados binários associados aos objetos). Adaptação dimensional permite otimizar a difusão do fluxo de dados em função do débito e/ou do sistema de representação que possui o utilizador final.
    * Objetos de Média: representação de unidades de conteúdo de áudio, vídeo e audiovisual, naturais ou sintetizados;
    * Objetos de Média Compostos: descrição da composição dos objetos na criação dos objetos que formam as cenas audiovisuais;
    * Descrição da Cena: definição das relações espácio-temporais entre os objetos;
    * Interação com a cena audiovisual gerada no recetor;
    * Identificação de propriedade intelectual.
      * Perfil Visual: cinco níveis de exigência para a codificação de dados naturais e quatro níveis para a codificação de dados sintetizados ou mistos;
      * Perfil Áudio: quatro níveis definidos pelo número de técnicas integradas e débito requerido;
      * Perfil Gráfico: três níveis de tratamento de elementos gráficos e textuais;
      * Perfil de Descrição da Cena: quatro níveis determinam os tipos de informação suscetíveis de serem integradas;
      * Perfil de Descrição de Objetos: nível único que descreve objetos, sincronização, informação sobre objetos, propriedade intelectual e proteção.
  * MPEG-7
    * Descritor (D) - definição sintática e semântica das características;
    * Esquema de Descrição (DS) - especificação da estrutura e relação entre os seus componentes;
    * Linguagem de Definição de Descrição (DDL) - regras sintáticas para exprimir e combinar descritores e esquemas de descrição.