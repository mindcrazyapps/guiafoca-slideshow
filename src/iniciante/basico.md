<!-- Converted by db4-upgrade version 1.0 -->
chapter <!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" ###Explicações Básicas

Este capítulo traz explicações sobre os principais componentes existentes no
computador e do sistema operacional <command>Linux.



 userlevel='inic' basico-hardsoft">###Hardware e Software

**Hardware** - Significa parte física do computador (disquete,
pen-drive, impressoras, monitores, placa mãe, placa de fax, discos rígidos,
etc).


**Software** - São os programas usados no computador (sistema
operacional, processador de textos, planilha, banco de dados, scripts,
comandos, etc).




 userlevel='inic' basico-arquivo">###Arquivos

É onde gravamos nossos dados.  Um arquivo pode conter um texto feito por nós,
uma música, programa, planilha, etc.


Cada arquivo deve ser identificado por um <literal>nome, assim ele
pode ser encontrado facilmente quando desejar usa-lo.  Se estiver fazendo um
trabalho de história, nada melhor que salva-lo com o nome
<filename>historia</filename>.  Um arquivo pode ser binário ou texto (para
detalhes veja <xref linkend="basico-arquivo-bintext"/>).


O <command>GNU/Linux é **Case Sensitive** ou seja,
ele diferencia letras **maiúsculas** e
**minúsculas** nos arquivos.  O arquivo
<filename>historia</filename> é completamente diferente de
<filename>Historia</filename>.  Esta regra também é válido para os
**comandos** e **diretórios**.  Prefira,
sempre que possível, usar letras minúsculas para identificar seus arquivos,
pois quase todos os comandos do sistema estão em
**minúsculas**.


Um arquivo oculto no <command>GNU/Linux é identificado por um "."  no
inicio do nome (por exemplo, <filename>.bashrc</filename>).  Arquivos ocultos
não aparecem em listagens normais de diretórios, deve ser usado o comando
<literal>ls -a para também listar arquivos ocultos.

 basico-arquivo-tipos">###Extensão de arquivos

A extensão serve para identificar o tipo do arquivo.  A extensão são as letras
após um "."  no nome de um arquivo, explicando melhor:

<itemizedlist>
<listitem>

relatório**.txt** - O
<literal>.txt indica que o conteúdo é um arquivo texto.


<listitem>

script**.sh** - Arquivo de
Script (interpretado por <filename>/bin/sh</filename>).


<listitem>

system**.log** - Registro
de algum programa no sistema.


<listitem>

arquivo**.gz** - Arquivo
compactado pelo utilitário <command>gzip.


<listitem>

index**.html** - Página de
Internet (formato Hypertexto).




A extensão de um arquivo também ajuda a saber o que precisamos fazer para
abri-lo.  Por exemplo, o arquivo <filename>relatório.txt</filename> é um texto
simples e podemos ver seu conteúdo através do comando <xref linkend="comandos-cat"/>, já o arquivo <filename>index.html</filename> contém
uma página de Internet e precisaremos de um navegador para poder visualiza-lo
(como o <command>lynx, <command>Firefox ou o
<command>Konqueror).


A extensão (na maioria dos casos) não é requerida pelo sistema operacional
<command>GNU/Linux, mas é conveniente o seu uso para determinarmos
facilmente o tipo de arquivo e que programa precisaremos usar para abri-lo.




 userlevel='inic' basico-arquivo-tamanho">###Tamanho de arquivos

A unidade de medida padrão nos computadores é o <literal>bit.  A um
conjunto de 8 bits nós chamamos de <literal>byte.  Cada
arquivo/diretório possui um tamanho, que indica o espaço que ele ocupa no disco
e isto é medido em <literal>bytes.  O byte representa uma letra.
Assim, se você criar um arquivo vazio e escrever o nome
<literal>Linux e salvar o arquivo, este terá o tamanho de 5 bytes.
Espaços em branco e novas linhas também ocupam bytes.


Além do byte existem as medidas Kbytes, Mbytes, Gbytes.  Os prefixos K (quilo),
M (mega), G (giga), T (tera) etc.  vêem da matemática.  O "K" significa
multiplicar por 10^3, o "M" por 10^6, e assim por diante.  Esta letras servem
para facilitar a leitura em arquivos de grande tamanho.  Um arquivo de 1K é a
mesma coisa de um arquivo de 1024 bytes.  Uma forma que pode inicialmente lhe
ajudar a lembrar: K vem de Kilo que é igual a 1000 - 1Kilo é igual a 1000
gramas certo?.


Da mesma forma 1Mb (ou 1M) é igual a um arquivo de 1024K ou 1.048.576 bytes


1Gb (ou 1G) é igual a um arquivo de 1024Mb ou 1048576Kb ou 1.073.741.824 bytes
(1 Gb é igual a 1.073.741.824 bytes, são muitos números!).  Deu pra notar que é
mais fácil escrever e entender como 1Gb do que 1.073.741.824 bytes :-)


