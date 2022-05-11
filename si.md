# Segurança Informática

##### Atualizado em 06-05-2022 (faltam teóricas)
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

### Aula 02

Introdução à Lei do Cibercrime.

**Criptografia** - conjunto de técnicas que procuram tornar possível a comunicação secreta entre dois agentes sobre um canal aberto, constituído por cifras, mecanismos de integridade e de troca de chaves ou segredos criptográficos. As suas propriedades de segurança englobam *confidencialidade*, *autenticidade*, *anonimato* e *não repúdio*.

**Criptanálise** - estudo de técnicas que visam gorar os objetivos da Criptografia, ou seja, quebrar a segurança da comunicação de modo a obter o texto-limpo original, a chave de cifra ou o algoritmo de cifra.

**Cifra de chave simétrica** - par de algoritmos eficientes, um para cifrar $c=E(k,m)$, outro para decifrar $m=D(k,c)$. Deve assegurar-se que $m=D(k,E(k,m))$.

**Cifra de chave pública** - terno de algoritmos eficientes, um para gerar as chaves $(p_k,s_k)$, um para cifrar $c=E(p_k,m)$, um para decifrar $m=D(s_k,c)$. Deve assegurar-se que $m=D(s_k,E(p_k,m))$.

**Modelos de ataque**
* *Ciphertext-only Attack* (COA) - apenas o criptograma é conhecido;
* *Known Plaintext Attack* (KPA) - conhece-se o texto-limpo original;
* *Chosen-plaintext Attack* (CPA) - texto-limpo original escolhido, podendo pedir a cifra de texto-limpo previamente;
* *Adaptative-chosen-plaintext Attack* (CPA2) - texto-limpo escolhido de forma adaptativa, podendo pedir a cifra do texto-limpo de acordo com os criptogramas obtidos;
* *Chosen-ciphertext Attack* (CCA1) - criptogramas escolhidos, em que se podem decifrar criptogramas relacionados;
* *Adaptative chosen-ciphertext attack* (CCA2) - criptogramas escolhidos de forma adaptativa, podendo escolher o resultado da análise dos pares texto-limpo/criptogramas anteriores.

---

### Aula 03

**Ataque de força bruta** - o adversário opta por percorrer todo o espaço de chaves de cifra, inicializando e executando os algoritmos de cifra ou decifra para encontrar o texto-limpo correspondente a um criptograma, pressupondo que o espaço de chaves é muito inferior ao espaço de mensagens. Sempre passível de ser aplicado a uma cifra, porém condicionado pelo tempo dispendido.

**Princípio de Kerckhoffs** - um sistema criptográfico deve ser seguro mesmo se tudo acerca desse sistema, à exceção da chave, é do conhecimento público. O corolário define que a segurança da cifra deve ser totalmente dependente de um parâmetro explícito (chave de cifra).

**Teoria da Informação** (Claude Shannon):
* **Confusão** - obscurecer a relação que existe entre o texto-limpo, o criptograma e a chave;
* **Difusão** - espalhar as redundâncias do texto-limpo por todo o criptograma.

**Secretismo perfeito** - para quaisquer duas mensagens, a probabilidade de obter o mesmo criptograma pela cifra de Vernam (*One Time Pad*) depois de cifradas é igual `(secção 2.4 aula 2)`.

