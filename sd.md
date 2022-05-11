# Sistemas Distribuídos

##### Atualizado em 09-05-2022
###### A partir de: sebenta, exercícios das aulas teóricas e práticas

## Aulas Teóricas

### Aula 01

**Sistema distribuído** - conjunto de computadores ligados em rede, com *software* que permita a partilha de recursos e a coordenação de atividades, oferecendo um sistema integrado que permite:
* *Comunicação através de mensagens* - não existem variáveis globais ou memória partilhadas;
* *Concorrência* - vários utilizadores a usar o sistema em simultâneo;
* *Partilha de recursos* - levanta questões de segurança; gestores de recursos controlam o acesso a recursos partilhados;
* *Assincronicidade* - diferentes velocidades de processamento;
* *Independência de falhas* - a falha de um componente (falha de rede ou unidade de processamento) pode não impedir o funcionamento de outros;
* *Heterogeneidade* - diferentes tipos de rede, *hardware*, sistemas operativos, linguagens de programação (colmatado por uma camada intermédia de *software*: ***middleware***).

**Computação ubíqua** - sistemas cuja utilização está de tal modo integrada na funcionalidade do produto que é transparente para o utilizador, com maiores restrições em termos de custo, tamanho potência/autonomia.

Desafios da implementação de sistemas distribuídos:
* **Escalabilidade** - manter o sistema a funcionar de forma correta e à velocidade desejada, independentemente do número de utilizadores, exigindo:
  * Desenho do *software* de forma a que o aumento de utilizadores não exija grandes alterações;
  * Evitar algoritmos e estruturas de dados centralizadas;
  * Controlo do aumento de custos devido à disponibilidade de mais recursos;
  * Controlo da perda de *performance*;
  * Evitar o transbordo de certos limites de recursos;
* **Sistema aberto** - poder estender o sistema em *hardware* e *software*, podendo adicionar-se novos componentes sem pôr em causa o funcionamento dos já existentes, aplicando conhecimento das interfaces dos novos componentes e protocolos e formatos padrão;
* **Tolerância a falhas** - conter os efeitos de falhas de forma a que o sistema continue a funcionar, exigindo deteção, localização e tolerância da falha;
* **Segurança** - manter o nível de confidencialidade exigido, garantir a integridade dos dados e manter a disponibilidade do sistema;
* **Transparência** - o sistema deve ser visto como um todo e não como uma coleção de componentes distribuídos:
  * *Transparência de acesso* permite que o acesso a recursos locais e remotos seja feito através das mesmas operações;
  * *Transparência de localização* permite que os recursos possam ser acedidos sem o conhecimento da sua localização;
  * *Transparência de concorrência* permite que os vários clientes de um componente não necessitem de ter em conta o acesso concorrente ao componente;
  * *Transparência de replicação* permite que os clientes de um componente não se apercebam se existe replicação de recursos, por motivos de desempenho ou fiabilidade;
  * *Transparência de falhas* permite que o sistema funcione na presença de falhas de *hardware* ou *software* sem que utilizadores e programadores saibam como as falhas foram ultrapassadas;
  * *Transparência de migração* permite que um recurso possa mudar de localização sem afetar o seu uso;
  * *Transparência de desempenho* permite que o sistema seja reconfigurado para melhorar o seu desempenho sem que os utilizadores se apercebam;
  * *Transparência de escalabilidade* permite que o sistema seja expandido sem que os utilizadores se apercebam.

**Exercícios:**
* **1.** *Hardware*, *software*, bases de dados.
* **2.** Um URL não diz em que zona da base de dados está a informação a que se está a aceder, no entanto, qualquer pessoa pode obtê-la através dele.
* **3.** Cliente: *browser*, servidor: servidor da empresa.
* **4.** Sistemas operativos, linguagens de programação, *hardware*, rede.
* **5.** Forma de distinção de utilizadores (por exemplo, através de credenciais de entrada); o servidor tem de saber o que é que cada tipo de cliente pode fazer e ao que pode aceder. O cliente tem de ter a certeza de que a resposta ao pedido que vem do servidor e não me uma mensagem externa "injetada". 
* **6.** Falha de ligação cliente-servidor.
* **7.** 

---

### Aula 02

**Comunicação interprocessos** (IPC) é usada para transferir dados entre os processos e coordenar a sua atividade - *memória partilhada* e *comunicação por mensagens*.

Em **sistemas de memória partilhada** os processos acedem a um único espaço de endereçamento, comunicam através de variáveis partilhadas e a sincronização é feita pelas técnicas clássicas da programação concorrente (semáforos, monitores).

