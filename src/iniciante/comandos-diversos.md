<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cmdv">###Comandos Diversos

Comandos de uso diversos no sistema.

 cmdv-clear">###clear

Limpa a tela e posiciona o cursor no canto superior esquerdo do vídeo.


<literal>clear




 cmdv-date">###date

Permite ver/modificar a Data e Hora do Sistema.  Você precisa estar como
usuário root para modificar a data e hora.  
<!-- [ %INTERMEDIARIO [ --> 
Muitos programas do sistema, arquivos de registro (log) e tarefas agendadas 
funcionam com base na data e hora fornecidas pelo sistema, assim esteja consciente 
das modificações que a data/hora pode trazer a estes programas (principalmente em 
se tratando de uma rede com muitos usuários). <!-- ]]> -->


<command>date MesDiaHoraMinuto[AnoSegundos]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>MesDiaHoraMinuto[AnoSegundos]
<listitem>

São respectivamente os números do mês, dia, hora e minutos sem espaços.
Opcionalmente você pode especificar o Ano (com 2 ou 4 dígitos) e os Segundos.



<varlistentry>
<term>+[FORMATO]
<listitem>

Define o formato da listagem que será usada pelo comando
<command>date.  Os seguintes formatos são os mais usados:

<itemizedlist>
<listitem><literal>%d - Dia do Mês (00-31).
<listitem><literal>%m - Mês do Ano (00-12).
<listitem><literal>%y - Ano (dois dígitos).
<listitem><literal>%Y - Ano (quatro dígitos).
<listitem><literal>%H - Hora (00-24).
<listitem><literal>%I - Hora (00-12).
<listitem><literal>%M - Minuto (00-59).
<listitem><literal>%j - Dia do ano (1-366).
<listitem><literal>%p - AM/PM (útil se utilizado com %d).
<listitem><literal>%r - Formato de 12 horas completo (hh:mm:ss AM/PM).
<listitem><literal>%T - Formato de 24 horas completo (hh:mm:ss).
<listitem><literal>%w - Dia da semana (0-6).


Outros formatos podem ser obtidos através da página de manual do
<command>date.



</variablelist>
<!-- ]]> -->

Para maiores detalhes, veja a página de manual do comando
<command>date.

<!-- [ %EXEMPLO [ -->

Para ver a data atual digite: <literal>date


Se quiser mudar a Data para 25/12 e a hora para 08:15 digite: <literal>date
12250815


Para mostrar somente a data no formato dia/mês/ano: <literal>date
+%d/%m/%Y

<!-- ]]> -->



 cmdv-df">###df

Mostra o espaço livre/ocupado de cada partição.


<command>df [**opções**]

<!-- [ %OPCOES [ --> 

onde:

<variablelist>

<varlistentry>
<term>**opções**
<term>-a
<listitem>

Inclui sistemas de arquivos com 0 blocos.




<varlistentry>
<term>-h, --human-readable
<listitem>

Mostra o espaço livre/ocupado em **MB, KB, GB** ao invés de
blocos.




<varlistentry>
<term>-H
<listitem>

Idêntico a <literal>-h mas usa 1000 ao invés de 1024 como unidade de
cálculo.




<varlistentry>
<term>-k
<listitem>

Lista em Kbytes.




<varlistentry>
<term>-l
<listitem>

Somente lista sistema de arquivos locais.




<varlistentry>
<term>-m
<listitem>

Lista em Mbytes (equivalente a --block-size=1048576).




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>--sync
<listitem>

Executa o <command>sync antes de mostrar os dados.




<varlistentry>
<term>-T
<listitem>

Lista o tipo de sistema de arquivos de cada partição




<varlistentry>
<term>-t **tipo**
<listitem>

Lista somente sistema de arquivos do tipo **tipo**.




<varlistentry>
<term>-x **tipo**
<listitem>

Não lista sistemas de arquivos do tipo **tipo**.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos: <literal>df, <literal>df -h, <literal>df -t
vfat.

<!-- ]]> -->



 cmdv-ln">###ln

Cria links para arquivos e diretórios no sistema.  
<!-- [ %DESCRICAOD [ --> O link é um mecanismo que faz referência a outro arquivo ou 
diretório em outra localização.  O link em sistemas <command>GNU/Linux 
faz referência reais ao arquivo/diretório podendo ser feita cópia do link (será 
copiado o arquivo alvo), entrar no diretório (caso o link faça referência a um 
diretório), etc. <!-- ]]> -->


<command>ln [**opções**] [**origem**]
[**link**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**origem**
<listitem>

Diretório ou arquivo de onde será feito o link.



<varlistentry>
<term>**link**
<listitem>

Nome do link que será criado.



<varlistentry>
<term>**opções**
<term>-s
<listitem>

Cria um link simbólico.  Usado para criar ligações com o arquivo/diretório de
destino.



<varlistentry>
<term>-v
<listitem>

Mostra o nome de cada arquivo antes de fazer o link.



<varlistentry>
<term>-d
<listitem>

Cria um hard link para diretórios.  Somente o root pode usar esta opção.



</variablelist>
<!-- ]]> -->

Existem 2 tipos de links: **simbólicos** e
**hardlinks**.

<itemizedlist>
<listitem>

O **link simbólico** cria um arquivo especial no disco (do
tipo link) que tem como conteúdo o caminho para chegar até o arquivo alvo (isto
pode ser verificado pelo tamanho do arquivo do link).  Use a opção
<literal>-s para criar links simbólicos.


<listitem>

O **hardlink** faz referência ao mesmo inodo do arquivo
original, desta forma ele será perfeitamente idêntico, inclusive nas permissões
de acesso, ao arquivo original.


Ao contrário dos links simbólicos, não é possível fazer um hardlink para um
diretório ou fazer referência a arquivos que estejam em partições diferentes.




<!-- [ %OBS [ -->

Observações:

<itemizedlist>
<listitem>

Se for usado o comando <command>rm com um link, somente o link será
removido.


<listitem>

Se for usado o comando <command>cp com um link, o arquivo original
será copiado ao invés do link.


<listitem>

Se for usado o comando <command>mv com um link, a modificação será
feita no link.


<listitem>

Se for usado um comando de visualização (como o <command>cat), o
arquivo original será visualizado.



<!-- ]]> -->

<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

<literal>ln -s /dev/ttyS1 /dev/modem - Cria o link
<filename>/dev/modem</filename> para o arquivo <filename>/dev/ttyS1</filename>.


<listitem>

<literal>ln -s /tmp ~/tmp - Cria um link <filename>~/tmp</filename>
para o diretório <filename>/tmp</filename>.



<!-- ]]> -->


 cmdv-du">###du

Mostra o espaço ocupado por arquivos e sub-diretórios do diretório atual.


<command>du [**opções**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-a, --all
<listitem>

Mostra o espaço ocupado por todos os arquivos.



<varlistentry>
<term>-b, --bytes
<listitem>

Mostra o espaço ocupado em bytes.



<varlistentry>
<term>-c, --total
<listitem>

Faz uma totalização de todo espaço listado.



<varlistentry>
<term>-D
<listitem>

Não conta links simbólicos.



<varlistentry>
<term>-h, --human
<listitem>

Mostra o espaço ocupado em formato legível por humanos (Kb, Mb) ao invés de
usar blocos.



<varlistentry>
<term>-H
<listitem>

Como o anterior mas usa 1000 e não 1024 como unidade de cálculo.



<varlistentry>
<term>-k
<listitem>

Mostra o espaço ocupado em Kbytes.



<varlistentry>
<term>-m
<listitem>

Mostra o espaço ocupado em Mbytes.



<varlistentry>
<term>-S, --separate-dirs
<listitem>

Não calcula o espaço ocupado por sub-diretórios.




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-x
<listitem>

Não faz a contagem de diretórios em sistemas de arquivos diferentes do atual.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>du -h, <literal>du -hc.

<!-- ]]> -->



 cmdv-find">###find

