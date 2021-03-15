# Redes de Computadores

## Apontamentos

### Aulas Teóricas

Redes de computadores classificam-se quanto a:
* **Área espacial / geográfica**
  *  BAN (_Body Area Network_) - intracorporal (por exemplo, dispositivo para diabéticos _Libre_);
  *  PAN (_Personal Area Network_) - metro quadrado;
  *  LAN (_Local Area Network_) - divisão, edifício, campo;
  *  MAN (_Metropolitan Area Network_) - cidade;
  *  WAN (_Wide Area Network_) - país, continente;
  *  Internet - planeta;
  *  Rede interplanetária - galáxia (por exemplo, ligações entre Terra e Marte);
* **Topologia** - variam consoante as conexões físicas e lógicas:
  * Barramento (_bus_) - vários equipamentos partilham o mesmo meio de acesso (por exemplo, _wifi_). Defeitos: _hidden node_ (quando um nodo pode comunicar com um ponto de acesso sem fios (AP), mas não consegue comunicar com outros nodos que comuniquem com esse mesmo AP);caso um elemento pare, toda a rede deixa de funcionar (*mas não devia dar para voltar atrás? perguntar*);
  * Ponto a ponto - dois equipamentos a partilhar o mesmo meio de acesso. Defeitos: tipologia bastante limitada;
  * Anel (_ring_) - barramento fechado que permite redundância. 
  * Estrela (_star_) - uma máquina central concentra toda a comunicação da rede. Defeitos: Se a máquina central parar, toda a rede para;
  * Malha (_mesh_) - não existe organização definida; rede dinâmica que pode variar várias vezes por dia. Defeitos: não é prática numa rede pequena;
* **Canal**
  * Cablado - cabo ótico, cabo elétrico;
  * Não cablado (sem fios) - laser, infravermelhos, microondas, eletromagnetismo (utilizados na _wifi_);
* **Transmissão de dados**
  * _Simplex_ - transmissão de um só sentido entre um ponto A e um ponto B;
  * _Duplex_ - transmissão bidirecional entre um ponto A e um ponto B;
  * _Half-Duplex_ - transmissão bidirecional não simultânea entre um ponto A e um ponto B (um só cabo que só transmite ou só recebe);
  * _Full-Duplex_ - transmissão bidirecional simultânea entre um ponto A e um ponto B (dois cabos: um para transmitir, outro para receber);
* **Tipos de comunicação**
  * Circuito dedicado - o computador emissor estabelece um circuito com o computador recetor, o qual recebe os dados sem restrições (enquanto o circuito está estabelecido, apenas estas duas máquinas transmitem dados naquele segmento);
  * Canal partilhado - o computador emissor envia dados para o canal, identificando o recetor da mensagem; todos os computadores recebem, mas só o destinatário interpreta a mensagem (não é preciso predefinir circuitos, havendo melhor aproveitamento dos recursos físicos (tempo, canal)). Problemas: menor privacidade, só pode haver uma transmissão de cada vez;
* **Redes e Serviços Internet**
  * Computadores: redes de acesso (tributárias) - geram tráfego;
  * Rede interior: rede de transporte (_backbone_, rede nuclear) - transporta tráfego, resistente a problemas técnicos;
  * Equipamentos interno: pontos de agregação de tráfego - junção de tráfegos para transporte.
* **Multiplexagem de canal**
  * No tempo - síncrono (STDM), assíncrono (ATDM);
  * Em frequência - xDSL (_x Digital Subscriber Line_), WDM (_Wavelength Division Multiplexing_);
* **ISP** (_Internet Service Provider_)
  * ISP _Tier_ 1 - implementação física;
  * ISP _Tier_ 2 - aluguer da implementação física no _Tier_ 1;
  * ISP _Tier_ 3 - aluguer da implementação física no _Tier_ 2...;
* **Elementos**
  * Ativos (cabos);
  * Passivos (armários);
