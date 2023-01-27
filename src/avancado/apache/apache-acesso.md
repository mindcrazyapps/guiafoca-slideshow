<!--- <?xml version="1.0" encoding="utf-8" ?> --->

 """>###Restrições de Acesso

A restrição de acesso do <command>Apache é feita através de
**Autorização** (<xref linkend="""-autor"/>) e **Autenticação**
(<xref linkend="""-auth"/>).  Através da
**autorização**, é checado se o endereço/rede especificada tem
ou não permissão para acessar a página.  A **autenticação**
requer que seja passado nome e senha para garantir acesso a página.  Os métodos
de **Autorização** e **Autenticação** podem
ser combinados como veremos mais adiante.


 s-apache-acesso">###Especificando opções/permissões para as páginas
    
    As opções de restrição podem tanto ser especificadas nas diretivas
    &lt;Directory&gt;, &lt;Location&gt; ou &lt;Files&gt; quanto nos arquivos
    <filename>.htaccess</filename> (ou outro nome de arquivo de controle de acesso
    especificado pela opção **AccessFileName** do arquivo de
    configuração do <command>Apache).  Cada diretiva de acesso é
    especificada entre &lt;tags&gt; e devem ser fechadas com &lt;/tag&gt; (como na
    linguagem HTML).  As seguintes diretivas de acesso são válidas no
    <command>Apache:
    
    <variablelist>
    <varlistentry>
    <term>Directory
    <listitem>
    
    As restrição afetará o diretório no disco especificado, conseqüentemente a
    página armazenada nele.  Por exemplo:
    
    <screen>
    &lt;Directory /var/www&gt;
     Order deny,allow
     deny from all
     allow from 10.1.0.1
    &lt;Directory&gt;
    
    
    O acesso ao diretório <filename>/var/www</filename> será permitido somente ao
    computador com o endereço IP <literal>10.1.0.1.
    
    
    
    <varlistentry>
    <term>DirectoryMatch
    <listitem>
    
    Funciona como a diretiva &lt;Directory&gt; mas trabalha com expressões
    regulares como argumento.  Por exemplo:
    
    <screen>
    &lt;DirectoryMatch "^/www/.*"&gt;
     Order deny,allow
     deny from all
    &lt;DirectoryMatch&gt;
    
    
    Bloqueará o acesso ao diretório <filename>/www</filename> e sub-diretórios
    dentro dele.
    
    
    
    <varlistentry>
    <term>Files
    <listitem>
    
    As restrições afetarão os arquivos do disco que conferem com o especificado.  É
    possível usar os coringas **?** e ***** como
    no shell.  Também podem ser usadas expressões regulares especificando um "~"
    após <literal>Files e antes da expressão.  Por exemplo:
    
    <screen>
    &lt;Files *.txt&gt;
     Order deny,allow
     deny from all
    &lt;/Files&gt;
    
    
    Bloqueia o acesso a todos os arquivos com a extensão <filename>.txt</filename>
    
    <screen>
    &lt;Files ~ "\.(gif|jpe?g|bmp|png)$"&gt;
     Order deny,allow
    &lt;/Files&gt;
    
    
    Bloqueia o acesso a arquivos <filename>gif, jpg, jpeg, bmp, png</filename>
    (note que o "~" ativa o modo de interpretação de expressões regulares).
    
    
    
    <varlistentry>
    <term>FilesMatch
    <listitem>
    
    Permite usar expressões regulares na especificação de arquivos (equivalente a
    diretiva &lt;Files ~ "expressão"&gt;).  Por exemplo:
    
    <screen>
    &lt;FilesMatch "\.(gif|jpe?g|bmp|png)$"&gt;
     Order deny,allow
    &lt;/FilesMatch&gt;
    
    
    Bloqueia o acesso a arquivos <filename>gif, jpg, jpeg, bmp, png</filename>.
    
    
    
    <varlistentry>
    <term>Location
    <listitem>
    
    As restrições afetarão o diretório base especificado na URL e seus
    sub-diretórios.  Por exemplo:
    
    <screen>
    &lt;Location /security&gt;
     Order allow,deny
    &lt;/Location&gt;
    
    
    Bloqueia o acesso de todos os usuários ao diretório
    <filename>/security</filename> da URL (a explicação porque o acesso é bloqueado
    neste caso será explicado em <xref linkend="""-autor"/>).
    
    
    
    <varlistentry>
    <term>LocationMatch
    <listitem>
    
    Idêntico a diretiva &lt;Location&gt; mas trabalha com expressões regulares.
    Por exemplo:
    
    <screen>
    &lt;LocationMatch "/(extra|special)/data"&gt;
     Order deny,allow
     deny from all
    &lt;/LocationMatch&gt;
    
    
    Bloqueará URLs que contém a substring "/extra/data" ou "/special/data".
    
    
    
    </variablelist>
    
    O uso das diretivas &lt;Directory&gt; e &lt;Files&gt; é apropriada quando você
    deseja trabalhar com permissões a nível de diretórios/arquivos no disco local
    (o controle do proxy também é feito via &lt;Directory&gt;), o uso da diretiva
    &lt;Location&gt; é adequado para trabalhar com permissões a nível de URL.  A
    ordem de processamento das diretivas de acesso são processadas é a seguinte:
    
    <orderedlist numeration="arabic">
    <listitem>
    
    A diretiva &lt;Directory&gt; (com exceção de &lt;DirectoryMatch&gt;) e os
    arquivos <filename>.htaccess</filename> são processados simultaneamente.  As
    definições dos arquivos <filename>.htaccess</filename> substituem as de
    &lt;Directory&gt;)
    
    
    <listitem>
    
    Expressões regulares de &lt;DirectoryMatch&gt;, &lt;Directory&gt;.
    
    
    <listitem>
    
    &lt;Files&gt; e &lt;FilesMatch&gt; são processados simultaneamente.
    
    
    <listitem>
    
    &lt;Location&gt; e &lt;LocationMatch&gt; são processados simultaneamente.
    
    
    </orderedlist>
    
    Normalmente é encontrado a opção **Options** dentro de uma das
    diretivas acima, a função desta diretiva é controlar os seguintes aspectos da
    listagem de diretórios:
    
    <variablelist>
    <varlistentry>
    <term>All
    <listitem>
    
    Todas as opções são usadas exceto a <literal>MultiViews.  É a padrão
    caso a opção **Options** não seja especificada.
    
    
    
    <varlistentry>
    <term>ExecCGI
    <listitem>
    
    Permite a execução de scripts CGI.
    
    
    
    <varlistentry>
    <term>FollowSymLinks
    <listitem>
    
    O servidor seguirá links simbólicos neste diretório (o caminho não é
    modificado).  Esta opção é ignorada caso apareça dentro das diretivas
    &lt;Location&gt;, &lt;LocationMatch&gt; e &lt;DirectoryMatch&gt;.
    
    
    
    <varlistentry>
    <term>Includes
    <listitem>
    
    É permitido o uso de includes no lado do servidor.
    
    
    
    <varlistentry>
    <term>IncludesNOEXEC
    <listitem>
    
    É permitido o uso de includes do lado do servidor, mas o comando
    <literal>#exec e <literal>#include de um script CGI são
    desativados.
    
    
    
    <varlistentry>
    <term>Indexes
    <listitem>
    
    Se não existir um arquivo especificado pela diretiva &lt;DirectoryIndex&gt; no
    diretório especificado, o servidor formatará automaticamente a listagem ao
    invés de gerar uma resposta de acesso negado.
    
    
    
    <varlistentry>
    <term>MultiViews
    <listitem>
    
    Permite o uso da Negociação de conteúdo naquele diretório.  A negociação de
    conteúdo permite o envio de um documento no idioma requisitado pelo navegador
    do cliente.
    
    
    
    <varlistentry>
    <term>SymLinksIfOwnerMatch
    <listitem>
    
    O servidor somente seguirá links simbólicos se o arquivo ou diretório alvo
    tiver como dono o mesmo user ID do link.  Esta opção é ignorada caso apareça
    dentro das diretivas &lt;Location&gt;, &lt;LocationMatch&gt; e
    &lt;DirectoryMatch&gt;.
    
    
    
    </variablelist>
    
    Múltiplos parâmetros para **Options** podem ser especificados
    através de espaços.
    
    
    **OBS1**: A opção Options não tem efeito dentro
    da diretiva FILES.
    
    
    **OBS2**: Tanto faz usar maiúsculas quanto
    minúsculas nas diretivas de configuração, opções e parâmetros de configuração
    do <command>Apache, a capitalização apenas ajuda a leitura e
    interpretação: SymLinksIfOwnerMatch (LinksSimbólicosSeDonoConferir).
    
    
    As opções especificadas para o diretório afetam também seus sub-diretórios, a
    não ser que sejam especificadas opções separadas para o sub-diretório:
    
    <screen>
    &lt;Directory /var/www&gt;
     Options Indexes FollowSymLinks
    &lt;/Directory&gt;
    
    
    Ao acessar o diretório <filename>/var/www/focalinux</filename>, as permissões
    usadas serão de <filename>/var/www</filename>, ao menos que uma diretiva
    &lt;Directory&gt; ou &lt;Location&gt; seja especificada:
    
    <screen>
    &lt;Directory /var/www&gt;
     Options Indexes FollowSymLinks
    &lt;/Directory&gt;
    
    &lt;Directory /var/www/focalinux&gt;
     Options Includes
    &lt;/Directory&gt;
    
    
    As opções e restrições de acesso de <filename>/var/www/focalinux</filename>
    serão EXATAMENTE as especificadas no bloco da diretiva &lt;Directory
    /var/www/focalinux&gt; e somente os **includes** serão
    permitidos.  Para adicionar ou remover uma opção individual definidas por
    diretivas anteriores, podem ser usado os sinais "+" ou "-", por exemplo:
    
    <screen>
    &lt;Directory /var/www&gt;
     Options Indexes FollowSymLinks
    &lt;/Directory&gt;
    
    &lt;Directory /var/www/focalinux&gt;
     Options +Includes -Indexes
    &lt;/Directory&gt;
    
    
    As opções **Indexes** e **FollowSymLinks**
    são definidas para o diretório <filename>/var/www</filename>, então as
    permissões do diretório <filename>/var/www/focalinux</filename> serão
    **FollowSymLinks** (do diretório
    <filename>/web/docs</filename>) e **Includes** (adicionada) e
    o parâmetro **Indexes** não terá efeito neste diretório.
    
    
    É permitido fazer um aninhamento das diretivas &lt;Directory&gt; e
    &lt;Files&gt;:
    
    <screen>
    &lt;Directory /var/www&gt;
     Order allow,deny
     allow from all
    
     &lt;Files LEIAME-DONO.txt&gt;
      Order deny,allow
      deny from all
     &lt;/Files&gt;
    
    &lt;/Directory&gt;
    
    
    Neste caso, somente os arquivos <filename>LEIAME-DONO.txt</filename> existentes
    no diretório <filename>/var/www</filename> e seus sub-diretórios serão
    bloqueados.
    
    
    Se a diretiva &lt;Files&gt; for usada fora de uma estrutura &lt;Directory&gt;,
    ela terá efeito em todos os arquivos disponibilizados pelo servidor.  Este é
    excelente método para proteger os arquivos de acesso, senhas e grupos, conforme
    será explicado mais adiante.
    
    
    Qualquer outro tipo de aninhamento de diretivas resultará em um erro de
    configuração ao se tentar carregar/recarregar o <command>Apache.  Um
    exemplo de diretiva incorreta:
    
    <screen>
    &lt;Directory /var/www&gt;
     Options Indexes FollowSymLinks
    
     &lt;Directory /var/www/focalinux&gt;
      Options +Includes -Indexes
     &lt;/Directory&gt;
    
    &lt;/Directory&gt;
    
    
    O correto é:
    
    <screen>
    &lt;Directory /var/www&gt;
     Options Indexes FollowSymLinks
    &lt;/Directory&gt;
    
    &lt;Directory /var/www/focalinux&gt;
     Options +Includes -Indexes
    &lt;/Directory&gt;
    
    
    Espero que tenha observado o erro no exemplo acima.
    
    
    **OBS1**: Você pode verificar se a configuração
    do apache está correta digitando <literal>apache -t como usuário
    root, se tudo estiver correto com suas configurações ele retornará a mensagem:
    "Syntax OK".
    
    
    **OBS2**: Se **Options** não
    for especificado, o padrão será permitir tudo exceto
    **MultiViews**.
    
    
    **OBS3**: Qualquer restrição afetará o diretório
    atual e todos os seus sub-diretórios!  Defina permissões de sub-diretórios
    específicos separadamente caso precise de um nível de acesso diferente.  Veja
    também a seção sobre arquivos OverRide (<filename>.htaccess</filename>) para
    detalhes sobre este tipo de arquivo.
    
    
    **OBS4**: A diretiva de acesso "&lt;Directory
    /&gt;" não afetará outros sistemas de arquivos montados dentro de seus
    subdiretórios.  Caso uma diretiva de acesso padrão não seja especificada para
    outros sistemas de arquivos, o acesso será automaticamente negado.
    
 

 ""-autor">###Autorização

