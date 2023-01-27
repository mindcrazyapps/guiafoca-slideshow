<!-- Converted by db4-upgrade version 1.0 -->
chapter <!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" s-cvs">###CVS

Este capítulo explica os requerimentos, instalação, configuração, segurança e
diversos modelos de configuração de acesso para trabalho em grupo utilizados
pelo <command>CVS.


Não tome-o como uma referência completa ao uso e configuração do cvs, a
pesquisa de sua info page é muito importante.

 s-cvs-intro">###Introdução ao CVS

O CVS (**Concurrent Version Software**) permite que se
organizem grupos de trabalho para desenvolvimento de projetos colaborativos.
Um projeto pode ser desde um programa em C, documentação em equipe, etc.  O uso
do CVS é recomendado para qualquer desenvolvimento de projeto que tenha vários
envolvidos trabalhando ao mesmo tempo.


Para cada mudança feita no programa, é pedido uma descrição dos trabalhos
realizados e o sistema registra todas as modificações realizadas ao longo do
desenvolvimento, permitindo voltar a uma versão anterior ou ver as mudanças
entre elas facilmente.


Imagine uma situação onde você está desenvolvendo um programa de computador e
após a última modificação ele para de funcionar.  Com o CVS é possível ver o
que foi modificado e voltar até a versão que estava funcionando para consertar
o problema.  No desenvolvimento de documentação e tradução o CVS também
desempenha um papel importante, pois com ele o tradutor pode ver o que foi
modificado entre a versão do documento original que ele usou para tradução e
uma versão recente, traduzindo apenas as diferenças.


Uma seção de <command>cvs é feita de modo interativo através do
comando <command>cvs.  Por exemplo:

<itemizedlist>
<listitem>

<literal>logar no sistema - cvs login


<listitem>

<literal>baixar um projeto - cvs checkout projeto




Cada comando do <command>cvs será explicado em detalhes no decorrer
deste capítulo.

 s-cvs-versao">###Versão

A versão do <command>CVS documentada no guia é a
**1.11.1**.  As explicações aqui certamente serão compatíveis
com versões posteriores deste programa.



 s-cvs-historia">###História

O <command>CVS é uma substituição do sistema RCS (Revision Control
System) ele possui mais recursos e foi criado sendo compatível com o RCS.


A história do CVS (extraída de sua info page) é que ele foi iniciado a partir
de um conjunto de scripts shell escritos por **Dick Grune**
que foram postados ao grupo de notícias <literal>comp.sources.unix no
volume 6 de Dezembro de 1986.  Na versão atual não estão mais presentes shell
scripts porque muitos dos conflitos de resolução de algorítmos vem deles.


Em Abril de 1989, **Brian Berliner** fez o design e programou
o CVS.  Mais tarde, Jeff Polk ajudou Brian com o design do módulo CVS.



 s-cvs-contribuindo">###Contribuindo com o CVS

Através da lista de discussão <literal>info-cvs.  Para se inscrever
envie uma mensagem com o subject "subscribe" para
<literal>info-cvs-request@gnu.org.  Outra alternativa é através do
grupo de noticias (newsgroup) da Usenet
<literal>comp.software.config-mgm.



 s-cvs-caracteristicas">###Características

Abaixo uma lista de características que tornam o CVS útil no gerenciamento de
trabalhos em grupo:

<itemizedlist>
<listitem>

Gerenciamento de projeto em equipe


<listitem>

Log de todas as alterações realizadas


<listitem>

Lock de arquivos, permitindo que somente uma determinada pessoa modifique o
arquivo durante o desenvolvimento do projeto.


<listitem>

Histórico de todas as mudanças feitas, isto permite voltar a uma versão
anterior em caso de problemas, e ver o que houve de errado com o código.


<listitem>

Os projetos podem ser hospedados em repositórios.


<listitem>

Podem ser criados diversas equipes de trabalho para cada repositórios, e
definidos quem terá ou não acesso ao repositório individualmente.  O
desenvolvedor <literal>gleydson, por exemplo, podem ter acesso ao
projeto <literal>x_beta e não ter acesso a projeto
<literal>secret_y.


<listitem>

Permissões de acesso individuais de leitura/gravação.


<listitem>

É possível criar um usuário com acesso anônimo sem dar uma conta no sistema.


<listitem>

Pode tanto utilizar o banco de dados de contas/senhas do sistema como um banco
de dados de autenticação do próprio CVS.


<listitem>

Permite utilizar diversos "métodos" de acesso ao servidor:
**local**, **pserver**,
**ext**, etc.  Cada um destes métodos será descrito a seguir.


<listitem>

Permite o acesso via ssh para usuários que já possuam conta na máquina
servidora.  Este método garante segurança no envio da senha criptografada (veja
<xref linkend="d-cripto-sniffer"para detalhes).


<listitem>

Permite visualizar facilmente o que foi modificado entre duas versões de um
arquivo.




