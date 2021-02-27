# Redes de Computadores

## Apontamentos - Aula Teórica

Redes de computadores classificam-se quanto a:
* **Área espacial / geográfica:**
  *  BAN (_Body Area Network_) - intracorporal (por exemplo, dispositivo para diabéticos _Libre_);
  *  PAN (_Personal Area Network_) - metro quadrado;
  *  LAN (_Local Area Network_) - divisão, edifício, campo;
  *  MAN (_Metropolitan Area Network_) - cidade;
  *  WAN (_Wide Area Network_) - país, continente;
  *  Internet - planeta;
  *  Rede interplanetária - galáxia (por exemplo, ligações entre Terra e Marte);
* **Topologia** - variam consoante as conexões físicas e lógicas:
  * Barramento (_bus_) - vários equipamentos partilham o mesmo meio de acesso (por exemplo, _wifi_). Defeitos: _hidden node_ (quando um nodo pode comunicar com um ponto de acesso sem fios (AP), mas não consegue comunicar com outros nodos que comuniquem com esse mesmo AP);
  * Ponto a ponto - dois equipamentos a partilhar o mesmo meio de acesso. Defeitos: tipologia bastante limitada;
  * Anel (_ring_) - barramento fechado que permite redundância. Defeitos: caso um elemento pare, toda a rede deixa de funcionar (*mas não devia dar para voltar atrás? perguntar*);
  * Estrela (_star_) - uma máquina central concentra toda a comunicação da rede. Defeitos: Se a máquina central parar, toda a rede para;
  * Malha (_mesh_) - não existe organização definida; rede dinâmica que pode variar várias vezes por dia. Defeitos: não é prática numa rede pequena;
* **Canal**
* **Relação de Funcionalidade**;
* **Tipo de Protocolos**;...

Tipos de transmissão de dados:
* _Simplex_ - transmissão de um só sentido entre um ponto A e um ponto B;
* _Duplex_ / _Full-Duplex_ - transmissão bidirecional entre um ponto A e um ponto B;
* _Half-Duplex_ - transmissão bidirecional não simultânea entre um ponto A e um ponto B;

## Apontamentos - Aula Prática

DHCP -> endereço de rede não estático de uma rede sem fios com autenticação pelo MAC Address (não há dois MAC Address's iguais)

O _subnet mask_ indica a gama de valores que é possível utilizar num código IPv4, ou seja, determina a quantidade de máquinas que é possível ligar à rede (por exemplo, 255.255.255.0 [base decimal] == 11111111.11111111.11111111.00000000 [base binária]). Em IPv4 tem-se quatro conjuntos de 256 símbolos:
* 192.168.1.0                 -> código IPv4 de identificação da rede;
* 192.168.1.1 - 192.168.1.254 -> código IPv4 de identificação da máquina;
* 192.168.1.255               -> código IPv3 de identificação do endereço de broadcast.

Num _hub_, toda a informação é partilhada com todos os dispositivos (o que provoca maior colisão e consequente maior degradação dos componentes). Num _switch_, pode haver várias redes independentes com segmentação de tráfego (certos componentes só se relacionam com outros determinados componentes).

Para evitar / diminuir o efeito de ataques informáticos e impedir grandes danos por falhas técnicas, deve haver vários pontos de acesso, circuitos redundantes e implementação de _firewalls_ (sendo necessário entender como é que as informações são trocadas).

As tabelas ARP ligam o IP de cada máquina ao seu MAC Address após o envio de pacotes por `ping`. Uma tabela ARP é normalmente constituída por: endereço de internet, endereço físico, tipo.

_Top Level Domain_ são máquinas servidores de DNS que permitem associar nomes a IP's.