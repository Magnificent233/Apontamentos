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

## Aula Prática 1

**Bash Shell** (_Born Again Shell_), **SH Bourne Shell** (_Bourne Shell_), **CSH**, **TCSK** são CLI (_Command Line Interpretor_) do sistema operativo Linux.
GUI (_Graphical User Interface_).

LOOP
    leitura de comandos (ambiente gráfico -> cliques) (CLI -> instruções escritas)
    interpretação
        parsing
        ação
            execução de novos comandos que o sistema operativo pode encontrar
            funcionalidade do próprio programa _shell_ (embutida)

EDITORES
    linha a linha : `ed`
    screen based : `vi emacs`
    complex screen based : `vim xemacs`
    graphics : `gedit` `notepad` `notepad++`
    ides: `netbeans` `intellij` `vscode` `vspro`

Tudo em Linux é um ficheiro (ficheiros 'normais', pastas, _sockets_, discos, periféricos).

`man`
página 1 -> bash
página 2 -> linux sys calls
página 3 -> c standard library