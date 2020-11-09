# Laboratórios de Programação

## Aula Prática 01

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

## Aula Prática 02

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

_Resposta:_ Permite reduzir o tamanho da figura para 50% do seu tamanho original. Não é obrigatório (porque está entre parênteses retos).

---

**Questão 20: É possível gerar um índice de figuras?**

_Resposta:_ Após uma pesquisa rápida, cheguei à conclusão que é o comando `\listoffigures`.

---

**Questão 21: O índice encontra-se vazio?**

_Resposta:_ Está vazio, sim, e deduzo (porque tenho um tio que ainda é arraçado do _Sherlock Holmes_) que é preciso fazer algo semelhante ao que foi feito para as tabelas...

---

**Questão 22: O índice continua vazio?**

_Resposta:_ Já não está vazio. Consigo ver a legenda no índice e a indicação da página onde a figura está.

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

## Aula Prática 03

**Questão 01: Onde é que deve aparecer o capítulo da _Engenharia de Software_?**

_Resposta:_ Antes da Implementação e depois do Estado da Arte.

---

**Questão 02: Relativamente à secção de `Estado da Arte`, devemos citar os seguintes recursos para realizar a pesquisa bibliográfica (selecione todas as que se apliquem):**

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

_Resposta:_ Acrónimo não foi definido por extenso na primeira utilização. (Uso em demasia de acrónimo.) Utilização de acrónimo por extenso quando já havia sido definido.

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

_Resposta:_ Para ficar corretamente ordenado, Detalhes de Implementação teria de trocar com Estado da Arte.

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

_Resposta:_ Não, falta referir a tabela no texto.

---

**Questão 17: Quantos erros se enconram na frase anterior?**

_Resposta:_ Dois.

Correção: Um `upgrade` à aplicação ocorrerá em três dias.

</br></br>

## Aula Prática 04

**Questão 01: Qual é o nome deste programa em Windows?**

_Resposta:_ Consola.

---

**Questão 02: Analise a sua _prompt_ e identifique o seu _user_ e _hostname_:**

_Resposta:_ sara & Prometheus.

---

**Questão 03: Qual o caratere que se encontra entre o _user_ e _hostname_, na sua _prompt_?**

_Resposta:_ `@`.

---

**Questão 04: Qual o caratere que, numa _prompt_ de um sistema _Unix_ ou _Unix-like_, pode denotar _utilizador com privilégios de administração_?**

_Resposta:_ `#`.

---

**Questão 05: O que é considerado um ficheiro (selecione todas as que se apliquem)?**

_Resposta:_ Diretoria. Disco inteiro. Teclado. Rato. Ficheiro. Memória. Impressora. Monitor.

---

**Questão 06: No ambiente de linha de comandos, quantos e quais são os fluxos de dados que interessa conhecer?**

_Resposta:_ São 3: `stdin` (_standard input_), `stdout` (_standard output_) e `stderr` (_standard error_).

---

**Questão 07: Qual o comando que permite obter um manual de um determinado comando?**

_Resposta:_ `man`.

---

**Questão 08: O que observou ao executar o comando da tarefa anterior?**

_Resposta:_ O terminal ficou preenchido com informação, aparentemente dividida por secções de _name_, _synopsis_ e _description_...

---

**Questão 09: O que faz o comando `echo`?**

_Resposta:_ Segundo o manual, exibe uma linha de texto, no terminal.

---

**Questão 10: Há alguma opção do comando `echo` que permita imprimir no terminal, mas evitar que se mude de linha no final de imprimir?**

_Resposta:_ Sim, há. É a opção `-n`.

---

**Questão 11: Qual o último número da versão do comando `man` no seu sistema?**

_Resposta:_ 1.

---

**Questão 12: O que observou ao executar o comando da tarefa anterior?**

_Resposta:_ Ficou lá o comentário e apareceu um novo _prompt_, pronto a receber _input_. Mas não aconteceu mais nada...

---

**Questão 13: No contexto do comando em que foi utilizada, o que constitui a expressão `Olá Mundo`?**

_Resposta:_ Constitui um parâmetro não obrigatório do comando.

---