Procura por arquivos/diretórios no disco.  
<!-- [ %DESCRICAOD [ --> O<command>find pode
procurar arquivos através de sua data de modificação, tamanho, etc através do
uso de opções.  <command>find, ao contrário de outros programas, usa
opções longas através de um <literal>"-". <!-- ]]> -->


<command>find [**diretório**]
[**opções/expressão**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**diretório**
<listitem>

Inicia a procura neste diretório, percorrendo seu sub-diretórios.



<varlistentry>
<term>**opções/expressão**
<term>-name [expressão]
<listitem>

Procura pelo nome [expressão] nos nomes de arquivos e diretórios processados.



<varlistentry>
<term>-depth
<listitem>

Processa os sub-diretórios primeiro antes de processar os arquivos do diretório
principal.



<varlistentry>
<term>-maxdepth [num]
<listitem>

Faz a procura até [num] sub-diretórios dentro do diretório que está sendo
pesquisado.



<varlistentry>
<term>-mindepth [num]
<listitem>

Não faz nenhuma procura em diretórios menores que [num] níveis.



<varlistentry>
<term>-mount, -xdev
<listitem>

Não faz a pesquisa em sistemas de arquivos diferentes daquele de onde o comando
<command>find foi executado.




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-amin [num]
<listitem>

Procura por arquivos que foram acessados [num] minutos atrás.  Caso for
antecedido por "-", procura por arquivos que foram acessados entre [num]
minutos atrás até agora.



<varlistentry>
<term>-atime [num]
<listitem>

Procura por arquivos que foram acessados [num] dias atrás.  Caso for antecedido
por "-", procura por arquivos que foram acessados entre [num] dias atrás e a
data atual.



<varlistentry>
<term>-gid [num]
<listitem>

Procura por arquivos que possuam a identificação numérica do grupo igual a
[num].



<varlistentry>
<term>-group [nome]
<listitem>

Procura por arquivos que possuam a identificação de nome do grupo igual a
[nome].



<varlistentry>
<term>-uid [num]
<listitem>

Procura por arquivos que possuam a identificação numérica do usuário igual a
[num].



<varlistentry>
<term>-user [nome]
<listitem>

Procura por arquivos que possuam a identificação de nome do usuário igual a
[nome].



<varlistentry>
<term>-inum [num]
<listitem>

Procura por arquivos que estão localizados no inodo [num].



<varlistentry>
<term>-links [num]
<listitem>

Procura por arquivos que possuem [num] links como referência.



<varlistentry>
<term>-mmin [num]
<listitem>

Procura por arquivos que tiveram seu conteúdo modificado há [num] minutos.
Caso for antecedido por "-", procura por arquivos que tiveram seu conteúdo
modificado entre [num] minutos atrás até agora.



<varlistentry>
<term>-mtime [num]
<listitem>

Procura por arquivos que tiveram seu conteúdo modificado há [num] dias.  Caso
for antecedido por "-", procura por arquivos que tiveram seu conteúdo
modificado entre [num] dias atrás até agora.



<varlistentry>
<term>-ctime [num]
<listitem>

Procura por arquivos que teve seu status modificado há [num] dias.  Caso for
antecedido por "-", procura por arquivos que tiveram seu conteúdo modificado
entre [num] dias atrás até agora.



<varlistentry>
<term>-nouser
<listitem>

Procura por arquivos que não correspondam a identificação do usuário atual.



<varlistentry>
<term>-nogroup
<listitem>

Procura por arquivos que não correspondam a identificação do grupo do usuário
atual.



<varlistentry>
<term>-perm [modo]
<listitem>

Procura por arquivos que possuam os modos de permissão [modo].  Os [modo] de
permissão pode ser numérico (octal) ou literal.



<varlistentry>
<term>-used [num]
<listitem>

O arquivo foi acessado [num] vezes antes de ter seu status modificado.



<!-- ]]> -->
<varlistentry>
<term>-size [num]
<listitem>

Procura por arquivos que tiverem o tamanho [num].  [num] pode ser antecedido de
"+" ou "-" para especificar um arquivo maior ou menor que [num].  A opção -size
pode ser seguida de:

<itemizedlist>
<listitem>

<literal>b - Especifica o tamanho em blocos de 512 bytes.  É o padrão
caso [num] não seja acompanhado de nenhuma letra.


<listitem>

<literal>c - Especifica o tamanho em bytes.


<listitem>

<literal>k - Especifica o tamanho em Kbytes.





<varlistentry>
<term>-type [tipo]
<listitem>

Procura por arquivos do [tipo] especificado.  Os seguintes tipos são aceitos:

<itemizedlist>
<listitem><literal>b - bloco
<listitem><literal>c - caracter
<listitem><literal>d - diretório
<listitem><literal>p - pipe
<listitem><literal>f - arquivo regular
<listitem><literal>l - link simbólico
<listitem><literal>s - sockete



</variablelist>
<!-- ]]> -->

A maior parte dos argumentos numéricos podem ser precedidos por "+" ou "-".
Para detalhes sobre outras opções e argumentos, consulte a página de manual.

<!-- [ %EXEMPLO [ -->

Exemplo:

<itemizedlist>
<listitem>

<literal>find / -name grep - Procura no diretório raíz e
sub-diretórios um arquivo/diretório chamado <filename>grep</filename>.


<listitem>

<literal>find / -name grep -maxdepth 3 - Procura no diretório raíz e
sub-diretórios até o 3o.  nível, um arquivo/diretório chamado
<filename>grep</filename>.


<listitem>

<literal>find .  -size +1000k - Procura no diretório atual e
sub-diretórios um arquivo com tamanho maior que 1000 kbytes (1Mbyte).


<listitem>

<literal>find / -mmin 10 - Procura no diretório raíz e sub-diretórios
um arquivo que foi modificado há 10 minutos atrás.


<listitem>

<literal>find / -links 4 - Procura no diretório raíz e
sub-diretórios, todos os arquivos que possuem 4 links como referência.



<!-- ]]> -->



 cmdv-free">###free

Mostra detalhes sobre a utilização da memória RAM do sistema.


<command>free [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-b
<listitem>

Mostra o resultado em bytes.



<varlistentry>
<term>-k
<listitem>

Mostra o resultado em Kbytes.



<varlistentry>
<term>-m
<listitem>

Mostra o resultado em Mbytes.



<varlistentry>
<term>-o
<listitem>

Oculta a linha de buffers.



<varlistentry>
<term>-t
<listitem>

Mostra uma linha contendo o total.



<varlistentry>
<term>-s [num]
<listitem>

Mostra a utilização da memória a cada [num] segundos.



</variablelist>
<!-- ]]> -->

O <command>free é uma interface ao arquivo
<filename>/proc/meminfo</filename>.




 cmdv-grep">###grep

Procura por um texto dentro de um arquivo(s) ou no dispositivo de entrada
padrão.