* **Redes de Pacotes de Dados**
  * Pacote / Datagrama (_packet_)
  * Trama / Quadro (_frame_)
    * **Organização:** PRE (preâmbulo, 7 bytes, avisar que irá ser transmitido algo); SFD (_Start-of-Frame Delimiter_, 1 byte); DA (_Destination Address_, 6 bytes); SA (_Source Address_, 6 bytes); _Length / Type_ (4 bytes); Dados (_Data_, _Pad_, 46 a 1500 dados); FCS (_Frame Check Sequence_, 4 bytes);
      * O FCS é gerado do SFD à Pad e o erro é detetado do SFD à FCS final;
* **Relação de Funcionalidade**;
* **Tipo de Protocolos**;...

O CODEC estipula o nível de redundância da mensagem para poder ser mais imune ao ruído do canal e para poder transmitir de forma eficiente um determinado conteúdo. A mensagem codificada tem de ser representada em sinais elétricos, óticos ou eletromagnéticos para poder ser transmitida com eficiência no canal. Há diferentes tipos de codificação (diapositivo 8 da aula 2B):
* _Nonreturn-to-Zero-Level_ (NRZ-L) - 0 = nível alto, 1 = nível baixo;
* _Nonreturn-to-Zero-Inverted_ (NRZI) - 0 = sem transição no princípio do intervalo, 1 = mudança de nível;
* Bipolar-AMI - 0 = sem nível, 1 = nível alto ou baixo (alternados) (três estados diferentes);
* Pseudoternárnio - 0 = nível alto ou baixo (alternados), 1 = sem nível (três estados diferentes);
* Manchester - 0 = alto baixo, 1 = baixo alto;
* _Differential Manchester_ - 0 = muda de nível ao princípio do bit, 1 = não muda de nível ao princípio do bit.

O BER (_Bit Error Rate_) é o rácio de bits que têm erro numa comunicação e o SNR (_Signal to Noise Ratio_) é a relação (normalmente medida em decibeis) entre o sinal e o ruído. Existem códigos que:
* Detetam erros:
  * Códigos de verificação de paridade;
  * _Cyclic Redundancy Check_ (CRC) / Códigos Polinomiais ou _Frame Check Sequence_ (FCS) - são códigos que transmitem além da mensagem inicial o resto da divisão dessa mensagem por polinómios conhecidos pelo emissor e recetor; detetam todos os erros em dois bits, todos os erros num número ímpar de bits, todos os erros num bloco menor que 16 bits, quase todos os erros (99.9%) num bloco maior ou igual que 16 bits;
* Detetam e corrigem erros - aumentam o tamanho dos dados a transmitir (mais funcionalidades => necessidade de mais informação => mais bits para transmitir):
  * Códigos de Hamming;
  * Códigos de Reed-Solomon;
  * Códigos convolucionais.

**Modelo TCP/IP**:
* Camada Física (1)
* Camada de Ligação de Dados (2)   // CAMADA FÍSICA E CAMADA DE LIGAÇÃO DE DADOS SÃO CORRESPONDENTES? OU A CAMADA FÍSICA SIMPLESMENTE NÃO EXISTE NO TCP IP, MAS SIM NO OSI?
* Camada de Redes
* Camada de Transporte
* Camada de Aplicação
**Modelo OSI (_Open Systems Interconnection_)** - concetual, não implementado fisicamente:
* Camada **Física** (1)
* Camada de **Ligação de Dados** (2)
  * Responsável por transmitir dados sobre um canal físico;
  * Funcionalidades: endereçamento físico, isolamento da topologia de rede;
  * Serviço não fiável (o recetor não envia ACKs (_Acknowledgment Code_) ao emissor para validar a boa receção das tramas) e sem conexão (não existe estabelecimento de um circuito virtual (_handshake_) entre o emissor e o recetor);
  * Possui duas subcamadas:
    * _Link Layer Control_ (LLC) - faz a multiplexagem dos protocolos das camadas superiores e controla erros;
    * _Media Access Control_ (MAC) - controla o acesso ao meio físico, implementando algoritmos de controlo / resolução de colisões CSMA (_Carrier-Sense Multiple Access); // ESTA SUBCAMADA MAC É EQUIVALENTE AO ENDEREÇO MAC? OU SÃO DUAS COISAS COM O MESMO NOME MAS QUE NÃO SÃO IGUAIS?
