# Programação de Dispositivos Móveis

##### Atualizado em 26-12-2021
###### A partir de: sebenta; exercícios das aulas práticas

## Aulas Teóricas

### Aula 01

**Interface** - programa de computador que permite que o utilizador comunique com esse computador ou com partes do programa.

**Programação direcionada a eventos** - evento > gatilho > manipulador de eventos > ciclo de eventos. Um evento corresponde a uma ação que um programa foi capaz de detetar e tratar. A interface gráfica é composta por vários objetos interativos e elementos cuja localização é conhecida, estruturados hierarquicamente em árvore.

**Modelo de delegação de eventos** - controlos (fontes do evento); consumidores (_listeners_, rotinas de tratamento do evento); interface (forma normalizada de comunicação). O programador deve definir os controlos e registar o conjunto de eventos que deseja escutar, bem como implementar a interface.

Os objetos interativos são conhecidos por **_widgets_** ou **controlos**, com uma representação gráfica semelhante ao que conhecemos de outros dispositivos usados no quotidiano. Os **contentores** são elementos que podem conter outros contentores ou objetos interativos, permitindo organizar o aspeto gráfico da aplicação.

Os eventos gerados dependem normalmente do contexto do objeto interativo e aqueles que vão ser efetivamente tratados dependem dos objetivos da aplicação. O **_handler_** recebe o próprio objeto interativo como parâmetro de entrada; o objeto interativo onde o evento é gerado é designado por **fonte**. Objetos interativos costumam ter acesso aos métodos de outros objetos no mesmo nível hierárquico ou acima, cuja comunicação se faz por:
* Manipulação direta de propriedades de outros objetos;
* Aviso ao elemento imediatamente acima na hierarquia;
* Geração de novos eventos.

A arquitetura **modelo-visão-controlador** (MVC) é um modelo de arquitetura para desenvolvimento de _software_ que separa a lógica da aplicação, a representação da informação e a interação do utilizador. O objetivo é favorecer a sua escalabilidade e manutenção, bem como a portabilidade e reutilização de código com um maior grau de abstração.
* **Modelo** - componente central; encapsula o estado interno, implementa objetos, métodos ou rotinas que capturam o comportamento base da aplicação de forma concisa, segura e uniformizada e acede e manipula base de dados. Só pode interagir com o controlador, sendo completamente independente da interface - o utilizador nunca interage diretamente. As implementações devem ser o mais genéricas possível na representação dos dados, contudo, a interface de programação deve ser clara e consistente;
* **Visão** - possível representação dos dados da aplicação; define as interfaces (podendo haver várias representações para o mesmo conjunto de dados), que podem ser desenvolvidas em pararelo e melhoradas ao longo do tempo;
* **Controlador** - intermediário entre o modelo, a visão e o utilizador, com rotinas de captura e reencaminhamento de eventos, atualização de objetos da visão e despoletação de mudanças no estado da aplicação através de instruções enviadas para o modelo; responsável pela coordenação de tarefas de uma aplicação ou a gestão do ciclo de vida de objetos.