**OBS**: O CVS possui algumas limitações e
falhas, uma delas que mais me faz falta é um suporte a protocolo pserver via
ssh que resolveria o problema de tráfego em texto plano e gerenciamento de
grupos com permissões diferenciadas.



 s-cvs-ficha">###Ficha técnica

Pacote: <systemitem role="package">cvs</systemitem>


Utilitários:

<itemizedlist>
<listitem>

<literal>cvs - Servidor/ferramenta cliente.


<listitem>

<literal>cvsbug - Envia um bug sobre o CVS para a equipe de suporte.


<listitem>

<literal>rcs2log - Converte arquivos de log do formato usado pelo
<command>RCS para o <command>CVS.  Utilizado na migração
desta ferramenta para o <command>CVS.


<listitem>

<literal>cvsconfig - Usado pela <command>Debian para
ativar/desativar o servidor <literal>pserver.  Pode também ser usado
o <literal>dpkg-reconfigure cvs para desativar o servidor
<literal>pserver e suas características.


<listitem>

<literal>cvs-makerepos - Script da <command>Debian que lê a
lista de repositórios de <filename>/etc/cvs-pserver.conf</filename>, cria os
repositórios no local apropriado, corrige as permissões do diretório e adiciona
os repositórios no servidor <literal>pserver.


<listitem>

<literal>cvs-pserver - Script da <command>Debian
responsável por fazer uma inicialização mais inteligente do servidor de CVS via
<literal>pserver, leitura e processamento de repositórios, etc.
Normalmente ele é chamado a partir do arquivo
<filename>/etc/inetd.conf</filename>.





 s-cvs-hwreq">###Requerimentos de Hardware

Para executar o <command>CVS é requerido pelo menos 3 vezes mais
memória que o tamanho do maior arquivo usado pelo projeto (para realização de
diffs entre as atualizações) e uma boa quantidade de espaço em disco.


Na realidade os requerimentos sobre o CVS dependem muito da aplicação que será
desenvolvida.  É recomendável que a máquina tenha memória suficiente para
evitar o uso de swap, que degrada bastante a performance do sistema.



 s-cvs-logs">###Arquivos de log criados pelo CVS

Problemas na inicialização do <command>CVS são registrados no arquivo
<filename>/var/log/daemon.log</filename>.  Os logs de modificações feitas nos
arquivos de um projeto no CVS são armazenadas no formato
<filename>arquivo.extensão,v</filename> (é adicionado o ",v" ao final do
arquivo para indicar que é um arquivo de controle de modificações do CVS).



 s-cvs-install">###Instalação