Em **sistemas de memória distribuída** há vários espaços de endereçamento disjuntos, em que a comunicação é feita por mensagens e a comunicação e sincronização estão agrupadas num único conceito. As comunicações por mensagens distinguem-se por:
* **Tipo de sincronização**
    * *Comunicação síncrona* - o envio de uma mensagem é uma operação atómica que requer a participação de dois processos (emissor e recetor) e que sincroniza as sequências de execução dos dois processos. Conceito de baixo nível mais eficiente;
    * *Comunicação assíncrona* - o emissor pode enviar a mensagem e continuar a executar sem bloquear, independentemente do estado do processo recetor. Permite maior grau de concorrência, embora exija que o sistema de execução faça gestão e armazenamento de mensagens;
    * *Remote Procedure Calling* (RPC) - o processo emissor envia uma mensagem, o processo recetor produz uma resposta à mensagem e o emissor permanece suspenso até à receção da resposta. Do ponto de vista do emissor, este mecanismo funciona como a chamada de um procedimento, que não é executado no próprio processo mas sim no recetor;
        * Variante: após o envio da mensagem, o emissor prossegue a execução até precisar do resultado (permite maior concorrência), ficando suspenso se a resposta não estiver disponível; quando um processo recetor executa uma instrução de aceitação de mensagem, é suspenso até à chegada da mesma;
* **Tipo de intervenientes**
    * *Identificação dos processos* - todos os processos têm um nome único, em que os comandos de envio e receção podem nomear diretamente os processos, ou definem-se entidades intermédias (caixas de correio) conhecidas por ambos os intervenientes na comunicação;
    * *Criação dos processos* - os processos podem ser criados de forma estática (processos criados no início da execução) ou dinâmica (o sistema ajusta-se às necessidades, com mecanismos de balanceamento de carga);
    * *Comunicação uni ou bidirecional*.

***Socket*** é a interface de um canal de comunicação entre dois processos, cujo endereço é especificado pelo endereço IP da máquina ou pelo número de um porto. A classe `Socket` permite criar *sockets* que comunicam através do protocolo TCP (*Transmission Control Protocol*), usando uma *stream* de bytes.

**Exercício:**

```java=
// cliente
public static void main (String args[]) {
	Socket se = new Socket ("127.0.0.1", 1111);
	ObjectOutputStream oos = new ObjectOutputStream(se.getOutputStream());
	ObjectInputStream ois = new ObjectInputStream(se.getInputStream());
	oos.writeObject("Hello world, i'm the client.");
	String s = (String) ois.readObject();
	System.out.println(s);
}

// servidor
public static void main (String args[]) {
	ServerSocket ss = new ServerSocket(1111);
	Socket st;
	st = ss. accept();
	ObjectOutputStream oos = new ObjectOutputStream(st.getOutputStream());
	ObjectInputStream ois = new ObjectInputStream(st.getInputStream());
	String s = (String) ois.readObject();
	System.out.println(s);
	oos.writeObject("Hello world, i'm the server.");
}
```

---

### Aula 03

***Threads*** - sequências de execução independente que partilham o mesmo espaço de endereçamento que o processo que lhes deu origem. Seja `P` um processo constituído pelas *threads* `T1` e `T2`, a execução de `P` é a sequência pertencente ao conjunto formado por todas as sequências de combinações possíveis de execução de `T1` e `T2`.

Uma *thread* começa por ser um **objeto instanciado** (`.new Thread()`), que pode serinicializado (`.start()`), tornando-se **executável**. A instrução `.yield()` permite que outra *thread* seja escalonada para execução. Os métodos `.sleep(i)` e `.wait()` tornam a *thread* **não executável** (não pode ser escalonada para execução), e podem ser revertidos quando o tempo `i` termina ou com a instrução `.notify()`. Uma *thread* pode ser **terminada** pela instrução `.destroy()` enquanto objeto instanciado ou, enquanto executável, pelo término do método `run()` ou pelo método `.interrupt()`. Uma *thread* no estado executável não está necessariamente em execução, apenas pode ser escalonada para ser executada.

A **sincronização de *threads*** é um método baseado no conceito de monitor, com um *lock* associado a cada objeto e classe. Após calcular a referência para o objeto, mas antes de executar o corpo de instruções, a *thread* adquire o *lock* associado ao objeto e executa as instruções, libertando o *lock* em seguida. O *lock* é também libertado se a execução do bloco de instruções termina anormalmente ou é interrompido.
* Um método pode ser declarado como `synchronized`, comportando-se como se estivesse contido numa instrução sincronizada:
    * Se o método sincronizado é um **método de instância**, a *thread* adquire o *lock* do objeto e todas as *threads* que tentem executar esse mesmo método no mesmo objeto terão de esperar, competindo pela aquisição do *lock*;
    * Se o método sincronizado é um **método de classe**, a *thread* adquire o *lock* da classe e todas as *threads* que tentam executar esse método em qualquer objeto da classe terão de esperar que o *lock* seja libertado;
