# Engenharia de _Software_

##### Atualizado em 01-10-2021
###### A partir de: sebenta

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
* **Cascata** - baseado em planos (diapositivo 8). As fases de especificação e desenvolvimento são separadas e distintas:
    * _Definição de requisitos_;
    * Design _de sistema e_ software;
    * _Implementação e teste de unidade_;
    * _Integração e teste de sistema_;
    * _Operação e manutenção_ (a partir da qual podem ser atingidas as fases anteriores);
        * É difícil acomodar mudanças após o início do processo (em princípio, uma fase deve ser concluída antes de se passar para a seguinte). Vantajoso em sistemas de requisitos estáveis;
* **Desenvolvimento incremental** - baseado em planos ou ágil (diapositivo 11). Especificação, desenvolvimento e validação são intercaladas:
    * _Descrição da_ outline;
    * _Especificação_;
    * _Desenvolvimento_;
    * _Validação_;
    * _Versões_;
        * O custo de acomodar mudanças de requisitos é reduzido; é mais simples obter _feedback_ do cliente sobre o trabalho feito; entrega e lançamento de _software_ útil mais rápido. O processo não é visível; a estrutura do sistema tende a degradar com a adição de novos incrementos;
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

**Atividades do processo** são sequências de atividades técnicas, colaborativas e gerenciais com o principal objetivo de especificar, desenhar, implementar e testar um sistema de _software_:
* _Análise e elicitação de requisitos_;
* _Especificação de requisitos_ - que serviços são requisitos e restrições na operação e desenvolvimento do sistema;
* _Validação de requisitos_;
* _Descrições de sistema_;
* _Requisitos de utilizador e de sistema_;
* _Documentação de requisitos_.

**Especificação de _software_** é o processo de estabelecer quais serviços são requeridos e as restrições na operação e desenvolvimento do sistema: o que é esperado, detalhes e validade dos requisitos. **Implementação e _design_ de _software_** é o processo de converter as especificações de sistema num sistema executável: desenhar uma estrutura que concretiza a especificação e traduzi-la num sistema executável (diapositivo 24).

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