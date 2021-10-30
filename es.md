# Engenharia de _Software_

##### Atualizado em 30-10-2021
###### A partir de: sebenta, aulas práticas

## Aulas Teóricas

### Aula 01

**_Software_** - programas de computador e documentação associada, que podem ser desenvolvidos para um utilizador particular ou um mercado geral. Produtos podem ser **genéricos** (sistemas independentes que podem ser utilizados por qualquer pessoa) ou **customizados** (sistemas comissionados para atingir fins específicos).

**Engenharia de _software_** - disciplina de engenharia (teorias e métodos apropriados para resolução de problemas com restrições organizacionais e financeiras) envolvida todos os aspetos de produção de _software_ desde as etapas iniciais da especificação do sistema até à manutenção do sistema (gestão de projeto, desenvolvimento de ferramentas, métodos).

**Engenharia de _software_ vs engenharia informática** - engenharia informática foca-se na teoria e fundamentos; engenharia de _software_ envolve-se com os aspetos práticos e úteis do desenvolvimento de _software_.

**Engenharia de _software_ vs engenharia de sistemas** - engenharia de sistemas foca-se nos aspetos do desenvolvimento de sistemas baseados em computador (_hardware_, _software_ e engenharia de processo); engenharia de _software_ é parte integrante do processo (especificação de sistemas, _design_ de arquitetura, integração e desenvolvimento).

**Processo de _software_** - escrita de frases em linguagem computacional (não apropriada para a descrição do problema a resolver): o engenheiro de _software_ deve entender um problema, definir como pode ser resolvido por um computador e escrever os comandos que lhe permitem resolver o problema. As atividades de processo de _software_ são:
* _Especificação de_ software - clientes e engenheiros definem o _software_ a profuzir e as restrições na sua operação;
* _Desenvolvimento de_ software - _design_ e programação do _software_;
* _Validação do_ software - verificação do _software_ para assegurar que cumpre os requisitos;
* _Evolução do_ software - modificação do _software_ para refletir os diferentes requisitos do cliente e do mercado.

**Modelo de processo de _software_** - representação simplificada do processo de _software_ apresentada de uma perspetiva específica (_workflow_, sequência de atividades; _data-flow_, fluxo de informação; _role-action_, quem faz o quê).

**Custo da engenharia de _software_** - depende do tipo e dos requisitos dos atributos do sistema, e o modelo de desenvolvimento utilizado.

**Atributos de bom _software_**:
* _Manutenção_: escrita de modo a facilitar a evolução das necessidades dos clientes;
* _Confiabilidade e segurança_: não causar dano físico ou económico no caso de falha do sistema, nem permitir o acesso ou dano do sistema de utilizadores maliciosos;
* _Eficiência_: não desperdiçar recursos do sistema (ciclos de memória, processador); inclui capacidade de resposta, tempo de processamento, uso de memória;
* _Aceitabilidade_: aceitação pelos clientes para o qual é desenvolvido (deve ser percetível, usável e compatível com outros sistemas).

**Desafios da engenharia de _software_**:
* _Heterogeneidade_: distribuição nos diferentes sistemas operativos;
* _Mudança empresarial e social_: mudança do _software_ existente e desenvolvimento rápido de novo _software_;
* _Segurança e confiança_;
* _Escala_: distribuição por diversas escalas, de sistemas pequenos e portáteis individuais a sistemas baseados em nuvem globais;
* _Sistemas legados_: manutenção e atualização de sistemas antigos valiosos;
* _Entrega_: rápida entrega de _software_.

---

### Aula 02

**Produtos de _software_** são sistemas de _software_ genérico que providenciam funcionalidades que são úteis a uma gama de utilizadores. Métodos e técnicas de engenharia de produtos de _software_ evoluíram das técnicas de engenharia de _software_ de suporte de sistemas customizados.

Um problema (cliente) gera requisitos (cliente e _developer_), implementados por _software_ (_developer_), que pode levantar novos problemas. O ponto de partida para o desenvolvimento de _software_ é um conjunto de requisitos que pertencem a um cliente externo e definem as suas necessidades para apoiar os seus processos de negócio, que podem ser alterados a qualquer momento pelo cliente e devem ser refletidos no _software_.

Uma oportunidade inspira características de produto, implementadas em _software_ que concretiza novas oportunidades. O ponto de partida é uma oportunidade através da qual se desenvolve um produto de _software_ que tira vantagem desta e a torna apetecível aos clientes. O desenho, características, desenvolvimento e mudanças do produto devem ser definidas por quem apanhou a oportunidade, devendo haver um rápido lançamento para apanhar o mercado.

**Linha de produtos de _software_** - conjunto de produtos de _software_ que partilham um núcleo comum, em que cada membro inclui adaptações e adições específicas a cada utilizador; pode ser utilizada para implementar um sistema customizado para um utilizador cujas necessidades não podem ser resolvidas com um produto genérico.

**Plataforma de _software_** - produto que inclui funcionalidades de modo a que novas aplicações possam ser construídas sobre ela.

**Modelos de execução de _software_**:
* _Independente_ - executa apenas no computador do cliente;
* _Híbrido_ - certas funcionalidades estão implementadas no computador do cliente, outras nos servidores dos _developers_;
* _Serviço de software_ - todas as funcionalidades estão implementadas nos servidores dos _developers_, acedidos a partir de aplicações.