A restrição de acesso por autorização (controlado pelo módulo
<filename>mod_access</filename>), permite ou não o acesso ao cliente de acordo
com o endereço/rede especificada.  As restrições afetam também os
sub-diretórios do diretório alvo.  Abaixo um exemplo de restrição de acesso que
bloqueia o acesso de qualquer host que faz parte do domínio
**.spammers.com.br** a URL
<filename>http://servidor/teste</filename>:

<screen>
&lt;Location /teste&gt;
 Option Indexes
 Order allow,deny
 allow from all
 deny from .spammers.com.br
&lt;/Location&gt;


A opção <literal>Option foi explicada acima, seguem as explicações
das outras diretivas:

<variablelist>
<varlistentry>
<term>Order
<listitem>

Especifica em que ordem as opções de acesso **allow/deny**
serão pesquisadas.  Caso não seja especificada, o padrão será
**deny/allow**.  Note que a ordem de pesquisa de
**allow** e **deny** é a inversa da
especificada.  A diretiva **Order** aceita os seguintes
valores:

<itemizedlist>
<listitem>

<literal>deny,allow - Esta é a padrão, significa um servidor mais
restritivo; a diretiva **allow** é processada primeiro e
somente depois a diretiva **deny**.  Caso nenhuma diretiva
allow e deny forem especificadas ou não conferirem, **PERMITE TUDO** como padrão.


