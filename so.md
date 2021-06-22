# Sistemas Operativos

##### Atualizado em 11-06-2021
###### A partir de: apontamentos das aulas teóricas

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
* o sistema _online_ tem de estar disponível para acesso a dados e código. Quando o sistema operativo termina a execução de um comando, procura a próxima 'instrução de controlo' introduzida por um utilizador via teclado;
* o sistema _batch_ tem de executar programas de utilizadores _offline_.
  * Problema: memória insuficiente para todos os _jobs_. A CPU é atribuída a um _job_ só se ele estiver em memória e é multiplexada entre os vários _jobs_ em memória e no disco. Dificuldade na gestão de privacidade dos dados dos utilizadores.

Em sistemas multiprocessador / core:
* _Symmetric Multiprocessing_ (SMP): cada processador corre a única instância do sistema operativo, que escalona trabalho a qualquer dos processadores;
* _Assymetric Multiprocessing_ (AMP): o processador-mestre corre o sistema operativo e escalona trabalho aos processadores-escravos, que correm as aplicações.

Sistemas de Tempo Real - sistema com necessidades temporais onde os resultados têm de ser produzidos dentro de um tempo específico (prazo, _deadline_):
* Sistemas Embebidos - dispositivo de computação embutido num sistema maior (aviões, automóveis, satélites..., com múltiplos _inputs_ e _outputs_ físicos);
* Sistemas Críticos - com efeitos catastróficos em caso de falha (controlo de comportas, central nuclear, sistema médico);
* Sistemas Estritos de Tempo Real - garantem que as tarefas são executadas dentro das _deadlines_;
* Sistemas Latos de Tempo Real - tarefas de tempo real têm prioridade sobre tarefas normais.

---

## Aula Teórica 2

**BIOS** é a sigla para _Basic Input/Output System_, o primeiro programa executado pelo computador ao ser ligado, cuja função é preparar a máquina para que o sistema operativo possa ser carregado para memória e executado. O BIOS é _firmware_ (_software_ armazenado sob a forma de memória de leitura não volátil).

Um programa **_bootstrap_** é carregado durante _power up_ ou _reboot_ do BIOS, inicializando o _hardware_ para um estado "conhecido". O BIOS transfere controlo para o programa _bootstrap_, que inicializa todas as partes necessárias do sistema para carregar o _kernel_ do sistema operativo e inicializar a sua execução.

Os controladores de _input_/_output_ e a CPU podem executar de forma concorrente: cada controlador está encarregue de um dispositivo particular, com um _buffer_ local, e a CPU movimenta dados de e para a memória principal para e a partir de _buffers_ locais. Um controlador informa a CPU de que terminou a sua operação com uma **interrupção**, que transfere o controlo de uma rotina de serviço através do _interrupt vector_, que contém os endereços de todas as rotinas. As interrupções são desativadas enquanto outra interrupção está a ser processada de forma a evitar a sua perda; uma interrupção gerada por _software_ devido a erro ou pedido do utilizador é chamada por **_trap_**. A maior parte das CPU tem duas linhas de interrupção:
* **Linha de interrupção não mascarável**, reservada para eventos como erros de memória irrecuperáveis;
* **Linha de interrupção mascarável**, que pode ser desligada pela CPU antes da execução de uma sequência de instruções críticas que não podem ser interrompidas.

Durante _input_/_output_, as interrupções são feitas por vários dispositivos quando estão prontos para serviço, que significam o fim da saída de dados, a disponibilidade da entrada de dados ou a deteção de uma falha. O controlador interrompe a CPU, que a deteta e despacha para o _interrupt handler_, rotina que determina a causa da interrupção, executa o processamento necessário e termina, fazendo a CPU regressar ao estado anterior à interrupção.

Qualquer transferência é um _output_ de um dispositivo e um _input_ para outro. O controlador tem um ou mais registos para dados (registos _data-in_, _data-out_) e sinais de controlo (registos _status_, _control_). A interação entre a CPU e um controlador faz-se por **aperto de mão** (_handshaking_), utilizando dois bits (_busy_ bit do registo _status_ e _ready_ bit do registo _command_):
* A CPU lê repetidamente o bit _busy_ até que seja 0 (_busy-wait cicle_), ativa o bit _write_ a 1 no registo _command_ e escreve um byte no registo _data-out_. A CPU ativa o bit _ready_ a 1 no registo _command_ e, quando o controlador nota que o bit _ready_ está a 1, escreve o bit _busy_ a 1;
* O controlador lê o registo _command_ e vê o comando _write_, lendo o registo _data-out_ para obter o byte e fazer o _input_/_output_ para o dispositivo; desativa o bit _ready_ a 0, assim como o bit _error_ no registo _status_, para indicar que a transferência foi bem sucedida, colocando depois o bit _busy_ a 0 para indicar que a transferência terminou.

O **método síncrono** faz que, após o início de uma operação de _input_/_output_, o controlo só retorne ao programa do utilizador após essa operação através de uma instrução _wait_. Desvantagens: no máximo um pedido de _input_/_output_ é atendido de cada vez; não existe processamento de _input_/_output_ simultâneo; contenção para acesso à memória (ciclo _wait_). O **método assíncrono** faz que, após o início de uma operação de _input_/_output_, o controlo retorne ao programa do utilizador sem esperar pela terminação da operação de _input_/_output_. Vantagens: permite operações de _input_/_output_ concorrentes e processamento simultâneo. Desvantagens: implementação mais complexa.

