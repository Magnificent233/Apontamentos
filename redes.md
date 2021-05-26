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
  * Barramento (_bus_) - vários equipamentos partilham o mesmo meio de acesso (por exemplo, _wifi_). Defeitos: _hidden node_ (quando um nodo pode comunicar com um ponto de acesso sem fios (AP), mas não consegue comunicar com outros nodos que comuniquem com esse mesmo AP); caso um elemento pare, toda a rede deixa de funcionar;
  * Ponto a ponto - dois equipamentos a partilhar o mesmo meio de acesso. Defeitos: tipologia bastante limitada;
  * Anel (_ring_) - barramento fechado que permite redundância;
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
  * Equipamentos internos: pontos de agregação de tráfego - junção de tráfegos para transporte.
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
    * **Organização:** PRE (preâmbulo, 7 bytes, avisar que irá ser transmitido algo); SFD (_Start-of-Frame Delimiter_, 1 byte); DA (_Destination Address_, 6 bytes); SA (_Source Address_, 6 bytes); _Length / Type_ (4 bytes); Dados (_Data_, _Pad_, 46 a 1500 bytes); FCS (_Frame Check Sequence_, 4 bytes);
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
* Camada de Ligação de Dados (2)
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
    * _Media Access Control_ (MAC) - controla o acesso ao meio físico, implementando algoritmos de controlo / resolução de colisões CSMA (_Carrier-Sense Multiple Access_);
* Camada de **Redes**
* Camada de **Transporte**
* Camada de **Sessão**
* Camada de **Apresentação**
* Camada de **Aplicação**
  * Mnemónica: _People Desperately Need To See Pamela Anderson_ (ascendente) // _All People Seem To Need Data Processing_ (descendente)

`255 dec = 11111111 bin = FF hex`

O **endereço MAC** (_Media Access Control_) faz endereçamento ao nível da ligação e é necessário para encaminhar uma trama de uma interface para outra interface da mesma rede. É armazenado na EPROM do computador (placa de rede) e escreve-se em notação hexadecimal com separador `:`, `.` ou `-`. São geridos pelo IEEE (_Institute of Electrical and Electronics Engineers_) e devem ser únicos numa LAN.

As **tabelas ARP** (_Address Resolution Protocol_) são locais para cada máquina e permitem que uma comunicação crie uma trama _ethernet_ com o endereço MAC associado ao endereço IP de destino. São dinâmicas, construídas a cada nova comunicação, e constituídas por endereços IP, endereços MAC e TTL (_Time To Live_).

O endereço _default gateway_ (só configurado nos clientes) é o endereço da interface mais próxima do router mais próximo. Serve para conseguir enviar tramas de computadores para o router.

`sh ip route` -> código que, aplicado num router, mostra a tabela de rotas IP conhecidas pelo router (tabela de routing).

O **hub** atua no nível 1 (físico) e interliga segmentos de uma rede, permitindo aumentar a máxima distância entre nós, embora não isole os segmentos a nível de colisões. (obsoleto)

O **switch** atua no nível 2 (ligação) e armazena e encaminha frames Ethernet com base no endereço MAC de destino, diminuindo o nível de colisão a cada segmento, utilizando o protocolo CSMA/CD para garantir o acesso. É um dispositivo **transparente**, ou seja, é _plug-and-play self-learning_ e não precisa de ser configurado. Executa filtragem (_filtering_, determinar se uma trama deve ou não ser encaminhada para uma área da rede [VLANs, _Virtual Local Area Network_]) e encaminhamento (_forwarding_, determinar para que área da rede uma trama deve ser encaminhada). Vários switches não podem criar uma rede em anel, derivado ao _spanning tree protocol_ (STP). Cada switch mantém uma _switch table_, que mostra os endereços MAC conhecidos pelo switch, interface e _time stamp_, a que se acede pelo comando `sh mac address-table`. O switch memoriza os endereços dos dispositivos que estão ligados a cada uma das suas interfaces, cujos elementos (endereço MAC, interface, instante de chegada) são guardados na tabela de switching e eliminados ao final de um período de tempo quando não são recebidas novas frames. Quando um switch recebe uma trama:
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