<listitem>

<literal>allow,deny - Significa um servidor mais permissivo, a opção
**deny** é processada primeiro e somente depois a opção
**allow**.  Caso nenhuma diretiva allow e deny for
especificadas ou não conferirem, **BLOQUEIA
TUDO** como padrão.


<listitem>

<literal>mutual-failure - Somente permite o acesso se o usuário
receber autorização através da opção **allow** e **NÃO** ser bloqueado pela opção
**deny**, caso uma das checagens falhe, o acesso é
imediatamente negado.  É uma opção interessante quando você quer somente
pessoas de um determinado endereço/rede acessando o seu sistema e não estejam
em sua lista negra :-)




**ATENÇÃO**: É importante saber se a página será
permissiva ou restritiva para escolher a ordem mais adequada ao seu caso,
também leve em consideração a possibilidade do processamento cair na diretiva
de acesso padrão, caso nem a diretiva allow e deny conferiram e estiver usando
a ordem de acesso "allow,deny" ou "deny,allow".  Um sistema mal configurado
neste aspecto poderá trazer sérias conseqüências.


É comum em páginas permissivas se definir a seguinte configuração:

<screen>
Order allow,deny
allow from all


O motivo é que em um grande site, se forem adicionadas mais restrições nesta
página (devido a alguns domínios que tem usuários mal comportados, bloqueio de
acesso a rede do concorrente, potenciais atacantes, etc...), estas deverão ser
lidas antes da diretiva "allow from all" e podem passar desapercebidas ao
administrador e podem simplesmente não funcionar caso a opção
**Order** não esteja ajustada corretamente (lembre-se, você é
o administrador e a integridade do site depende de sua atenção na escolha da
ordem correta das diretivas de acesso).



<varlistentry>
<term>allow from
<listitem>

Especifica o endereço que terá acesso ao recurso especificado.  A diretiva
**allow** from aceita os seguintes valores:

<itemizedlist>
<listitem>

<literal>all - O acesso é permitido a todos.


<listitem>

um endereço de domínio completo (FQDN).  Por exemplo
<filename>www.debian.org.br</filename>.


<listitem>

um endereço de domínio parcial.  Qualquer computador que confira com o inicio
ou fim terá o acesso permitido.  Por exemplo,
<filename>.spammers.com.br</filename>, <filename>.debian.org</filename>.


<listitem>

um endereço IP completo, como <literal>192.168.1.1


<listitem>

um endereço IP parcial como <literal>192.168.1.


<listitem>

um par rede/máscara como <literal>10.1.0.0/255.255.0.0 ou
<literal>10.1.0.0/16, uma faixa de acesso a máquinas de uma mesma
rede pode ser definida facilmente através deste método.




**OBS1**: É necessário reiniciar o
<command>Apache depois de qualquer modificação em seu arquivo de
configuração (executando <literal>apachectl restart), ou recarregar
os arquivos de configuração (<literal>apachectl graceful).


**OBS2**: Mais de um host pode ser especificado
separando com um espaço:

<screen>
allow from 192.168. .debian.org.br


Permitirá o acesso de qualquer máquina que o endereço IP confira com
<literal>192.168.*.* e qualquer computador do domínio
<literal>debian.org.br


**OBS3**: Regras baseadas em nomes simples de
hosts (como <literal>www) não conferirão!  Deverá ser usado o FQDN ou
IP: <literal>www.dominio.com.br


**OBS4**: Caso Order não seja especificado,
**deny,allow** será usado como padrão (ou seja, permitirá tudo
como padrão).



<varlistentry>
<term>deny from
<listitem>

Especifica os endereços que NÃO terão acesso ao recurso especificado.  As
explicações referentes a esta diretiva de acesso são idêntica as de
**allow from**.



</variablelist>

É recomendável o uso de endereços IP ao invés de endereços DNS e um mecanismo
anti-spoofing no firewall ou código de roteamento, pois ficará mais difícil um
ataque baseado em DNS spoofing, aumentando consideravelmente a segurança de seu
servidor web.