A **interface de _input_/_output_ do _kernel_** é um conjunto de operações de _input_/_output_ independentes de _hardware_, e os **_device drivers_** são módulos do _kernel_ dependentes do _hardware_, cada um encapsulando o funcionamento específico de cada dispositivo. Vantagem: facilidade na implementação de novos periféricos. Os relógios e temporizadores (_clocks_, _timers_) permitem determinar tempo corrente / decorrido e ativar um temporizador para despoletar uma operação numa dada altura. Os dispositivos de _input_/_output_ caracterizam-se por:
* _Character-stream_/_block_ - transferência de bytes um a um (dispositivo de carateres [teclado, rato, com interface básica _get_, _put_]) ou em bloco (dispositivo de blocos [disco rígido, com interface básica _read_, _write_, _seek_; dispositivo de rede, com _sockets_]);
* Sequenciais / Acesso Aleatório;
* Síncronos / Assíncronos - transferência de dados com tempos de resposta previsíveis ou não;
* Partilháveis / Dedicados - se há partilha concorrente de processos ou não;
* Velocidade de operação;
* _Read-Write_ / _Read-Only_ / _Write-Only_.

Um DMA (**_Direct Memory Access_**) permite que certos dispositivos de _hardware_ de alta velocidade num computador acedam a memória do sistema para efetuar operações de _input_/_output_ independentemente da CPU. O controlador transfere blocos de dados do _buffer_ diretamente para a memória principal sem intervenção da CPU, com uma interrupção gerada por bloco (e não por byte), permitindo execução simultânea de CPU e operações de _input_/_output_. A transferência de dados pode ser feita por pedido síncrono do _software_ ou impulso assíncrono do _hardware_ para o sistema.

Armazenamento:
* **Memória Principal:** só acedida pela CPU;
* **Memória Secundária:** extensão da memória principal com grande capacidade de armazenamento não-volátil;
* **Discos Magnéticos:** pratos de vidro ou metal rígido revestidos de material magnético de gravação com pistas (_tracks_) divididas em setores (_sectors_);
* **_Caching_:** cópia de informação num sistema de armazenamento utilizando memória de alta velocidade para guardar dados recentemente acedidos.

A partilha de recursos do sistema requer que o sistema operativo assegure que um programa incorreto não faça com que outros programas funcionem incorretamente. A proteção de _hardware_ é assegurada por:
* **Operação em _dual-mode_:** diferencia pelo menos dois modos de operação, _user-mode_ (desencadeada pelo utilizador) e _monitor-mode_/_kernel-mode_/_system-mode_/_bit-mode_ (desencadeada pelo sistema operativo), em que quando uma interrupção ocorre, o _hardware_ comuta para o _monitor-mode_;
* **Proteção de _input_/_output_:** todas as instruções de _input_/_output_ são instruções privilegiadas, assegurando que um programa do utilizador não consegue controlar o computador em _monitor-mode_;
* **Proteção de memória:** adiciona dois registos que determinam a gama de endereços a que um programa pode aceder (**registo de base**, endereço mais baixo da memória física; **registo limite**, tamanho da gama), em que as instruções de carregamento dos registos de base e de limite são instruções privilegiadas;
* **Proteção da CPU:** o temporizador interrompe o computador após um período de tempo especificado, assegurando que o sistema operativo possa manter controlo e implementar _time-sharing_ e em que _load-timer_ é uma instrução privilegiada.

---

## Aula Teórica 3

**Modelo de compilação**
* Pré-processador (`.i`) - `cc -E main.c -o main.i`, `cc -E sub.c -o sub.i`
* Compilador (`.s`) - `cc -Wall -ansi -S *.i`
* Assembler (`.o`) - `cc -c *.s`
* _Linkagem_ (`.out`) - `cc -o exemplo main.o sub.o -lm`
  * Estática (código embutido)
  * Dinâmica (endereço do código)
    * Modelo de _Run-Time_: programa executável > chamada ao sistema > início > realocação de código > execução do programa
* Programa binário executável

O _scope_ de uma variável define as secções de código onde a variável está válida. Símbolos são entidades lexicais que nomeiam funções, variáveis e constantes, cada um com um valor (endereço de memória). O código consiste de definições e referências de símbolos, que podem ser locais ou externas (globais). Cada ficheiro-objeto executável tem uma tabela de símbolos. Os símbolos podem ser **fortes** (procedimentos e variáveis globais inicializadas) ou **fracos** (variáveis globais não inicializadas), seguindo as seguintes regras:
* um símbolo forte só pode aparecer uma vez;
* Um símbolo fraco pode ser sobreposto por um símbolo forte com o mesmo nome;
* Se há vários símbolos fracos, o _linker_ pode escolher um aleatoriamente.

Um _linker_ funde ficheiros-objetos num único ficheiro-objeto executável, realocando símbolos das suas posições relativas nos ficheiros `.o` para posições 'absolutas' no executável. _Linkers_ são **modularidáveis** (o programa pode ser escrito numa coleção de ficheiros-fonte mais pequenos, permitindo construir bibliotecas de funções comuns) e **eficientes** (não necessita de recompilar todos os ficheiros após alterações; permite utilizar apenas os programas que contenham o código desejado).

O formato **ELF** (_Executable and Linkable Format_) é um formato binário padrão para ficheiros-objeto. É constituído por _elf header_ (número mágico, tipo, máquina, ordenação de bytes), _program header table_ (tamanho de página, segmentos de endereços virtuais de memória, tamanho de segmentos), _.text section_ (código), _.data section_ (dados estáticos inicializados), _.bss section_ (dados estáticos não inicializados), _.symtab section_ (tabela de símbolos, nomes de variáveis estáticas e procedimentos, nomes e localizações de secções), _.rel.text section_ (informação realocada da secção _.text_, endereços de instruções a alterar no executável, instruções a executar), _.rel.data section_ (realocação da secção _.data_, endereços de apontadores de dados que precisam de ser modificados no executável), _.debug section_ (informação para _debugging_).