Toda a transmissão de dados feita em redes tem três bases fundamentais: esquema de endereçamento, protocolos comuns e negociação formatada. A camada 3 (de rede) serve para:
* Encapsular segmentos em pacotes no emissor (no emissor);
* Encaminhar pacotes do emissor ao recetor (no meio da rede);
* Entregar os segmentos ao nível de transporte no recetor (no recetor);
* Implementar os protocolos ao nível de rede em todos os _hosts_ (computadores e routers);
* Examinar o _header_ de todos os pacotes (no router).

Há dois tipos de _routing_:
* **_Cut-through_** - o router começa a transmitir o pacote recebido assim que interpreta o cabeçalho;
* **_Store-and-forward_** - o pacote é recebido, armazenado, processado e retransmitido.

O _Internet Protocol_ (IP) foi criado em 1974 por Vint Cerf e Bob Khan. O IPv4 é referenciado pela primeira vez na RFC 791 (setembro de 1981) e o IPv6 na RFC 2460 (1998). Nas redes IP só há dois tipos de endereços:
* **IPv4** - do tipo 192.168.4.3, podem ser públicos (usados em redes locais) ou privados (uso cobrado aos utilizadores finais, visíveis por todas as outras máquinas da Internet, incluindo as que estão dentro de uma rede local), cujos blocos são atribuídos pela IANA (_Internet Assigned Numbers Authority_);
* **IPv6** - podem ser públicos ou _Unique Local Addresses_.

Um datagrama IPv4 contém **versão** (4 bits), **comprimento do cabeçalho** (IHL, 4 bits), **tipo de serviço** (8 bits), **comprimento total** (16 bits), **identificação** (16 bits), **_flags_** (3 bits), **_offset_** (13 bits), **time to live** (TTL, 8 bits), **protocolo** (8 bits), **_header checksum_** (16 bits), **endereço de origem** (32 bits), **endereço de destino** (32 bits), **opções** (32 bits). Um datagrama IPv6 contém **versão** (4 bits), **classe de tráfego** (8 bits), **_flow label_** (20 bits), **_payload length_** (16 bits), **_header_ seguinte** (8 bits), **_hop limit_** (8 bits), **endereço de origem** (128 bits), **endereço de destino** (128 bits).

Os endereços IP podem ser de várias classes:
* **Classe A:** `net.host.host.host`
  * Endereços: rede (8 bits), _host_ (24 bits) - de 1.0.0.0 a 127.255.255.255;
  * Máscara de rede: 255.0.0.0;
* **Classe B:** `net.net.host.host`
  * Endereços: rede (16 bits), _host_ (16 bits) - de 128.0.0.0 a 191.255.255.255;
  * Máscara de rede: 255.255.0.0;
* **Classe C:** `net.net.net.host`
  * Endereços: rede (24 bits), _host_ (8 bits) - de 192.0.0.0 a 223.255.255.255;
  * Máscara de rede: 255.255.255.0;
* **Classe D:** `multicast`
  * Endereços: endereço _multicast_ (32 bits) - de 224.0.0.0 a 239.255.255.255;
  * Máscara de rede: não aplicável;
* **Classe E:** `research`
  * Endereços: reservado para uso futuro (32 bits) - de 240.0.0.0 a 255.255.255.255;
  * Máscara de rede: não aplicável.

A máscara de rede é utilizada localmente com o endereço de origem ou com o endereço local para determinar se a máquina está dentro ou fora da subrede. Os datagramas IP são divididos em 'fragmentos' pela rede e assemblados no destino, com os bits do _header IP_ usados para identificação e ordenação.

Na entrega de pacotes, é importante ter em conta o atraso (_delay_), a irregularidade de tempo de separação entre pacotes (_jitter_) e a perda (_loss_), quando aplicadas a um pacote isolado ou a um fluxo de pacotes (_flow_). Nas redes de pacotes não existe estabelecimento de conexão no nível de rede, os routers não guardam o estado relativamente às conexões _end-to-end_ e os pacotes são encaminhados usando o endereço _host_ de destino (podendo seguir rotas diferentes). A determinação do caminho a seguir em cada router é feita pela análise do endereço de destino (pela tabela de encaminhamento, que associa um intervalo de redes a um interface de saída, enviando depois o pacote pela interface associada ao intervalo a que pertence o endereço de destino - usando o conceito de _hot potato routing_, de Paul Baran). As tabelas de encaminhamento podem ser:
* **Estáticas:** permitem a definição de políticas de encaminhamento, mas em caso de avaria exigem reconfiguração do router;
* **Dinâmicas:** permitem que pacotes com o mesmo destino sigam pelo caminho ativo, exigindo uma atualização permanente.

