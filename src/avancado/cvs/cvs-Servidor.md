<?xml version="1.0" encoding="UTF-8"?>

 s-cvs-d">###Servidor de CVS - configurando métodos de acesso ao repositório

O CVS é uma aplicação cliente/servidor, possuindo diversas maneiras de fazer o
acesso seu repositório (veja <xref linkend="s-cvs-p-repos"repositórios).
Estes métodos são os seguintes:

<itemizedlist>
<listitem>

local (<xref linkend="s-cvs-d-metodos-local"/>).


<listitem>

ext (<xref linkend="s-cvs-d-metodos-ext"/>).


<listitem>

pserver (<xref linkend="s-cvs-d-metodos-pserver"/>).


<listitem>

fork (<xref linkend="s-cvs-d-metodos-fork"/>).


<listitem>

GSSAPI (<xref linkend="s-cvs-d-metodos-gssapi"/>).




Eles são explicados em detalhes nas sub-seções a seguir.

 s-cvs-d-metodos-local">###local

Acessa o diretório do repositório diretamente no disco local.  A vantagem deste
método é que não é requerido nem nome nem senha para acesso (você precisa
apenas ter permissões para acesso aos arquivos que deseja trabalhar) e também
não é preciso nenhuma conexão de rede.


Este método é ideal para trabalhar na máquina local ou com os arquivos
administrativos do CVS existentes no diretório <filename>CVSROOT</filename> do
repositório.  É muito útil também para configurar outros métodos de acesso,
como o <literal>pserver.


Para criar seu repositório, veja <xref linkend="s-cvs-p-mkrepos"/>.

 s-cvs-d-metodos-local-c">###Configurando o método local

Para utilizar o método de acesso local, basta definir a variável
<replaceable>CVSROOT</replaceable> da seguinte forma (assumindo que o
repositório esteja instalado em <filename>/var/lib/cvs</filename>):

<screen>
export CVSROOT=/var/lib/cvs

ou 

export CVSROOT=local:/var/lib/cvs


Depois disso, basta utilizar os comandos normais do <command>cvs sem
precisar se autenticar no sistema.  Veja os detalhes de utilização dos comandos
de CVS após o login na seção <xref linkend="s-cvs-c"/>.





 s-cvs-d-metodos-fork">###fork

Este método é semelhante ao local, mas ele "simula" uma conexão de rede com o
servidor.  É muito usado para fins de testes.

 s-cvs-d-metodos-fork-c">###Configurando o método fork

Para utilizar o método de acesso **fork**, basta definir a
variável <replaceable>CVSROOT</replaceable> da seguinte forma (assumindo que o
repositório esteja instalado em <filename>/var/lib/cvs</filename>):

<screen>
export CVSROOT=fork:/var/lib/cvs


Depois disso, basta utilizar os comandos normais do <command>cvs, sem
precisar se autenticar no sistema.  Veja os detalhes de utilização dos comandos
do CVS após o login em <xref linkend="s-cvs-c"/>.





 s-cvs-d-metodos-ext">###ext

Este método de acesso lhe permite especificar um programa externo que será
usado para fazer uma conexão remota com o servidor <command>cvs.Este
programa é definido na variável <replaceable>CVS_RSH</replaceable> e caso não
ela seja especificada o padrão é <command>rsh.


Este método requer que o usuário possua um login/senha no banco de dados de
autenticação <filename>/etc/passwd</filename> do servidor de destino.  Suas
permissões de acesso ao CVS (leitura/gravação) serão as mesmas definidas neste
arquivo.


O uso do acesso criptografado via <command>ssh é possível definindo o
programa <command>ssh na variável <replaceable>CVS_RSH</replaceable>.
Veja os exemplos a seguir em <xref linkend="s-cvs-d-metodos-ext-c"/>.


Para criar seu repositório, veja <xref linkend="s-cvs-p-mkrepos"/>.

 s-cvs-d-metodos-ext-c">###Configurando o método ext

Defina a variável <replaceable>CVSROOT</replaceable> da seguinte forma para
utilizar este método de acesso (assumindo <filename>/var/lib/cvs</filename>
como repositório):

<screen>
export CVSROOT=:ext:conta@servidor.org.br:/var/lib/cvs
cvs login


A "conta" é uma conta de usuário existente no servidor remoto (por exemplo,
<literal>gleydson) seguido do nome do servidor remoto (separado por
uma "@").  Por exemplo para acessar o servidor
**cvs.cipsga.org.br** usando a conta
**michelle**:

<screen>
export CVSROOT=:ext:michelle@cvs.cipsga.org.br:/var/lib/cvs
cvs checkout