As **bibliotecas estáticas** (ficheiros de arquivo `.a`) concatenam arquivos de objetos relocáveis relacionados num único ficheiro com um índice (arquivo), melhorando o _linker_ de modo a que este procure referências externas não resolvidas ao observar os símbolos de um ou mais arquivos e as ligue a ficheiros executáveis. O _archiver_ permite atualizações pontuais, como recompilar uma função modificada ou substituir ficheiros `.o` num arquivo. O algoritmo do _linker_ para encontrar referências externas é:
* Examinar ficheiros `.o` e `.a` na linha de comandos, mantendo uma lista de referências não resolvidas;
* A cada novo `.o` ou `.a` encontrado, tentar resolver as referências;
* Se alguma entrada na lista continuar não resolvida, mostrar erro.
Isto implica ordem específica de ficheiros e colocação de bibliotecas no final da linha de comandos. Tal pontenciona a duplicação de código comum nos ficheiros executáveis e na memória, e que a reparação de pequenos _bugs_ requira que cada aplicação seja explicitamente _relinkada_.

As **bibliotecas partilhadas** (_Dynamic Link Libraries_, DLL) permitem que a _linkagem_ dinâmica ocorra antes ou durante a execução do ficheiro e sejam partilhadas por processos múltiplos.

---

## Aula Teórica 4

Um **processo** é um programa em execução sequencial que inclui secção de texto, contador de programa, registos do processador, pilha (_stack_) com variáveis locais, funções, endereços de retorno, e secção de dados com variáveis globais. Esta noção permite que vários utilizadores usem várias cópias do mesmo programa em simultâneo. Um processo é representado por um **bloco de controlo do processo** (PCB, _process control block_), que é a representação do conceito pelo sistema operativo e contém um identificador único (valor inteiro chamado PID, _process ID_). Cada processo tem informação associada:
* **Estado do processo** - diagramas de estados;
* **Contador do programa (PC)** - endereço da próxima instrução a ser executada;
* **Registos da CPU** - acumuladores, registos de indexação, ponteiros de pilha, registos gerais, ...;
* **Informação de escalonamento da CPU** - prioridade do processo, ponteiros para filas de escalonamento, ...;
* **Informação de gestão de memória** - valores dos registos de base e de limite, tabelas de paginação/segmentação;
* **Informação de inventário** - CPU gasto, memória usada;
* **Informação de estado de I/O** - lista de dispositivos I/O afetados, lista de ficheiros abertos, ....

Para maximizar a utilização da CPU deve haver sempre um processo a correr (em execução) e, num dado instante, só um processo pode usar um dispositivo de I/O. Isto obriga a troca entre os processos em execução (comutação do contexto), separação por estádios (filas de processos) e escolha dos processos nas filas e transições (escalonamento). A **comutação do contexto** define a partilha do processador através de um mecanismo de comutação de processos através da salvaguarda do estado do processo que perde a CPU e a restauração do estado do processo que ganha a CPU; se for demasiado frequente, pode ter um custo _overhead_ para o sistema. O sistema operativo executa muitos processos em simultâneo, com o CPU multiplexado entre eles, fornecendo também mecanismos de manipulação e comunicação (IPC, _InterProcess Communication_).

Um _dispatcher_ é um procedimento que atribui o processador de um processo para outro e previne que um processo ocupe todo o tempo do CPU. Num modelo de dois estados, o programa é _dispatched_ e pausado em ciclo, até terminar.

Num modelo de cinco estados, o processo é criado (_new_), as instruções são executadas (_running_), o processo espera que algum evento ocorra (_waiting_) ou que lhe seja atribuído o processador (_ready_), até terminar a execução (_terminated_). Só um processo pode estar no estado _running_, mas vários podem estar nos estados _ready_ e _waiting_.

No escalonamento de processos, um novo processo é colocado na _ready queue_, onde fica em espera até ser selecionado e despachado para a CPU. Durante a sua execução, o processo pode emitir um pedido I/O e ser colocado numa _I/O device queue_; ser removido da CPU por interrupção do _timer_ e transitar de novo para a _ready queue_; criar um novo subprocesso, ficando à espera que ele termine; esperar por um _interrupt_ qualquer e pela sua reinicialização. A _ready queue_ contém os PCBs dos processos residentes na memória em estado _ready_ (prontos e à espera de executar); as _waiting queues_ contêm processos em espera da conclusão de I/O ou outro dispositivo. Qualquer recurso pode ter associada uma fila de escalonamento, e existe migração de processos entre as várias filas.

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

O processo filho criado pela chamada ao sistema `fork()` duplica o espaço de memória do processo pai, executando depois em concorrência, quando o `fork()` devolve valores diferentes para os diferentes processos, podendo o programa tomar várias linhas de ação através de uma instrução de controlo _if_. O processo pai pode esperar a terminação do processo filho usando a chamada `wait()`. A função `fork()` cria um novo processo (processo filho) que é uma cópia exata do processo inicial (processo pai), exceto que: o ID no processo filho é único e diferente do ID do processo pai, o processo filho tem a sua própria cópia dos descritores do processo pai, os recursos utilizados pelo processo filho são inicializados a 0. O processo filho (ou pai) pode carregar um novo programa usando a chamada ao sistema `exec()`, que necessita do nome de um novo programa - o texto e variáveis do programa velho são substituídos pelo novo, que herda também o identificador do processo (PID) e outras informações.

Um processo pai pode terminar-se com uma chamada a `exit()`, sendo depois os processos filho herdados pelo processo `init`. Processos pai podem esperar pela terminação dos processos filho pela chamada `wait()`, que retorna ao processo pai caso o processo filho já tenha terminado, ou bloqueia o processo pai caso contrário. `exit()` termina o processo de chamada: todos os ficheiros são fechados, o _output_ do _buffer_ é escrito e são chamadas funções `exit` registadas. `_exit()` termina a execução sem fechar quaisquer ficheiros, esvaziar o _output_ ou chamar qualquer função `exit`.

