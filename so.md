# Sistemas Operativos

## Aula Teórica 1

Um computador moderno é constituído por um CPU (_Central Processing Unit_), memória (principal [RAM (_Random Access Memory_), volátil], secundária [discos, persistente]) e periféricos (dispositivos de entrada / saída [ecrã, impressora, rato...]). Respeita o modelo de Von-Neumann e é gerido por uma camada de _software_: sistema operativo. 

Um **sistema operativo** é um programa intermediário entre o utilizador e o _hardware_, que gere e reserva recursos da máquina, permitindo que múltiplos programas (de vários utilizadores) utilizem a máquina ao mesmo tempo (_multiplexing_, partilha de recursos em tempo e espaço). Controla a execução de programas dos utilizadores e de operações dos periféricos para evitar erros e utilização indevida. O _kernel_ (núcleo) é o único programa que está sempre pronto a correr (todos os outros são aplicações ou programas de sistema).

Um sistema de computação tem um ou mais CPUs ligados através de uma ligação comum (_bus_) a uma memória comum (RAM) e é composto por:
* _Hardware_: recursos físicos (CPU, memória, periféricos);
* Sistema operativo: controla e coordena a utilização do _hardware_;
* Programas: aplicações (definem formas de utilização dos recursos dos sistemas para resolver problemas do utilizador [compiladores, SGBD's, jogos,...]), utilitários (conjunto de programas de sistema que têm funcionalidades muito úteis [gestor de ficheiros, instaladores]);
* Utilizadores: pessoas, máquinas, outros computadores, serviços de web.

Um sistema operativo liberta o utilizador da complexidade do _hardware_, tornando os humanos (utilizadores, programadores) mais eficazes e produtivos. Enquanto máquina virtual (_top-down view_), permite transformar um conjunto diversificado de _hardware_ numa máquina simples de utilizar, virtualizar o _hardware_ de modo a apresentar uma abstração simples e de fácil compreensão, apresentar uma interface que trata de modo uniforme operações sobre entidades semelhantes e garantir fiabilidade e segurança. Enquanto gestor de recursos (_bottom-up view_), permite obter o máximo rendimento do _hardware_, garantir uma gestão de recursos e otimizar o desempenho.

A partição de memória em sistemas _batch_ enquadra-se em dois modelos:
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

Sistemas de Tempo Real - sistema com necessidades temporais onde os resultados têm de ser produzidos dentro de um tempo específico (prazo, _deadline_);
* Sistemas Embebidos - dispositivo de computação embutido num sistema maior (aviões, automóveis, satélites..., com múltiplos _inputs_ e _outputs_ físicos);
* Sistemas Críticos - com efeitos catastróficos em caso de falha (controlo de comportas, central nuclear, sistema médico);
* Sistemas Estritos de Tempo Real - garantem que as tarefas são executadas dentro das _deadlines_;
* Sistemas Latos de Tempo Real - tarefas de tempo real têm prioridade sobre tarefas normais.

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

*Pergunta 1.* b, c, g (b, c, d, g)

*Pergunta 2.* a, e, f, g (e, g, h)

*Pergunta 3.* aumentar a segurança pela diferenciação de tipos de modo de utilizador (read,write, combinação entre os dois ;; executar código de algo em group mode)

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

Um **processo** é um programa em execução sequencial que inclui secção de texto, contador de programa, registos do processador, pilha (_stack_) com variáveis locais, funções, endereços de retorno, e secção de dados com variáveis globais. Esta noção permite que vários utilizadores a usar várias cópias do mesmo programa em simultâneo. Um processo é representado por um **bloco de controlo do processo** (_PCB-process control block_), que é a representação do conceito pelo SO e contém um identificador único (valor inteiro chamado _process ID_). Cada processo tem informação associada:
* **Estado do processo** - diagramas de estados;
* **Contador do programa (PC)** - endereço da próxima instrução a ser executada;
* **Registos da CPU** - acumuladores, registos de indexação, ponteiros de pilha, registos gerais, ...;
* **Informação de escalonamento da CPU** - prioridade do processo, ponteiros para filas de escalonamento, ...;
* **Informação de gestão de memória** - valores dos registos de base e de limite, tabelas de paginação / segmentação;
* **Informação de inventário** - CPU gasto, memória usada;
* **Informação de estado de I/O** - lista de dispositivos I/O afetados, lista de ficheiros abertos, ....

Para maximizar a utilização da CPU deve haver sempre um processo a correr (em execução) e, num dado instante, só um processo pode usar um dispositivo de I/O. Isto obriga a troca entre os processos em execução (comutação do contexto), separação por estádios (filas de processos) e escolha dos processos nas filas e transições (escalonamento). A **comutação do contexto** define a partilha do processor através de um mecanismo de comutação de processos através da salvaguarda do estado do processo que perde a CPU e a restauração do estado do processo que ganha a CPU; se for demasiado frequente, pode ter um custo _overhead_ para o sistema. O sistema operativo executa muitos processos em simultâneo, com o CPU multiplexado entre eles, fornecendo também mecanismos de manipulação e comunicação (_InterProcess Communication_ (IPC)).

Um _dispatcher_ é um procedimento que atribui o processador de um processo para outro e previne que um processo ocupe todo o tempo do CPU. Num modelo de dois estados, o programa é _dispatched_ e pausado em ciclo, até terminar.

Num modelo de cinco estados, o processo é criado (_new_), as instruções são executadas (_running_), o processo espera que algum evento ocorra (_waiting_) ou que lhe seja atribuído o processador (_ready_), até terminar a execução (_terminated_). Só um processo pode estar no estado _running_, mas vários podem estar nos estados _ready_ e _waiting_.

No escalonamento de processos, um novo processo é colocado na _ready queue_, onde fica em espera até ser selecionado e despachado para a CPU. Durante a sua execução, o processo pode emitir um pedido I/O e ser colocado numa _I/O device queue_; ser removido da CPU por interrupção do _timer_ e transitar de novo para a _ready queue_; criar um novo subprocesso, ficando à espera que ele termine; esperar por um _interrupt_ qualquer e pela sua reinicialização. A _ready queue_ contém os PCBs dos processos residentes na memória em estado _ready_ (prontos e à espera de executar); as _waiting queues_ contém processos em espera da conclusão de I/O ou outro dispositivo. Qualquer recurso pode ter associada uma fila de escalonamento, e existe migração de processos entre as várias filas.

Um processo migra entre várias filas de escalonamento durante o seu tempo de vida, e o sistema operativo deve selecionar processos destas filas com base nalgum método ou algoritmo com três tipos de escalonadores:
* **Escalonador de curto prazo:** seleciona os processos que devem ser executados de seguida e reserva a CPU necessária, sendo invocado com alta frequência;
* **Escalonador de médio prazo:** aloca memória para os processos, sendo invocado apenas quando necessário. Remove processos da memória, que podem ser reintroduzidos e continuarão a sua execução do ponto onde tinham sido deixados, permitindo uma mistura de processos - _swapping_;
* **Escalonador de longo prazo:** seleciona os processos que devem ser levados para a fila _ready_ e controla o grau de multiprogramação, sendo invocado com pouca frequência.

O **processo progenitor** (pai) cria **processos progénito** (filho), que por sua vez criam outros processos, formando uma árvore de processos. Processos pai e filho podem executar concorrentemente ou o processo pai pode esperar que os processos filho sejam concluídos. O processo filho duplica o espaço do processo pai e carrega um novo programa. Os recursos podem ser partilhados na totalidade entre processos pai e filho, ou os processos filho podem partilhar um subconjunto dos recursos do processo pai, ou não há partilha de recursos. A chamada à função `fork()` cria um novo processo, e a chamada seguinte ao sistema `exec()` depois de um `fork()` é usada para substituir o espaço de memória do processo com um novo programa.

O controlo de processos é feito por _signals_ ao sistema operativo com `CTRL + C` (matar processo ativo), `CTRL + Z` (suspender processo ativo) e `CTRL + ALT + DEL` (interrupção de sistema). 

Quando um processo é executado, o _shell_ original é posto em _background_ e o novo processo é posto no _foreground_. Quando um processo está em _background_ quer dizer que está pronto (_waiting_) para executar ou até mesmo em execução na memória, mas não é possível interagir com ele. Um processo pode ser terminado por:
* **Terminação normal:** quando acaba a execução da sua última instrução e pede ao sistema operativo que o elimine com a função `exit ()`. O processo devolve (`return`) eventualmente dados ao progenitor (via a chamada ao sistema `wait`) e recursos do processo pai são libertados pelo sistema operativo;
* **Terminação abrupta:** quando o processo pai termina a execução dos processos filho através de uma chamada ao sistema (`abort`). O processo filho excedeu os recursos reservados ou a sua tarefa não é mais necessária, ou o processo pai está a terminar, o que obriga os processos filho a terminar também.

Na cooperação entre processos, estes podem classificar-se como:
* **Independentes:** não podem afetar nem ser afetados pela execução de outros processos;
* **Cooperantes:** podem afetar ou ser afetados pela execução de outros processos, permitindo partilha de informação, aceleração da computação, modularidade e utilidade, embora seja mais complexo e exija sincronização, por IPC:
  * **Memória partilhada** - uma área de memória é partilhada pelos processos que querem comunicar, com a comunicação sob o controlo dos processos do utilizador e não do sistema operativo, sendo necessário fornecer e usar um mecanismo que permita aos processos sincronizar as suas ações no acesso a essa memória;
  * **Passagem de mensagem** - os processos comunicam entre si sem recorrer a variáveis partilhadas, mas através de mensagens de tamanho fixo ou variável enviadas por `send (message)` e recebidas por `receive (message)`.

Métodos de comunicação entre processos (IPC):
* **_Pipes_** (não síncronos) - conduta que permite a comunicação entre dois processos, unidirecionais, apenas acessíveis pelo processo que os criou e requerendo relações pai-filho;
* **_Named Pipes_** (não síncronos) - mais poderosos que _pipes_ ordinários, com comunicação bidirecional e sem necessidade de relações pai-filho;
* _Message Queues (síncronos);
* _Shared Memory Segments_ (não síncronos);
* _Sockets_ - _pipes full duplex_ de rede;
* _Remote Procedure Calls_ (RPC);
* _Remote Method Invocation_ (Java RMI).

O problema produtor-consumidor é um paradigma para processos de cooperação: o processo produtor produz informação que é consumida por um processo consumidor, com _unbounded-buffer_ se não tiver limite de tamanho, ou _bounded-buffer_ se tiver limite de tamanho.

---

## Aula Teórica 5

O processo filho criado pela chamada ao sistema `fork()` duplica o espaço de memória do processo pai, executando depois em concorrência, quando o `fork()` devolve valores diferentes para os diferentes processos, podendo o programa tomar várias linhas de ação através de uma instrução de controlo _if_. O processo pai pode esperar a terminação do processo filho usando a chamada `wait()`. A função `fork()` cria um novo processo (processo filho) que é uma cópia exata do processo inicial (processo pai), exceto que: o ID no processo filho é único e diferente do do processo pai, o processo filho tem a sua própria cópia dos descritores do processo pai, os recursos utilizados pelo processo filho são inicializados a 0. O processo filho (ou pai) pode carregar um novo programa usando a chamada ao sistema `exec()`, que necessita do nome de um novo programa - o texto e variáveis do programa velho são substituídos pelo novo, que herda também o identificador do processo (PID) e outras informações.

Um processo pai pode terminar-se com uma chamada a `exit()`, sendo depois os processos filho herdados pelo processo `init`. Processos pai podem esperar pela terminação dos processos filho pela chamada `wait()`, que retorna ao processo pai caso o processo filho já tenha terminado, ou bloqueia o processo pai caso contrário. `exit()` termina o processo de chamada: todos os ficheiros são fechados, o _output_ do _buffer_ é escrito e são chamadas funções `exit` registadas. `_exit()` termina a execução sem fechar quaisquer ficheiros, esvaziar o _output_ ou chamar qualquer função `exit`.

O escalonamento do processor tem por principal objetivo maximizar o uso da CPU através de multiprogramação (remoção da CPU de um processo para a atribuir a outro). Um **ciclo _burst CPU - I/O_** é a execução de um processo com execução na CPU e espera no I/O. O sucesso do escalonamento da CPU depende de vários ciclos CPU-I/O tal que uma intermitência (_burst_) de execução da CPU alterna com uma intermitência (_burst_) de espera pela finalização de uma operação I/O. Os processos _I/O-bound_ têm grande número de _CPU bursts_ de curta duração, e os processos _CPU-bound_ têm pequeno número de _CPU-bursts_ de longa duração. Quando a CPU fica livre, cabe ao sistema operativo selecionar um dos processos da _ready queue_ para executar, através do escalonador de curto prazo quando um processo comuta de _running_ para _waiting_, _ready_ ou _terminated_ ou de _waiting_ para _ready_.

No **escalonamento não preentivo**, o processo ocupa a CPU até ao seu término ou até que passe para o estado _waiting_, sendo depois selecionado um novo processo da _ready queue_, sem garantir a execução em primeiro lugar dos processos com prioridade mais alta (adequado para sistemas de tempo real). No **escalonamento preentivo**, usa-se um mecanismo de interrupção que suspende o processo em execução e invoca um cronograma para determinar qual processo é executado em seguida (o que pode causar problemas de inconsistência de dados).

Um despachador (_dispatcher_) é o módulo que despacha o controlo da CPU para o processo selecionado pelo escalonador de curto prazo, fazendo comutação de contexto, comutação para o modo de utilizador e salto para o endereço certo de memória de forma a (re)executá-lo. O tempo que decorre entre a paragem de execução de um processo e o início de outro é designado por _latência de despacho_.

Os algoritmos de escalonamento são comparados por, usando uma média entre todos:
* **Utilização da CPU:** uso da CPU (maximização);
* **Débito (_throughput_):** número de processos concluídos por unidade de tempo (maximização);
* **Tempo de circulação (_turnaround_):** tempo que decorre entre o instante em que um processo é submetido e o instante em que é concluído (minimização);
* **Tempo de espera:** soma dos períodos dispendidos na _ready queue_ (minimização);
* **Tempo de resposta:** tempo que decorre entre a submissão de um pedido e o início da resposta (sistemas interativos, minimização).

Algoritmos de escalonamento (Tempo Médio de Espera, TME; Tempo Médio de _Turnaround_, TMT):
* **_First Come, First Served_ (FCFS)** - processos selecionados (servidos) pela ordem de chegada à _queue_ (com _convoy effect_, processo curto antes de processo longo). O tempo médio de espera pode ser bastante elevado dependendo da duração e frequência dos _bursts_; não é preemtivo (logo inadequado para sistemas interativos ou de tempo real, mas adequado para sistemas _batch_);
* **_Shortest Job First_ (SJB)** - a cada processo associa-se o tempo do seu próximo _CPU burst_, selecionando o processo com o _CPU burst_ mais pequeno (o desempate faz-se com FCFS). É um algoritmo ótimo (porque minimiza o tempo médio de espera de um dado conjunto de processos), embora seja problemático determinar qual é o valor do próximo _CPU burst_ de um processo (fórmula: aula 5.16). Pode ser:
  * Não preemtivo - ao ser atribuída CPU a um processo, este não pode ser preemcionado até completar o seu _CPU burst_;
  * Preemtivo - se um novo processo chega à _ready queue_ com um _CPU burst_ menor que o tempo restante do processo em execução, então há preemção (_Shortest Remaining Time First (SRTF));
* **Prioridade** - caso geral do SJB, em que a cada processo é atribuída uma prioridade e o escalonador atribui a CPU ao processo com maior prioridade (menor inteiro, cujo desempate se faz com FCFS). Processos de baixa prioridade arriscam-se a nunca ser executados (_starvation_), o que é solucionado por _aging_ (à medida que o tempo passa, a prioridade de um processo aumenta). A prioridade é atribuída de acordo com: limites de tempo, requisitos de memória, número de ficheiros abertos, duração média dos _bursts_ de I/O e de CPU (fatores internos), importância, preço pago pelo uso, proprietário (fatores externos);
* **_Round Robin_** - concebido para sistemas de _time sharing_ e semelhante ao FCFS (mas preemtivo), atribui a cada processo uma pequena unidade de tempo na CPU (_time quantum_ ou _time slice_), ao final do qual o processo é preemcionado e adicionado à cauda da _ready queue_ (tratada como uma fila circular). Se há `n` processos na _ready queue_ e o _time quantum_ é `q`, cada processo obtém `1/n` do tempo da CPU em fatias de `q` unidades de tempo de uma vez, sem que nenhum processo espere mais do que `(n - 1) * q` unidades de tempo. Se `q` é grande, aplica-se FIFO, se não, a sobrecarga é muito elevada;
* **Multifila** - usado quando os processos podem ser classificados em classes distintas e particionados em várias filas dependendo do processo (_foreground_, sistemas interativos (RR), e _background_, sistemas _batch_ (FCFS)));
* **Multifila com Transbordo** - permite prioridades por fila, preemção, generalidade e configurabilidade, e também a movimentação de processos entre várias filas.

A avaliação de algoritmos é feita por **modelação e simulação**: definir um _workload_/_trace_ e depois simular o desempenho de cada algoritmo, podendo ser **determinístico** (definir um _workload_ baseado em dados reais ou inventados) ou **aleatório** (utilizar processos aleatórios e probabilísticos).

Num escalonamento multiprocessador, é usada uma única _ready queue_ para evitar que haja processadores inativos enquanto outros têm processos à espera. Há duas políticas de escalonamento multiprocessador: **processadores autoescalonáveis** (cada processador é responsável pela seleção de um processo existente na _ready queue_ partilhada) e **processador meste - processadores escravo**, em que um processador (mestre) desempenha o papel de escalonador dos restantes (escravos).

---

## Aula Teórica 6

**Sistemas de Tempo Real** têm o tempo (prazo temporal em que processos precisam de ser criados/executados) como fator mais importante. Os processos podem ser **periódicos** (surgem depois de um intervalo de tempo fixo) ou **esporádicos** (surgem em instantes sem padrão regular). O escalonamento de múltiplos processos (com ou sem prazo temporal) é chamado de **escalonamento de tempo real**. Para cada processo sabe-se a sua frequência de execução, a sua quantidade de trabalho e a sua _deadline_.

O _schedule_ é o plano de ordem de execução. É **válido** quando no máximo uma tarefa é atribuída ao processador num dado instante, **viável** quando todas as tarefas alcançam as especificações temporais e **competente** quando é possível escalonar todos os processos de forma viável. Para que o escalonamento competente exista, é necessário que cada processo termine a sua execução antes da chegada de uma nova instância desse mesmo processo, e o tempo de código do sistema operativo, ao fazer comutação de contexto, despacho, ..., é desprezado (zero) - embora teoricamente possível, é praticamente impossível.

Os processos são periódicos e independentes. No escalonamento preentivo, um processo em execução pode ser interrompido para outro com maior prioridade, com a preenção a ocorrer instantaneamente e sem sobrecargas. O _deadline_ de cada processo coincide com o seu período, o tempo de computação de cada processo é conhecido e constante e as decisões de escalonamento são tomadas durante a execução.

O **_Rate Monotonic Scheduling_** é um algoritmo estático em que o escalonamento dos processos é baseado em parâmetros fixos, em que a prioridade é proporcional à frequência de ocorrência do processo (períodos mais curtos (alta frequência) implicam prioridade alta; períodos mais longos (baixa frequência) implicam prioridade baixa).

O **_Earliest Deadline First Scheduling_** é um algoritmo dinâmico em que o escalonamento dos processos é feito por uma lista de processos ordenada por _deadlines_, não requerendo processos periódicos. A ordenação de um processo é definida segundo o seu _deadline_ absoluto, sendo que o mais prioritário é o que tem o _deadline_ mais próximo em tempo real. A ordem de execução das tarefas é atualizada a cada chegada de um novo processo.

O **_Priority Inheritance Protocol_** é uma solução simples, mas fraca, em que uma tarefa na sua secção crítica não pode ser preentida, pelo que tarefas com uma prioridade mais alta podem sofrer bloqueio desnecessário. Quando uma tarefa bloqueia uma ou mais tarefas com priorirdade mais alta, ignora a sua prioridade original e executa a sua secção crítica no nível de mais alta prioridade de todas as tarefas que está a bloquear - a herança de prioridade é transitiva, podendo haver _deadlocks_ e bloqueios em cadeia.

O **_Priority Ceiling Protocol_** associa uma prioridade com cada recurso partilhado do sistema. Uma tarefa só pode começar uma nova secção crítica quando a sua prioridade é mais alta que todas as prioridades máximas de todos os recursos partilhados bloqueados por outras tarefas.

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

---

## Minitestes

#### Miniteste 1 - Bases, Estruturas e Arquitetura de um SO

* **Quais das funções seguintes das bibliotecas _standard_ de C nunca podem invocar uma chamada ao sistema no Linux?** : `strcmp`, `sqrt`.
* **Qual declaração sobre o DMA é sempre verdadeira?** : Exige sempre um _hardware_ especial / dedicado.
* **Considere o seguinte programa escrito em C. `main () { printf("ola"); asm(cli); }` Qual declaração está correta?** : O programa compila com avisos e executa com erro sem imprimir "ola" no ecrã.
* **Pode-se descrever os objetivos de um sistema operativo em tudo menos** : projetar uma solução informática.
* **O papel principal do temporizador de um sistema computacional para o sistema operativo é** : fornecer um mecanismo para poder sempre controlar o sistema.
* **O que não é um exemplo de um recurso que é habitualmente multiplexado por espaço?** : CPU.
* **O único programa que está sempre ponto a correr é** : o _kernel_ de um sistema operativo.
* **Um sistema operativo faz cada um dos seguintes, exceto** : garantir que os programas encerram a sua execução.
* **Quais das seguintes instruções devem ser privilegiadas?** : Limpar a memória. Aceder a um dispositivo de entrada/saída. Modificar as entradas na tabela de _status_ do dispositivo. Definir o valor do temporizador.
* **Qual declaração sobre o tratamento das interrupções num sistema operativo multiprogramado e preemtivo está incorreta?** : Quando é determinado que a nova sequência de instruções é concluída, a CPU restaura o PC antigo e a execução da sequência original prossegue.
* **O que não é um exemplo de um recurso que é habitualmente multiplexado por tempo?** : Memória principal.
* **No modelo de Von Neumann, quais das declarações seguintes estão falsas?** : Um sistema operativo é necessário para gerir a computação. Um programa está gravado num disco.
* **A principal função do interpretador de comandos é** : obter e executar o próximo comando especificado pelo utilizador.
* **O que é um sistema operativo?** : Todas as opções indicadas (Um conjunto de programas que gere os recursos físicos de um computador. Um sistema para ajudar utilizadores a atingirem os seus objetivos. Um fornecedor de serviços de sistema às aplicações).
* **Qual dos seguintes deve ser implementado como _software_ confiável no _kernel_?** : Gerente de multiprogramação.