<command>grep [**expressão**] [**arquivo**]
[**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**expressão**
<listitem>

palavra ou frase que será procurada no texto.  Se tiver mais de 2 palavras você
deve identifica-la com aspas "" caso contrário o <command>grep
assumirá que a segunda palavra é o arquivo!



<varlistentry>
<term>**arquivo**
<listitem>

Arquivo onde será feita a procura.



<varlistentry>
<term>**opções**
<term>-A [número]
<listitem>

Mostra o [número] de linhas após a linha encontrada pelo
<command>grep.



<varlistentry>
<term>-B [número]
<listitem>

Mostra o [número] de linhas antes da linha encontrada pelo
<command>grep.



<varlistentry>
<term>-f [arquivo]
<listitem>

Especifica que o texto que será localizado, esta no arquivo [arquivo].



<varlistentry>
<term>-h, --no-filename
<listitem>

Não mostra os nomes dos arquivos durante a procura.



<varlistentry>
<term>-i, --ignore-case
<listitem>

Ignora diferença entre maiúsculas e minúsculas no texto procurado e arquivo.



<varlistentry>
<term>-n, --line-number
<listitem>

Mostra o nome de cada linha encontrada pelo <command>grep.



<varlistentry>
<term>-E
<listitem>

Ativa o uso de expressões regulares.



<varlistentry>
<term>-U, --binary
<listitem>

Trata o arquivo que será procurado como binário.



</variablelist>
<!-- ]]> -->

Se não for especificado o nome de um arquivo ou se for usado um hífen "-",
<command>grep procurará a string no dispositivo de entrada padrão.  O
<command>grep faz sua pesquisa em arquivos texto.  Use o comando
<command>zgrep para pesquisar diretamente em arquivos compactados com
<command>gzip, os comandos e opções são as mesmas.

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>grep "capitulo" texto.txt, <literal>ps ax|grep
inetd, <literal>grep "capitulo" texto.txt -A 2 -B 2.

<!-- ]]> -->



 cmdv-head">###head

Mostra as linhas iniciais de um arquivo texto.


<command>head [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>-c [numero]
<listitem>

Mostra o [numero] de bytes do inicio do arquivo.



<varlistentry>
<term>-n [numero]
<listitem>

Mostra o [numero] de linhas do inicio do arquivo.  Caso não for especificado, o
<command>head mostra as 10 primeiras linhas.



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos: <literal>head teste.txt, <literal>head -n 20
teste.txt.

<!-- ]]> -->


 cmdv-nl">###nl

Mostra o número de linhas junto com o conteúdo de um arquivo.


<command>nl [**opções**]
[**arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-f [opc]
<listitem>

Faz a filtragem de saída de acordo com [opc]:

<variablelist>
<varlistentry>
<term>a
<listitem>

Numera todas as linhas.



<varlistentry>
<term>t
<listitem>

Não numera linhas vazias.



<varlistentry>
<term>n
<listitem>

Numera linhas vazias.



<varlistentry>
<term>texto
<listitem>

Numera somente linhas que contém o [texto].



</variablelist>


<varlistentry>
<term>-v [num]
<listitem>

Número inicial (o padrão é 1).



<varlistentry>
<term>-i [num]
<listitem>

Número de linhas adicionadas a cada linha do arquivo (o padrão é 1).



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos: <literal>nl /etc/passwd, <literal>nl -i 2
/etc/passwd.

<!-- ]]> -->



 cmdv-more">###more

Permite fazer a paginação de arquivos ou da entrada padrão.  
<!-- [ %DESCRICAOD [ --> O comando <command>more pode ser usado como comando 
para leitura de arquivos que ocupem mais de uma tela.  Quando toda a tela é ocupada, 
o <command>more efetua uma pausa e permite que você pressione
<literal>Enter ou <literal>espaço para continuar avançando
no arquivo sendo visualizado.  Para sair do <command>more pressione
<literal>q. <!-- ]]> -->


<command>more [**arquivo**]


Onde: **arquivo** É o arquivo que será paginado.


Para visualizar diretamente arquivos texto compactados pelo
<command>gzip <filename>.gz</filename> use o comando
<command>zmore.

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>more /etc/passwd, <literal>cat
/etc/passwd|more.
 
<!-- ]]> -->



 cmdv-less">###less

Permite fazer a paginação de arquivos ou da entrada padrão.  
<!-- [ %DESCRICAOD [ --> O comando
<command>less pode ser usado como comando para leitura de arquivos
que ocupem mais de uma tela.  Quando toda a tela é ocupada, o
<command>less efetua uma pausa (semelhante ao
<command>more) e permite que você pressione Seta para Cima e Seta
para Baixo ou PgUP/PgDown para fazer o rolamento da página.  Para sair do
<command>less pressione <literal>q. <!-- ]]> -->


<command>less [**arquivo**]


Onde: **arquivo** É o arquivo que será paginado.

<!-- [ %OBS [ -->

Para visualizar diretamente arquivos texto compactados pelo utilitário
<command>gzip (arquivos <filename>.gz</filename>), use o comando
<command>zless.
 <!-- ]]> -->
<!-- [ %EXEMPLO [ --> 

Exemplos: <literal>less /etc/passwd, <literal>cat
/etc/passwd|less

<!-- ]]> -->



 cmdv-sort">###sort

Organiza as linhas de um arquivo texto ou da entrada padrão.  
<!-- [ %DESCRICAOD [ --> A organização é
feita por linhas e as linhas são divididas em **campos** que é
a ordem que as palavras aparecem na linha separadas por um delimitador
(normalmente um espaço). <!-- ]]> -->


