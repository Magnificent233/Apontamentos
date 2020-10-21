# Laboratórios de Programação

## Aula Prática 1

**Questão 1: O que é que está errado nas seguintes expressões/palavras?**

`Tex Live, LaTeX e MikTex`

_Resposta:_ Estas palavras requerem uma estilização muito própria, com letras acima e abaixo da linha de texto, que só se consegue com muito jeitinho (e com comandos _LaTeX_).

---

**Questão 2: Quais as duas partes que constituem a estrutura geral de um documento LaTeX (escolha duas respostas)?**

_Resposta:_ Preâmbulo. Conteúdo.

---

**Questão 3: As palavras % `Preâmbulo` e % `Conteúdo` aparecem no documento após compilação?**

_Resposta:_ Claro que não aparecem, porque são comentários.

---

**Questão 4: O que acontece se colocar texto (e.g., a palavra `teste`) após a instrução `\end{document}`?**

_Resposta:_ Não dá erro, e a palavra `teste` não aparece no documento (é ignorada).

---

**Questão 5: É verdade que foi gerada uma página rosto só com o título, o autor e a data?**

_Resposta:_ Mesmo! Ficou lindo!

---

**Questão 6: Qual é a diferença entre o comando `\label` e `ref`?**

_Resposta:_ O comando `\label` permite atribuir uma etiqueta a um elemento anterior, enquanto que o comando `\ref` permite fazer referência ao elemento.

---

**Questão 7: Qual é o comando que permite mostrar as páginas de uma referência?**

_Resposta:_ `\pageref`.

---

**Questão 8: Qual é a finalidade do comando `\eg` e do ambiente `\ac`?**

_Resposta:_ O comando `\eg` substitui comando pela expressão definida no início do programa e pelos valores que lhe são atribuídos. O comando `\ac` cria um ambiente predefinido que pode envolver diversos comandos.

---

**Questão 9: Apareceu tudo direitinho?**

_Resposta:_ Sim, tudo bem!

---

**Questão 10: Apareceu tudo direitinho?**

_Resposta:_ Já está impecável.

<br/><br/>

## Aula Prática 2

**Questão 1: Tendo   em   conta   os   comandos   enunciados   no   início   desta   secção,    acha   que é    possível    escrever    a    palavra `teste` em itálico e, simultaneamente, a negrito?**

_Resposta:_ Sim, encadeando os   comandos da seguinte forma: `\textit{\textbf{teste}}`.
Sim, encadeando os comandos  da  seguinte forma: `\textbf{\textit{teste}}`.

---

**Questão 2: O que faz o comando `\emph{palavra}`?**

_Resposta:_ Tem efeito semelhante  a `\textit{itálico}` em alguns  casos. Contudo, a seguinte combinação `\textit{\textit{itálico}}` comporta-se de maneira diferente de `\emph{\emph{itálico}}`.

---

**Questão 3: Qual é o nome do pacote para adicionar cor?**

_Resposta:_ O pacote para adicionar cor é o color.

---

**Questão 4: Qual(is) é(são) a(s) diferença(s) deste comando para o comando `\color`?**

_Resposta:_ Ao contrário do comando \color, o `\textcolor` recebe como argumento um excerto de texto.

---

**Questão 5: Qual o comando para introduzir uma cor de fundo numa porção de texto?**

_Resposta:_ `\colorbox`.

---

**Questão 6: Tendo em conta o comando utilizado acima, assinale a opção correta:**

_Resposta:_ Ambas as palavras ficam com tamanho minúsculo.

---

**Questão 7: O termo utilizado, entre chavetas, em `\begin` e `\end` tem de ser o mesmo?**

_Resposta:_ Sim, claro. Senão até dá erro de compilação. 

---

**Questão 8: Só para que fique bem sólido na memória: como é que se pode começar um parágrafo novo em _LaTeX_?**

_Resposta:_ Deixando uma linha em branco antes desse novo parágrafo.

---

**Questão 9: Na tarefa anterior, a segunda frase começou num novo parágrafo?**

_Resposta:_ Sim, pois a frase começou com um espaço em relação à margem esquerda.

---

**Questão 10: Notou alguma diferença, relativamente ao resultado final, entre o uso de `\\` e `\par`?**

_Resposta:_ Sim, notei. Usando \\ parece que ficou mais junto à margem esquerda.

---

**Questão 11: Como proceder se quisermos adicionar uma barra invertida e quisermos que esta apareça na versão final do documento, após compilação?**

_Resposta:_ Usando o comando `\textbackslash`.

---

**Questão 12: Visto que já está no nível de _padawan_ de _LaTeX_, e só de vista, quantas colunas é que acha que a tabela representada no código anterior tem?**

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

_Resposta:_ howdy

---

**Questão 20: É possível gerar um índice de figuras?**

_Resposta:_ howdy

---

**Questão 21: O índice encontra-se vazio?**

_Resposta:_ howdy

---

**Questão 22: O índice continua vazio?**

_Resposta:_ howdy

---

**Questão 23: Qual é a diferença entre os dois excertos de código criados na tarefa anterior?**

_Resposta:_ howdy

---

**Questão 24: O excerto de código foi compilado com sucesso?**

_Resposta:_ howdy

---

**Questão 25: Com a introdução deste novo ficheiro, o excerto de código foi compilado com sucesso?**

_Resposta:_ howdy

---

**Questão 26: Com mais esta mudança, o excerto de código foi (finalmente) compilado com sucesso?**

_Resposta:_ howdy

<br/><br/>

## Aula Prática 3

**Questão 1:**

_Resposta:_

---