**ATENÇÃO**: Caso receba erros 403 (acesso
negado) sem bloquear a URL nas diretivas de acesso, uma dos seguintes problemas
pode ser a causa:

<itemizedlist>
<listitem>

O servidor Web não tem permissões para acessar/abrir o diretório da página.
Certifique-se que o **dono** e **grupo** do
processo <command>Apache (especificado pela diretiva
**User** e **Group**) possuem permissões de
acesso àquele diretório.


<listitem>

Quando quer fazer uma listagem de arquivos do diretório e não especifica a
opção <literal>Option Indexes como opção de listagem.


<listitem>

Quando não está usando <literal>Option Indexes para impedir a
listagem de conteúdo do diretório e o não foi encontrado um arquivo de índice
válido dentre os existentes na diretiva <literal>DirectoryIndex no
diretório atual.




Abaixo alguns exemplos de permissões de acesso:

<screen>
&lt;Directory /var/www&gt;
 Options SymLinksIfOwnerMatch Indexes MultiViews
 Order allow,deny
 allow from all
&lt;/Directory&gt;


Permite o acesso a de qualquer usuário de qualquer lugar (allow from all),
permite também a visualização da listagem formatada de arquivos caso nenhum
arquivo especificado na diretiva **DirectoryIndex** seja
encontrado (Indexes), permite negociação de conteúdo
(**MultiViews**) e seguir links caso o dono do arquivo confira
com o nome do link (**SymLinksIfOwnerMatch**).

<screen>
&lt;Directory /var/www&gt;
 Options SymLinksIfOwnerMatch Indexes MultiViews
&lt;/Directory&gt;


Tem o mesmo significado da diretiva acima por métodos diferentes; quando
nenhuma opção **Order** é especificada,
**deny,allow** é definido como padrão, e como nenhuma opção de
acesso **allow/deny** foi especificada, o padrão "Order
deny,allow" é usado e permite TUDO como padrão.

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 Order deny,allow
 deny from all
&lt;/Directory&gt;


Esta regra acima não tem muita lógica pois restringe o acesso de todos os
usuários ao diretório <filename>/var/www</filename>, ao menos se esta for sua
intenção...

<screen>
&lt;Location /focalinux&gt;
 Options All
 Order allow,deny
 allow from all
&lt;/Location&gt;


A regra acima permite o acesso a URL
<filename>http://www.servidor.org/focalinux</filename> de qualquer host na
Internet

<screen>
&lt;Files .htaccess&gt;
 Order deny,allow
 deny from all
&lt;/Files&gt;


Bloqueia o acesso a qualquer arquivo <filename>.htaccess</filename> do sistema

<screen>
&lt;Files ~ "leiame-(arm|alpha|m68k|sparc|powerpc)\.txt"&gt;
 Order deny,allow
 deny from all
&lt;/Files&gt;


Bloqueia o acesso a qualquer arquivo <filename>leiame-arm.txt</filename>,
<filename>leiame-alpha.txt</filename>, <filename>leiame-m68k.txt</filename>,
<filename>leiame-sparc.txt</filename> e <filename>leiame-powerpc.txt</filename>
fazendo uso de expressões regulares.

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 Order mutual-failure
 allow from .dominio.com.br
 deny from lammer.dominio.com.br
&lt;/Directory&gt;


A diretiva acima somente permite acesso ao diretório
<filename>/var/www</filename> de máquinas pertencentes ao domínio
<filename>.dominio.com.br</filename> desde que não seja
<filename>lammer.dominio.com.br</filename>.

<screen>
&lt;Directory /var/www&gt;
 Options Indexes MultiViews
 Order allow,deny
 deny from .com .com.br
 allow from all
&lt;/Directory&gt;


Bloqueia o acesso ao diretório <filename>/var/www</filename> de computadores
pertencentes aos domínios **.com** e
**.com.br**.

<screen>
&lt;Directory /var/www&gt;
 Options None
 Order deny,allow
 allow from 192.168.1. .guiafoca.org .debian.org
 deny from 200.200.123.
&lt;/Directory&gt;


A regra acima permite o acesso de máquinas da rede
<literal>192.168.1.*, do domínio <literal>*.guiafoca.org e
<literal>*.debian.org, o acesso de máquinas da rede
<literal>200.200.123.* é bloqueado (nada contra, peguei nesse número
ao acaso :-).


Note que a máquina <literal>192.168.4.10 terá acesso LIVRE a regra
acima, pois não conferirá nem com **allow** nem com
**deny**, então o processamento cairá na diretiva padrão de
**deny,allow**, que neste caso permite o acesso caso nem
**allow** e **deny** conferiram com o padrão.

<screen>
&lt;Directory /var/www&gt;
 Options None
 Order allow,deny
 allow from 192.168.1. .cipsga.org.br .debian.org
 deny from 200.200.123.
&lt;/Directory&gt;


A regra acima é idêntica a anterior somente com a mudança da opção
**Order**.  Bloqueia o acesso de máquinas da rede
<literal>200.200.123.* e permite o acesso de máquinas da rede
<literal>192.168.1.*, do domínio <literal>*.cipsga.org.br e
<literal>*.debian.org.


Note que a máquina <literal>192.168.4.10 terá acesso BLOQUEADO a
regra acima, pois não conferirá nem com **allow** nem com
**deny**, então o processamento cairá na diretiva padrão de
**allow,deny** que neste caso bloqueia o acesso.



 ""-auth">###Autenticação

Através da **autenticação** (controlado pelo módulo
<filename>mod_auth</filename>) é possível especificar um
**nome** e **senha** para acesso ao recurso
solicitado.  As senhas são gravadas em formato criptografado usando
**Crypto** ou **MD5** (conforme desejado).  O
arquivo de senhas pode ser centralizado ou especificado individualmente por
usuário, diretório ou até mesmo por arquivo acessado.


 ""-auth-arqsenha">###Criando um arquivo de Senhas

O arquivo de senhas pode ser criado e mantido através do uso de 3 utilitários:
<command>htpasswd, <command>htdigest e
<command>dbmmanage:


 ""-auth-arqsenha-htpasswd">###htpasswd