* O facto de uma *thread* adquirir o *lock* associado a um objeto não impede que outras *threads* acedam aos campos do objeto ou possam invocar métodos não sincronizados.

---

### Aula 04

Os métodos `wait()`, `notify()` e `notifyAll()` permitem a transferência de controlo de uma *thread* que tenha o *lock* do objeto para outra, deixando-se em suspenso.

Ao executar o `wait()`, uma *thread* `T` é adicionada ao *wait set*, suspende e liberta o *lock*; permanece no estado "não executável" até que:
* Alguma outra *thread* invoque o método `notify()` para o objeto e aquela *thread*;
* Alguma outra *thread* invoque o método `notifyAll()`;
* Alguma outra *thread* invoque o método `interrupt()` na *thread* `T`;
* O intervalo de tempo especificado na invocação do método `wait()` expirou.

Após a reativação da *thread* `T`, esta é removida do *wait set* e escalonada para execução, voltando a adquirir o *lock* sobre o objeto e retornando ao ponto onde foi invocado o `wait()`.

O método `notify()` só é eficaz se o *wait set* não está vazio, sendo escolhida arbitrariamente uma *thread* para ser retirada do conjunto e passar ao estado executável. No método `notifyAll()`, todas as *threads* do *wait set* são removidas e passam ao estado executável, podendo ser reescalonadas quando a *thread* invocadora libertar o *lock*.

Um **semáforo**, segundo Dijkstra, é uma variável `s` que apenas pode assumir valores positivos ou nulos e à qual está associada uma fila de processos.

---

### Aula 05

**Sockets** são abstrações para representar a comunicação entre dois processos (transmissão de uma mensagem no *socket* de um processo para um *socket* de outro processo). O *socket* de um processo tem de ser conectado a um porto local para que possa começar a enviar e receber mensagens, associado a um determinado protocolo:
* ***User Datagram Protocol*** (UDP) - protocolo sem conexão de comunicação por datagramas com mensagens até $2^16$ bytes (mensagens maiores são truncadas), feito pelos métodos:
    * `send` - não bloqueável. O processo retorna assim que a mensagem é enviada; no destino, a mensagem é colocada na fila do *socket* respetivo (se nenhum processo estiver ligado ao *socket*, a mensagem é descartada);
    * `receive` - bloqueável. O processo bloqueia até que consiga ler a mensagem para o seu *buffer*; enquanto espera por uma mensagem, o processo pode criar uma nova *thread* para executar outras tarefas. Ao *socket* pode ser associado um *timeout*, findo o qual o *receive* desbloqueia;
        * Pode haver **avaria por omissão** (a mensagem não chega porque o *buffer* local ou remoto está cheio ou por erro de conteúdo (`checksum error`)) ou **avaria de ordenamento** (as mensagens chegam fora de ordem);
* ***Transmission Control Protocol*** (TCP) - protocolo com conexão de comunicação por *streams* sem limite de tamanho, com um esquema de confirmação da receção. Há uniformização das velocidades dos processos que leem e escrevem de e para uma *stream*, e o recetor pode detetar e rejeitar mensagens duplicadas ou reordenar mensagens fora de ordem;
    * Há `checksum` para detetar e rejeitar pacotes corrompidos, `timeouts` e retransmissão para lidar com pacotes perdidos e número de sequência para detetar e rejeitar pacotes duplicados.

Tanto o processo local como o processo remoto manipulam estruturas de dados locais, que precisam de ser serializados em sequências de bytes para serem transmitidos. Quaisquer sistemas podem trocar valores entre si se houver uma representação externa comum para os dois ou for enviada informação sobre o formato usado juntamente com os dados. Na implementação de *Remote Procedure Calling* (RPC) e *Remote Method Invocation* (RMI), qualquer tipo de dados que possa ser passado como argumento ou devolvido como resultado tem de poder ser serializado pelo *middleware*.

O processo de transformar os dados do seu formato interno para uma representação externa que possa ser transmitida numa mensagem denomina-se ***marshalling*** (serialização). O processo inverso, de converter os dados da representação externa para o formato interno do recetor reconstruindo as estruturas de dados denomina-se ***unmarshalling*** (desserialização).

Uma **referência para um objeto remoto** é um identificador de um objeto válido em todo o âmbito do sistema distribuído, que deve existir no processo local, na mensagem enviada ao objeto e no processo remoto que possui a instância do objeto cujo método é invocado. Referências remotas devem ser geradas de forma a garantir unicidade no espaço e no tempo.