**Cifras de chave simétrica contínua** - substitui-se a chave aleatória de tamanho `n` igual ao do texto-limpo por uma chave pseudo-aleatória que é gerada, a partir de uma semente, por um gerador seguro que deve ser imprevisível. A chave de cifra não deve ser usada mais do que uma vez, no entanto, pode haver redundância suficiente na linguagem e codificação utilizada para permitir reaver as mensagens originais a partir do seu XOR.
* **Segurança semântica** - se o adversário errar aproximadamente tantas vezes quantas acerta na mensagem cifrada, então a cifra é segura (a vantagem deve ser menor do que `1/2^80`.

As cifras de chave simétrica contínuas podem ser usadas em situações em que o canal de comunicação pode ser escutado mas não manipulado, no entanto, as cifras são **maneáveis** (o criptograma pode ser alterado sem que tal facto seja notado após decifragem, com impacto previsível no texto limpo). A ***Rivest Cipher 4*** é dos melhores exemplos, aceitando chaves de 128 bits.

---

### Aula 04

**Cifras de chave simétrica por blocos** elaboram em funções (*Pseudo Random Permutations* (PRP)), que aceitam como valor de entrada uma chave e um bloco de bits, com tamanho fixo, e devolvem um bloco com o mesmo tamanho. Existe um algoritmo determinístico eficiente para avaliar $E(k, x)$; para cada $k$, a função $E(k, .)$ é bijetiva; existe um algoritmo determinístico eficiente para inverter $D(k, y)$. Exemplos canónicos: *Data Encryption Standard* (DES), *Triple DES* (3DES), *Advanced Encryption Standard* (AES).

O algoritmo de cifra ou decifra começa por aplicar funções de expansão da chave de cifra, dando origem a várias chaves de ronda $k_i$ que, por sua vez, são usadas como segundo parâmetro de entrada nas funções núcelo destas cifras (funções ronda $R(k_i, .)$). Cada uma destas funções é invertível - a decifra faz-se aplicando as chaves e as funções de ronda no sentido inverso.

Para que uma PRP $F(k, .)$ seja segura, esta deve ser indistinguível de uma qualquer outra função $F(.)$ escolhida ao acaso da totalidade de funções de $X$ para $X$.

**Redes de Feistel** são funções sempre invertíveis, mas construídas a partir de funções que podem não ter inversa. O **teorema de Luby-Rackoff** assegura que qualquer rede de Feistel com mais do que 3 rondas construída a partir de *Pseudo Random Functions* (PRF) seguras define um PRP seguro.

**Modos de cifra** definem circuitos ou algoritmos de cifra e decifra:
* *Eletronic Code Book* (ECB) - mais simples e direto, a mensagem a cifrar é dividida em blocos de tamanho $n$ e cada bloco é cifrado independentemente dos outros, com a mesma chave;
    * Não é semanticamente seguro no modelo COA e pode apenas ser usado para cifrar pedaços de informação aleatórios e tipicamente mais pequenos que o bloco;
    * Os padrões existentes no texto limpo não são disfarçados;
    * Suscetível a ataques por *code book* ou por remoção, troca e repetição de blocos;
    * Permite o acesso aleatório a dados cifrados e o processamento paralelo de informação, sendo que o último bloco necessita sempre de tratamento em termos de preenchimento;
    * Não apresenta problemas de propagação de erros entre blocos, no entanto, erros de sincronização (perda de bits) são irrecuperáveis;
* *Deterministic Counter Mode* () - define uma cifra de chave simétrica contínua a partir de uma cifra por blocos, fazendo uso apenas da função de cifra $E(k, .)$, que é inicializada com uma chave e reincidentemente usada para gerar blocos pseudo-aleatórios. A decifra é exatamente igual à decifra, trocando apenas o criptograma de lugar com o texto-limpo no final;
* *Cipher Block Chaining* (CBC) - o criptograma deve ser diferente, mesmo que se cifre a mesma mensagem com duas chaves, o que é conseguido por um fator de aleatoriedade no processo de cifragem: **vetor de inicialização** (VI), valor que deve ser potencialmente único para cada combinação de chave de cifra/mensagem que não necessita de ser secreto e pode ser enviado juntamente com o criptograma;
    * Cifra: ![](https://i.imgur.com/Gc6XrEB.png)
    * Decifra: ![](https://i.imgur.com/yRP5Dx3.png)
    * Semanticamente seguro no modelo CPA desde que o VI seja imprevisível;
    * Os padrões do texto limpo são mascarados pelo XOR e pelo efeito cascata;
    * De textos limpos iguais resultam criptogramas distintos, inviabilizando ataques por *code book* e por repetição;
    * Alguns ataques por manipulação de blocos são detetáveis, mas ataques por manipulação do VI podem não ser detetáveis;
    * Permite o acesso aleatório a dados cifrados e o processamento paralelo da informação cifrada;
    * Cada alteração ao texto limpo implica uma nova cifragem completa, sendo que o último bloco necessita sempre de tratamento em termos de preenchimento;
    * Um erro num bit afeta o bloco de texto limpo correspondente e um bit no bloco seguinte; erros de sincronização (perda de bits) são irrecuperáveis;
* *Randomized Counter Mode* (CTR) - o algoritmo de cifra define que se gere um vetor de inicialização aleatório e potencialmente único para cada combinação chave/mensagem $(k, m)$. Os algoritmos de cifra e decifra são iguais, trocando apenas as posições do texto-limpo e do criptograma, tornando a cifra mais simples e eficiente de implementar:
    * Semanticamente segura no modelo CPA;
    * Os padrões do texto-limpo são mascarados por se imitar uma cifra de chave simétrica contínua;
    * De textos-limpos iguais resultam criptogramas diferentes, inviabilizando ataques por *code book* e repetição; ataques por manipulação de bits não são detetados;
    * Permite o acesso aleatório a dados cifrados e o processamento paralelo de informações;
    * O último bloco não necessita de preenchimento;
    * Não há propagação de erros, e erros de sincronização (perda de bits) não são recuperáveis.

O último bloco de uma mensagem pode ser preenchido até que a condição que verifique, ***padding***, em que se repete o número de bytes que foram necessários para preencher o bloco na parte final do bloco incompleto.

---

### Aula 05

Se uma cifra está bem construída, então a segurança do sistema criptográfico vai depender do secretismo da chave de cifra ou da chave de cifra privada. Os ataques são frequentemente focados no comprometimento da chave de cifra ou na sua distribuição, o que implica que a gestão das chaves seja um problema de importância crítica na criptografia. A abordagem mais direta consiste em gerar e distribuir as chaves de cifra antes da comunicação, seguindo:
* Dois esquemas:
    * Todos os pares partilham uma chave de cifra de chaves de sessão;
    * Todas as entidades partilham uma chave de cifra de chaves de sessão com um agente de confiança;
* Dois protocolos de acordo de chaves (KAP):
    * **Diffie-Hellman** - duas entidades conseguem estabelecer uma chave de sessão através de diálogo sobre um canal público, independentemente de terem estabelecido antes ou não alguns parâmetros ou segredos - seguro apenas no caso em que um adversário pode escutar a comunicação, mas não manipulá-la. Gera-se um número inteiro $x$ e calcula-se $X = g^x mod P$, em que $P$ é um número primo grande (maior que 1024 bits) e $g$ é um gerador do grupo $\mathbb{Z}_P$; se o $X$ for dado a alguém, é impossível, na prática, esse alguém obter o $x$;
    * **Puzzles de Merkle** - usa apenas mecanismos da criptografia de chave simétrica. O primeiro interveniente prepara uma série de puzzles, que são baralhados e cifrados antes de serem enviados para o segundo interveniente. Este deve decifrar um dos puzzles, por força bruta; qualquer atacante que tenha acesso aos puzzles deve decifrar todos de modo a descobrir qual está a ser utilizado na comunicação.

**Chave de sessão** - usada para cifrar e decifrar, gerada somente para determinada comunicação.

**Chave de cifra da chave de sessão** - usada única e exclusivamente para cifrar e decrifrar chaves de sessão - $C^n_2$, em que uma das entidades envolvida na comunicação gera a chave de sessão e envia-a à outra entidade cifrada com a chave pré-estabelecida.

**Agente de confiança** - entidade do sistema de comunicações em quem os utilizadores confiam plenamente e com quem podem ter chaves pré-estabelecidas.

O **problema do logaritmo discreto** está na base do protocolo de chaves Diffie-Hellman e da cifra RSA. Dado um grupo cíclico finito $G$ e um gerador $g$ parra esse grupo, $G = {1, g, g^2, ..., g^n-1}$, o **problema do logaritmo discreto** é intratável se para todos os algoritmos eficientes $A$ que se venham a definir para resolver o problema a probabilidade de este algoritmo encontrar $x$ dqdo $g$ e $g^x$ é desprezível. O melhor algoritmo conhecido para resolver o problema é o *general number field sieve*, que determina o tamanho que estes números devem ter para garantir a segurança dos mecanismos que neles elaboram.

A cifra RSA baseia-se também no **problema da fatorização em números primos**, que define que é computacionalmente inviável fatorizar um número composto pelo produto de dois números primos grandes.

---

### Aula 06

Um protocolo define que as chaves são trocadas por mensagens e um esquema define que as chaves são definidas no início (não tem mensagens).

A segurança da informação deve assentar nos pilares de **confidencialidade** (os dados não podem ser acedidos por quem não lhes pertence), **integridade** (os dados devem encontrar-se como foram deixados ou transmitidos) e **disponibilidade**.

Uma **função de *hash*** é uma função $H(m)$ definida no espaço de mensagens $M$ com tamanho arbitrariamente para uma sequência de *bits* ${0, 1}^n$ com tamanho fixo $n$. É uma função **não injetiva** (a vários *inputs* diferentes pode corresponder o mesmo valor de *hash*), **compressora** (o seu retorno tem sempre o mesmo tamanho, independentemente do tamanho do *input*) e **fácil de computar** (é computacionalmente eficiente calcular $H(m)$).

Uma função de *hash* diz-se **criptográfica** se for computacionalmente inviável obter quaisquer duas mensagens $m_1$ e $m_2$ com o mesmo valor de *hash*. Para além das propriedades de compressão e computação das funções de *hash* normais, uma função de *hash* criptográfica dever ser **resistente a: descoberta de um texto original** (dado qualquer valor de *hash*, é computacionalmente inviável encontrar uma mensagem que lhe dê origem); **descoberta de um segundo texto original** (dada uma mensagem, é computacionalmente inviável encontrar outra mensagem com o mesmo valor de *hash* da primeira); **colisão** (é computacionalmente inviável encontrar quaisquer duas mensagens com o mesmo valor de *hash*).

**Construção iterativa de Merkle-Damgard** - pode obter-se uma função $H(m)$ que primeiramente aplique $g$ a um vetor de inicialização $vi$ e ao primeiro bloco da mensagem com $r$ bits, e depois a aplique iterativamente a cada bloco de $r$ bits e ao resumo obtido no passo anterior, devolvendo o valor resultante para o último bloco. Qualquer função construída conforme o esquema de Merkle-Damgard é resistente a colisões, no entanto, não permite o processamento paralelo.

O algoritmo ***Message Digest* 5** (MD5) opera sobre um estado de 128 bits dividido em quatro palavras de 32 bits. A mensagem é dividida em blocos de 512 bits, que são subdivididos em peças de 32 bits que são combinadas com as quatro palavras definidas antes em 64 operações. O algoritmo ***Secure Hash Algorithm* 1** (SHA1) produz um resumo de 160 bits de qualquer mensagem.

O ***Message Authentication Code*** (MAC) é um par de algoritmos $(S, V)$ definidos sobre o espaço de chaves, mensagens e códigos possíveis, em que $S(k, m)$ é normalmente designado por algoritmo de assinatura e $V(k, m, t)$ é conhecido como algoritmo de verificação, que permite garantir a integridade de mensagens. O algoritmo de verificação devolve o valor `verifica` ou `não verifica` conforme o código corresponda ou não à mensagem a que está associado. O MAC assume que apenas as entidades que estão em comunicação possuem a chave de integridade e que, portanto, um adversário mal intencionado não deverá conseguir alterar a mensagem e o código simultaneamente.
* ***Encrypted Cipher Block Chaining MAC*** (ECBC-MAC) - construído a partir de funções de permutação pseudo-aleatórias seguras (exige duas chaves de cifra);
* ***Hash Based MAC*** (HMAC) - construído a partir de funções de *hash* criptográficas.

---

### Aula 07

Um **sistema de cifra de chave pública** é um terno de algoritmos eficientes $(G, E, D)$, em que $G$ define um algoritmo que dado um número de bits devolve um par de chaves pública e privada; $E$ define um algoritmo aleatorizado que dada uma mensagem e uma chave pública devolve um criptograma; $D$ define um algoritmo que dado um criptograma e uma chave privada devolve uma mensagem ou um símbolo de erro. Os três algoritmos satisfazem a condição de consistência, fornecendo imediatamente uma forma de trocar chaves de sessão sobre um canal inseguro.

A **criptografia de chave pública** é possível devido a funçẽs de sentido único com propriedades homomórficas (cifra ElGamal) e com propriedades homomórficas com alçapão (RSA). Uma função de sentido único com alçapão é uma função $f: X \rightarrow Y$ para a qual existe um algoritmo eficiente para a avaliar em qualquer ponto de $X$, mas não existe nenhum eficiente para a inverter, a não ser que se saiba um segredo (alçapão).

A **cifra ElGamal** elabora no protocolo de acordo de chaves Diffie-Hellman, em que se usa a chave que é gerada no âmbito do acordo de chaves para cifrar a mensagem com criptografia simétrica; como cada chave só deve ser usada uma vez, quem cifra deve gerar um valor diferente para cada bloco da mensagem a cifrar. É um método probabilístico (a mesma mensagem pode dar origem a diferentes criptogramas) e o tamanho do criptograma é sempre superior ao tamanho da mensagem.

***Rivest, Shamir e Adleman*** (RSA) refere um sistema de cifra de chave pública, mais corretamente definido como uma permutação com alçapão. Possibilita a construção de assinaturas digitais de um modo simples. Se se escolher dois números primos grandes, calcular $N = p \times q$ e dar $N$ a alguém para descobrir quais os dois números primos que o decompõem, está-se perante um problema intratável. O **RSA em modo livro da escola** não deve ser usado, porque é determinístico (logo, não é semanticamente seguro) e porque os criptogramas são maneáveis.

O ***Optimal Asymmetric Encryption Padding*** (OAEP) define uma função de pré-processamento da preenchimento e aleatorização da mensagem antes de esta ser cifrada. Aquando da receção de uma mensagem codificada, o recetor começa por decifrar o criptograma com a função inversa e a respetiva chave privada, recuperando primeiro $r$ e depois $m$.

---

### Aula 08

Um sistema de **assinatura digital** é um terno de algoritmos eficientes $(G, S, V)$ em que: $G$ define um algoritmo que, dado um número de bits, devolve um par de chaves pública e privada; $S$ define um algoritmo que, dada uma mensagem e uma chave privada, devolve um código (assinatura digital); $V$ define um algoritmo que, dada uma assinatura digital, uma mensagem e uma chave pública, devolve a validade dessa assinatura. Os três algoritmos satisfazem a condição de **consistência**, em que $S$ é designado algoritmo de assinatura e $V$ algoritmo de verificação. Se se assinar um documento e alterar um bit *a posteriori*, então a assinatura não será válida.

A assinatura digital possui as seguintes propriedades:
* **Autenticidade da informação** - assegura que a entidade que assinou a mensagem tinha conhecimento do seu conteúdo;
* **Integridade dos dados** - assegura que a mensagem a que corresponde a assinatura não foi alterada desde que foi assinada até que foi validada;
* **Garantia de não-repúdio** - assegura que a entidade que a assinou não pode negar que o fez;
* **Autenticação da origem da informação** - assegura que a mensagem veio pela entidade que a assinou;
* **Dificuldade de falsificação** - assegura que mais nenhuma entidade pode ter assinado a mensagem, à exceção do emissor já (re)conhecido.

É possível construir uma assinatura digital segura usando apenas mecanismos da criptografia de chave simétrica. Se alguém diz que não assinou algo, o agente de confiança tem a prova de que o fez através da mensagem cifrada com `ka`.

**Certificado** - conjunto de parâmetros; documento eletrónico assinado digitalmente que liga dois ou mais valores entre si. Certificados são gerados e geridos por uma *Public Key Infrastructure* (PKI). Um **certificado de chave pública** é uma estrutura que associa uma chave pública a uma entidade em particular. A associação chave-entidade é estabelecida por um terceiro - **autoridade de certificação**, que assina digitalmente cada certificado.

O uso de criptografia de chave pública é regulado pela recomendação **X.509** do *International Telecommunications Union* (ITU), definida num conjunto de *Requests For Comments* (RFCs) publicados pela *Internet Engineering Task Force* (IETF). A norma X.509 especifica a sintaxe dos certificados de chave pública, das listas de revogação de certificados e dos certificados de atributos, bem como o algoritmo de validação dos certificados. A utilidade de um certificado depende apenas da confiança que as entidades têm relativamente à Autoridade de Certificação.

A utilização de uma PKI e de certificados X.509 assenta nas seguintes propriedades e factos:
* A entidade que requisitou e possui o certificado confia que a Autoridade Certificadora verificou que a chave pública expressa no certificado pertence, de facto, ao proprietário;
* A assinatura digital anexa ao certificado assegura a sua autenticidade e integridade;
* Como a assinatura e a validade temporal de um certificado podem ser verificadas independentemente de um utilizador, os certificados podem ser distribuídos por canais inseguros.

Para além de conterem a chave pública, o período de validade e o identificador do dono, os certificados de chave pública contêm também um campo que indica para que efeitos pode ser usada a chave neles contida: assinatura digital, autenticação, troca de chaves de sessão ou assinatura de outros certificados. Assim, o processo de verificação de uma assinatura digital e de cifra de chaves de sessão fica mais complexo: é necessário verificar que a assinatura do certificado é válida, que foi emitida por uma entidade certificadora de segurança e que está dentro do prazo de validade, bem como se é consistente com as permissões/privilégios indicados.

***Public Key Infrastructure*** (PKI) é o conjunto de *hardware*, *software*, pessoas, políticas e procedimentos necessários à criação, gestão, distribuição, utilização, armazenamento e revogação de certificados digitais. Uma PKI é composta por:
* **Entidade terminal** (cliente) - aquela que utiliza os certificados PKI ou sistema a que se refere determinado certificado;
* **Autoridade Certificadora** (AC) - aquela que emite ou revoga certificados;
* **Autoridades de Registo Organizacional** (ARO) - sistema opcional ao qual as ACs delegam certas funcionalidades de gestão;
* **Emissor de Listas de Revogação de Certificados** (LRC) - sistema que gera e assina LRCs;
* **Repositório** - sistema ou coleção de sistemas distribuídos que guardam certificados e LRCs, e que servem como meio de distribuição destes a entidades terminais.

A PKI assenta em dois tipos de protocolos: **protocolos operacionais** (necessários para entregar certificados e LRCs a utilizadores cliente) e **protocolos de gestão** (necessários para suportar interações em linha entre utilizadores cliente e entidades de gestão ou entre entidades de gestão (registo, inicialização, certificação, recuperação/atualização de chaves, publicação de certificados e LRCs, pedido de revogação, certificação mútua entre ACs)).

A validação de um certificado de um utilizador envolve o conhecimento da chave pública da AC que emitiu o certificado, logo, requer a obtenção do certificado que contém a chave pública da AC. A cadência de certificados necessários à validação de determinada chave pública é denominada de **caminho de certificação**, que concretiza uma hierarquia de ACs. As ACs superiores emitem certificados de ACs de níveis inferiores; no topo da hierarquia, a **AC Raiz de Confiança** emite e assina o seu próprio significado. Assim, a validação de um caminho de certificação termina quando é encontrado um certificado com propriedade raiz de confiança.

---

### Aula 09

**Listas de revogação de certificados** (LRC) são documentos com os números de série dos certificados que são revogados antes de terminarem a validade, com assinatura digital (emitidos pela empresa que lançou o certificado revogado). Uma lista é **base**, se tiver todos os certificados que ainad não expiraram mas foram revogados; ou **delta**, se lista apenas os certificados que mudaram o seu estado (revogados ou excluídos) desde a emissão de uma LRC base.

***Pretty Good Privacy*** (PGP) - *software* que combina diversos mecanismos da criptografia de chave simétrica e de chave pública para fornecer serviços de segurança a comunicações eletrónicas e armazenamento de dados:
* **Autenticação**;
* **Confidencialidade**;
* **Compressão**;
* **Serviço de compatibilidade** - codificar o ficheiro cifrado em carateres ASCII usando codificação Base64;
* **Serviço de segmentação** - dividir um ficheiro grande em segmentos.

No PGP, um utilizador tem dois pares de chaves: um só para assinaturas digitais, outro só para confidencialidade. As chaves assimétricas são guardadas em dois ficheiros diferentes: um **chaveiro privado** (com uma ou mais chaves privadas, protegido por uma palavra-passe) e um **chaveiro público** (povoado com chaves públicas de outros utilizadores, por troca direta ou através de servidores).

A **rede de confiança** baseia-se na hipótese de existirem em média seis graus de separação entre dois humanos. O primeiro mecanismo consiste em assinar digitalmente as chaves em que se confia com a chave privada, indicando ao *software* que se tem confiança absoluta naquela chave. Usam-se três níveis de confiança:
* **Confiança absoluta** - define que determinado utilizador é um *trusted introducer* e que se confia em todas as suas chaves endossadas;
* **Confiança marginal** - define que não se confia totalmente num utilizador, mas pode eventualmente vir-se a confiar na chave caso vários utilizadores com confiança marginal a assinem;
* **Sem confiança** - define que não se confiam em chaves de determinado utilizador.

A **rede de confiança** determina que: se confia todas as chaves assinadas por nós; se confia em todas as chaves assinadas por uma chave em que se confia totalmente (nível 1); se confia nas chaves que foram assinadas por, pelo menos, $n$ chaves em que se confia marginalmente.

Caso as chaves públicas sejam comprometidas ou deixem de ser seguras, no PGP: o utilizador emite um certificado a revogar a sua própria chave pública, assinando-a com a sua chave privada; ou o utilizador nomeia outro utilizador para revogar as suas chaves (caso as tenha perdido).

Um cartão de cidadão possui dois pares de chaves, dos quais é impossível remover a chave privada. É dentro do cartão que se guarda a assinatura digital, sendo pedido sempre o PIN pessoal. As operações de assinatura e autenticação são pedidas pelo próprio cartão, não pelo *software* que o lê. Um cartão de cidadão tem pelo menos cinco certificados digitais e dois métodos de autenticação (o próprio cartão e o PIN). Um cartão de cidadão não permite cifrar. Por definição, um cartão de cidadão traz os seus pares de chave revogados.

---

### Aula 10

**Segurança da Informação** é sinónimo de proteção da informação e dos sistemas de informação das ameaças às três propriedades fundamentais CIA (Confidencialidade, Integridade, Disponibilidade). Inclui identificação das ameaças, dos recursos críticos e das vulnerabilidades, a quantificação do risco ($risco = probabilidade x valor$) e a concretização dos objetivos de segurança para determinada organização ou entidade através de um documento escrito - **política de segurança**.

Vulnerabilidades devem-se, na sua maioria, a problemas de desenho, de realização ou de administração. O sucesso de um ataque, ou da técnica usada para o prevenir, depende de um passo inicial importante: a identificação do sistema operativo e das vulnerabilidades da máquina alvo. Sabendo o sistema operativo, é possível obter imediatamente um catálogo de todas as vulnerabilidades, para explorar ou mitigar.

Muitos servidores enviam uma mensagem de boas-vindas aquando da primeira ligação, onde anunciam o seu nome, a versão do *software* servidor e, frequentemente, o sistema operativo em que estão a executar. Este método - **flâmulas** - não é útil para identificar o sistema operativo da maioria das máquinas cliente e não funciona quando se suprimem ou alteram (de propósito) os *banners* dos servidores.

Outro método é a **impressão digital da pilha TCP/IP** (*Transmission Control Protocol*/*Internet Protocol*). Todos os sistemas com ligação à Internet possuem esta pilha; a especificação dos protocolos da suite TCP/IP deixa espaço para alguma personalização; o comportamento padrão permite expansões, que são fontes de diferenças. Desvios ao comportamento padrão da pilha são indicadores do sistema operativo utilizado e da respetiva versão.
* A ferramenta **RING** procura explorar o tempo de reação do sistema operativo a pacotes TCP enviados pela rede. O protocolo TCP determina que as partes interatuantes de uma ligação devem retransmitir os dados caso não haja resposta depois de um estímulo, mas não determina exatamente quantas vezes devem retransmitir ou quanto tempo devem esperar entre retransmissões, facto que é explorado em sistemas com portos TCP abertos;
* A ferramenta **`nmap`** (*Network Mapper*) foca-se nas respostas a esses estímulos (segmentos TCP ou datagramas UDP (*User Datagram Protocol*)) forjados (sondas, mais eficazes mas mais arriscadas). Combina as respostas aos vários estímulos de modo a obter uma assinatura que pode comparar com uma base de dados de assinaturas.

A **inventariação de serviços** consiste em identificar quais os portos da camada de transporte acessíveis - se esses portos estiverem associados a serviços, então esses serviços estarão provavelmente disponíveis, em princípio - para determinar quais os serviços que correm em determinada máquina. O rastreio pode ser feito por:
* **Portas TCP**: tenta-se estabelecer uma ligação TCP a uma determinada porta. Para o atacante, se a ligação for completamente estabelecida, deixa um rasto, e então deve optar por mandar apenas um segmento SYN e esperar pela resposta, sem estabelecer ligação, enviar um segmento FIN, sobrefragmentar os pacotes ou usar mediadores;
* **Portas UDP**: envia-se um datagrama UDP para o porto em questão, e espera-se a resposta: se não houver serviços a correr nesse porto, é enviado um datagrama ICMP com um erro; se não, pode ou não haver resposta, identificando-se pela negativa.

A correta configuração dos servidores é essencial para reduzir o número de vulnerabilidades dos sistemas, seja através de **correção dos serviços prestados** (testar se o servidor funciona) ou **segurança do sistema contra explorações ilegítimas** de falhas de configurações. As ferramentas de inventariação de deficiências de administração procuram vulnerabilidades conhecidas em máquinas. O **OpenVAS** (*Open Vulnerability Assessment System*) é uma ferramenta pública de inventariação remota de deficiências e possui uma arquitetura cliente/servidor, devolvendo um relatório com a lista de serviços encontrados e das vulnerabilidades detetadas.

Os cenários anormais podem surgir a partir de uma conjugação de fatores não premeditados (pode resultar na falha do sistema de modo imprevisível) ou a partir de intenções maliciosas (resultado da tentativa de exploração de vulnerabilidades derivadads de mau desenho ou de realização deficiente).

O **ataque LAND** consistia em enviar um segmento TCP SYN com o mesmo endereço fonte e destino e o mesmo porto fonte e destino para a máquina vítima. A pilha TCP/IP (defeituosa) de alguns sistemas operativos respondiam a este pedido e entravam em ciclo logo de seguida, ficando lentos ou incapazes de responder a pedidos legítimos.

O **ataque *Teardrop*** explorava uma vulnerabilidade de implementação do algoritmo de desfragmentação IP. O algoritmo problemático verificava se dois fragmentos do mesmo pacote se sobrepunham e calculava a parte que devia ser copiada em caso de sobreposição; o ataque consistia em forjar dois segmentos de modo a que um fragmento estivesse dentro do outro. O algoritmo calculava uma área a copiar negativa e, dado a função que implementava a cópia só aceitar valores sem sinal, interpretava aquele valor como um valor de grande dimensão levando o procedimento a procurar o fragmento numa posição errada de memória (fora dos limites).

O **ataque Echo-Chargen** consiste em enviar um pacote UDP com o mesmo endereço IP fonte e destino para a máquina vítima e com os portos UDP de um e de outro serviço na forte e no destino. O `echo` reenvia para o `chargen`, e o `chargen` reenvia para o `echo`.

O **ataque *Ping of Death*** explora outra falha da implementação do algoritmo de desfragmentação. O algoritmo assume que o tamanho dos pacotes não vai para além do limite máximo estipulado e a implementação errónea construía os vários fragmentos antes de calcular o tamanho máximo que o pacote tinha. O ataque consistia em enviar um pacote ICMP demasiado grande mas muito fragmentado e esperar que o fragmentador o montasse antes de verificar que já tinha escrito em zonas da memória que não devia.

O **ataque de inundação de início de ligação** (SYN) consiste em gerar e enviar para o servidor um número inusitado e contínuo de pedidos de sincronização. O servidor é obrigado a guardar o estado de um grande número de ligações meio estabelecidades e a aguardar por respostas que não vão chegar, tendo também de lidar com as possíveis retransmissões que o TCP define para o caso em que não há respostas. Tal leva à negação de serviço a clientes legítimos, sendo base para os grandes ataques de DDoS (*Distributed Denial of Service*).

A exploração de **erros de realização** de código ou implementação deficiente pode induzir situações de negação de prestação de serviço ou situações de penetração e compromisso do sistema. Devem-se à incapacidade do programador de antecipar qualquer combinação complexa de cenários anormais e ao facto de poder não dominar a linguagem que está a usar na implementação.
* **Vulnerabilidades de transbordamento de memória** (*memory overflow*) - responsáveis por grande parte dos problemas de segurança em sistemas informáticos. O ataque consiste em provocar o transbordamento de memória para locais que podem alterar o fluxo do programa de modo lucrativo para o atacante, nomeadamente, para permitir a execução de código malicioso - seja pela atribuição de um valor errodo a determinada variável ou pela modificação dos endereços de contexto local ou de retorno;
  * Parte da solução consiste em colocar canários a guardar os valores dos ponteiros; se alguém tentar alterar os ponteiros, quase de certeza o canário é modificado. Antes de se usar o ponteiro de retorno ou de contexto local, o(s) canário(s) é(são) verificado(s) e o código só é executado se os canários não tiverem sido modificados;
* **Vulnerabilidades associadas a cadeias de formato** - usa dados de entrada com códigos de controlo, que podem forçar o programa a revelar informação acerca de endereços de memória ou a injetar código.

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

**Questão 01: O que é o OpenSSL?**

*Resposta:* Implementação de código aberto dos protocolos SSL (*Secure Sockets Layer*) e TLS (*Transport Layer Security*), disponibilizando funções básicas de criptografia e utilitárias.

**Questão 02: Procure saber se o OpenSSL é importante nos dias de hoje e se, apersar de ser um recursos que tem a ver com a segurança da informação, foi a base de alguma vulnerabilidade crítica nos últimos tempos.**

*Resposta:* O OpenSSL é muito importante e (eish!) continha um mega *bug* que ia acabando com a Internet.

**Questão 03: Como é que normalmente se pode aceder ao manual de um comando Linux ou Unix *like*?**

*Resposta:* Escrevendo `man <comando>` no terminal.

**Questão 04: Há alguma diferença entre OpenSSL (devidamente capitalizado) e `openssl` (em `monospace`)?**

*Resposta:* *Nope*... As duas designações referem-se exatamente à mesma *toolkit*.

**Questão 05: Pode usar o OpenSSL para gerar chaves assimétricas?**

*Resposta:* Nunca experimentei, mas penso que sim.

**Questão 06: Pode usar esta ferramenta para lidar com email cifrado?**

*Resposta:* Claro.

**Questão 07: E para gerar *timestamps*?**

*Resposta:* Também dá.

**Questão 08: E para verificar o MD5 de determinado ficheiro?**

*Resposta:* Faz tudo!

**Questão 09: Pode usar o OpenSSL para fazer o pequeno-almoço?**

*Resposta:* Não, mas de resto faz tudo...

**Tarefa 02: Construa o comando OpenSSL que lhe permite gerar 10 bytes aleatórios de qualidade em hexadecimal.**

*Resposta:* `openssl rand -hex 10`

**Questão 10: Acha que ainda está na linha de comandos?**

*Resposta:* Sim, porque continuo a interagir apenas por texto, e não por uma interface gráfica.

**Questão 11: Acha que `help` é um comando/opção do OpenSSL?**

*Resposta:* Sim.

**Questão 12: Quantos são os comandos principais (*standard*) que tem à disposição?**

*Resposta:* 48.

**Questão 13: Das seguintes, quais correspondem a opções existentes para o comando `openssl enc`?**

*Resposta:* `-in <file>`, `-out <file>`, `-pass <arg>`, `-e`, `-d`, `-a`/`-base64`, `-k`, `-md`, `-S`, `-K`/`-iv`, `-bufsize`, `-nopad`.

**Questão 14: Será que o OpenSSL também consegue comprimir e descomprimir ficheiros?**

*Resposta:* Não, visto que mesmo o encadeamento de comandos `man enc | grep compress` não devolve qualquer resultado...

**Questão 15: O que significa RC4?**

*Resposta:* *Rivest Cipher* 4.

**Questão 16: A chave de cifra fornecida parece-lhe boa?**

*Resposta:* Não, porque me parece ter muita entropia.

**Questão 17: O comando funcionou sem problemas?**

*Resposta:* Sim, funcionou. :D

**Questão 18: Já verificou o que está dentro do ficheiro?**

*Resposta:* Sim, já verifiquei usando `cat ciphertext.rc4` e o que lá encontrei não faz sentido nenhum.

**Questão 19: Nos espaços incluídos em baixo, coloque a opção que especifica cada parte do comando `OpenSSL` incluído antes.**

*Resposta:*
* `-K` especifica que o valor incluído a seguir é a chave de cifra em hexadecimal.
* `-k` especifica que o valor incluído a seguir é a chave de cifra em ASCII.
* `-out` especifica que o valor incluído a seguir é o nome do ficheiro de saída.
* `-in` especifica que o valor incluído a seguir é o nome do ficheiro de entrada.
* `-e` especifica que se trata da operação de cifra (*encryption*).

**Questão 20: Qual o comando `OpenSSL` que utilizou?**

*Resposta:* `openssl enc -rc4 -d -k abcdef0123456789 -in ciphertext.rc4 -out new.txt`

**Questão 21: Para além do ficheiro, precisou de pedir ou receber do(a) seu(ua) colega mais algum dado para executar esta tarefa com sucesso?**

*Resposta:* Sim, precisei, nomeadamente da chave de cifra.

**Questão 22: Ao que é que se refere a palavra *simétrica* nesta designação?**

*Resposta:* Ao facto de a mesma chave de cifra ser usada para cifrar e para decifrar.

---

### Aula 03

**Questão 01: Quantos bits têm os números resultantes da execução do programa?**

*Resposta:* 32 bits (porque um int tem 4 bytes).

**Questão 02: A sequência que o seu computador gerou é a mesma que o computador do(a) seu(ua) colega?**

*Resposta:* Sim, é, porque a sequência depende apenas do valor inicial (*seed*) que, neste caso, é igual nos dois casos.

**Questão 03: Parece-lhe conteúdo cifrado?**

*Resposta:* Sim, parece.

**Questão 04: Dado isto, como é que procederia para decifrar o ficheiro `ciphertext.txt` para o ficheiro `plaintext-2.txt`?**

*Resposta:* Só tenho de invocar a função da seguinte forma: `encrypt("ciphertext.txt", "plaintext2.txt", 123456789)`.

**Questão 05: Parece-lhe bem?**

*Resposta:* Hummm, o facto de o professor estar a perguntar deixa-me desconfiada...

**Questão 06: Consegue ler a mensagem original?**

*Resposta:* Não, de maneira nenhuma. Que estranho?!

**Questão 07: Diria que, se alguém alterasse qualquer byte no ficheiro durante a sua transmissão, o recetor iria notar essa alteração?**

*Resposta:* Sim, neste caso poder-se-ia dizer isso.

**Questão 08: Que tipo de cifra é a AES?**

*Resposta:* Cifra de chave simétrica por blocos.

**Questão 09: Nota algo estranho no ficheiro decifrado?**

*Resposta:* Sim, noto algo até meio (vá) assustador!

**Questão 10: Será que um atacante poderia mudar o texto-limpo sem o conhecer, alterando apenas o criptograma respetivo, e sem ser notado?**

*Resposta:* Sim, pelos vistos sim.

**Questão 11: De 0 a 5, em que 0 é muito má e 5 é muito boa, como classifica o facto de uma cifra ser maneável?**

*Resposta:* 0.

**Questão 12: Usaria uma cifra simétrica contínua para transmitir uma mensagem confidencial sobre um canal que está sujeito a escutas, mas não à alteração das mensagens?**

*Resposta:* Sim, sem problema.

---

### Aula 04

**Questão 01: Sabendo isto, consegue deduzir a fórmula que dá o valor máximo da Entropia?**

*Resposta:* Então não haveria de conseguir? Dá o seguinte: $log_b (n)$.

**Questão 02: Quantos bytes diferentes há? Por outras palavras, qual o valor de `n` para este caso?**

*Resposta:* 256.

**Tarefa 02:**

| Nome            | Tamanho   | Entropia |
| --------------- | --------- | -------- |
| texto.txt       | 631 bytes | 3.165123 |
| comprimido.zip  | 559 bytes | 4.792306 |
| cifrado.aes     | 640 bytes | 5.309780 |
| cmp-cif.zip.aes | 560 bytes | 5.252844 |
| cif-cmp.aes.zip | 845 bytes | 5.129994 |

**Questão 03: Com base na resposta dada antes, qual o valor máximo para a entropia calculada para os bytes de um ficheiro?**

*Resposta:* 2.41.

**Questão 04: Qual é o modo de cifra definido pela opção `-aes128`?**

*Resposta:* *Cipher Block Chaining*.

**Questão 05: Qual é o tamanho da chave de cifra que o usou no comando anterior?**

*Resposta:* 16 bytes.

**Questão 06: Se tivesse de cifrar e comprimir um ficheiro, o que é que faria primeiro?**

*Resposta:* Primeiro comprimir e depois cifrar.

**Questão 07: O que significa o acrónimo AES?**

*Resposta:* *Advanced Encryption Standard*.

**Questão 08: Qual é o tipo da cifra AES?**

*Resposta:* Cifra de chave simétrica por blocos.

**Questão 09: Consegue detetar padrões no ficheiro cifrado?**

*Resposta:* Sim.

**Questão 10: De acordo com a experiência que fez antes, qual é o tamanho do bloco que esta cifra utiliza?**

*Resposta:* 16 bytes.

**Questão 11: O modo ECB precisa de vetor de inicialização?**

*Resposta:* Não, não precisa.

**Questão 12: Não me diga que o comando enunciado antes não funcionou?**

*Resposta:* Digo, digo.

**Questão 13: Como se resolve a situação?**

*Resposta:* Adicionando um vetor de inicialização no final do comando, por exemplo, `-iv 0`.

**Questão 14: O que significa CBC?**

*Resposta:* *Cipher Block Chaining*

**Questão 15: O que é o CBC?**

*Resposta:* Um modo de utilização de uma cifra.

**Questão 16: Consegue detetar algum padrão no texto cifrado?**

*Resposta:* Que interessante, não vejo qualquer padrão.

**Questão 17: O que é que aconteceria se cifrasse outra vez o mesmo ficheiro com a mesma chave no modo CBC, mas com diferente vetor de inicialização?**

*Resposta:* Os dois criptogramas seriam totalmente distintos.

---

### Aula 05

**Tarefa 01:**

    openssl dgst -md5 PodiaSerAFreqMasNaoE.pdf
    openssl dgst -sha1 PodiaSerAFreqMasNaoE.pdf

**Questão 01: Os valores são iguais ou diferentes?**

*Resposta:* Iguanas.

**Questão 02: Qual o significado da resposta anterior?**

*Resposta:* Que, neste caso, o ficheiro que chegou à minha máquina não sofreu erros durante a transmissão. Que, neste caso e confiando no que o Professor afirmou, o ficheiro que descarreguei é, de facto, o ficheiro que está no servidor, e para o qual calculou os valores de *hash*.

**Questão 03: Quem é o criptógrafo que está por detrás do algoritmo MD5?**

*Resposta:* Ron Rivest.

**Questão 04: Já conhecia este criptógrafo ou algum dos seus trabalhos?**

*Resposta:* Sim, já conhecia pelo menos outra obra dele: *Rivest Cipher 4*.

**Questão 05: Quantos bits tem o resumo devolvido por cada uma das funções utilizadas?**

*Resposta:* MD5: 128. SHA1: 160.

**Questão 06: O que abrevia a letra S do acrónimo SHA1?**

*Resposta:* *Secure*.

**Questão 07: O que abrevia a letra D do acrónimo MD5?**

*Resposta:* *Digest*.

**Questão 08: Os valores que obteve são iguais aos originais?**

*Resposta:* Não, são diferentes.

**Questão 09: Acha que o ficheiro pode ter sido modificado enquanto era transmitido ou que sofreu alterações?**

*Resposta:* Sim, deve ter sido isso que aconteceu.

**Questão 10: Nas opções que se seguem, consegue identificar algumas utilidades para as funções de *hash*?**

*Resposta:* Integridade dos dados. Identificação de burlas em ficheiros descarregados da Internet.

**Questão 11: O que é que este URL contém e qual a utilidade desse conteúdo?**

*Resposta:* O `.txt` tem o *hash* dos ficheiros de um `.iso` e `.tar.gz`. Desta forma, o utilizador que for descarregar estes ficheiros consegue ver se os ficheiros mantêm a mesma integridade, comparando os *hash* entre o que descarregou e o que estava no `.txt`.

**Tarefa 5:**
* `openssl dgst -sha1 file.txt`
* `openssl dgst -md5 file.txt`
* SHA1 (original): 8eb1f8feb408ae834301d2f542ba30e5231b685b
* SHA1 (alterado): af7e038080323e52b5e63a7c1850532b24bf7afb
* MD5 (original): 0934b8364b20f11c1e7e92e83b99b442
* MD5 (alterado): f909eca5011b56e5356705ba9920d9ec

**Questão 12: O que é que aconteceu após a alteração de um único byte?**

*Resposta:* Os valores de *hash* ficaram totalmente diferentes.

**Questão 13: Quantos bits ficaram diferentes após a alteração de um único byte?**

*Resposta:* Mudam aproximadamente 1/2 dos bits.

**Questão 14: O que é que aconteceria se se mudassem vários bytes em vez de um só?**

*Resposta:* Obtínhamos exatamente o mesmo comportamento que observamos quando mudamos 1 só byte.

**Questão 15: Parece-lhe haver alguma relação entre o byte alterado no ficheiro e os bits que foram alterados nos respetivos valores de *hash*?**

*Resposta:* Não. As alterações produzidas parecem ser aparentemente imprevisíveis.

**Questão 16: Acha que conseguia alterar o ficheiro original de tal forma que ia obter os mesmos valores de *hash* original?**

*Resposta:* Não estou a ver como iria fazer isso para já, mas creio que iria conseguir. A minha ideia era a seguinte: tentar recuperar uma versão anterior do ficheiro. Correção: *brute force*.

**Questão 17: A que propriedade das funções de *hash* criptográficas se refere a questão anterior?**

*Resposta:* Resistência a colisões.

**Questão 18: Acha que conseguia ao menos arranjar dois ficheiros diferentes com o mesmo valor do SHA1 em tempo útil?**

*Resposta:* Se não, procure explicar. $2^160 / 2^28 = 5.4e39$, logo, não se fazia em tempo útil (160 é o comprimento do SHA1 em bits).

**Questão 19: A que propriedade das funções de *hash* criptográficas se refere a questão anterior?**

*Resposta:* Resistência à descoberta de um segundo texto original.

**Questão 20: Consegue descobrir a palavra-passe que o utilizador `chico-fininho` usa?**

*Resposta:* Sim, é `pedro`.

**Questão 21: Dado a resposta que deu antes, acha que o método *simples* enunciado em cima é seguro?**

*Resposta:* Não, porque não protege contra ataques que usam *rainbow tables* ou tabelas de *hash* pré-computadas. Ora bolas! :S

---

### Aula 06

**Questão 01: Qual é o tamanho do bloco na DES?**

*Resposta:* 8 bytes.

**Questão 02: Como se compila um programa escrito em linguagem C que use funções da *toolkit* do OpenSSL?**

*Resposta:* `cc programa.c  -lcrypto`.

**Questão 03: Consegue cifrar um ficheiro com o OpenSSL e decifrá-lo com o seu programa?**

*Resposta:* Mas é claro que sim. É canja de galinha.

**Questão 04: Como se compila um programa em Java no terminal?**

*Resposta:* `javac sha1sum.java`

**Questão 05: Os valores resumo têm de ser necessariamente iguais?**

*Resposta:* Claro que sim.

**Questão 06: O valor resumo obtido foi igual pelas duas vias?**

*Resposta:* Sim, foi.

---

### Aula 07

**Questão 01: O que significa MAC?**

*Resposta:* *Message Authentication Code*.

**Tarefa 1:**
* `openssl dgst -sha1 texto-limpo.txt > texto-limpo.sha1`
* `openssl enc -aes128 -K 5555ffff1234aedf9876cbcb6546789e -in texto-limpo.sha1 -out texto-limpo.aes-sha1 -iv 0`

**Tarefa 2:**
* `openssl dgst -sha1 recebido.txt > recebido.sha1`
* `openssl enc -aes128 -K 5555ffff1234aedf9876cbcb6546789e -in recebido.sha1 -out recebido.aes-sha1 -iv 0`
* `diff texto-limpo.sha1 recebido.sha1`

**Questão 02: O MAC que recebeu verifica ou não verifica?**

*Resposta:* Sim, verifica.

**Questão 03: O MAC que criou é igual ao MAC que o(a) seu(ua) colega criou?**

*Resposta:* Não, não é, porque o ficheiro é diferente.

**Questão 04: Dado ser um mecanismo da criptografia da chave simétrica, quantas entidades diferentes podem fazer ou verificar um MAC no seio de uma comunicação?**

*Resposta:* Todos os que possuem a chave secreta.

**Questão 05: Quais das seguintes concretizam garantias dadas por um MAC?**

*Resposta:* Garantia de que o ficheiro não sofreu erros aleatórios durante a transmissão (integridade). Garantia de que o ficheiro não foi alterado intencionalmente durante a transmissão (autenticação da origem da informação).

**Questão 06: É possível?**

*Resposta:* Sim, é, com um só comando: `openssl dgst -sha1 -hmac 5555ffff1234aedf9876cbcb6546789e texto-limpo.txt > texto-limpo.hmac`

**Questão 07: Qual a proveniência da letra H no acrónimo HMAC?**

*Resposta:* *Hash*.

**Tarefa 4:**
* `openssl dgst -sha1 -hmac [key] [file]`
* `diff [file] [file]`

**Questão 08: O número `2` é um gerador do grupo $Z^*_17$?**

*Resposta:* Não, não é. Mas o 3 já é!

**Questão 09: Qual foi o número aleatório que o professor usou e de que forma chegou a esse resultado?**

*Resposta:* 14. Tentativa e erro.

**Questão 10: Consegue estimar quanto demoraria a encontrar um `x` aleatoriamente escolhido entre 1 e o número colocado em cima, tendo em conta o tempo que demorou a resolver a questão anterior?**

*Resposta:* Ainda mais do que isto tudo.

**Questão 11: Concorda com esta afirmação?**

*Resposta:* Sim, concordo, porque o atacante apenas conseguia escutar as comunicações.

---

### Aula 08

**Tarefa 1:**

    p = 17, q = 13, N = 13 * 17 = 221, ϕ(N) = (17 - 1) * (13 - 1) = 16 * 12 = 192
    Isto é canja de galinha: e = 7, d = 55
    pk = (7, 221); sk = 55

**Tarefa 2:**

    E(pk, m) = (111 ** 7) % 221 = 19 = c
    E(sk, c) = (19 ** 55) % 221 = 111

**Questão 01: Precisou de algum cuidado especial quando transmitia a chave pública?**

*Resposta:*  Não, e não há qualquer problema de segurança nisso.

**Questão 02: Como é que o(a) seu(ua) colega sabe que a chave pública que vai usar para cifrar a mensagem que está prestes a enviar-lhe é sua?**

*Resposta:* Porque eu lha dei diretamente.

**Questão 03: E se lhe tivesse enviado a chave pública pela Internet, respondia à questão anterior da mesma forma?**

*Resposta:* Respondia que sim, mas com alguma hesitação.

**Tarefa 3:** `(n ** 55) % 221`.

**Questão 04: Qual a chave usada para cifrar?**

*Resposta:* A chave pública.

**Questão 05: Qual a chave usada para decifrar?**

*Resposta:* A chave privada.

**Tarefa 4:**
* `openssl genrsa -out sk-and-pk.pem 1024`
* `openssl rsa -in sk-and-pk.pem -pubout -out pk-nome-aluno.pem`
* `openssl rsa -in pk-nome-aluno.pem -pubin -text -noout`

**Tarefa 5:**
* `openssl rand -hex 16 > secret.key`
* `openssl rsautl -encrypt -pubin -inkey pk-nome-aluno.pem -in secret.key -out secret.key.rsa`.

**Questão 06: Conseguiu cifrar?**

*Resposta:* Claro que consegui.

**Tarefa 6:**
* `openssl rsautl -decrypt -inkey sk-and-pk.pem -in secret.key.rsa -out secretDEC.key`.

**Questão 07: Qual o tamanho do módulo do par de chaves que gerou antes?**

*Resposta:* 1024.

**Questão 08: Conseguiu cifrar o ficheiro?**

*Resposta:* Não. O texto é grande demais e o OpenSSL não deixa cifrar por blocos usando o RSA, visto que este modo (livro de escola), por si só, já é inseguro.

**Questão 09: O que significa o acrónimo PGP?**

*Resposta:* *Pretty Good Privacy*.

**Tarefa 8:**
* Cifragem:
    * `openssl rand -hex 16 > key.key` (para gerar a chave simétrica)
    * `openssl rsautl -encrypt -pubin -inkey pk-nome-aluno.pem -in secret.key -out secret.key.rsa`
    * `openssl enc -aes128 -K 45fb13c4f6248e165e99978fac6f821a -in tuga.txt -out portugal.txt -iv 0`
* Decifragem:
    * `openssl rsautl -decrypt -inkey sk-and-pk.pem -in secret.key.rsa -out secretDEC.key`
    * `openssl enc -d -aes128 -K 45fb13c4f6248e165e99978fac6f821a -in portugal.txt -out henipt.txt -iv 0`
    * `cat henipt.key`

**Questão 10: Ainda tem o par de chaves pública e privada gerado anteriormente?**

*Resposta:* Sou uma moça certinha e tenho tudo guardadinho.

**Tarefa 9:**
* Calcular o valor SHA256:
    * `openssl dgst -sha1 tuga.txt > tuga.sha256`
    * `openssl rsautl -encrypt -pubin -inkey pk-nome-aluno.pem -in tuga.sha256 -out tuga.sig`
* Verificar a assinatura:
    * `openssl rsautl -decrypt -inkey sk-and-pk.pem -in tuga.sig -out dec.sig`
    * `openssl`
    * `diff tuga.sha256 dec.sig`

**Tarefa 10:**
* `openssl genpkey -out privatekey.pem -algorithm rsa 2048`

**Questão 11: Quem é que pode assinar determinada mensagem?**

*Resposta:* Só quem possui a chave privada.

**Questão 12: Quem é que pode fazer o MAC de determinada mensagem?**

*Resposta:* Só quem possui a chave simétrica secreta.

**Questão 13: Quem é que pode verificar a assinatura de determinada mensagem?**

*Resposta:* Só quem possui a chave pública.

**Questão 14: Quem é que pode fazer a verificação do MAC?**

*Resposta:* Só quem possui a chave simétrica secreta.

**Questão 15: Quais são os objetivos de uma assinatura digital?**

*Resposta:* Autenticação da origem da informação. Integridade. Não repúdio. Autenticidade. Dificuldade de falsificação.

**Questão 16: Quais são os propósitos de um MAC?**

*Resposta:* Autenticação da origem da informação. Integridade.

---

### Aula 09

**Questão 01: O que significa GPG?**

*Resposta:* Gnu Privacy Guard.

**Questão 02: O que significa RSA?**

*Resposta:* Rivest Shamir Adleman.

**Questão 03: Qual é a versão do GPG que está a utilizar?**

*Resposta:* 2.2.19.

**Questão 04: Qual dos seguintes comandos gera pares de chaves para o utilizador do GPG?**

*Resposta:* `gpg --full-generate-key`.

**Questão 05: Quais os dois objetivos diferentes dos dois pares de chaves que acabou de criar?**

*Resposta:* Confidencialidade (cifra). Integridade. Autenticação (assinatura-digital).

**Questão 06: Para além da RSA, qual o outro tipo de cifra de chave pública que pode ser usado no GPG?**

*Resposta:* ElGamal. Criptografia sobre curvas elíticas.

**Questão 07: Nota alterações no ficheiro `/dev/random/` à medida que mexe o rato ou escreve?**

*Resposta:* No meu sistema nem preciso fazer nada para ver a atividade imposta pelo sistema no ficheiro.

**Questão 08: Em que eventos é que o sistema operativo se baseia para popular a piscina de entropia que alimenta o `/dev/random`?**

*Resposta:* Movimentos e ações do rato. Introdução de dados pelo teclado. Operações de leitura/escrita no disco. *Interrupts* ao processador.

**Questão 09: Experimentou fazer `cat /dev/random`?**

*Resposta:* Sim, e creio ter o mesmo comportamento que o anterior.

**Questão 10: Acha que é seguro gerar chaves de cifra ou de assinatura digital a partir do `/dev/random`?**

*Resposta:* Acho que é muito seguro. Acho que é muito seguro e, caso tenha de gerar chaves no meu trabalho prático de grupo, vou usar este ficheiro como fonte de aleatoriedade.

**Questão 11: E para ver o porta-chaves privado, que comando deve usar?**

*Resposta:* `gpg --list-secret-keys`.

**Questão 12: Quantas chaves há dentro de cada porta-chaves?**

*Resposta:* 2 chaves.

**Questão 13: Precisa de tomar alguma precaução no envio deste ficheiro?**

*Resposta:* Com confiança: não!

**Questão 14: Já verificou o conteúdo do ficheiro criado? Quais os carateres que lá encontrou?**

*Resposta:* Carateres de 0 a 9. Carateres de a a z. Carateres de A a Z. Carateres de = a /.

**Questão 15: A que porta-chaves é que vai adicionar esta chave?**

*Resposta:* Ao porta-chaves público.

**Questão 16: Qual o comando que vai usar para importar a chave?**

*Resposta:* `gpg --import --armor --input pub-keys-44488.pem`

**Questão 17: Quantas chaves tem o porta-chaves privado?**

*Resposta:* As mesmas que antes.

**Tarefa 8:**

	`--armor` - Opção que codifica a mensagem em Base64.
	`-s` - Opção que pede ao GPG para assinar digitalmente.
	`-e` - Opção que pede ao GPG para cifrar.

**Questão 18: Acha que vai pedir a palavra-passe que guarda o porta-chaves privado?**

*Resposta:* Claro. É necessário cifrar com a chave privada para que as outras pessoas possam cifrar com a pública.

**Questão 19: Porque é que o programa dá este aviso?**

*Resposta:* Porque o programa não é inteligente, e não sabe o que é a confiança. Porque nunca disse ao programa que confiava nesse utilizador e nas chaves dele(a).

**Questão 20: Que opção ou opções faltam no comando anterior?**

*Resposta:* 

**Questão 21: Quando decifrou a mensagem do seu colega, o GPG deu algum aviso acerca da autenticidade da chave usada?**

*Resposta:* Sim, emitiu um aviso.

**Questão 22: Porquê?**

*Resposta:* Porque o programa precisa de aceder ao porta-chaves privado.

**Questão 23: O GPG emitiu algum aviso relacionado com a confiança ou autenticidade da chave utilizada?**

*Resposta:* Não, não emitiu.

**Questão 24: Por curiosidade, como se elimina uma chave do GPG?**

*Resposta:* `gpg --delete-keys Sara Martins`.

**Tarefa 11:** `gpg --armor --output key-amigo.pem --export sara.maria.martins@ubi.pt`

**Questão 25: Quais das seguintes opções refletem essa política?**

*Resposta:* 3 chaves com confiança marginal. 1 chave com confiança absoluta.

**Questão 26: Qual a opção que permite exportar chaves PGP para um servidor?**

*Resposta:* `--send-keys`

**Questão 27: Qual a opção que permite importar chaves PGP a partir de um servidor?**

*Resposta:* `--recv-keys`

**Questão 28: Dadas as respostas que deu na secção anterior, o que pode dizer acerca da confiança que o GPG terá na chave com 10 assinaturas?**

*Resposta:* Que o GPG não deposita qualquer confiança nessa chave. 

**Questão 29: A sua instância do GPG confia absolutamente na chave com as duas assinaturas?**

*Resposta:* Sim, sem sombra de dúvidas.

---

### Aula 10

**Questão 01: O que significam as várias letras do acrónimo antes referido?**

*Resposta:* 

**Questão 02: Qual o nome dessa iniciativa?**

*Resposta:* 

**Questão 03: Quais são os maiores patrocinadores dessa iniciativa?**

*Resposta:* 

**Questão 04: Consegue reconhecer o melhor comando para o conseguir?**

*Resposta:* 

**Questão 05: Qual o comando que pode usar para conseguir este efeito?**

*Resposta:* 

**Questão 06: A instrução SQL seguinte produz o resultado pedido antes?**

*Resposta:*

**Questão 07: Faz sentido usar o tipo `VARCHAR` para o primeiro atributo e `CHAR` para os outros dois?**

*Resposta:* 

**Questão 08: Para que serve o `salt` no contexto desta tabela e da autenticação de utilizadores?**

*Resposta:* 

---

### Aula 11

**Questão 01: Qual o endereço IPv4 do seu computador?**

*Resposta:* 

**Questão 02: A sua máquina tem um endereço IPv6?**

*Resposta:* 

**Questão 03: Qual o nome da rede IPv4 em que se insere a sua máquina?**

*Resposta:* 

**Questão 04: Como é que se pode especificar a gama de 255 endereços na rede que indicou acima?**

*Resposta:* 

**Questão 05: Que comando/opções utilizou?**

*Resposta:* 

**Questão 06: De que forma é que o `nmap` identifica as máquinas ligadas?**

*Resposta:* 

**Questão 07: Tomou nota dos endereços *Internet Protocol* (IP) das máquinas ligadas à rede?**

*Resposta:* 

**Questão 08: Consegue identificar, pelo IP, alguma dessas máquinas imediatamente?**

*Resposta:* 

**Tarefa 3:**
* IP1:
* IP2:
* Comando:

**Questão 09: A que conclusões é que chegou?**

*Resposta:* 

**Questão 10: Utilizando esta opção, consegue ver a assinatura que foi usada na identificação?**

*Resposta:* 

**Questão 11: Para uma máquina *Windows*, o que é que o `nmap` tem a dizer sobre isto?**

*Resposta:* 

**Questão 12: Qual o endereço IP do *Gateway* de rede?**

*Resposta:* 

**Questão 13: Já agora, qual é o sistema operativo do *gateway* da rede?**

*Resposta:* 

**Questão 14: Qual dos seguintes identifica a sua própria máquina ou o endereço IP do *localhost*?**

*Resposta:* 

**Questão 15: Qual o comando que utilizou?**

*Resposta:* 

**Questão 16: Conseguiu fazer a deteção do sistema operativo que corre na sua máquina?**

*Resposta:* 

**Questão 17: Qual é o motivo por detrás da resposta anterior?**

*Resposta:* 

**Questão 18: Já experimentou desligar alguns desses serviços (e.g., `systemctl stop sshd`) e tentar novamente?**

*Resposta:* 

**Questão 19: Qual o comando que utilizou?**

*Resposta:* 

**Questão 20: Qual dos seguintes comandos lhe permitem identificar os serviços (e a sua versão) que estão a correr no sistema operativo *Microsoft Windows Server*?**

*Resposta:* 

**Tarefa 7:**

**Questão 21: Encontrou alguma impressora de rede durante as suas incursões?**

*Resposta:* 

**Questão 22: Qual a marca e modelo?**

*Resposta:* 

**Questão 23: Quais as portas disponíveis para este equipamento?**

*Resposta:* 

**Questão 24: Há alguma porta que lhe pareça ser de configuração na impressora?**

*Resposta:* 

**Questão 25: Já tentou aceder via *browser*/*telnet*/ssh a essa porta?**

*Resposta:* 

**Questão 26: Qual a motivação principal para forjar o endereço fonte?**

*Resposta:* 

**Questão 27: O que significa SYN?**

*Resposta:* 

**Tarefa 11:**

**Questão 28: Qual a opção/letra que falta a seguir ao - para que o ataque de inundação seja do tipo SYN?**

*Resposta:* 

**Tarefa 12:**
* `-i` - 
* `-A` - 
* `-v` - 
* `-t` - 

**Tarefa 13:**

**Questão 29: O que pode concluir deste exercício?**

*Resposta:* 

**Questão 30: Como é que o problema anterior se pode resolver em ligações HTTP?**

*Resposta:* 