**Visão de produto** é o ponto de partida para o desenvolvimento de produtos de _software_, afirmações simples que definem a essência do produto a ser desenvolvido que respondem a três questões fundamentais: o que é o produto; qual é o público alvo; por que deveria ser comprado. _Template_ de visão de Moore:
* **Para quem** (público alvo);
* **Quem** (contexto da necessidade ou oportunidade);
* **Nome**;
* **O quê** (benefícios, razão convincente para comprar);
* **Diferenciação** (alternativa competitiva);
* **Nosso produto** (afirmação da diferenciação).

**Fontes de informação para desenvolver visão de produto**:
* _Experiência no domínio_ - trabalhar e entender o apoio de _software_ necessário em áreas específicas;
* _Experiência de produto_ - verificar formas mais simples e melhores de providenciar funcionalidades comparáveis e implementá-las num novo sistema, podendo tirar vantagem de desenvolvimentos tecnológicos recentes;
* _Experiência de cliente_ - entender problemas dos clientes como restrições que limitem a compra de novo _software_ e atributos críticos necessários;
* _Prototipagem_ - desenvolver uma melhor compreensão de uma ideia e do que pode estar envolvido no seu desenvolvimento, com a qual podem experimentar novas ideias e variações.

A **gestão de produtos de _software_** foca nos produtos de _software_ desenvolvidos e comercializados por cada empresa através de _gestores de produto_, responsáveis pelo produto e envolvidos no planeamento, desenvolvimento e _marketing_. Gestores de produto são a interface entre a organização, clientes e equipa de desenvolvimento de _software_, envolvidos em todas as etapas de vida de um produto, devem focar-se mais nos clientes e não no _software_ em desenvolvimento e também focar-se em:
* **Necessidades da empresa** - assegurar que o _software_ concretiza os objetivos;
* **Restrições tecnológicas** - assegurar que os _developers_ estão cientes de problemas tecnológicos importantes para os clientes;
* **Experiência de cliente** - estar em contacto regular com clientes para entender as suas necessidades, tipos e _backgrounds_ e forma de uso do _software_.

**Interações técnicas de gestores de produto**:
* _Gestão de visão de produto_ - ajudar no desenvolvimento da visão de produto, avaliando mudanças propostas;
* _Desenvolvimento do guião do produto_ - plano para o desenvolvimento, lançamento e _marketing_ do _software_, decidindo as alterações a fazer;
* _Desenvolvimento de cenários e histórias de cliente_ - refinar uma visão de produto e identificar características;
* _Criação e gestão de_ backlog _do produto_ - lista do que precisa de ser desenvolvido, priorizando determinadas características;
* _Teste de aceitação_ - verificar se um _software_ vai ao encontro dos objetivos apontados no guião do produto e se é eficiente e confiável;
* _Teste de cliente_ - lançar um produto e receber _feedback_ sobre as suas características, usabilidade e negócio;
* Design _de interface de utilizador_ - entender limitações dos clientes e atuar como utilizador suplente nas suas interações com a equipa de desenvolvimento para verificar se as características não são desnecessariamente complexas ou forçam os utilizadores a trabalhar de forma não natural.

**Prototipagem** é o processo de desenvolver uma versão do produto para testar ideias, provar o seu potencial de mercado, identificar componentes de _software_ fundamentais e testar tecnologia, que possa ser melhorada e desenvolvida de acordo com ideias de potenciais utilizadores. Deve ser uma versão funcional do _software_ que mostre as suas características principais, a partir do qual se desenha de raiz um produto confiável e seguro:
* **Demonstração de exequibilidade** - demonstrar as novas ideias num produto, verificando se são funcionais e melhores que as já existentes;
* **Demonstração de utilizador** - demonstrar ideias para características possíveis e como realizá-las, devendo já possuir alguns estudos de utilizadores e cenários de uso.

O **processo de _software_** é um conjunto de atividades requiridas para desenvolver um sistema de _software_. Há processos diferentes mas todos incluem:
* **Especificação** - definir o que o sistema deve fazer;
* **_Design_ e Implementação** - definir a organização e implementação do sistema;
* **Validação** - verificar que cumpre as necessidades do cliente;
* **Evolução** - alterar o sistema de acordo com as necessidades do cliente.