O **protocolo pedido-resposta** é implementado em três operações base:
* `public byte [] doOperation (RemoteObjectRef o, int methodId, byte [] arguments` - envia uma mensagem de pedido a um objeto remoto, em que o processo invoca uma operação de `receive`, ficando bloqueado até à chegada da resposta. Os argumentos especificam o objeto remoto, o método a ser invocado e os argumentos desse método;
* `public byte [] getRequest ()` - espera por pedidos de clientes, aos quais o processo servidor executa o método executado e envia a resposta correspondente pelo método `sendReply`;
* `public void sendReply (byte [] reply, InetAddress clientHost, int clientPort)` - envia a resposta ao cliente utilizando o seu endereço IP e o número do porto, desbloqueando a operação `doOperation`;
    * Possuem as mesmas avarias que o protocolo UDP, *crash failures* (se o processo parar e permanecer parado, não produzindo valores arbitrários) e *timeouts*. O servidor pode detetar repetições de mensagens repetidas e processar o método novamente se a resposta se perdeu (caso seja idempotente).

Possíveis semânticas perante falhas:
* *Maybe* - perante possíveis perdas, não é repetido o pedido de invocação;
* *At Least Once* - perante perdas ou atrasos na resposta, são reenviados pedidos de execução que não são reconhecidos como duplicados pelo servidor;
* *At Most Once* - os possíveis reenvios de pedidos são reconhecidos como duplicados pelo servidor.

---

### Aula 06

Num sistema orientado a objetos, os objetos são acedidos através das suas **referências** (objeto, nome do método e argumentos correspondentes). Referências podem ser atribuídas a variáveis, passadas como argumentos e devolvidas como resultado de métodos. Uma **referência remota** é um identificador que pode ser usado no âmbito de um sistema distribuído para se referir a um particular e único objeto remoto.

**Objetos locais** são passados por cópia (a referência não faz sentido na máquina remota). **Objetos remotos** são passados por referência - a referência aponta para um objeto local que funciona como um *proxy* do objeto remoto.

**Interface** é uma especificação sintática de um conjunto de métodos que devem ser obrigatoriamente implementados pela classe que a invoque. Numa **interface remota**, cada objeto remoto tem uma interface remota que especifica quais dos seus métodos podem ser invocados remotamente.

A invocação de um **método local** resulta na execução do código correspondente no objeto recetor e retorno do controlo da execução ao objeto invocador, podendo resultar na alteração do estado de um objeto ou noutras invocações. Quando ocorre uma situação de erro recuperável, gera-se uma exceção que pode ser capturada e controlada por um bloco de código que trata da condição do erro.

A invocação de um **método remoto** pode resultar na invocação de métodos noutros objetos remotos ou locais que, se atravessar a barreira de um processo ou computador, pode ser um procedimento remoto (para o qual necessita da sua referência remota). Para além das exceções ocorridas no processo recetor, também podem gerar-se exceções devido a erro na transmissão de argumentos, *crash* do processo que contém o objeto remoto e perda do resultado da invocação.

O ***software* RMI** é a camada de *software* entre a aplicação e os módulos de comunicação e referência. Um ***proxy*** torna transparente a invocação do método remoto, recebe a invocação, serializa os argumentos e envia a invocação através do módulo de comunicação; quando recebe o resultado, deserializa-o e envia-o ao objeto cliente. O ***dispatcher*** recebe o pedido do módulo de comunicação e encaminha-o para um ***skeleton***, que desserializa os argumentos, invoca o método no objeto local, recebe o resultado e encaminha-o no sentido inverso.

---

### Aula 07

**Modelo arquitetural** - estrutura do sistema em termos de localização das suas diferentes partes, o papel que cada parte desempenha e como se interrelacionam. A arquitetura implicações no desempenho, fiabilidade e segurança. Os modelos podem ser:
* **Cliente-Servidor** - de interação simples, muito usado na prática, com segurança centrada no servidor (que se torna um ponto de falha único) e não escalável para lá de determinados limites. O servidor (*backend*) é um processo passivo que, quando contactado por um cliente, envia uma resposta; o cliente (*frontend*) contacta o servidor com o objetivo de utilizar um serviço, enviando um pedido e aguardando uma resposta. A máquina que suporta o processo servidor precisa de ter recursos mais poderosos de forma a suportar centenas de pedidos num curto intervalo de tempo;
    * Num sistema típico, este modelo tem três camadas: **camada de apresentação** (*view*, interface com o utilizador); **camada da lógica de negócio** (*model*, regras que controlam o comportamento da aplicação); **camada de persistência de dados** (*controller*, armazenamento e integridade de dados);
* **Múltiplos Servidores** - um serviço pode ser implementado por vários processos servidores localizados em diferentes computadores:
    * **Cliente-Servidor Replicado** - existem vários servidores capazes de responder aos mesmos pedidos. Permite distribuir a carga, melhorando o desempenho e sem ter um único ponto de falha; no entanto, é difícil manter o estado do servidor coerente em todas as réplicas;
    * **Cliente-Servidor Particionado** - existem vários servidores com a mesma interface, cada um capaz de responder a uma parte dos pedidos. O servidor pode redirigir o cliente para outro servidor (iterativo) ou invocar o pedido noutro servidor (recursivo). Permite escalabilidade e as mesmas vantagens que um modelo cliente-servidor replicado, no entanto, a falha de um servidor impede acesso aos dados nele presente;
