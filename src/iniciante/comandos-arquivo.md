<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cmd">###Comandos para manipulação de Arquivos

Abaixo, comandos utilizados para manipulação de arquivos.

 comandos-cat">###cat

Mostra o conteúdo de um arquivo binário ou texto.


<command>cat [opções] [**diretório/arquivo**]
[**diretório1/arquivo1**]

<!-- [ %OPCOES [ -->
<variablelist>
<varlistentry>
<term>**diretório/arquivo**
<listitem>

Localização do arquivo que deseja visualizar o conteúdo.



<varlistentry>
<term>**opções**
<term>-n, --number
<listitem>

Mostra o número das linhas enquanto o conteúdo do arquivo é mostrado.



<varlistentry>
<term>-s, --squeeze-blank
<listitem>

Não mostra mais que uma linha em branco entre um parágrafo e outro.



<varlistentry>
<term>-
<listitem>

Lê a entrada padrão.



</variablelist>
<!-- ]]> -->

O comando <command>cat trabalha com arquivos texto.  Use o comando
<command>zcat para ver diretamente arquivos compactados com
<command>gzip.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>cat /usr/doc/copyright/GPL

<!-- ]]> -->



 comando-tac">###tac

Mostra o conteúdo de um arquivo binário ou texto (como o
<command>cat) só que em ordem inversa.


<command>tac [opções] [**diretório/arquivo**]
[**diretório1/arquivo1**]

<!-- [ %OPCOES [ -->
<variablelist>
<varlistentry>
<term>**diretório/arquivo**
<listitem>

Localização do arquivo que deseja visualizar o conteúdo



<varlistentry>
<term>**opções**
<term>-s [string]
<listitem>

Usa o [string] como separador de registros.



<varlistentry>
<term>-
<listitem>

Lê a entrada padrão.



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>tac /usr/doc/copyright/GPL.

<!-- ]]> -->



 comando-rm">###rm

Apaga arquivos.  Também pode ser usado para apagar diretórios e sub-diretórios
vazios ou que contenham arquivos.


<command>rm
[**opções**][**caminho**][**arquivo/diretório**]
[**caminho1**][**arquivo1/diretório1**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**caminho**
<listitem>

Localização do arquivo que deseja apagar.  Se omitido, assume que o arquivo
esteja no diretório atual.



<varlistentry>
<term>**arquivo/diretório**
<listitem>

Arquivo que será apagado.



<varlistentry>
<term>**opções**
<term>-i, --interactive
<listitem>

Pergunta antes de remover, esta é ativada por padrão.



<varlistentry>
<term>-v, --verbose
<listitem>

Mostra os arquivos na medida que são removidos.



<varlistentry>
<term>-r, --recursive
<listitem>

Usado para remover arquivos em sub-diretórios.  Esta opção também pode ser
usada para remover sub-diretórios.



<varlistentry>
<term>-f, --force
<listitem>

Remove os arquivos sem perguntar.



<varlistentry>
<term>-- arquivo
<listitem>

Remove arquivos/diretórios que contém caracteres especiais.  O separador "--"
funciona com todos os comandos do shell e permite que os caracteres especiais
como "*", "?", "-", etc.  sejam interpretados como caracteres comuns.



</variablelist>
<!-- ]]> -->

Use com atenção o comando <command>rm, uma vez que os arquivos e
diretórios forem apagados, eles não poderão ser mais recuperados.