OBS: A senha via método de acesso "ext" será pedida somente uma vez quando for
necessário o primeiro acesso ao servidor remoto.  Veja os detalhes de
utilização dos comandos de CVS após o login na seção <xref linkend="s-cvs-c"/>.
O uso mais freqüente do <literal>ext é para conexões seguras feitas
via <command>ssh, feita da seguinte forma:

<screen>
export CVS_RSH=ssh
export CVSROOT=:ext:michelle@cvs.cipsga.org.br:/var/lib/cvs
cvs checkout


O acesso de leitura/gravação do usuário, é definido de acordo com as permissões
deste usuário no sistema.  Uma maneira recomendada é definir um grupo que terá
acesso a gravação no CVS e adicionar usuários que possam fazer gravação neste
grupo.


**OBS1:** O acesso via <command>ssh
traz a vantagem de que as senhas trafegarão de forma segura via rede, não sendo
facilmente capturadas por sniffers e outros programas de monitoração que possam
estar instalados na rota entre você e o servidor.


**OBS2:** É possível especificar a senha na
variável <replaceable>CVSROOT</replaceable> usando a sintaxe semelhante a usada
no ftp:

<screen>
export CVSROOT=:ext:michelle:senha@cvs.cipsga.org.br:/var/lib/cvs


Entretanto isto não é recomendado, pois os processos da máquina poderão
capturar facilmente a senha (incluindo usuários normais, caso a máquina não
esteja com patches de restrições de acesso a processos configurada, que é o
padrão em quase todas as distribuições de <command>Linux).





 s-cvs-d-metodos-pserver">###pserver (password server)

Este é um método de acesso remoto que utiliza um banco de dados de usuários
senhas para acesso ao repositório.  A diferença em relação ao método de acesso
**ext** é que o **pserver** roda através de
um servidor próprio na porta 2401.  O acesso dos usuários (leitura/gravação) no
repositório pode ser feita tanto através do banco de dados de usuários do
sistema (<filename>/etc/passwd</filename>) como através de um banco de dados
separado por repositório.


A grande vantagem deste segundo método é que cada projeto poderá ter membros
com acessos diferenciados; o membro x poderá ter acesso ao projeto
<literal>sgml mas não ao projeto <literal>focalinux; ou o
usuário y poderá ter acesso de gravação (para trabalhar no projeto
<literal>focalinux) mas somente acesso de leitura ao projeto
<literal>sgml.


Este é o método de acesso preferido para a criação de usuários anônimos (uma
vez que o administrador de um servidor que hospede muitos projetos não vai
querer abrir um acesso anônimo via <literal>ext para todos os
projetos).


Também existe a vantagem que novos membros do projeto e tarefas administrativas
são feitas por qualquer pessoa que possua acesso de gravação aos arquivos do
repositório.



 s-cvs-d-metodos-pserver-c">###Configurando um servidor pserver
 s-cvs-d-metodos-pserver-c-pserver">###Ativando o servidor pserver

Para ativar o pserver (caso ainda não o tenha feito).  Execute o comando
<literal>dpkg-reconfigure cvs e selecione a opção <literal>Ativar o
servidor pserver.  Uma maneira de fazer isso automaticamente é
modificando o arquivo <filename>/etc/inetd.conf</filename> adicionando a
seguinte linha:

<screen>
# na Debian
cvspserver      stream  tcp     nowait.400      root    /usr/sbin/tcpd /usr/sbin/cvs-pserver

# em outras Distribuições 
cvspserver  stream  tcp  nowait  root  /usr/bin/cvs cvs -f --allow-root=/var/lib/cvs pserver


Na <command>Debian, o cvs é iniciado através do script
<filename>/usr/sbin/cvs-pserver</filename> que checa os binários e executa o
<command>cvs para todos os repositórios especificados no arquivo
<filename>/etc/cvs-pserver.conf</filename>.


Caso precise adicionar mais repositórios para acesso via
**pserver** ou outro método de acesso, veja <xref linkend="s-cvs-p-mkrepos"/>.


Você também poderá executar o método <literal>pserver sob um usuário
que não seja o root, para isto, modifique a entreada referênte ao usuário.grupo
no <filename>inetd.conf</filename> e tenha certeza que o daemon consegue fazer
as operações de suid/sgid no diretório onde o repositório se encontra.



 s-cvs-d-metodos-pserver-c-system">###Servidor pserver usando autenticação do sistema