* ***Proxies*** - uma *cache*, localizada no cliente ou em servidores *proxy* partilhados, permite o armazenamento numa localização próxima de dados/objetos recentemente usados, com o objetivo de aumentar a disponibilidade e a *performance* do serviço. Quando um cliente necessita de um objeto, o serviço de *caching* verifica se possui uma cópia atualizada do objeto, fornecendo uma cópia em caso afirmativo;
* ***Peer Processes*** - todos os processos desempenham papéis similares. Cada processo é responsável pela consistência dos seus dados (recursos) e pela sincronização das várias operações e pode assumir, simultânea ou alternadamente, o papel de cliente e servidor do mesmo serviço. É um modelo de interação e coordenação mais complexo, com algoritmos mais complexos, sem um ponto único de falha e com grande potencial de escalabilidade, apropriado para ambientes em que todos os participantes querem cooperar para fornecer um dado serviço. Paradigma de distribuição em que os serviços são suportados diretamente pelos seus clientes/utilizadores, sem recurso a uma infraestrutura criada e mantida explicitamente para esse fim, com a ideia de conseguir explorar os recursos disponíveis nas máquinas ligadas em rede:
    * **Serviço de Diretório Centralizado** - quando um novo processo se liga, informa o servidor central do seu endereço e conteúdo, podendo comunicar depois com os outros pares;
    * **Serviço de Diretório Distribuído** - quando um novo processo se liga, liga-se a um grupo cujo líder regista o conteúdo de todos os elementos do grupo. Cada processo acede ao líder do seu grupo para localizar o que pretende e cada líder pode aceder a outros líderes.

Outros modelos variantes do modelo cliente-servidor incluem **código móvel** (o pedido de um cliente resulta no *download* de código *applet*, com o qual interage), **sistemas com *hardware* limitado**, **adição/remoção de periféricos móveis ao sistema**.

Um **agente** é um programa executável que pode mover-se de uma máquina para outra e age em nome de um utilizador específico, num dado computador, para o qual se transfere para realizar algum serviço para o seu proprietário, obtendo informações que mais tarde transmitirá ao local de origem.

**Exercício:**

```java=
// classe
public class doador {
    private double donativo;
    private ArrayList <String> doadores;
    
    public doador () {
        donativo = 0;
        doadores = new ArrayList <String> ();
    }
    
    (...)
}

// servidor (sem try-catches)
public class servidor {
    public static void main (String [] args) {
        ServerSocket ss = new ServerSocket (2222);
        Socket s = null;
        doador d = new doador ();
        connection c;
        while (true) {
            s = ss.accept();
            c = new connection (s, d);
        }
    }
}

// thread
public class connection extends Thread {
    private Socket s;
    private doador d;
    
    public connection (Socket s, doador d) {
        super(); // pode ser omitido, o próprio compilador o insere
        this.s = s;
        this.d = d;
        start();
    }
    
    public void run () {
        ObjectOutputStream oos = new ObjectOutputStream (s.getOutputStream());
        ObjectInputStream ois = new ObjectInputStream (s.getInputStream());
        int opcao = -1;
        while (opcao != 0) {
            opcao = ois.readInt();
            switch (opcao) {
                case 1:
                    // fazer donativo
                    double donativo = ois.readDouble();
                    String nome = ois.readString();
                    // ou: String nome = (String) ois.readObject();
                    d.setDonativo (d.getTotal + donativo);
                    d.setDoadores (nome);
                    // neste método anterior, a verificação ficaria na classe
                    // doador, uma vez que não devem haver nomes repetidos
                    break;
                case 2:
                    // consultar total
                    oos.writeDouble(d.getDonativo());
                    oos.flush();
                    break;
                case 3:
                    // consultar lista de doadores
                    oos.writeObject(d.getDoadores());
                    oos.flush();
                    break;
            }
        }
    }
}

// cliente
public class cliente {
    public static void main (String [] args) {
        Socket s = new Socket (2222);
        int opcao = -1;
        ObjectOutputStream oos = new ObjectOutputStream (s.getOutputStream());
        ObjectInputStream ois = new ObjectInputStream (s.getInputStream());
        while (opcao != 0) {
            // menu
            opcao = readInt();
            oos.writeInt(); // enviar opção do cliente
            oos.flush();
            switch (opcao) {
                case 1:
                    double donativo = readDouble();
                    oos.writeDouble(donativo);
                    oos.flush();
                    String nome = readString();
                    oos.writeString(nome);
                    oos.flush();
                    break;
                case 2:
                    System.out.println(ois.readDouble());
                    break;
                case 3:
                    System.out.println(ois.readObject());
                    break;
            }
        }
    }
}
```