Os endereços das tabelas de encaminhamento são obtidos por _Classless InterDomain Routing_ (CIDR), em que cada zona de rede tem um comprimento arbitrário de formato `xxx.yyy.zzz.kkk / nn`, em que `nn` é o número de bits do endereço de rede - _routing_ por intervalos ou por classes -, ou por _prefix matching_ - comparação da parte mais significativa de cada endereço.

Os algoritmos de _intra-domain routing_ devem ser corretos, ótimos, eficientes, robustos, estáveis, justos (_fairness_) e simples. Podem ser:
* **_Link State_:** cada router troca informações com todos os routers da rede sobre os seus vizinhos (routers diretamente ligados) quando há uma mudança na rede (se um router vizinho não responde a uma mensagem), havendo inundação (_flood_) de informação na rede. Tem rápida convergência, alta quantidade de tráfego e resposta rápida a mudanças (_Open Shortest Path First_ (OSPF), _Intermediate System to Intermediate System_ (IS-IS)), no entanto, o algoritmo _Dijkstra_ é muito pesado para os processadores, muitas mudanças implicam muitas atualizações e usa-se _reliable flooding_ para os pacotes;
* **_Distance Vector_:** cada router troca informações de toda a rede com os seus vizinhos em intervalos regulares (_Routing Information Protocol_ (RIP), de onde deriva o _Border Gateway Protocol_ (BGP), que determina as rotas entre _Autonomous Systems_ (AS), partes da Internet geridas por uma dada entidade). Pode ocorrer _count-to-infinity_, baixa convergência e baixa fidelidade em caso de falhas de _links_.

No _routing_ hierárquico, os routers são agregados em regiões (_autonomous systems_ (AS)), onde todos correm o mesmo protocolo (_"intra-AS" routing protocol_) e um deles é o router de _gateway_, que também é responsável por dar _routing_ aos endereços fora da AS (_"inter-AS" routing protocol_). Em _inter-AS_, o administrador controla como o tráfego é navegado e quem navega na sua rede; em _intra-AS_ não há decisões de política porque só há um administrador, o que aumenta o foco na _performance_. É poupado tamanho da tabela de _routing_ e o tráfego de atualização é reduzido. A internet global consiste de AS interconetadas entre si: _stub AS_ (pequena corporação), _multihomed AS_ (grande corporação, sem tráfego), _transit AS_ (fornecedor). 

---

A notação binária refere-se ao facto de os computadores apenas com 0s e 1s. Para definir uma rede e porções de um endereço, os dispositivos usam padrões separados de 32 bits - máscara de subrede - que indica onde procurar cada porção num dado IPv4.

Há três formas de transmitir em IPv4:
* **_unicast_** - processo de enviar um pacote de um anfitrião para outro anfitrião;
* **_broadcast_** - processo de enviar um pacote de um anfitrião para todos os anfitriões da rede;
* **_multicast_** - processo de enviar um pacote de um anfitrião para um grupo selecionado de anfitriões (na mesma rede ou em redes diferentes), reduzindo tráfego pelo uso de endereços exclusivos.

Em IPv4, os blocos de endereços privados são anfitriões que não requerem acesso à Internet  os endereços de espaço partilhado não são globalmente roteáveis e apenas usados para redes provedoras de serviços. Os endereços de uso especial são:
* _Network and Broadcast_ - dentro de cada rede, o primeiro e último endereços não podem ser atribuídos a anfitriões;
* _Loopback_ - endereço 127.0.0.1, que permite que os anfitriões usam para direcionar tráfego para si próprios;
* _Link Local_ - endereços automaticamente atribuídos ao anfitrião local;
* _TEST-NET_ - colocados à parte para propósitos de ensino e aprendizagem, usados em documentação e exemplos;
* _Experimental_ - reservados.

