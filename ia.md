# Inteligência Artificial

##### Atualizado em 27-09-2021
###### A partir de: sebenta

## Aulas Teóricas

### Aula 01

A definição de Inteligência Artificial (IA) pode ser integrada em quatro grupos:
* **1 -** _Sistemas que agem como os humanos_:
    * Teste de Turing (1950) - uma máquina passa no teste se, após responder a questões colocadas por escrito, não ser possível definir se as respostas foram dados por um humano ou não. A máquina necessita de:
        * **Processamento da linguagem natural** (capacidade de comunicar na linguagem humana);
        * **Representação do conhecimento** (armazenamento da informação);
        * **Raciocínio automático** (uso de informação armazenada para responder a perguntas e atingir conclusões);
        * **Aprendizagem automática** (adaptação a novas circunstâncias, deteção e extrapolação de padrões);
    * Teste de Turing total - usa também sinal de vídeo, permitindo ao interrogador testar as capacidades percetuais do candidato e a passagem de objetos. A máquina necessita, além do supracitado, de:
        * **Visão computacional** - reconhecimento de objetos;
        * **Robótica** - manipulação de objetos e deslocação;
    * No entanto, não é preciso agir como um humano para ser inteligente - como é caso da aerodinâmica;
* **2 -** _Sistemas que pensam como os humanos_:
    * A perceção de como os humanos pensam é feita por **introspeção** (tentativa de análise dos próprios pensamentos) ou **experiências psicológicas** (ciências cognitivas). No entanto, a interligação para a IA enfrenta dois grandes obstáculos:
        * Difícil passagem de conhecimento informal para notação lógica;
        * Diferença entre capacidade de resolver problemas na teoria e na prática;
* **3 -** _Sistemas que agem racionalmente_:
    * Um **agente** é algo que age: de forma autónoma, com captação de dados do ambiente (sensores), durante longos períodos de tempo, com adaptação a mudanças e capaz de atingir determinados objetivos. Um **agente racional** age de forma a alcançar o melhor resultado ou, no caso de existir incerteza, o melhor resultado esperado;
    * Este estudo é mais vantajoso porque: é mais geral que a abordagem do pensamento racional e é mais adaptado ao desenvolvimento científico (usa uma definição de racionalidade clara e geral);
* **4 -** _Sistemas que pensam racionalmente_.

Um **agente** é algo que tem perceção do ambiente através de sensores e que pode agir sobre esse ambiente através de atuadores. Um **agente racional** é o que toma a decisão correta, ou seja, o seu desempenho melhora na tarefa que realiza. Uma **medida de desempenho** contém o critério de sucesso relativo ao comportamento de um agente, devendo ser desenhada de acordo com o que se pretende que aconteça no ambiente ao invés do que se pensa ser o melhor comportamento do agente.

Num dado instante, uma **decisão racional** depende de: a medida de desempenho; o conhecimento que o agente tem do ambiente; as ações que o agente pode executar; a sequência de observações realizadas pelos sensores do agente até ao instante atual. Para cada sequência de observações possível, um **agente racional** deve escolher a ação que se espera que maximize a sua medida de desempenho, dadas as observações realizadas e o conhecimento adquirido pelo agente.

Os ambientes de tarefa devem ter: a medida de desempenho, o ambiente da tarefa, os atuadores e os sensores do agente. Quanto mais restrito for o ambiente de atuação, mais fácil é o problema. Um ambiente é:
* **Totalmente observável** (se os sensores do agente tiverem acesso a todo o estado do ambiente em cada instante) ou **parcialmente observável** (existência de ruído, mau funcionamento ou inexistência de sensores);
* **Determinístico** (se o estado do ambiente no instante seguinte for determinado pelo estado atual e pela ação do agente) ou **estocástico** (caso contrário);
* **Episódico** (se as ações num episódio não influenciam as de outro) ou **sequencial** (se todas as ações influenciam o estado);
* **Dinâmico** (se o ambiente mudar enquanto há decisão) ou **estático** (caso contrário);
* **Discreto** (se o problema tem estados discretos) ou **contínuo** (caso contrário);
* **Agente único** ou **multi-agente**.

| Problema | Totalmente Observável | Determinístico | Episódico | Estático | Discreto | Agente Único |
| --- | --- | --- | --- | --- | --- | --- |
| Palavras Cruzadas | Sim | Sim | Não | Sim | Sim | Sim |
| Robô de Peças | Não | Não | Sim | Não | Não | Sim |
| Táxi Automático | Não | Não | Não | Não | Não | Não |
| Xadrez | Sim | Sim | Não | Sim | Sim | Não |
| Monopólio | Sim | Não | Não | Sim | Sim | Não |

Um **agente reflexivo** escolhe a ação a executar com base na observação atual, sem contar com as observações feitas anteriormente (segue uma regra _condição-ação_). Um **agente reflexivo baseado em modelo** deve manter um estado interno onde armazene informação dependente das observações passadas, que é atualizada com base no funcionamento do mundo independentemente das observações e na influência das ações do agente no mundo - **modelo**.