O <command>CVS pode ser baixado de ("http://www.w3.org/1999/xlink) [](http://www.cvshome.org)http://www.cvshome.org/.


Para pacotes <command>Debian basta apenas executar o comando:
<literal>apt-get install cvs e seguir as telas de configuração para
ter o pacote <command>CVS instalado e (opcionalmente) com o servidor
sendo executado.  Você poderá a qualquer momento reconfigurar o
<command>CVS executando: <literal>dpkg-reconfigure cvs.


Uma boa documentação de referência é encontrada no pacote <systemitem role="package">cvs-doc</systemitem>.



 s-cvs-rodando">###Iniciando o servidor/reiniciando/recarregando a configuração

A única configuração requerida é quando o <command>CVS é executado
via <literal>pserver.  Para isto, é necessária a seguinte linha no
arquivo <filename>/etc/inetd.conf</filename>

<screen>
cvspserver      stream  tcp     nowait.200      root    /usr/sbin/tcpd /usr/sbin/cvs-pserver


Note que o parâmetro "200" indica quantas vezes o processo
<command>CVS poderá ser executado por minuto no sistema.  Caso esse
número seja excedido, o serviço será desabilitado e será necessário reiniciar o
servidor <command>inetd com o comando <literal>killall -HUP
inetd para reativar o servidor CVS pserver (veja <xref linkend="rede-servicos-inetd-c"capítulo do <command>inetd para
detalhes).  Ajuste este valor de forma adequada ao seu servidor!


Veja o script <filename>cvs-pserver</filename> sendo executado no final da
linha.  Ele foi desenvolvido para lidar de forma mais inteligente com a
configuração do servidor CVS pserver.



 s-cvs-opcoescmd">###Opções de linha de comando

As seguintes opções são aceitas pelo CVS.

<variablelist>
<varlistentry>
<term>-z [num]
<listitem>

Utiliza o gzip para fazer a transferência compactada dos arquivos.  O valor
especificado pode ser de 0 a 9, quanto maior o número maior o nível de
compactação e uso da CPU.


Exemplo: <literal>cvs -z 3 checkout teste



<varlistentry>
<term>-q
<listitem>

Oculta mensagens sobre recursão de diretório durante os comandos do CVS.



<varlistentry>
<term>-d [repositório]
<listitem>

Permite especificar o repositório através da linha de comando.



<varlistentry>
<term>-e [editor]
<listitem>

Define qual é o editor de textos usado para registrar o texto de commits.



<varlistentry>
<term>-n
<listitem>

Executa o cvs em modo "simulação" não modificando qualquer arquivo do
repositório.



<varlistentry>
<term>-t
<listitem>

Mostra mensagens mostrando o processo de execução de comandos do CVS.  É
bastante útil para aprendizado do cvs usado junto com a opção
**-n**.



<varlistentry>
<term>-r
<listitem>

Torna os novos arquivos criados somente para leitura.  É a mesma coisa que
especificar a variável <replaceable>CVSREAD</replaceable>.



<varlistentry>
<term>-w
<listitem>

Torna os novos arquivos criados leitura/gravação que é o padrão.



<varlistentry>
<term>-x
<listitem>

Utiliza criptografia para a transferência dos arquivos quando é utilizado em
conjunto com o <command>Kerberos.



</variablelist>

Você pode obter detalhes sobre opções sobre um comando em especial do CVS
(**commit**, **checkout**, etc) digitando:
<literal>cvs comando --help.  Veja <xref linkend="s-cvs-p"para
exemplos sobre cada uma delas.





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





 s-cvs-p">###Criando projetos para serem usados no CVS

Esta seção descreve todos os passos necessários para colocação de um projeto
para ser desenvolvido através do CVS, os comandos do cvs, considerações a
respeito dos comandos e sua utilização através de exemplos didáticos.

 s-cvs-p-repos">###Repositório

Um repositório CVS é o local que armazena módulos e também os arquivos
administrativos (que contém permissões, etc) são armazenados em um subdiretório
chamado <filename>CVSROOT</filename>.


O acesso a um repositório é feito através de parâmetros especificados na
variável <replaceable>CVSROOT</replaceable> ou pela opção **-d
repositório** do cvs.  Veja <xref linkend="s-cvs-d"para ver
exemplos de métodos de acesso.


O Repositório pode conter um ou mais módulos, cada módulo representa um projeto
no servidor, criado após o uso do comando <literal>import.  Segue um
exemplo da estrutura de um repositório CVS:

<screen>
var/lib
     |
     +- cvs
         |- CVSROOT
         |- projeto1
         +- projeto2


O subdiretório <filename>cvs</filename> é o repositório (veja o subdiretório
<filename>CVSROOT</filename> dentro dele) e os diretórios dentro dele
<filename>projeto1</filename> e <filename>projeto2</filename> são os módulos
criados através do comando <literal>cvs import ...(veja <xref linkend="s-cvs-p-import"/>).


Para acessar o projeto do CVS, então é definido o repositório que tem
permissões de acesso na variável <literal>CVSROOT e então é executado
um comando (checkout, update, commit, etc) no módulo que desejamos utilizar:

<screen>
export CVSROOT=:ext:anonymous@servidor.org.br:/var/lib/cvs (&lt;- Repositório "cvs")
cvs checkout projeto1 (&lt;- módulo que desejamos pegar do servidor)


Nas seções seguintes serão explicados cada um dos comandos usados para
trabalhar com um projeto no <command>cvs.



 s-cvs-p-mkrepos">###Criando um repositório

Para adicionar um novo repositório no sistema, edite o arquivo
<filename>/etc/cvs-pserver.conf</filename> e defina o nome de cada repositório
na variável <replaceable>CVS_PSERV_REPOS</replaceable> separados por ":"
(exemplo: <literal>CVS_PSERV_REPOS="/var/lib/cvs:/var/lib/cvs2").


Feito isso execute o comando <command>cvs-makerepos para que os
diretórios especificados no arquivo <filename>/etc/cvs-pserver.conf</filename>
sejam criados com as devidas permissões.


Para adicionar manualmente um repositório (/var/lib/cvs), execute os seguintes
passos:

<orderedlist numeration="arabic">
<listitem>

Execute o comando <literal>cvs -d /var/lib/cvs init (para criar o
repositório e os arquivos administrativos que ficam armazenados dentro de
<filename>CVSROOT</filename>.


<listitem>

Mude as permissões do diretório para sgid com: <literal>chmod 2775
/var/lib/cvs.


<listitem>

Mude o dono/grupo com o comando: <literal>chown root.src /var/lib/cvs


<listitem>

Opcional: caso utilize o método de acesso **pserver** será
necessário adicionar a opção <literal>--allow-root=/var/lib/cvs na
linha que inicia o servidor pserver.  Este parâmetro deve ser usada para cada
repositório adicionado no servidor.


</orderedlist>

A partir de agora, seu repositório já está pronto para ser utilizado.



 s-cvs-p-login">###Logando no servidor de CVS via pserver

Quando é usado o método de acesso pserver (<xref linkend="s-cvs-d-metodos-pserver"/>), é necessário fazer para ter acesso ao
repositório.  Por exemplo, para acessar o repositório
<filename>/var/lib/cvs</filename> no servidor
<filename>servidor.org.br</filename>:

<screen>
export CVSROOT=:pserver:anonymous@servidor.org.br:/var/lib/cvs
cvs login

ou 

cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs login


Então será solicitada a senha para ter acesso ao sistema.  Note que toda a
seção de <command>cvs ocorre por comandos interativos que logo após
concluídos retornam para o interpretador de comandos.  O restante desta seção
descreverá estes comandos e como utiliza-los de maneira eficiente.


**OBS:** O uso da variável
<replaceable>CVSROOT</replaceable> torna a utilização bastante prática, assim
não precisamos especificar o repositório, método de acesso, etc.  toda vez que
usar um comando do <command>cvs.



 s-cvs-p-logout">###Encerrando uma seção de CVS

Embora que não seja necessário, após o uso do cvs é recomendável executar o
logout do servidor para encerrar sua conexão com a máquina remota.

<screen>
# (assumindo que a variável CVSROOT está definida)
cvs logout

ou 

cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs logout


**OBS:** Para os paranóicos é importante
encerrar uma seção de CVS, pois ele possui alguns bugs e um spoofing pode
tornar possível o uso de uma seção deixada aberta.



 s-cvs-p-checkout">###Baixando arquivos

O comando <literal>checkout (ou "co") é usado para fazer isto.  Para
utilizá-lo seguindo os exemplos anteriores:

<screen>
mkdir /tmp/cvs
cd /tmp/cvs
cvs checkout modulo
cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs


Será criado um subdiretório chamado <filename>modulo</filename> que contém
todos os arquivos do servidor de CVS remoto.  É necessário apenas que tenha
acesso de leitura ao servidor de CVS para executar este comando.  Você pode
usar a opção <literal>-z [num] para ativar a compactação na
transferência dos arquivos, isso acelera bastante a transferência em conexões
lentas: <literal>cvs -z 3 checkout modulo.


Também é possível especificar apenas subdiretórios de um módulo para baixa-lo
via CVS e a estrutura de diretórios criada localmente será idêntica ao do
servidor remoto.



 s-cvs-p-import">###Adicionando um novo projeto

Use o comando <literal>cvs import para adicionar um novo projeto ao
CVS.  As entradas nos arquivos administrativos serão criadas e o projeto estará
disponível para utilização dos usuários.  A sintaxe básica do comando
<literal>import é a seguinte:


<literal>cvs import [**opções**]
[**dir_modulo**] [**tag**] start


Para adicionar o projeto <literal>focalinux que reside em
<filename>/usr/src/focalinux</filename> ao cvs:

<screen>
# Primeiro exportamos o CVSROOT para dizer onde e qual repositório acessar
export CVSROOT=:ext:usuario@servidor.com.br:2401/var/lib/cvs

cd /usr/src/focalinux
cvs import documentos/focalinux tag_modulo start


Por padrão o <command>import sempre utiliza a máscara
***** para fazer a importação dos arquivos do diretório atual.
O projeto <literal>focalinux será acessado através de
$CVSROOT/documentos/focalinux (<literal>cvs checkout
documentos/focalinux), ou seja,
<filename>/var/lib/cvs/documentos/focalinux</filename> no servidor CVS terá a
cópia do focalinux.  <literal>tag_modulo define o nome que será usado
como identificador nas operações com os arquivos do CVS (pode ser usado
"focalinux" em nosso exemplo).  O parâmetro "start" diz para criar o módulo.


**OBS:** Por segurança, o diretório que contém
os arquivos deverá ser sempre um caminho relativo na estrutura de diretórios,
ou seja, você precisará entrar no diretório pai (como
<filename>/usr/src/projeto</filename>) para executar o <literal>cvs
import.  Não é permitido usar <literal>/ ou
<literal>.., isto proíbe a descida em diretórios de nível mais altos
e sérios incidentes de segurança em servidores CVS mal configurados pelo
Administrador.



 s-cvs-p-update">###Sincronizando a cópia remota com a cópia local

Este comando sincroniza a cópia remota do CVS (ou arquivo) com a cópia local
que está trabalhando em sua máquina.  Quando se trabalha nativamente no CVS em
equipe é recomendado a utilização deste comando pois alguém pode ter modificado
o arquivo antes de você, então uma incompatibilidade entre sua versão e a nova
poderia causar problemas.


Supondo que tenha acabado de modificar o arquivo <filename>main.c</filename> do
módulo <filename>cvsproj</filename>, então antes de fazer o commit (<xref linkend="s-cvs-p-commit"/>) use o update:

<screen>
cvs update main.c

ou 

cvs -d :ext:usuario@servidor.com.br:2401/var/lib/cvs update main.c


Após alguns segundos, sua cópia local ficará sincronizada com a cópia remota.
Caso ele mostre alguma mensagem de saída, verifique o arquivo para solucionar
qualquer conflito e então envie o arquivo para o servidor remoto (<xref linkend="s-cvs-p-commit"/>).


Você pode fazer o update de mais arquivos usando referências globais
(<literal>*, <literal>? ou <literal>[]).



 s-cvs-p-commit">###Enviando as mudanças para o servidor remoto

O comando "commit" (ou "ci"), envia as mudanças feitas nos arquivos locais para
o servidor remoto.  Um exemplo de commit no arquivo
<filename>main.c</filename>:

<screen>
cvs commit main.c

cvs commit main.?

cvs commit *


O editor padrão do sistema será aberto e pedirá uma descrição das modificações
para o commit.  Esta descrição será usada como referência sobre as atualizações
feitas em cada etapa do desenvolvimento.  A mensagem também pode ser
especificada usando a opção "-m mensagem", principalmente quando o texto
explicando as alterações é pequeno.


Para mudar o editor de texto padrão que será usado pelo <command>cvs,
altere a variável de ambiente <replaceable>EDITOR</replaceable> ou especifique
o editor que deseja usar na linha de comando com a opção "-e editor":

<screen>
cvs commit -e vi main.c



 s-cvs-p-add">###Adicionando um arquivo ao módulo CVS do servidor

Após criar/copiar o arquivo para seu diretório de trabalho, use o comando
<literal>add para fazer isto.  O arquivo será enviado ao servidor,
bastando apenas executa o <literal>commit para salvar o arquivo:

<screen>
cvs add main.h
cvs commit main.h



 s-cvs-p-add-dir">###Adicionando um diretório ao módulo CVS do servidor

O método para adicionar um diretório com arquivos é semelhante ao de adicionar
apenas arquivos ao cvs.  O único ponto que deve se seguido é que primeiro deve
ser adicionado o diretório (com o "cvs add") salvar no servidor remoto ("cvs
commit") e depois adicionar os arquivos existentes dentro dele (assim como
descrito em <xref linkend="s-cvs-p-add"/>).  Para adicionar o diretório
<filename>teste</filename> e seus arquivos no servidor <command>cvs
remoto:

<screen>
cvs add teste
cvs commit -m "Adicionado" teste
cvs add teste/*
cd teste
cvs commit -m "Adicionados" .


Os dois primeiros comandos agendam o diretório <filename>teste</filename> e
fazem o <literal>commit no diretório remoto.  Os dois últimos, enviam
os arquivos existentes dentro deste diretório para o servidor remoto.



 s-cvs-p-remove">###Removendo um arquivo do módulo CVS remoto

O comando para fazer isto é o "remove".  Primeiro use o <command>rm
para remover o arquivo/diretório de sua cópia local, depois execute o
<literal>remove seguido de commit para confirmar a remoção do
arquivo:

<screen>
cvs remove main.h
cvs commit main.h



 s-cvs-p-removed">###Removendo um diretório do módulo CVS remoto

Para remover um diretório, primeiro remova todos os arquivos existentes dentro
dele com o comando <command>rm e salve para o servidor (seguindo os
métodos descritos em <xref linkend="s-cvs-p-remove"/>).  O CVS não remove
diretamente diretórios vazios, uma maneira de contornar isto é usar o
<literal>update ou <literal>commit seguido da opção
<literal>-P para ignorar diretórios vazios.  Então a cópia remota do
diretório será removida do servidor:

<screen>
rm -f teste/*
cvs remove teste/.
cvs commit teste/.
cd ..
cvs checkout modulo


Depois do checkout, o subdiretório teste terá sido removido.



 s-cvs-p-release">###Dizendo que o módulo atual não está mais em uso

O comando "release" faz esta função.  Ele não é requerido, mas caso você tenha
feito modificações que ainda não foram salvas no servidor de cvs
(<literal>commit), ele alertará de arquivos modificados e perguntará
se deseja continuar.  Registrando também o abandono das modificações no
histórico do <command>cvs.  O comando pode ser acompanhado de "-d"
para remover o módulo anteriormente baixado com o "commit":

<screen>
cvs release modulo

cvs release -d modulo


O <literal>release retorna os seguintes códigos quando verifica que
as duas cópias (local e remota) não estão sincronizadas:

<variablelist>
<varlistentry>
<term>U ou P
<listitem>

Existe uma versão nova do arquivo no repositório.  Para corrigir isso, execute
o comando "update".



<varlistentry>
<term>A
<listitem>

O arquivo não foi adicionado ainda ao repositório remoto.  Se apagar o
repositório local, este arquivo não será adicionado.  Para corrigir isto,
executa o comando "add" do cvs.



<varlistentry>
<term>R
<listitem>

O arquivo foi removido localmente, mas não foi removido do servidor remoto.
Use os procedimentos em <xref linkend="s-cvs-p-remove"para corrigir a
situação.



<varlistentry>
<term>M
<listitem>

O arquivo está modificado localmente e não foi salvo ainda no servidor.  Use os
procedimentos em <xref linkend="s-cvs-p-update"e <xref linkend="s-cvs-p-commit"para salvar o arquivo.



<varlistentry>
<term>?
<listitem>

O arquivo está em seu diretório de trabalho mas não tem referências no
repositório remoto e também não está na lista de arquivos ignorados do CVS.



</variablelist>


 s-cvs-p-diff">###Visualizando diferenças entre versões de um arquivo

Com o comando "diff" é possível visualizar que diferenças o arquivo que está
sendo editado possui em relação ao arquivo do repositório remoto.  Outra
funcionalidade útil do "diff" é comparar 2 versões de arquivos do mesmo
repositório CVS.  Exemplos:

<variablelist>
<varlistentry>
<term>cvs diff main.c
<listitem>

Verifica as diferenças entre o arquivo <filename>main.c</filename> local e
remoto.



<varlistentry>
<term>cvs diff -u -r 1.1 -r 1.2 main.c
<listitem>

Mostra as diferenças em formato unificado para mostrar as diferenças entre as
versões 1.1 e 1.2 do arquivo <filename>main.c</filename>.



</variablelist>


 s-cvs-p-status">###Visualizando o status de versão de arquivos

O comando "status" permite verificar que versões do arquivo especificado está
disponível localmente, remotamente, qual a versão inicial do arquivo no
repositório, sticky tag.  Exemplos:

<variablelist>
<varlistentry>
<term>cvs status main.c
<listitem>

Verifica o status do arquivo <filename>main.c</filename>.



<varlistentry>
<term>cvs status -v main.c
<listitem>

Mostra o status do arquivo <filename>main.c</filename>, adicionalmente mostra
também as tags existentes no arquivo (versão inicial, versão do repositório).



</variablelist>


 s-cvs-p-utils">###Outros utilitários para trabalho no repositório

Além dos comandos do <command>cvs descritos aqui, existem comandos no
pacote <systemitem role="package">cvsutils</systemitem> que auxiliam desde quem
está aprendendo a utilizar o CVS (com o comando <command>cvsdo para
simular algumas operações de adição/remoção de arquivos) até profissionais que
usam o programa no dia a dia (<command>cvsu,
<command>cvsco, <command>cvschroot).





 s-cvs-cvsroot">###Arquivos administrativos em CVSROOT

Esta seção descreve a função de cada um dos arquivos administrativos, isto pode
ser útil na configuração e personalização do CVS e de seu repositório.


Para não alongar muito o capítulo, procurei colocar uma breve descrição da
função de cada um deles, o comentários e exemplos existentes nos arquivos
oferecem uma boa compreensão do seu conteúdo.

 s-cvs-cvsroot-config">###<filename>config</filename>

Este arquivo é segue os padrões do arquivos de configuração e possui alguns
parâmetros que controlam o comportamento do CVS.  Segue uma lista deles:

<variablelist>
<varlistentry>
<term><replaceable>SystemAuth</replaceable>
<listitem>

Define se será utilizado a autenticação via <filename>/etc/passwd</filename>
quando o método **pserver** for utilizado.  Note que se o
arquivo <filename>passwd</filename> for criado no <filename>CVSROOT</filename>,
o <replaceable>SystemAuth</replaceable> será definido automaticamente para
<literal>no.


Exemplo: <literal>SystemAuth=yes.



<varlistentry>
<term><replaceable>LockDir</replaceable>
<listitem>

Especifica o diretório onde serão gravados os arquivos de lock.  Caso não seja
especificado, será usado o diretório do CVS.


Exemplo: <literal>LockDir=/var/lock/cvs



<varlistentry>
<term><replaceable>TopLevelAdmin</replaceable>
<listitem>

Permite criar ou não um diretório chamado <filename>CVS</filename> no root do
diretório de trabalho durante o <literal>cvs checkout.



<varlistentry>
<term><replaceable>LogHistory</replaceable>
<listitem>

Utiliza opções para especificar o que será registrado nos arquivos de log do
<literal>CVS.

<itemizedlist>
<listitem>

<literal>TOFEWGCMAR ou <literal>all


Registra todas as operações nos logs do <command>cvs.


<listitem>

<literal>TMAR


Registra todas as operações que modificam os arquivos <filename>",v"</filename>





</variablelist>


 s-cvs-cvsroot-modules">###<filename>modules</filename>

Especifica opções e programas externos que serão usados durante a execução de
comandos no repositório CVS.



 s-cvs-cvsroot-cvswrappers">###<filename>cvswrappers</filename>

Este arquivo define ações de controle de características de arquivos, de acordo
com seu nome.


Pode ser também definidas ações através de arquivos
<filename>.cvswrappers</filename>.



 s-cvs-cvsroot-commitinfo">###<filename>commitinfo</filename>

Define programas para fazer uma checagem baseada no diretório e dizer se o
commit é permitido.



 s-cvs-cvsroot-verifymsg">###<filename>verifymsg</filename>

Especifica o programa usado para verificar as mensagens de log.



 s-cvs-cvsroot-loginfo">###<filename>loginfo</filename>

Programa que é executado após o commit.  Ele pode ser usado para tratar a
mensagem de log e definir onde ela será gravada/enviada, etc.



 s-cvs-cvsroot-cvsignore">###<filename>cvsignore</filename>

Tudo que constar neste arquivo não será gravado (commit) no cvs.  Referências
globais podem ser usadas para especificar estes arquivos.  Veja a info page do
cvs para detalhes sober seu formato.


Pode também ser especificado através de arquivos
<filename>.cvsignore</filename>.



 s-cvs-cvsroot-checkoutlist">###<filename>checkoutlist</filename>

Especifica os arquivos que deseja manter sobre o controle do CVS que se
encontram em <filename>CVSROOT</filename>.  Se adicionar um script adicional,
ou qualquer outro arquivo no diretório <filename>CVSROOT</filename> ele deverá
constar neste arquivo.



 s-cvs-cvsroot-history">###<filename>history</filename>

É usado para registrar detalhes do comando **history** do CVS.





 s-cvs-c">###Clientes de CVS

Esta seção traz alguns programas cliente em modo texto/gráfico e visualizadores
de repositórios via web.  Eles facilitam o trabalho de controle de revisão por
parte de iniciantes e flexibilidade para pessoas mais experientes, além de ter
uma interface de navegação disponível para todos os interessados em fazer
pesquisas no repositório.

 s-cvs-c-cvs">###cvs

Este é o cliente <command>Unix padrão, bastante poderoso e que opera
em modo texto.  As explicações neste capítulo do guia assumem este cliente de
<command>cvs, então as explicações sobre sua utilização se encontra
em <xref linkend="s-cvs-p"e os parâmetros de linha de comando em <xref linkend="s-cvs-opcoescmd"/>


É **altamente** recomendável a leitura caso
deseje utilizar um cliente de <command>cvs gráfico, pois os conceitos
são os mesmos.



 s-cvs-c-gcvs">###gcvs - Linux

Este é um cliente CVS em GTK+Python para <command>Linux que interage
externamente com o cliente <command>cvs externo, todas as opções do
cvs estão disponíveis através de checkboxes nas telas de comando, incluindo
suporte a compactação, visualizador gráfico da árvore de releases, histórico,
diffs, etc.


Sua instalação é bastante fácil, instale o programa com <literal>apt-get
install gcvs e execute o programa através do menu do sistema ou do
terminal.  Utilize os seguintes procedimentos para configurar e utilizar o
programa:

<orderedlist numeration="arabic">
<listitem>

Defina o repositório <replaceable>CVSROOT</replaceable> através do menu
**Admin**/**Preferences**.  Selecione o
método de acesso, entre com o login, servidor e repositório.

<screen>
Exemplo: :pserver:anonymous@servidor:/var/lib/cvs


O formato deve ser **EXATAMENTE** como o usado na variável
CVSROOT no shell, incluindo os ":".  Caso tenha erros de login, verifique o
valor de <replaceable>CVSROOT</replaceable> cuidadosamente antes de contactar o
administrador de sistemas!


<listitem>

Agora faça o login no sistema em: **Admin**,
**Login**.  Note que o status de todas as operações do
<command>cvs são mostradas na janela de status que fica na parte
inferior da tela.


<listitem>

Crie um diretório que será usado para armazenar os fontes baixados do CVS, por
exemplo: <literal>mkdir ~/projetos


<listitem>

Acesse o menu **Create**, **Checkout Module**
para baixar o projeto do CVS para sua máquina local.  Ele irá te pedir o nome
de diretório para onde o código fonte do servidor CVS será baixado.  Digite
<filename>~/projetos</filename> ou outro diretório que foi criado no passo
anterior.


**OBS:** Não utilize o nome
<filename>"cvs"</filename> para o diretório local, pois o
<command>gcvs oculta automaticamente pois os arquivos administrativos
de controle ficam neste local.


<listitem>

Altere o diretório padrão do <command>gcvs para o diretório onde
baixou o projeto (<filename>~/projetos</filename>)clicando no botão "set" no
topo da coluna esquerda do <command>gcvs.


<listitem>

Para enviar um arquivo modificado de volta ao servidor, selecione os arquivos,
clique em **Modify**, **Commit Selection**,
entre com a mensagem descrevendo as alterações e clique em "OK".


Note que os arquivos modificados serão identificados por um ícone vermelho e
seu status será "Mod.  File" (arquivo modificado).


<listitem>

Se desejar adicionar um novo projeto no CVS, entre em
**Create**, **Import Module**, entre no
diretório que deseja adicionar como um projeto no servidor de CVS.  Após isto
será feita uma checagem e mostrada uma tela de possíveis problemas que podem
ocorrer durante a importação do novo projeto.


Na próxima tela, digite o nome do módulo e caminho no servidor remoto no
primeiro campo, no segundo campo a mensagem de log para adicionar o projeto ao
servidor.  Em "Vendor tag" especifique o nome do projeto e sua versão logo
abaixo.  Clique em "OK" e aguarde a transferência dos arquivos para o servidor.


Para maiores detalhes sobre a criação de novos projetos no servidor de CVS,
veja <xref linkend="s-cvs-p-import"/>.


**OBS:** Você deverá ter permissão de gravação
para criar um novo projeto no servidor CVS.


<listitem>

A partir de agora você poderá explorar as funções do programa e fazer uso das
funções habituais do CVS.  Todas as funções de operação e opções extras do CVS
estão disponíveis na interface gráfica, basta se acostumar com sua utilização.


</orderedlist>

Após isto, explore bastante as opções do programa.  Todas as funcionalidades do
CVS estão organizadas entre os menus do programa.  Caso não entenda bem as
funções do programa, leia atentamente <xref linkend="s-cvs-p"e também não
deixe de consultar detalhes na info page do cvs.



 s-cvs-c-wincvs">###WinCVS - Windows

Este é um cliente CVS em Python para <command>Windows equivalente ao
<command>gcvs para <command>Linux.  Suas funcionalidades e
recomendações são idênticas aos do <command>gcvs.  Este cliente pode
ser baixado de: ("http://www.w3.org/1999/xlink) [](http://telia.dl.sourceforge.net/sourceforge/cvsgui/WinCvs13b13.zip">http://telia.dl.sourceforge.net/sourceforge/cvsgui/WinCvs13b13.zip
e o Python para Windows de ("http://www.w3.org/1999/xlink) [](http://starship.python.net/crew/mhammond/downloads/win32all-153.exe">http://starship.python.net/crew/mhammond/downloads/win32all-153.exe.


Para sua utilização, as explicações em <xref linkend="s-cvs-c-gcvs"são
totalmente válidas.



 s-cvs-c-maccvs">###MacCVS - Macintosh (PPC)

Idêntico ao <command>gcvs, pode ser baixado de ("http://www.w3.org/1999/xlink) [](http://telia.dl.sourceforge.net/sourceforge/cvsgui/MacCvsX-3.3a1-1.dmg">http://telia.dl.sourceforge.net/sourceforge/cvsgui/MacCvsX-3.3a1-1.dmg.



 s-cvs-c-viewcvs">###viewcvs

Este é um visualizador de repositórios CVS via web, ele precisa apenas de um
servidor web instalado com suporte a CGI.  Para instalar, execute o comando
<literal>apt-get install <systemitem role="package">viewcvs</systemitem> e siga os passos para configurar
programa.  Para adequar melhor o <command>viewcvs ao seu sistema,
edite o arquivo <filename>/etc/viewcvs/viewcvs.conf</filename>.


O <command>viewcvs possui uma interface que se parece com a navegação
de um diretório de ftp, recursos como a extração de diffs coloridos entre
versões de um arquivo selecionado, visualização de commits (com data, log do
commit, usuário, etc.), classificação da listagem exibida.


**OBS:**Leve em consideração as implicações de
segurança impostas por aplicativos cgi sendo executados em seu sistema.  Veja
<xref linkend="apache"para entender melhor o assunto.





 s-cvs-exemplo">###Exemplo de uma seção CVS

Nota: este exemplo é apenas didático, não foi feita nenhuma modificação real no
conteúdo do repositório do <command>dillo :-)

<screen>
# Definir o CVSROOT
export CVSROOT=:pserver:gleydson@ima.cipsga.org.br:/var/lib/cvs

# entrar no servidor
gleydson@host:/tmp/teste$ cvs login
Logging in to :pserver:gleydson@ima.cipsga.org.br:2401/var/lib/cvs
CVS password: &lt;password&gt;

gleydson@oberon:/tmp/teste$ 

# Pegar o módulo "dillo do cvs"
cvs -z 3 co dillo

cvs server: Updating dillo
cvs server: Updating dillo/CVSROOT
U dillo/CVSROOT/checkoutlist
U dillo/CVSROOT/commitinfo
U dillo/CVSROOT/config
U dillo/CVSROOT/cvswrappers
U dillo/CVSROOT/editinfo
U dillo/CVSROOT/loginfo
U dillo/CVSROOT/modules
U dillo/CVSROOT/notify
U dillo/CVSROOT/rcsinfo
U dillo/CVSROOT/taginfo
U dillo/CVSROOT/verifymsg
cvs server: Updating dillo/CVSROOT/Emptydir
cvs server: Updating dillo/dillo
U dillo/dillo/AUTHORS
U dillo/dillo/COPYING
U dillo/dillo/ChangeLog
U dillo/dillo/ChangeLog.old
U dillo/dillo/INSTALL
U dillo/dillo/Makefile.am
U dillo/dillo/Makefile.in
U dillo/dillo/NEWS
U dillo/dillo/README
U dillo/dillo/aclocal.m4
U dillo/dillo/config.h.in
U dillo/dillo/configure
U dillo/dillo/configure.in
U dillo/dillo/depcomp
U dillo/dillo/dillorc
U dillo/dillo/install-sh
U dillo/dillo/missing
U dillo/dillo/mkinstalldirs
U dillo/dillo/stamp-h.in
cvs server: Updating dillo/dillo/doc
U dillo/dillo/doc/Cache.txt
U dillo/dillo/doc/Cookies.txt
U dillo/dillo/doc/Dillo.txt
U dillo/dillo/doc/Dw.txt
U dillo/dillo/doc/DwImage.txt
U dillo/dillo/doc/DwPage.txt
...

# Modifica o arquivo do projeto
cd /dillo/dillo/doc
vi Cache.txt


# Update no arquivo para atualizar a cópia local com a remota
cvs update Cache.txt
M Cache.txt

gleydson@host:/tmp/teste

# Damos o commit no arquivo
cvs commit Cache.txt


# Saimos do sistema
cvs logout



