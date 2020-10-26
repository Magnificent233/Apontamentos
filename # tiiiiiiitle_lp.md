# Laboratórios de Programação

## Aula Prática 1

**Questão 01: O que é que está errado nas seguintes expressões/palavras?**

`Tex Live, LaTeX e MikTex`

_Resposta:_ Estas palavras requerem uma estilização muito própria, com letras acima e abaixo da linha de texto, que só se consegue com muito jeitinho (e com comandos $\LaTeX$).

---

**Questão 02: Quais as duas partes que constituem a estrutura geral de um documento $\LaTeX$ (escolha duas respostas)?**

_Resposta:_ Preâmbulo. Conteúdo.

---

**Questão 03: As palavras % `Preâmbulo` e % `Conteúdo` aparecem no documento após compilação?**

_Resposta:_ Claro que não aparecem, porque são comentários.

---

**Questão 04: O que acontece se colocar texto (e.g., a palavra `teste`) após a instrução `\end{document}`?**

_Resposta:_ Não dá erro, e a palavra `teste` não aparece no documento (é ignorada).

---

**Questão 05: É verdade que foi gerada uma página rosto só com o título, o autor e a data?**

_Resposta:_ Mesmo! Ficou lindo!

---

**Questão 06: Qual é a diferença entre o comando `\label` e `ref`?**

_Resposta:_ O comando `\label` permite atribuir uma etiqueta a um elemento anterior, enquanto que o comando `\ref` permite fazer referência ao elemento.

---

**Questão 07: Qual é o comando que permite mostrar as páginas de uma referência?**

_Resposta:_ `\pageref`.

---

**Questão 08: Qual é a finalidade do comando `\eg` e do ambiente `\ac`?**

_Resposta:_ O comando `\eg` substitui comando pela expressão definida no início do programa e pelos valores que lhe são atribuídos. O comando `\ac` cria um ambiente predefinido que pode envolver diversos comandos.

---

**Questão 09: Apareceu tudo direitinho?**

_Resposta:_ Sim, tudo bem!

---

**Questão 10: Apareceu tudo direitinho?**

_Resposta:_ Já está impecável.

<br/><br/>

## Aula Prática 2

**Questão 01: Tendo   em   conta   os   comandos   enunciados   no   início   desta   secção,    acha   que é    possível    escrever    a    palavra `teste` em itálico e, simultaneamente, a negrito?**

_Resposta:_ Sim, encadeando os   comandos da seguinte forma: `\textit{\textbf{teste}}`.
Sim, encadeando os comandos  da  seguinte forma: `\textbf{\textit{teste}}`.

---

**Questão 02: O que faz o comando `\emph{palavra}`?**

_Resposta:_ Tem efeito semelhante  a `\textit{itálico}` em alguns  casos. Contudo, a seguinte combinação `\textit{\textit{itálico}}` comporta-se de maneira diferente de `\emph{\emph{itálico}}`.

---

**Questão 03: Qual é o nome do pacote para adicionar cor?**

_Resposta:_ O pacote para adicionar cor é o color.

---

**Questão 04: Qual(is) é(são) a(s) diferença(s) deste comando para o comando `\color`?**

_Resposta:_ Ao contrário do comando \color, o `\textcolor` recebe como argumento um excerto de texto.

---

**Questão 05: Qual o comando para introduzir uma cor de fundo numa porção de texto?**

_Resposta:_ `\colorbox`.

---

**Questão 06: Tendo em conta o comando utilizado acima, assinale a opção correta:**

_Resposta:_ Ambas as palavras ficam com tamanho minúsculo.

---

**Questão 07: O termo utilizado, entre chavetas, em `\begin` e `\end` tem de ser o mesmo?**

_Resposta:_ Sim, claro. Senão até dá erro de compilação. 

---

**Questão 08: Só para que fique bem sólido na memória: como é que se pode começar um parágrafo novo em $\LaTeX$?**

_Resposta:_ Deixando uma linha em branco antes desse novo parágrafo.

---

**Questão 09: Na tarefa anterior, a segunda frase começou num novo parágrafo?**

_Resposta:_ Sim, pois a frase começou com um espaço em relação à margem esquerda.

---

**Questão 10: Notou alguma diferença, relativamente ao resultado final, entre o uso de `\\` e `\par`?**

_Resposta:_ Sim, notei. Usando \\ parece que ficou mais junto à margem esquerda.

---

**Questão 11: Como proceder se quisermos adicionar uma barra invertida e quisermos que esta apareça na versão final do documento, após compilação?**

_Resposta:_ Usando o comando `\textbackslash`.

---

**Questão 12: Visto que já está no nível de _padawan_ de $\LaTeX$, e só de vista, quantas colunas é que acha que a tabela representada no código anterior tem?**

_Resposta:_ Três.

---

**Questão 13: E quantas linhas?**

_Resposta:_ Duas.

---

**Questão 14: O que pode comentar, relativamente ao alinhamento das células da tabela?**

_Resposta:_ As células da primeira coluna estão alinhadas à esquerda, as da segunda à direita e as da terceira ao centro.

---

**Questão 15: Qual é a finalidade do comando `\line`?**

_Resposta:_ Gera uma linha horizontal entre o conteúdo da tabela e o cabeçalho.

---

**Questão 16: À semelhança do índice de conteúdos, demonstrado na aula anterior, qual é o comando para gerar um índice de tabelas?**

_Resposta:_ Cheguei à conclusão, após cuidada deliberação, que é o comando `\listoftables`.

---

**Questão 17: É verdade que o índice está vazio?**

_Resposta:_ Está vazio... Será que usei o comando certo?

