# Administração de Sistemas em Rede

##### Atualizado em 06-05-2022
###### A partir de: sebenta, exercícios das aulas práticas

## Aulas Teóricas

### Aula 01

**Administração de sistemas em rede** é um ramo da engenharia que lida com a gestão operacional de humanos e dos sistemas computacionais - montar uma rede de computadores, colocá-os a funcionar e mantê-los em funcionamento, apesar das atividades dos utilizadores que tendem a causar falhas nos sistemas.

**Administração de redes** lida com a gestão de dispositivos de infraestrutura de redes. **Administração de sistemas** lida com a gestão de computadores, acoplados a uma rede ou não - planeia e desenha uma comunidade eficiente de computadores de modo a que utilizadores possam realizar o seu trabalho (*hardware*, *software*, suporte, diagnóstico, reparação, prevenção):
* Desenhar uma rede lógica e eficiente;
* Lançar um grande número de máquinas que podem ser facilmente atualizadas;
* Decidir que serviços são necessários;
* Planear e implementar segurança adequada;
* Providenciar um ambiente confortável para utilizadores;
* Desenvolver formas de corrigir erros e problemas;
* Manter registo e compreender como usar a enorme quantidade de conhecimento que cresce a cada ano.

Administrar sistemas é um exercício de equilíbrio com paciência, compreensão, conhecimento e experiência, que exige trabalho com recursos limitados e capacidade de improviso. É necessário saber e ganhar confiança pela experiência, mas conhecer as próprias limitações para evitar erros descuidados. Um administrador de sistemas (*sysadmin*) necessita de muita dedicação, com capacidades teóricas e práticas, e tem o poder para fazer mudanças radicais sobre sistemas, sobre escolhas lógicas. Deve preparar-se para lidar com *bugs* e trabalhar com eles, qualquer que seja a razão da sua existência.

**Metaprincípios da administração de sistemas:**
* *Princípio 1. **Política*** - deve estar escrito num ficheiro os princípios que regulam a administração dos sistemas, sobre o que se quer e o que se deve fazer, em relação ao que se pode custear;
* *Princípio 2. **Previsibilidade*** - trabalha-se sobre um sistema previsível (base para confiabilidade e segurança), para não haver problemas inesperados;
* *Princípio 3. **Escalabilidade*** - sistemas devem crescer em concordância com as políticas.

### Aula 02

Um *sysadmin* deve conhecer os desafios apresentados por um sistema e definir as regras e procedimentos a aplicar, de acordo com leis, regulamentos, melhores práticas e senso comum. Para um *sysadmin*, um sistema é uma colaboração organizada entre humanos e computadores para resolver um problema ou fornecer um serviço.

Um *sysadmin* deve manter-se invisível, recorrendo a diversas formas para manter o trabalhado fluido e eficiente:
* Ter um sistema de *trouble-tickets* - receber e organizar os pedidos, para não esquecer nenhum requerimento e entender a perceção dos utilizadores da qualidade do serviço;
* Gerir corretamente os pedidos rápidos - ter alguém que lide com as interrupções diárias (tratando-as ou delegando-as para um *helpdesk*), de modo a que os restantes possam trabalhar sem interrupções;
* Adotar três políticas de poupança de tempo - por exemplo, com códigos para definir as prioridades das tarefas a cumprir;
* Iniciar cada novo anfitrião num estado conhecido - ter um mínimo denominador comum entre os sistemas, que possa ser usado para recuperar de uma falha;
* Outros - bom sistema de comunicação, documentação, monitorização de sistemas...