A lista completa em ordem progressiva das unidades de medida é a seguinte:

<screen>
Símbolo	10^	2^	Nome

K	 3	10	Quilo
M	 6	20	Mega
G	 9	30	Giga
T	12	40	Tera
P	15	50	Peta
E	18	60	Eta
Z	21	70	Zetta
Y	24	80	Yotta




 userlevel='inic' basico-arquivo-bintext">###Arquivo texto e binário

Quanto ao tipo, um arquivo pode ser de texto ou binário:

<variablelist>
<varlistentry>
<term><literal>texto
<listitem>

Seu conteúdo é compreendido pelas pessoas.  Um arquivo texto pode ser uma
carta, um script, um programa de computador escrito pelo programador, arquivo
de configuração, etc.



<varlistentry>
<term><literal>binário
<listitem>

Seu conteúdo somente pode ser entendido por computadores.  Contém caracteres
incompreensíveis para pessoas normais.  Um arquivo binário é gerado através de
um arquivo de programa (digitado pela pessoa que o criou, o programador)
através de um processo chamado de <literal>compilação.  Compilação é
basicamente a conversão de um programa em linguagem humana para a linguagem de
máquina.



</variablelist>





 userlevel='inic' basico-diretorio">###Diretório

Diretório é o local utilizado para armazenar conjuntos arquivos para melhor
organização e localização.  O diretório, como o arquivo, também é
"**Case Sensitive**" (diretório <filename>/teste</filename> é
completamente diferente do diretório <filename>/Teste</filename>).

<!-- [ %OBS [ -->

Não podem existir dois arquivos com o <literal>mesmo nome em um
diretório, ou um sub-diretório com um mesmo nome de um arquivo em um mesmo
diretório.

<!-- ]]> -->

Um diretório nos sistemas <command>Linux/UNIX são especificados por
uma "**/**" e não uma "**\**" como é feito no
<command>DOS.  Para detalhes sobre como criar um diretório, veja o
comando <command>mkdir (<xref linkend="comando-mkdir"/>).



 userlevel='inic' basico-diretorio-raiz">###Diretório Raíz

Este é o diretório principal do sistema.  Dentro dele estão todos os diretórios
do sistema.  O diretório Raíz é representado por uma "**/**",
assim se você digitar o comando <literal>cd / você estará acessando
este diretório.


Nele estão localizados outros diretórios como o <filename>/bin, /sbin, /usr,
/usr/local, /mnt, /tmp, /var, /home,</filename> etc.  Estes são chamados de
**sub-diretórios** pois estão dentro do diretório
"<filename>/</filename>".  A estrutura de **diretórios** e
**sub-diretórios** pode ser identificada da seguinte maneira:

<itemizedlist>
<listitem>

/


<listitem>

/bin


<listitem>

/sbin


<listitem>

/usr


<listitem>

/usr/local


<listitem>

/mnt


<listitem>

/tmp


<listitem>

/var


<listitem>

/home




A estrutura de diretórios também é chamada de <literal>Árvore de
Diretórios porque é parecida com uma **árvore** de
cabeça para baixo.  

<!-- [ %OBS [ -->
Cada diretório do sistema tem seus respectivos arquivos que
são armazenados conforme regras definidas pela **FHS**
(**FileSystem Hierarchy Standard - Hierarquia Padrão do Sistema de
Arquivos**) versão 2.0, definindo que tipo de arquivo deve ser
armazenado em cada diretório.

<!-- ]]> -->



 userlevel='inic' basico-diretorio-atual">###Diretório atual

É o diretório em que nos encontramos no momento.  Você pode digitar
<literal>pwd (veja <xref linkend="comando-pwd"/>) para verificar qual
é seu diretório atual.


O diretório atual também é identificado por um "."  (ponto).  O comando comando
<literal>ls . pode ser usado para listar seus arquivos (é claro que
isto é desnecessário porque se não digitar nenhum diretório, o comando
<command>ls listará o conteúdo do diretório atual).




 userlevel='inic' basico-diretorio-home">###Diretório home

Também chamado de diretório de usuário.  Em sistemas
<command>GNU/Linux cada usuário (inclusive o root) possui seu próprio
diretório onde poderá armazenar seus programas e arquivos pessoais.


Este diretório está localizado em <filename>/home/[login]</filename>, neste
caso se o seu login for "joao" o seu diretório home será
<filename>/home/joao</filename>.  O diretório home também é identificado por um
<literal>~(til), você pode digitar tanto o comando <literal>ls
/home/joao como <literal>ls ~ para listar os arquivos de
seu diretório home.


O diretório home do usuário root (na maioria das distribuições
<command>GNU/Linux) está localizado em <filename>/root</filename>.


