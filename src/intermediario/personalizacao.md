<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inter;avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" pers">###Personalização do Sistema

Este capítulo ensina como personalizar algumas características de seu sistema
<command>GNU/Linux.


 pers-varamb">###Variáveis de Ambientes

É um método simples e prático que permite a especificação de opções de
configuração de programas sem precisar mexer com arquivos no disco ou opções.
Algumas variáveis do <command>GNU/Linux afetam o comportamento de
todo o Sistema Operacional, como o idioma utilizado e o path (veja <xref linkend="run-path"/>) .  Variáveis de ambientes são nomes que contém algum
valor e tem a forma <literal>Nome=Valor.  As variáveis de ambiente
são individuais para cada usuário do sistema ou consoles virtuais e permanecem
residentes na memória RAM até que o usuário saia do sistema (logo-off) ou até
que o sistema seja desligado.


As variáveis de ambiente são visualizadas/criadas através do comando
<command>set ou <literal>echo $NOME (apenas visualiza) e
exportadas para o sistemas com o comando <literal>export NOME=VALOR.


Nos sistemas <command>Debian, o local usado para especificar
variáveis de ambiente é o <filename>/etc/environment</filename> (veja <xref linkend="pers-environment"/>).  Todas as variáveis especificadas neste arquivos
serão inicializadas e automaticamente exportadas na inicialização do sistema.


Exemplo: Para criar uma variável chamada <filename>TESTE</filename> que
contenha o valor <literal>123456 digite: <literal>export
TESTE=123456.  Agora para ver o resultado digite: <literal>echo
$TESTE ou <literal>set|grep TESTE.  Note que o
<literal>$ que antecede o nome <filename>TESTE</filename> serve para
identificar que se trata de uma variável e não de um arquivo comum.



 pers-idioma">###Modificando o Idioma usado em seu sistema

O idioma usado em seu sistema pode ser modificado facilmente através das
variáveis de ambiente.  Atualmente a maioria dos programas estão sendo
**localizados**.  A localização é um recurso que especifica
arquivos que contém as mensagens do programas em outros idiomas.  Você pode
usar o comando <command>locale para listar as variáveis de
localização do sistema e seus respectivos valores.  As principais variáveis
usadas para determinar qual idioma os programas <literal>localizados
utilizarão são:

<itemizedlist>
<listitem>

<filename>LANG</filename> - Especifica o idioma_PAIS local.  Podem ser
especificados mais de um idioma na mesma variável separando-os com
<literal>:, desta forma caso o primeiro não esteja disponível para o
programa o segundo será verificado e assim por diante.  A língua Inglesa é
identificada pelo código <literal>C e usada como padrão caso nenhum
locale seja especificado.


Por exemplo: <literal>export LANG=pt_BR, <literal>export
LANG=pt_BR:pt_PT:C


<listitem>

<filename>LC_MESSAGES</filename> - Especifica o idioma que serão mostradas as
mensagens dos programas.  Seu formato é o mesmo de <filename>LANG</filename>.


<listitem>

<filename>LC_ALL</filename> - Configura todas as variáveis de localização de
uma só vez.  Seu formato é o mesmo de <filename>LANG</filename>.




