# Sistemas Distribuídos

##### Atualizado em 21-02-2022
###### A partir de: sebenta, exercícios das aulas práticas

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
---

## Aulas Práticas

### Aula Prática 01