* Camada de **Redes**
* Camada de **Transporte**
* Camada de **Sessão**
* Camada de **Apresentação**
* Camada de **Aplicação**
  * Mnemónica: _People Desperately Need To See Pamela Anderson_ (ascendente) // _All People Seem To Need Data Processing_ (descendente)

`255 dec = 11111111 bin = FF hex`

O **endereço MAC** (_Media Access Control_) faz endereçamento ao nível da ligação e é necessário para encaminhar uma trama de um interface para outro interface da mesma rede. É armazenado na EPROM do computador (placa de rede) e escreve-se em notação hexadecimal com separador `:`, `.` ou `-`. São geridos pelo IEEE (_Institute of Electrical and Electronics Engineers_) e devem ser únicos numa LAN.

As **tabelas ARP** (_Address Resolution Protocol_) são locais para cada máquina e permitem que uma comunicação crie uma trama _ethernet_ com o endereço MAC associado ao endereço IP de destino. São dinâmicas, construídas a cada nova comunicação, e constituídas por endereços IP, endereços MAC e TTL (_Time To Live_).

O endereço _default gateway_ (só configurado nos clientes) é o endereço da interface mais próxima do router mais próximo. Serve para conseguir enviar tramas de computadores para o router.

`sh ip route` -> código que, aplicado num router, que mostra a tabela de rotas IP conhecidas pelo router (tabela de routing).

O **hub** atua no nível 1 (físico) e interliga segmentos de uma rede, permitindo aumentar a máxima distância entre nós, embora não isole os segmentos a nível de colisões. (obsoleto)

O **switch** atua no nível 2 (ligação) e armazena e encaminha frames Ethernet com base no endereço MAC de destino, diminuindo o nível de colisão a cada segmento, utilizando o protocolo CSMA/CD para garantir o acesso. É um dispositivo **transparente**, ou seja, são _plug-and-play self-learning_ e não precisa de ser configurado. Executam filtragem (_filtering_, determinar se uma trama deve ou não ser encaminhada para uma área da rede [VLANs, _Virtual Local Area Network_]) e encaminhamento (_forwarding_, determinar para que área da rede uma trama deve ser encaminhada). Vários switches não podem criar uma rede em anel, derivado ao _spanning tree protocol_ (STP). Cada switch mantém uma _switch table_, que mostra os endereços MAC conhecidos pelo switch, interface e _time stamp_, a que se acede pelo comando `sh mac address-table`. O switch memoriza os endereços dos dispositivos que estão ligados a cada uma das suas interfaces, cujos elementos (endereço MAC, interface, instante de chegada) são guardados na tabela de switching e eliminados ao final de um período de tempo quando não são recebidas novas frames. Quando um switch recebe uma trama:
* Extrai o endereço MAC de origem da trama e procura o endereço na tabela de switching:
  * Se encontrar, não executa quaisquer operações;
  * Se não encontrar, cria um novo elemento com esse endereço, nome da interface recetora e instante de chegada;
* Extrai o endereço MAC de destino da trama e procura o endereço na tabela de switching:
  * Se encontrar e se a interface é a mesma por onde a trama chegou, então descarta a trama;
  * Se encontrar e se a interface é diferente, encaminha a trama para a interface associada;
  * Se não encontrar, propaga a trama para todas as interfaces, exceto a de chegada.

**Switches** e **Routers** são ambos dispositivos _store-and-forward_. Routers examinam e mudam o cabeçalho do pacote/datagrama (nível 3), implementando algoritmos e tabelas de routing através de ligações em anel. Switches examinam o cabeçalho da trama (e podem alterá-lo em VLANs; nível 2), mantêm tabelas de switching e implementam algoritmos de filtragem e manutenção da prevenção de ciclos, não devendo ser ligados em anel.