---

### Aula 08

**Entreprise Bean** - standard para definição de classes reutilizáveis, com atributos privados, métodos públicos, um construtor sem parâmetros e implementa a inferface `Serializable`. É um componente executado do lado do servidor que implementa a lógica da aplicação. O *Bean container* oferece os serviços do sistema para gerir transações, segurança, concorrência e escalabilidade.

***Session Beans*** implementam uma tarefa para a aplicação cliente. Um *session Bean* é referido por `dependency injection`(usando anotações da linguagem, `@EJB`) ou JNDI (*Java Naming and Directory Interface*), que pode ser acedido no contexto local (`@Local`), numa interface remota (`@Remote`) ou por *web service* (`@WebService`). Podem ser:
* *Stateful* se guardar as variáveis. Cada instância está associada a um único cliente, mantendo o estado de sessão não partilhado com este (estado: valores das variáveis de instância). permitem guardar informação do cliente entre múltiplas informações, possuindo um tempo de vida configurável até serem removidos;
* *stateless* se não guardar as variáveis. O estado existe apenas durante a invocação de um método, não mantendo informação específica de um cliente. O servidor gere uma *pool* de instâncias que servem pedidos de vários clientes, podendo ser implementadas como *web services*;
* *singleton* se apenas houver uma instância para toda a aplicação. O estado é partilhado por todos os clientes e preservado entre invocações. Se tiver a anotação `@Startup`, deve ser instanciado no princípio da execução.

***Message Driven Beans*** são recetores assíncronos, atuando como *listeners* para um determinado tipo de mensagens. Não mantêm estados e podem processar mensagens de múltiplos clientes.

***Java Persistence API*** permite converter o conteúdo de uma classe Java a uma tabela específica numa base de dados, e vice-versa. É uma *framework* JAVA que engloba a API, a linguagem JPQL (*Java Persistence Query Language*) e os metadados. 

Cada entidade (`Entity`) é uma classe POJO tem um construtor público sem argumentos, campos (*getters* e *setters*), chaves primárias e associações que representa uma tabela numa base de dados relacional. Usa a anotação `@javax.persistence.Entity` e uma chave primária (`@Id`, única, ou `@EmbeddedId`, composta).

:::warning
A anotação `@GeneratedValue` pode dar erros nas transações ACID.
:::

**Arquitetura orientada a serviços** (SOA) é uma arquitetura de sistemas distribuídos em que a funcionalidade é disponibilizada sob a forma de serviços, bem definidos e independentes, para permitir a interoperabilidade de sistemas heterogéneos e a independência de plataformas e linguagens. É uma tecnologia proprietária, específica para uma determinada plataforma, não interoperável, que requer a configuração de *firewalls*.

*Web Services* são uma SOA que usam HTTP como protocolo de transporte de mensagens, descritos através de uma linguagem de descrição em XML. Permite a independência de plataformas e linguagens, com menor suscetibilidade a restrições de segurança (não é necessário configurar portos e *firewalls*) e o todo o tráfego é HTTP. Fazem:
* **Publicação** - processo opcional pelo qual se dá a conhecer a existência de um serviço;
* **Descoberta** - processo opcional através do qual uma aplicação cliente faz uma pesquisa sobre o reservatório de *web services* e toma conhecimento da existência do serviço requerido;
* **Descrição** - a aplicação cliente tem acesso à interface do *web service*, à descrição das funcionalidades disponibilizadas e aos tipos de mensagem que permitem aceder a essas funcionalidades;
* **Invocação** - processo pelo qual cliente e servidor interaem através da troca de mensagens.

**SOAP** (*Simple Object Access Protocol*) é um protocolo para a troca de mensagens em XML entre processos. Cada recetor chama-se *endpoint* e, ao receber uma mensagem, analisa-a e verifica se alguma parte lhe é endereçada; se sim, verifica se das partes que lhe são dirigidas alguma requer processamento e executa as operações; se parte da mensagem é para reenviar, retira a parte já processada e envia.

**WSDL** (*Web Services Description Language*) é um formato XML para descrever *web services* e invocá-los, através de quatro tipos de operações: **pedido** (o servidor recebe um pedido, mas não envia resposta); **pedido/resposta** (o servidor recebe um pedido e envia uma resposta); **solicitação/resposta** (o servidor envia uma mensagem ao cliente e recebe uma resposta); **notificação** (o servidor envia uma mensagem para a qual não espera nenhuma resposta).

