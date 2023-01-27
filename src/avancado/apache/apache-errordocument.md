<!-- Converted by db4-upgrade version 1.0 -->

 s-apache-errordocument">###Definindo documentos de erro personalizados

Documentos de erros personalizados são definidos através da diretiva
**ErrorDocument**.  É possível especificar códigos de erros
que serão atendidos por certos documentos ou colocar esta diretiva dentro de
blocos de controle de acesso &lt;Directory&gt;, &lt;Location&gt; ou
&lt;VirtualHost&gt; para que tenham mensagens de erro personalizadas, ao invés
da padrão usada pelo servidor <command>httpd.


<literal>ErrorDocument [**código de erro**]
[**documento**]


Onde:

<variablelist>
<varlistentry>
<term>**código de erro**
<listitem>

Código de erro da mensagem (veja <xref linkend="s-apache-httpcodes"como
referência).  O código de erro **401** deve referir-se a um
arquivo local.



<varlistentry>
<term>**documento**
<listitem>

Documento, mensagem de erro ou redirecionamento que será usado no servidor caso
aquele código de erro seja encontrado:



</variablelist>

Para definir uma mensagem de erro padrão para todo servidor web, basta colocar
a diretiva **ErrorDocument** fora das diretivas que controlam
o acesso a diretórios e virtual hosts (o inicio do arquivo
<filename>httpd.conf</filename> é ideal).


Exemplos:

<itemizedlist>
<listitem>

<literal>ErrorDocument 404 /cgi-bin/erros404.pl - Direciona para um
script em Perl que manda um e-mail ao administrador falando sobre o link
quebrado e envia o usuário a uma página de erro padrão.


<listitem>

<literal>ErrorDocument 404 /naoencontrada.html - Direciona o usuário
para o arquivo <filename>naoencontrada.html</filename> (dentro de
**DocumentRoot**) quando ocorrer o erro 404.  Note que o
diretório <filename>/</filename> levado em consideração é o especificado pela
diretiva **DocumentRoot**.


<listitem>

<literal>ErrorDocument 500 "Erro Interno no servidor" - Mostra a
mensagem na tela quando ocorrer o erro 500.


<listitem>

<literal>ErrorDocument 401 /obtendoacesso.html - Direciona o usuário
ao arquivo explicando como obter acesso ao sistema.


<listitem>

<literal>ErrorDocument 503  [guiafoca](http://www.guiafoca.org) )/servicos.html -
Redireciona o usuário a URL especificada.


<listitem>

<literal>ErrorDocument 403 "Acesso negado" - Mostra a mensagem na
tela no caso de erros 403.





