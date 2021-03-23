# Sistemas Operativos

## Aula Teórica 1

Um computador moderno é constituído por um CPU (_Central Processing Unit_), memória (principal [RAM (_Random Access Memory_), volátil], secundária [discos, persistente]) e periféricos (dispositivos de entrada / saída [ecrã, impressora, rato...]). Respeita o modelo de Von-Neumann e é gerido por uma camada de _software_: sistema operativo. 

Um **sistema operativo** é um programa intermediário entre o utilizador e o _hardware_, que gere e reserva recrursos da máquina, permitindo que múltiplos programas (de vários utilizadores) utilizem a máquina ao mesmo tempo (_multiplexing_, partilha de recursos em tempo e espaço). Controla a execução de programas dos utilizadores e de operações dos periféricos para evitar erros e utilização indevida. O _kernel_ (núcleo) é o único programa que está sempre pronto a correr (todos os outros são aplicações ou programas de sistema).

Um sistema de computação tem um ou mais CPUs ligados através de uma ligação comum (_bus_) a uma memória comum (RAM) e é composto por:
* _Hardware_: recursos físicos (CPU, memória, periféricos);
* Sistema operativo: controla e coordena a utilização do _hardware_;
* Programas: aplicações (definem formas de utilização dos recursos do sistemas para resolver problemas do utilizador [compiladores, SGBD's, jogos,...]), utilitários (conjunto de programas de sistema que têm funcionalidades muito úteis [gestor de ficheiros, instaladores]);
* Utilizadores: pessoas, máquinas, outros computadores, serviços de web.

Um sistema operativo liberta o utilizador da complexidade do _hardware_, tornando os humanos (utilizadores, programadores) mais eficazes e produtivos. Enquanto máquina virtual (_top-down view_), permite transformar um conjunto diversificado de _hardware_ numa máquina simples de utilizar, virtualizar o _hardware_ de modo a apresentar uma abstração simples e de fácil compreensão, apresentar uma interface que trata de modo uniforme operações sobre entidades semelhantes e garantir fiabilidade e segurança. Enquanto gestor de recursos (_bottom-up view_), permite obter o máximo rendimento do _hardware_, garantir uma gestão de recursos e otimizar o desempenho.

A partição de memória em sistemas batch enquadra-se em dois modelos:
* Sistema monoprogramado - em que se combinam dois ou mais canais de informação num meio de comunicação comum (um sistema operativo e uma área de utilizador);
* Sistema multiprogramado - em que vários _jobs_ são mantidos em memória principal, simultaneamente, e a CPU é multiplexada entre eles com partilha espacial (um sistema operativo e várias tarefas na área de utilizador).

Para a multiprogramação, um sistema operativo deve possuir:
* Gestão de memória - para alocar e gerir memória para vários _jobs_;
* Escalonamento da CPU - escolher entre os vários _jobs_ prontos para correr;
* Rotinas de I/O fornecidas pelo sistema - bibliotecas de código, interface comum de acesso (chamadas ao sistema);
* Reserva e gestão de dispositivos - periféricos.

Na computação interativa (sistemas por partilha de tempo):
* o sistema online tem de estar disponível para acesso a dados e código. Quando o sistema operativo termina a execução de um comando, procura a próxima 'instrução de controlo' introduzida por um utilizador via teclado;
* o sistema _batch_ tem de executar programas de utilizadores offline.
  * Problema: memória insuficiente para todos os _jobs_. A CPU é atribuída a um _job_ só se ele estiver em memória e é multiplexada entre os vários _jobs_ em memória e no disco. Dificuldade na gestão de privacidade dos dados dos utilizadores.

Em sistemas multiprocessador / core:
* _Symmetric Multiprocessing_ (SMP): cada processador corre a única instância do sistema operativo, que escalona trabalho a qualquer dos processadores;
* _Assymetric Multiprocessing_ (AMP): o processador-mestre corre o sistema operativo e escalona trabalho aos processadores-escravos, que correm as aplicações.

Sistemas de Tempo Real - sistema com necessiades temporais onde os resultados têm de ser produzidos dentro de um tempo específico (prazo, _deadline_);
* Sistemas Embebidos - dispositivo de computação embutido num sistema maior (aviões, automóveis, satélites..., com múltiplos _inputs_ e _outputs_ físicos);
* Sistemas Críticos - com efeitos catastróficos em caso de falha (controlo de comportas, central nuclear, sistema médico);
* istemas de Tempo Real Duro - garantem que as tarefas são executadas dentro das _deadlines_;
* Sistemas de Tempo Real Suave - tarefas de tempo real têm prioridade sobre tarefas normais.

---

## Aula Teórica 2

**BIOS** é a sigla para *Basic Input/Output System*, o primeiro programa executado pelo computador ao ser ligado, cuja função é preparar a máquina para que o sistema operativo possa ser carregado para memória e executado. O BIOS é _firmware_ (_software_ armazenado sob a forma de memória de leitura não volátil).

Um programa ***bootstrap*** é carregado durante _power up_ ou _reboot_ do BIOS, inicializando o _hardware_ para um estado "conhecido". O BIOS transfere controlo para o programa _bootstrap_, que inicializa todas as partes necessárias do sistema para carregar o _kernel_ do sistema operativo e inicializar a sua execução.

Os controladores de _input_/_output_ e a CPU podem executar de forma concorrente: cada controlador está encarregue de um dispositivo particular, com um _buffer_ local, e a CPU movimenta dados de e para a memória principal para e a partir de _buffers_ locais. Um controlador informa a CPU de que terminou a sua operação com uma **interrupção**, que transfere o controlo de uma rotina de serviço através do _interrupt vector_, que contém os endereços de todas as rotinas. As interrupções são desativadas enquanto outra interrupção está a ser processada de forma a evitar a sua perda; uma interrupção gerada por _software_ devido a erro ou pedido do utilizador é chamada por ***trap***. A maior parte das CPU tem duas linhas de interrupção:
* **Linha de interrupção não mascarável**, reservada para eventos como erros de memória irrecuperáveis;
* **Linha de interrupção mascarável**, que pode ser desligada pela CPU antes da execução de uma sequência de instruções críticas que não podem ser interrompidas.

Durante _input_/_output_, as interrupções são feitas por vários dispositivos quando estão prontos para serviço, que significam o fim da saída de dados, a disponibilidade da entrada de dados ou a deteção de uma falha. O controlador interrompe a CPU, que a deteta e despacha para o _interrupt handler_, rotina que determina a causa da interrupção, executa o processamento necessário e termina, fazendo a CPU regressar ao estado anterior à interrupção.

Qualquer transferência é um _output_ de um dispositivo e um _input_ para outro. O controlador tem um ou mais registos para dados (registos _data-in_, _data-out_) e sinais de controlo (registos _status_, _control_). A interação entre a CPU e um controlador faz-se por **aperto de mão** (_handshaking_), utilizando dois bits (_busy_ bit do registo _status_ e _ready_ bit do registo _command_):
* A CPU lê repetidamente o bit _busy_ até que seja 0 (_busy-wait cicle_), ativa o bit _write_ a 1 no registo _command_ e escreve um byte no registo _data-out_. A CPU ativa o bit _ready_ a 1 no registo _command_ e, quando o controlador nota que o bit _ready_ está a 1, escreve o bit _busy_ a 1;
* O controlador lê o registo _command_ e vê o comando _write_, lendo o registo _data-out_ para obter o byte e fazer o _input_/_output_ para o dispositivo; desativa o bit _ready_ a 0, assim como o bit _error_ no registo _status_, para indicar que a transferência foi bem sucedida, colocando depois o bit _busy_ a 9 para indicar que a transferência terminou.

O **método síncrono** faz que, após o início de uma operação de _input_/_output_, o controlo só retorne ao programa do utilizador após essa operação através de uma instrução _wait_. Desvantagens: no máximo um pedido de _input_/_output_ é atendido de cada vez; não existe processamento de _input_/_output_ simultâneo; contenção para acesso à memória (ciclo _wait_). O **método assíncrono** faz que, após o início de uma operação de _input_/_output_, o controlo retorne ao programa do utilizador sem esperar pela terminação da operação de _input_/_output_. Vantagens: permite operações de _input_/_output_ concorrentes e processamento simultâneo. Desvantagens: implementação mais complexa.

A **interface de _input_/_output_ do _kernel_** é um conjunto de operações de _input_/_output_ independentes de _hardware_, e os ***device drivers*** são módulos do _kernel_ dependentes do _hardware_, cada um encapsulando o funcionamento específico de cada dispositivo. Vantagem: facilidade na implementação de novos periféricos. Os relógios e temporizadores (_clocks_, _timers_) permitem determinar tempo corrente / decorrido e ativar um temporizador para despoletar uma operação numa dada altura Os dispositivos de _input_/_output_ caracterizam-se por:
* _Character-stream_ / _block_ - transferência de bytes um a um (dispositivo de carateres [teclado, rato, com interface básica _get_, _put_]) ou em bloco (dispositivo de blocos [disco rígido, com interface básica _read_, _write_, _seek_; dispositivo de rede, com _sockets_]);
* Sequenciais / Acesso Aleatório;
* Síncronos / Assíncronos - transferência de dados com tempos de resposta previsíveis ou não;
* Partilháveis / Dedicados - se há partilha concorrente de processos ou não;
* Velocidade de operação;
* _Read-Write_ / _Read-Only_ / _Write-Only_.

Um DMA (***Direct Memory Access***) permite que certos dispositivos de _hardware_ de alta velocidade num computador acedam a memória do sistema para efetuar operações de _input_/_output_ independentemente da CPU. O controlador transfere blocos de dados do _buffer_ diretamente para a memória principal sem intervenção da CPU, com uma interrupção gerada por bloco (e não por byte), permitindo execução simultânea de CPU e operações de _input_/_output_. A transferência de dados pode ser feita por pedido síncrono do _software_ ou impulso assíncrono do _hardware_ para o sistema.

Armazenamento:
* **Memória Principal:** só acedida pela CPU;
* **Memória Secundária:** extensão da memória principal com grande capacidade de armazenamento não-volátil;
* **Discos Magnéticos:** pratos de vidro ou metal rígido revestidos de material magnético de gravação com pistas (_tracks_) divididas em setores (_sectors_);
* ***Caching*:** cópia de informação num sistema de armazenamento utilizando memória de alta velocidade para guardar dados recentemente acedidos.

A partilha de recursos do sistema requer que o sistema operativo assegure que um programa incorreto não faça com que outros programas funcionem incorretamente. A proteção de _hardware_ é assegurada por:
* **Operação em _dual-mode_:** diferencia pelo menos dois modos de operação, _user-mode_ (desencadeada pelo utilizador) e _monitor-mode_/_kernel-mode_/_system-mode_/_bit-mode_ (desencadeada pelo sistema operativo), em que quando uma interrupção ocorre, o _hardware_ comuta para o _monitor-mode_;
* **Proteção de _input_/_output_:** todas as instruções de _input_/_output_ são instruções privilegiadas, assegurando que um programa do utilizador não consegue controlar o computador em _monitor-mode_;
* **Proteção de memória:** adiciona dois registos que determinam a gama de endereços a que um programa pode aceder (**registo de base**, endereço mais baixo da memória física; **registo limite**, tamanho da gama), em que as instruções de carregamento dos registos de base e de limite são instruções privilegiadas;
* **Proteção da CPU:** o temporizador interrompe o computador após um período de tempo especificado, assegurando que o sistema operativo possa manter controlo e implementar _time-sharing_ e em que _load-timer_ é uma instrução privilegiada.

*Pergunta 1.* b, c, g

*Pergunta 2.* a, e, f, g

*Pergunta 3.* aumentar a segurança pela diferenciação de tipos de modo de utilizador

---

## Aula Teórica 3

**Modelo de compilação**
* Pré-processador (`.i`) - `cc -E main.c -o main.i`, `cc -E sub.c -o sub.i`
* Compilador (`.s`) - `cc -Wall -ansi -S *.i`
* Assembler (`.o`) - `cc -c *.s`
* _Linkagem_ (`.out`) - `cc -o exemplo main.o sub.o -lm`
  * Estática (código embutido)
  * Dinâmica (endereço do código)
    * *Modelo de _Run-Time_: programa executável > chamada ao sistema > início > realocação de código > execução do programa
* Programa binário executável

O _scope_ de uma variável define as secções de código onde a variável está válida. Símbolos são entidades lexicais que nomeiam funções, variáveis e constantes, cada um com um valor (endereço de memória). O código consiste de definições e referências de símbolos, que podem ser locais ou externas (globais). Cada ficheiro-objeto executável tem uma tabela de símbolos. Os símbolos podem ser **fortes** (procedimentos e variáveis globais inicializadas) ou **fracos** (variáveis globais não inicializadas), seguindo as seguintes regras:
* um símbolo forte só pode aparecer uma vez;
* Um símbolo fraco pode ser sobreposto por um símbolo forte com o mesmo nome;
* Se há vários símbolos fracos, o _linker_ pode escolher um aleatoriamente.

Um _linker_ funde ficheiros objetos num único ficheiro objeto executável, realocando símbolos das suas posições relativas nos ficheiros `.o` para posições 'absolutas' no executável. _Linkers_ são **modularidáveis** (o programa pode ser escrito numa coleção de ficheiros-fonte mais pequenos, permitindo construir bibliotecas de funções comuns) e **eficientes** (não necessita de recompilar todos os ficheiros após alterações; permite utilizar apenas os programas que contenham o código desejado).

O formato **ELF** (_Executable and Linkable Format_) é um formato binário padrão para ficheiros-objeto. É constituído por _elf header_ (número mágico, tipo, máquina, ordenação de bytes), _program header table_ (tamanho de página, segmentos de endereços virtuais de memória, tamanho de segmentos), _.text section_ (código), _.data section_ (dados estáticos inicializados), _.bss section_ (dados estáticos não inicializados), _.symtab section_ (tabela de símbolos, nomes de variáveis estáticas e procedimentos, nomes e localizações de secções), _.rel.text section_ (informação realocada da secção _.text_, endereços de instruções a alterar no executável, instruções a executar), _.rel.data section_ (realocação da secção _.data_, endereços de apontadores de dados que precisam de ser modificados no executável), _.debug section_ (informação para _debugging_).

As **bibliotecas estáticas** (ficheiros de arquivo `.a`) concatenam arquivos de objetos relocáveis relacionados num único ficheiro com um índice (arquivo), melhorando o _linker_ de modo a que este procure referências externas não resolvidas ao observar os símbolos de um ou mais arquivos e as ligue a ficheiros executáveis. O _archiver_ permite atualizações pontuais, como recompilar uma função modificada ou substituir ficheiros `.o` num arquivo. O algoritmo do _linker_ para encontrar referências externas é:
* Examinar ficheiros `.o` e `.a` na linha de comandos, mantendo uma lista de referências não resolvidas;
* A cada novo `.o` ou `.a` encontrado, tentar resolver as referências;
* Se alguma entrada na lista continuar não resolvida, mostrar erro.
Isto implica ordem específica de ficheiros e colocação de bibliotecas no final da linha de comandos. Tal pontenciona a duplicação de código comum nos ficheiros executáveis e na memória, e que a reparação de pequenos _bugs_ requira que cada aplicação seja explicitamente relincada.

As **bibliotecas partilhadas** (_Dynamic Link Libraries_, DLL) permitem que a _linkagem_ dinâmica ocorra antes ou durante a execução do ficheiro e sejam partilhadas por processos múltiplos.

---

## Aula Teórica 4



---

## Aula Prática 1

**Bash Shell** (_Born Again Shell_), **SH Bourne Shell** (_Bourne Shell_), **CSH**, **TCSK** são CLI (_Command Line Interpretor_) do sistema operativo Linux.
GUI (_Graphical User Interface_).

LOOP:
* leitura de comandos (ambiente gráfico -> cliques) (CLI -> instruções escritas)
* interpretação
  * parsing
  * ação
    * execução de novos comandos que o sistema operativo pode encontrar
    * funcionalidade do próprio programa _shell_ (embutida)

EDITORES
* linha a linha : `ed`
* screen based : `vi emacs`
* complex screen based : `vim xemacs`
* graphics : `gedit` `notepad` `notepad++`
* ides: `netbeans` `intellij` `vscode` `vspro`

Tudo em Linux é um ficheiro (ficheiros 'normais', pastas, _sockets_, discos, periféricos).

`man`
página 1 -> bash
página 2 -> linux sys calls
página 3 -> c standard library

## Aula Prática 3

ctrl + z -> suspender

fg -> voltar a excecutar último comando / script

0 -> sucesso

`grep` -> procupar expressões regulares, que podem ser especificadas
* ^ -> início de uma linha
* $ -> fim de uma linha