O escalonamento do processador tem por principal objetivo maximizar o uso da CPU através de multiprogramação (remoção da CPU de um processo para a atribuir a outro). Um **ciclo _burst CPU - I/O_** é a execução de um processo com execução na CPU e espera no I/O. O sucesso do escalonamento da CPU depende de vários ciclos CPU-I/O tal que uma intermitência (_burst_) de execução da CPU alterna com uma intermitência (_burst_) de espera pela finalização de uma operação I/O. Os processos _I/O-bound_ têm grande número de _CPU bursts_ de curta duração, e os processos _CPU-bound_ têm pequeno número de _CPU-bursts_ de longa duração. Quando a CPU fica livre, cabe ao sistema operativo selecionar um dos processos da _ready queue_ para executar, através do escalonador de curto prazo quando um processo comuta de _running_ para _waiting_, _ready_ ou _terminated_ ou de _waiting_ para _ready_.

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
  * Não preentivo - ao ser atribuída CPU a um processo, este não pode ser preencionado até completar o seu _CPU burst_;
  * Preentivo - se um novo processo chega à _ready queue_ com um _CPU burst_ menor que o tempo restante do processo em execução, então há preenção (_Shortest Remaining Time First (SRTF));
* **Prioridade** - caso geral do SJB, em que a cada processo é atribuída uma prioridade e o escalonador atribui a CPU ao processo com maior prioridade (menor inteiro, cujo desempate se faz com FCFS). Processos de baixa prioridade arriscam-se a nunca ser executados (_starvation_), o que é solucionado por _aging_ (à medida que o tempo passa, a prioridade de um processo aumenta). A prioridade é atribuída de acordo com: limites de tempo, requisitos de memória, número de ficheiros abertos, duração média dos _bursts_ de I/O e de CPU (fatores internos), importância, preço pago pelo uso, proprietário (fatores externos);
* **_Round Robin_** - concebido para sistemas de _time sharing_ e semelhante ao FCFS (mas preentivo), atribui a cada processo uma pequena unidade de tempo na CPU (_time quantum_ ou _time slice_), ao final do qual o processo é preencionado e adicionado à cauda da _ready queue_ (tratada como uma fila circular). Se há `n` processos na _ready queue_ e o _time quantum_ é `q`, cada processo obtém `1/n` do tempo da CPU em fatias de `q` unidades de tempo de uma vez, sem que nenhum processo espere mais do que `(n - 1) * q` unidades de tempo. Se `q` é grande, aplica-se FIFO, se não, a sobrecarga é muito elevada;
* **Multifila** - usado quando os processos podem ser classificados em classes distintas e particionados em várias filas dependendo do processo (_foreground_, sistemas interativos (RR), e _background_, sistemas _batch_ (FCFS)));
* **Multifila com Transbordo** - permite prioridades por fila, preenção, generalidade e configurabilidade, e também a movimentação de processos entre várias filas.

A avaliação de algoritmos é feita por **modelação e simulação**: definir um _workload_/_trace_ e depois simular o desempenho de cada algoritmo, podendo ser **determinístico** (definir um _workload_ baseado em dados reais ou inventados) ou **aleatório** (utilizar processos aleatórios e probabilísticos).

Num escalonamento multiprocessador, é usada uma única _ready queue_ para evitar que haja processadores inativos enquanto outros têm processos à espera. Há duas políticas de escalonamento multiprocessador: **processadores autoescalonáveis** (cada processador é responsável pela seleção de um processo existente na _ready queue_ partilhada) e **processador mestre - processadores escravo**, em que um processador (mestre) desempenha o papel de escalonador dos restantes (escravos).

---

## Aula Teórica 6

**Sistemas de Tempo Real** têm o tempo (prazo temporal em que processos precisam de ser criados/executados) como fator mais importante. Os processos podem ser **periódicos** (surgem depois de um intervalo de tempo fixo) ou **esporádicos** (surgem em instantes sem padrão regular). O escalonamento de múltiplos processos (com ou sem prazo temporal) é chamado de **escalonamento de tempo real**. Para cada processo sabe-se a sua frequência de execução, a sua quantidade de trabalho e a sua _deadline_.

O _schedule_ é o plano de ordem de execução. É **válido** quando no máximo uma tarefa é atribuída ao processador num dado instante, **viável** quando todas as tarefas alcançam as especificações temporais e **competente** quando é possível escalonar todos os processos de forma viável. Para que o escalonamento competente exista, é necessário que cada processo termine a sua execução antes da chegada de uma nova instância desse mesmo processo, e o tempo de código do sistema operativo, ao fazer comutação de contexto, despacho, ..., é desprezado (zero) - embora teoricamente possível, é praticamente impossível.

Os processos são periódicos e independentes. No escalonamento preentivo, um processo em execução pode ser interrompido para outro com maior prioridade, com a preenção a ocorrer instantaneamente e sem sobrecargas. O _deadline_ de cada processo coincide com o seu período, o tempo de computação de cada processo é conhecido e constante e as decisões de escalonamento são tomadas durante a execução.

O **_Rate Monotonic Scheduling_** é um algoritmo estático em que o escalonamento dos processos é baseado em parâmetros fixos, em que a prioridade é proporcional à frequência de ocorrência do processo (períodos mais curtos (alta frequência) implicam prioridade alta; períodos mais longos (baixa frequência) implicam prioridade baixa).

O **_Earliest Deadline First Scheduling_** é um algoritmo dinâmico em que o escalonamento dos processos é feito por uma lista de processos ordenada por _deadlines_, não requerendo processos periódicos. A ordenação de um processo é definida segundo o seu _deadline_ absoluto, sendo que o mais prioritário é o que tem o _deadline_ mais próximo em tempo real. A ordem de execução das tarefas é atualizada a cada chegada de um novo processo.

