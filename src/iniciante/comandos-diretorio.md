<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cmdd">###Comandos para manipulação de diretório

Abaixo comandos úteis para a manipulação de diretórios.



 comando-ls">###ls

Lista os arquivos de um diretório.


<command>ls [**opções**]
[**caminho/arquivo**] [**caminho1/arquivo1**]
...

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**caminho/arquivo**
<listitem>

Diretório/arquivo que será listado.



<varlistentry>
<term>**caminho1/arquivo1**
<listitem>

Outro Diretório/arquivo que será listado.  Podem ser feitas várias listagens de
uma só vez.



<varlistentry>
<term>**opções**
<term>-a, --all
<listitem>

Lista todos os arquivos (inclusive os ocultos) de um diretório.



<varlistentry>
<term>-A, --almost-all
<listitem>

Lista todos os arquivos (inclusive os ocultos) de um diretório, exceto o
diretório atual e o de nível anterior.



<varlistentry>
<term>-B, --ignore-backups
<listitem>

Não lista arquivos que terminam com ~ (Backup).



<varlistentry>
<term>--color=PARAM
<listitem>

Mostra os arquivos em cores diferentes, conforme o tipo de arquivo.  PARAM pode
ser:

<itemizedlist>
<listitem>

**never** - Nunca lista em cores (mesma coisa de não usar o
parâmetro --color).


<listitem>

**always** - Sempre lista em cores conforme o tipo de arquivo.


<listitem>

**auto** - Somente colore a listagem se estiver em um
terminal.





<varlistentry>
<term>-d, --directory
<listitem>

Lista os nomes dos diretórios ao invés do conteúdo.



<varlistentry>
<term>-f
<listitem>

Não classifica a listagem.



<varlistentry>
<term>-F
<listitem>

Insere um caracter após arquivos executáveis ('*'), diretórios ('/'), soquete
('='), link simbólico ('@') e pipe ('|').  Seu uso é útil para identificar de
forma fácil tipos de arquivos nas listagens de diretórios.



<varlistentry>
<term>-G, --no-group
<listitem>

Oculta a coluna de grupo do arquivo.



<varlistentry>
<term>-h, --human-readable
<listitem>

Mostra o tamanho dos arquivos em Kbytes, Mbytes, Gbytes.



<varlistentry>
<term>-H
<listitem>

Faz o mesmo que <literal>-h, mas usa unidades de 1000 ao invés de
1024 para especificar Kbytes, Mbytes, Gbytes.



<varlistentry>
<term>-l
<listitem>

Usa o formato longo para listagem de arquivos.  Lista as permissões, data de
modificação, donos, grupos, etc.



<varlistentry>
<term>-n
<listitem>

Usa a identificação de usuário e grupo numérica ao invés dos nomes.



<varlistentry>
<term>-L, --dereference
<listitem>

Lista o arquivo original e não o link referente ao arquivo.



<varlistentry>
<term>-o
<listitem>

Usa a listagem longa sem os donos dos arquivos (mesma coisa que -lG).



<varlistentry>
<term>-p
<listitem>

Mesma coisa que -F, mas não inclui o símbolo '*' em arquivos executáveis.  Esta
opção é típica de sistemas <command>Linux.



<varlistentry>
<term>-R
<listitem>

Lista diretórios e sub-diretórios recursivamente.



<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>--full-time
<listitem>

Lista data e hora completa.



<varlistentry>
<term>Classificação da listagem
<listitem>

A listagem pode ser classificada usando-se as seguintes opções:

<variablelist>
<varlistentry>
<term>-f
<listitem>

Não classifica, e usa -au para listar os arquivos.



<varlistentry>
<term>-r
<listitem>

Inverte a ordem de classificação.



<varlistentry>
<term>-c
<listitem>

Classifica pela data de alteração.



<varlistentry>
<term>-X
<listitem>

Classifica pela extensão.



<varlistentry>
<term>-U
<listitem>

Não classifica, lista os arquivos na ordem do diretório.



<varlistentry>
<term>-Z
<listitem>

Exibe o contexto SELinux de cada arquivo.



</variablelist>


<!-- ]]> -->
</variablelist>
<!-- ]]> -->

Uma listagem feita com o comando <literal>ls -la normalmente é
mostrada da seguinte maneira:

<screen>
-rwxr-xr--  1  gleydson user    8192 nov 4 16:00 teste


Abaixo as explicações de cada parte:

<variablelist>
<varlistentry>
<term><literal>-rwxr-xr--
<listitem>

São as permissões de acesso ao arquivo teste.  A primeira letra (da esquerda)
identifica o tipo do arquivo, se tiver um <literal>d é um diretório,
se tiver um "-" é um arquivo normal.


As permissões de acesso é explicada em detalhes em <xref linkend="perm"/>.



<varlistentry>
<term><literal>1
<listitem>

Se for um diretório, mostra a quantidade de sub-diretórios existentes dentro
dele.  Caso for um arquivo, será 1.



<varlistentry>
<term><literal>gleydson
<listitem>

Nome do dono do arquivo <filename>teste</filename>.