<!-- [ %EXEMPLO [ -->

Exemplos:

<itemizedlist>
<listitem>

<literal>rm teste.txt - Apaga o arquivo
<filename>teste.txt</filename> no diretório atual.


<listitem>

<literal>rm *.txt - Apaga todos os arquivos do diretório atual que
terminam com <filename>.txt</filename>.


<listitem>

<literal>rm *.txt teste.novo - Apaga todos os arquivos do diretório
atual que terminam com <filename>.txt</filename> e também o arquivo
<filename>teste.novo</filename>.


<listitem>

<literal>rm -rf /tmp/teste/* - Apaga todos os arquivos e
sub-diretórios do diretório <filename>/tmp/teste</filename> mas mantém o
sub-diretório <filename>/tmp/teste</filename>.


<listitem>

<literal>rm -rf /tmp/teste - Apaga todos os arquivos e sub-diretórios
do diretório <filename>/tmp/teste</filename>, inclusive
<filename>/tmp/teste</filename>.


<listitem>

<literal>rm -f -- --arquivo-- - Remove o arquivo de nome
<filename>--arquivo--</filename>.



<!-- ]]> -->



 comando-cp">###cp

Copia arquivos.

<!-- [ %OPCOES [ -->

<command>cp [**opções**] [**origem**]
[**destino**]


onde:

<variablelist>
<varlistentry>
<term>**origem**
<listitem>

Arquivo que será copiado.  Podem ser especificados mais de um arquivo para ser
copiado usando "coringas" (veja <xref linkend="basico-coringas"/>).



<varlistentry>
<term>**destino**
<listitem>

O caminho ou nome de arquivo onde será copiado.  Se o destino for um diretório,
os arquivos de origem serão copiados para dentro do diretório.



<varlistentry>
<term>**opções**
<term>i, --interactive
<listitem>

Pergunta antes de substituir um arquivo existente.



<varlistentry>
<term>-f, --force
<listitem>

Não pergunta, substitui todos os arquivos caso já exista.



<varlistentry>
<term>-r
<listitem>

Copia arquivos dos diretórios e subdiretórios da origem para o destino.  É
recomendável usar -R ao invés de -r.



<varlistentry>
<term>-R, --recursive
<listitem>

Copia arquivos e sub-diretórios (como a opção -r) e também os arquivos
especiais FIFO e dispositivos.



<varlistentry>
<term>-v, --verbose
<listitem>

Mostra os arquivos enquanto estão sendo copiados.



<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-s, --simbolic-link
<listitem>

Cria link simbólico ao invés de copiar.



<varlistentry>
<term>-l, --link
<listitem>

Faz o link no destino ao invés de copiar os arquivos.



<varlistentry>
<term>-p, --preserve
<listitem>

Preserva atributos do arquivo, se for possível.



<varlistentry>
<term>-u, --update
<listitem>

Copia somente se o arquivo de origem é mais novo que o arquivo de destino ou
quando o arquivo de destino não existe.



<varlistentry>
<term>-x
<listitem>

Não copia arquivos que estão localizados em um sistema de arquivos diferente de
onde a cópia iniciou.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

O comando <command>cp copia arquivos da ORIGEM para o DESTINO.  Ambos
origem e destino terão o mesmo conteúdo após a cópia.


<!-- [ %EXEMPLO [ -->

Exemplos:

<variablelist>
<varlistentry>
<term><literal>cp teste.txt teste1.txt
<listitem>

Copia o arquivo <filename>teste.txt</filename> para
<filename>teste1.txt</filename>.



<varlistentry>
<term><literal>cp teste.txt /tmp
<listitem>

Copia o arquivo <filename>teste.txt</filename> para dentro do diretório
<filename>/tmp</filename>.



<varlistentry>
<term><literal>cp * /tmp
<listitem>

Copia todos os arquivos do diretório atual para <filename>/tmp</filename>.



<varlistentry>
<term><literal>cp /bin/* .
<listitem>

Copia todos os arquivos do diretório <filename>/bin</filename> para o diretório
em que nos encontramos no momento.



<varlistentry>
<term><literal>cp -R /bin /tmp
<listitem>

Copia o diretório <filename>/bin</filename> e todos os arquivos/sub-diretórios
existentes para o diretório <filename>/tmp</filename>.



<varlistentry>
<term><literal>cp -R /bin/* /tmp
<listitem>

Copia todos os arquivos do diretório <filename>/bin</filename> (exceto o
diretório <filename>/bin</filename>) e todos os arquivos/sub-diretórios
existentes dentro dele para <filename>/tmp</filename>.



<varlistentry>
<term><literal>cp -R /bin /tmp
<listitem>

Copia todos os arquivos e o diretório <filename>/bin</filename> para
<filename>/tmp</filename>.



</variablelist>
<!-- ]]> -->



 comando-mv">###mv

Move ou renomeia arquivos e diretórios.  
<!-- [ %DESCRICAOD [ --> O processo é semelhante ao do comando 
<command>cp mas o arquivo de origem é apagado após o término da
cópia. <!-- ]]> -->


<command>mv [**opções**] [**origem**]
[**destino**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**origem**
<listitem>

Arquivo/diretório de origem.



<varlistentry>
<term>**destino**
<listitem>

Local onde será movido ou novo nome do arquivo/diretório.



<varlistentry>
<term>**opções**
<term>-f, --force
<listitem>

Substitui o arquivo de destino sem perguntar.



<varlistentry>
<term>-i, --interactive
<listitem>

Pergunta antes de substituir.  É o padrão.



<varlistentry>
<term>-v, --verbose
<listitem>

Mostra os arquivos que estão sendo movidos.




<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-u, --update
<listitem>

Move somente arquivos antigos, ou novos arquivos.



<!-- ]]> -->

</variablelist>
<!-- ]]> -->

O comando <command>mv copia um arquivo da **ORIGEM**
para o **DESTINO** (semelhante ao <command>cp), mas
após a cópia, o arquivo de **ORIGEM** é apagado.

<!-- [ %EXEMPLO [ -->

Exemplos:

<variablelist>
<varlistentry>
<term><literal>mv teste.txt teste1.txt
<listitem>

Muda o nome do arquivo <filename>teste.txt</filename> para
<filename>teste1.txt</filename>.



<varlistentry>
<term><literal>mv teste.txt /tmp
<listitem>

Move o arquivo teste.txt para <filename>/tmp</filename>.  Lembre-se que o
arquivo de origem é apagado após ser movido.



<varlistentry>
<term><literal>mv teste.txt teste.new (supondo que <filename>teste.new</filename> já exista)
<listitem>

Copia o arquivo <filename>teste.txt</filename> por cima de
<filename>teste.new</filename> e apaga <filename>teste.txt</filename> após
terminar a cópia.



</variablelist>

<!-- ]]> -->
