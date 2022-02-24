# Segurança Informática

##### Atualizado em 21-02-2022
###### A partir de: sebenta, exercícios das aulas práticas

## Aulas Teóricas

### Aula 01

Definições básicas de criptografia:
* **Texto limpo** - informação que determinada entidade (transmissora) quer enviar para outra ou para si própria no futuro (recetora);
* **Cifra** - conjunto de dois algoritmos eficientes em que um é usado para transformar o texto limpo numa mensagem com significado obscurecido (criptograma) e o outro faz a operação inversa mediante uma chave de cifra;
* **Criptograma** - resultado da operação de cifra, de que se pode recuperar a mensagem original em texto limpo mediante decifra e apresentação da chave de cifra;
* **Chave de cifra** - parâmetro de segurança dos algoritmos de cifra e decifra;
* **Sistema criptográfico** - especificação das operações de inicialização;
* **Modelo de ataque** - classificação para os possíveis ataques baseada na quantidade de informação a que um criptanalista tem acesso enquanto tenta quebrar um esquema criptográfico;
* **Ataque** - comprometimento dos objetivos da técnica criptográfica e especificação dos passos que levaram a esse comprometimento;
* **Atacante**/**Adversário** - entidade que personifica quem pretende comprometer os objetivos da técnica criptográfica.

Definições básicas de segurança em redes e sistemas distribuídos:
* ***Firewall*** - sistema ou conjunto de módulos de *software* relacionados, localizados num *gateway* da rede, que protege e controla o acesso aos recursos de uma rede privada ou de uma máquina anfitriã;
* ***Hacker*** - indivíduo habilidoso na arte de atacar sistemas computacionais;
* ***White hat*** - *hacker* ético ou especialista em segurança informática que é normal e particularmente bom em testes de penetração e em métodos de teste de segurança;
* ***Black hat*** - *hacker* que viola a segurança de sistemas computacionais sem razões que vão para além do regozijo próprio e malícia;
* ***Script kiddie*** - indivíduo que efetua atos ilícitos num sistema computacional por brincadeira, benefício ou regozijo próprio, sem partilhar os conhecimentos técnicos de um *hacker*;
* **Sistema de deteção de intrusões** (IDS) - sistema ou *software* que monitoriza e tenta detetar atividades maliciosas ou violações à política de segurança em sistemas computacionais ou redes de computadores;
* **Sistema de deteção e prevenção de intrusões** - para além das funções de um IDS, também identificam problemas nas políticas de segurança, documentam ameaças atuais e desmotivam os indivíduos a violar essas políticas;
* **Vulnerabilidade** - característica do sistema que o torna vulnerável a determinados ataques;
* ***Exploit*** - pacote de *software* construído com o propósito de tirar vantagem de uma dada vulnerabilidade;
* **Ataque** - conjunto de passos executados com o intuito de explorar uma vulnerabilidade e que permitem concretizar uma ação ilícita;
* **Risco**/**Ameaça** - dano que pode resultar da execução bem-sucedida de um ataque;
* **Defesa** - conjunto de políticas e mecanismos desenhados, concretizados e implantados para: diminuir o número e severidade das vulnerabilidades, detetar e contrariar/anular ataques, minimizar os riscos decorrentes de ataques bem sucedidos;
* **Políticas de segurança** - definem o foco da segurança e o que precisa ser garantido nesse aspeto num sistema, organização ou entidade;
* **Vírus de computador** - programa que se pode replicar e espalhar de computador para computador, com intervenção humana;
* ***Worm*** - programa que é capaz de se replicar e disseminar sozinho, através da exploração de vulnerabilidades em sistemas interligados em rede ou de gravação e leitura de meios amovíveis;
* **Cavalo de Tróia** - *malware* que se apresenta como ficheiro ou programa legítimo com o propósito de fornecer acesso não autorizado, tipicamente remoto, ao sistema computacional infetado.

---
---

## Aulas Práticas

### Aula 01

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
A B C D E F G H I J K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
Z A B C D E F G H I J K L M N O P Q R S T U V W X Y
Y Z A B C D E F G H I J K L M N O P Q R S T U V W X
X Y Z A B C D E F G H I J K L M N O P Q R S T U V W
W X Y Z A B C D E F G H I J K L M N O P Q R S T U V
V W X Y Z A B C D E F G H I J K L M N O P Q R S T U
U V W X Y Z A B C D E F G H I J K L M N O P Q R S T
T U V W X Y Z A B C D E F G H I J K L M N O P Q R S
S T U V W X Y Z A B C D E F G H I J K L M N O P Q R
R S T U V W X Y Z A B C D E F G H I J K L M N O P Q
Q R S T U V W X Y Z A B C D E F G H I J K L M N O P
P Q R S T U V W X Y Z A B C D E F G H I J K L M N O
O P Q R S T U V W X Y Z A B C D E F G H I J K L M N
N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
M N O P Q R S T U V W X Y Z A B C D E F G H I J K L
L M N O P Q R S T U V W X Y Z A B C D E F G H I J K
K L M N O P Q R S T U V W X Y Z A B C D E F G H I J
J K L M N O P Q R S T U V W X Y Z A B C D E F G H I
I J K L M N O P Q R S T U V W X Y Z A B C D E F G H
H I J K L M N O P Q R S T U V W X Y Z A B C D E F G
G H I J K L M N O P Q R S T U V W X Y Z A B C D E F
F G H I J K L M N O P Q R S T U V W X Y Z A B C D E
E F G H I J K L M N O P Q R S T U V W X Y Z A B C D
D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
C D E F G H I J K L M N O P Q R S T U V W X Y Z A B
B C D E F G H I J K L M N O P Q R S T U V W X Y Z A