O **_Priority Inheritance Protocol_** é uma solução simples, mas fraca, em que uma tarefa na sua secção crítica não pode ser preentida, pelo que tarefas com uma prioridade mais alta podem sofrer bloqueio desnecessário. Quando uma tarefa bloqueia uma ou mais tarefas com prioridade mais alta, ignora a sua prioridade original e executa a sua secção crítica no nível de mais alta prioridade de todas as tarefas que está a bloquear - a herança de prioridade é transitiva, podendo haver _deadlocks_ e bloqueios em cadeia.

O **_Priority Ceiling Protocol_** associa uma prioridade com cada recurso partilhado do sistema. Uma tarefa só pode começar uma nova secção crítica quando a sua prioridade é mais alta que todas as prioridades máximas de todos os recursos partilhados bloqueados por outras tarefas.

---

## Aula Teórica 7

O conceito de um processo pode ser dividido em dois:
* Conjunto de recursos necessários para a execução de um programa (espaço de endereçamento com texto e dados do programa, tabela de descritores de ficheiros abertos pelo processo, informação sobre processos-filho, código para tratar de sinais, informação sobre o próprio programa);
* Linha ou contexto de execução (_thread_, com um _program counter_ que guarda informação sobre a próxima instrução a executar, contexto (registo dos valores das variáveis atuais), _stack_ (histórico de execução com um _frame_ para cada procedimento chamado mas não terminado)).

Processos são usados para agrupar recursos (independentes e com variáveis, _stack_ e alocação de memória próprias) e _threads_ são as entidades escalonadas para execução no CPU (rotinas com partilha de espaço de memória e variáveis globais).

_Threads_ são muito rápidas (com criação, comutação e término de _threads_ mais rápido que os de processos), permitem partilha de recursos e a criação de várias _user interfaces_ e escalabilidade (usam um modelo mais simples e portável do que processos). No entanto, é fácil fazer erros com _threads_ (concorrência) e há mais problemas de segurança. _Threads_ múltipas podem estar a executar simultaneamente para aproveitar arquiteturas e pode haver um conjunto de _threads_ (_thread pool_) prontas para executar, sem desperdício de tempo para a sua inicialização. _Threads_ são implementadas por:
* **_Kernel-Level Threads_** - chamadas ao sistema. O _kernel_ pode escalonar várias _threads_ do mesmo processo em vários processadores ao mesmo tempo e as _threads_ podem ser aproveitadas pelas rotinas do próprio _kernel_; no entanto, a troca entre _threads_ implica ações do _kernel_ que podem ter um custo significativo;
* **_User-Level Threads_** - bibliotecas de _threads_. A troca de _threads_ não envolve o _kernel_ (logo, mais simples e sem custos), o escalonamento pode ser específico para uma aplicação e podem ser executadas em qualquer sistema operativo; no entanto, muitas das chamadas ao sistema são bloqueadas pelo _kernel_ e duas _threads_ do mesmo processo não podem ser executadas em simultâneo numa arquitetura com múltiplos processadores.

O _standard_ **POSIX** define uma _Application Programming Interface_ (API) para a escrita, criação, destruição, sincronização e agendamento de aplicações com _multithreading_. A rotina `pthread_join()` espera pelo término de uma _thread_ específica. Se uma _thread_ não executa a operação da união por não precisar de saber o término de outra por ela criada, está-se na presença de _detached threads_. Uma _thread_ pode precisar de terminar outra _thread_ (_canceled thread_). Quando duas ou mais _threads_ podem alterar em simultâneo as mesmas variáveis globais (ou uma alterar enquanto outra está a ler) poderá ser necessário sincronizar o acesso a essa variável para evitar problemas - **secção crítica**, que deve ser protegida com um trinco lógico (funções `pthread_mutex_lock()` e  `pthread_mutex_unlock()`). Estes _locks_ são implementados com variáveis mutuamente exclusivas, cujo _default_ é NULL e, quando criada dinamicamente (através de _malloc_), deve ser destruída com a função `pthread_mutex_destroy()`.

---

## Aula Teórica 8 / 9

Há três tipos de problemas de gestão de recursos:
* _Starvation_ (inanição) - um processo fica indefinidamente bloqueado sem recursos devido à política de escalonamento da CPU;
* _Deadlock_ (impasse / bloqueio mútuo) - quando dois processos se bloqueiam entre si;
* Inconsistência / Corrupção de Dados - dois processos com acesso à mesma estrutura de dados não podem atualizá-la sem sincronização.

A **condição de corrida** é a situação em que vários processos acedem e manipulam dados partilhados em simultâneo, podendo criar inconsistências nos dados, tornando-se necessário haver **sincronização** para o evitar. Uma operação atómica é uma instrução executada na totalidade sem interrupção. Um _spooler_ é uma fila composta por um diretório onde é guardada uma cópia dos ficheiros a imprimir e uma estrutura de dados a controlar a ordem de impressão. O _kernel_ do sistema operativo ou o processo responsável pelo _spooler_ deve detetar disponibilidade da impressora, enviar o ficheiro para a impressora quando ela estiver livre, atualizar o diretório do _spooler_ ao remover o ficheiro, e atualizar a fila de espera.

Os problemas clássicos de sincronização são:
* Produtor-Consumidor (_bounded-buffer_) - o processo-produtor produz itens para uma fila, que são removidos por um processo-consumidor, sendo a fila partilhada entre ambos;
* _Readers/Writers Problem_ - os dados partilhados entre os vários processos são lidos apenas por alguns processos e escritos apenas por outros (que modificam os dados), de modo a que os dados a serem lidos não estejam a ser alterados;
* Jantar de Filósofos - partilha de um número finito de recursos entre um número de processos maior que o número de recursos.

Na partilha de dados por vários processos, cada processo tem um segmento de código (**secção crítica**) no qual os dados partilhados são acedidos. Para assegurar que, enquanto um processo está a executar na secção crítica, nenhum outro processo pode executar na sua secção crítica:
* Exclusão mútua - só um processo de cada vez pode entrar e executar na secção crítica;
* Progressão - um processo a executar numa secção não-crítica não pode impedir outros processos de entrar na secção crítica;
* Espera Limitada - um processo que queira entrar numa secção crítica não deve ficar à espera indefinidamente.