<command>sort [**opções**]
[**arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivo**
<listitem>

É o nome do arquivo que será organizado.  Caso não for especificado, será usado
o dispositivo de entrada padrão (normalmente o teclado ou um "|").



<varlistentry>
<term>**opções**
<term>-b
<listitem>

Ignora linhas em branco.



<varlistentry>
<term>-d
<listitem>

Somente usa letras, dígitos e espaços durante a organização.



<varlistentry>
<term>-f
<listitem>

Ignora a diferença entre maiúsculas e minúsculas.



<varlistentry>
<term>-r
<listitem>

Inverte o resultado da comparação.



<varlistentry>
<term>-n
<listitem>

Caso estiver organizando um campo que contém números, os números serão
organizados na ordem aritmética.  Por exemplo, se você tiver um arquivo com os
números

<screen>
100
10
50


Usando a opção <literal>-n, o arquivo será organizado desta maneira:

<screen>
10
50 
100


Caso esta opção **não** for usada com o
<command>sort, ele organizará como uma listagem alfabética (que
começam de <literal>a até <literal>z e do
<literal>0 até <literal>9)

<screen>
10 
100
50



<varlistentry>
<term>-c
<listitem>

Verifica se o arquivo já esta organizado.  Caso não estiver, retorna a mensagem
"disorder on **arquivo**".



<varlistentry>
<term>-o **arquivo**
<listitem>

Grava a saída do comando <command>sort no
**arquivo**.




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-m **arquivo1** **arquivo2**
<listitem>

Combina o conteúdo de **arquivo1** e
**arquivo2** gerando um único arquivo.  Os dois arquivos
precisam estar ordenados antes de se utilizar esta opção.



<varlistentry>
<term>-i
<listitem>

Ignora os caracteres fora da faixa octal ASCII 040-0176 durante a organização.



<varlistentry>
<term>-t **caracter**
<listitem>

Usa **caracter** como delimitador durante a organização de
linhas.  Por padrão é usado um **espaço em branco** como
delimitador de caracteres.



<varlistentry>
<term>**+num1 -num2**
<listitem>

Especifica qual o campo dentro na linha que será usado na organização.  O(s)
campo(s) usado(s) para organização estará entre **+num1** e
**+num2**.  O delimitador padrão utilizado é um
**espaço em branco** (use a opção <literal>-t para
especificar outro).  A contagem é iniciada em "0".  Caso não for especificada,
a organização é feita no primeiro campo.  Caso **-num2** não
seja especificado, a organização será feita usando a coluna
**+num1** até o fim da linha.



<varlistentry>
<term>-k **num1**, **num2**
<listitem>

Esta é uma alternativa ao método acima para especificar as chaves de
organização.  O uso é idêntico, mas o delimitador é iniciado em "1".



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

<!-- [ %EXEMPLO [ -->

Abaixo, exemplos de uso do comando <command>sort:

<itemizedlist>
<listitem>

<literal>sort <filename>texto.txt</filename> - Organiza o arquivo
<filename>texto.txt</filename> em ordem crescente.


<listitem>

<literal>sort <filename>texto.txt</filename> -r - Organiza o conteúdo
do arquivo <filename>texto.txt</filename> em ordem decrescente.


<listitem>

<literal>cat <filename>texto.txt</filename>|sort - Faz a mesma coisa
que o primeiro exemplo, só que neste caso a saída do comando
<command>cat é redirecionado a entrada padrão do comando
<command>sort.


<listitem>

<literal>sort -f <filename>texto.txt</filename> - Ignora diferenças
entre letras maiúsculas e minúsculas durante a organização.


<listitem>

<literal>sort +1 -3 texto.txt - Organiza o arquivo
<filename>texto.txt</filename> usando como referência a segunda até a quarta
palavra (segundo ao quarto campo) que constam naquela linha.


<listitem>

<literal>sort -t : +2 -3 passwd - Organiza o arquivo
<filename>passwd</filename> usando como referência a terceira até a quarta
palavra (terceiro ao quarto campo).  Note que a opção <literal>-t
especifica o caracter ":" como delimitador de campos ao invés do espaço.  Neste
caso, o que estiver após ":" será considerado o próximo campo.



<!-- ]]> -->



 cmdv-tail">###tail

Mostra as linhas finais de um arquivo texto.


<command>tail [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>-c [numero]
<listitem>

Mostra o [numero] de bytes do final do arquivo.



<varlistentry>
<term>-n [numero]
<listitem>

Mostra o [numero] de linhas do final do arquivo.



<varlistentry>
<term>-f
<listitem>

Mostra continuamente linhas adicionadas no final do arquivo.



</variablelist>
<!-- ]]> -->

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>tail teste.txt, <literal>tail -n 20 teste.txt.

<!-- ]]> -->



 cmdv-time">###time

Mede o tempo gasto para executar um processo (programa).


<command>time [**comando**]

<!-- [ %OPCOES [ -->

Onde: **comando** é o comando/programa que deseja medir o
tempo gasto para ser concluído.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>time ls, <literal>time find / -name
crontab.

<!-- ]]> -->



 cmdv-touch">###touch

Muda a data e hora que um arquivo foi criado.  Também pode ser usado para criar
arquivos vazios.  
<!-- [ %DESCRICAOD [ --> Caso o <command>touch seja usado com arquivos que
não existam, por padrão ele criará estes arquivos. <!-- ]]> -->


<command>touch [**opções**]
[**arquivos**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivos**
<listitem>

Arquivos que terão sua data/hora modificados.



<varlistentry>
<term>**opções**
<term>-t MMDDhhmm[ANO.segundos]
<listitem>

Usa Mês (MM), Dias (DD), Horas (hh), minutos (mm) e opcionalmente o ANO e
segundos para modificação do(s) arquivos ao invés da data e hora atual.



<varlistentry>
<term>-a, --time=atime
<listitem>

Faz o <command>touch mudar somente a data e hora do acesso ao
arquivo.



<varlistentry>
<term>-c, --no-create
<listitem>

Não cria arquivos vazios, caso os **arquivos** não existam.



<varlistentry>
<term>-m, --time=mtime
<listitem>

Faz o <command>touch mudar somente a data e hora da modificação.



<varlistentry>
<term>-r [arquivo]
<listitem>

Usa as horas no [arquivo] como referência ao invés da hora atual.



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

<literal>touch teste - Cria o arquivo <filename>teste</filename> caso
ele não existir.


<listitem>

<literal>touch -t 10011230 teste - Altera da data e hora do arquivo
para 01/10 e 12:30.


<listitem>

<literal>touch -t 120112301999.30 teste - Altera da data, hora ano, e
segundos do arquivo para 01/12/1999 e 12:30:30.


<listitem>

<literal>touch -t 12011200 * - Altera a data e hora do arquivo para
01/12 e 12:00.



<!-- ]]> -->



 cmdv-uptime">###uptime

Mostra o tempo de execução do sistema desde que o computador foi ligado.


<command>uptime




 cmdv-dmesg">###dmesg

Mostra as mensagens de inicialização do kernel.  São mostradas as mensagens da
última inicialização do sistema.

<!-- [ %EXEMPLO [ -->

<command>dmesg | less

<!-- ]]> -->



 cmdv-mesg">###mesg

Permite ou não o recebimentos de requisições de <command>talk de
outros usuários.


<command>mesg [**y/n**]

<!-- [ %OPCOES [ -->

Onde: **y** permite que você receba "talks" de outros
usuários.

<!-- ]]> -->

Digite <literal>mesg para saber se você pode ou não receber "talks"
de outros usuários.  Caso a resposta seja "n" você poderá enviar um talk para
alguém mas o seu sistema se recusará em receber talks de outras pessoas.


É interessante colocar o comando <literal>mesg y em seu arquivo de
inicialização <filename>.bash_profile</filename> para permitir o recebimento de
"talks" toda vez que entrar no sistema.


Para detalhes sobre como se comunicar com outros usuários, veja o comando <xref linkend="cmdn-talk"/>.




 cmdv-echo">###echo

Mostra mensagens.  Este comando é útil na construção de scripts para mostrar
mensagens na tela para o usuário acompanhar sua execução.


<command>echo [**mensagem**]


A opção <literal>-n pode ser usada para que não ocorra o salto de
linha após a mensagem ser mostrada.




 cmdv-su">###su

Permite o usuário mudar sua identidade para outro usuário sem fazer o logout.
<!-- [ %DESCRICAOD [ --> Útil para executar um programa ou comando como root sem ter que 
abandonar a seção atual. <!-- ]]> -->

<!-- [ %OPCOES [ -->

<command>su [**usuário**] [**-c comando**]


Onde: **usuário** é o nome do usuário que deseja usar para
acessar o sistema.  Se não digitado, é assumido o usuário
<literal>root.  Caso seja especificado **-c
comando**, executa o comando sob o usuário especificado.

<!-- ]]> -->

Será pedida a senha do superusuário para autenticação.  Digite
<literal>exit quando desejar retornar a identificação de usuário
anterior.




 cmdv-sync">###sync

Grava os dados do cache de disco na memória RAM para todos os discos rígidos e
flexíveis do sistema.  
<!-- [ %DESCRICAOD [ --> O cache um mecanismo de aceleração que permite que um
arquivo seja armazenado na memória ao invés de ser imediatamente gravado no
disco, quando o sistema estiver ocioso, o arquivo é gravado para o disco.  O
<command>GNU/Linux procura utilizar toda memória RAM disponível para
o cache de programas acelerando seu desempenho de leitura/gravação. <!-- ]]> -->


<literal>sync