_Classless Addressing_ (ou _Classless Inter-Domain Routing_ (CIDR)) cria um novo conjunto de padrões que permite aos provedores de serviços alocar endereços IPv4 em qualquer limite de endereço. A atribuição de endereços IP é dado por _Regional Internet Registries_ (RIR): RIPE, APNIN, AFRINIC, LACNIC, ARIN, controladas pela _Internet Assigned Numbers Authority_ (IANA). Os ISP de _tier 1_ são serviços (inter)nacionais diretamente ligadas à _backbone_ da Internet; os de _tier 2_ focam-se em clientes empresariais e os de _tier 3_ oferecem conetividade à Internet a clientes particulares, a partir de serviços comprados aos de _tier 2_.

As técnicas de migração entre IPv4 e IPv6 podem ser divididos em:
* **_Dual-Stack_** - permite que IPv4 e IPv6 coexistam na mesma rede, correndo ambos os protocolos em simultâneo;
* **_Tunneling_** - transporte de um pacote IPv6 para uma rede IPv4, encapsulado dentro de um pacote IPv4 (e vice-versa);
* **_Translation_** - traduz um pacote IPv4 para IPv6 e vice-versa (_routing_ NAT64);

Em IPv6 há três tipos de endereços (não há _broadcast_):
* **_unicast_** - um pacote enviado para um endereço _unicast_ (identificação única de uma interface) é recebida pela interface atribuiu esse endereço. Podem ser:
  * _Global unicast_ - endereços públicos, roteáveis e configuráveis estática ou dinamicamente;
  * _Link local_ - endereços privados, não roteáveis, usados para comunicar com outros dispositivos dentro da mesma rede local;
  * _Loopback_ - endereço que permite enviar um pacote para si próprio;
  * _Unspecified_ - usado como endereço de origem quando o dispositivo não tem endereço IPv6 permanente ou quando a origem é irrelevante para o destino do pacote;
  * _Unique local_ - endereços privados, usados para comunicação numa rede ou entre um número limitado de redes;
  * _Embedded IPv4_ - endereço auxiliar na transição IPv4-IPv6;
* **_multicast_** - ;
* **_anycast_** - pedido _unicast_ que é respondido por duas máquinas diferentes que partilham o mesmo endereço de rede.

A atribuição dinâmica de endereços IPv4 é feita através de _Automatic Private IP Address_ (APIPA); e a de IPv6 é por _Stateless Address Autoconfiguration_ (SLAAC).

Os _routers_ são computadores especializados com CPU, sistema operativo, memória e armazenamento responsáveis pelo roteamento de tráfego entre redes, podendo ter múltiplas interfaces com endereços IP diferentes. _Routers_ usam rotas estáticas e protocolos de _routing_ dinâmico, utilizando as tabelas de _routing_ para determinar o melhor trajeto para enviar pacotes. Um _switch_ pode alterar um cabeçalho, sem nunca alterar o pacote; um _router_ pode não encapsular pacotes, mas analisa-os e fragmenta-os para envio. Para permitir o acesso à rede, os dispositivos devem ser configurados com a seguinte informação: endereço IP (anfitrião único numa rede local), máscara de subrede (subrede do anfitrião) e _default gateway_ (identificação do _router_ para onde é enviado o pacote quando o destino não pertence à mesma subrede).

O melhor trajeto é selecionado por um protocolo de _routing_ baseado no valor ou métrica usados para determinar a distância para atingir uma rede, escolhendo-se o menor. Os protocolos dinâmicos usam as suas próprias regras e métricas para construir e atualizar tabelas de _routing_: RIP (_Routing Information Protocol_, pelo número de saltos), OSPF (_Open Shortest Path First_, baseado na largura de banda cumulativa da origem ao destino), EIGRP (_Enhanced Interior Gateway Routing Protocol_, largura de banda, demora, carregamento, confiabilidade).

Uma tabela de _routing_ é um ficheiro guardado na RAM que contém informação sobre rotas diretamente conectadas, rotas remotas e associações de rede ou de próximo salto. As **rotas estáticas** devem ser implementadas manualmente após as interfaces diretamente conectadas serem adicionadas à tabela de _routing_, devendo ser atualizadas se houver alteração de topologia. As **rotas dinâmicas** são usadas para partilhar informação sobre a acessibilidade e estado de redes remotas, encontrando novas redes e mantendo tabelas de _routing_.