**REST** (*Representational State Transfer*) é uma arquitetura para sistemas distribuídos de *hypermedia* (recursos como texto, imagens e vídeo são guardados em rede e ligados via hiperligações). Um recurso é uma entidade com um URI (*Universal Resource Identifier*). **REST *Web Services*** comunicam sobre o protocolo HTTP, numa arquitetura baseada na transferência de representações de recursos através de pedidos (*requests*) e respostas (*responses*), manipulados pelos métodos `PUT`, `GET`, `POST`, `DELETE`.

---

### Aula 09

Os sistemas distribuídos podem ser analisados segundo três modelos transversais a todos os sistemas: **modelo de interação** (ou de sincronismo), **modelo de falhas** (ou avarias), **modelo de segurança**.

Num **modelo de interação**, interação é uma ação (comunicação e sincronização) entre as partes para realizar um qualquer trabalho. É afetada por:
* **Performance dos canais de comunicação**:
  * Latência - intervalo de tempo entre o início da transmissão de uma mensagem por um processo e o início da sua receção pelo outro processo;
  * Largura de banda - total de informação que pode ser transmitida pela rede num dado intervalo de tempo;
  * *Jitter* - variação no tempo necessário para enviar grupos de mensagens consecutivos constituintes de uma informação transmitida de um ponto para outro na rede;
* **Inexistência de um tempo global** - cada computador tem um *drift* (desvio) do tempo de referência e os *drifts* de dois relógios são distintos, pelo que o tempo entre eles será sempre divergente.

Um modelo de interação pode ser um sistema distruído:
* **Síncrono** - sistemas onde podem existir limites máximos de tempo conhecidos para tempo de execução dos processos, atrasos na comunicação e variações no tempo de referência. Se o tempo necessário para executar cada passo de um processo tem um limite inferior e um limite superior conhecidos, cada mensagem transmitida por um canal é recebida dentro de um limite de tempo conhecido, cada processo tem um relógio cujo desvio máximo para o tempo de referência é conhecido, podem definir-se *timeouts* para detetar falhas;
* **Assíncrono** - não possui limites para tempos de execução dos processos ou de transmissão de mensagens, em que o desvio para o tempo de referência pode ser qualquer.

Para, num modelo de interação, conhecer a ordem pela qual ocorreu um conjunto de eventos, pode criar-se um relógio lógico para marcar a sequência de eventos e determinar a ordem correta em que eles aparecem no tempo.

Num **modelo de falhas**, uma avaria é qualquer alteração do comportamento do sistema em relação ao esperado, que pode atingir processos ou canais de comunicação:
* **Avarias por omissão** - um processo deixa de funcionar em algum ponto do sistema; o canal de comunicação falha:
  * *Fail-stop* - o processo bloqueou e esse bloqueio pode ser detetado por outros processos;
  * *Crash* - o processo aparentemente bloqueou, mas não é possível garantir que apenas deixou de responder por estar muito lento ou porque as mensagens que enviou não chegaram;
  * *Omission* - uma mensagem colocada no *buffer* de emissão nunca chega ao *buffer* de receção;
  * *Send-omission* - uma mensagem perde-se entre o emissor e o *buffer* de emissão;
  * *Receive-omission* - uma mensagem perde-se entre o *buffer* de receção e o recetor;
* **Avarias arbitrárias** (bizantinas) - qualquer erro pode acontecer no processo (não responde, corrompido, responde de forma errada, responde fora de tempo) ou no canal de comunicação (mensagens corrompidas, não entregues, duplicadas, entrega de mensagens inexistentes);
* **Avarias em tempo** - ocorrem quando o tempo limite para um evento ocorrer é ultrapassado. Em sistemas síncronos, é indicativo seguro de falha.

Num **modelo de segurança** há proteção das entidades do sistema, especificando direitos de acesso que definem que entidades podem aceder, e de que forma, a que recursos. O servidor é responsável por verificar a identidade de quem fez o pedido e verificar se essa entidade tem direitos de acesso para realizar a operação pretendida. O cliente deverá verificar a identifade de quem lhe enviou a resposta, para ver se a resposta veio da entidade esperada. As ameaças são classificadas em relação a:
* Processos - os protocolos de rede não oferecem proteção para que o servidor saiba a identidade do servidor, e um cliente também não dispõe de métodos para validar as respostas de um servidor;
* Canais de comunicação - um processo inimigo pode copiar, alterar ou injetar mensagens na rede; a comunicação pode ser violada por processos que observam a rede à procura de mensagens significativas;
* Negação de serviço - um processo intruso captura uma mensagem de solicitação de serviço e retransmite-a inúmeras vezes ao destinatário, fazendo-o executar sistematicamente o mesmo serviço e ultrapassando a sua capacidade de resposta.