A consistência de dados é assegurada por vários mecanismos de sincronização:
* _Software_ - mecanismos genéricos de uma linguagem de programação (algoritmos experimental, de Dekker, de 2, de Lamport);
* _Hardware_ - mecanismos disponibilizados pelo _hardware_;
* Recursos do sistema operativo - semáforos, passagem de mensagens;
* Monitores - mecanismo específico de uma linguagem de programação.

O algoritmo de **solução alternância estrita** garante a exclusão mútua a apenas dois processos, não garante progressão ou espera limitada e só funciona se os dois processos forem absolutamente alternativos. O algoritmo de **Dekker** / **Peterson** garante exclusão mútua e progressão, mas obriga a que o número de processos seja dois e não garante a espera limitada. O algoritmo de **Lamport** atribui uma senha de entrada na secção crítica (que não está garantido ser a superior), e o processo efetua um ciclo para determinar se o seu número de ordem é o menor de todos; se for, entra na secção crítica.

Para simplificar os algoritmos, pode usar-se variáveis que funcionam como trincos lógicos de uma estrutura de dados, que é fechado quando se acede à estrutura de dados e aberto à saída, manipulado por duas primitivas: _lock_ e _unlock_. Um processo que tenta aceder a uma secção crítica protegida por um trinco ficará em ciclo no teste até o trinco ser libertado.

Também se pode inibir as interrupções antes da entrada de uma secção crítica e ativá-las de novo à saída, impedindo a troca de processos pela CPU (o que garante que um processo pode utilizar uma variável partilhada sem a interferência de nenhum outro processo); no entanto, apenas funciona com sistemas de uniprocessador, pode impedir o tratamento de interrupções e pode implicar o _crash_ do sistema operativo e problemas a nível de _cache_.

Os trincos lógicos podem ser feitos por _hardware_ através da implementação da exclusão mútua, garantindo ou não a espera limitada. Todos os processos que não conseguem entrar na secção crítica ficam à espera, não havendo nenhum mecanismo que evite a preenção de um processo quando está a executar na zona crítica - **espera ativa**, quando um processo a executar na secção crítica é retirado do processador: o trinco mantém-se fechado e os outros processos vão passando sucessivamente pelos processadores, continuando a testar o trinco para verificar a sua abertura e a gastar CPU.

Um **semáforo** é um mecanismo de sincronização sem espera ativa que consiste numa variável e numa fila de espera associada a um recurso que contém todos os descritores dos processos bloqueados no semáforo, manipulado através de duas primitivas atómicas (_wait_ e _signal_). **Bloquear** um processo num semáforo significa retirá-lo do estado de execução (_running state_) e movê-lo para a fila de processos bloqueados (_waiting state_); **desbloquear** um processo significa retirá-lo da fila de processos bloqueados (_waiting state_) e inseri-lo na fila de processos executáveis (_ready state_). Dois ou mais processos podem executar uma secção crítica com exclusão mútua, progressão e espera limitada - semáforo binário de exclusão mútua. Dois ou mais processos podem cooperar através de sinais, em que um processo é obrigado a parar num local especificado até receber um determinado sinal - semáforo de manipulação de eventos.
* *Deadlock* ocorre quando dois ou mais processos estão à espera indefinidamente por um evento que só pode ser causado por um dos processos à espera;
* *Starvation* é um bloqueio indefinido, em que um processo corre o risco de nunca ser removido da fila do semáforo na qual está suspenso.

Outros métodos de comunicação entre processos:
* _Pipes_ - sincronização e comunicação unidirecional através do _kernel_ (interação entre um produtor (remetente, emissor) e um consumidor (destinatário, recetor) de informação);
* _Message Queues_ - sincronização e comunicação bidirecional através do _kernel_ (comunicação através de _mailboxes_ ordenadas em FIFO, com as primitivas _send (mailbox, message)_ e _receive (mailbox, message)_, cujas mensagens contêm tipo, comprimento e dados);
* _Shared Memory_ - comunicação rápida de dados sem sincronização (exige o uso de um semáforo partilhado);
* _Signals_ - permitem sincronização (comunicação do acontecimento de um evento, mas sem comunicação de dados ou informação);
* _Sockets_ - comunicação por canal bidirecional sem sincronização.

A capacidade da _mailbox_ pode ser:
* **Capacidade zero** - não pode haver mensagens armazenadas, o emissor tem de esperar pela disponibilidade do recetor e os processos têm de sincronizar em qualquer troca de mensagens;
* **Capacidade limitada** - tamanho finito, se a fila estiver cheia não há necessidade de bloquear o emissor, o sucesso de envio não implica sucesso de receção;
* **Capacidade ilimitada** - tamanho infinito, o emissor nunca é bloqueado, o sucesso de envio não implica sucesso de receção.

A passagem de mensagens pode ser **assíncrona** (o emissor envia um pedido e continua a execução), **síncrona** (o emissor fica bloqueado até receção da mensagem) ou **cliente/servidor** (o emissor fica bloqueado até o recetor lhe responder). Uma falha num processo não implica necessariamente a falha de todo o sistema, mas quando ocorre alguma avaria deve ser executado algum processo de recuperação de erro. A terminação anormal de um processo pode decorrer porque o processo B bloqueia indefinidamente à espera de uma mensagem do processo Q que já terminou ou porque o processo P envia uma mensagem ao processo Q que já terminou.