**Questão 01: Qual o resultado?**

*Resposta:* OLA > LIX

**Tarefa 02:** BENFICAEOMAIOR

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
F G H I J K L M N O P Q R S T U V W X Y Z A B C D E

**Tarefa 03:** O MAR SALGADO, QUANTO DO TEU SAL SAO LAGRIMAS DE PORTUGAL!

**Questão 02: Para o alfabeto especificado em cima, quantas chaves diferentes se podem definir?**

*Resposta:* 25.

**Questão 03: Em média e mesmo que não soubesse nada acerca das frequências relativas das letras do alfabeto do texto limpo, de quantas tentativas precisa para encontrar o texto limpo original?**

*Resposta:* 13.

**Questão 04: Ainda que não seja especialista na área, faça um esforço para tentar identificar o modelo de ataque que utilizou.**

*Resposta:* *Ciphertext-only attack* (COA).

**Tarefa 04:** 
TIO MANEL TINHA UMA QUINTA
AUL AAULA AULAA ULA AULAAU
TCZ MAHPL TCYHA POA QPTNTU

**Questão 05: Quantas chaves de cifra diferentes existem com 4 letras?**

*Resposta:* 26 x 26 x 26 x 26.

**Questão 06: Qual, ou quais, as famílias de chaves que transformam a cifra de Vigenère numa cifra de César?**

*Resposta:* Chaves com letras todas iguais. Chaves com só uma letra.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
A B C D E F G H I J K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z

**Tarefa 05:**
JUWP G IBELM
ZYXZ Y XZYXZ
ISTO E FACIL

**Questão 07: Faça novamente um esforço para tentar identificar o modelo de ataque que utilizou para quebrar a cifra desta vez.**

*Resposta:* *Know plaintext attack* (KPA).

**Questão 08: Depois de analisar a sua definição, consegue dizer quantas chaves diferentes suporta a cifra de substituição?**

*Resposta:* 26!.

**Questão 09: Acha que esse computador conseguia testar exaustivamente (i.e., por *brute force*) todas as chaves possíveis para a cifra analisada em tempo útil?**

*Resposta:* Sim, conseguia nas calmas. Curte!

**Questão 10: Tendo em conta o que fez e estudou até esta parte do guia, esta cifra parece-lhe segura?**

*Resposta:* Sim, parece-me ser segura.

**Questão 11: Esta cifra é vulnerável a ataques em que se conhece parte do texto-limpo associado a um criptograma ou em que o texto-limpo associado a um criptograma tem propriedades estatísticas notáveis?**

*Resposta:* Sim, é vulnerável em ambas as situações.

**Questão 12: Quanto tempo demoraria um computador atual a tentar essas combinações?**

*Resposta:* Cerca de 1.5 segundos.


**Questão 13: Quantos 0s saíram?**

*Resposta:* 3.

**Questão 14: Quantos 1s saíram?**

*Resposta:* 13.

**Questão 15: Quantas vezes saiu a combinação 00?**

*Resposta:* 1.

**Questão 16: Quantas vezes saiu a combinação 01?**

*Resposta:* 2.

**Questão 17: Se lhe dissessem o que saiu das 6 primeiras vezes, conseguiria adivinhar o que ia sair na sétima?**

*Resposta:* Não, não ia.

**Questão 18: A sequência que resultou desta experiência vai de encontro ao conceito que tem de aleatoriedade?**

*Resposta:* Sim, vai.

**Questão 19: Esta mensagem parece-lhe aleatória ou fácil de prever?**

*Resposta:* Aleatória.

EXPERIÊNCIA:   1101111111111001
ENUNCIADO:     0000000100000001
RESULTADO XOR: 1101111011111000

**Questão 20: Quantos 0s tem o resultado do xor?**

*Resposta:* 5.

**Questão 21: Quantos 1s o resultado do xor?**

*Resposta:* 11.

**Questão 22: Quantas vezes tem a combinação 00?**

*Resposta:* 2.

**Questão 23: Quantas vezes tem a combinação 11?**

*Resposta:* 8.

**Questão 24: A sequência resultante parece-lhe ser aleatória?**

*Resposta:* Sim, de facto parece.

**Questão 25: Se enviar a sequência resultante do xor ao(à) seu(ua) colega, este(a)consegue recuperar o texto-limpo da mensagem? De que forma?**

*Resposta:* É impossível obter o texto-limpo de volta, a não ser que também lhe envie a sequência resultante da minha experiência.

---

### Aula 02