Este é usado para criar o arquivo de senhas.  Para criar um banco de dados com
o nome <filename>senhas</filename> para o usuário
<replaceable>convidado</replaceable>, é usada a seguinte sintaxe:


<literal>htpasswd -c -m senhas convidado


Você será perguntado por uma senha para o usuário
<replaceable>convidado</replaceable> e para redigita-la.  A opção "-c" indica
que deverá ser criado um arquivo, a opção "-m" indica a utilização de senhas
criptografadas usando o algoritmo **MD5**, que garante maior
segurança que o método **Crypto**.  A senha pode ser
especificada diretamente na linha de comando através da opção "-b" (isto é um
ótimo recurso para utilização em shell scripts ou programas CGI de integração
com o navegador).


<literal>htpasswd -b -d senhas chefe abcdef


No exemplo acima, uma senha de alta segurança será introduzida no banco de
dados <filename>senhas</filename> tornando impossível o acesso a página do
usuário :-)


Note que esta senha foi cadastrada usando o algoritmo de criptografia Crypto
(opção -d).  O algoritmo **SHA** também pode ser usado como
alternativa, através da opção "-s".  Para modificar a senha do usuário
convidado, basta usar a mesma sintaxe (sem a opção "-c" que é usada para criar
um novo arquivo):


<literal>htpasswd -m senhas convidado


ou


<literal>htpasswd -b -m senhas convidado nova_senha


Opcionalmente você pode especificar a opção "-d" para atualizar também o
formato da senha para **Crypto**.  Podem existir senhas de
criptografias mistas (**SHA, Crypto, MD5**) no mesmo arquivo
sem nenhum problema.


A mudança do formato de senhas é útil quando se deseja aumentar o nível de
segurança oferecido por um melhor sistema ou para manter a compatibilidade com
alguns scripts/programas que compartilhem o arquivo de senhas.



 ""-auth-arqsenha-htdigest">###htdigest e dbmmanage

Estes são idênticos ao <command>htpasswd, a diferença é que o
<command>htdigest permite criar/manter um arquivo de senhas usando a
autenticação Digest, enquanto o <command>dbmmanage permite manter o
banco de dados de senhas em um arquivo <filename>DB, DBM, GDBM</filename> e
<filename>NDBM</filename>, formatos conhecidos pelo Perl.





 ""-auth-usuarios">###Autenticação através de usuários

Através deste método é possível especificar que usuários terão acesso ao
recurso definido, usando senhas de acesso individuais criptografadas usando um
dos utilitários da seção anterior.  Para restringir o acesso ao endereço
<filename>http://servidor.org/teste</filename>:

<screen>
&lt;Location /teste&gt;
 AuthName "Acesso a página do Foca Linux"
 AuthType basic
 AuthUserFile /home/gleydson/SenhaUsuario
# AuthGroupFile /home/users/SenhaGrupo
 Require valid-user
&lt;/Location&gt;


Ao tentar acessar o endereço <filename>http://servidor/teste</filename>, será
aberta uma janela no navegador com o título **Enter username for Acesso
a página do Foca Linux at servidor.org**, a diretiva **Require
valid-user** definem que o usuário e senha digitados devem existir no
arquivo especificado por **AuthUserFile** para que o acesso
seja garantido.  Uma explicação de cada opção de acesso usado na autenticação:

<variablelist>
<varlistentry>
<term>AuthName
<listitem>

Será o nome que aparecerá na janela de autenticação do seu navegador indicando
qual área restrita está solicitando senha (podem existir várias no servidor,
bastando especificar várias diretivas de restrições).



<varlistentry>
<term>AuthType
<listitem>

Especifica o método de que o nome e senha serão passados ao servidor.  Este
método de autenticação pode ser **Basic** ou
**Digest**

<itemizedlist>
<listitem>

<literal>Basic - Utiliza a codificação **base64**
para encodificação de nome e senha, enviando o resultado ao servidor.  Este é
um método muito usado e pouco seguro, pois qualquer sniffer instalado em um
roteador pode capturar e descobrir facilmente seu nome e senha.


<listitem>

<literal>Digest - Transmite os dados de uma maneira que não pode ser
facilmente decodificada, incluindo a codificação da área protegida
(especificada pela diretiva **AuthName**) que possui a
seqüencia de login/senha válida.  A diferença deste método é que você precisará
de arquivos de senhas diferentes para cada área protegida especificada por
**AuthName** (também chamada de Realm).





<varlistentry>
<term>AuthUserFile
<listitem>

É o arquivo gerado pelo utilitário <command>htpasswd que contém a
senha correspondente ao usuário



<varlistentry>
<term>AuthGroupFile
<listitem>

É um arquivo texto que contém o nome do grupo, dois pontos (":") e o nome dos
usuários que podem ter acesso ao recurso, separados por vírgulas.  No exemplo
acima ele se encontra comentado, mas a seguir encontrará exemplos que explicam
em detalhes o funcionamento desta diretiva.



<varlistentry>
<term>Require
<listitem>

Especifica que usuários podem ter acesso ao diretório.  Podem ser usadas uma
das 3 sintaxes:

<itemizedlist>
<listitem>

<literal>Require user usuário1 usuário2 usuário3 - Somente os
usuários especificados são considerados válidos para ter acesso ao diretório.


<listitem>

<literal>Require group grupo1 grupo2 grupo3 - Somente os usuários dos
grupos especificados são considerados válidos para terem acesso ao diretório.
Esta diretiva é útil quando deseja que somente alguns usuários de determinado
grupo tenham acesso ao recurso (por exemplo, usuários do grupo admins).


<listitem>

<literal>Require valid-user - Qualquer usuário válido no banco de
dados de senhas pode acessar o diretório.  É bem útil quando as opções de
acesso especificadas por Require user são muito longas.


A opção Require deve ser acompanhado das diretivas
**AuthName**, **AuthType** e as diretivas
**AuthUserFile** e **AuthGroupFile** para
funcionar adequadamente.





</variablelist>

**OBS**: É necessário reiniciar o
<command>Apache depois de qualquer modificação em seu arquivo de
configuração (<literal>apachectl restart), ou recarregar os arquivos
de configuração (<literal>apachectl graceful).  Note que o
<command>apachectl é somente um shell script para interação mais
amigável com o servidor web <command>apache, retornando mensagens
indicando o sucesso/falha no comando ao invés de códigos de saída.