**Questão 14: Qual foi o comando que utilizou para imprimir o caminho completo da diretoria atual?**

_Resposta:_ Utilizei o comando `pwd`.

---

**Questão 15: Qual foi o comando que utilizou na tarefa anterior?**

_Resposta:_ Utilizei o comando `ls`. Utilizei o comando `dir`.

---

**Questão 16: O que significa a letra `w` do comando `pwd`?**

_Resposta:_ _working_.

---

**Questão 17: O que pode comentar relativamente à opção `-h` do comando `ls`?**

_Resposta:_ Lista as informações dos ficheiros num formato que facilita a leitura humana como, por exemplo, 1K, 234M, 2G, etc. Tem de ser usada em conjunto com outras opções, nomeadamente, `-l` ou `-s`.

---

**Questão 18: Qual é o comando que pode utilizar para navegar da sua diretoria atual para a nova diretoria `teste`?**

_Resposta:_ Estudei arduamente em preparação para esta aula e, neste momento, transbordo de tal maneira de conhecimento que até as minhas vísceras me dizem que é o comando `cd Teste`.

---

**Questão 19: Qual é o comando que sugere utilizar?**

_Resposta:_ Sugiro usar o comando `rm -r`, no entanto não sei para que serve a opção `-r`.

Dada a minha _expertise_ na leitura avançada de manuais, sugeria usar o comando `rmdir`, visto a diretoria estar vazia, mas quem sou eu para ser levad@ em consideração?

---

**Questão 20: Conseguiu remover a diretoria `teste`?**

_Resposta:_ Consegui porque me apercebi que tinha de sair da diretoria para a eliminar.

---

**Questão 21: Qual foi o comando que utilizou para criar o ficheiro na tarefa anterior?**

_Resposta:_ `touch`.

---

**Questão 22: Tem a certeza de que o ficheiro está mesmo vazio?**

_Resposta:_ Tem toda a razão.  Devo verificar se, de facto, o ficheiro está vazio, eventualmente com a instrução `ls -l`.

---

**Questão 23: De que maneira poderia imprimir o conteúdo do ficheiro, criado na tabela anterior, no terminal?**

_Resposta:_ Usando o comando `cat vazio.txt`.

---

**Questão 24: Relativamente a movimentação do ficheiro, que comando utilizou para realizar a tarefa anterior?**

_Resposta:_ `mv vazio.txt nova_dir/`.

---

**Tarefa 12:** `cp nova_dir/vazio.txt ./vazio.txt`.

---

**Questão 25: Para relembrar, qual é a finalidade do caratere `|`?**

_Resposta:_ O caractere `|` representa um _pipe_, que permite ligar o fluxo `stdout` de um comando ao fluxo `stdin` de outro comando.

---

**Questão 26: O que faz o comando `cat`?**

_Resposta:_ Imprime o conteúdo de um ou mais ficheiros no terminal.

---

**Questão 27: O que faz o comando `grep`?**

_Resposta:_ Imprime linhas que contenham o padrão procurado.

---

**Questão 28: Tendo em conta as respostas das questões anteriores, qual é a função do `pipe` na tarefa anterior?**

_Resposta:_ Dado o conteúdo do ficheiro `vazio.txt`, exibe as linhas que contenham a palavra CLI.

---

**Tarefa 14:** `cat vazio.txt > vazio_copia.txt`.

---

**Questão 29: Dados os exemplos, qual é a diferença entre os comandos `>` e `>>`?**

_Resposta:_ Usando `>`, o conteúdo do ficheiro `file2.txt` será substituído pelo conteúdo do ficheiro `file1.txt`, enquanto `>>` concatena o conteúdo do ficheiro `file1.txt` no final do ficheiro `file2.txt`.

---

<br/><br/>

## Aula Prática 05

**Questão 01: Qual é a utilidade da primeira linha do ficheiro criado na tarefa anterior?**

_Resposta:_ Serve para indicar que o _script_ deve ser interpretado pelo _bash_ e não por outro interpretador.

---

**Questão 02: Qual foi o comando que usou para imprimir a mensagem no terminal?**

_Resposta:_ `echo`.

---