Um **canal seguro** é um canal utilizado para comunicação entre dois processos, em que cada processo pode identificar com cem por cento de confiança a entidade responsável pela execução do outro processo, as mensagens que são transferidas de um proceso para outro são garantidas do ponto de vista da integridade e da privacidade, as mensagens têm garantia de não repetibilidade ou reenvio por odem distinta. **Criptografia** é a técnica de codificar o conteúdo de uma mensagem de forma a esconder o seu conteúdo, sendo necessário que ambos os processos possuam a chave de (des)codificação. A **autenticação** inclui na mensagem uma porção encriptada que contém informação suficiente para identifiar a entidade e verificar os seus direitos de acesso.

Para criar um **modelo de segurança**, analisam-se as principais ameaças, riscos envolvidos e possíveis consequências, e faz-se o balanço entre o custo de proteger o sistema e o risco que de facto as ameaças representam.

O **tempo** precisa de ser medido com elevada precisão e de forma consistente pelos diversos componentes de um sistema, sendo crucial na ordenação de eventos. O tempo real é uma função monótona contínua e crescente. Sistemas distribuídos usam tempo para: registar e observar a localização de eventos na *timeline* e forçar o futuro posicionamento de eventos na *timeline*, através de um *timestamp* (sequência de carateres que marcam a data e/ou tempo no qual um certo evento ocorreu).

Para comparar a duração de vários acontecimentos pode usar-se intervalos de tempo (cadeia de tempo composta por vários intervalos adicionados), *timers*/relógios locais (implementam a abstração da *timeline*).

**Tempo global** implementa a abstração de um tempo universal, através de um relógio que fornece o mesmo tempo a todos os participantes no sistema. **Tempo absoluto** são padrões universalmente ajustados, disponíveis como fontes de tempo externo para o qual qualquer relógio interno se pode sincronizar.

A sincronização pode ser **interna** (relógios têm de obter precisão relativamente a um tempo interno ao sistema) ou **externa** (relógios têm de estar sincronizados com uma fonte externa de tempo universal).

---
---

## Aulas Práticas

### Aula 00

***Stream*** - abstração que representa uma fonte genérica de entrada de dados ou um destino genérico para escrita de dados que é definida independentemente do dispositivo físico concreto.

### Aula 01

**Protocolo UDP** (*User Datagram Protocol*) - protocolo de transporte sem conexão que não garante a entrega de todos os pacotes de dados nem garante a entrega por ordem de envio.

**4.a) Experimente eliminar (terminar) o processo cliente. O que acontece?** Nada.

**4.b) E se eliminar (terminar) o processo servidor?** Se o processo cliente envia uma mensagem, esta nunca é recebida.

**4.c) Investigue quais as alterações que deve colocar no cliente para este gerar um *timeout* quando não recebe uma resposta do servidor no espaço de 10 segundos.** Inserir um *timeout* sobre o mesmo *socket* e implementar um *try-catch* para tentar receber a mensagem enviada, que deve terminar o ciclo *while* se se ultrapassar o tempo definido no *timeout*.

### Aula 02

**1.a) O que acontece se tentar executar este programa?** O primeiro `sysout` indica a abertura do processo cliente, mas o programa é interrompido por problemas de conexão ao *socket*.

**1.e) Modifique o Cliente e o Servidor das alíneas a) e b) de forma a ambos efectuarem primeiro as operações de leitura no *socket* e depois as operações de escrita. O que acontece?** Ambos são iniciados, mas ambos ficam à escuta de mensagens indefinidamente.

**1.e) Modifique o Cliente e o Servidor das alíneas a) e b) de forma a ambos efectuarem primeiro as operações de escrita no *socket* e depois as operações de leitura. O que acontece?** A comunicação entre processos pelo *socket* decorre normalmente.

### Aula 03

***Threads*** - conjunto de instruções que pode ser escalonado para execução num dado processador que partilham o mesmo espaço de endereçamento que o processo principal que lhes deu origem.

**Interface** - conjunto de métodos que a(s) classe(s) que implementa(m) essa interface terá(ão) de implementar.

***Thread Daemon*** - *thread* usualmente usada para executar serviços em *background*, que termina automaticamente após todas as *threads* "normais" terem terminado, obtida pelo método `setDaemon()`.

### Aula 04

**Sincronização de threads** - cada objeto tem associado um monitor que pode ser ativado se a palavra-chave `synchronized` for usada na definição de pelo menos um método de instâcia. Se várias *threads* invocarem um método declarado como `synchronized` em simultâneo, o monitor associado ao objeto garantirá a execução desse método em exclusão mútua.

### Aula 06

***Remote Object Reference*** - outros objetos podem invocar os métodos de um objeto remoto se tiverem acesso à sua referência remota.

***Remote Interface*** - cada objeto remoto tem de possuir uma interface remota que especifica quais dos seus métodos podem ser invocados remotamente.

***RMI Registry*** - serviço de nomes que faz a gestão das referências remotas para o sistema RMI. O servidor tem de registar o objeto no `registry`, permitindo aos clientes obter a referência do objeto remoto.