![](https://i.imgur.com/KHfhYm5.png)

Como não existe comunicação direta entre o _modelo_ e as _visões_, qualquer alteração que precise de ser refletida na interface tem de ser comunicada ao _controlador_ por uma notificação que contenha os dados necessários.

---

### Aula 02

Uma pilha de _software_ contém várias camadas e é desenhada para permitir a construção e execução de aplicações móveis:
* Serviços base - arquitetura de permissões, gestão de memória e processos, suporte a comunicações entre processos, operações de baixo nível de escrita e leitura em ficheiros, comunicações em rede; _drivers_ para suporte de dispositivos de _hardware_ adicionais (câmaras fotográficas, antenas de rádio, sensores);
* Bibliotecas nativas - implementadas em C/C++, para atualizar o ecrã, renderizar páginas _web_, gerir bases de dados, lidar com áudio e vídeo;
* _Android Runtime_ - bibliotecas Java fundamentais, máquina virtual; aplicações compiladas para _bytecode_;
* _Framework_ de aplicações - recursos utilizáveis, provedores de conteúdo (bases de dados para armazenamento e partilha de informações do sistema), gestores de pacotes (registo de todas as aplicações instaladas no sistema), atividades (coordenação e suporte de navegação entre atividades e ciclos de vida), janelas, localização e notificações;
* Aplicações - aplicações de fábrica, em desenvolvimento (_debug_) ou desenvolvidas por terceiros; é com esta camada que o utilizador final interage.

A virtualização permite obter vantagens na economia, versatilidade, confinamento, mas pode ter desvantagens de desempenho, funcionalidades em falta.

---

### Aula 03

Uma aplicação AndroidTM é constituída sobre quatro blocos fundamentais:
* **Atividades** - permitem a construção de interfaces de utilizador gráficas, para manipulação, adição ou obtenção de informação de uma aplicação. Uma atividade deve corresponder a uma única ação ou interação que um utilizador pode fazer. Uma aplicação com mais do que uma funcionalidade deve possuir mais do que uma atividade.
    * `super.onCreate(savedInstanceState)` recupera o estado em que a aplicação foi parada que foi guardado no `bundle`, que depois é construída com a instrução `setContentView(R.layout.main)`;
* **Serviços** - permitem executar operações de longa duração em segundo plano, despoletados por outra componente, continuando a fornecer funcionalidades mesmo que se mude de atividade ou aplicação;
* **Fornecedor de Conteúdos** - fornecem conteúdos estruturados a aplicações AndroidTM, permitindo que as aplicações comuniquem entre si ou usem dados que são partilhados por todo o sistema. O `ContentResolver` é a interface que verifica se a aplicação tem os privilégios necessários para aceder ao fornecedor de conteúdos, caso positivo, envia o pedido para o fornecedor de conteúdos respetivo;
* **Recetores de Difusão** - escutam e processam eventos, permitindo que determinada aplicação se registe no sistema como capaz de lidar com determinado evento e, quando esse evento acontece, seja chamada pelo sistema operativo para o processar.

Durante o processo de preparação da aplicação, alguns ficheiros do projeto são compilados e empacotados juntamente com outros recursos num arquivo `.apk`, que contém os ficheiros `.dex` (ficheiros `.class` compilados para o _byte code_ específico da máquina), uma versão binária do `AndroidManifest.xml`, os ficheiros com metadados acerca dos recursos `resources.arsc` e também todos os recursos que a aplicação usa em formato original.

A classe `R` contém a definição de várias classes estáticas (como `id` e `string` que permitem acesso facilitado a recursos da diretoria `res`). É gerada pela ferramenta `aapt` (_Android Asset Packaging Tool_).

O ficheiro `AndroidManifest.xml` é uma estrutura fundamental em todas as aplicações AndroidTM, que apresenta informação essencial acerca da aplicação ao sistema para que este a possa executar. Indica o nome do pacote Java (identificador único no sistema); enumera as várias atividades, serviços, recetores de difusão e fornecedores de conteúdos; indica o nome de todas as classes que implementam as componentes supracitadas e as suas capacidades; declara as permissões da aplicação para acesso a partes protegidas ou interação com outras aplicações; declara as permissões que outras aplicações precisam de ter para aceder às suas funcionalidades; identifica a API mínima requerida; lista eventuais bibliotecas necessárias.

Uma **tarefa** é um conjunto ordenado de atividades que um utilizador percorre para obter determinada funcionalidade no contexto de uma aplicação AndroidTM. Uma aplicação pode ter várias tarefas, e nem todas as atividades de uma determinada tarefa pertencem à mesma aplicação. O sistema contém um conjunto de mecanismos que ajudam o utilizador a navegar pelas diversas atividadse (por exemplo, pilha de retrocesso de tarefas (_Task Backstack_)) e gere automaticamente o ciclo de vida das atividades, garantindo que estas são devidamente inicializadas, suspendidas ou retomadas, bem como destruídas em caso de falta de memória.

Uma atividade pode estar **ativa**/**em execução** (se estiver totalmente visível em primeiro plano); **pausada** (parcialmente visível, mantém o estado e continua ligada ao gestor de janelas); **parada** (se estiver completamente tapada por outra atividade). Quando pausada ou parada, pode ser destruída para colmatar problemas de memória. Métodos:
* `onCreate()` - chamado quando a atividade é criada pela primeira vez, com configuração estática (criação ou ajuste da interface de utilizador, colocação de lógica aplicacional para lidar com eventos e recuperação do estado anterior);
* `onStart()` - chamado quando a atividade está próxima de ficar visível, ideal para colocar código que reajuste o estado da aplicação com dados provenientes de sensores ou guardados no sistema;
* `onResume()` - despoletado quando a atividade está a transitar de um estado invisível ou tapado para o primeiro plano, com instruções para inicializar e correr animações ou toques. Depois de executar, a atividade fica em estado de execução e o utilizador pode interagir com ela;
* `onPause()` - despoletado quando a atividade está a perder o foco, usado para guardar dados persistentes que a atividade esteja a editar, gerir a paragem de animações e outras operações que exijam recursos de computação para agilizar a transição para a nova atividade, ou fechar recursos externos;
* `onStop()` - chamado quando a atividade já não está visível para o utilizador para _caching_ de alguns dados caso a atividade seja retomada. Atividades paradas têm uma maior probabilidade de serem terminadas por falta de memória e o método não deve ser utilizado para guardar estados;
* `onRestart()` - chamado apenas quando uma atividade foi colocada em segundo plano e o utilizador volta a navegar para a mesma, com código que permite recuperar dados que tenham sido guardados;
* `onDestroy()` - invocado quando a atividade está para terminar normalmente, com libertação de recursos computacionais (_threads_), podendo não ser chamado caso a atividade seja terminada de modo abrupto, pelo que não deve conter funcionalidades críticas.

---

### Aula 04

Um **intento** é a manifestação de uma intenção de fazer uma ação, encapsulado pelo objeto `intent`, que pode ser: executada por uma componente da aplicação ou de outra, capturada pelo sistema operativo e entregue a uma de várias componentes aptas para a executar ou descartada. O `intent` pode lançar uma nova atividade (`startActivity(Intent)`, `startActivityForResult(Intent)`), executar serviços (`startService(Intent)`, `bindService(Intent, ServiceConnection, int`), emitir _broadcasts_ (`sendBroadcast()`, `sendOrderedBroadcast()`, `sendStickyBroadcast()`).

Quando um componente de uma aplicação quer começar outro componente, instancia um intento e envia-o para o sistema, que fica responsável por identificar, verificar as suas permissões e, em caso de encontrar o seu destino e ser permitido, de o enviar para execução. O `intent` é composto por:
* Nome do componente destino - opcional, distingue intentos explícitos (contêm nome) de implícitos (não contêm nome);
* Ação a efetuar - especificada normalmente através de uma _string_ predefinida, que é obrigatória caso o nome do destinatário não seja indicado;
* Dados - _Uniform Resource Locator_ (URL) e _Multi-Purpose Internet Mail Extensions_ (MIME) para que aponta;
* Categoria - _string_ que indica o tipo de componente;
* Extras - pares chave-valor para transferir dados adicionais;
* _Flags_ - metadados para o objeto para instruir o sistema sobre como deve lançar ou manipular as atividades ou serviços por ele lançados.

Um **intento explícito** especifica univocamente a componente que deve ser despoletada pelo seu nome no sistema operativo (pacote e nome de classe), usado para despoletar outra componente da própria aplicação ou quando se sabe o nome da classe ou atividade destino. Quando um intento explícito é criado, o sistema operativo despoleta a atividade ou serviço indicados imediatamente.

Um **intento implícito** indica a ação genérica a executar e, se disponíveis, dados adicionais para a sua realização. Para encontrar uma componente apropriada, o sistema operativo compara o conteúdo do intento com os filtros de intentos: se apenas uma correspondência for encontrada, a componente respetiva é despoletada; se não, é mostrada uma caixa de diálogo ao utilizador, que deve escolher interativamente qual deverá tratar a ação.

---

### Aula 05

Uma das bases da **arquitetura de segurança** do AndroidTM consiste na assunção de que uma aplicação, por defeito, não tem permissão para executar operações que possam ter impacto adverso noutras aplicações, no sistema operativo ou no utilizador. Cada aplicação tem de explicitamente pedir permissões para utilizar recursos não fornecidos de forma nativa pela _sandbox_ em que é executada. As **permissões** são declaradas estática e explicitamente no manifesto da aplicação, e o sistema pede o consentimento ao utilizador para o usufruto dos recursos aquando da instalação ou durante a execução.

Durante o processo de instalação de uma aplicação, o sistema operativo atribui-lhe um identificador de utilizador que é único nesse dispositivo. Como o núcleo Linux garante o controlo de acesso ao nível dos processos, assegura-se que determinada aplicação não pode aceder aos recursos de outra diretamente ou que corram no mesmo processo. Após instalada, geralmente, todos os dados guardados por determinada aplicação ficam associados ao ID que lhe é atribuído.

Os arquivos `.apk` de uma aplicação têm de ser assinados digitalmente para serem aceites pelo sistema operativo, num certificado que pode ser auto-assinado e identifica univocamente o autor da aplicação, de modo a que o sistema forneça ou negue o acesso de uma aplicação aos recursos ou componentes de outra.

Por defeito, não são dadas quaisquer permissões a aplicações AndroidTM: o sistema veda acesso a todos os recursos que estão para além daqueles incluídos no processo ou criados pela própria aplicação, a menos que se faça um pedido explícito no ficheiro `AndroidManifest.xml`. O pedido é feito através da colocação de uma ou mais _tags_ `<uses-permission>`, cujo atributo `android:name` especifica o recurso a que se quer ter acesso.

O **atributo** `protectionLevel` é necessário e caracteriza o risco associado a uma permissão:
* `normal` - permissão sem impacto para o utilizador ou para o sistema, podendo ser dada automaticamente aquando da instalação;
* `dangerous` - permissão para dados pessoais do utilizador ou recursos mais sensíveis do sistema;
* `signature`, `signatureOrSystem` - permissão apenas a outras aplicações assinaladas com o mesmo certificado ou a aplicações de sistema.

A permissão mais específica sobrepõe sempre a menos específica. O **nome** da permissão é usado para a identificar de forma única em todo o sistema e para especificar a que componentes se aplica no atributo `android:permission` dos elementos:
* `<activity>` - **permissões aplicadas a uma atividade**, restringem que componentes é que a podem despoletar;
* `<service>` - **permissões aplicadas a um serviço**, restringem quem pode começar ou associar-se ao mesmo;
* `<receiver>` - **permissões aplicadas a recetores de difusão**, restringem quais as aplicações que podem enviar eventos para esses recetores, validada após o método `sendBroadcast()` devolver, já que é o sistema que faz a tentativa de entrega ao recetor e o emissor tem de esperar pelo retorno do sistema;
* `<provider>` - **permissões aplicadas a fornecedores de conteúdos**, restringem o acesso a determinados conteúdos.

---

### Aula 06

A gestão e armazenamento de dados de forma persistente é possível no AndroidTM através de:
* **Recurso `SharedPreferences`** - guarda dados primitivos em pares chave-valor:
    * Um objeto é instanciado pelos métodos `getSharedPreferences (string, int)` (caso se pretenda dar um nome ao ficheiro de preferências ou obter o ficheiro previamente guardado) ou `getPreferences (int)` (caso se utilize um ficheiro por defeito);
    * A leitura é feita por `getBoolean (string, boolean)` ou `getInt (string, int)`. Pela `string` (chave) devolvem o respetivo valor ou o tipo definido no segundo parâmetro caso a chave não exista;
    * A escrita é feita por um segundo objeto `Edit` através do método `edit()`, que disponibiliza vários métodos com prefixo `put` (`putBoolean (string, boolean)`, `putInt (string, int)`) para guardar pares no objeto. Os pares só são guardados no ficheiro após os métodos `apply()` ou `commit()`;
* **Armazenamento interno** - guarda dados na memória persistente do dispositivo:
    * Ficheiros são abertos e guardados pelo método `openFileOutput (String, int)`, cujos parâmetros são nome do ficheiro e modo de acesso, e são apagados aquando da desinstalação da aplicação. Há quatro modos de operação:
        * `MODE_PRIVATE` (valor 0) - método sugerido por defeito, define que apenas a aplicação que criou o ficheiro ou todas aquelas que partilhem o mesmo ID lhe podem aceder;
        * `MODE_WORLD_READABLE` (valor 1) - define que o ficheiro pode ser acedido para leitura por qualquer aplicação;
        * `MODE_WORLD_WRITEABLE` (valor 2) - define que qualquer aplicação pode aceder ao ficheiro;
        * `MODE_APPEND` (valor 32768) - determina que a escrita de dados novos no ficheiro deve ser feita no final, caso este já exista;
    * A escrita é possível por `write (int iByte)`, `write (byte[])`, `write (byte[] buffer, int offset, int count)`. Os ficheiros devem ser fechados após serem alterados, pelo método `close()`, e podem ser manipulados também pelos métodos:
        * `getFilesDir()` - devolve o caminho absoluto da diretoria;
        * `getDir (string, int)` - cria a diretoria com o nome definido no primeiro parâmetro;
        * `deleteFile (string)` - elimina o ficheiro cujo nome é passado em parâmetro;
        * `fileList()` - devolve um vetor de _strings_ com o nome de todos os ficheiros já guardados na aplicação;
    * A leitura é possível pela instanciação de um `FileInputStream` invocado pelo método `openFileInput (string)`, sendo depois lido por `read()`;
    * A cache guarda ficheiros temporariamente, que são eliminados em caso de escassez de recursos de armazenamento do sistema;
* **Armazenamento externo** - guarda dados públicos na memória persistente partilhada e externa:
    * Os ficheiros são `world-readable`, permitindo a sua alteração por outro dispositivo computacional compatível, requerendo uma verificação para a sua existência ou disponibilidade pelo método `getExternalStorageState()`. Para que uma aplicação tenha acesso ao armazenamento externo, é necessário normalmente pedir essa permissão no `AndroidManifest.xml` (versões anteriores à 4.4). Se os ficheiros forem guardados numa diretoria da aplicação (por exemplo, `getExternalFilesDir (null)`), serão eliminados aquando da desinstalação da aplicação, no entanto, tal não determina necessariamente que outras aplicações (com as devidas permissões) ou o utilizador não os possam manusear;
* **Base de dados SQLite** - armazenamento e acesso eficiente de dados estruturados em bases de dados privadas:
    * SQLite é uma biblioteca de _software_ que implementa um motor de bases de dados SQL que não necessita de configurações para o uso. Cada base de dados é guardada num único ficheiro e pode ser manipulada, consultada e gerida pela linha de comandos, havendo a possibilidade de ser compilada e embutida no executável de uma aplicação. É uma linguagem declarativa: as instruções definem o que deve ser feito, não como deve ser feito (exemplos nas páginas 6 e 7 do pdf do professor). Tem total suporte para transações **ACID**:
        * _Atomicidade_ - uma transação é realizada completamente ou não é realizada;
        * _Consistência_ - a execução de uma transação preserva a consistência da base de dados;
        * _Isolamento_ - as atualizações feitas por várias transações concorrentes produzem o mesmo efeito que se fossem executadas em série;
        * _Durabilidade_ - as alterações nunca se perdem mesmo na ocorrência de falhas;
    * As bases de dados são criadas recorrendo ao método `onCreate`, através de _software_ dos pacotes `android.database` ou `android.database.sqlite`, que é executado apenas da primeira vez que uma base de dados é criada;
* **Acesso à rede** - armazenamento e gestão de dados remotos.

---

### Aula 07

Atividades em segundo plano são conseguidas através de quatro formas distintas: classe `Thread`, para processamento assíncrono; classe `Handler` que permite definir um manípulo na *thread* principal para o qual se podem enviar mensagens ou código para ser executado; classe `AsyncTask`; classe `Service`.

Um **serviço** é uma forma de anunciar o desejo de uma aplicação AndroidTM executar uma operação demorada sem interação com o utilizador ou de fornecer funcionalidades a outras aplicações. Um serviço corre no mesmo processo da aplicação e não tem uma interface de utilizador. Enquanto que as *threads* criam módulos de execução separados dentro do mesmo processo, os serviços declaram ao sistema que determinada tarefa deve continuar, ainda que outros processos ou aplicações sejam trazidos para primeiro plano.
* **Serviços sem vínculo** (`started`) - colocados em execução por outro componente através do método `startService()`, que podem correr indefinidamente em segundo plano, mesmo que o componente que os colocou em execução seja destruído; fazem apenas uma operação sem devolução de resultados, devendo autoterminar-se;
* **Serviços com vínculo** (`bound`) - colocados em execução através do método `bindService()`, definem uma interface que permite que outros componentes da mesma aplicação, ou de aplicações diferentes, interajam com o serviço enviando pedidos e recebendo resultados; executam enquanto tiverem componentes vinculadas.

O ciclo de vida de um serviço começa pela invocação de `onCreate()`, onde deve ser feita a configuração inicial da instância do componente. O período da atividade do ciclo de vida de um serviço começa com a invocação de um dos métodos `onStartCommand(.,.,.)` ou `onBind()`, a quem é automaticamente entregue o intento que invocou o serviço e onde devem ser tomadas as providências necessárias para que as tarefas que definem o serviço sejam desempenhadas. O serviço deve ser declarado no `AndroidManifest.xml`, com a *tag* `<service>` contendo o nome e alguns filtros de intentos (usados pelo sistema para encontrar componentes capazes de lidar com determinada ação). O método `onStartCommand (.,.,.)` termina com um retorno:
* `START_NOT_STICKY` define que caso o serviço seja morto pelo sistema enquanto está no estado ativo, este não deve voltar a tentar criá-lo se puder;
* `START_STICKY` define que o sistema deve tentar recomeçar um serviço que matou logo que tenha recursos para o fazer, chamando o método `onStartCommand(.,.,.)` de novo, mas sem o intento;
* `START_REDELIVER_INTENT` indica ao sistema que este deve guardar o intento antes de o matar para que o possa utilizar para recriar o serviço.

A classe `IntentService` permite criar uma *thread* separada da principal para executar todos os intentos entregues na `onStartCommand()`, criando uma pilha de trabalho que permite lidar com os vários intentos passados de forma sequencial. O método `stopSelf()` é invocado por defeito assim que todas as tarefas tenham sido concluídas. É apenas necessário reescrever o método `onHandleIntent()` e implementar o construtor que invoca o seu análogo da super classe, fornecendo-lhe um nome para a *thread* que é criada.

Ao definir um vínculo, o serviço toma o papel de servidor e a componente que o invoca toma o papel de cliente. Um vínculo define-se ao:
* Estender a classe `Binder`, aplicável em situações em que o serviço é apenas usado pela própria aplicação e corre no mesmo processo do cliente:
    * No serviço, deve ser instanciado um objeto da classe `Binder` que contém métodos públicos que o cliente poderá usar, ou devolve uma instância de outra classe cuja definição está contida na do serviço e que contém métodos públicos que o cliente pode invocar, ou devolve a própria instância do serviço atual, permitindo que o cliente invoque os seus métodos públicos;
    * No serviço, deve devolver-se a instância da classe `Binder` no método *callback* `onBind()`;
    * No cliente, deve receber-se o `Binder` da função *callback* `onServiceConnected()`, bem como instanciar um objeto local da mesma classe do objeto instanciado no `Binder` e tirar partido dos métodos públicos por ele fornecidos;
* Combinar objetos das classes `Messenger` e `Handler`, em que um manípulo é criado num serviço e um conjunto de mensagens a tratar é definido programaticamente no seu código, sendo também possível criar um destes objetos e enviá-lo via mensagem ao serviço, para que este lhe possa enviar retorno (*InterProcess Communication*, IPC);
* Usar *Android Interface Definition Language* (AIDL) para definir interfaces que determinado serviço quer expor a clientes; deve ter-se em consideração que não é garantido que as chamadas aos vários métodos da interface sejam feitas na *thread* principal, pelo que o serviço deve ser implementado de forma a ser *thread-safe* (a execução concorrente de várias operações que acedem aos mesmos recursos não incorrem em estados de inconsistência no estado da aplicação).

Apenas atividades, serviços e provedores de conteúdos se podem vincular a um serviço (recetores de conteúdos não o podem fazer).

Enquanto que os serviços sem vínculo devem ser explicitamente terminados, quer dentro do próprio serviço ou por outra atividade, os serviços com vínculo não precisam de ser explicitamente terminados, desde que se garanta que é feita a sua desvinculação, uma vez que o sistema mata automaticamente e com maior facilidade serviços que não têm qualquer vínculo. Um serviço `started` pode ser terminado pelos métodos `stopSelf()` (por si próprio) ou `stopService(Intent)` (pela componente que o despoletou); um serviço `bound` pode ser terminado pelo método `unbindService(.)`. Quando um componente cliente é destruído pelo sistema, também é automaticamente desvinculado de qualquer serviço ao qual tenha sido vinculado. Se a interação com o serviço só precisa de acontecer enquanto uma atividade está visível, a vinculação e desvinculação devem ser feitas nos métodos `onStart()` e `onStop()`, respetivamente; caso se queira que a atividade receba respostas do serviço mesmo enquanto está parada em segundo plano, então o serviço pode ser vinculado no método `onCreate()` e desvinculado no método `onDestroy()`.

Um ***toast*** é um objeto interativo (*widget*) direcionado à exibição de mensagens curtas ao utilizador. Se despoletada por um serviço, a *view* é mostrada sobre a interface de utilizador da aplicação atualmente em execução. Uma **notificação** na barra de estados é um objeto algo elaborado que permite interação e tem necessariamente de transmitir uma ideia ao utilizador da forma mais eficiente possível. Uma notificação é criada através do método `build()` e imediatamente passada ao gestor de notificações do sistema pelo método `notify()`. Para inserir ações nas notificações, deve ser usado um objeto da classe `PendingIntent` que, quando é despoletado por outro componente, é executado como se viesse da aplicação original com as suas permissões.

---

### Aula 08

Um **recetor de difusão** permite que as aplicações se registem para receber eventos provenientes do sistema ou de outra aplicação. Os eventos também podem ser representados por intentos: chegam a todas as aplicações com recetores registados para receber determinados eventos e nunca atingem filtros de componentes. A emissão pode ser feita por qualquer aplicação do sistema, embora possa requerer o pedido de algumas permissões no manifesto. Recetores podem ser registados de forma **estática**, incluindo uma *tag* `<receiver>` no manifesto, ou **dinâmica**, no código da implementação de um dos outros componentes de uma determinada aplicação pelo método `registerReceiver()`.

Um **recetor estático** é registado aquando do arranque do sistema AndroidTM ou logo que um pacote é instalado. Quando um evento/intento representando uma das ações definidas nos filtros é despoletado, o sistema AndroidTM entrega esse intento a todos os recetores registados e autorizados através da invocação do método `onReceive`. Um **recetor dinâmico** é programado pelos métodos `registerReceiver(.,.)`, que aceita o recetor de difusão a registar e o filtro de intentos a escutar, e `unregisterReceiver(.)`, que aceita apenas o objeto recetor de difusão cujo registo deve ser eliminado. A classe `IntentFilter` permite a definição dinâmica de filtros de intentos.

Intentos em difusão **não ordenados** são enviados através do método `sendBroadcast(.)`, que aceita o intento a enviar como parâmetro de entrada, e entregues pelo sistema AndroidTM a todos os recetores que estejam registados para os receber, sem qualquer ordem; ou seja, o método é **assíncrono**, regressando imediatamente à componente que o chamou depois de ser entregue ao sistema, não permitindo que sejam recebidos resultados da execução dos recetores ou abortar determinado intento. Intentos em difusão **ordenados** são enviados através do método `sendOrderedBroadcast(.,.)`, que aceita o intento a enviar e uma *string* como parâmetros de entrada, e entregues pelo sistema AndroidTM a todos os recetores que estejam registados para os receber, por uma ordem particular definida no manifesto pelo atributo `android:priority="integer"` na *tag* `intent-filter`; também é **assíncrono**, mas permite que um recetor ajuste dados que são enviados com o intento para outros recetores antes que eles recebam o intento e também abortar o intento antes de este chegar a outros recetores com prioridade inferior.

---

### Aula 09

**Provedores de conteúdo** permitem gerir o acesso a um repositório de dados de uma determinada aplicação, direcionados sobretudo a aplicações diferentes daquelas que os criam, ou seja, permitem controlar de forma consistente e central o acesso a recursos que deveriam ser privados, oferecendo uma interface padrão para aceder aos dados que lida automaticamente com comunicação entre-processos e segurança no acesso aos dados. A criação de um provedor de conteúdos é um processo algo elaborado, porque se deve comportar como uma fase de análise da real necessidade de o implementar, a modelação e estruturação de dados e a implementação em si. É necessário: modelar a forma como os dados são armazenados e implementar a lógica necessária para os criar; definir uma *string* que determina, de forma unívoca no universo AndroidTM, o provedor de conteúdos a implementar; implementar a classe `ContentProvider`, reescrevendo alguns dos seus métodos; declarar o novo componente no manifesto e definir as permissões necessárias.

**URI**'s (*Uniform Resource Identifier*) são recursos muito poderosos, podendo ser usados para determinar desde o provedor de conteúdos até à linha da tabela que se quer obter. O tratamento do URI num provedor de conteúdos significa decompô-lo em várias partes e lidar com elas caso a caso. Um URI é decomposto em `<standard_prefix>://<authority>/<data_path>/<id>`:
* `<standard_prefix>` determina o protocolo ou tipo de recurso;
* `<authority>` determina unicamente o recurso a que se quer aceder;
* `<data_path>` especifica a parte do recurso a que se quer aceder;
* `<id>` transporta parâmetros para a parte do recurso especificado.

---

### Aula 10

Os **sensores** podem ser: de **movimento** (medem forças de aceleração e rotação em três eixos); de **ambiente** (medem parâmetros como pressão do ar, humidade, iluminação); ou de **posicionamento** (medem a posição física dos dispositivos). Para aceder a sensores, é necessário declarar um objeto da classe do gestor, pedir a instância do gestor ao sistema e aceder a funcionalidades disponibilizadas pelo gestor. Os sensores podem ser *hardware-driven* (derivados diretamente de um dispositivo físico) ou *software-driven* (derivados de um ou mais dispositivos físicos, que podem ser tratados antes de devolvidos).

A *framework* dos sensores permite: determinar que sensores estão disponíveis no dispositivo, obter as capacidades de cada sensor, adquirir os dados em bruto e definir a cadência com que devem ser adquiridos, registar ou eliminar o registo de *listeners* para determinado tipo de eventos:
* `SensorManager` - classe que encapsula os métodos que podem ser usados para interagir com o gestor em execução, constituindo o ponto de partida para aceder e listar sensores;
* `Sensor` - classe que permite criar uma instância de um sensor específico e verificar as suas características através de métodos específicos;
* `SensorEvent` - classe que permite obter valores em estado bruto de determinado sensor (valores, tipo, precisão e momento);
* `SensorEventListener` - interface que pode ser implementada para receber eventos quando os valores ou a precisão dos sensores mudam.

A obtenção de valores de sensores requer sempre que se registe um *listener* para o sensor do tipo desejado, através do método `registerListener(.,.,.)`, que aceita três parâmetros: um objeto da classe que implementa `SensorEventListener`, o objeto da classe `Sensor` e um inteiro, que determina a frequência com que o sistema deve tentar entregar os eventos do sensor à aplicação. O método `onAccuracyChanged(.,.)` recebe dois parâmetros (um objeto da classe `Sensor` e um inteiro que informa a nova precisão) e é invocado sempre que a precisão do sensor é alterado. O método `onSensorChanged(.)` recebe apenas um parâmetro (um objeto da classe `SensorEvent`) e é invocado quando o sensor reporta novos valores.

A classe `SensorEvent` não disponibiliza qualquer método além dos que herda da superclasse `Object`, contudo, todos os seus atributos são públicos: `accuracy` (inteiro que determina a precisão da captura), `sensor` (objeto da classe `Sensor` que identifica o sensor onde se deu a captura), `timestamp` (inteiro que representa o momento, em nanossegundos, da captura) e `values` (vetor de decimais com os valores da captura).

---
---

## Aulas Práticas

### Aula 01

**Questão 01: O que significa, para si, IDE?**

_Resposta:_ _Integrated Development Environment_.

**Questão 02 - E o acrónimo SDK, é abreviatura de quê?**

_Resposta:_ _Software Development Kit_.

**Questão 03 - Qual das seguintes opções define corretamente SDK?**

_Resposta:_ É um conjunto de ferramentas de desenvolvimento de software que permitem a criação de aplicações para um dado pacote, sistema de software, plataforma de hardware, computador, consola de jogos de vídeo, sistema operativo ou outra plataforma de desenvolvimento semelhante.

**Questão 04 - A Programação de Dispositivos Móveis é uma unidade curricular de que ano das licenciaturas em Engenharia Informática e em Informática Web?**

_Resposta:_ Terceiro ano.

**Questão 5 - No 3º ano da sua licenciatura em Engenharia Informática ou em Informática Web ainda precisa de ir à Internet ver o que é uma API?**

_Resposta:_ Claro que não. Claro que não, mas... vou só abrir o browser para ver o e-mail...

**Questão 06 - O que é uma API?**

_Resposta:_ _Application Program Interface_ é um conjunto de funções e procedimentos que permitem a criação de aplicações que acedem às características e dados de um sistema operativo, aplicação ou outro serviço.

**Tarefa 3** - AVD: _Android Virtual Device_.

**Questão 07 - Qual a versão mais recente já em utilização do SO `AndroidTM`?**

_Resposta:_ `AndroidTM 11.0`.

**Questão 08 - Por curiosidade, qual a versão mais recente, e atualmente em utilização, do iOS?**

_Resposta:_ `iOS 15`.

**Questão 09 - Já agora, escreve-se iOS ou IOS?**

_Resposta:_ Escreve-se, obrigatoriamente, iOS.

**Questão 10 - Existe algum SO chamado IOS (com o 'i' capitalizado)?**

_Resposta:_ Pois existe, que engraçado! `Internetwork Operating System`

**Questão 11 - Que esquema era esse?**

_Resposta:_ A designação de algumas versões do SO é constituída por um ou mais substantivos e faz sempre lembrar um doce. A primeira letra da designação segue o alfabeto.

**Q12 - Como se chama a versão mais recente, e em utilização, do SO `AndroidTM`?**

_Resposta:_ `Android 11`.

**Questão 13 - Como se chama a versão anterior à versão 10 do SO `AndroidTM`?**

_Resposta:_ Pie

**Questão 14 - (_Out of curiosity_,) Qual o ano em que foi lançado o AndroidTM pela primeira vez?**

_Resposta:_ 2008.

**Questão 15 - Qual é o núcleo base sobre o qual o SO AndroidTM foi construído?**

_Resposta:_ Linux.

**Questão 16 - Por curiosidade, qual é o núcleo base do iOS?**

_Resposta:_ Unix.

**Questão 17 - A versão do emulador coincide com a que definiu anteriormente, aquando da sua criação?**

_Resposta:_ Sim, coincide.

**Questão 18 - Assumindo que escolheu o modo _Project_, onde está contigo o código JAVA da aplicação?**

_Resposta:_ Na pasta `app/java`.

**Questão 19 - O que significa `src`?**

_Resposta:_ Já estou mais calma... significa _source_ (fonte)!

**Questão 20 - Assumindo que escolheu o modo _Project_, em que pasta está contido o ficheiro `AndroidManifest.xml`?**

_Resposta:_ Na pasta `app/manifests`.

**Questão 21 - Quais das seguintes informações pode definir neste ficheiro?**

_Resposta:_ O _layout_ da aplicação.

**Questão 22 - O que significa o X do acrónimo XML?**

_Resposta:_ _eXtensible_.

**Questão 23 - Qual o elemento raiz deste XML?**

_Resposta:_ `manifest`.

**Questão 24 - Quantos elementos raiz podem existir num XML bem formado?**

_Resposta:_ Só um.

**Questão 25 - Qual o elemento pai de `activity`?**

_Resposta:_ `application`.

**Questão 26 - O elemento `activity` tem algum elemento filho?**

_Resposta:_ Sim, tem, nomeadamente `intent-filter`.

**Questão 27 - De que forma é que é descrito o nome do pacote (_package_) no manifesto da aplicação?**

_Resposta:_ Em forma de atributo.

**Questão 28 - De acordo com o `manifest`, por quantas atividades é constituída a aplicação que acabou de criar?**

_Resposta:_ Uma.

**Questão 29 - O que é que isso significa? Consegue dizer exatamente o tema ou o _path_ (caminho) do ícone no disco?**

_Resposta:_ Sim, consigo: `/home/sara/AndroidStudioProjects/OlaMundo`.

---

### Aula 02

**Questão 01 - Para efeitos de registo, em que pasta fica o projeto criado pelo comando anterior?**

_Resposta:_ `/home/sara/AndroidStudioProjects/TestingGradle`.

**Questão 02 - O que é que esta instrução está a fazer exatamente?**

_Resposta:_ Está a especificar o valor da variável `ANDROID_HOME`.

**Questão 03 - Qual é a versão mais recente desta ferramenta de compilação?**

_Resposta:_ Versão 6+. (?)

**Questão 04 - Em que linguagem é que o GradleTM foi implementado?**

_Resposta:_ JAVA.

**Questão 05 - É possível usá-la para automatizar o processo de compilação e construção para outras linguagens?**

_Resposta:_ Sim, é.

**Questão 06 - Na expressão "construir uma aplicação AndroidTM" (e _grosso modo_), o que é que lhe parece significar a palavra construir?**

_Resposta:_ Compilar o código fonte, juntar e enumerar recursos, e empacotar binários, recursos e descrições, para além de outros artefactos.

**Questão 07 - (_Just for the sake of it_) Qual o símbolo do _gradle_?**

_Resposta:_ Um elefante.

**Tarefa 6** - `gradle` >> `NOTICE, LICENSE, etc.`, `bin`, `docs`, `initi.d`, `lib`, `media`, `samples`, `src`.

**Questão 08 - Em que diretoria é que está guardado o comando `gradle`?**

_Resposta:_ `bin`.

**Questão 09 - O que é que contém a diretoria `lib`?**

_Resposta:_ Contém ficheiros `.jar` relativos à implementação do GradleTM.

**Tarefa 6** - `Sdk` >> `build-tools`, `emulator`, `fonts`, `patcher`, `platforms`, `platform-tools`, `skins`, `sources`, `system-images`, `tools`, `.knowPackages`.

**Questão 10 - Em que pasta está a ferramenta `adb`?**

_Resposta:_ `platform-tools`.

**Questão 11 - Em que pasta pode ser encontrada a ferramenta `sdkmanager`?**

_Resposta:_ `tools/bin`

**Questão 12 - É possível encontrar uma _shell_ para bases de dados SQLite3 em alguma das diretorias antes enunciadas?**

_Resposta:_ Sim, é, nomeadamente na diretoria `platform-tools`.

**Questão 13 - Em que pasta pode ser encontrada a ferramenta `avdmanager`?**

_Resposta:_ Na mesma que a ferramenta `sdkmanager`. Na `tools/bin`.

**Questão 14 - Qual dos seguintes comandos é que lhe mostra quais as versões disponíveis no seu sistema?**

_Resposta:_ `./avdmanager list targets`.

**Questão 15 - Como traduziria o comando para português?**

_Resposta:_ `./avdmanager listar alvos`.

**Questão 16 - Já agora, e revisitando o tema da secção _Preliminares_, acha que é possível colocar um dispositivo virtual a correr sem abrir o Android Studio ou o AVD _Manager_?**

_Resposta:_ Sim. Navegando até à diretoria onde estão as ferramentas do Android SDK e usando o comando `emulator`: `cd Android/Sdk/emulator` > `./emulator -avd NOME_DISPOSITIVO`.

**Questão 17 - Como se chama esse ficheiro?**

_Resposta:_ `build.gradle`.

**Questão 18 - O que abrevia exatamente `apk`?**

_Resposta:_ `android package`.

**Questão 19 - Em que subdiretoria é que o arquivo resultante foi colocado?**

_Resposta:_ `app/build/outputs/apk/debug`.

**Questão 20 - Como se chama o arquivo resultante?**

_Resposta:_ `app-debug.apk`.

**Questão 21 - Acha que é possível instalar esta aplicação de teste num dispositivo comum com SO Android?**

_Resposta:_ Hum... Algo me diz que não!

**Questão 22 - O que é um arquivo?**

_Resposta:_ É um ficheiro composto por outros ficheiros e metadados.

**Questão 23 - Quais das seguintes palavras fazem parte da expansão do acrónimo ADB?**

_Resposta:_ Android Debug Bridge.

**Questão 24 - Qual o resultado deste comando?**

_Resposta:_ É exibido um _log_ do sistema virtualizado que se está a usar para testar a aplicação.

---

### Aula 03

**Questão 01: Qual das seguintes combinações lista todos os AVDs disponíveis com o comando `$emulador`?**

_Resposta:_ `emulator -list-avds`.

**Interface:** estrutura ou sintaxe de programação que permite ao computador impor determinadas propriedades num objeto (classe).

**Questão 02: Consegue aperceber-se da diferença entre uma interface de utilizador e uma interface entre duas componentes de um programa?**

_Resposta:_ Não. :-(  (?)

**Questão 03: Em que local pode o ficheiro mencionado ser encontrado?**

_Resposta:_ `src/main/res/layout`.

**Questão 04: Funcionou?**

_Resposta:_ Ehh... quer se me dizer... Instalar até instalou, mas está tudo assim: uma salganhada.

**Questão 05: Qual das seguintes deverá usar?**

_Resposta:_ `app:layout_constraintTop_toBottomOf`. (?)

**Questão 06: Não pergunta ao professor pelo significado do `@` e do `+` da propriedade `android:id`?**

_Resposta:_ Não, porque já sei tudo. `@` usa-se para referenciar qualquer objeto de recurso do XML; `+` usa-se para definir um valor que representa um novo objeto de recurso.

**Questão 07: Estes factos vão de encontro ao que foi referido em relação à arquitetura de _software_ MVC?**

_Resposta:_ De facto, isto parece ir ao encontro daquela arquitetura de desenvolvimento de _software_ na medida em que o controlo está separado do código da aplicação.

**Questão 08: Já se sabe que estará dentro da diretoria `src`, mas qual é o caminho completo do ficheiro a partir da raiz da aplicação?**

_Resposta:_ `app/src/main/java/pt/ubi/di/pdm/advancedcalculator`.

**Questão 09: Consegue encontrar a linha de código que carrega o _layout_ da aplicação a partir do ficheiro?**

_Resposta:_ Sim, é a linha com a instrução `setContentView (R.layout.activity_main);`.

**Questão 10: Porque é que cada vez que declara a função `findViewById(...)` necessita de colocar o nome de uma classe de um objeto entre parêntesis antes?**

_Resposta:_ A função devolve sempre um objeto mais geral, da classe `View`, que precisa ser convertido para a subclasse mais específica através de um _cast_.

**Questão 11: Agora sem olhar (!), consegue encontrar este ficheiro?**

_Resposta:_ Sim, algures dentro da pasta `src`.

**Questão 12: Qual o efeito desta alteração na interface de utilizador da aplicação?**

_Resposta:_ O botão passa a ocupar o máximo do ecrã na horizontal.

**Questão 13: Que nome se dá à classe criada pela instrução `new View.onClickListener ()`?**

_Resposta:_ Classe anónima.

**Questão 14: Já agora, só por curiosidade, o que significa URL?**

_Resposta:_ _Uniform Resource Locators_.

---

### Aula 04

**Questão 01: Só para relembrar: qual é o pacote que deve importar para usar objetos interativos como o botão?**

_Resposta:_ `android.widget.*`.

**Questão 02: Por curiosidade, qual é a classe pai (ou super classe) da classe `Button`?**

_Resposta:_ `android.widget.TextView`.

**Questão 03: Já agora, como se chama o cunhado do `Button`?**

_Resposta:_ ?

**Questão 04: A interface de utilizador que desenhou em cima é semelhante à que realmente apareceu?**

_Resposta:_ Ups, o resultado não ficou bem como eu tinha pensado que ia ficar. Vou já ver o que é que compreendi mal.

**Questão 05: Experimentou os botões?**

_Resposta:_ Experimentei, e não faziam nada, mas deviam fazer.

**Questão 06: A que conceito se refere a instrução `R.id`?**

_Resposta:_ A uma classe estática.

**Questão 07: Afinal, o que são os IDs que utiliza no código para referenciar alguns recursos de uma aplicação AndroidTM?**

_Resposta:_ São números inteiros.

**Questão 08: De uma maneira geral, esta abordagem parece-lhe mais simples que as que já foram estudadas até aqui?**

_Resposta:_ De facto, parece-me mais simples (legível).


**Questão 09: Este parâmetro é mesmo necessário?**

_Resposta:_ É sim. Sem ele, o _callback_ não funciona.

**Questão 10: Por curiosidade, em que versão da _Application Programming Interface_ (API) AndroidTM é que os botões foram disponibilizados?**

_Resposta:_ Na API 1.

**Questão 11: Como se chama a classe que lhe permite fazer isso?**

_Resposta:_ `Log`.

**Questão 12: Qual o pacote que terá de importar para poder usar a classe mencionada antes?**

_Resposta:_ `android.util.*`.

**Questão 13: Como é que se aplicam filtros no `logcat` via linha de comandos?**

_Resposta:_ Combinando a opção `-f` com `ALC`.

**Questão 14: Consegue simular um fluxo normal (completo) de execução no seu `logcat`?**

_Resposta:_ Claro que consigo.

![](https://developer.android.com/images/activity_lifecycle.png)

**Questão 15: Consegue simular o fluxo definido a seguir no seu `logcat`?**

_Resposta:_ Este está a oferecer resistência, mas penso que vou conseguir.

**Questão 16: Por curiosidade, o que é que acontece quando muda a orientação (e.g., de vertical (_portrait_) para horizontal (_landscape_)) do dispositivo, em termos do ciclo de vida de uma atividade?**

_Resposta:_ A atividade parece ter sido terminada e depois reiniciada!

---

### Aula 05

**Questão 01: Qual a aparência deste botão, em termos de altura?**

_Resposta:_ Vai ocupar o ecrã de cima a baixo.

**Questão 02: Em termos de disposição, onde se vai situar este botão?**

_Resposta:_ Ao centro.

**Questão 03: Só da análise do XML, diria que precisa de implementar algum método na atividade principal para que a aplicação funcione bem?**

_Resposta:_ Hum... parece-me que sim, nomeadamente o método com protótipo `sendMessage`.

**Questão 04: Este _import_ é mesmo necessário?**

_Resposta:_ Não percebo porque é que lá foi incluído.

**Questão 05: E o _import_ de `android.content.Intent`, é necessário?**

_Resposta:_ Indubitavelmente.

**Questão 06: Em que pacote/classe é que o método `setContentView()` está definido?**

_Resposta:_ `import android.app.Activity`.

**Questão 07: O que é que esta aplicação supostamente deve fazer?**

_Resposta:_ Enviar uma SMS.

**Questão 08: Porque é que o _intent_ que foi criado no âmbito desta parte do guia laboratorial é conhecido por intento implícito?**

_Resposta:_ Porque a atividade que vai tratar da ação especificada não é conhecida à partida.

**Questão 09: Só para que fique registado, o que é que acontece quando pressiona o botão _Send Message_?**

_Resposta:_ É mostrada uma caixa de diálogo onde é dada a hipótese de escolher qual a aplicação para onde o fluxo vai evoluir. A atividade onde estava fica desfocada no fundo.

**Questão 10: Esta assunção parece-lhe válida?**

_Resposta:_ Assim à primeira vista, não vejo porque não. Porque as instruções de definição de _layout_ são `wrap_content`, a posição predefinida será centrada na aplicação, contendo o título do botão.

**Questão 11: Só mesmo por curiosidade, como se chama a classe que implementa a atividade principal?**

_Resposta:_ Então: tem de se chamar, obrigatoriamente, `MainActivity`.

**_Imports_:** `import android.os.Bundle`, `import android.view.*`, `import android.content.Intent`, `import android.content.ComponentName`.

**Questão 12: Só para que fique registado, o que é que acontece quando pressiona o botão `Start Calculator`?**

_Resposta:_ É aberta a aplicação que gere as definições do sistema operativo (que estranho).

**Questão 13: O que é que significam as duas _strings_ neste trecho?**

_Resposta:_ A primeira é o nome do pacote da aplicação de gestão de definições que vem de fábrica com o AndroidTM; a segunda é o nome da atividade principal dessa aplicação.

**Questão 14: Quando usada como um adjetivo, como é o caso em `intento explicito`, a palavra _explícito_ deve ou não ser acentuada?**

_Resposta:_ Deve ser. A palavra _explícito_ leva acento quando é um adjetivo e não leva acento quando é uma forma verbal.

**Questão 15: A atividade desenvolvida envia dados para a atividade recetora do intento?**

_Resposta:_ Sim, nomeadamente o intento que vai realizar.

**Questão 16: O que é que pode concluir da observação do código?**

_Resposta:_ Que é instanciada uma `TextView` e depois preenchida com algo que vem dentro da `Intent`, nomeadamente numa variável geral com designação `string1`.

**Questão 17: Qual o ficheiro XML que define o _layout_ desta segunda atividade?**

_Resposta:_ `main2.xml`. É um ficheiro que ainda não existe.

**Tarefa 12:** `app/res/layout`.

**Questão 18: Da análise do código que antecede o XML, falta algum atributo em algum elemento incluído em cima?**

_Resposta:_ Sim, falta, e vou já tratar disso.

**Questão 19: Como é que se instancia um intento para uma atividade local?**

_Resposta:_ Através do construtor `Intent(Context, Class)`, que aceita o contexto da classe atual e o nome do componente destino.

**Questão 20: Funcionou?**

_Resposta:_ Como não podia deixar de ser. Ao clicar no botão `Start Second Activity`, este guarda no `intent` uma "variável" `string1` que depois é recebida na segunda atividade e enviada para o `textview`.

---

### Aula 06

**Questão 01: Onde (em que ficheiro) é que se criam os filtros de intentos?**

_Resposta:_ No `AndroidManifest.xml`.

**Questão 02: Dentro de que elemento é que deve ser colocado o filtro de intentos no ficheiro `xml`?**

_Resposta:_ Dentro do elemento `activity`.

**Questão 03: Qual dos seguintes excertos de código `xml` define corretamente o filtro de intentos?**

_Resposta:_
~~~
<intent-filter>
    <action android:name="android.intent.action.SEND"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <data android:mimeType="text/plain"/>
</intent-filter>
~~~

**Questão 04: Acha que vais precisar de alguns dos _imports_ seguintes?**

_Resposta:_ Vou, sim senhor. `import android.util.Log`.

**Questão 05: Das opções seguintes, quais concretizam formas de ver o `logcat`?**

_Resposta:_ `$ adb logcat`.

**Questão 06: A sua aplicação aparece na caixa de diálogo de seleção seguinte?**

_Resposta:_ Pois aparece, que engraçado.

**Questão 07: Qual o método que permite que a atividade principal chame a segunda de forma a que esta lhe devolva um resultado?**

_Resposta:_ `startActivityForResult (Intent, int)`.

**Questão 08: Qual a função do segundo parâmetro (um inteiro (`int`)) referido na questão anterior?**

_Resposta:_ Este segundo parâmetro serve para identificar um pedido de retorno em particular. Isto é, se forem lançados vários intentos com pedido de retorno, é este inteiro que permite identificar uma resposta específica.

**Questão 09: Qual é a função que ajusta o resultado de novo para a primeira atividade?**

_Resposta:_ `setResult (RESULT_OK, Result)`.

**Questão 10: O resultado é enviado no mesmo intento que despoletou a segunda atividade?**

_Resposta:_ Não, é enviada num novo intento.

**Questão 11: Qual é o método que é automaticamente despoletado quando uma atividade retorna um valor àquela que a invocou?**

_Resposta:_ `onActivityResult(int, int, Intent);`.

**Questão 12: Qual o objetivo da primeira condição do `if`?**

_Resposta:_ O objetivo é verificar se o intento que foi devolvido diz respeito ao que foi despoletado.

**Questão 13: Qual o objetivo da segunda condição do `if`?**

_Resposta:_ O objetivo é verificar se o resultado foi efetivamente devolvido ou se houve algum erro no processo.

**Questão 14: Ao todo, quantos ficheiros precisou de editar para conseguir a aplicação desejada?**

_Resposta:_ 5.

**Questão 15: Como é que se pode fazer uma chamada de um emulador para outro?**

_Resposta:_ Abrindo a aplicação de chamadas num dos emuladores, digitando o número da instância do segundo emulador (dada por `$adb devices`) e executando as chamadas.

**Questão 16: Qual o nome do separador específico que permite fazer chamadas e enviar mensagens de voz?**

_Resposta:_ _Phone_.

**Questão 17: Existe algum separador para gravação do ecrã do dispositivo virtual?**

_Resposta:_ Ahh, que giro!

**Questão 18: Quantos dedos podem ser simulados para o sensor de impressões digitais?**

_Resposta:_ 1 dedo.

**Questão 19: Das seguintes, qual concretiza a linha que define corretamente o id da etiqueta de texto?**

_Resposta:_ `android:id="@+id/lc"`.

**Tarefa 18:** `Uri allCalls = Uri.parse("content://call_log/calls");`. Ordem: 1 2 3 5 4 6.

**Questão 20: Quais dos seguintes pacotes interessa importar para a atividade principal desta aplicação?**

_Resposta:_ `android.os.Bundle`, `android.widget.TextView`, `android.net.Uri`, `android.database.Cursor`, `android.provider.CallLog`.

**Questão 21: Funcionou?**

_Resposta:_ Não funcionou.

**Questão 22: O registo de chamadas é considerado como um recurso a proteger no sistema AndroidTM?**

_Resposta:_ Pelos vistos sim.

**Questão 23: De que forma é que o sistema responde a pedidos a recursos protegidos?**

_Resposta:_ Negando todo o acesso, a não ser que a permissão para aceder ao recurso tenha sido declarada no `AndroidManifest.xml`. Negando todo o acesso, a não ser que a permissão para aceder ao recurso tenha sido declarada no `AndroidManifest.xml` e o utilizador tenha especificamente dado essa permissão aquando da instalação da aplicação.

**Questão 24: Desta vez já funcionou?**

_Resposta:_ Ainda não. _Reset_!

**Questão 25: O que é que fazem as três linhas de código sugeridas nesta tarefa?**

_Resposta:_ A linha 1 verifica se as permissões já foram dadas; a linha 3 pede as permissões. A linha 2 é um comentário. Dah! (Mas explica o significado do 0 dentro do `if`. Incrível!)

**Questão 26: Porque é que o método `requestPermissions` leva um _array_ de _strings_?**

_Resposta:_ Porque posso ter que pedir mais do que uma permissão simultaneamente.

**Questão 27: O método `requestPermissions(.,.)` é síncrono ou assíncrono?**

_Resposta:_ É síncrono.

**Questão 28: Qual o significado do segundo parâmetro (um `int`) no método `requestPermissions(.,.)`?**

_Resposta:_ Confirmar que as permissões foram todas aceites.

---

### Aula 07

**Questão 01: O ficheiro é mapeado na classe `R`?**

_Resposta:_ Sim, é, ficando com o identificador `R.raw.instructions`.

**Questão 02: O identificador para o qual é mapeado o ficheiro tem a ver com o seu nome?**

_Resposta:_ Sem dúvida.

**Questão 03: A definição da largura e da altura dos objetos interativos é obrigatória nas versões mais recentes do Android?**

_Resposta:_ Sim, é; caso contrário dá erro de compilação!

**Questão 04: O que é que acontece se definir a largura ou a altura de um _widget_ a zero (0) (e.g., com `android:layout_width="0"`)?**

_Resposta:_ Esse _widget_ ocupa sempre o máximo que consegue nessa dimensão tendo em conta outros elementos gráficos e as suas restrições.

**Questão 05: Também é possível escrever nesses ficheiros?**

_Resposta:_ Não, não é possível escrever nesses ficheiros, principalmente porque estarão dentro do arquivo `apk` aquando da sua execução.

**Questão 06: Quais os pacotes que necessitou incluir para concluir esta parte do guia?**

_Resposta:_ `import android.os.Bundle`. `android.util.Log`. `import android.view.View`. `import android.widget.EditText`. `import java.io.IOException`. `import java.io.InputStream`.

**Questão 07: Para que serve o inteiro no método `getPreferences (int)`?**

_Resposta:_ Este inteiro define o modo de acesso ao ficheiro.

**Questão 08: Em que diretoria é que o ficheiro das preferências partilhadas é normalmente guardado?**

_Resposta:_ `data/data/pt.ubi.pdm.aula7_storage/shared_prefs`

**Questão 09: Para que serve o `boolean`?**

_Resposta:_ Este valor deve ser `false` quando queremos obter o valor que está guardado com a chave `recover`; e `true` quando queremos substituir esse valor.

**Questão 10: É possível guardar tipos complexos (e.g., objetos) nas `Shared Preferences`?**

_Resposta:_ Não. Só tipos simples primitivos.

**Questão 11: Quais os pacotes que necessitou incluir para concluir esta parte do guia (para além dos que já tinha assinalado antes)?**

_Resposta:_ `import android.content.SharedPreferences`.

**Questão 12: Qual é a classe do objeto que lhe permite ajustar os valores guardados nas preferências partilhadas?**

_Resposta:_ `SharedPreferences`.

**Questão 13: Qual ou quais os nomes dos métodos que lhe permitem guardar, de facto, as alterações que estiver a introduzir nas preferências partilhadas?**

_Resposta:_ `Commit()`.

**Questão 14: Para que serve o método `Undo()`, enunciado na questão anterior?**

_Resposta:_ Para desfazer uma determinada ação no objeto.

**Tarefa 14**: Quando carregamos no botão `Exit`.

**Questão 15: O que faz o código incluído antes?**

_Resposta:_ Abre um ficheiro, escreve algo nesse ficheiro, e depois fecha o ficheiro.

**Questão 16: Qual o significado do número 0 no método `openFileOutput (string, int)`?**

_Resposta:_ Que o ficheiro é criado no modo privado, o que significa que só a aplicação é que lhe pode aceder.

**Questão 17: Lembra-se de ter implementado, no método `exitNotSave (View view)`, um editor para as preferências partilhadas?**

_Resposta:_ Sim, lembro.

**Questão 18: Pense bem: onde é que faz mais sentido colocar esses métodos?**

_Resposta:_ Antes do bloco `try {...} catch {...}`.

**Questão 19: Em que diretoria do sistema de ficheiros AndroidTM é que o ficheiro `savednote.txt` é guardado?**

_Resposta:_ `data/data/pt.ubi.pdm.aula7_storage/files`

**Questão 20: É possível verificar a existência do ficheiro usando o `Android Monitor`?**

_Resposta:_ Olha! Boa ideia!

**Questão 21: Isto faz sentido?**

_Resposta:_ Em Linux faz todo o sentido, visto que tudo, inclusive as diretorias, são ficheiros. O método `getExternalStoragePublicDirectory(...)` não devolve um `File`, mas sim um `Directory`.

**Questão 22: Lembrou-se de colocar o `commit()` no local certo da função?**

_Resposta:_ Atão não lembrei?

**Questão 23: Precisou de importar pacotes adicionais para esta parte do guia laboratorial?**

_Resposta:_ Sim, nomeadamente: `import java.io.File`, `import java.io.FileInputStream`, `import java.io.FileOutputStream`.

**Questão 24: Tem fechado todos os ficheiros que tem aberto?**

_Resposta:_ Eh... sim sim, tenho fechado tudo.

---

### Aula 08

**Questão 01: O que tem a dizer acerca da informação seguinte?**

*Resposta:* Esta afirmação é estapafúrdia.

**Questão 02: Já agora, o que significa o S do acrónimo SQL?**

*Resposta:* Significa *Structured*.

**Questão 03:  Que nome se dá às instruções SQL usadas assim no contexto de outra linguagem de programação?**

*Resposta:* _Embedded SQL_.

**Questão 04: Ainda no contexto da questão anterior, que qualificação se dá à linguagem Java?**

*Resposta:* Linguagem hospedeira.

**Questão 05: De acordo com o código incluído antes, o que é que acontece à base de dados durante um *upgrade*?**

*Resposta:* A única tabela da base de dados é eliminada e depois recriada. Todos os registos que lá estavam são mantidos.

**Questão 06: Falta algum *import* em alguma das classes implementadas antes?**

*Resposta:* Não falta absolutamente nada.

**Questão 07: Qual a diretoria onde as bases de dados são criadas?**

*Resposta:* `data/data/pt.ubi.pdm.aula8_storage/databases`.

**Questão 08: A que tipo de armazenamento é que a diretoria que indicou antes pertence?**

*Resposta:* Armazenamento interno.

**Questão 09: Foi criado mais algum ficheiro juntamente com a base de dados?**

*Resposta:* Que estranho: sim, foi!

**Questão 10: O que pode dizer acerca do tamanho da primeira caixa de texto, em relação aos outros dois objetos interativos da mesma linha, depois de definir o *layout* seguindo as indicações do guia?**

*Resposta:* Que a largura da segunda linha ficou dividida em 5, sendo 3 desses pedaços são ocupados pela primeira caixa de texto. 

**Questão 11: Que classes (adicionais) vai precisar de importar para que o código compile corretamente?**

*Resposta:* `import android.content.ContentValues`, `import android.view.View`, `import android.widget.EditText`.

**Questão 12: Em que diretoria do SDK está o executável que lhe permite abrir uma *shell* SQLite3 na sua máquina?**

*Resposta:* 

**Questão 13: Qual o comando que lhe permite ver quais os dispositivos que estão disponíveis via `adb`?**

*Resposta:* `$ adb list devices`.

**Tarefa 11:** `adb -s emulator-5554 shell`

**Questão 14: Qual é o comando que permite ver a descrição de todos os outros?**

*Resposta:* `.description`. (?)

**Questão 15: Agora que já tem fora de ver todos os comandos disponíveis, qual é o que permite ver todas as tabelas contidas na base de dados?**

*Resposta:* `.show`. (?)

**Questão 16: Verificou se a tabela `Movies` foi criada, de facto, na base de dados em análise?**

*Resposta:* Não verifiquei e sim, existe!

**Tarefa 14:**
* *Self-contained:* não tem dependências;
* *Serverless:* os processos leem e escrevem diretamente nos ficheiros de base de dados no disco;
* *Zero-configuration:* não é preciso ser "instalado" para ser usado;
* *Transactional:* segue as propriedades ACID.

**Questão 17: Em que linguagem foi escrito o SQLite?**

*Resposta:* `ANSI-C`.

**Questão 18: Em quantos ficheiros distintos se encontra a implementação do SQLite, e qual a razão principal que levou os seus programadores a fazer a implementação desta forma?**

*Resposta:* Está implementado em um único ficheiro e foi assim implementado para que fosse um motor autocontido, ou seja, para não possuir dependências e correr otimamente mesmo com recursos limitados.

**Questão 19: O SQLite permite acesso concorrente?**

*Resposta:* Permite.

**Questão 20: Qual das seguintes opções concretiza uma situação para a qual o SQLite não garante as propriedades ACID de uma transação?**

*Resposta:* Uma falha do programa.

**Questão 21: Como se sai do SQLite?**

*Resposta:* Com o caratere `EOF` (*End-of-file*).

**Questão 22: É possível obter as instruções que definem a criação das tabelas?**

*Resposta:* Sim é, nomeadamente através do comando `.schema`.

**Questão 23: O que é que faz uma `ScrollView`?**

*Resposta:* Uma `ScrollView` é um contentor especial, que oferece a funcionalidade de *scrolling* sempre que o seu conteúdo ultrapassa os limites do ecrã.

**Questão 24: Nota algum detalhe estranho no excerto de código adicionado?**

*Resposta:* Sim, o `LinearLayout` interno não contém qualquer objeto.

**Questão 25: Pode colocar objetos interativos, i.e., *widgets*, (e.g., um botão) diretamente dentro de um contentor do tipo `ScrollView`?**

*Resposta:* Sim, sem problemas.

**Tarefa 18:** `import android.widget.LinearLayout`, `import android.database.Cursor`. A primeira linha vai encontrar o *widget* de *LinearLayout*; a segunda linha serve para definir uma *query* em SQLite.

**Questão 26: O que faz o excerto de código anterior?**

*Resposta:* Coloca o `Cursor` a apontar para a linha imediatamente antes da primeira, movendo-o de seguida para a primeira linha.

**Questão 27: O que é que devolve o método `moveToNext()`?**

*Resposta:* Verdadeiro caso tenha conseguido mover-se para a próxima linha, e falso caso contrário.

**Questão 28: O que faz o método `inflate()`, presente na primeira linha de código do excerto anterior?**

*Resposta:* Lê o conteúdo do recurso dado por `line.xml`, convertendo-o para um objeto da aplicação.

**Questão 29: O que fazem todas as linhas de código que contêm o método `setId(.)`?**

*Resposta:* Na verdade, colocam todos os identificadores dos objetos a que se referem com o mesmo valor, i.e., o valor da chave primária da linha atual.

**Questão 30: Qual o ID atribuído a cada um dos objetos interativos representados?**

*Resposta:*

**Questão 31: Considera que o esquema que o professor engendrou para os IDs dos *widgets* é efetivo?**

*Resposta:* Não, porque há situações em que os IDs se podem repetir, nomeadamente quando há muitos dados, o que obriga a dar *scroll*.

**Questão 32: O que faz a última linha de código do excerto anterior (i.e., `oLL.addView(oLL1)`?**

*Resposta:* Adiciona todos os *widgets* redefinidos dentro do `while` ao `LinearLayout` que estava (inicialmente) vazio.

**Questão 33: O que fazem as últimas duas linhas de código do excerto anterior?**

*Resposta:* A primeira linha cria uma instância do contentor que contém o elemento a retirar e a segunda linha retira-o do seu elemento pai.