Um conjunto de sistemas está mutuamente bloqueado (**_deadlocked_**) quando cada processo do conjunto está atribuído a pelo menos um recurso mas está à espera da libertação de um recurso atribuído a outro processo do conjunto. Os **recursos** podem ser físicos (ciclos CPU, espaço de memória, dispositivos de I/O) ou lógicos (semáforos, ficheiros, _sockets_) e preentivos (podem ser removidos do processo proprietário sem problema) ou não preentivos (não podem ser removidos sem que a computação falhe). Um processo requisita, utiliza e liberta um recurso; se o recurso não estiver disponível, o programa continua (sem utilizar o recurso) ou espera que o recurso fique disponível. Para ocorrer _deadlock_, há quatro condições:
* **Exclusão mútua** - um recurso pode ser atribuído apenas a um processo;
* **Posse e espera** - um processo na posse de um recurso está à espera de mais recursos;
* **Não preenção** - um recurso só pode ser libertado pelo processo proprietário depois de terminar o seu uso, sem poder ser removido;
* **Espera circular** - existe um encadeamento circular de dois ou mais processos, cada um à espera de um recurso na posse do processo seguinte.

Se num grafo de alocação de recursos não houver ciclos, então não há _deadlock_; se houver pelo menos um ciclo, e se existir apenas uma instância de cada recurso então há _deadlock_, se existirem várias instâncias então há a possibilidade de haver _deadlock_ (deve ser analisado por análise virtual e argumento lógico, algoritmos de deteção de ciclos ou _model checkers_). Para evitar e prevenir _deadlocks_, o sistema operativo deve conhecer sempre o estado do sistema e guardar informações suplementares sobre cada processo (ou configurar o sistema _a priori_ para evitar processos), embora muitas vezes se use o 'algoritmo de avestruz' (fingir que não existem _deadlocks_).

---

## Aula Teórica 10

Um programa deve ser colocado na memória dentro do contexto de um processo para poder ser executado. O _binding_ ou conexão de endereços a instruções e dados a endereços de memória pode acontecer em três estágios diferentes:
* Tempo de compilação - se a localização em memória de um programa é conhecida _a priori_, então o código absoluto pode ser gerado, se não, o código é recompilado;
* Tempo de carregamento - se a localização em memória não é conhecida em tempo de compilação, então é necessário gerar código relocável;
* Tempo de execução - se um processo pode ser transladado durante a sua execução de um segmento de memória para outro, então os endereços são alterados a nível de _hardware_.

O processo que contém o programa poderá transitar entre o disco e a memória durante o seu tempo de execução, sendo cada instrução e dados acedidos pela CPU à medida que o programa é executado e cujo espaço é libertado após o término da execução. Em multiprogramação há dois problemas: **código relocável** (como a localização da memória física não é conhecida _a priori_, os endereços são relativos) e **proteção** (deve assegurar-se de que um programa não interfere noutro enquanto executam), que podem ser solucionados usando **registo base** para o endereço físico mais baixo da memória e **registo limite** para o endereço físico mais elevado da memória, permitindo mudar um processo de uma parte da memória para outra.

O **endereço lógico** (virtual) é gerado pela CPU e o **endereço físico** é gerado pela MMU (_Memory Management Unit_, dispositivo de _hardware_ que transforma endereços virtuais em endereços físicos). Se forem conectados em tempo de compilação ou carregamento, os endereços devem ser iguais; se forem conectados em tempo de execução, os endereços devem ser diferentes.

A **locação contínua de memória em partição única** pretende proteger o espaço de endereçamento do sistema operativo de modo a evitar alterações por parte dos processos e o espaço de endereçamento dos processos uns dos outros, através do _registo de recolocação_ (endereço físico mais baixo gerado pela CPU) e do _registo limite_ (gama de endereços lógicos usados pelo processo).
* Uma solução é subdividir a memória em **partições de tamanho fixo**, para as quais são atribuídos processos à medida que são executados e o seu espaço de memória é liberto. No entanto, torna-se difícil saber o tamanho de partição necessário por um processo; um processo posto numa das filas pode ser proibido de executar devido a outros processos também em espera; há desperdício de memória (_fragmentação interna_, quando um programa tem tamanho menor que a partição);
* Outra solução é a subdivisão da memória em **partições de tamanho variável** de acordo com o tamanho dos processos, com algoritmos de _first-fit_, _best-fit_ ou _worst-fit_. No entanto, pode haver _fragmentação externa_;
* Outra solução é a **paginação**, em que a memória física é dividida em blocos de tamanho fixo (molduras) e a memória lógica é dividida em blocos do mesmo tamanho (páginas). As páginas (cujo endereço gerado na CPU tem _page number_ e _page offset_) são atribuídas a molduras de acordo com o seu tamanho e os programas são executados. A tabela de páginas é guardada na memória principal, acedida em conjunto com os dados e instruções, e o acesso à memória pode ser resolvido através de uma cache de pesquisa rápida. A proteção de memória é garantida com um bit de proteção em cada moldura, que pode ser válido (se a página associada está no endereçamento lógico do processo) ou inválido (se a página associada não está no endereçamento lógico do processo).

A segmentação é um esquema de gestão de memória que reflete a visão que o utilizador tem da memória. A tabela de segmentação traduz endereços lógicos bidimensionais em endereços físicos unidimensionais (com base (endereço físico do início do segmento de memória) e limite (comprimento do segmento)). 

---

## Aula Teórica 11

Em sistemas apenas com memória física, os endereços gerados pelo CPU têm uma correspondência quase direta aos endereços da memória física. A execução de programas com tamanho total superior à capacidade de memória é conseguido por:
* **Overlay** - mecanismo obsoleto de linguagem de programação. Mantinha-se em memória apenas as instruções e dados necessários em determinada altura, dividindo o programa em secções logicamente distintas. O programador era responsável pela divisão do programa, numa operação difícil e dispendiosa em termos temporais;
* **Swapping** - mecanismo embutido no sistema operativo que usa memória secundária como memória principal. Um processo pode ser temporariamente expulso (_swapped out_) da memória para um _backing store_ (disco que aloja cópias das imagens de memória dos processos dos utilizadores), e depois readmitido (_swapped in_) para continuar a sua execução;
* **Memória virtual** - extensão do conceito lógico de memória. Apenas a parte ativa (_working set_) do programa precisa de estar em memória (maior eficácia), fornecendo mecanismos de simplificação de gestão de memória e proteção (por _demand paging_ e _demand segmentation_).