Para usar o banco de dados de autenticação do sistema
(<filename>/etc/passwd</filename>) para autenticar os usuários remotos,
primeiro tenha certeza que o servidor **pserver** está ativado
(como descrito em <xref linkend="s-cvs-d-metodos-pserver-c-pserver"/>.
Repetindo o exemplo anterior, a usuária **Michelle** deverá
ter uma conta em <filename>/etc/passwd</filename> para fazer acesso ao cvs:

<screen>
export CVSROOT=:pserver:michelle@cvs.cipsga.org.br:/var/lib/cvs
cvs login


Será pedido a senha da usuária <literal>michelle.  Entrando com a
senha correta, o sistema retornará para o aviso de comando.  Uma mensagem será
mostrada caso a senha entrada seja incorreta.  Daqui em diante, o resto da
seção CVS é normal e você terá as permissões de acesso ao repositório de acordo
com as suas permissões de acesso naquele diretório.


**OBS1:** A senha poderá ser passada junto com o
login da mesma forma como o ftp.  Veja a observação em <xref linkend="s-cvs-d-metodos-ext-c"/>.


**OBS2:** A desvantagem do método pserver padrão
é que a seção é feita em texto plano, desta forma, alguns cuidados podem ser
tomados para tornar o sistema um pouco mais seguro.  Um deles é dar
<filename>/bin/false</filename> como shell de usuário (para desativar o login
no sistema) ou usar o método de acesso descrito em <xref linkend="s-cvs-d-metodos-pserver-c-system"em combinação com este.  Tenha
conciencia das influências disso se a máquina for usada para outras tarefas,
como um servidor "pop3" por exemplo.



 s-cvs-d-metodos-pserver-c-pwrepos">###Servidor pserver com autenticação própria

Esta forma de acesso armazena os usuários em um banco de dados próprio, não
requerendo a criação de contas locais no arquivo
<filename>/etc/passwd</filename>.  Para criar um servidor deste tipo siga os
seguintes procedimentos:

<orderedlist numeration="arabic">
<listitem>

Exporte a variável <replaceable>CVSROOT</replaceable> apontando para o
repositório que deseja configurar o acesso.  Como isto é uma configuração
administrativa, assumo o método de acesso **local** sendo
usada pelo usuário administrador do servidor: <literal>export
CVSROOT=/var/lib/cvs.


<listitem>

Crie um diretório para trabalhar nos arquivos administrativos do repositório:
<literal>mkdir /tmp/repos


<listitem>

Entre no diretório criado acima e execute o comando: <literal>cvs checkout
.


<listitem>

Quando terminar de baixar os arquivos, entre no subdiretório
<filename>CVSROOT</filename>, os arquivos de configuração do repositório se
encontram lá (para detalhes sobre cada um destes arquivos, veja <xref linkend="s-cvs-cvsroot"/>.


<listitem>

Edite o arquivo <filename>config</filename> e mude a variável
<replaceable>SystemAuth</replaceable> para <literal>no.  Isto diz ao
servidor **pserver** não usar os arquivos de autenticação do
sistema, mas a invés disso usar seu banco de dados próprio.


Em algumas instalações, caso exista o arquivo <filename>passwd</filename> no
repositório, o **pserver** automaticamente o utiliza ao invés
do <filename>/etc/passwd</filename>.


<listitem>

Crie um arquivo <filename>passwd</filename> no diretório
<filename>CVSROOT</filename> o formato deste arquivo é:

<screen>
usuario:senha:usuario_local


Onde:

<variablelist>
<varlistentry>
<term>usuario
<listitem>

Nome da conta de usuário que fará acesso ao CVS.



<varlistentry>
<term>senha
<listitem>

Senha que será usada pelo usuário.  Ela deverá ser criptografada usando o
algoritmo crypt.  O comando <command>mkpasswd senha pode ser usado
para gerar a senha criptografada.  Caso este campo seja deixado em branco,
nenhuma senha de usuário será utilizada.  O utilitário
<command>mkpasswd está presente no pacote <systemitem role="package">whois</systemitem> na <command>Debian.



<varlistentry>
<term>usuario_local
<listitem>

Usuário local que terá suas permissões mapeadas ao usuário do CVS.  Como a
conta de usuário do <command>cvs não existe no sistema, é necessário
que o sistema tenha uma maneira de saber que nível de acesso este usuário terá.
Caso não crie este usuário ou ele seja inválido, você terá erros do tipo ": no
such user" no momento que fizer o "cvs login".


Uma forma segura de se fazer isto, é criar uma conta de usuário *somente* com
acesso aos arquivos do CVS, sem shell e senha.  Isto permitirá mapear a UID/GID
do usuário criado com o acesso do CVS sem comprometer a segurança do sistema de
arquivos.  Isto pode ser feito através do seguinte comando:

<screen>
adduser --disabled-password --disabled-login usuario


É necessário especificar um diretório home do usuário, pois o servidor cvs
precisa ter acesso ao arquivo <filename>/home/do/cvs/.cvsignore</filename>.


**OBS1:** Mais uma vez: Leve sempre em conta a
forma que os outros serviços em sua máquina estão configurados (como eles fazem
acesso, permissões de acesso, diretórios onde gravam arquivos, são algumas
delas) antes de escolher como um serviço novo na máquina funcionará.  Isto
poderá modificar ou deixar vulnerável a segurança de sua instalação.


**OBS2:** Permita que os usuários **somente** tenham acesso a máquina via CVS.


**OBS3:** Certifique-se sempre que o dono/grupo
do repositório seja <literal>root.src (ou outro grupo que tenha
criado) adicione somente usuários de confiança no grupo
<filename>src</filename> para criar novos projetos.


Exemplos:

<screen>
gleydsonm:K32dk1234k:cvsuser
anonymous::pooruser


O usuário cvs **gleydsonm** quando logar no cvs, terá as
permissões de acesso do usuário **cvsuser** do sistema.


**OBS1:** Certifique-se que o usuário local
possui permissões de gravação no diretório do CVS, caso contrário ele não
poderá fazer **commits**.  Lembre-se que as permissões de
leitura/gravação do usuário serão controladas através de arquivos do próprio
pserver, mas também é necessária a permissão de gravação do usuário no
repositório.  Isto poderá ser feito através de grupos de sistema e garante uma
dupla camada de segurança.


**OBS2:** Caso tenha preferido usar o
<literal>pserver sob um usuário diferente de root e esteja obtendo a
mensagem <literal>setgid failed: Operation not permitted, significa
que o servidor CVS não consegue mudar para o grupo referente ao usado no
diretório do repositório.  Verifique se as permissões estão adequadas e se o
grupo do usuário CVS no <filename>/etc/passwd</filename> é o mesmo que
especificou para acesso ao repositório.



</variablelist>

<listitem>

Para dar direito de leitura ao repositório, crie um arquivo chamado
<filename>readers</filename> e adicione os nomes de usuários que terão acesso
ao repositório (um por linha).  O nome que deverá ser usado é o nome do usuário
de **CVS** e não do sistema (usuário
<literal>gleydsonm, segundo o exemplo).


Exemplo:

<screen>
gleydsonm
anonymous


<listitem>

Para dar direito de gravação ao repositório, crie um arquivo chamado
<filename>writers</filename>.  Seu formato é idêntico ao arquivo
<filename>readers</filename>.


Exemplo:

<screen>
gleydsonm
macan
otavio
hmh
kov


<listitem>

Pronto, o acesso a CVS usando um banco de dados próprio está pronto!  basta dar
o commit nos arquivos, adicionar os arquivos <filename>readers</filename>,
<filename>writers</filename> e <filename>passwd</filename> no repositório (veja
<xref linkend="s-cvs-p-add"/>) para o servidor de CVS para te-lo funcionando.
Note que em versões mais novas do CVS, não é possível transferir o arquivo
<filename>passwd</filename> via rede, então será necessário cria-lo manualmente
dentro do repositório do servidor.


**OBS:** O arquivo <filename>passwd</filename>
não é transferido pelo commit por motivos de segurança, pois ele contém senhas
que podem ser capturadas e usada por pessoas maliciosas.  Será necessário
transferi-lo manualmente para o repositório do servidor remoto (você terá que
ser o usuário **root** ou ter permissões adequadas).  O
recomendável é utilizar o <command>scp (<xref linkend="s-ssh-cliente-scp"/>) para realizar transferências seguras.  .


</orderedlist>

O método de acesso do CVS aos arquivos <filename>readers</filename> e
<filename>writers</filename> é restritiva, portanto se um nome de usuário
existir no arquivo <filename>readers</filename> e <filename>writers</filename>
o que valerá será o menor nível de acesso.  Vendo os exemplos acima, os
usuários **gleydsonm e anonymous** terão somente acesso a
leitura do repositório e **macan, otavio, hmh, kov** acesso de
leitura e gravação.





 s-cvs-d-metodos-gssapi">###gssapi

Quando o CVS é compilado com o suporte a Kerberos 5, ele tenta estabelecer
automaticamente uma conexão segura usando este método.  Este método funciona
somente se o CVS estiver compilado com o suporte a Kerberos (opção
<literal>--with-gssapi).