Dependendo de sua configuração e do número de usuários em seu sistema, o
diretório de usuário pode ter a seguinte forma:
<filename>/home/[1letra_do_nome]/[login]</filename>, neste caso se o seu login
for "joao" o seu diretório home será <filename>/home/j/joao</filename>.



 userlevel='inic' basico-diretorio-superior">###Diretório Superior

O diretório superior (Upper Directory) é identificado por <literal>..
(2 pontos).


Caso estiver no diretório <filename>/usr/local</filename> e quiser listar os
arquivos do diretório <filename>/usr</filename> você pode digitar, <literal>ls
.. Este recurso também pode ser usado para copiar, mover
arquivos/diretórios, etc.




 userlevel='inic' basico-diretorio-anterior">###Diretório Anterior

O diretório anterior é identificado por "-".  É útil para retornar ao último
diretório usado.


Se estive no diretório <filename>/usr/local</filename> e digitar <literal>cd
/lib, você pode retornar facilmente para o diretório
<filename>/usr/local</filename> usando <literal>cd -.




 userlevel='inic' basico-diretorio-caminho">###Caminho na estrutura de diretórios

São os diretórios que teremos que percorrer até chegar no arquivo ou diretório
que que procuramos.  Se desejar ver o arquivo <filename>/etc/hosts</filename>
você tem duas opções:

<orderedlist numeration="arabic">
<listitem>

Mudar o diretório padrão para <filename>/etc</filename> com o comando
<literal>cd /etc e usar o comando <literal>cat hosts


<listitem>

Usar o comando <command>"cat" especificando o caminho completo na
estrutura de diretórios e o nome de arquivo: <literal>cat /etc/hosts.


</orderedlist>

As duas soluções acima permitem que você veja o arquivo
<filename>GPL</filename>.  A diferença entre as duas é a seguinte:

<itemizedlist>
<listitem>

Na primeira, você muda o diretório padrão para
<filename>/usr/doc/copyright</filename> (confira digitando
<literal>pwd) e depois o comando <literal>cat GPL.  Você
pode ver os arquivos de <filename>/usr/doc/copyright</filename> com o comando
<command>"ls".


<filename>/usr/doc/copyright</filename> é o caminho de diretório que devemos
percorrer para chegar até o arquivo <filename>GPL</filename>.


<listitem>

Na segunda, é digitado o caminho completo para o <command>"cat"
localizar o arquivo <filename>GPL</filename>: <literal>cat
/usr/doc/copyright/GPL.  Neste caso, você continuará no diretório
padrão (confira digitando <literal>pwd).  Digitando
<literal>ls, os arquivos do diretório atual serão listados.




O **caminho de diretórios** é necessário para dizer ao sistema
operacional onde encontrar um arquivo na "árvore" de diretórios.




<!-- [ %EXEMPLO [ -->
 userlevel='inic' basico-diretorio-exemplo">###Exemplo de diretório

Um exemplo de diretório é o seu diretório de usuário, todos seus arquivos
essenciais devem ser colocadas neste diretório.  Um diretório pode conter outro
diretório, isto é útil quando temos muitos arquivos e queremos melhorar sua
organização.  Abaixo um exemplo de uma empresa que precisa controlar os
arquivos de Pedidos que emite para as fábricas:


/pub/vendas - diretório principal de vendas /pub/vendas/mes01-1999 - diretório
contendo vendas do mês 01/1999 /pub/vendas/mes02-2009 - diretório contendo
vendas do mês 02/2009 /pub/vendas/mes01-2010 - diretório contendo vendas do mês
03/2010


<filename>mes01-99, mes02-2009, mes01-2010</filename> são diretórios usados
para armazenar os arquivos de pedidos do mês e ano correspondente.  Isto é
essencial para organização, pois se todos os pedidos fossem colocados
diretamente no diretório vendas, seria muito difícil encontrar o arquivo do
cliente "João" do mês 01/2009.


Você deve ter reparado que usei a palavra **sub-diretório**
para mes01-1999, mes02-2009 e mes01-2010, porque que eles estão dentro do
diretório vendas.  Da mesma forma, <filename>vendas</filename> é um
sub-diretório de <filename>pub</filename>.


<!-- ]]> -->


 userlevel='inic' basico-diretorio-estrutura">###Estrutura básica de diretórios do Sistema Linux

O sistema <command>GNU/Linux possui a seguinte estrutura básica de
diretórios organizados segundo o FHS (Filesystem Hierarchy Standard):

<variablelist>
<varlistentry>
<term><filename>/bin</filename>
<listitem>

Contém arquivos programas do sistema que são usados com freqüência pelos
usuários.



<varlistentry>
<term><filename>/boot</filename>
<listitem>

Contém arquivos necessários para a inicialização do sistema.



<varlistentry>
<term><filename>/cdrom</filename>
<listitem>

Ponto de montagem da unidade de CD-ROM.



<varlistentry>
<term><filename>/media</filename>
<listitem>

Ponto de montagem de dispositivos diversos do sistema (rede, pen-drives, CD-ROM
em distribuições mais novas).