O uso do <command>sync é útil em disquetes quando gravamos um
programa e precisamos que os dados sejam gravados imediatamente para retirar o
disquete da unidade.  Mas o método recomendado é especificar a opção
<literal>sync durante a montagem da unidade de disquetes (para
detalhes veja <xref linkend="disc-fstab"/>.




 cmdv-uname">###uname

Retorna o nome e versão do kernel atual.


<literal>uname




 cmdv-reboot">###reboot

Reinicia o computador.




 cmdv-shutdown">###shutdown

Desliga/reinicia o computador imediatamente ou após determinado tempo
(programável) de forma segura.  
<!-- [ %DESCRICAOD [ --> Todos os usuários do sistema são avisados que o
computador será desligado .  Este comando somente pode ser executado pelo
usuário root ou quando é usada a opção <literal>-a pelos usuários
cadastrados no arquivo <filename>/etc/shutdown.allow</filename> que estejam
logados no console virtual do sistema. <!-- ]]> -->


<command>shutdown [**opções**] [**hora**]
[**mensagem**]

<!-- [ %OPCOES [ -->
<variablelist>
<varlistentry>
<term>**hora**
<listitem>

Momento que o computador será desligado.  Você pode usar
<literal>HH:MM para definir a hora e minuto, <literal>MM
para definir minutos, <literal>+SS para definir após quantos
segundos, ou <literal>now para imediatamente (equivalente a +0).


O <command>shutdown criará o arquivo
<filename>/etc/nologin</filename> para não permitir que novos usuários façam
login no sistema (com excessão do root).  Este arquivo é removido caso a
execução do <command>shutdown seja cancelada (opção -c) ou após o
sistema ser reiniciado.



<varlistentry>
<term>**mensagem**
<listitem>

Mensagem que será mostrada a todos os usuários alertando sobre o
reinicio/desligamento do sistema.



<varlistentry>
<term>**opções**
<term>-h
<listitem>

Inicia o processo para desligamento do computador.



<varlistentry>
<term>-r
<listitem>

Reinicia o sistema



<varlistentry>
<term>-c
<listitem>

Cancela a execução do <command>shutdown.  Você pode acrescentar uma
mensagem avisando aos usuários sobre o fato.




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-a
<listitem>

Permite que os nomes de usuários contidos no arquivo
<filename>/etc/shutdown.allow</filename> possam utilizar o
<command>shutdown para reinicializar/desligar o sistema.  Deve ser
colocado um nome de usuário por linha.  O limite máximo de usuários neste
arquivo é de 32.


Este arquivo é útil quando o <command>shutdown é usado para controlar
o pressionamento das teclas <literal>CTRL+ALT+DEL no
<filename>/etc/inittab</filename>.



<varlistentry>
<term>-k
<listitem>

Simula o desligamento/reinicio do sistema, enviando mensagem aos usuários.



<varlistentry>
<term>-f
<listitem>

Não executa a checagem do sistema de arquivos durante a inicialização do
sistema.  Este processo é feito gravando-se um arquivo
<filename>/fastboot</filename> que é interpretado pelos scripts responsáveis
pela execução do <command>fsck durante a inicialização do sistema.



<varlistentry>
<term>-F
<listitem>

Força a checagem do sistema de arquivos durante a inicialização.  É gravado um
arquivo chamado <filename>/forcefsck</filename> que é interpretado pelos
scripts responsáveis pela execução do <command>fsck durante a
inicialização do sistema.



<varlistentry>
<term>-n
<listitem>

Faz com que o <command>shutdown ignore a execução do
<command>init fechando todos os processos.



<varlistentry>
<term>-t [num]
<listitem>

Faz com que o <command>shutdown envie um sinal de término aos
processos e aguarde [num] segundos antes de enviar o sinal KILL.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->


O <command>shutdown envia uma mensagem a todos os usuários do sistema
alertando sobre o desligamento durante os 15 minutos restantes e assim permite
que finalizem suas tarefas.  Após isto, o <command>shutdown muda o
nível de execução através do comando <command>init para 0
(desligamento), 1 (modo monousuário), 6 (reinicialização).  É recomendado
utilizar o símbolo "&amp;" no final da linha de comando para que o
<command>shutdown seja executado em segundo plano.

<!-- [ %OBS [ -->

Quando restarem apenas 5 minutos para o reinicio/desligamento do sistema, o
programa <command>login será desativado, impedindo a entrada de novos
usuários no sistema.


O programa <command>shutdown pode ser chamado pelo
<command>init através do pressionamento da combinação das teclas de
reinicialização <literal>CTRL+ALT+DEL alterando-se o arquivo
<filename>/etc/inittab</filename>.  Isto permite que somente os usuários
autorizados (ou o root) possam reinicializar o sistema.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

<literal>"shutdown -h now" - Desligar o computador imediatamente.


<listitem>

<literal>"shutdown -r now" - Reinicia o computador imediatamente.


<listitem>

<literal>"shutdown 19:00 A manutenção do servidor será iniciada às
19:00" - Faz o computador entrar em modo monousuário (init 1) às
19:00 enviando a mensagem **A manutenção do servidor será iniciada às
19:00** a todos os usuários conectados ao sistema.


<listitem>

<literal>"shutdown -r 15:00 O sistema será reiniciado às 15:00 horas"
- Faz o computador ser reiniciado (init 6) às 15:00 horas enviando a mensagem
**O sistema será reiniciado às 15:00 horas** a todos os
usuários conectados ao sistema.


<listitem>

<literal>shutdown -r 20 - Faz o sistema ser reiniciado após 20
minutos.


<listitem>

<literal>shutdown -c - Cancela a execução do
<command>shutdown.


<!-- [ %INTERMEDIARIO [ -->
<listitem>

<literal>shutdown -t 30 -r 20 - Reinicia o sistema após 20 minutos,
espera 30 segundos após o sinal de término para enviar o sinal KILL a todos os
programas abertos.


<!-- ]]> -->

<!-- ]]> -->



 cmdv-wc">###wc

Conta o número de palavras, bytes e linhas em um arquivo ou entrada padrão.  
<!-- [ %DESCRICAOD [ --> Se as opções forem omitidas, o <command>wc mostra 
a quantidade de linhas, palavras, e bytes. <!-- ]]> -->


<command>wc [**opções**]
[**arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivo**
<listitem>

Arquivo que será verificado pelo comando <command>wc.



<varlistentry>
<term>**opções**
<term>-c, --bytes
<listitem>

Mostra os bytes do arquivo.



<varlistentry>
<term>-w, --words
<listitem>

Mostra a quantidade de palavras do arquivo.



<varlistentry>
<term>-l, --lines
<listitem>

Mostra a quantidade de linhas do arquivo.



</variablelist>
<!-- ]]> -->
<!-- [ %OBS [ -->

A ordem da listagem dos parâmetros é única, e modificando a posição das opções
não modifica a ordem que os parâmetros são listados.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo:

<itemizedlist>
<listitem>

<literal>wc /etc/passwd - Mostra a quantidade de linhas, palavras e
letras (bytes) no arquivo <filename>/etc/passwd</filename>.


<listitem>

<literal>wc -w /etc/passwd - Mostra a quantidade de palavras.


<listitem>

<literal>wc -l /etc/passwd - Mostra a quantidade de linhas.


<listitem>

<literal>wc -l -w /etc/passwd - Mostra a quantidade de linhas e
palavras no arquivo <filename>/etc/passwd</filename>.



<!-- ]]> -->



 cmdv-seq">###seq

Imprime uma seqüência de números começando em [primeiro] e terminando em
[último], utilizando [incremento] para avançar.


<command>seq [**opções**] [**primeiro**]
[**incremento**] [**último**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**primeiro**
<listitem>

Número inicial da seqüência.



<varlistentry>
<term>**incremento**
<listitem>

Número utilizado para avançar na seqüência.



<varlistentry>
<term>**último**
<listitem>

Número final da seqüência.



<varlistentry>
<term>**opções**
<term>-f, --format=[formato]
<listitem>

Formato de saída dos números da seqüência.  Utilize o estilo do printf para
ponto flutuante (valor padrão: %g).



<varlistentry>
<term>-s, --separator=[string]
<listitem>

Usa [string] para separar a seqüência de números (valor padrão: \n).



<varlistentry>
<term>-w, --equal-width
<listitem>

Insere zeros na frente dos números mantendo a seqüência alinhada.



</variablelist>
<!-- ]]> -->
<!-- [ %OBS [ -->

Observações:

<itemizedlist>
<listitem>

Se [primeiro] ou [incremento] forem omitidos, o valor padrão 1 será utilizado.


<listitem>

Os números recebidos são interpretados como números em ponto flutuante.


<listitem>

[incremento] deve ser positivo se [primeiro] for menor do que o último, e
negativo caso contrário.


<listitem>

Quando utilizarmos a opção --format, o argumento deve ser exatamente %e, %f ou
%g.



<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos: <literal>seq 0 2 10, <literal>seq -w 0 10,
<literal>seq -f%f 0 10, <literal>seq -s", " 0 10

<!-- ]]> -->



	<!-- [ %INTERMEDIARIO [ -->
 cmdv-chattr">###chattr

Modifica atributos de arquivos/diretórios.  Não confunda atributos de arquivo
com permissões de acesso (<xref linkend="perm"/>), os atributos são diferentes
e definem outras características especiais para os arquivos/diretórios
especificados.


<command>chattr [**opções**] [**atributos**] [**arquivos/diretórios**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivos/diretórios**
<listitem>

Arquivos/Diretórios que terão os atributos modificados.  Podem ser usados
coringas



<varlistentry>
<term>**opções**
<term>-R
<listitem>

Modifica atributos em subdiretórios



<varlistentry>
<term>-V
<listitem>

Mostra detalhes sobre a modificação de atributos.



<varlistentry>
<term>**atributos**
<listitem>

Os atributos de arquivos/diretórios podem ser especificados da seguinte
maneira:

<itemizedlist>
<listitem>

<literal>+ - Adiciona o atributo


<listitem>

<literal>- - Remove o atributo


<listitem>

<literal>= - Define o atributo exatamente como especificado




Os atributos são os seguintes:

<itemizedlist>
<listitem>

<literal>A - Não modifica a hora de acesso de arquivos.  Poder
aumentar consideravelmente a performance em Notebooks devido a diminuição de
I/O no disco rígido.  Quando especificada em diretórios, faz com que todos os
arquivos e subdiretórios residentes nele não tenham a hora de acesso
modificada.


Este atributo funciona apenas em kernels 2.2 e superiores


<listitem>

<literal>a - Append-Only - Arquivos com este atributo podem somente
ser gravados em modo incrementais (o conteúdo poderá somente ser adicionado ao
final do arquivo).  Eles não poderão ser removidos, renomeados e novos links
não poderão ser criados para estes arquivos.


Em diretórios faz com que os arquivos sejam apenas adicionados.  Somente o root
pode especificar ou retirar este atributo.


<listitem>

<literal>c - Permite compactação nos arquivos especificados de forma
transparente para o usuário.  Durante a leitura, o kernel retorna dados
descompactados e durante a gravação os dados são compactados e gravados no
disco.


Este atributo ainda não foi totalmente implementado no código atual do kernel.


<listitem>

<literal>d - Este atributo não é usado pelo kernel, mas faz com que o
programa <command>dump evitar backup dos arquivos marcados com este
atributo.


<listitem>

<literal>i - Imutável - Arquivos imutáveis não podem ser modificados,
os dados também não podem ser gravados para estes arquivos, não podem ser
removidos, renomeados.  Até mesmo o usuário root não poderá modificar estes
arquivos.


Em diretórios, faz com que arquivos não possam ser adicionados ou apagados.
Somente o usuário root pode especificar ou retirar este atributo.


<listitem>

<literal>s - O arquivo especificado é marcado como "apagamento
seguro"; quando o arquivo é apagado, seus blocos são zerados e gravados de
volta no disco (eliminando qualquer possibilidade de recuperação).


<listitem>

<literal>S - Faz a gravação imediatamente para o arquivo
especificado.  É como especificar a opção "sync" na montagem do sistema de
arquivos ext2, mas afeta somente os arquivos especificados.  Não tem efeito em
diretórios.


<listitem>

<literal>u - O arquivo especificado é marcado como recuperável.
Quando o arquivo é apagado, seu conteúdo é salvo para permitir futura
recuperação.


Este atributo ainda não foi implementado totalmente no código atual do kernel.





</variablelist>
<!-- ]]> -->

Os atributos de arquivos/diretórios são visualizados através do utilitário
<command>lsattr.  Existem patches para os kernels da série 2.2 que
adicionam o suporte experimental aos atributos "c" e "u".

<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

<literal>chattr +AacdiSsu teste.txt - Adiciona todos os atributos


<listitem>

<literal>chattr =ASs teste.txt - Define os atributos para "ASs"


<listitem>

<literal>chattr +i -A teste.txt - Retira o atributo "A" e adiciona
"i"


<listitem>

<literal>chattr = teste.txt - Retira todos os atributos



<!-- ]]> -->



 cmdv-lsattr">###lsattr