Um **modelo de processo de _software_** é uma representação abstrata do processo que apresenta uma descrição do processo de uma perspetiva particular. Os processos podem ser _guiados por plano_, em que todas as atividades são planeadas com antecedência e o progresso é medido com base nelas, ou _ágeis_, em que o planeamento é incremental e mais fácil de alterar de modo a refletir os requisitos alterados:
* **Cascata** - baseado em planos. As fases de especificação e desenvolvimento são separadas e distintas:
    * _Definição de requisitos_;
    * Design _de sistema e_ software;
    * _Implementação e teste de unidade_;
    * _Integração e teste de sistema_;
    * _Operação e manutenção_ (a partir da qual podem ser atingidas as fases anteriores);
        * É difícil acomodar mudanças após o início do processo (em princípio, uma fase deve ser concluída antes de se passar para a seguinte). Vantajoso em sistemas de requisitos estáveis;
        * ![](https://i.imgur.com/cRGY9sI.png)

* **Desenvolvimento incremental** - baseado em planos ou ágil. Especificação, desenvolvimento e validação são intercaladas:
    * _Descrição da_ outline;
    * _Especificação_;
    * _Desenvolvimento_;
    * _Validação_;
    * _Versões_;
        * O custo de acomodar mudanças de requisitos é reduzido; é mais simples obter _feedback_ do cliente sobre o trabalho feito; entrega e lançamento de _software_ útil mais rápido. O processo não é visível; a estrutura do sistema tende a degradar com a adição de novos incrementos;
        * ![](https://i.imgur.com/TAIAfVX.png)

* **Integração e configuração** - reutilização de _software_ em que os sistemas são integrados de componentes existentes ou sistemas de aplicação, que podem ser configurados para adaptar o seu comportamento e funcionalidades aos requisitos do utilizador (diapositivo 16):
    * _Especificação de requisitos_;
    * _Descoberta de_ software;
    * _Avaliação de_ software;
    * _Refinação de requisitos_;
    * _Configuração da aplicação do sistema_;
    * _Adaptação de componentes_;
    * _Desenvolvimento de novos componentes_;
    * _Integração do sistema_;
        * Redução de custos e riscos porque menos _software_ é construído de raiz; maior rapidez de entrega e lançamento do sistema. O sistema pode não responder aos requisitos do cliente; perda de controlo sobre a evolução dos elementos de sistema reutilizados.
        * ![](https://i.imgur.com/Wj1uKoR.png)


**Atividades do processo** são sequências de atividades técnicas, colaborativas e gerenciais com o principal objetivo de especificar, desenhar, implementar e testar um sistema de _software_:
* _Análise e elicitação de requisitos_;
* _Especificação de requisitos_ - que serviços são requisitos e restrições na operação e desenvolvimento do sistema;
* _Validação de requisitos_;
* _Descrições de sistema_;
* _Requisitos de utilizador e de sistema_;
* _Documentação de requisitos_.

**Especificação de _software_** é o processo de estabelecer quais serviços são requeridos e as restrições na operação e desenvolvimento do sistema: o que é esperado, detalhes e validade dos requisitos. **Implementação e _design_ de _software_** é o processo de converter as especificações de sistema num sistema executável: desenhar uma estrutura que concretiza a especificação e traduzi-la num sistema executável:
![](https://i.imgur.com/wetd2zS.png)

---

### Aula 03

A mudança é inevitável e leva a novos custos (reavaliação de requisitos, implementação de novas funcionalidades), que podem ser reduzidos se determinadas mudanças forem antecipadas e toleradas a baixo custo. Outras estratégias incluem prototipagem (versão básica do sistema para confirmar requisitos do utilizador, demonstrar conceitos e testar o _design_) e entrega incremental (incrementos entregues ao utilizador para comentário e experiência).

A prototipagem permite uma maior usabilidade do sistema, maior aproximação às necessidades do cliente, qualidade de _design_ e manutenção melhoradas, redução de esforço de desenvolvimento. O desenvolvimento de protótipos pode ser baseado em linguagens ou ferramentas rápidas e pode envolver perda de funcionalidades (sem verificação de erros ou recuperação de dados, com foco em áreas mal-entendidas do produto, na confiabilidade e segurança). Como não é documentado e certas funcionalidades não estão presentes no sistema, bem como tem degradação pelas diversas alterações, o protótipo deve ser descartado.

No **desenvolvimento e entrega incremental**, o desenvolvimento e entrega são feitos gradualmente de acordo com as funcionalidades desenvolvidas, com priorização de requisitos de cliente e requisitos de elevada prioridade incluídos nos incrementos iniciais. No **desenvolvimento incremental**, cada incremento é avaliado pelo utilizador antes de iniciar o desenvolvimento do seguinte (normalmente usado em métodos ágeis). Na **entrega incremental**, lança-se um incremento para consumidores finais, com uma avaliação mais realista:

![](https://i.imgur.com/wqLekTX.png)

A entrega incremental permite: funcionalidades do sistema disponíveis mais cedo, incrementos iniciais como protótipo para incrementos póstumos, menor risco de falha de projeto, serviços críticos com maior testagem. No entanto, pode ser difícil identificar necessidades comuns a todos os incrementos e a especificação é desenvolvida em conjunto com o _software_, o que pode não ser desejado pelas empresas.

**Melhoria de processos** implica compreender os processos existentes e alterá-los para aumentar a qualidade do produto e/ou reduzir custos e tempo de desenvolvimento. A abordagem de **maturidade do processo** foca na melhoria da gerência de processos e projetos e na introdução de boas práticas de engenharia de _software_; a abordagem **ágil** foca no desenvolvimento iterativo e a redução de despesas no processo de _software_, com rápida entrega de funcionalidades e responsividade aos requisitos em mudança.

**Medição de processo** permite a medição de um ou mais atributos do processo de _software_ ou produto (dados quantitativos de tempo, recursos e frequência de determinados eventos), a partir da qual se decide se as melhorias são eficazes. **Análise de processo** identifica falhas e fraquezas a serem melhoradas na **mudança de processo**.

**Desenvolvimento guiado por planos** é essencial para certos tipos de sistema, mas pode não responder às necessidades empresariais; métodos de **desenvolvimento ágil** pretendem reduzir o tempo de entrega para sistemas de _software_ funcionais. No desenvolvimento ágil a especificação, _design_ e implementação de programas são intercalados, com entregas frequentes de novas versões para avaliação; a documentação é mínima e há suporte extenso de ferramentas para apoiar o desenvolvimento.

![](https://i.imgur.com/aaoi1AI.png)

Os **métodos ágeis** focam-se no código em detrimento do _design_, baseados numa abordagem iterativa de desenvolvimento de _software_ de modo a entregar _software_ funcional rapidamente e evoluí-lo de acordo com os requisitos em mudança. Pretende reduzir despesas gerais no processo de _software_ (por exemplo, na documentação) e responder rapidamente às mudanças de requisitos sem trabalho excessivo. Baseiam-se em desenvolvimento e entrega incremental, com foco nas características de _software_ úteis ao cliente, dando prioridade às características mais importantes. Princípios:
* **Envolvimento do cliente** - manter o cliente próximo durante o processo de desenvolvimento para providenciar, priorizar e avaliar requisitos do sistema;
* **Entrega incremental** - desenvolvimento por partes que respondem a determinados requisitos;
* **Pessoas, não processos** - reconhecimento das capacidades da equipa de desenvolvimento;
* **Acolher mudanças** - esperar mudança dos requisitos do sistema e desenhá-lo para acomodar as mudanças;
* **Manter simplicidade** - foco na simplicidade no desenvolvimento.

Atividades de desenvolvimento incremental:
* **Escolha de características a incluir**;
* **Refinação de descrições de características** - adição de detalhes para que todos os membros da equipa compreendam cada característica e como implementar;
* **Implementação e teste** - verificar se o comportamento da característica é consistente com a sua descrição;
* **Integração de característica e teste** - integrar a característica ao sistema existente e verificar a sua compatibilidade com as outras características já existentes;
* **Entrega de sistema incrementado** - entrega do sistema ao cliente ou gestor de produto para verificação e comentário, com possível lançamento a público.

No **_extreme programming_** (XP), novas versões são criadas várias vezes por dia, com incrementos entregues a cada duas semanas e testes a cada nova construção (que só é aceite se todos os testes forem bem-sucedidos). Tem foco mais técnico e não é fácil de integrar em determinadas organizações. Práticas:
* **Planeamento incremental** - registo e avaliação de requisitos por tempo disponível e prioridade relativa (tarefas);
* **Pequenos lançamentos** - desenvolvimento do mínimo conjunto útil de funcionalidades com valor de negócio ao qual são adicionadas novas funcionalidades ao longo do tempo;
* **_Design_ simples**;
* **Desenvolvimento _test-first_** - são feitos testes a uma nova funcionalidade antes da sua implementação;
* **Refatoração** - melhoramento contínuo do código para beneficiar simplicidade, compreensão e manutenção. A refatoração deve ser feita ao adicionar uma característica, ao corrigir um _bug_ ou ao rever o código; o código deve ficar mais claro, a nova funcionalidade não deve ser criada durante o processo e todos os testes existentes devem ser bem sucedidos após a refatoração;
* **Programação em pares** - trabalho em pares dinâmicos, com verificação mútua de códigos e apoio constante, que permite reduzir os custos de saída de um dos membros da equipa;
* **Posse coletiva** - todos devem trabalhar em todas as áreas do sistema, para que a responsabilidade do código seja geral e todos possam fazer alterações;
* **Integração contínua** - integração de tarefa no sistema assim que é concluída;
* **Ritmo sustentável** - horas extra não são consideradas aceitáveis pois podem provocar redução da qualidade do código e da produtividade a médio prazo;
* **Cliente _on-site_** - o representante do cliente do sistema deve estar sempre disponível para a equipa de desenvolvimento e é responsável por trazer requisitos para implementação.

A Engenharia ágil de _software_ tem foco no rápido lançamento de produtos funcionais, minimizando custos de desenvolvimento e respondendo às especificações em mudança. O método **SCRUM** dá uma _framework_ para organização e planeamento ágeis de processos sem requerer práticas técnicas especiais, com maior foco na gestão de desenvolvimento iterativo do que nas práticas ágeis específicas, com três fases:
* Planeamento da _outline_ - estabelecimento dos objetos gerais do projeto e desenho da arquitetura do _software_;
* Ciclos de _sprints_ - desenvolvimento em ciclos de incrementos;
* Encerramento do projeto - conclusão da documentação e revisão dos novos conhecimentos adquiridos.

Terminologia do método SCRUM:
* **Produto** - _software_ a ser desenvolvido;
* **Dono do produto** - membro responsável por identificar características e atributos do produto, rever o trabalho feito e testar, bem como verificar que não há divergências no desenvolvimento do código;
* **_Backlog_ do produto** - lista _to-do_ de itens como _bugs_, características e melhorias de produto por completar;
* **Equipa de desenvolvimento** - cinco a oito pessoas responsáveis por desenvolver o produto;
* **_Sprint_** - curto período (duas a quatro semanas) em que um incremento é desenvolvido;
* **_Scrum_** - encontro diário da equipa de revisão do progresso e discussão de trabalho a fazer;
* **_Scrum Master_** - líder que garante o uso eficiente do Scrum;
* **Incremento potencialmente entregável do projeto** - resultado de um _sprint_ de qualidade alta o suficiente para ser lançada para uso geral;
* **Velocidade** - estimativa de quanto trabalho é possível fazer num único _sprint_.

---

### Aula 04

**_Personas_** são utilizadores imaginários com um retrato de caráter de um tipo de utilizador que talvez utilize o produto. Devem possuir _background_ e motivação para uso do produto, bem como as capacidades técnicas, de modo a perceber se uma característica será útil, percetível e utilizável para utilizadores comuns. Permitem: maior empatia com potenciais utilizadores do _software_, verificação de ideias para que não haja inclusão de características que não sejam realmente necessárias, evitar o desenho de um produto demasiado complexo ou irrelevante.

Um **cenário** é uma narrativa que descreve como um utilizador (ou um grupo) poderá usar o sistema, através de uma situação em que um utilizador está a utilizar as características do produto para fazer algo. É composto por nome, objetivo geral, passos necessários para atingir o objetivo, _personas_ envolvidas, problema não resolvível com o sistema atual, possívis formas de resolver o problema. Deve ser escrito da perspetiva do utilizador, geral e sem detalhes de implementação, e cada _persona_ deverá ter vários cenários.

Uma **estória** é uma narrativa mais refinada que estabelece algo que o utilizador quer de um sistema de _software_ com maior detalhe e estrutura. Enquanto _persona_, eu _quero/preciso_ de _ação_ (de modo a _razão_). Deve focar numa característica bem definida do sistema ou no aspeto de uma característica que pode ser implementada num único _sprint_.

Cenários são mais naturais, descrevendo ao certo o que o utilizador faz com o sistema, escritos numa linguagem mais informal e com maior contexto (informação sobre o que o utilizador está a tentar fazer e a sua forma normal de trabalhar).

No estado inicial de _design_ do produto, deve ser criada uma lista de características de forma a permitir aos utilizadores acesso e uso das funcionalidades do produto. **Características** são fragmentos de funcionalidade e devem ser:
* _Independentes_ - não devem depender nem ser afetadas entre si;
* _Coerentes_ - devem ligar-se a um único item de funcionalidade;
* _Relevantes_ - devem refletir a forma como são utilizadas normalmente pelos utilizadores.

O desenho de características deve refletir:
* Conhecimento do utilizador - o que os utilizadores querem e como poderão usar características do _software_;
* Conhecimento do produto - experimentar produtos para verificar características que possam ser replicadas para providenciar funcionalidades fundamentais;
* Conhecimento do domínio - entender o domínio para procurar formas inovadoras de atingir os objetivos dos utilizadores;
* Conhecimento da tecnologia - utilizar desenvolvimentos tecnológicos mais eficientes para desenvolver o _software_.

Nas características, é necessário encontrar um equilíbrio entre simplicidade e funcionalidade, familiaridade e novidade, e automação e controlo. **Falha nas características** ocorre quando novas características são adicionadas sem considerar se são úteis ou podem ser implementadas de forma diferente (relutância em negar novas características, tentativa de igualar características de produtos concorrentes, suporte para utilizadores com e sem experiência).

---

### Aula 05

**Engenharia de requisitos** é o processo de estabelecer os serviços que um cliente requer de um sistema e as restrições sob as quais opera e é desenvolvido. **Requisitos** são descrições dos serviços de sistema e restrições geradas durante o processo de engenharia de requisitos, podendo variar entre alto-nível de abstração e alto-nível de detalhe; devem ser **completos** (descrições de todas as funcionalidades necessárias) e **consistentes** (sem contradições entre si).

**Requisitos de utilizador** são frases em linguagem natural com diagramas dos serviços do sistema e restrições operacionais. **Requisitos de sistema** é um documento com descrições detalhadas das funções, serviços e restrições operacionais de um sistema, que define o que deve ser implementado.

Os **_stakeholders_ de sistema** são quaisquer pessoas ou organizações afetadas pelo sistema de alguma forma e, por tal, com interesse legítimo nele (utilizadores finais, gestor de sistema, proprietários do sistema, terceiros).

**Requisitos Funcionais** são declarações dos serviços que o sistema deve dar, como o sistema deve reagir a _inputs_ particulares e como o sistema se deve comportar em determinadas situações. Descrevem funcionalidades e dependem do tipo de _software_ e de sistema e dos utilizadores. Requisitos funcionais de utilizador são declarações alto-nível do que o sistema deve fazer; requisitos funcionais de sistema devem descrever os serviços do sistema em detalhe.

**Requisitos Não Funcionais** são restrições de serviços ou funções oferecidas num sistema (temporais, de desenvolvimento, padrões, ...). Definem propriedades e restrições do sistema, podendo ser mais críticos que os funcionais por afetar a arquitetura geral do sistema e não apenas componentes individuais (um único requisito não funcional pode gerar requisitos funcionais relacionados que definem serviços do sistema). **Requisitos de domínio** são restrições do sistema do domínio de operação.

![](https://i.imgur.com/sLLVShl.png)

Requisitos não funcionais são classificados por: requisitos de produto (especificação de como o produto se deve comportar), requisitos organizacionais (consequências de políticas e procedimentos da organização), requisitos externos (de fatores externos ao sistema, como legislações). As métricas são:
* _Velocidade_: transações por segundo, tempo de resposta utilizador-evento, tempo de atualização do ecrã;
* _Tamanho_;
* _Facilidade de uso_: tempo de treino, número de _frames_ de ajuda;
* _Confiabilidade_: tempo médio de erro, probabilidade de indisponibilidade, rácio de ocorrência de falhas, disponibilidade;
* _Robustez_: tempo de reinício após falha, percentagem de eventos a causar falhas, probabilidade de corrupção de dados;
* _Portabilidade_: percentagem de declarações dependentes do alvo, número de sistemas alvo.

---

### Aula 06

O processo de **engenharia de requisitos** depende do domínio da aplicação, das pessoas envolvidas e da organização que desenvolve os requisitos, sendo uma atividade iterativa em que os seguintes processos estão intercalados:
* _Elicitação de requisitos_ - trabalho conjunto entre técnicos e utilizadores (_stakeholders_) sobre domínio da aplicação, serviços e restrições operacionais do sistema. Problemas: os _stakeholders_ não sabem o que querem e expressam-se de forma única, podendo ter requisitos em conflito entre si, os requisitos podem ser influenciados por fatores organizacionais e políticos e podem alterar-se durante o processo de análise. Inclui:
    * Descoberta de requisitos - recolha de informação sobre os sistemas desejado e existentes, a partir da qual se recolhem requisitos;
    * Classificação e organização de requisitos - agrupamento em grupos coerentes de requisitos relacionados;
    * Priorização e negociação de requisitos - resolução de conflitos e definição de prioridades;
    * Especificação de requisitos - documentação de requisitos, de forma a serem compreendidos por utilizadores sem _background_ técnico, em linguagem natural, linguagem natural estruturada (função, _input_, _output_, informação relevante, ação, pré e pós-condições (se apropriado), efeitos secundários (se aplicável)), linguagem de descrição de _design_, notações gráficas (caso de uso UML), especificações matemáticas;
* _Análise de requisitos_;
* _Validação de requisitos_ - demonstrar que os requisitos definem o sistema desejado pelo cliente, por revisões (verificabilidade, compreensibilidade, rastreabilidade, adaptabilidade), prototipagem ou geração de casos de teste:
    * Validade - funções suportam bem as necessidades do cliente;
    * Consistência - inexistência de conflitos de requisitos;
    * Completude - todas as funções necessárias estão incluídas;
    * Realismo - implementação de requisitos dentro do orçamento e tecnologia disponíveis;
    * Verificabilidade - possibilidade de confirmar os requisitos;
* _Gestão de requisitos_ - gestão de requisitos em mudança, mantendo ligações entre requisitos dependentes para avaliar o impacto das mudanças. Cada requisito deve ser identificado de modo único para se poder fazer referências cruzadas. A decisão segue os seguintes passos:
    * Análise do problema e especificação da mudança: verificar a validade da alteração para prosseguir ou desistir;
    * Análise e custo da mudança: impacto da alteração, de acordo com a informação de rastreio e conhecimento geral dos requisitos do sistema;
    * Implementação da mudança: alteração do documento de requisitos e _design_ e implementação do sistema (se necessário).

Os requisitos devem declarar o que o sistema deve fazer e o _design_ deve descrever como o sistema deve fazer.

**Casos de uso** identificam os atores numa interação e descrevem a ação em si, num modelo gráfico de alto nível suplementado com descrições tabuladas detalhadas. O conjunto de casos de uso deve descrever todas as interações possíveis com o sistema, numa sequência de eventos.

O **documento de requisitos de _software_** é a declaração oficial do que é requerido aos desenvolvedores do sistema, devendo incluir uma definição dos requisitos de utilizador e de sistema. É utilizado por _clientes_ (especificação de requisitos), _gestores_ (orçamento e planeamento do sistema), _engenheiros de sistema_ (compreensão do sistema a desenvolver), _engenheiros de teste de sistema_ (desenvolvimento de testes para o sistema), _engenheiros de manutenção do sistema_ (entendimento do sistema e relações entre as suas partes). Segue a seguinte estrutura:
* _Prefácio_: definição do público alvo do documento e histórico de versões, com resumos das alterações feitas em cada uma;
* _Introdução_: descrição da necessidade do sistema, funções, funcionamento com outros sistemas e integração na organização;
* _Glossário_: definição dos termos técnicos;
* _Definição de requisitos de utilizador_: descrição dos serviços prestados ao utilizador (requisitos funcionais e não funcionais);
* _Arquitetura do sistema_: prévia alto-nível da arquitetura do sistema, com distribuição das funções ao longo do sistema;
* _Especificação de requisitos do sistema_: descrição mais detalhada de requisitos funcionais e não funcionais, bem como interfaces para outros sistemas;
* _Modelos de sistema_: modelos gráficos do sistema que mostram a relação entre ele, os seus componentes e o ambiente;
* _Evolução do sistema_: descrição das bases do sistema, com possíveis alterações antecipadas;
* _Apêndices_: informação detalhada e específica sobre a aplicação em desenvolvimento;
* _Índice_.

---
---

## Aulas Práticas

### Aula 01

**Questão 01 - Explique por que _software_ profissional não são apenas os programas desenvolvidos para um cliente.**

_Resposta:_ _Software_ profissional não envolve apenas a escrita de código, mas todo o processo envolvente (especificação e definição de requisitos, _design_ de sistema, implementação, testes, manutenção e documentação do sistema, observação do ambiente de funcionamento do sistema, prototipagem). É também necessário escolher a metodologia mais adequada para o SDLC (_Software Development Life Circle_: cascata, incrementação, integração).

**Questão 02 - Qual é a mais importante diferença entre desenvolvimento de produtos de _software_ genérico e desenvolvimento de _software_ customizado? O que pode isto explicar na prática para utilizadores de produtos de _software_ genérico? Apresente exemplos de _software_ genérico e customizado.**

_Resposta:_ _Software_ genérico são sistemas independentes comercializados e vendidos para qualquer cliente que deseje comprá-los: programas de gráficos, ferramentas de gestão de projeto. _Software_ customizado são sistemas comissionados por um cliente específico para responder às suas necessidades: sistemas de controlo embutidos, sistemas de controlo de tráfego aéreo, sistemas de monitorização de tráfego. O _software_ genérico pode adaptar-se a diferentes necessidades de diversos utilizadores; o _software_ comissionado tem funções rígidas e com maiores custos de manutenção.

**Questão 03 - Quais são os mais importantes atributos que o _software_ profissional deve ter? Sugira atributos adicionais que possam ser por vezes significantes.**

_Resposta:_ Manutenção (escrita de _software_ de modo a evoluir para ir ao encontro das necessidades em mudança dos clientes); confiabilidade e segurança (_software_ que não cause dano físico ou económico no evento de falha do sistema); eficiência (não desperdício de recursos do sistema (memória, processador), com maximização de responsividade, tempo de processamento, uso de memória); aceitabilidade (percetível, usável e compatível com outros sistemas). Outros atributos podem ser: rápido desenvolvimento e lançamento; escalabilidade; disponibilidade.

**Questão 04 - Explique porque há ideias fundamentais de engenharia de _software_ que se aplicam a todos os tipos de sistema de _software_.**

_Resposta:_ Os princípios fundamentais definem que: sistemas devem ser desenvolvidos com um processo gerido e compreendido de acordo com o tipo de _software_; confiabilidade e _performance_ são importantes para qualquer tipo de sistema; entender e gerir as especificações e requisitos do _software_ são importantes; quando possível, deve ser reutilizado _software_. Isto permite uma maior abstração a partir da qual os programas podem ser desenvolvidos e facilita a manutenção e a melhoria de _software_ a longo prazo.

**Questão 05 - Para ajudar no contraterrorismo, muitos países estão a planear ou desenvolveram sistemas computacionais que rastreiam grandes números de cidadãos e as suas ações. Claramente, isto acarreta implicações de privacidade. Discuta as éticas de trabalhar no desenvolvimento deste tipo de sistema.**

_Resposta:_ A monitorização de indivíduos sem razão específica representa uma violação da privacidade individual. Embora seja vantajoso o desenvolvimento de sistemas de monitorização, esta deveria ser realizada de modo a buscar o bem comum (e não o bem de indivíduos na busca de bodes expiatórios). No entanto, para a monitorização de indivíduos potencialmente perigosos, é necessário monitorizar uma larga percentagem de população para fazer uma espécie de "triagem", pelo que os sistemas deveriam conseguir descortinar sinais de perigo sem invadir demasiado e desnecessariamente a sua privacidade.

**Questão 06 - No contexto de engenharia de _software_, comente a imagem seguinte.**

_Resposta:_ A primeira imagem representa as necessidades do utilizador, que pode não saber ao certo aquilo que quer. A segunda imagem descreve como o líder de projeto, que necessita de compreender o problema na sua totalidade, entendeu as necessidades do utilizador. A terceira imagem descreve como o analista, que acede apenas a pequenas partes do projeto e não tem uma perspetiva mais abrangente, desenhou o projeto. A quarta imagem mostra como o programador, que acede apenas a pequenas partes do projeto e não tem uma perspetiva mais abrangente (e que pode ter sido deturpada pela explicação do cliente e as interpretações da equipa), escreveu o código do projeto. https://thecodest.co/blog/the-ugly-truth-about-software-development-process/

**Questão 07 - Explique por que a mudança é inevitável em sistemas complexos e dê exemplos (para além de prototipagem e entrega incremental) de atividades de processos de _software_ que ajudem a prever mudanças e fazer o _software_ em desenvolvimento mais resiliente à mudança.**

_Resposta:_ Sistemas complexos englobam inúmeras tecnologias e são propensos a erros e _bugs_ que devem ser eliminados através de alterações no código do produto. Para além da prototipagem e entrega incremental, é possível prever mudanças e tornar o _software_ mais resiliente através de rastreio de mudanças, refatorização de código, histórico de mudanças de requisitos (para entender motivos de alterações anteriores).

**Questão 08 - Historicamente, a introdução da tecnologia causou mudanças profundas no mercado de trabalho e, temporariamente pelo menos, tirou pessoas de trabalhos. Discuta se a introdução de automação extensiva de processo é provável que tenha as mesmas consequências para engenheiros de _software_. Se não, explique por que não. Se pensa que irá reduzir oportunidades de trabalho, é ético para os engenheiros afetados resistirem passiva ou ativamente à introdução da nova tecnologia?**

_Resposta:_ Não creio que novas introduções tecnológicas venham a afetar os engenheiros de _software_, uma vez que a omnipresença da tecnologia iria provocar uma falta de humanidade e humanismo. A maior presença de tecnologia poderá aumentar a possibilidade de criatividade dos engenheiros, que continuarão a ser necessários para supervisionar sistemas críticos. Além disso, há também a possibilidade de Engenharia de _Software_ evoluir para uma nova engenharia ou área de desenvolvimento, o que apenas requer capacidade de adaptação dos engenheiros existentes.

---

### Aula 02

**Questão 01 - Explique como os princípios base dos métodos ágeis levam a um desenvolvimento e lançamento de _software_ acelerados.**

_Resposta:_ Os princípios dos métodos ágeis designam envolvimento do cliente (o cliente fica próximo para providenciar, priorizar e avaliar requisitos do sistema), entrega incremental (desenvolvimento por partes que respondem a determinados requisitos de acordo com a sua prioridade), pessoas em detrimento de processos (reconhecimento das capacidades da equipa), acolhimento de mudanças (as mudanças são esperadas e preparadas com antecedência) e manutenção da simplicidade. Tal permite que o sistema seja desenvolvido como uma série de versões que vão sendo desenvolvidas e entregues, com apoio extensivo para desenvolvimento com mínimo foco na documentação.

**Questão 02 - _Extreme Programming_ expressa requisitos de utilizadores como histórias, com cada história escrita num cartão. Discuta as vantagens e desvantagens desta abordagem para a descrição de requisitos.**

_Resposta:_ As histórias ou cenários de utilizador são expressas como cartões, de onde depois são quebradas para tarefas de implementação pela equipa de desenvolvimento onde se baseiam cronologias e estimativas de custo. Estas tarefas são incluídas na versão seguinte de lançamento de acordo com a sua prioridade e as estimativas cronológicas. Tal permite desenvolvimento incremental (com facilidade na mudança de requisitos), consistência (cada versão é sempre testado) e fácil manutenção (refatoração em tempo de desenvolvimento). No entanto, o cliente tem de participar no projeto (com maior custo e dispensão de tempo), exige mais trabalho e custos adicionais.

**Questão 03 - Sugira razões pelas quais a taxa de produtividade de programadores a trabalhar em pares pode ser mais do que metade de dois programadores a trabalhar individualmente.**

_Resposta:_ A programação em pares permite a posse conjunta do código e partilha de conhecimento, com revisão e refatoração constante de código, reduzindo os riscos gerais de mudança de um dos membros da equipa. Há também maior colaboração e espírito de entreajuda, com complementação de raciocínio e maior facilidade de _brainstorming_.

**Questão 04 - Determine histórias de utilizador e cartões de tarefa relacionados com atividades centrais de ATM (_automate teller machine_): retirar dinheiro, verificar saldos, transferir fundos...**

_Resposta:_ Enquanto administrador, eu quero ter acesso às transações dos utilizadores para efeitos estatísticos. Enquanto administrador, eu preciso de ter acesso à quantidade de dinheiro na máquina para saber se é necessário reabastecer. Enquanto utilizador, eu quero poder levantar dinheiro da máquina. Enquanto utilizador, eu quero poder fazer transações entre contas.

**Questão 05 - Determine histórias de utilizador e cartões de tarefa relacionados com uma consulta clínica.**

_Resposta:_ Enquanto administrador, eu quero ter acesso aos balanços financeiros da clínica. Enquanto administrador, eu quero poder pagar os salários aos trabalhadores. Enquanto médico, eu quero ter acesso ao historial clínico do paciente. Enquanto médico, eu quero poder receitar medicação. Enquanto assistente, eu quero ter acesso ao _stock_ de material. Enquanto assistente, eu quero ter acesso aos horários dos médicos para poder agendar consultas de pacientes. Enquanto paciente, eu quero marcar consultas. Enquanto paciente, eu quero fazer e levantar exames.

**Questão 06 - Determine histórias de utilizador e cartões de tarefa relacionados com o sistema `iLearn`.**

_Resposta:_ Enquanto diretor, eu quero gerir os horários dos professores. Enquanto diretor, eu quero ter acesso às atividades extracurriculares propostas. Enquanto professor, eu quero criar páginas personalizadas para a minha cadeira. Enquanto professor, eu preciso de poder interagir com os alunos mais informalmente. Enquanto aluno, eu quero ter uma página onde possa partilhar ideias com colegas. Enquanto aluno, eu preciso de uma página onde tenha toda a calendarização importante.

---

### Aula 03

**Questão 01 - Explique por que o conhecimento do domínio é importante aquando da identificação e desenho de características do produto.**

_Resposta:_ Quanto maior for o conhecimento da área em que se está a trabalhar (finanças, organização de eventos), mais facilmente se podem detetar as necessidades para novos sistemas de acordo com a análise aos sistemas já existentes. Tal permite a inovação e o desenvolvimento de novas formas mais ágeis e simples de executar as funções desejadas num sistema.

**Questão 02 - Explique por que é útil desenvolver um número de _personas_ que representem tipos de utilizadores do sistema antes de mover para a escrita dos cenários de como o sistema será utilizado.**

_Resposta:_ Personas são utilizadores imaginários com um retrato de caráter de um tipo de utilizador que talvez utilize o produto. Personas de diferentes tipos de utilizador ajudam a imaginar o que cada um poderá querer fazer com o _software_ e como este será utilizado, ajudando a enviesar possíveis dificuldades em compreender e utilizar características do produto. As personas permitem que haja uma empatia com os utilizadores do _software_, um colocar-se no lugar do utilizador, que ajuda a perceber melhor comportamentos e reações para com o sistema, assegurando-se de que as características a incluir são as necessárias e ajudando a desenhar cenários mais realistas e simples do funcionamento do produto.

**Questão 03 - Utilizando o _template input_/ação/_output_, descreva duas características de _software_ usado em geral, como o editor de texto.**

_Resposta:_ Input: caratere. Ação: adicionar o caratere à cadeia existente. Output: texto. (?)

**Questão 04 - Sugira como a equipa de desenvolvimento pode evitar as falhas nas características quando confrontados com muitas sugestões diferentes de novas características a serem introduzidas num novo produto.**

_Resposta:_ Falha nas características ocorre quando novas características são adicionadas sem considerar se são úteis ou podem ser implementadas de forma diferente. Demasiadas características aumentam a complexidade de um sistema, tornando-o mais difícil de usar e entender. Ao ter demasiadas sugestões diferentes, pode ocorrer que as características se tornem redundantes ou contraditórias, que sejam formas diferentes de fazer ações que já são executadas por características existentes, que sejam apenas úteis a uma pequena gama de utilizadores e que não possam ser generalizadas.

**Questão 05 - Explique a figura abaixo, relacionada com o desenho de características.**

![](https://i.imgur.com/Bvb4Ul2.png)

_Resposta:_ O desenho de características é feito com conhecimento do utilizador, do produto, do domínio e da tecnologia. O conhecimento do utilizador permite utilizar cenários e estórias para mostrar à equipa o que os utilizadores desejam e como poderão utilizar os recursos do _software_. O conhecimento do produto permite utilizar experiências prévias ou pesquisas com produtos existentes como parte do processo de desenvolvimento, podendo replicar os seus recursos para funcionalidades fundamentais que são sempre necessárias. O conhecimento do domínio permite pensar em novas maneiras inovadoras de ajudar os utilizadores a fazer o que desejam com o novo sistema. O conhecimento da tecnologia permite tirar partido dos novos desenvolvimentos tecnológicos para a otimização do sistema e aumentar a concorrência com outros produtos já existentes.