# Programação de Dispositivos Móveis

##### Atualizado em 30-10-2021
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
* **Modelo** - componente central; encapsula o estado interno, implementa objetos, métodos ou rotinas que capturam o comportamento base da aplicação de forma concisa, segura e uniformizada e acede e manipula base de dados. Só pode inteargir com o controlador, sendo completamente independente da interface - o utilizador nunca interage diretamente. As implementações devem ser o mais genéricas possível na representação dos dados, contudo, a interface de programação deve ser clara e consistente;
* **Visão** - possível representação dos dados da aplicação; define as interfaces (podendo haver várias representações para o mesmo conjunto de dados), que podem ser desenvolvidas em pararelo e melhoradas ao longo do tempo;
* **Controlador** - intermediário entre o modelo, a visão e o utilizador, com rotinas de captura e reencaminhamento de eventos, atualização de objetos da visão e despoletação de mudanças no estado da aplicação através de instruções enviadas para o modelo; responsável pela coordenação de tarefas de uma aplicação ou a gestão do ciclo de vida de objetos.

![](https://i.imgur.com/KHfhYm5.png)

Como não existe comunicação direta entre o _modelo_ e as _visões_, qualquer alteração que precise de ser refletida na interface tem de ser comunicada ao _controlador_ por uma notificação que contenha os dados necessários.

---

### Aula 02

Uma pilha de _software_ contém várias camadas e é desenhada para permitir a construção e execução de aplicações móveis:
* Serviços base - arquitetura de permissões, gestão de memória e processos, suporte a comunicações entre processos, operações de baixo nível de escrita e leitura em ficheiros, comunicações em rede; _drivers_ para suporte de dispositivos de _hardware_ adicionais (câmaras fotográficas, antenas de rádio, sensores);
* Bibliotecas nativas - implementadas em C/C++, para refrescar o ecrã, renderizar páginas _web_, gerir bases de dados, lidar com áudio e vídeo;
* _Android Runtime_ - bibliotecas Java fundamentais, máquina virtual; aplicações compiladas para _bytecode_;
* _Framework_ de aplicações - recursos utilizáveis, provedores de conteúdo (bases de dados para armazenamento e partilha de informações do sistema), gestores de pacotes (registo de todas as aplicações instaladas no sistema), atividades (coordenação e suporte de navegação entre atividades e ciclos de vida), janelas, localização e notificações;
* Aplicações - aplicações de fábrica, em desenvolvimento (_debug_) ou desenvolvidas por terceiros; é com esta camada que o utilizador final interage.

A virtualização permite obter vantagens na economia, versatilidade, confinamento, mas pode ter desvantagens de desempenho, funcionalidades em falta.

---

### Aula 03

Uma aplicação AndroidTM é constituída sobre quatro blocos fundamentais:
* **Atividades** - permitem a construção de interfaces de utilizador gráficas, para manipulação, adição ou obtenção de informação de uma aplicação. Uma atividade deve corresponder a uma única ação ou interação que um utilizador pode fazer. Uma aplicação com mais do que uma funcionalidade deve possuir mais do que uma atividade.
    * `super.onCreate(savedInstanceState)` recupera o estado em que a aplicação foi parada que foi guardado no `bundle`, que depois é construída com a instrução `setContentView(R.layout.main)`.;
* **Serviços** - permite executar operações de longa duração em segundo plano, despoletado por outra componente, continuando a fornecer funcionalidades mesmo que se mude de atividade ou aplicação;
* **Fornecedor de Conteúdos** - fornecem conteúdos estruturados a aplicações AndroidTM, permitindo que as aplicações comuniquem entre si ou usem dados que são partilhados por todo o sistema. O `ContentResolver` é a interface que verifica se a aplicação tem os privilégios necessários para aceder ao fornecedor de conteúdos, caso positivo, envia o pedido para o fornecedor de conteúdos respetivo;
* **Recetores de Difusão** - escutam e processam eventos, permitindo que determinada aplicação se registe no sistema como capaz de lidar com determinado evento e, quando esse evento acontece, seja chamada pelo sistema operativo para o processar.

Durante o processo de preparação da aplicação, alguns ficheiros do projeto são compilados e empacotados juntamente com outros recursos num arquivo `.apk`, que contém os ficheiros `.dex` (ficheiros `.class` compilados para o _byte code_ específico da máquina), uma versão binária do `AndroidManifest.xml`, os ficheiros com metadados acerca dos recursos `resources.arsc` e também todos os recursos que a aplicação usa em formato original.

A classe `R` contém a difinição de várias classes estáticas (como `id` e `string` que permitem acesso facilitado a recursos da diretoria `res`). É gerada pela ferramenta `aapt` (_Android Asset Packaging Tool_).

O ficheiro `AndroidManifest.xml` é uma estrutura fundamental em todas as aplicações AndroidTM, que apresenta informação essencial acerca da aplicação ao sistema para que este a possa executar. Indica o nome do pacote Java (identificador único no sistema); enumera as várias atividades, serviços, recetores de difusão e fornecedores de conteúdos; indica o nome de todas as classes que implementam as componentes supracitadas e as suas capacidades; declara as permissões da aplicação para acesso a partes protegidas ou interação com outras aplicações; declara as permissões que outras aplicações precisam de ter para aceder às suas funcionalidades; identifica a API mínima requerida; lista eventuais bibliotecas necessárias.

Uma **tarefa** é um conjunto ordenado de atividades que um utilizador percorre para obter determinada funcionalidade no contexto de uma aplicação AndroidTM. Uma aplicação pode ter várias tarefas, e nem todas as atividades de uma determinada tarefa pertencem à mesma aplicação. O sistema contém um conjunto de mecanismos que ajudam o utilizador a navegar pelas diversas atividadse (por exemplo, pilha de retrocesso de tarefas (_Task Backstack_)) e gere automaticamente o ciclo de vida das atividades, garantindo que estas são devidamente inicializadas, suspendidas ou retomadas, bem como destruídas em caso de falta de memória.

Uma atividade pode estar **ativa**/**em execução** (se estiver totalmente visível em primeiro plano); **pausada** (parcialmente visível, mantém o estado e continua ligada ao gestor de janelas); **parada** (se estiver completamente tapada por outra atividade). Quando pausada ou parada, pode ser destruída para colmatar problemas de memória. Métodos:
* `onCreate()` - chamado quando a atividade é criada pela primeira vez, com configuração estática (criação ou ajuste da interface de utilizador, colocação de lógica aplicacional para lidar com eventos e recuperação do estado anterior);
* `onStart()` - chamado quando a atividade está próxima de ficar visível, ideal para colocar código que reajuste o estado da aplicação com dados provenientes de sensores ou guardados no sistema;
* `onResume()` - despoletado quando a atividade está a transitar de um estado invisível ou tapado para o primeiro plano, com instruções para inicializar e correr animações ou toques. Depois de executar, a atividade fica em estado de execução e o utilizador pode interagir com ela;
* `onPause()` - despoletado quando a atividade está a perder o foco, usado para guardar dados persistentes que a atividade esteja a editar, gerir a paragem de animações e outras operações que exijam recursos de computação para agilizar a transição para a nova atividade, ou fechar recursos externos;
* `onStop()` - chamado quando a atividade já não está visível para o utilizador para _caching_ de alguns dados caso a atividade seja retomada. Atividades paradas têm uma maior probabilidade de serem terminadas por falta de memória e o método não deve ser utilizado para guardar estados;
* `onRestart()` - chamado apenas quando uma atividade foi colocada em segundo plano e o utilizador volta a navegar para a mesma, com código que permite recuperar dados que tenham sido guardados;
* `onDestroy()` - invocado quando a ativiade está para terminar normalmente, com libertação de recursos computacionais (_threads_), podendo não ser chamado caso a atividade seja terminada de modo abrupto, pelo que não deve conter funcionalidades críticas.

---

### Aula 04

Um **intento** é a manifestação de uma intenção de fazer uma ação, encapsulado pelo objeto `intent`, que pode ser: executada por uma componente da aplicação ou de outra, capturada pelo sistema operativo e entregue a uma de várias componentes aptas para a executar ou descartada. O `intent` pode lançar uma nova atividade (`startActivity(Intent)`, `startActivityForResult(Intent)`), executar serviços (`startService(Intent)`, `bindService(Intent, ServiceConnection, int`), emitir _broadcasts_ (`sendBroadcast()`, `sendOrderedBroadcast()`, `sendStickyBroadcast()`).

Quando um componente de uma aplicação quer começar outro componente, instancia um intento e envia-o para o sistema, que fica responsável por identificar, verificar as suas permissões e, em caso de encontrar o seu destino e ser permitido, de o enviar para execução. O `intent` é composto por:
* Nome do componente destino - opcional, distingue intentos explícitos (contêm nome) de implícitos (não contêm nome);
* Ação a efetuar - especificada normalmente através de uma _string_ predefinida, que é obrigatória caso o nome do destinatário não seja indicado;
* Dados - _Uniform Resource Locator_ (URI) e _Multi-Purpose Internet Mail Extensions_ (MIME) para que aponta;
* Categoria - _string_ que indica o tipo de componente;
* Extras - pares chave-valor para transferir dados adicionais;
* _Flags_ - metadados para o objeto para instruir o sistema sobre como deve lançar ou manipular as atividades ou serviços por ele lançados.

Um **intento explícito** especifica univocamente a componente que deve ser despoletada pelo seu nome no sistema operativo (pacote e nome de classe), usado para despoletar outra componente da própria aplicação ou quando se sabe o nome da classe ou atividade destino. Quando um intento explícito é criado, o sistema operativo despoleta a atividade ou serviço indicados imediatamente.

Um **intento implícito** indica a ação genérica a executar e, se disponíveis, dados adicionais para a sua realização. Para encontrar uma componente apropriada, o sistema operativo compara o conteúdo do intento com os filtros de intentos: se apenas uma correspondência for encontrada, a componente respetiva é despoletada; se não, é mostrada uma caixa de diálogo ao utilizador, que deve escolher interativamente qual deverá tratar a ação.

---

### Aula 05

Uma das bases da **arquitetura de segurança** do AndroidTM consiste na assunção de que uma aplicação, por defeito, não tem permissão para excutar operações que possam ter impacto adverso noutras aplicações, no sistema operativo ou no utilizador. Cada aplicação tem de explicitamente pedir permissões para utilizar recursos não fornecidos de forma nativa pela _sandbox_ em que é executada. As **permissões** são declaradas estática e explicitamente no manifesto da aplicação, e o sistema pede o consentimento ao utilizador para o usufruto dos recursos aquando da instalação ou durante a execução.

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

