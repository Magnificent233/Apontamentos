# Inteligência Artificial

##### Atualizado em 20-09-2021
###### A partir de: sebenta

## Aulas Teóricas

### Aula 1

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
* **4 -** Sistemas que pensam racionalmente.

Um **agente** é algo que tem perceção do ambiente através de sensores e que pode agir sobre esse ambiente através de atuadores. Um **agente racional** é o que toma a decisão correta, ou seja, o seu desempenho melhora na tarefa que realiza. Uma **medida de desempenho** contém o critério de sucesso relativo ao comportamento de um agente, devendo ser desenhada de acordo com o que se pretende que aconteça no ambiente ao invés do que se pensa ser o melhor comportamento do agente.

Num dado instante, uma **decisão racional** depende de: a medida de desempenho; o conhecimento que o agente tem do ambiente; as ações que o agente pode executar; a sequência de observações realizadas pelos sensores do agente até ao instante atual. Para cada sequência de observações possível, um **agente racional** deve escolher a ação que se espera que maximize a sua medida de desempenho, dadas as observações realizadas e o conhecimento adquirido pelo agente.

Os ambientes de tarefa devem ter: a medida de desempenho, o ambiente da tarefa, os atuadores e os sensores do agente. Quanto mais restrito for o ambiente de atuação, mais fácil é o problema. Um ambiente é:
* **Totalmente observável** (se os sensores do agente tiverem acesso a todo o estado do ambiente em cada instante) ou **parcialmente observável** (existência de ruído, mau funcionamento ou inexistência de sensores);
* **Determinístico** (se o estado do ambiente no instante seguinte for determinado pelo estado atual e pela ação do agente) ou **estocástico** (caso contrário);
* **Episódico** (se as ações num episódio não influenciam as de outro) ou **sequencial** (se todas as ações influenciam o estado);
* **Dinâmico** (se o ambiente mudar enquanto há decisão) ou **estático** (caso contrário);
* **Discreto** (se o problema tem estados discretos) ou **contínuo** (caso contrário);
* **Agente único** ou **multi-agente**.

\\ diapositivo 35 //