O **_routing_ estático** permite aumentar a segurança da rede, usar menor largura de banda (já que as rotas não gastam CPU para serem definidas) e a rota é conhecida. No entanto, há perda de tempo na configuração inicial e manutenção de rotas, a configuração é propensa a erros, requer a intervenção do administrador da rede para a manutenção das rotas, a manutenção de redes grandes ou em crescimento é inexequível, requer conhecimento completo de toda a rede para uma implementação funcional. Tem três usos primários: manutenção simples de redes pequenas ou definitivas; _routing_ de e para redes _stub_ (acedidas por uma única rota sem routers vizinhos); uso de uma única rede predefinida para representar uma rota para qualquer rede sem outra ligação. O _routing_ estático é usado para conetar uma rede específica, providenciar um _gateway_ de último recurso para uma rede _stub_, reduzir o número de rotas ao sumarizar diversas redes contíguas como uma única rota estática, criar uma rota de _backup_.

A **sumarização de rotas** (ou agregação de rotas) é o processo de propagar um conjunto contíguo de endereços como um único endereço menos específico, com uma menor máscara de rede, reduzindo o número de entradas em atualizações de _routing_ e em tabelas locais de _routing_.

Uma VLAN é uma partição lógica da camada dois de uma rede feita num switch, sendo um domínio de _broadcast_ usualmente com a sua própria rede IP. VLANs podem ser múltiplas e mutuamente isoladas, e pacotes só podem passar entre elas através de um router. VLANS aumentam segurança, reduzem custos, aumentam performance, diminuem domínios de _broadcast_, aumentam a eficácia dos técnicos e simplificam a gestão de processos e aplicações.

Uma VLAN pode ser de dados, geral, nativa ou de gestão. As VLANs de voz são sensíveis ao tempo e requerem largura de dados garantida para assegurar qualidade, transmissão prioritária relativamente a outros tipos de tráfego de rede, capacidade de ser transmitidas em zonas de rede congestionadas, atraso menor do que 150 milissegundos através da rede. Um _trunk_ VLAN carrega mais do que uma VLAN e é usualmente estabelecido entre switches para que dispositivos dentro da mesma VLAN possam comunicar entre si.

A camada de transporte controla as comunicações individuais entre as aplicações de origem e destino; segmenta os dados para garantir que cabem nos PDUs das camadas inferiores e reassembla os dados recebidos numa _data stream_; identifica as aplicações que correspondem a cada um dos _data streams_. A comunicação pode ser _connectionless_ (_User Datagram Protocol_ (UDP)), _connection oriented_ (_Transmission Control Protocol_, (TCP)), entre outros. O TCP é orientado à ligação (exige um _handshake_ e envia os dados em qualquer direção após se estabelecer o circuito virtual), é fiável, ordenado, pesado e cria _flow_ de pacotes; o UDP não considera o estado do recetor, não é fiável, ordenado, é leve, as mensagens não são fragmentadas, não há controlo de congestão.

Numa transmissão UDP, o recetor não confirma a receção dos dados (_streaming media_, jogos multijogador, _voice over IP_, _Domain Name System_ (DNS), _Simple Network Management Protocol_ (SNMP), _Routing Information Protocol_ (RIP), _Dynamic Host Configuration Protocol_ (DHCP)); os portos podem ser _portos bem conhecidos_, controlados pela IANA (0 - 1023), _portos registados_ (IANA, 1024 - 49151), _portos dinâmicos, efémeros ou privados_ (49152 - 65535):
* 20 (TCP) - FTP;
* 21 (TCP) - FTP control;
* 22 (TCP / UDP) - SSH;
* 23 (TCP) - TELNET;
* 25 (TCP) - SMTP;
* 53 (TCP/UDP) - DNS;
* 80 (TCP/UDP) - HTTP;
* 110 (TCP) - POP3;
* 443 (TCP) - HTTPS (sobre SSL/TLS).

Numa transmissão TCP, o cliente usa portos bem conhecidos como porto de destino e portos aleatórios como portos de origem, e o servidor usa o porto de destino do pedido como porta de origem e o porto de origem do pedido como porto de destino. Usa-se um _handshake_ SYN ACK (_synchronize_ _acknowlegment_) para iniciar e um FIN ACK (_final_ _acknowledgment_) para terminar. O tamanho da janela determina o número de bytes enviados antes do _acknowledgment_, que toma o valor do próximo byte esperado. Se os segmentos são perdidos devido à congestão, o recetor vai reconhecer o último segmento sequencial recebido e responder com uma janela de tamanho menor. Datagramas e segmentos diferentes podem tomar rotas diferentes.