Lista atributos de um arquivo/diretório.  Os atributos podem ser modificados
através do comando <command>chattr.


<command>lsattr [**opções**] [**arquivos/diretórios**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivos/diretórios**
<listitem>

Arquivos/diretórios que deseja listar os atributos.  Podem ser usados coringas.



<varlistentry>
<term>**opções**
<term>-a
<listitem>

Lista todos os arquivos, incluindo ocultos (iniciando com um ".").



<varlistentry>
<term>-d
<listitem>

Lista os atributos de diretórios ao invés de listar os arquivos que ele contém.



<varlistentry>
<term>-R
<listitem>

Faz a listagem em diretórios e subdiretórios.



<varlistentry>
<term>-v
<listitem>

Mostra versões dos arquivos.



</variablelist>
<!-- ]]> -->

Caso seja especificado sem parâmetros, o <command>lsattr listará os
atributos de todos os arquivos e diretórios do diretório atual.  O
<command>lsattr mostrará mensagens de erro caso seja usado em um
diretório de pontos de montagem ou arquivos que não sejam
**ext2**.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>lsattr -d, <literal>lsattr -R,
<literal>lsattr -R *.txt

<!-- ]]> -->



 cmdv-cut">###cut

Mostra seções de cada linha do arquivo dependendo das opções passadas ao
programa.


<command>cut [**opções**] [**arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivo**
<listitem>

Arquivo que será verificado pelo comando <command>cut.



<varlistentry>
<term>**opções**
<term>-b, --bytes [bytes]
<listitem>

Mostra somente a lista de [bytes] do arquivo.



<varlistentry>
<term>-c, --characters [numero]
<listitem>

Mostra somente o [número] de caracteres no arquivo.  É semelhante a opção "-b"
mas tabs e espaços são tratados como qualquer caracter.



<varlistentry>
<term>-f, --field [campos]
<listitem>

Mostra somente a lista de [campos].



<varlistentry>
<term>-d, --delimite [delimitador]
<listitem>

Para uso com a opção -f, os campos são separados pelo primeiro caracter em
[delimitador] ao invés de tabulações.



<varlistentry>
<term>-s
<listitem>

Para uso com a opção -f, somente mostra linhas que contém o caracter separador
de campos.



</variablelist>
<!-- ]]> -->