Estados possíveis de um sistema: ![](https://i.imgur.com/LrgWsC5.png)

Um **sistema humano-computador** é uma colaboração organizada não-determinística entre humanos e computadores para resolver um problema ou fornecer um serviço.

Um *sysadmin* deve gerir o *hardware* (cumprindo as instruções, tendo em conta a sensibilidade e a fragilidade, controlando o ambiente (humidade, frio, calor, energia)) e o *software* (escolhendo o sistema operativo certo para as tarefas, tendo cuidado com *updates*, verificando incompatibilidades). Deve seguir o princípio de **privilégio mínimo:** restrição de privilégios desnecessários que protege um sistema de dano acidental ou malicioso e infeção por vírus e previne utilizadores de esconder as suas ações com identidades falsas. Um *sysadmin* deve ter em conta que humanos precisam de treino, explicação, paciência e documentação para autoajuda.

### Aula 03

**Sistema** - tanto o sistema operativo, como o conjunto de todos os computadores que cooperam e interagem numa rede. Um sistema possui requisitos (infraestrutura de computação dedicada/em rede, aplicações, recursos computacionais e ligações ao exterior para atingir os objetivos de uma organização).

Num sistema, o *hardware* deve ser inventariado e configurado, mantendo-se uma monitorização do seu desempenho e atualização. O *software* deve ser inventariado e configurado de acordo com licenças, interdependências, fóruns e máquinas virtuais. A rede deve ter a largura de banda necessária, com VLANs e VPNs (se aplicável) e conexões *upstream* e *downstream*. Os utilizadores devem ser identificados (código, *login*, posição interna, grupos, privilégios).

O **ciclo de vida de um sistema** integra *conceção*, *implementação* e *manutenção* (que engloba BURN (*Backup*, *Update*, *Recovery*, *New System*) e compatibilidade inter-sistemas).

### Aula 04

O **sistema de ficheiros** é a forma como o sistema operativo gere o armazenamento dos ficheiros no volume. Deve ser conhecido, tanto por estrutura, limitações (*cluster*: grupo de máquinas que funciona como um único sistema; *grid*: grupo de *clusters*), problemas de portabilidade, retrocompabitilidade e políticas de privilégio.

Servidores são equipamento caro e crítico, cuja falha é muito perigosa. Servidores devem manter a integridade dos dados (devendo ter-se um *backup* de um *backup*) e devem ser mantidos seguros (em *data centers* ou ambientes controlados). Para escolher um servidor, **escalabilidade** é o principal princípio a ter em conta: servidores são menos e mais caros, devendo evitar-se *single points of failure*; também deve ter-se em conta: extensibilidade, performance de CPU, performance de I/O, opções de atualização, montagem em bastidores, necessidade de acesso lateral, opções de disponibilidade, contratos de manutenção, opções de gestão. Também é necessário considerar MTBF (*Mean Time Between Failure*), MTTR (*Mean Time to Repair*) e RAID (*Redundant Array of Independent Disks*).

Além disso, é preciso ter em conta a **previsibilidade** - antecipar movimentos/tendências futuras de forma a escolher o melhor tipo de equipamento, bem como ter em conta os fóruns e experiências prévias de outros *sysadmins* - e a **política** - deve escolher-se o melhor equipamento de acordo com as metodologias de trabalho.

A saúde do disco e da CPU são importantes para equipamentos específicos da *workstation*. Deve-se garantir que o servidor opera dentro dos limites definidos pelo fabricante e conta com um ambiente controlado (temperatura, humidade, ventilação, ausência de poeiras, boa instalação elétrica).

### Aula 05 - easter egg

Para definir as *network portion* e *host portion* de um endereço, dispositivos usam um padrão de 32 bits - ***subnet mask*** - que define onde procurar por essas porções num endereço IPv4.

**DHCP** (*Dynamic Host Configuration Protocol*) - método preferencial de atribuir endereços IPv4 a anfitriões em redes grandes, uma vez que reduz o trabalho de *staff* de apoio a redes e elimina, virtualmente, erros de entrada.

**IPv4** pode comunicar por *unicast* (enviar um pacote de um computador para um computador), *broadcast* (enviar um pacote de um computador para todos os computadores de uma rede) e *multicast* (enviar um pacote de um computador para vários computadores numa ou várias redes).

A transição de IPv4 para **Ipv6** pode ser feita por *dual-stack* (coexistência de IPv4 e IPv6 na mesma rede), *tunnelling* (pacotes IPv6 são encapsulados dentro de pacotes IPv4) e *translation* (um pacote IPv6 é traduzido para um pacote IPv4, e vice-versa).

### Aula 06

Os sistemas de ficheiros devem ser compreendidos para saber qual a melhor escolha em termos de **manutenção** (segurança, *backup*, compatibilidade), **movimento de ficheiros** (tamanho, privilégios, localização) e **eficiência do sistema operativo**.

Dados são o cerne das organizações modernas. A perda de dados pode ter causa humana (sobreescrita ou eliminação de ficheiros), de *hardware* (falha) ou de *software* (corrupção, sobre-escrita ou eliminação de ficheiros, falhas na cibersegurança).

**RAID** (*Redundant Array of Independent Disks*) é uma tecnologia de virtualização de armazenamento de dados que combina múltiplos componentes de discos físicos numa ou mais unidades lógicas para aumentar a redundância de dados. O uso de RAID não implica tempo total *online*, não substitui *backups*, não protege contra corrupção de dados, erro humano ou problemas de segurança e pode não permitir o crescimento dinâmico do *array*.

***Small Computer System Interface*** (SCSI) é uma arquitetura cliente-servidor, em que o cliente é chamado *iniciador* e envia pedidos ao servidor, e o servidor é chamado *alvo* e recebe, processa e responde os pedidos do iniciador. SCSI suporta transferência de grandes quantidades de *input*/*output* de informação em blocos.

***Network Attached Storage*** (NAS) (oposto a *Direct Attached Storage* (DAS)) é um dispositivo dedicado ao armazenamento que opera num modo cliente-servidor, conetado ao servidor de ficheiros via LAN. Utiliza os protocolos NFS (*Network File System*) ou CIFS (*Common Internet File System*). Não tem limites de distância, embora possa ter problemas de velocidade e latência, com falhas de segurança.

***Storage Area Network*** (SAN) é uma rede especializada e dedicada a alta velocidade que junta servidores com armazenamento, em que o armazenamento está separado dos processadores. Tem alta capacidade, disponibilidade, escalabilidade, facilidade de (re)configuração. O FCP (*Fibre Channel Protocol*) está estabelecido como a arquitetura subjacente da SAN. Permite consolidação, integridade e partilha de dados, escalabilidade, *backup* e recuperação de dados, tolerância a desastres.

`fim de matéria para a primeira frequência`

### Aula 07

NTP (*Network Time Protocol*) - protocolo que permite sincronizar os tempos do sistema com os da aplicação (por exemplo, `crontab`, que permite a um anfitrião executar tarefas num horário predeterminado).

Cada sistema operativo tem uma forma específica de criação de um utilizador local, tendo em conta nome do utilizador, palavra-passe, grupos e nível de acesso.

**Desastre** - qualquer evento catastrófico que cause uma falha massiva que afete um edifício ou local inteiros. Para se criar um plano de recuperação de desastre, é necessário fazer uma avaliação de risco.

### Aula 08

Há sempre um risco de acontecer um desastre, qualquer que seja o sistema. Um desastre está relacionado com as funcionalidades de um determinado sistema. A partir da possibilidade da ocorrência de um desastre, cria-se uma lista de riscos, que devem ser minimizados e mitigados.

**Exercício**

```
Quatro sistemas:
1. Smartphone
2. Desktop
3. Servidor de email
4. Infraestrutura de rede

Riscos de desastre:
1.1. Cair na água;
1.2. Problemas na bateria;
1.3. Sobreaquecimento;
1.4. Roubo, furto, perda;
1.5. Quebra;
1.6. Malware, software mal intencionado;
1.7. Erros de software;
1.8. Avaria na rede;
1.9. Falta de armazenamento;
1.10. Falta de bateria, problemas de alimentação...

2.1. Queda, inundações, climatização;
2.2. Avaria nos periféricos;
2.3. Sobreaquecimento, incêndios;
2.4. Roubo, furto, perda;
2.5. Malware, software mal intencionado;
2.6. Erros de software;
2.7. Avaria na rede;
2.8. Falta de armazenamento;
2.9. Problemas de alimentação.

4.1. Queda, inundações, climatização;
4.2. Falha em ponto único/crítico;
4.3. Sobreaquecimento, incêndio;
4.4. Roubo, furto, perda;
4.5. Malware, software mal intencionado;
4.6. Erros de software;
4.7. Avaria na rede;
4.8. Falta de recursos;
4.9. Problemas na alimentação.

Minimização (ser proativo, prevenir)
1.1. Boas práticas (educação);
1.2. Não expor a calor, escolha criteriosa do equipamento/fabricante/marca...;
1.3. Não expor a calor;
1.4. Boas práticas (educação), ter cuidado;
1.5. Boas práticas (educação), usar capa de proteção;
1.6. Boas práticas (educação), usar antivírus; estar atento aos fóruns;
1.7. Updates de software, estar atento aos fóruns;
1.8. Operadoras diferentes, verificar cobertura de rede;
1.9. Unidades extra de armazenamento (cartão SD, cloud);
1.10. Modo poupança de bateria, carregar, escolha criteriosa do equipamento.

4.1. Boas práticas (educação);
4.2. Eliminar SPF, adicionar redundância;
4.3. Boas práticas, sistemas de alarme;
4.4. SNMP (Simple Network Management Protocol);
4.5. Boas práticas (educação), usar antivírus; estar atento aos fóruns;
4.6. Updates de software, estar atento aos fóruns;
4.7. Redundância;
4.8. Boas práticas (educação), unidades extra de armazenamento;
4.9. Boas práticas (educação), UPS.

Mitigação (ser reativo)
1.1. Colocar em arroz;
1.2. Trocar a bateria, reparar o equipamento;
1.3. Reparação do equipamento;
1.4. Uso de backup (hardware, software, dados);
1.5. Reparar o equipamento, uso de backup;
1.6. Usar antivírus, serviços de atualização;
1.7. Atualização de serviços;
1.8. Access Point portátil;
1.9. Não se aplica;
1.10. Carregar a bateria, powerbank.

4.1. Reparação do equipamento;
4.2. Reparação do serviço, uso de backup, substituição;
4.3. Extintores, reparação de serviço;
4.4. Reparação de serviço, uso de backup (hardware, software, dados);
4.5. Usar antivírus, serviços de atualização;
4.6. Atualização de serviços;
4.7. Reparação do equipamento;
4.8. Falta de recursos;
4.9. UPS, geradores.
```

---

### Aula 09

Para criar um **plano de recuperação de desastres**, também é necessário ter em conta:
* **Política de segurança** - definir objetivos claros, assegurando que os compromissos legais e contratuais são cumpridos e que as implicações económicas de uma falha de segurança são compreendidas;
* **Segurança organizacional** - definir políticas e fornecer conselhos multidisciplinares;
* **Classificação e controlo de ativos** - manter um inventário de ativos, que classifique cada ativo de acordo com o nível apropriado de segurança, e determinar procedimentos para lidar com diferentes níveis de informação;
* **Segurança de pessoal** - o *staff* deve ser identificado, ter responsabilidades de segurança e ter formações sobre possíveis ameaças e procedimentos de combate, de modo a que falhas de segurança e fraquezas sejam reportadas no imediato;
* **Segurança física e de ambiente** - envolve um perímetro de segurança com restrições físicas, bem como ambientes seguros e controlados;
* **Gestão de comunicações e operações** - o processamento e tratamento da informação devem ser especificados com procedimentos apropriados para o nível de informação, incluindo autorizações e documentação significativa de alterações para permitir análises;
* **Controlo de acesso** - manutenção de utilizadores, palavras-passe e chave, direitos de acesso, segregação de ativos independentes, autenticação, sincronização, BYOD;
* **Desenvolvimento e manutenção de sistemas** - a segurança deve ser imbutida nos sistemas desde o princípio;
* **Manutenção de continuidade de negócio** - estimar o impacto de catástrofes e falhas de segurança na empresa;
* **Conformidade** - leis e regulamentos devem ser respeitados, de acordo com a localização da empresa.

Para criar um **plano de recuperação de desastres** deve medir-se e quantificar-se os riscos e manter os dados atualizados. Também se deve conceber e implementar ações de minimização do risco (e testar e verificar a sua eficácia) e ações de atenuação de desastres (e testar, se possível). Repetir. Deve ter-se em vista "quem, quando, como, onde, com quê, com quem, em quanto tempo, para quê".

Conclusões:
* É importante compreender quais serviços são os mais críticos e quais as restrições de tempo para restauros.
* É necessário saber quais os desastres possíveis de acontecer;
* Um plano de recuperação de desastres requer planeamento prévio;
* O plano deve ter formas simples de limitar o dano, bem como formas mais complexas e caras;
* Deve haver redundância total, incluindo uma localização redundante.

Tanto para prevenir como para corrigir, um administrador de sistemas tem uma poderosa ferramenta: ***logs***. *Logs* são registos dos acontecimentos que ocorrem num sistema, com demasiada informação "inútil" que necessita de ser filtrada. Por omissão, os *logs* são escritos localmente, embora possam ser feitos num servidor ou para um servidor. Podem ser classificados como:
* De informação - permitem a utilizadores e administradores saber que algo benigno ocorreu;
* Debug - geradas de sistemas de *software*, ajudam *developers* a identificar e resolver problemas na execução de código;
* Aviso - ocorrem em situações em que haja coisas necessárias ou em falta para um sistema, mas sem impactar a sua operação;
* Erro - transmitem erros que ocorrem a diversos níveis de um sistema, sendo necessária investigação para chegar à causa raiz do erro;
* Alerta - indicam que algo interessante aconteceu.

*Loghost* é a máquina que armazena os *logs*; *syslog* é o protocolo que permite visualizar/transmitir mensagens de *logs*; SNMP (*Simple Network Management Protocol*) gera *logs*. Um *log* deve ter, pelo menos, uma *timestamp*, uma origem e informação. Gerir *logs* é importante (para gestão de recursos, deteção de intrusões, resolução de problemas, análise forense), mas dá muito trabalho, ocupa recursos e exige mineração, sendo necessário controlar um equilíbrio.

*Logs* devem informar sobre o acontecimento: o quê (com detalhe), quando, onde, quem esteve envolvido, a origem.

### Aula 10

VPN.

### Aula 11

---
---

## Aulas Práticas

### Aula 01

**1.1.** `uname -o`

**1.2.** `uname -v`

**1.3.** `uname -p`

**1.4.** `uname -a`

**1.5.** `logname`

**1.6.** `hostname`

**1.7.** `who`

**2.1:** `cal nov 1986`

**2.2.** `cal feb 1955`

**2.3.** `cal jan 1960`

**2.4.** `cal apr 2020`

**2.5.** `cal`

**2.6.** `date "+%d/%m/%y"`

**2.7.** `date "+24 Hour: %T   12 Hour: %r"`

**3.** `pwd`

**4.** `mkdir Lab01`

**4.1.** `cd Lab01` > `mkdir 44488`

**4.2.** `cd 44488`

**5.** `cd`

**5.1.** `ls -l`

**6.**

    Caminho absoluto: cd /home/sara/ASR/Lab01/44488/
    Caminho relativo: cd Lab01/44488

**6.1.** `cd ..` > `rm -r 44488`

**7.** `mkdir ./grumble`

**8.** `cd`

**9.** `cd ..` > `rm -r ./grumble`

**10.**

    touch primeiro.txt
    touch segundo.txt
    touch terceiro.txt

**10.1.**

    cat primeiro.txt
    cat segundo.txt
    cat terceiro.txt

**10.2.**

    nano primeiro.txt
    echo "texto" > segundo.txt
    cat > terceiro.txt
    
**10.3.**

    cat primeiro.txt
    cat segundo.txt
    cat terceiro.txt
    
**10.4.** `echo "mais texto" >> primeiro.txt`

**10.5.** `rm terceiro.txt`

**11.** `touch .oculto`

**11.1.** `cp primeiro.txt .oculto`

**11.2.** `cat .oculto`

**11.3.** `ls -a`

**12.** `ln segundo.txt snd`

**12.1.** `cat snd`

**12.2.** `type alias`

**13.** `cp segundo.txt segundoCopia.txt`

**13.1.** `mkdir COMPARAR` > `mv segundoCopia.txt COMPARAR`

**14.** `mv .oculto COMPARAR`

**15.** `cmp .oculto segundoCopia.txt`

**15.1.** `nano .oculto` > `cmp .oculto segundoCopia.txt`

**15.2.** `diff .oculto segundoCopia.txt`

**15.3.** `cd ..` > `rm -r COMPARAR`

**16.** `mv Lab01 Laboratorio1_ASR`

**17.** `cp - r Laboratorio1_ASR Laboratorio1_ASR_backup`

---

### Aula 02

**1.** `name="Sara"` > `echo $name`

**2.** `export AGE=21` > `echo $AGE`

**3.** `echo $name`, `echo $AGE`. Não conseguimos ver o valor da variável local, uma vez que, tal como o nome indica, está apenas presente na *shell* onde foi criada.

**4.** `exit`

**4.1.** `set | less`

**4.2.** `env`

**5.** `unset name`, `unset AGE` > `set | less`

**6.** `echo $PATH`

**7.1.** `which ls`

**7.2.** `which man`

**7.3.** `which cal`

**7.4.** `which pwd`

**8.** `cd ASR` > `mkdir Lab02` > `PATH=$PATH:/home/sara/ASR/Lab02` > `echo $PATH`

**9.** `echo "echo hello $USER" > hello.sh` > `chmod a+x hello.sh`

**9.1.** `hello.sh`

**9.2.** `which hello.sh`

**10.** `less .bashrc`

**11.** `grep PATH .bashrc`

**12.** `history`

**13.** `!15`

**14.** `HISTCONTROL=ignoredups` > `history`

**15.** `HISTCONTROL=ignorespace` > `history`

**16.** `history -c`

---

### Aula 03

**1.** `echo *`

**2.** `echo D*`

**3.** `echo D*n*`

**4.** `echo /usr/bin/pyd*`

**5.** `echo /usr/bin/py*`

**6.** `echo /usr/bin/????`

**7.** `echo P?*`

**8.** `echo [TMP]*`

**9.** `echo /etc/rc[4-9]*`

**10.** `echo [A-J]???*`

**11.** `echo D[m-z]???????`

**12.** `echo /etc/p*t*[1-4]`

**13.** `echo /etc/rc[^0-2]*`

**14.** `ls -l /usr/bin`

**15.** `ls -lS /usr/bin`

**15.1.** `ls -lSr /usr/bin`

**16.** `ls -R`

**17.** `file /usr/bin/lorder`

**18.** `touch teste` > `ls -l teste` > `touch -t 201902151435 teste`

**18.1.** `stat teste`

**19.** `locate hosts`

**20.** `sudo find /etc/ -name hosts`

**21.** `find /etc/ -mtime -7 2>/dev/null`

**21.1.** `find /etc/ -mmin -45 2>/dev/null`

**22.** `find / -size +512k 2>/dev/null`

**23.** `touch sample` > `find ~/ -empty 2>/dev/null`

**24.** `find /usr/bin 2>/dev/null | wc -l`

**24.1.** `find /usr/bin -name "*.sh" 2>/dev/null | wc -l`

**25.** `cp /etc/*.conf .` > `ls` > `find ~ -name "*.conf" -exec rm {} \;` > `ls`

**25.1.** `cp /etc/*.conf .` > `ls` > `find ~ -name "*.conf" -ok rm {} \;` > `ls`

---

### Aula 04

**1.** `cat /etc/hosts`, `cat /etc/hostname`

**2.** `cat /etc/hosts /etc/hostname`

**3.** `cat /etc/hosts /etc/hostname > file.txt`

**4.** `less /etc/passwd`

**5.** `less /etc/passwd` > `/usr`

**6.** `cp /usr/share/dict/words dictionary.txt`

**6.1.** `split dictionary.txt -d fragment.txt` > `ls fragment.txt*`

**6.2.** `split dictionary.txt -d -l 2000 fragment.txt`

**7.** `cd Documents` > `nl newhome.txt` ou `nl -ba newhome.txt` ou `cat -b newhome.txt` ou `cat -n newhome.txt`

**8.** `head newhome.txt`

**8.1.** `head -n 5 newhome.txt` ou `head -5 newhome.txt`

**9.** `tail newhome.txt`

**9.1.** `tail -n 5 newhome.txt` ou `tail -5 newhome.txt`

**10.** `tail -n +500 dictionary.txt`

**11.** `head -n 20 dictionary.txt > first.txt` `tail -n 20 dictionary.txt > final.txt`

**12.** `sort -k 1 newhome.txt`

**13.** `cat newhome.txt | tr 'a-z' 'A-Z' newhomecopy.txt`

**13.1.** `cat newhome.txt | tr 'e' '3' newhomecopy.txt`

**14.** `cat /etc/passwd | grep "root"` ou `grep 'root' /etc/passwd`

**14.1** `grep 'bash$' /etc/passwd`

**14.2.** `grep 'b.*h' /etc/passwd`

**14.3.** `grep ':[2-6]:' /etc/passwd`

**15.** `grep '^ag.*g$' /usr/share/dict/words`

---

### Aula 05

**1.** `echo $EDITOR`

**2.** `vi newFile.txt`

**2.1.** `ls -lR /usr > newFile.txt`

**2.2.** `i` > ESC > `:w`

**2.3.** `i` > ESC > `:w`

**2.4.** `dd`

**2.5.** `G`

**3.** `gg` > `/local` > `n`

**4.** `/local` > `n` > `dw`

**4.1.** `1G` > `5dd`

**5.** `1G` > `3yy` > `G` > `P`

**5.1.** `u` > `:q!`

**6.** `1G` > `cc` > *Resultado:* > ESC > `:w` > `:q!`

**6.1.** `head newFile.txt`, `tail newFile.txt`

**7.** `nano bash.rc` > CTRL + X > `source bash.rc`

**8.** `sort` > CTRL + D

**9.** `ls > output.txt`

**9.1.** `date >> output.txt`

**10.** 

---

### Aula 06

---

### Aula 07

---

### Aula 08