**Bridges** são equipamentos que atuam no nível 2 e ligam várias redes diferentes no nível físico ou de ligação, mas com o mesmo protocolo no nível de rede ou transporte, permitindo a criação de uma rede homogénea, possuindo uma tabela dinâmica que contém todos os endereços de rede, e podem impedir a passagem de certos tipos de pacotes.

Algoritmo CSMA/CD Ethernet:
* O adaptador recebe o datagrama do nível de rede e constrói uma trama;
* Se o adaptador detetar que o canal está livre, começa a transmitir (senão espera que fique livre);
  * Se o adaptador conseguir transmitir a trama até ao fim sem que haja colisões, a transmissão é um sucesso;
  * Se o adaptador detetar uma colisão, interrompe a emissão e envia sinal de engarrafamento, tentando ao final de algum tempo (_exponential backoff_) enviar uma nova transmissão.

---

### Aula Prática 1

DHCP -> endereço de rede não estático de uma rede sem fios com autenticação pelo MAC Address (não há dois MAC Address's iguais)

O _subnet mask_ indica a gama de valores que é possível utilizar num código IPv4, ou seja, determina a quantidade de máquinas que é possível ligar à rede (por exemplo, 255.255.255.0 [base decimal] == 11111111.11111111.11111111.00000000 [base binária]). Em IPv4 tem-se quatro conjuntos de 256 símbolos:
* 192.168.1.0                 -> código IPv4 de identificação da rede;
* 192.168.1.1 - 192.168.1.254 -> código IPv4 de identificação da máquina;
* 192.168.1.255               -> código IPv4 de identificação do endereço de broadcast.

Num _hub_, toda a informação é partilhada com todos os dispositivos (o que provoca maior colisão e consequente maior degradação dos componentes). Num _switch_, pode haver várias redes independentes com segmentação de tráfego (certos componentes só se relacionam com outros determinados componentes).

Para evitar / diminuir o efeito de ataques informáticos e impedir grandes danos por falhas técnicas, deve haver vários pontos de acesso, circuitos redundantes e implementação de _firewalls_ (sendo necessário entender como é que as informações são trocadas).

As tabelas ARP (_Address Resolution Protocol_) ligam o IP de cada máquina ao seu MAC Address após o envio de pacotes por `ping`. Uma tabela ARP é normalmente constituída por: endereço de internet, endereço físico, tipo.

_Top Level Domain_ são máquinas servidores de DNS que permitem associar nomes a IP's.

Máquinas iguais ligam-se com cabos cruzados.

2.3. `arp -a`
2.4. `ping <endereço-computador-recetor>`
2.5. Não, porque são endereços diferentes.
2.6. A. IP e subnet mask.
     B. Protocolo DHCP.
     C. `255.255.255.0`
     D. Classe C. (verificar tabela de classes de IP's)
     E.
3.5. Não, porque são endereços diferentes.
4. `ipconfig`
5. Não sei

### Aula Prática 2

2.1.1. a) `enable`
2.1.2. b) `show running-config`
2.2.1. `enable` > `configure terminal` > `hostname nome`
2.2.2. a) `line con 0` > `password passe` > `login` > `service password-encrypt`
2.2.4. a) `enable` > `enable secret passe`
4. `banner motd #texto#`
5.2. `copy running-config startup-config` > Config > Startup Config > Export...
8.2. `enable` > `configure terminal` > `hostname nome`
9.1.1. `enable` > `interface fastEthernet 0/0` > `ip address 192.168.1.1 255.255.255.0` > `no shutdown` > `description descricao`
(para a primeira porta fastEthernet)
12.  _Default Gateways_ servem para especificar um endereço IP predefinido para onde são enviados todos os pacotes de uma rede.

### Aula Prática 3

Para definir uma rede, é necessário IP, máscara, _gateway_ e domínio (DNS [_Domain Name System_]), usando DHCP (_Dynamic Host Configuration Protocol_).
11. Os domínios de email devem ser adicionados ao servidor DNS para que todos os dispositivos ligados ao servidor os reconheçam.