Devem ser especificadas opções para o funcionamento deste comando.  Os bytes,
campos e delimitadores podem ser especificados através de intervalos de
caracteres (usando a-z), através de vírgulas (a,b,d) ou da combinação entre
eles.

<!-- [ %EXEMPLO [ -->
<itemizedlist>
<listitem>

<literal>cut -b 1,3 /etc/passwd - Pega a primeira e terceira letra
(byte) de cada linha do arquivo <filename>/etc/passwd</filename>


<listitem>

<literal>cut -b 1,3-10 /etc/passwd - Pega a primeira letra (byte) e
terceira a décima letra de cada linha do arquivo
<filename>/etc/passwd</filename>.


<listitem>

<literal>cut -c 1,3-10 /etc/passwd - Pega o primeiro caracter e
terceiro ao décimo caracter de cada linha do arquivo
<filename>/etc/passwd</filename>.



<!-- ]]> -->



 cmdv-cmp">###cmp

Compara dois arquivos de qualquer tipo (binário ou texto).  
<!-- [ %DESCRICAOD [ --> Os dois arquivos especificados serão comparado e caso exista 
diferença entre eles, é mostrado o número da linha e byte onde ocorreu a primeira 
diferença na saída padrão (tela) e o programa retorna o código de saída 1. <!-- ]]> -->


<command>cmp [**arquivo1**] [**arquivo2**] [**opções**]

<!-- [ %OPCOES [ -->

Opções:

<variablelist>
<varlistentry>
<term>**arquivo1/arquivo2**
<listitem>

Arquivos que serão comparados.



<varlistentry>
<term>**opções**
<term>-l
<listitem>

Mostra o número do byte (hexadecimal) e valores diferentes de bytes (octal)
para cada diferença.



<varlistentry>
<term>-s
<listitem>

Não mostra nenhuma diferença, só retorna o código de saída do programa.



</variablelist>
<!-- ]]> -->

Use o comando <command>zcmp para comparar diretamente arquivos
binários/texto compactados com <command>gzip.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>cmp teste.txt teste1.txt.

<!-- ]]> -->



 cmdv-dirname">###dirname

Obtém o nome do diretório através do caminho passado ao programa.


<command>dirname [**diretório/arquivo**]