As mensagens de localização estão localizadas em arquivos individuais de cada
programa em <filename>/usr/share/locale/[Idioma]/LC_MESSAGES</filename> .  Elas
são geradas através de arquivos <literal>potfiles (arquivos com a
extensão <filename>.po</filename> ou <filename>.pot</filename> e são gerados
catálogos de mensagens <filename>.mo</filename>.  As variáveis de ambiente
podem ser especificadas no arquivo <filename>/etc/environment</filename> desta
forma as variáveis serão carregadas toda a vez que seu sistema for iniciado.
Você também pode especificar as variáveis de localização em seu arquivos de
inicialização <filename>.bash_profile</filename>, <filename>.bashrc</filename>
ou <filename>.profile</filename> assim toda a vez que entrar no sistema, as
variáveis de localização personalizadas serão carregadas.


Siga as instruções a seguir de acordo com a versão de sua distribuição
<command>Debian:

<variablelist>
<varlistentry>
<term>Debian 4.0
<listitem>

Acrescente a linha <literal>pt_BR ISO-8859-1 no arquivo
<filename>/etc/locale.gen</filename>, rode o utilitário
<command>locale-gen para gerar os locales.  Agora acrescente as
variáveis de localização no arquivo <filename>/etc/locale.def</filename>
seguindo a forma:

<screen>
export LANG=pt_BR
export LC_ALL=pt_BR
export LC_MESSAGES=pt_BR


Note que o arquivo <filename>/etc/environment</filename> também pode ser usado
para tal tarefa, mas o <filename>locales.def</filename> foi criado
especialmente para lidar com variáveis de localização na
<command>Debian 4.0.



</variablelist>

Para as mensagens e programas do X-Window usarem em seu idioma local, é preciso
colocar as variáveis no arquivo <filename>~/.xserverrc</filename> do diretório
home de cada usuário e dar a permissão de execução neste arquivo
(<literal>chmod 755 .xserverrc).  Lembre-se de incluir o caminho
completo do arquivo executável do seu gerenciador de janelas na última linha
deste arquivo (sem o <literal>&amp; no final), caso contrário o Xserver
será finalizado logo após ler este arquivo.


Abaixo exemplos de localização com as explicações:

<itemizedlist>
<listitem>

<literal>export LANG=pt_BR - Usa o idioma pt_BR como língua padrão do
sistema.  Caso o idioma Portugues do Brasil não esteja disponível, C é usado
(Inglês).


<listitem>

<literal>export LANG=C - Usa o idioma Inglês como padrão (é a mesma
coisa de não especificar <filename>LANG</filename>, pois o idioma Inglês é
usado como padrão).


<listitem>

<literal>export LANG=pt_BR:pt_PT:es_ES:C - Usa o idioma Português do
Brasil como padrão, caso não esteja disponível usa o Português de Portugal, se
não estiver disponível usa o Espanhol e por fim o Inglês.


<listitem>

<literal>LANG=es_ES ls --help - Executa apenas o comando <literal>ls
--help usando o idioma es_ES (sem alterar o locale do sistema).




É recomendável usar a variável <filename>LC_ALL</filename> para especificar o
idioma, desta forma todos os outras variáveis (<filename>LANG, MESSAGES,
LC_MONETARY, LC_NUMERIC, LC_COLLATE, LC_CTYPE e LC_TIME</filename>) serão
configuradas automaticamente.



 pers-alias">###alias

Permite criar um apelido a um comando ou programa.  Por exemplo, se você gosta
de digitar (como eu) o comando <literal>ls --color=auto para ver uma
listagem longa e colorida, você pode usar o comando <command>alias
para facilitar as coisas digitando: <literal>alias ls='ls
--color=auto' (não se esqueça da meia aspa 'para identificar o
comando').  Agora quando você digitar <literal>ls, a listagem será
mostrada com cores.


Se você digitar <literal>ls -la, a opção <literal>-la será
adicionada no final da linha de comando do alias: <literal>ls --color=auto
-la, e a listagem também será mostrada em cores.


Se quiser utilizar isto toda vez que entrar no sistema, veja <xref linkend="pers-bashprofile"e <xref linkend="pers-bashrc"/>.



 pers-profile">###Arquivo <filename>/etc/profile</filename>

Este arquivo contém comandos que são executados para **todos**
os usuários do sistema no momento do login.  Somente o usuário root pode ter
permissão para modificar este arquivo.


Este arquivo é lido antes do arquivo de configuração pessoal de cada usuário
(<filename>.profile</filename>(root) e <filename>.bash_profile</filename>).


Quando é carregado através de um shell que requer login (nome e senha), o
<command>bash procura estes arquivos em seqüência e executa os
comandos contidos, caso existam:

<orderedlist numeration="arabic">
<listitem>

<filename>/etc/profile</filename>


<listitem>

<filename>~/.bash_profile</filename>


<listitem>

<filename>~/.bash_login</filename>


<listitem>

<filename>~/.profile</filename>


</orderedlist>

Ele **interrompe** a pesquisa assim que localiza o primeiro
arquivo no diretório do usuário (usando a sequência acima).  Por exemplo, se
você tem o arquivo <filename>~/.bash_login</filename> e
<filename>~/.bash_profile</filename> em seu diretório de usuário, ele
processará o <filename>/etc/profile</filename> e após isto o
<filename>~/.bash_profile</filename>, mas nunca processará o
<filename>~/.bash_login</filename> (a menos que o
<filename>~/.bash_profile</filename> seja apagado ou renomeado).


Caso o <command>bash seja carregado através de um shell que não
requer login (um terminal no X, por exemplo), o seguinte arquivo é executado:
<filename>~/.bashrc</filename>.


Observação: Nos sistemas Debian, o profile do usuário root está configurado no
arquivo <filename>/root/.profile</filename>.  A razão disto é porque se o
<command>bash for carregado através do comando <command>sh,
ele fará a inicialização clássica deste shell lendo primeiro o arquivo
<filename>/etc/profile</filename> e após o <filename>~/.profile</filename> e
ignorando o <filename>.bash_profile</filename> e <filename>.bashrc</filename>
que são arquivos de configuração usados somente pelo <command>Bash.
Exemplo, inserindo a linha <literal>mesg y no arquivo
<filename>/etc/profile</filename> permite que todos os usuários do sistema
recebam pedidos de <filename>talk</filename> de outros usuários.  Caso um
usuário não quiser receber pedidos de <command>talk, basta somente
adicionar a linha <literal>mesg n no arquivo pessoal
<filename>.bash_profile</filename>.



 pers-bashprofile">###Arquivo <filename>.bash_profile</filename>

Este arquivo reside no diretório pessoal de cada usuário.  É executado por
shells que usam autenticação (nome e senha).
<filename>.bash_profile</filename> contém comandos que são executados para o
usuário no momento do login no sistema após o
<filename>/etc/profile</filename>.  Note que este é um arquivo oculto pois tem
um "."  no inicio do nome.


Por exemplo colocando a linha: <literal>alias ls='ls --colors=auto'
no <filename>.bash_profile</filename>, cria um apelido para o comando
<command>ls --colors=auto usando <command>ls, assim toda
vez que você digitar <literal>ls será mostrada a listagem colorida.



 pers-bashrc">###Arquivo <filename>.bashrc</filename>

Possui as mesmas características do <filename>.bash_profile</filename> mas é
executado por shells que não requerem autenticação (como uma seção de terminal
no X).


Os comandos deste arquivo são executados no momento que o usuário inicia um
shell com as características acima.  Note que este é um arquivo oculto pois tem
um "."  no inicio do nome.



 pers-hushlogin">###Arquivo <filename>.hushlogin</filename>

Deve ser colocado no diretório pessoal do usuário.  Este arquivo faz o
<command>bash pular as mensagens do <filename>/etc/motd</filename>,
número de e-mails, etc.  Exibindo imediatamente o aviso de comando após a
digitação da senha.



 pers-environment">###Arquivo <filename>/etc/environment</filename>

Armazena as variáveis de ambiente que são exportadas para todo o sistema.  Uma
variável de ambiente controla o comportamento de um programa, registram
detalhes úteis durante a seção do usuário no sistema, especificam o idioma das
mensagens do sistema, etc.


Exemplo do conteúdo de um arquivo <filename>/etc/environment</filename>:

<screen>
LANG=pt_BR
LC_ALL=pt_BR
LC_MESSAGES=pt_BR



 pers-conf-skel">###Diretório <filename>/etc/skel</filename>

Este diretório contém os modelos de arquivos <filename>.bash_profile</filename>
e <filename>.bashrc</filename> que serão copiados para o diretório pessoal dos
usuários no momento que for criada uma conta no sistema.  Desta forma você não
precisará configurar estes arquivos separadamente para cada usuário.