Num sistema com memória virtual, o _hardware_/_software_ traduzem os endereços virtuais para endereços físicos através de uma estrutura de dados gerida pelo sistema operativo. Se o espaço virtual tem 32 bits (4 GB) e a página tem 12 bits (4 KB), então a tabela de páginas tem 20 bits de entradas de 32 bits - gastando 4 MB. Cada página, além de uma _frame_, tem associado um bit válido/inválido (1 = válido (dentro da memória), 0 = inválido (fora da memória)), que é inicializado a 0.

Em _demand paging_, uma página é trazida para a memória apenas quando necessária (diminuindo o I/O e memória necessários e o tempo de resposta e permitindo mais utilizadores). As zonas de memória virtual não carregadas em memória principal e com dados ou código dos processos estão numa _backing store_. Uma _page fault_ é uma instrução na CPU que utiliza um endereço lógico traduzido pelo _memory management unit_ (MMU) (1) para uma página que não está na memória (_trap OS_) (2); obtém-se a localização da _frame_ (3), há o _swap_ de páginas na _frame_ (4), _reset_ de tabelas (5) e recomeço da instrução (6). No _hardware_, o processador sinaliza o controlador (lê um bloco de comprimento P que começa no endereço de disco X e guarda no endereço de memória Y), lê-se pela memória de acesso direto (DMA) sob o controlo de I/O, que interrompe o processo e faz o sistema operativo retomar os processos suspensos. A probabilidade de uma falha de página está entre 0 (sem falhas) e 1 (cada referência é uma falha).

Se não houver uma _frame_ disponível, o sistema operativo terá de encontrar uma página em memória não utilizada e utilizá-la. O **mecanismo de substituição** completa a separação da memória lógica da memória física - permitindo que uma grande memória virtual possa ser fornecida por uma pequena memória física. A execução do processo é parada e o sistema operativo localiza a página no _backing store_ e uma _frame_ livre (se existir, utiliza-a, se não, seleciona uma vítima através de algoritmos); o processo é inserido na _frame_ e as estruturas do sistema operativo são atualizadas, recomeçando a execução do processo. Os algoritmos usam uma dada sequência de referências à memória (_reference string_) e calculam o número de falhas da página:
* **FIFO** (_First In First Out_);
* **Random** - a página de substituição é escolhida aleatoriamente entre as m _frames_ de probabilidade 1/m;
* **Optimal** (Beladys) - substituição da página que não vai ser usada durante a maior quantidade do tempo (_benchmark_ contra o qual outros algoritmos podem ser comparados);
* **LRU** (_Least Recently Used_) - os programas acedem à memória por _localidade temporal_ (se um endereço for acedido agora, há uma grande probabilidade de ser acedido no futuro próximo) e _localidade espacial_ (se um endereço for acedido, há uma grande probabilidade de os próximos endereços serem endereços próximos), ou seja, as páginas muito utilizadas nas últimas instruções têm grande probabilidade de ser utilizadas novamente na seguinte e as páginas não utilizadas permanecerão sem uso.

O LRU pode ser implementado com _contadores_ (cada página tem um relógio associado com valor inicial nulo que é atualizado de cada vez que a página é utilizada, comparando-se depois os valores dos relógios) ou com _pilhas_ (guarda-se uma estrutura de dados que representa uma pilha de páginas usadas, com a última referenciada no topo).

Também é preciso definir uma **política de alocação**, especificando quantas _frames_ são tidas por um processo, baseadas num _working set_: conjunto de páginas que um processo referencia ativamente. As páginas usadas de um processo têm de ser mantidas na memória, e outras páginas não utilizadas podem estar inválidas (libertando espaço em memória para outros processos) - havendo necessidade de otimizar o tamanho do conjunto de trabalho. O **esquema de frequência de _page fault_** define uma taxa de falhas aceitável - se for demasiado baixa implica perda de _frames_, se for demasiado alta implica ganho de _frames_.

Se um processo não tiver páginas válidas (_frames_) suficientes, a taxa de falhas de páginas pode ser muito alta, havendo baixa taxa de utilização do CPU, aumentando o grau de multiprogramação e adicionando outro processo ao sistema. No **_thrashing_**, os processos estão ocupados na troca de páginas, não fazendo qualquer trabalho.

Outras utilizações de memória virtual são:
* **COW** (_Copy On Write_) - processos pai e filho partilham as mesmas páginas de memória; se qualquer dos dois processos altera dados numa página partilhada, então a página é copiada, ficando cada processo com uma cópia própria. Os processos são criados de forma mais eficaz e rápida e as páginas livres são alocadas de um conjunto de páginas livres mantido pelo sistema operativo;
* **MMF** (_Memory Mapped Files_) - processos são tratados como rotinas de acesso à memória mapeando blocos do disco a páginas em memória. Um ficheiro é inicialmente lido com _demand paging_, em que uma parte do ficheiro do tamanho de uma página é lido do sistema de ficheiros para uma _frame_ e qualquer leitura/escrita subsequente é tratada como acesso à memória, permitindo a partilha de um ficheiro entre múltiplos processos pelas páginas em memória;
* **Seleção de tamanho de página** - determinação do tamanho de página a utilizar, fornecendo a possibilidade ao administrador de alterar o tamanho da página e de ter múltiplos tamanhos diferentes, de modo a permitir a otimização de tamanho pelas próprias aplicações, não havendo aumento significativo de fragmentação;
* **Bloqueio de I/O** - as páginas são fechadas (_locked_) em memória e não podem ser retiradas;
* **Localidade**.