No UDP há _connectionless_, o _overhead_ é menor, há requerimentos de transmissão rápida, não há entrega garantida, não há reconhecimento de receção. No TCP há estabelecimento de sessão, segmentos de mensagem em sequência, entrega garantida, entrega ordenada e controlo de fluxo.

O PDU é a unidade de medida de dados de um protocolo. Na camada física (1) é o bit; na camada de ligação de dados (2) é a trama; na camada de rede (3) é o pacote; na camada de transporte (4) é o segmento; nas camadas de sessão, apresentação e aplicação (5, 6, 7) é variável (podendo ser dados ou mensagens).

A conexão sem fios permite maior flexibilidade e produtividade, redução de custos e capacidade de crescimento e adaptação para requerimentos em mudança. As redes _wireless_ podem ser classificadas como:
* _Wireless Personal-Area Network_ (WPAN);
* _Wireless LAN_ (WLAN);
* _Wireless Wide-Area Network_ (WWAN);
* _Bluetooth_ - WPAN IEEE 802.15;
* _Wireless Fidelity_ (Wi-Fi) - WLAN IEEE 802.11;
* _Worldwide Interoperability for Microwave Access_ (WiMax);
* _Cellular Broadband_ - organizações nacionais, internacionais e corporativas que utilizam acesso móvel para providenciar conetividade de rede de _broadband_ móvel;
* _Satellite Broadband_.

As frequências do espetro eletromagnético são, das menores para as maiores: energia e telefonia, ondas rádio (muito baixa frequência (VLF), baixa frequência (LF), média frequência (MF), alta frequência(HF), muito alta frequência (VHF), ultra alta frequência (UHF), super alta frequência (SHF), extremamente alta frequência (EHF)), infravermelhos, luz visível, ultravioletas, raios-X, raios gama, raios cósmicos.

Uma rede cablada é física, segue o protocolo CSMA/CD (deteção de colisões), requer ligação por cabos, não tem consequências de interferência de sinal e segue as regras impostas pelo IEEE. Uma rede _wireless_ é virtual, segue o protocolo CSMA/CA (evitação de colisões), tem interferência de sinal e requer regulação adicional das autoridades de cada país.

As antenas _wireless_ podem ser:
* Omnidirecionais - com cobertura de 360 graus;
* Direcionais - focam o sinal numa direção específica, aumentando o sinal de e para o _access point_ na direção em que a antena está a apontar;
* Yagi - tipo de antena direcional para rede Wi-Fi de longa distância.

A topologia de redes _wireless_ pode ser modo Ad Hoc, modo infraestrutural e _tethering_ (_hotspot_ pessoal). Uma _frame_ 802.11 é constituída por cabeçalho (controlo de _frame_, duração, endereço 1, endereço 2, endereço 3, controlo de sequência, endereço 4), _payload_ e FCS. Numa operação sem fios, os parâmetros de associação são:
* **SSID** - identificador único para distinção de redes sem fios múltiplas próximas;
* **Palavra-passe** - ou chave de segurança, para permitir a autenticação do cliente ao _access point_;
* **Modo de rede** - padrões WLAN 802.11a/b/g/n/ac/ad, que podem ou não ser utilizados em simultâneo;
* **Modo de segurança** - WEP, WPA, WPA2;
* **Definições de canal** - bandas de frequência usadas para transmitir dados _wireless_, que podem ser definidas manual ou automaticamente.

Um _access point_ pode ser descoberto em **modo passivo** (o AP anuncia o seu serviço através de _broadcast_ de _frames_ farol com SSID, padrões suportados e definições de segurança, que permitem aos clientes saber que redes e APs estão disponíveis numa dada área) ou em **modo ativo** (os clientes devem saber o nome do SSID e inicializam o processo ao transmitir uma _frame_ de pedido de sondagem, que inclui o SSID e padrões suportados). A autenticação pode ser **aberta** (se for direta) ou **de chave partilhada** (se é necessário haver uma palavra-passe partilhada _a priori_ entre cliente e AP).