<varlistentry>
<term><literal>user
<listitem>

Nome do grupo que o arquivo <filename>teste</filename> pertence.



<varlistentry>
<term><literal>8192
<listitem>

Tamanho do arquivo (em bytes).



<varlistentry>
<term><literal>nov
<listitem>

Mês da criação/ última modificação do arquivo.



<varlistentry>
<term><literal>4
<listitem>

Dia que o arquivo foi criado.



<varlistentry>
<term><literal>16:00
<listitem>

Hora em que o arquivo foi criado/modificado.  Se o arquivo foi criado há mais
de um ano, em seu lugar é mostrado o ano da criação do arquivo.



<varlistentry>
<term><filename>teste</filename>
<listitem>

Nome do arquivo.



</variablelist>
<!-- [ %EXEMPLO [ -->

Exemplos do uso do comando <command>ls:

<itemizedlist>
<listitem>

<literal>ls - Lista os arquivos do diretório atual.


<listitem>

<literal>ls /bin /sbin - Lista os arquivos do diretório /bin e /sbin


<listitem>

<literal>ls -la /bin - Listagem completa (vertical) dos arquivos do
diretório /bin inclusive os ocultos.



<!-- ]]> -->



 comando-cd">###cd

Entra em um diretório.  Você precisa ter a permissão de execução para entrar no
diretório.


<command>cd [**diretório**]

<!-- [ %OPCOES [ -->

onde:


**diretório** - diretório que deseja entrar.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

Usando <literal>cd sem parâmetros ou <literal>cd ~, você
retornará ao seu diretório de usuário (diretório home).


<listitem>

<literal>cd /, retornará ao diretório raíz.


<listitem>

<literal>cd -, retornará ao diretório anteriormente acessado.


<listitem>

<literal>cd .., sobe um diretório.


<listitem>

<command>cd ../[**diretório**], sobe um diretório e
entra imediatamente no próximo (por exemplo, quando você está em
<filename>/usr/sbin</filename>, você digita <literal>cd ../bin, o
comando <command>cd retorna um diretório (<filename>/usr</filename>)
e entra imediatamente no diretório <filename>bin</filename>
(<filename>/usr/bin</filename>).



<!-- ]]> -->



 comando-pwd">###pwd

Mostra o nome e caminho do diretório atual.


Você pode usar o comando pwd para verificar em qual diretório se encontra (caso
seu aviso de comandos não mostre isso).




 comando-mkdir">###mkdir

Cria um diretório no sistema.  
<!-- [ %DESCRICAOD [ --> Um diretório é usado para armazenar arquivos de
um determinado tipo.  O diretório pode ser entendido como uma
**pasta** onde você guarda seus papeis (arquivos).  Como uma
pessoa organizada, você utilizará uma pasta para guardar cada tipo de
documento, da mesma forma você pode criar um diretório
<filename>vendas</filename> para guardar seus arquivos relacionados com vendas
naquele local. <!-- ]]> -->


<command>mkdir [**opções**]
[**caminho/diretório**]
[**caminho1/diretório1**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**caminho**
<listitem>

Caminho onde o diretório será criado.



<varlistentry>
<term>**diretório**
<listitem>

Nome do diretório que será criado.



<varlistentry>
<term>**opções:**
<term>-p
<listitem>

Caso os diretórios dos níveis acima não existam, eles também serão criados.



<varlistentry>
<term>--verbose
<listitem>

Mostra uma mensagem para cada diretório criado.  As mensagens de erro serão
mostradas mesmo que esta opção não seja usada.



</variablelist>
<!-- ]]> -->

Para criar um novo diretório, você deve ter permissão de gravação.  Por
exemplo, para criar um diretório em /tmp com o nome de
<filename>teste</filename> que será usado para gravar arquivos de teste, você
deve usar o comando <filename>"mkdir /tmp/teste"</filename>.


Podem ser criados mais de um diretório com um único comando (<literal>mkdir
/tmp/teste /tmp/teste1 /tmp/teste2).




 comando-rmdir">###rmdir

Remove um diretório do sistema.  
<!-- [ %DESCRICAOD [ --> Este comando faz exatamente o contrário do
<command>mkdir.  O diretório a ser removido deve estar vazio e você
deve ter permissão de gravação para remove-lo. <!-- ]]> -->


<command>rmdir [**caminho/diretório**]
[**caminho1/diretório1**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**caminho**
<listitem>

Caminho do diretório que será removido.



<varlistentry>
<term>**diretório**
<listitem>

Nome do diretório que será removido.



</variablelist>
<!-- ]]> -->

É necessário que esteja um nível acima do diretório(s) que será(ão)
removido(s).  Para remover diretórios que contenham arquivos, use o comando
<command>rm com a opção <literal>-r (para maiores detalhes,
veja <xref linkend="comando-rm"/>).

<!-- [ %EXEMPLO [ -->

Por exemplo, para remover o diretório <filename>/tmp/teste</filename> você deve
estar no diretório <filename>tmp</filename> e executar o comando <literal>rmdir
teste.

<!-- ]]> -->