<varlistentry>
<term><filename>/dev</filename>
<listitem>

Contém arquivos usados para acessar dispositivos (periféricos) existentes no
computador.



<varlistentry>
<term><filename>/etc</filename>
<listitem>

Arquivos de configuração de seu computador local.



<varlistentry>
<term><filename>/floppy</filename>
<listitem>

Ponto de montagem de unidade de disquetes



<varlistentry>
<term><filename>/home</filename>
<listitem>

Diretórios contendo os arquivos dos usuários.



<varlistentry>
<term><filename>/lib</filename>
<listitem>

Bibliotecas compartilhadas pelos programas do sistema e módulos do kernel.



<varlistentry>
<term><filename>/lost+found</filename>
<listitem>

Local para a gravação de arquivos/diretórios recuperados pelo utilitário
<command>fsck.ext2.  Cada partição possui seu próprio diretório
<filename>lost+found</filename>.



<varlistentry>
<term><filename>/mnt</filename>
<listitem>

Ponto de montagem temporário.



<varlistentry>
<term><filename>/proc</filename>
<listitem>

Sistema de arquivos do kernel.  Este diretório não existe em seu disco rígido,
ele é colocado lá pelo kernel e usado por diversos programas que fazem sua
leitura, verificam configurações do sistema ou modificar o funcionamento de
dispositivos do sistema através da alteração em seus arquivos.



<varlistentry>
<term><filename>/sys</filename>
<listitem>

Sistema de arquivos do kernel.  Este diretório não existe em seu disco rígido,
ele é colocado lá pelo kernel e usado por diversos programas que fazem sua
leitura, verificam configurações do sistema ou modificar o funcionamento de
dispositivos do sistema através da alteração em seus arquivos.



<varlistentry>
<term><filename>/root</filename>
<listitem>

Diretório do usuário <literal>root.



<varlistentry>
<term><filename>/sbin</filename>
<listitem>

Diretório de programas usados pelo superusuário (root) para administração e
controle do funcionamento do sistema.



<varlistentry>
<term><filename>/tmp</filename>
<listitem>

Diretório para armazenamento de arquivos temporários criados por programas.



<varlistentry>
<term><filename>/usr</filename>
<listitem>

Contém maior parte de seus programas.  Normalmente acessível somente como
leitura.



<varlistentry>
<term><filename>/var</filename>
<listitem>

Contém maior parte dos arquivos que são gravados com freqüência pelos programas
do sistema, e-mails, spool de impressora, cache, etc.



</variablelist>





 userlevel='inic' basico-nomeando">###Nomeando Arquivos e Diretórios

No <command>GNU/Linux, os arquivos e diretórios podem ter o tamanho de
até **255** letras.  Você pode identifica-lo com uma extensão
(um conjunto de letras separadas do nome do arquivo por um ".").


Os programas executáveis do <command>GNU/Linux, ao contrário dos
programas de <command>DOS e <command>Windows, não são
executados a partir de extensões <filename>.exe, .com</filename> ou
<filename>.bat</filename>.  O <command>GNU/Linux (como todos os
sistemas POSIX) usa a **permissão de execução** de arquivo
para identificar se um arquivo pode ou não ser executado.


No exemplo anterior, nosso trabalho de história pode ser identificado mais
facilmente caso fosse gravado com o nome <filename>trabalho.text</filename> ou
<filename>trabalho.txt</filename>.  Também é permitido gravar o arquivo com o
nome <filename>Trabalho de Historia.txt</filename> mas não é recomendado gravar
nomes de arquivos e diretórios com espaços.  Porque será necessário colocar o
nome do arquivo entre "aspas" para acessa-lo (por exemplo, <literal>cat
"Trabalho de Historia.txt").  Ao invés de usar espaços, prefira
**capitalizar** o arquivo (usar letras maiúsculas e minúsculas
para identifica-lo): <filename>TrabalhodeHistoria.txt</filename>.




 userlevel='inic' basico-comandos">###Comandos

Comandos são ordens que passamos ao sistema operacional para executar uma
determinada tarefa.


Cada comando tem uma função específica, devemos saber a função de cada comando
e escolher o mais adequado para fazer o que desejamos, por exemplo:

<itemizedlist>
<listitem>

<command>ls - Mostra arquivos de diretórios


<listitem>

<command>cd - Para mudar de diretório




Este guia tem uma lista de vários comandos organizados por categoria com a
explicação sobre o seu funcionamento e as opções aceitas (incluindo alguns
exemplos).


É sempre usado um espaço depois do comando para separá-lo de uma opção ou
parâmetro que será passado para o processamento.  Um comando pode receber
opções e parâmetros:

<variablelist>
<varlistentry>
<term>**opções**
<listitem>

As **opções** são usadas para controlar como o comando será
executado, por exemplo, para fazer uma listagem mostrando o **dono,
grupo, tamanho dos arquivos** você deve digitar <literal>ls
-l.