Alguns exemplos para melhor assimilação:

<screen>
&lt;Location /teste&gt;
 AuthName "Acesso a página do Foca Linux"
 AuthType basic
 AuthUserFile /home/gleydson/SenhaUsuario
 Require user gleydson
&lt;/Location&gt;


As explicações são idênticas a anterior, mas somente permite o acesso do
usuário <literal>gleydson a URL
<filename>http://servidor.org/teste</filename>, bloqueando o acesso de outros
usuários contidos no arquivo **AuthUserFile**.

<screen>
&lt;Location /teste&gt;
 AuthName "Acesso a página do Foca Linux"
 AuthType basic
 AuthUserFile /home/gleydson/SenhaUsuario
 Require user gleydson usuario1 usuario2
&lt;/Location&gt;

<screen>
&lt;Location /teste&gt;
 AuthName "Acesso a página do Foca Linux"
 AuthType basic
 AuthUserFile /home/gleydson/SenhaUsuario
 Require user gleydson
 Require user usuario1
 Require user usuario2
&lt;/Location&gt;


As 2 especificações acima são equivalentes e permite o acesso aos usuários
<literal>gleydson, <literal>usuario1 e
<literal>usuario2 a página
<filename>http://servidor.org/teste</filename>.



 ""-auth-grupos">###Autenticação usando grupos

Há casos onde existem usuários de um arquivo de senhas que devem ter acesso a
um diretório e outros não, neste caso a diretiva
**valid-user** não pode ser especificada (porque permitiria o
acesso de todos os usuários do arquivo de senha ao diretório) e uma grande
lista de usuários ficaria bastante complicada de ser gerenciada com vários
usuários na diretiva **Require user**.


Quando existe esta situação, é recomendado o uso de grupos de usuários.  Para
fazer uso desse recurso, primeiro deverá ser criado um arquivo quer armazenará
o nome do **grupo** e dos usuários pertencente àquele grupo
usando a seguinte sintaxe (vamos chamar este arquivo de
<filename>SenhaGrupo</filename>):

<screen>
admins: gleydson usuario2
usuarios: usuario1 usuario2 usuario3 gleydson


Agora adaptamos o exemplo anterior para que somente os usuários especificados
no grupo admins do arquivo criado acima:

<screen>
&lt;Location /teste&gt;
 AuthName "Acesso a página do Foca Linux"
 AuthType basic
 AuthUserFile /home/gleydson/SenhaUsuario
 AuthGroupFile /home/gleydson/SenhaGrupo
 Require group admins
&lt;/Location&gt;


Agora somente os usuários pertencentes ao grupo **admins**
(**gleydson** e **usuario2**) poderão ter
acesso ao diretório <filename>/teste</filename>.


**OBS1**: Verifique se o servidor Web possui
acesso a leitura no arquivo de senhas de usuários e grupos, caso contrário será
retornado um código "500 - Internal Server Error".  Este tipo de erro é
caracterizado por tudo estar OK na sintaxe dos arquivos de configuração após
checagem com "apache -t" e todas as diretivas de controle de acesso apontam
para os diretórios e arquivos corretos.


**OBS2:**: Sempre use espaços para separar os
nomes de usuários pertencentes a um grupo.


**OBS3**: NUNCA coloque os arquivos que contém
senhas e grupos em diretórios de acesso público onde usuários podem ter acesso
via o servidor Web.  Tais localizações são <filename>/var/www</filename>,
<filename>/home/"usuario"/public_html</filename> e qualquer outro diretório de
acesso público que defina em seu sistema.


É recomendável também ocultar estes arquivos através da diretiva &lt;Files&gt;
evitando possíveis riscos de segurança com usuários acessando os arquivos de
senha e grupo.


Na distribuição <command>Debian, qualquer arquivo iniciando com
<filename>.ht*</filename> será automaticamente ocultado pelo sistema, pois já
existe uma diretiva &lt;Files ~ "\.ht"&gt;.  Tal diretiva pode também ser
especificada no arquivo de acesso <filename>.htaccess</filename>.  Assim um
arquivo <filename>.htsenha</filename> e <filename>.htgroup</filename> são bons
nomes se estiver desejando ocultar dados de olhos curiosos...





 ""-autorANDauth">###Usando autorização e autenticação juntos

Os métodos de **autorização** e
**autenticação** podem ser usados ao mesmo tempo dentro de
qualquer uma das diretivas de controle de acesso.  As diretivas de
**autorização** são processadas primeiro (mod_access) e depois
as diretivas de **autenticação** (mod_auth).  Segue um
exemplo:

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 Order deny,allow
 allow from .dominiolocal.com.br
 deny from all
 AuthName "Acesso ao diretório do servidor Web"
 AuthType basic
 AuthUserFile /var/cache/apache/senhas
 Require valid-user
&lt;/Directory&gt;


Para ter acesso ao diretório <filename>/var/www</filename>, primeiro o
computador deve fazer parte do domínio
<filename>.dominiolocal.com.br</filename>, assim ela passa pelo teste de
autorização, depois disso será necessário fornecer o login e senha para acesso
a página, digitando o login e senha corretos, o teste de autenticação será
completado com sucesso e o acesso ao diretório <filename>/var/www</filename>
autorizado.

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 Order mutual-failure
 allow from .dominiolocal.com.br
 deny from lammer.dominiolocal.com.br
 AuthName "Acesso ao diretório do servidor Web"
 AuthType basic
 AuthUserFile /var/cache/apache/senhas
 AuthGroupFile /var/cache/apache/grupos
 Require group admins
&lt;/Directory&gt;


No exemplo acima, é usado o método de autorização com a opção **Order
mutual-failure** e o método de autenticação através de
**grupos**.  Primeiro é verificado se o usuário pertence ao
domínio <filename>.dominiolocal.com.br</filename> e se ele não está acessando
da máquina <filename>lammer.dominiolocal.com.br</filename>, neste caso ele
passa pelo teste de autorização.  Depois disso ele precisará fornecer o nome e
senha válidos, com o login pertencente ao **AuthGroupFile**,
passando pelo processo de autenticação e obtendo acesso ao diretório
<filename>/var/www</filename>.


 ""-autorANDauth-diferenciado">###Acesso diferenciado em uma mesma diretiva

