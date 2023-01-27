<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" redir">###Redirecionamentos e Pipe

Esta seção explica o funcionamento dos recursos de direcionamento de entrada e
saída do sistema <command>Linux.



 redir-maior">###&gt;

Redireciona a saída padrão de um programa/comando/script para algum dispositivo
ou arquivo ao invés do dispositivo de saída padrão (tela).  
<!-- [ %DESCRICAOD [ --> Quando é usado com arquivos, este redirecionamento cria ou 
substitui o conteúdo do arquivo. <!-- ]]> -->


Por exemplo, você pode usar o comando <command>ls para listar
arquivos e usar <literal>ls &gt;listagem para enviar a saída do
comando para o arquivo <filename>listagem</filename>.  Use o comando
<command>cat para visualizar o conteúdo do arquivo
<filename>listagem</filename>.


O mesmo comando pode ser redirecionado para o segundo console
<filename>/dev/tty2</filename> usando: <literal>ls &gt;/dev/tty2, o
resultado do comando <command>ls será mostrado no segundo console
(pressione <literal>ALT e <literal>F2 para mudar para o
segundo console e <literal>ALT e <literal>F1 para retornar
ao primeiro).  O mesmo resultado pode ser obtido com o comando <literal>ls
1&gt;/dev/tty2, sendo que o número <literal>1 indica que
será capturada a saída padrão do comando.


Para redirecionar somente a saída de erros do comando <command>ls,
use a sintaxe: <literal>ls 2&gt;/tmp/erros-do-ls




 redir-maior2">###&gt;&gt;

Redireciona a saída padrão de um programa/comando/script para algum dispositivo
ou adiciona as linhas ao final de arquivo ao invés do dispositivo de saída
padrão (tela).  
<!-- [ %DESCRICAOD [ --> A diferença entre este redirecionamento duplo e o simples, é se
caso for usado com arquivos, adiciona a saída do comando ao final do arquivo
existente ao invés de substituir seu conteúdo. <!-- ]]> -->


Por exemplo, você pode acrescentar a saída do comando <command>ls ao
arquivo <filename>listagem</filename> do capítulo anterior usando <literal>ls /
&gt;&gt;listagem.  Use o comando <command>cat para
visualizar o conteúdo do arquivo <filename>listagem</filename>.




 redir-menor">###&lt;

Direciona a entrada padrão de arquivo/dispositivo para um comando.  Este
comando faz o contrário do anterior, ele envia dados ao comando.


Você pode usar o comando <literal>cat &lt;teste.txt para enviar o
conteúdo do arquivo <filename>teste.txt</filename> ao comando
<command>cat que mostrará seu conteúdo (é claro que o mesmo resultado
pode ser obtido com <literal>cat teste.txt mas este exemplo serviu
para mostrar a funcionalidade do &lt;).




 redir-menor2">###&lt;&lt;

Este redirecionamento serve principalmente para marcar o fim de exibição de um
bloco.  Este é especialmente usado em conjunto com o comando
<command>cat, mas também tem outras aplicações.  Por exemplo:

<screen>
 cat &lt;&lt; final
este arquivo
será mostrado
até que a palavra final seja 
localizada no inicio da linha
final




 redir-pipe">###| (pipe)

Envia a saída de um comando para a entrada do próximo comando para continuidade
do processamento.  Os dados enviados são processados pelo próximo comando que
mostrará o resultado do processamento.


Por exemplo: <literal>ls -la | more, este comando faz a listagem
longa de arquivos que é enviado ao comando <command>more (que tem a
função de efetuar uma pausa a cada 25 linhas do arquivo).


Outro exemplo é o comando <literal>locate find | grep "bin/", neste
comando todos os caminhos/arquivos que contém **find** na
listagem serão mostrados (inclusive man pages, bibliotecas, etc.), então
enviamos a saída deste comando para <literal>grep "bin/" para mostrar
somente os diretórios que contém binários.  Mesmo assim a listagem ocupe mais
de uma tela, podemos acrescentar o <command>more: <literal>locate
find | grep "bin/" | more.


Podem ser usados mais de um comando de redirecionamento (&lt;, &gt;, |) em um
mesmo comando.




 s14.6">###Diferença entre o "|" e o "&gt;"

A principal diferença entre o "|" e o "&gt;", é que o Pipe envolve
processamento entre comandos, ou seja, a saída de um comando é enviado a
entrada do próximo e o "&gt;" redireciona a saída de um comando para um
arquivo/dispositivo.


Você pode notar pelo exemplo acima (<literal>ls -la | more) que ambos
<literal>ls e <literal>more são comandos porque estão
separados por um "|".  Se um deles não existir ou estiver digitado
incorretamente, será mostrada uma mensagem de erro.


Um resultado diferente seria obtido usando um <literal>"&gt;" no
lugar do <literal>"|"; A saída do comando <literal>ls -la &gt;
more seria gravada em um arquivo chamado <filename>more</filename>.




 redir-tee">###tee

Envia ao mesmo tempo o resultado do programa para a saída padrão (tela) e para
um arquivo.  Este comando deve ser usado com o pipe "|".


<command>comando | <command>tee [**arquivo**]

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>ls -la | tee listagem.txt, 
a saída do comando será mostrada normalmente na tela e ao mesmo tempo gravada 
no arquivo
<filename>listagem.txt</filename>.

<!-- ]]> -->