Opções podem ser passadas ao comando através de um "-" ou "--":

<variablelist>
<varlistentry>
<term>-
<listitem>

Opção identificada por uma letra.  Podem ser usadas mais de uma opção com um
único hífen.  O comando <literal>ls -l -a é a mesma coisa de
<literal>ls -la



<varlistentry>
<term>--
<listitem>

Opção identificada por um nome.  Também chamado de opção extensa.  O comando
<literal>ls --all é equivalente a <literal>ls -a.



</variablelist>

Pode ser usado tanto "-" como "--", mas há casos em que somente "-" ou "--"
esta disponível.



<varlistentry>
<term>parâmetros
<listitem>

Um parâmetro identifica o **caminho, origem, destino, entrada
padrão** ou **saída padrão** que será passada ao
comando.


Se você digitar: <literal>ls /usr/share/doc/copyright,
<filename>/usr/share/doc/copyright</filename> será o parâmetro passado ao
comando <command>ls, neste caso queremos que ele liste os arquivos do
diretório **/usr/share/doc/copyright**.


É normal errar o nome de comandos, mas não se preocupe, quando isto acontecer o
sistema mostrará a mensagem <literal>command not found (comando não
encontrado) e voltará ao aviso de comando.  As mensagens de erro não fazem
nenhum mal ao seu sistema, somente dizem que algo deu errado para que você
possa corrigir e entender o que aconteceu.  No <command>GNU/Linux,
você tem a possibilidade de criar comandos personalizados usando outros
comandos mais simples (isto será visto mais adiante).  Os comandos se encaixam
em duas categorias: **Comandos Internos** e **Comandos
Externos**.



</variablelist>
<!-- [ %EXEMPLO [ -->

Por exemplo: <literal>"ls -la /usr/share/doc", <literal>ls
é o comando, <literal>-la é a opção passada ao comando, e
<literal><filename>/usr/share/doc</filename> é o diretório passado
como parâmetro ao comando <literal>ls.

<!-- ]]> -->


 userlevel='inic' basico-comandos-internos">###Comandos Internos

São comandos que estão localizados dentro do interpretador de comandos
(normalmente o <command>Bash) e não no disco.  Eles são carregados na
memória RAM do computador junto com o interpretador de comandos.


Quando executa um comando, o interpretador de comandos verifica primeiro se ele
é um **Comando Interno** caso não seja é verificado se é um
**Comando Externo**.


Exemplos de comandos internos são: <literal>cd, exit, echo, bg, fg, source,
help





 userlevel='inic' basico-comandos-externos">###Comandos Externos

São comandos que estão localizados no disco.  Os comandos são procurados no
disco usando o ordem do <literal>PATH e executados assim que
encontrados.


Para detalhes veja <xref linkend="run-path"/>.



 userlevel='inic' basico-avisocmd">###Aviso de comando (Prompt)

Aviso de comando (ou Prompt), é a linha mostrada na tela para
**digitação de comandos** que serão passados ao
<literal>interpretador de comandos para sua execução.


A posição onde o comando será digitado é marcado um "traço" piscante na tela
chamado de **cursor**.  Tanto em shells texto como em gráficos
é necessário o uso do cursor para sabermos onde iniciar a digitação de textos e
nos orientarmos quanto a posição na tela.


O aviso de comando do usuário <literal>root é identificado por uma
"#" (tralha), e o aviso de comando de usuários é identificado pelo símbolo "$".
Isto é padrão em sistemas <command>UNIX.


Você pode retornar comandos já digitados pressionando as teclas <literal>Seta
para cima / <literal>Seta para baixo.


A tela pode ser rolada para baixo ou para cima segurando a tecla
<literal>SHIFT e pressionando <literal>PGUP ou
<literal>PGDOWN.  Isto é útil para ver textos que rolaram rapidamente
para cima.


Abaixo algumas dicas sobre a edição da linha de comandos (não é necessário se
preocupar em decora-los):

<itemizedlist>
<listitem>

Pressione a tecla <literal>Back Space ("**&lt;--**") para apagar um caracter à esquerda do cursor.


<listitem>

Pressione a tecla <literal>Del para apagar o caracter acima do
cursor.


<listitem>

Pressione <literal>CTRL+<literal>A para mover o cursor para
o inicio da linha de comandos.


<listitem>

Pressione <literal>CTRL+<literal>E para mover o cursor para
o fim da linha de comandos.


<listitem>

Pressione <literal>CTRL+<literal>U para apagar o que
estiver à esquerda do cursor.  O conteúdo apagado é copiado para uso com
<literal>CTRL+<literal>y.


<listitem>

Pressione <literal>CTRL+<literal>K para apagar o que
estiver à direita do cursor.  O conteúdo apagado é copiado para uso com
<literal>CTRL+<literal>y.


<listitem>

Pressione <literal>CTRL+<literal>L para limpar a tela e
manter o texto que estiver sendo digitado na linha de comando (parecido com o
comando <command>clear).