É interessante permitir usuários fazendo conexões de locais confiáveis terem
acesso direto sem precisar fornecer nome e senha e de locais inseguros
acessarem somente após comprovarem **quem**
realmente são.  Como é o caso de permitir usuários de uma rede privada terem
acesso completo aos recursos e permitir o acesso externo ao mesmo recurso
somente através de senha.  Isto pode ser feito com o uso da diretiva
**Satisfy** junto ao bloco de
**autorização/autenticação**.  Vamos tomar como base o exemplo
anterior:

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 Order mutual-failure
 allow from .dominiolocal.com.br
 deny from lammer.dominiolocal.com.br
 AuthName "Acesso ao diretório do servidor Web"
 AuthType basic
 AuthUserFile /var/cache/apache/senhas
 AuthGroupFile /var/cache/apache/grupos
 Require group admins
 Satisfy any
&lt;/Directory&gt;


Note que o exemplo é o mesmo com a adição da diretiva **Satisfy
any** no final do bloco do arquivo.  Quando a opção
**Satisfy** não é especificada, ela assumirá "all" como
padrão, ou seja, o usuário deverá passar no teste de autorização e autenticação
para ter acesso.


A diferença do exemplo acima em relação ao da seção anterior é se a máquina
passar no teste de autorização ela já terá acesso garantido.  Caso falhe no
teste de autorização, ainda terá a chance de ter acesso a página passando na
checagem de autenticação.


Isto garante acesso livre aos usuários do domínio
<filename>.dominiolocal.com.br</filename>.  Já os outros usuários, incluindo
acessos vindos de <filename>lammer.dominiolocal.com.br</filename> que pode ser
uma máquina com muito uso, poderá ter acesso ao recurso caso tenha fornecido um
nome e senha válidos para passar pelo processo de autenticação.  Tenha isto em
mente...  este tipo de problema é comum e depende mais de uma política de
segurança e conduta interna, o sistema de segurança não pode fazer nada a não
ser permitir acesso a um nome e senha válidos.


Tenha cuidado com o uso da opção **Satisfy** em diretivas que
especificam somente o método de autenticação:

<screen>
&lt;Directory /var/www&gt;
 Options Indexes
 AuthName "Acesso ao diretório do servidor Web"
 AuthType basic
 AuthUserFile /var/cache/apache/senhas
 AuthGroupFile /var/cache/apache/grupos
 Require group admins
 Satisfy any
&lt;/Directory&gt;


ATENÇÃO PARA O DESCUIDO ACIMA!: Como o método de autorização NÃO é
especificado, é assumido **deny,allow** como padrão, que
permite o acesso a TODOS os usuários.  O bloco acima **NUNCA** executará o método de autenticação por este
motivo.  A melhor coisa é NÃO usar a opção **Satisfy** em
casos que só requerem autenticação ou usar **Satisfy all**
(que terá o mesmo efeito de não usa-la, hehehe).


A falta de atenção nisto pode comprometer silenciosamente a segurança de seu
sistema.





 ""-htaccess">###O arquivo <filename>.htaccess</filename>

O arquivo <filename>.htaccess</filename> deve ser colocado no diretório da
página que deverá ter suas permissões de acesso/listagem controladas.  A
vantagem em relação a inclusão direta de diretivas de acesso dentro do arquivo
de configuração do <command>Apache, é que o controle de acesso poderá
ser definido pelo próprio webmaster da página, sem precisar ter acesso direto a
configuração do <command>Apache, que requerem privilégios de root.


Outro ponto fundamental é que não há necessidade de reiniciar o servidor Web,
pois este arquivo é lido no momento de cada acesso ao diretório que controla.
O nome do arquivo OverRide pode ser definido através da diretiva
**AccessFileName** no arquivo de configuração do
<command>Apache, <filename>.htaccess</filename> é usado como padrão.


O controle de que opções estarão disponíveis no <filename>.htaccess</filename>
são definidas na diretiva **AllowOverride** que pode conter o
seguintes parâmetros:

<itemizedlist>
<listitem>

<literal>None - O servidor não buscará o arquivo
<literal>.htaccess nos diretórios


<listitem>

<literal>All - O servidor utilizará todas as opções abaixo no arquivo
<filename>.htaccess</filename>


<listitem>

<literal>AuthConfig - Permite o uso de diretivas de autenticação
(**AuthDBMGroupFile**, **AuthDBMUserFile**,
**AuthGroupFile**, **AuthName**,
**AuthType**, **AuthUserFile**,
**Require**, etc.).


<listitem>

<literal>FileInfo - Permite o uso de diretivas controlando o tipo de
documento (**AddEncoding**, **AddLanguage**,
**AddType**, **DefaultType**,
**ErrorDocument**, **LanguagePriority**,
etc.).


<listitem>

<literal>Indexes - Permite o uso de diretivas controlando a indexação
de diretório (**AddDescription**,
**AddIcon**, **AddIconByEncoding**,
**AddIconByType**, **DefaultIcon**,
**DirectoryIndex**, **FancyIndexing**,
**HeaderName**, **IndexIgnore**,
**IndexOptions**, **ReadmeName**, etc.).


<listitem>

<literal>Limit - Permite o uso de diretivas controlando o acesso ao
computador (**allow**, **deny** e
**order**).


<listitem>

<literal>Options - Permite o uso de diretivas controlando
características específicas do diretório (**Options** e
**XBitHack**).




**OBS**: Não tem sentido usar a opção
**AllowOverride** dentro da diretiva &lt;Location&gt;, ela
será simplesmente ignorada.


Para acesso ao arquivo <filename>.htaccess</filename> do diretório
<filename>/var/www/focalinux</filename>, o <command>Apache buscará os
arquivos <filename>.htaccess</filename> na seqüencia:
<filename>/.htaccess</filename>, <filename>/var/.htaccess</filename>,
<filename>/var/www/.htaccess</filename>,
<filename>/var/www/focalinux/.htaccess</filename>, qualquer diretiva que não
exista no <filename>.htaccess</filename> do diretório
<filename>/var/www/focalinux</filename> terá seu valor definido pela diretiva
dos arquivos <filename>.htaccess</filename> dos diretórios anteriores.  Somente
após esta seqüencia de checagens o acesso ao documento é permitido (ou negado).