**Questão 03: Qual foi o símbolo utilizado?**

_Resposta:_ `$`.

---

**Questão 04: A execução do ficheiro culminou na impressão da mesnagem esperada?**

_Resposta:_ Sim. O terminal deu-me os bons dias e o meu dia até ficou melhor!

---

**Questão 05: É possível?**

_Resposta:_ Sim, é possível. Mas para tal é necessário usar o comando `chmod u+x script.sh` antes.

---

**Questão 06: O que teve de adicionar ao comando `echo` para que produzisse a mensagem requerida na tarefa anterior?**

_Resposta:_ Para usar o primeiro argumento tive de incuir `$1` no comando `echo`.

---

**Questão 07: Qual é a finalidade de `-gt`, no trecho de código exibido?**

_Resposta:_ É um operador de comparação. Neste caso, é usado para que a condição _if_ siva para verificar se o valor de VAR é superior (_greater than_) a 100.

---

**Questão 08: Houve alguma alteração relativamente à execução, deste mesmo ficheiro, comparativamente à tarefa 5?**

_Resposta:_ Houve, sim senhor! Agora o _script.sh_ exige que lhe passe um argumento. Será que se der mais do que um também funciona?

---

**Questão 09: Qual é o comando que pode utilizar para usufruir desta funcionalidade?**

_Resposta:_ `read`.

---

**Questão 10: Qual o comando que usou para ler o _input_ do utilizador e guardá-lo na variável `IDADE`?**

_Resposta:_ `read IDADE`.

---

**Questão 11: Qual o comando que usou para imprimir a mensagem com a variável `IDADE`?**

_Resposta:_ `echo "Tem $IDADE anos."`.

---

**Questão 12: Em qual das fases anteriormente apresentadas se enquadraria o comando apresentado?**

_Resposta:_ Compilação e interligação do código.

---

**Questão 13: O que pode comentar relativamente ao uso da oção `-o` no comando apresentado?**

_Resposta:_ É uma opção facultativa que permite definir o nome do executável.

---

**Questão 14: Qual é o significado de ficheiros com extensão `.h`?**

_Resposta:_ Significa que é ficheiro de cabeçalho (_header_).

---

**Questão 15: Qual é a utilidade da inclusão do ficheiro `soma.h`?**

_Resposta:_ Permite que seja usada uma função que está presente no ficheiro `soma.c`.

---

**Questão 16: Qual é a razão para que `soma.h` tenha sido incluído entre `""`, enquanto `stdio.h` foi incluído com `<>`?**

_Resposta:_ Ambos são ficheiros de cabeçalho mas `soma.h` é ficheiro de cabeçalho local enquanto `stdio.h` é do compilador.

---

**Tarefa 9:** 

---

**Questão 17: Qual o comnado que utilizaria para compilar o programa descrito na tarefa anterior?**

_Resposta:_ 

---

**Questão 18: Caso a sua intenção fosse compilar os ficheiros e obter os ficheiros objetos destes (com extenção `.o`) qual seria a opção a usar, aquando do processo de compilação?**

_Resposta:_ 

---

**Questão 19: Qual, das seguintes opções, permitiria atingir esse objetivo?**

_Resposta:_ 

---

**Questão 20: Dada a opção escolhida na questão anterior, de que forma executaria o ficheiro executável resultante?**

_Resposta:_ 

---

**Tarefa 10:** 

---

**Questão 21: Qual é a designação de `main.o` e `main.c` na nomenclatura dos `makefiles`, respetivamente, no exemplo anterior?**

_Resposta:_ 

---

**Questão 22: Qual é a designação de `cc -c main.c` no trecho de código apresentado?**

_Resposta:_ 

---

**Questão 23: Qual é a finalidade da regra apresentada no trecho de código?**

_Resposta:_ 

---

**Questão 24: Assumindo que tem os ficheiros `.c`, `.h` e `makefile` disponibilizados na diretoria `Lab_5_Compile_Make`, o que prevê que aconteça caso execute o comando `make`?**

_Resposta:_ 

---

**Questão 25: O que pode comentar relativamente a um _phony target_?**

_Resposta:_ 

---