<listitem>

Pressione <literal>CTRL+<literal>Y para colocar o texto que
foi apagado na posição atual do cursor.






 userlevel='avanc' basico-monitlogs">###Monitorando os logs

Os arquivos e diretórios de logs residem em <filename>/var/log</filename> e
registram tudo o que acontecem com o kernel, com os daemons e utilitários do
sistema.  Eles são muito importantes tanto para monitorar o que acontece com o
seu sistema como para ajudar na solução de problemas diversos.  É comum
programas como o servidor web, e-mail, mensagens instantaneas, firewall, irc,
banco de dados, gravarem os arquivos de log em diretórios próprios dentro de
<filename>/var/log/programa</filename>, desta forma evitam misturar seus
arquivos com os de log do sistema residentes em <filename>/var/log</filename>.


Acostume-se a olhar constantemente os arquivos de log em seu sistema, isto pode
ser importante para encontrar possíveis falhas de segurança, tentativa de
acesso ao sistema e, principalmente, solucionar problemas (principalmente os
mais complicados).  <!-- [ %CAPJUNTOS [ --> Leia <xref linkend="log"para mais detalhes. <!-- ]]> -->



 userlevel='avanc' basico-delarquivos">###Destruindo arquivos/partições de forma segura

Esta seção tem a intenção de conscientizar o administrador do uso devido de
técnicas para garantir que dados sensíveis sejam apagados de forma um pouco
mais segura em seu sistema.


Quando um arquivo é apagado, apenas a entrada na tabela de inodes é mexida, e
ele pode ainda ser recuperado com o <command>debugfs e um pouco de
paciência e engenharia.  O mesmo acontece com as partições, que podem ser
recuperadas com facilidade (isto é explicado no nível Intermediário do guia).
Esta recuperação é proporcionada pelas regras de funcionamento do sistema de
arquivos e do esquema de particionamento, ou seja, são permitidas pelo SO.


Vou um pouco mais além: O disco rígido é uma mídia magnética e opera de forma
mecânica para ler/gravar dados.  Quando um arquivo é apagado, seja por qualquer
motivo, ainda é possível recupera-lo.  O que permite isto é porque o HD nem
sempre tem a precisão de gravar **exatamente**
no mesmo lugar (pois a cabeça é movida mecanicamente), gravando em trilhas
microscópicamente vizinhas a anterior.  Então a imagem do arquivo que foi
apagada continua lá.  Segundo ouvi falar, a NASA possui recursos para recuperar
até 60 regravações posteriores no disco.  É claro que isto pode ocorrer em
pouco tempo, dependendo do tamanho de sua partição e se esta for uma
<filename>/var/spool</filename> em um servidor de e-mails :-)


Baseado nesta teoria, você poderá apagar os dados de forma destrutiva usando o
programa <command>shred, que regrava o arquivo repetidamente com
dados aleatórios.  Sua sintaxe é a seguinte:

<screen>
shred -n 70 -v -u arquivo


Isto faz com que ele regrava o conteúdo do <filename>arquivo</filename> 70
vezes com dados aleatórios.  O **-u** trunca e remove o
arquivo após concluído.


Note que o uso de dados aleatórios serve para destruir as possibilidades de uma
recuperação simples, este é o motivo de se recomendar sempre o uso de
<filename>/dev/urandom</filename> ao invés de <filename>/dev/zero</filename>
para destruição de arquivos.

<!-- [ %OBS [ -->

**OBS1:** Saiba exatamente o que está fazendo
pois estes procedimentos servem para dificultar ao máximo a recuperação de
dados.


**OBS2:** Devido as tecnologias de sistemas que
utilizam journaling (**XFS**, **EXT3**,
**EXT4**, **JFS** e
**ReiserFS**) e sistemas RAID, o <command>shred não
funcionará.  O <command>shred também não funcionará com sistemas de
arquivos via rede (**NFS**, **SMB**, etc.).
Se procura alguma forma de proteger seus dados, mesmo que apagados, utilize um
método de criptografia como o **DM-CRYPTO**,
**crypto-loop**, **gpg**, etc.


**OBS3:** Caso esteja usando um sistema de
arquivos criptografado, estes procedimentos são quase desnecessários
(dependendo do nível de segurança e algorítmos que você utiliza).

<!-- ]]> -->





 userlevel='inic;inter' basico-interpcmd">###Interpretador de comandos

Também conhecido como "shell".  É o programa responsável em interpretar as
instruções enviadas pelo usuário e seus programas ao sistema operacional (o
kernel).  
<!-- [ %DESCRICAOD [ --> Ele que executa comandos lidos do dispositivo de entrada padrão
(teclado) ou de um arquivo executável.  É a principal ligação entre o usuário,
os programas e o kernel.  O <command>GNU/Linux possui diversos tipos
de interpretadores de comandos, entre eles posso destacar o <command>bash, ash,
csh, tcsh, sh, etc.  Entre eles o mais usado é o
<command>bash.  O interpretador de comandos do DOS, por exemplo, é o
<filename>command.com</filename>. <!-- ]]> -->