Existem vários protocolos para enviar/receber emails: **SMTP** (_Simple Mail Transfer Protocol_, camada de aplicação, _standard_ para envio de emails (RFC 2821), cujo endereço está registado no campo MX do DNS), **POP** (_Post Office Protocol_ (RFC 1225)), **IMAP** (_Internet Message Access Protocol_ (RFC 3501)).

Uma _firewall_ controla os acessos do exterior ou do interior e decide que tráfego sai e entra com base em regras. Podem implementar outros serviços, como _proxying_ e _network address translation_ (NAT) e _federated authentication_ (RADIUS).

---

---

### Aula Prática 1

DHCP -> endereço de rede não estático de uma rede sem fios com autenticação pelo MAC Address (não há dois MAC Address's iguais dentro da mesma rede)

O _subnet mask_ indica a gama de valores que é possível utilizar num código IPv4, ou seja, determina a quantidade de máquinas que é possível ligar à rede (por exemplo, 255.255.255.0 [base decimal] == 11111111.11111111.11111111.00000000 [base binária]). Em IPv4 tem-se quatro conjuntos de 256 símbolos:
* 192.168.1.0                 -> código IPv4 de identificação da rede;
* 192.168.1.1 - 192.168.1.254 -> código IPv4 de identificação da máquina;
* 192.168.1.255               -> código IPv4 de identificação do endereço de broadcast.

Num _hub_, toda a informação é partilhada com todos os dispositivos (o que provoca maior colisão e consequente maior degradação dos componentes). Num _switch_, pode haver várias redes independentes com segmentação de tráfego (certos componentes só se relacionam com outros determinados componentes).

Para evitar / diminuir o efeito de ataques informáticos e impedir grandes danos por falhas técnicas, deve haver vários pontos de acesso, circuitos redundantes e implementação de _firewalls_ (sendo necessário entender como é que as informações são trocadas).

As tabelas ARP (_Address Resolution Protocol_) ligam o IP de cada máquina ao seu MAC Address após o envio de pacotes por `ping`. Uma tabela ARP é normalmente constituída por: endereço de internet, endereço físico, tipo.

_Top Level Domain_ são máquinas servidores de DNS que permitem associar nomes a IP's.

2.3. `arp -a`
2.4. `ping <endereço-computador-recetor>`
2.5. Não, porque pertencem a redes diferentes.
2.6. A. `Config` > `FastEthernet 0` > `Static` > `IPv4 Address + Submask`
     B. `Config` > `FastEthernet 0` > `DHCP`
        `Desktop` > `IPConfiguration` > `FastEthernet 0` > `Static` > `IPv4 Address + Submask`
        `Desktop` > `IPConfiguration` > `FastEthernet 0` > `DHCP`
     C. `255.255.255.0`
     D. Classe C. (_net.net.net.host_)
     E. Não. (?)
3.5. Não, porque pertencem a redes diferentes.
1. `ipconfig`
2. Zero.
6.1. Cabo direto - liga equipamentos (PCs, servidores, routers a switches, hubs ou bridges).
     Cabo cruzado - liga equipamentos da mesma camada segundo o modelo OSI.
6.2. Ambas as entradas fazem uso dos pares 2 e 3 do cabo (num total de 4).
6.3. As entradas do recebter e do transmissor são diferentes, com cabos trocados entre si.

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

### Aula Prática 4

3.2. `enable` > `show vlan`
3.11.1. `enable` > `show interface trunk`
3.11.2. A porta trunk permite o acesso simultâneo de clientes múltiplos à rede pela partilha de um conjunto de circuitos, transportadores, canais ou frequências, em vez de providenciar canais para cada cliente.
3.11.3. Não, porque as VLANs não conseguiriam comunicar entre si.
3.12. `copy running-config startup-config`
4.1.2. `int f0/0.5`
4.2. `show running-config`
4.3. `copy running-config startup-config`
5. `sh run`
11.3. O `ip helper-address` transmite um _broadcast_ para um único IP especificado.

* Passo 1 > criação das VLANs (switch)
  * `enable` > `configure terminal` > `vlan <num-vlan>` > `name <nome-vlan>`
* Passo 2 > configuração das interfaces (ligações do switch aos computadores)
  * `enable` > `configure terminal` > `int fa<interface>` > `switchport mode access` > `switchport access vlan <num-vlan>`
* Passo 3 > configuração da porta trunk (ligação do switch ao router)
  * `enable` > `configure terminal` > `interface fa<interface>` > `switchport mode trunk` > `switchport trunk allowed vlan <num-vlan>` > `switchport trunk allowed vlan add <num-vlan2>`
* Passo 4 > ativação da interface ligada ao switch (router)
  * `enable` > `configure terminal` > `int f<interface>.<num-vlan>` > `encapsulation dot1Q <num-vlan>` > `ip address <default-gateway-vlan> <máscara-de-rede>`

### Aula Prática 5

1.1.1. 192.168.17.6 (dec) = 11000000.10101000.00010001.00000110 (bin)
4.EQUIPAMENTO | INTERFACE |  ENDEREÇO IPv4  |   MÁSCARA SUBREDE    |   GATEWAY
      R1      |   R1.I1   |  192.168.31.1   | 255.255.255.192 / 26 | -----------
      R1      |   R1.I2   |  192.168.31.65  | 255.255.255.252 / 30 | -----------
      R2      |   R2.I1   |  192.168.32.129 | 255.255.255.192 / 26 | -----------
      R2      |   R2.I2   |  192.168.32.1   | 255.255.255.252 / 30 | -----------
      R3      |   R3.I1   |  192.168.30.1   | 255.255.255.224 / 19 | -----------
      R3      |   R3.I2   |  192.168.31.66  | 255.255.255.252 / 30 | -----------
      R3      |   R3.I3   |  192.168.32.2   | 255.255.255.252 / 30 | -----------
      A       |    A.I1   |  192.168.31.2   | 255.255.255.192 / 26 | 192.168.31.1
      B       |    B.I1   |  192.168.31.3   | 255.255.255.192 / 26 | 192.168.31.1
      C       |    C.I1   |  192.168.32.130 | 255.255.255.192 / 26 | 192.168.32.129
      D       |    D.I1   |  192.168.32.131 | 255.255.255.192 / 26 | 192.168.32.129
      E       |    E.I1   |  192.168.30.2   | 255.255.255.224 / 19 | 192.168.30.1
7.1.3. 192.168.2.0/28 255.255.255.240
7.1.4. `ip route <endereço-rede-destino> <submáscara-rede-destino> <endereço-próximo-salto> [permanent]`
       `ip route <endereço-rede-destino> <submáscara-rede-destino> <endereço-interface-saída> [permanent]`
       _permanent_ é uma cláusula facultativa que evita a perda dos endereços de routing em caso de falha do router. Routing estático é o protocolo que permite a troca de informações entre routers.
NOTA: não consegui implementar as rotas de sumarização (mas dá se puser a rede pretendida e a porta do router dessa rede que está ligada ao router atual), mas aqui ficam os cálculos.
8.1.1. R3 - 192.168.31.0  (dec) = 11000000.10100100.00011111.00000000 (bin)
            192.168.31.64 (dec) = 11000000.10100100.00011111.01000000 (bin)
            192.168.33.0  (dec) = 11000000.10100100.00100001.00000000 (bin)
                                  11000000.10100100.00 => 192.168.0.0/18 255.255.255.192
9.1 R2 - 192.168.32.129 (dec) = 11000000.10100100.00100000.10000001 (bin)
         192.168.32.1   (dec) = 11000000.10100100.00100000.00000001 (bin)
                                11000000.10100100.00100000 => 192.168.32.0/24 255.255.255.0
9.2 R1 - 192.168.31.1  (dec) = 11000000.10100100.00011111.00000001 (bin)
         192.168.31.65 (dec) = 11000000.10100100.00011111.01000001 (bin)
                               11000000.10100100.00011111.0 => 192.168.31.0/25 255.255.255.128

Rota estática R > R: `enable` > `configure terminal` > `ip route <IP-rede-destino> <mascara-rede-destino> <IP-router-rede-destino>`

### Aula Prática 6

4.2. 2001:DB8:5F73:A:0000:0000:0000:0001 <==> 2001:DB8:5F73:A::1
5.6. `ipv6 route <endereço-rede-destino> <endereço-interface-saída>` (?)