<!-- [ %EXEMPLO [ -->

<literal>dirname /usr/bin/dirname, <literal>dirname /tmp/*.

<!-- ]]> -->



 cmdv-diff">###diff

Compara dois arquivos e mostra as diferenças entre eles.  O comando
<command>diff é usado somente para a comparação de arquivos em
formato texto.  
<!-- [ %DESCRICAOD [ --> As diferenças encontradas podem ser redirecionadas para um
arquivo que poderá ser usado pelo comando <command>patch para aplicar
as alterações em um arquivo que não contém as diferenças.  Isto é útil para
grandes textos porque é possível copiar somente as modificações (geradas
através do diff, que são muito pequenas) e aplicar no arquivo para atualiza-lo
(através do <command>patch) ao invés de copiar a nova versão.  Este é
um sistema de atualização muito usado na atualização dos código fonte do kernel
do <command>Linux. <!-- ]]> -->


<command>diff [**diretório1/arquivo1**] [**diretório2/arquivo2**] 
[**opções**]

<!-- [ %OPCOES [ -->

Opções:

<variablelist>
<varlistentry>
<term>**diretório1/arquivo1 diretório2/arquivo2**
<listitem>

Arquivos /diretórios que serão comparados.  Normalmente é usado como primeiro
arquivo/diretório o mais antigo e o mais novo como segundo.



<varlistentry>
<term>**opções**
<term>-lines [num]
<listitem>

Gera a diferença com [num] linhas de contexto.  Por padrão o
<command>diff gera um arquivo com 2 linhas que é o mínimo necessário
para o correto funcionamento do <command>patch.



<varlistentry>
<term>-a
<listitem>

Compara os dois arquivos como arquivos texto.



<varlistentry>
<term>-b
<listitem>

Ignora espaços em branco como diferenças.



<varlistentry>
<term>-B
<listitem>

Ignora linhas em branco inseridas ou apagadas nos arquivos.



<varlistentry>
<term>-i
<listitem>

Ignora diferenças entre maiúsculas e minúsculas nos arquivos.



<varlistentry>
<term>-H
<listitem>

Usa análise heurística para verificar os arquivos.



<varlistentry>
<term>-N
<listitem>

Em uma comparação de diretórios, se o arquivo apenas existe em um diretório,
trata-o como presente mas vazio no outro diretório.



<varlistentry>
<term>-P
<listitem>

Em uma comparação de diretórios, se o arquivos apenas existe no segundo
diretório, trata-o como presente mas vazio no primeiro diretório.



<varlistentry>
<term>-q
<listitem>

Mostra somente se os dois arquivos possuem diferenças.  Não mostra as
diferenças entre eles.



<varlistentry>
<term>-r
<listitem>

Compara diretórios e sub-diretórios existentes.



<varlistentry>
<term>-S [nome]
<listitem>

Inicia a comparação de diretórios pelo arquivo [nome].  É útil quando
cancelamos uma comparação.



<varlistentry>
<term>-t
<listitem>

Aumenta a tabulação das diferenças encontradas.



<varlistentry>
<term>-u
<listitem>

Usa o formato de comparação unificado.



</variablelist>
<!-- ]]> -->

Use o comando <command>zdiff para comparar diretamente arquivos
compactados pelo utilitário <command>gzip


Use o comando <command>sdiff para visualizar as linhas diferentes
entre os dois arquivos em formato texto simples.

<!-- [ %EXEMPLO [ -->

Exemplo:

<itemizedlist>
<listitem>

<literal>diff texto.txt texto1.txt - Compara o arquivo
<filename>texto.txt</filename> com <filename>texto1.txt</filename> e exibe suas
diferenças na tela.


<listitem>

<literal>diff -Bu texto.txt texto1.txt - Compara o arquivo
<filename>texto.txt</filename> com <filename>texto1.txt</filename> ignorando
linhas em branco diferentes entre os dois arquivos e usando o formato
unificado.


<listitem>

<literal>diff texto.txt texto1.txt &gt;texto.diff - Compara o arquivo
<filename>texto.txt</filename> com <filename>texto1.txt</filename> e gera um
arquivo chamado <filename>texto.diff</filename> contendo a diferença entre
eles.  Este arquivo poderá ser usado pelo <command>patch para aplicar
as diferenças existente entre os dois no arquivo
<filename>texto.txt</filename>.


<listitem>

<literal>diff -r /usr/src/linux-2.2.13 /usr/src/linux-2.2.14
&gt;patch-2.2.14.diff - Compara o diretório e sub-diretórios
<filename>linux-2.2.13</filename> e <filename>linux-2.2.14</filename> e grava
as diferenças entre eles no arquivo <filename>patch-2.2.14.diff</filename>.



<!-- ]]> -->



 cmdv-pr">###pr

Página arquivos texto ou a entrada padrão para impressão.  
<!-- [ %DESCRICAOD [ --> Este comando faz a
paginação de um arquivo texto e opcionalmente ajusta o número de colunas e
mostra o resultado na saída padrão. <!-- ]]> -->


<command>pr [**opções**] [**arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**arquivo**
<listitem>

Arquivo que será paginado para impressão.



<varlistentry>
<term>**opções**
<term>+[NUM]
<listitem>

Inicia a numeração de páginas na página [PAGINA]



<varlistentry>
<term>-[NUM]
<listitem>

Mostra a saída com [NUM] colunas.



<varlistentry>
<term>-c
<listitem>

Imprime o caracter CTRL como <literal>"^" na saída padrão.



<varlistentry>
<term>-F, -f
<listitem>

Usa avanço de página ao invés de linhas em branco para separar páginas.



<varlistentry>
<term>-e[caracter][tamanho]
<listitem>

Usa o caracter [caracter] como tabulação (o padrão é tab) e o espaço da
tabulação [tamanho].



<varlistentry>
<term>-h [nome]
<listitem>

Mostra [nome] ao invés do nome do arquivo no cabeçalho.



<varlistentry>
<term>-l [num]
<listitem>

Define o número máximo de linhas por página para [num].



<varlistentry>
<term>-m
<listitem>

Imprime vários arquivos em paralelo, um por coluna.



<varlistentry>
<term>-r
<listitem>

Oculta mensagens de erro de abertura de arquivos.



<varlistentry>
<term>-w [num]
<listitem>

Ajusta a largura da página para [num] colunas (o padrão é 72).



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>pr -l 50 -h "Teste do comando pr" teste.txt.

<!-- ]]> -->



 cmdv-patch">###patch

Atualiza arquivos texto através das diferenças geradas pelo comando
<command>diff.


<command>patch [**opções**] [**arquivo.diff**] ou 
<command>patch [**opções**] &lt; [**arquivo.diff**]


Onde:

<variablelist>
<varlistentry>
<term>**arquivo.diff**
<listitem>

Arquivo contendo as diferenças geradas pelo comando <command>diff.



<varlistentry>
<term>**opções**
<term>-p [num]
<listitem>

Nível do diretório onde o <command>patch será aplicado, se igual a 0,
o <command>patch assume que os arquivos que serão atualizados estão
no diretório atual, se 1, assume que os arquivos que serão atualizado estão no
diretório acima (..), se 2, 2 diretórios acima ...



<varlistentry>
<term>-b
<listitem>

Cria cópias de segurança dos arquivos originais ao aplica o patch.



<varlistentry>
<term>-binary
<listitem>

Lê e grava arquivo usando modo binário.



<varlistentry>
<term>-d [dir]
<listitem>

Muda para o diretório [dir] antes de aplica o patch.



<varlistentry>
<term>-E
<listitem>

Remove arquivos vazios após a aplicação do patch.



<varlistentry>
<term>-n
<listitem>

Interpreta o arquivo de patch como um <filename>.diff</filename> normal.



<varlistentry>
<term>-N
<listitem>

Não desfaz patches já aplicados.



<varlistentry>
<term>-s
<listitem>

Não mostra mensagens de erro.



<varlistentry>
<term>-u
<listitem>

Interpreta o patch em formato unificado.



</variablelist>

As diferenças são aplicadas em arquivos originais gerados pelo comando
<command>diff.  É importante entender os comandos
<command>patch e <command>diff pois são comandos muito
utilizados para desenvolvimento feito por equipes de pessoas.

<!-- [ %EXEMPLO [ -->

Exemplo:

<itemizedlist>
<listitem>

<literal>patch -p0&lt;texto.diff - Aplica as diferenças contidas no
arquivo <filename>texto.diff</filename> nos arquivos originais.


<listitem>

<literal>patch -p0 texto.txt texto.diff - Aplica as diferenças
contidas no arquivo <filename>texto.diff</filename> nos arquivos originais.
Faz a mesma coisa que o comando anterior.



<!-- ]]> -->



 cmdv-whereis">###whereis

Localiza o arquivo que contém uma página de manual.  
<!-- [ %DESCRICAOD [ --> A pesquisa é feita usando-se os caminhos de páginas 
de manuais configuradas no sistema (normalmente o arquivo 
<filename>/etc/manpath.config</filename>). <!-- ]]> -->


<command>whereis [**comando**]

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>whereis ls, <literal>whereis cd.

<!-- ]]> -->



 cmdv-which">###which

Mostra a localização de um arquivo executável no sistema.  
<!-- [ %DESCRICAOD [ --> A pesquisa de
arquivos executáveis é feita através do path do sistema. <!-- ]]> -->
<!-- [ %INICIANTE [ --> Para maiores detalhes, veja <xref linkend="run-path"/>. <!-- ]]> -->


<command>which [**comando**]

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>which ls, <literal>which shutdown,
<literal>which which.

<!-- ]]> -->



 cmdv-zforce">###zforce

Renomeia extensão de arquivos para <filename>.gz</filename>.  
<!-- [ %DESCRICAOD [ --> Este comando é útil quando fazemos downloads de 
arquivos compactados pelo <command>gzip mas que não estão 
identificados pela extensão <filename>.gz</filename>. <!-- ]]> -->


<command>zforce [**arquivos**]


Quando é usado o <command>zforce verifica se o arquivo especificado foi
compactado pelo <command>gzip, caso seja, é verificado se já tem a
extensão <filename>.gz</filename>, caso não tiver, acrescenta a extensão.




 cmdv-gzexe">###gzexe

Cria arquivos compactados <command>gzip auto-extrácteis.  
<!-- [ %DESCRICAOD [ --> Este comando é usado para compactar arquivos executáveis 
que se auto-descompactam assim que são solicitados.  É útil para sistemas 
ou unidades de disco que possuem pouco espaço disponível. <!-- ]]> --> Este comando deve 
somente ser usado para arquivos executáveis.


<command>gzexe [**arquivo**]

<!-- [ %OPCOES [ -->

Onde: **arquivo** é o arquivo executável que será compactado.

<!-- ]]> -->

Quando <command>gzexe é executado, uma cópia do arquivo original é
gravada com o formato <filename>nome_do_arquivo</filename>~.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>gzexe /tmp/teste.

<!-- ]]> -->



 cmdv-znew">###znew

Recompacta arquivos do formato <command>compress
(<filename>.Z</filename>) para o formato <command>gzip
(<filename>.gz</filename>).  Após a re-compactação, os arquivos de origem
<filename>.Z</filename> são apagados.


<command>znew [**opções**] [**arquivo**]


Onde:

<variablelist>
<varlistentry>
<term>**arquivo.Z**
<listitem>

Arquivo compactado pelo <command>compress que será re-compactado para
o <command>gzip.



<varlistentry>
<term>**opções**
<term>-f
<listitem>

Substitui o arquivo <filename>.gz</filename> caso já exista.



<varlistentry>
<term>-t
<listitem>

Teste os novos arquivos criados antes de apagar os arquivos
<filename>.Z</filename>.



<varlistentry>
<term>-v
<listitem>

Mostra o nome e porcentagem de compactação para cada arquivo processado.



<varlistentry>
<term>-9
<listitem>

Usa a máxima compactação.



<varlistentry>
<term>-P
<listitem>

Usa pipes durante a conversão para reduzir o espaço ocupado no disco.  A data e
hora do arquivo não é mantida caso esta opção seja usada.



<varlistentry>
<term>-K
<listitem>

Mantém o arquivo <filename>.Z</filename> caso seja menor que o arquivo
<filename>.gz</filename>.



</variablelist>


	<!-- ]]> -->