Os comandos podem ser enviados de duas maneiras para o interpretador:
<literal>interativa e <literal>não-interativa:

<variablelist>
<varlistentry>
<term><literal>Interativa
<listitem>

Os comandos são digitados no aviso de comando e passados ao interpretador de
comandos um a um.  Neste modo, o computador depende do usuário para executar
uma tarefa, ou próximo comando.



<varlistentry>
<term><literal>Não-interativa
<listitem>

São usados arquivos de comandos criados pelo usuário (scripts) para o
computador executar os comandos na ordem encontrada no arquivo.  Neste modo, o
computador executa os comandos do arquivo um por um e dependendo do término do
comando, o script pode checar qual será o próximo comando que será executado e
dar continuidade ao processamento.


Este sistema é útil quando temos que digitar por várias vezes seguidas um mesmo
comando ou para compilar algum programa complexo.



</variablelist>

O shell <command>Bash possui ainda outra característica interessante:
A completação dos nomes.  Isto é feito pressionando-se a tecla
<literal>TAB.  Por exemplo, se digitar "ls tes" e pressionar
&lt;tab&gt;, o <command>Bash localizará todos os arquivos que iniciam
com "tes" e completará o restante do nome.  Caso a completação de nomes
encontre mais do que uma expressão que satisfaça a pesquisa, ou nenhuma, é
emitido um beep.  Se você apertar novamente a tecla TAB imediatamente depois do
beep, o interpretador de comandos irá listar as diversas possibilidades que
satisfazem a pesquisa, para que você possa escolher a que lhe interessa.  A
completação de nomes funciona sem problemas para comandos internos.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>ech (pressione <literal>TAB).
<literal>ls /vm(pressione <literal>TAB)

<!-- ]]> -->



 userlevel='inic;inter' basico-terminal">###Terminal Virtual (console)

Terminal (ou console) é o teclado e tela conectados em seu computador.  O
<command>GNU/Linux faz uso de sua característica
**multi-usuária** usando os "terminais virtuais".  Um terminal
virtual é uma segunda seção de trabalho completamente independente de outras,
que pode ser acessada no computador local ou remotamente via <command>telnet,
rsh, rlogin, etc.


No <command>GNU/Linux, em modo texto, você pode acessar outros
terminais virtuais segurando a tecla <literal>ALT e pressionando
<literal>F1 a F6.  Cada tecla de função corresponde a um número de
terminal do 1 ao 6 (o sétimo é usado por padrão pelo ambiente gráfico X).  O
<command>GNU/Linux possui mais de 63 terminais virtuais, mas apenas 6
estão disponíveis inicialmente por motivos de economia de memória RAM 
<!-- [ %INTERMEDIARIO [ --> (cada
terminal virtual ocupa aproximadamente 350 Kb de memória RAM, desative a
quantidade que não estiver usando para liberar memória RAM para uso de outros
programas!). <!-- ]]> -->


Se estiver usando o modo gráfico, você deve segurar <literal>CTRL+
<literal>ALT enquanto pressiona uma tela de &lt;F1&gt; a &lt;F6&gt;.
Para voltar ao modo gráfico, pressione
<literal>CTRL+<literal>ALT+ &lt;F7&gt;.

<!-- [ %EXEMPLO [ -->

Um exemplo prático: Se você estiver usando o sistema no Terminal 1 com o nome
"joao" e desejar entrar como "root" para instalar algum programa, segure
<literal>ALT enquanto pressiona &lt;F2&gt; para abrir o segundo
terminal virtual e faça o login como "root".  Será aberta uma nova seção para o
usuário "root" e você poderá retornar a hora que quiser para o primeiro
terminal pressionando <literal>ALT+&lt;F1&gt;.

<!-- ]]> -->


  userlevel='inic' basico-login">###Login

Login é a entrada no sistema quando você digita seu **nome** e
**senha**.  Por enquanto vou manter o seu suspense sobre o que
é o **logout**.




 userlevel='inic' basico-logout">###Logout

Logout é a saída do sistema.  A saída do sistema é feita pelos comandos
<command>logout, <command>exit,
<literal>CTRL+<literal>D, ou quando o sistema é reiniciado
ou desligado.




 userlevel='inic' basico-coringas">###coringas

coringas (ou referência global) é um recurso usado para especificar um ou mais
arquivos ou diretórios do sistema de uma só vez.  Este é um recurso permite que
você faça a filtragem do que será listado, copiado, apagado, etc.  São usados 4
tipos de coringas no <command>GNU/Linux:

<itemizedlist>
<listitem>

"*" - Faz referência a um nome completo/restante de um arquivo/diretório.


<listitem>

"?"  - Faz referência a uma letra naquela posição.


<listitem>