---

**Questão 18: O índice continua vazio?**

_Resposta:_ Não! Agora já lá está com o nome `tabela1` e indica em que página está e tudo! Até as galinhas dizem: imp, imp, impecável!

---

**Questão 19: O que tem a dizer relativamente ao extrato de instrução `[scale=0.5]`?**

_Resposta:_ Permite reduzir o tamanho da figura para 50% do seu tamanho original.

---

**Questão 20: É possível gerar um índice de figuras?**

_Resposta:_ Após uma pesquisa rápida, cheguei à conclusão que é o comando `\listoffigures`.

---

**Questão 21: O índice encontra-se vazio?**

_Resposta:_ Está vazio, sim, e deduzo (porque tenho um tio que ainda é arraçado do _Sherlock Holmes_) que é preciso fazer algo semelhante ao que foi feito para as tabelas...

---

**Questão 22: O índice continua vazio?**

_Resposta:_ Já não está vazio. Consigo ver a legenda no índice e a indicação da página onde a figura

---

**Questão 23: Qual é a diferença entre os dois excertos de código criados na tarefa anterior?**

_Resposta:_ Ambos exibem a fórmula, em destaque, mas o ambiente `equation` exibe, adicionalmente, um número junto da equação.

---

**Questão 24: O excerto de código foi compilado com sucesso?**

_Resposta:_ Compilou, mas deu-me uns avisos e apareceu-me um ponto de interrogação ali no meio do texto... Será que o $\LaTeX$ quer falar comigo?

---

**Questão 25: Com a introdução deste novo ficheiro, o excerto de código foi compilado com sucesso?**

_Resposta:_ Não parece ter mudado nada. Continuo com o ponto de interrogação ali no meio do texto...

---

**Questão 26: Com mais esta mudança, o excerto de código foi (finalmente) compilado com sucesso?**

_Resposta:_ Sim! O ponto de interrogação foi substituído por `1` e já aparece uma secção de referências.

<br/><br/>

## Aula Prática 3

**Questão 01: Onde é que deve aparecer o capítulo da _Engenharia de Software_?**

_Resposta:_ Antes da Implementação e depois do Estado da Arte.

---

**Questão 02: Relativamente à secção de `Estado da Arte`, podemos citar os seguintes recursos para realizar a pesquisa bibliográfica (selecione todas as que se apliquem):**

_Resposta:_
- Artigos científicos em revista.
- Artigos científicos em conferência.
- Livros.
- Teses e dissertações.
- Relatórios técnicos conhecidos.

---

**Questão 03: Considere o cenário em que está a ter dificuldades em termos sintáticos e/ou de concordância na redação do seu documento técnico. Que ferramenta(s) pode(m) ajudar nestes aspetos?**

_Resposta:_ Conheço uma que se chama `LanguageTool`. `Expresso App` (mas não é a do jornal).

---

**Questão 04: O que pode comentar relativamente ao uso das palavras-chave?**

_Resposta:_ A separação das palavras-chave não está bem. Deveria ter sido usado vírgula ou ponto-e-vírgula. As palavras-chave não estão por ordem alfabética.

---

**Questão 05: O que acha da afirmação anterior?**

_Resposta:_ Um uso equilibrado de palavras-chave é recomendado, dependendo também da quantidade de temas relevantes abordados no documento. Em caso de dúvida, entre três a cinco seria uma boa estimativa.

---

**Questão 06: Existe algum critério de ordenação para os acrónimos?**

_Resposta:_ Sim, devem estar ordenados por ordem alfabética.

---

**Questão 07: Relativamente à tarefa anterior, assinale todos os erros que encontrou:**

_Resposta:_ Acrónimo não foi definido por extenso na primeira utilização. Uso em demasia de acrónimo.

---

**Questão 08: Qual é o nome do pacote para utilizar acrónimos?**

_Resposta:_ Na aula teórica o Professor disse que era `acronym`.

---

**Questão 09: O que colocou como segundo argumento no comando `\acro`?**

_Resposta:_ Universidade da Beira Interior.

---

**Questão 10: O que apareceu no documento final compilado no local onde o acrónimo é utilizado pela _primeira_ vez?**

_Resposta:_ Universidade da Beira Interior (UBI).

---

**Questão 11: Houve algum capítulo em que não teve de realizar nenhuma alteração, ou seja, já se encontrava corretamente capitalizado?**

_Resposta:_ Não, tive de fazer alterações a todos os capítulos.

---


**Questão 12: O que pode comentar relativamente à ordenação dos capítulos na tarefa anterior?**

_Resposta:_ A ordenação está correta.

---

**Questão 13: Relativamente à tarefa anterior, em quantos capítulos introduziu as secções referidas?**

_Resposta:_ Dois.

---

**Questão 14: O que pode dizer da qualidade do trecho de código apresentado?**

_Resposta:_ A qualidade não é adequada porque tem uma paupérrima indentação e espaçamento.

---

**Questão 15: Tendo em conta os comentários de aplicação geral da aula teórica, o que tem a dizer da legenda apresentada?**

_Resposta:_ A legenda é auto-contida, descreve fielmente o conteúdo do trecho de código associado mas não termina com um ponto final.

---

**Questão 16: Relativamente à tarefa anterior, todas as figuras e tabelas são referidas, pelo menos uma vez no texto?**

_Resposta:_ NÃO SEI, AINDA NÃO EXPERIMENTEI.

---

**Questão 17: Quantos erros se enconram na frase anterior?**

_Resposta:_ Dois.
Correção: Um `upgrade` à aplicação ocorrerá em três dias.