![](https://i.imgur.com/cX2s8It.png)

![](https://i.imgur.com/8wRNB2m.png)


Um **agente com objetivo** combina a informação acerca das suas possíveis ações com o seu objetivo para decidir a ação a tomar, precisando por vezes de executar uma longa sequência de ações para o atingir.

![](https://i.imgur.com/kL9Czpe.png)


Um **agente com utilidade** escolhe o **estado** (representação de um instante no mundo em que o agente se encontra) mais favorável. Uma **função de utilidade** faz corresponder a um estado um número real que indica o respetivo grau de utilidade, utilizado quando existem objetivos contraditórios para encontrar um equilíbrio e quando existem objetivos múltiplos e não se sabe se é possível atingi-los.

![](https://i.imgur.com/WP27SLi.png)


Um **agente que aprende** aprende sozinho as melhores ações a tomar em cada situação, permitindo a sua atuação em ambientes inicialmente desconhecidos onde se torna gradualmente mais competente. Tem **elementos de aprendizagem** (melhoram comportamentos do agente), **elementos de desempenho** (selecionam as ações a tomar), **críticos** (indicam como o agente se está a comportar e como deve ser alterado o elemento de desempenho) e **geradores de problemas** (sugerem ações e permitem que o agente se comporte de forma sub-ótima de forma a poder, a médio prazo, atingir melhores resultados).

![](https://i.imgur.com/xVHJtG0.png)


---

### Aula 02

Os agentes devem tentar maximizar a sua medida de desempenho, examinando diferentes possíveis sequências de ações que levam a estados de valor conhecido para decidir a melhor sequência: **pesquisa**. Para tal, é necessário:
1. _Definir o problema_:
    * Um problema pode ser **real** ou **artificial** e é definido por:
        * Estado inicial;
        * Descrição das ações possíveis (função sucessor (`suc(x)`), que recebe estados e devolve pares do tipo `(ação, estado)`, que mostram o estado atingido partindo do estado inicial seguindo determinada ação);
        * Teste de objetivo (avaliação de um determinado estado para confirmar se é o estado objetivo);
        * Função de custo do caminho (atribuição de valores numéricos a cada caminho);
    * Através do estado inicial e a função sucessor define-se implicitamente o **espaço de estados** do problema (conjunto de todos os estados que se podem alcançar a partir do estado inicial, usando qualquer sequência de ações), que forma um **grafo** em que os nodos são estados e as arestas são ações. Um **caminho** é uma sequência de estados ligados por uma sequência de ações, e o **custo** é o custo de ir entre dois estados com uma determinada ação;
    * A **solução** de um problema é um caminho do estado inicial ao estado objetivo, cuja qualidade é definida pelo custo do caminho, e diz-se **ótima** se for a que tem menor custo;
2. _Formular o objetivo_;
3. _Pesquisar a solução_:
    * Uma **árvore de pesquisa** é uma estrutura de dados em que o estado inicial é a raiz, à qual se acrescentam os nodos correspondentes aos estados obtidos a partir de cada ação possível (**expansão**), cujo caminho ótimo é calculado através de uma **estratégia de pesquisa**:
        * **Não informada** - quando a única informação disponível é a presente na definição do problema:
            * _Pesquisa primeiro em largura_ (**PPL**) - expansão de todos os nodos num dado nível antes de prosseguir a expansão aos nodos do nível seguinte. É completa se o fator de ramificação é finito e ótima quando o custo do caminho é uma função não decrescente da profundidade do nodo;
            * _Pesquisa primeiro em profundidade_ (**PPP**) - expansão de cada nodo até que se atinja a maior profundidade;
            * _Pesquisa primeiro em profundidade com profundidade limitada_ (**PPP-PL**) - a pesquisa só atinge uma dada profundidade pré-definida. É útil para árvores de pesquisa não equilibradas, mas corre-se o risco de explorar profundidades muito grandes;
            * _Pesquisa primeiro em profundidade com profundidade iterativa_ (**PPP-PI**) - a profundidade da pesquisa é variável com graduação. Tem requisitos de memória reduzidos, é completa quando o fator de ramificação é finito e ótima quando o custo do caminho é uma função não decrescente da profundidade do nodo;
            * _Pesquisa bidirecional_ (**PB**) - são feitas duas pesquisas, uma com início no estado inicial e outra com início no estado objetivo através uma função predecessor (`pred(x)`) que devolve o estado anterior ao estado x. É completa se o fator de ramificação for finito e ótimo se as ções tiverem o mesmo custo (ambas as pesquisas devem ser em largura);
        * **Informada** - utilizam conhecimento específico do problema para permitir a descoberta de solução de forma mais eficiente, definindo se um estado é melhor que outro:
            * _Pesquisa melhor primeiro_ (**PMP**) - o nodo a expandir é escolhido em função do valor dado por uma **função de avaliação** que dá uma estimativa do custo associado, expandindo-se o de menor custo. Há vários algoritmos dependendo da **função heurística** (componente da função de avaliação que estima o custo do caminho mais barato do nodo inicial até ao objetivo);
            * _Pesquisa melhor primeiro gulosa_ (**PMPG**) - o nodo a expandir é o que estiver mais próximo do nodo objetivo. Não é completa nem ótima;
            * _Pesquisa A estrela_ (**PA***) - a função de avaliação usa também o custo do caminho para chegar ao nodo objetivo vindo do ponto inicial. É ótima se a função heurística for **admissível** (nunca sobrestima o custo de atingir o objetivo);
    * A **qualidade dos métodos de pesquisa** podem ser medidos por:
        * _Completude_: se o algoritmo for sempre capaz de encontrar a solução;
        * _Otimização_: se o algoritmo for sempre capaz de encontrar a solução ótima;
        * _Complexidade espacial_: espaço necessário em memória RAM para a execução do algoritmo;
        * _Complexidade temporal_: tempo necessário para a execução do algoritmo;
4. _Executar a solução_.