<literal>[padrão] - Faz referência a uma faixa de caracteres de um
arquivo/diretório.  Padrão pode ser:

<itemizedlist>
<listitem>

<literal>[a-z][0-9] - Faz referência a caracteres de
<literal>a até <literal>z seguido de um caracter de
<literal>0 até <literal>9.


<listitem>

<literal>[a,z][1,0] - Faz a referência aos caracteres
<literal>a e <literal>z seguido de um caracter
<literal>1 ou <literal>0 naquela posição.


<listitem>

<literal>[a-z,1,0] - Faz referência a intervalo de caracteres de
<literal>a até <literal>z ou <literal>1 ou
<literal>0 naquela posição.




A procura de caracteres é "Case Sensitive" assim se você deseja que sejam
localizados todos os caracteres alfabéticos você deve usar
<literal>[a-zA-Z].


Caso a expressão seja precedida por um <literal>^, faz referência a
qualquer caracter exceto o da expressão.  Por exemplo <literal>[^abc]
faz referência a qualquer caracter exceto <literal>a,
<literal>b e <literal>c.


<listitem>

<literal>{padrões} - Expande e gera strings para pesquisa de padrões
de um arquivo/diretório.

<itemizedlist>
<listitem>

<literal>X{ab,01} - Faz referência a seqüencia de caracteres
<literal>Xab ou <literal>X01


<listitem>

<literal>X{a-z,10} Faz referencia a seqüencia de caracteres
X<literal>a-z e <literal>X10.






O que diferencia este método de expansão dos demais é que a existência do
arquivo/diretório é opcional para geração do resultado.  Isto é útil para a
criação de diretórios.  Lembrando que os 4 tipos de coringas ("*", "?", "[]",
"{}") podem ser usados juntos.  


 condition='exemplos' basico-coringas-ex">###Exemplo de coringas

Para entender melhor vamos a prática:


Vamos dizer que tenha 5 arquivo no diretório <filename>/usr/teste</filename>:
<filename>teste1.txt, teste2.txt, teste3.txt, teste4.new,
teste5.new</filename>.


Caso deseje listar **todos** os arquivos do
diretório <filename>/usr/teste</filename> você pode usar o coringa "*" para
especificar todos os arquivos do diretório:


<literal>cd /usr/teste e <literal>ls * ou <literal>ls
/usr/teste/*.


Não tem muito sentido usar o comando <command>ls com "*" porque todos
os arquivos serão listados se o <command>ls for usado sem nenhum
Coringa.


Agora para listar todos os arquivos <filename>teste1.txt, teste2.txt,
teste3.txt</filename> com excessão de <filename>teste4.new</filename>,
<filename>teste5.new</filename>, podemos usar inicialmente 3 métodos:

<orderedlist numeration="arabic">
<listitem>

Usando o comando <literal>ls *.txt que pega todos os arquivos que
começam com qualquer nome e terminam com <filename>.txt</filename>.


<listitem>

Usando o comando <literal>ls teste?.txt, que pega todos os arquivos
que começam com o nome <filename>teste</filename>, tenham qualquer caracter no
lugar do coringa <literal>? e terminem com <filename>.txt</filename>.
Com o exemplo acima <literal>teste*.txt também faria a mesma coisa,
mas se também tivéssemos um arquivo chamado <filename>teste10.txt</filename>
este também seria listado.


<listitem>

Usando o comando <literal>ls teste[1-3].txt, que pega todos os
arquivos que começam com o nome <filename>teste</filename>, tenham qualquer
caracter entre o número 1-3 no lugar da 6a letra e terminem com
<filename>.txt</filename>.  Neste caso se obtém uma filtragem mais exata, pois
o coringa **?** especifica qualquer caracter naquela posição e
[] especifica números, letras ou intervalo que será usado.


</orderedlist>

Agora para listar somente <filename>teste4.new</filename> e
<filename>teste5.new</filename> podemos usar os seguintes métodos:

<orderedlist numeration="arabic">
<listitem>

<literal>ls *.new que lista todos os arquivos que terminam com
<filename>.new</filename>


<listitem>

<literal>ls teste?.new que lista todos os arquivos que começam com
<filename>teste</filename>, contenham qualquer caracter na posição do coringa
**?** e terminem com <filename>.new</filename>.


<listitem>

<literal>ls teste[4,5].* que lista todos os arquivos que começam com
<filename>teste</filename> contenham números de 4 e 5 naquela posição e
terminem com qualquer extensão.


</orderedlist>

Existem muitas outras formas de se fazer a mesma coisa, isto depende do gosto
de cada um.  O que pretendi fazer aqui foi mostrar como especificar mais de um
arquivo de uma só vez.  O uso de coringas será útil ao copiar arquivos, apagar,
mover, renomear, e nas mais diversas partes do sistema.  Alias esta é uma
característica do <command>GNU/Linux: permitir que a mesma coisa
possa ser feita com liberdade de várias maneiras diferentes.