Por este motivo, muitos administradores decidem desativar completamente o uso
de arquivos <filename>.htaccess</filename> no diretório raíz e habilitar
somente nos diretórios especificados pela diretiva &lt;Directory&gt; no arquivo
de configuração do <command>Apache, evitando brechas de segurança na
manipulação destes arquivos (esta é uma boa idéia a não ser que se dedique 24
horas somente na administração do seu servidor Web e conheça toda sua estrutura
hierárquica de segurança:

<screen>
&lt;Directory /&gt;
 AllowOverride none
&lt;/Directory&gt;

&lt;Directory /var/www&gt;
 AllowOverride limit authconfig indexes
&lt;/Directory&gt;


Na especificação acima, o arquivo <filename>.htaccess</filename> será procurado
no diretório <filename>/var/www</filename> e seus sub-diretórios, usando
somente opções que controlam a autorização de acesso
(**limit**), autenticação e opções
(**authconfig**) e de indexação de documentos
(**indexes**).


Alguns exemplos do uso do arquivo <filename>.htaccess</filename>:


Para permitir o acesso direto de usuários da rede
<literal>192.168.1.* diretamente, e requerer senha de acesso para
outros usuários, o seguinte arquivo <filename>.htaccess</filename> deve ser
criado no diretório <filename>/var/www</filename>:

<screen>
Order deny,allow
allow from 192.168.1.0/24
deny from all
AuthName "Acesso a página Web principal da Empresa"
AuthType basic
AuthUserFile /var/cache/apache/senhas
Require valid-user
Satisfy any


Note que a sintaxe é exatamente a mesma das usadas na diretivas de acesso, por
este motivo vou dispensar explicações detalhadas a respeito.


**ATENÇÃO**: A diretiva **Options
Indexes** deverá ser especificada no
**AllowOverRide** e não no arquivo
<filename>.htaccess</filename>.  Agora você já sabe o que fazer se estiver
recebendo erros 500 ao tentar acessar a página (Erro interno no servidor)...



 s-apache-acesso-setenvif">###Usando a diretiva SetEnvIf com Allow e Deny

É possível especificar o acesso baseado em variáveis de ambiente usando a
diretiva **SetEnvIf**, isto lhe permite controlar o acesso de
acordo com o conteúdo de cabeçalhos HTTP.  A sintaxe é a seguinte:


<literal>SetEnvIf [**atributo**]
[**expressão**] [**variável**]


Isto poder ser facilmente interpretado como: Se o "atributo" especificado
conter a "expressão", a "variável" será criada e armazenará o valor verdadeiro.
Veja abaixo:

<screen>
SetEnvIf User-Agent ".*MSIE*." EXPLODER
&lt;Directory /var/www&gt;
 Order deny,allow
 allow from all
 deny from env=EXPLODER
&lt;/Directory&gt;


Se o Navegador (campo **User-Agent** do cabeçalho http) usado
para acessar a página for o <literal>Internet Explorer, a variável
<replaceable>EXPLODER</replaceable> será criada e terá o valor verdadeiro
(porque a expressão de **SetEnvIf** conferiu com a expressão).


Note o uso de "deny from env=VARIÁVEL".  Neste caso se o navegador for o
<literal>Internet Explorer, o acesso será bloqueado (pois o navegador
conferiu, assim a variável <replaceable>EXPLODER</replaceable> recebeu o valor
verdadeiro).


É permitido especificar as diretivas de acesso normais junto com especificação
de variáveis de ambiente, basta separa-los com espaços.  Uma descrição completa
dos cabeçalhos HTTP, conteúdo e parâmetros aceitos por cada um são descritos na
<literal>RFC 2068.



 s-apache-acesso-limit">###A diretiva &lt;Limit&gt;

Esta diretiva é semelhante a &lt;Directory&gt; mas trabalha com métodos HTTP
(como GET, PUT, POST, etc) ao invés de diretórios.  A diretiva &lt;Limit&gt;
pode ser usada dentro da diretiva de acesso &lt;Directory&gt;,
&lt;Location&gt;, mas nenhuma diretiva de controle de acesso pode ser colocada
dentro de &lt;Limit&gt;.


Os métodos HTTP válidos são: GET, POST, PUT DELETE, CONNECT, OPTIONS, TRACE,
PATCH, PROPFIND, PROPPATCH, MKCOL, COPY, MOVE, LOCK e UNLOCK.  Note que os
métodos são case-sensitive.  Por exemplo:

<screen>
&lt;Directory /var/www&gt;
 Option Indexes
  &lt;Limit POST PUT DELETE&gt;
     Order deny,allow
     allow from 192.168.1.0/24
     deny from all
   &lt;/Limit&gt;
&lt;/Directory&gt;


Somente permitem o uso dos métodos POST, PUT, DELETE de máquinas da rede
interna.


**OBS1**: Se o método GET é bloqueado, o
cabeçalho HTTP também será bloqueado.


**OBS2**: A diretiva de acesso &lt;Limit&gt;
somente terá efeito na diretiva &lt;Location&gt; se for especificada no arquivo
de configuração do servidor web.  A diretiva &lt;Location&gt; simplesmente é
ignorada nos arquivos <filename>.htaccess</filename>...


Este abaixo é usado por padrão na distribuição <command>Debian para
restringir para somente leitura o acesso aos diretórios de usuários acessados
via módulo <filename>mod_userdir</filename>:

<screen>
&lt;Directory /home/*/public_html&gt;
    AllowOverride FileInfo AuthConfig Limit
    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
    &lt;Limit GET POST OPTIONS PROPFIND&gt;
        Order allow,deny
        Allow from all
    &lt;/Limit&gt;
    &lt;Limit PUT DELETE PATCH PROPPATCH MKCOL COPY MOVE LOCK UNLOCK&gt;
        Order deny,allow
        Deny from all
    &lt;/Limit&gt;
&lt;/Directory&gt;



 s-apache-acesso-limitexcept">###Diretiva &lt;LimitExcept&gt;

Esta diretiva é semelhante a &lt;Limit&gt;, mas atinge todos os métodos HTTP,
menos os especificados.




