<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" etc">###Principais arquivos de configuração do diretório <filename>/etc</filename>

Este capítulo descreve a função, parâmetros e exemplos de utilização de alguns
arquivos/diretórios de configuração em <filename>/etc</filename>.  Estes
arquivos estão disponíveis por padrão na instalação básica do
<command>GNU/Linux, o que assegura um máximo de aproveitamento deste
capítulo.  Não serão descritos aqui arquivos de configuração específicos de
servidores ou daemons (com exceção do <command>inetd).


 etc-alternatives">###Diretório <filename>/etc/alternatives</filename>

Este diretório contém links para diversos aplicativos padrões utilizados pelo
sistema.  Dentre eles são encontrados links para o <filename>editor</filename>
do sistema e o <filename>xterm</filename> padrão usado pelo sistema.


Por exemplo, se você quiser usar o editor <command>jed ao invés do
<command>ae ou <command>vi, remova o link
<filename>editor</filename> com o comando <literal>rm editor,
localize o arquivo executável do <command>jed com <literal>which
jed e crie um link para ele <literal>ln -s /usr/bin/jed
editor.  De agora em diante o editor padrão usado pela maioria dos
aplicativos será o <command>jed.



 etc-devpts">###Arquivo <filename>/etc/default/devpts</filename>

Este arquivo contém algumas configurações para os pseudo terminais em
<filename>/dev/pts</filename>.



 etc-rcs">###Arquivo <filename>/etc/default/rcS</filename>

Contém variáveis padrões que alteram o comportamento de inicialização dos
scripts em <filename>/etc/rcS.d</filename>


Por exemplo, se quiser menos mensagens na inicialização do sistema, ajuste o
valor da variável <filename>VERBOSE</filename> para <literal>no.


OBS: Somente modifique aquilo que tem certeza do que está fazendo, um valor
modificado incorretamente poderá causar falhas na segurança de sua rede ou no
sistemas de arquivos do disco.



 etc-config">###Arquivo <filename>/etc/console-tools/config</filename>

Este arquivo contém configurações padrões do pacote <systemitem role="package">console-tools</systemitem> para as fontes de tela e mapas de
teclado usados pelo sistema.  A fonte de tela é especificada neste arquivo (as
fontes disponíveis no sistema estão localizadas em
<filename>/usr/share/consolefonts</filename>).


Os arquivos de mapa de teclados estão localizados no diretório
<filename>/usr/share/keymaps/</filename>.



 etc-menu-methods">###Diretório <filename>/etc/menu-methods</filename>

Este diretório contém uma lista de arquivos que são executados pelo programa
<command>update-menu para criar os menus dos programas.



 etc-menu-translate">###Arquivo <filename>/etc/menu-methods/translate_menus</filename>

Este arquivo permite fazer a tradução de nomes de menus, identificação ou
títulos usados no ambiente gráfico.



 etc-networks">###Diretório <filename>/etc/network</filename>

Este diretório contém as configurações das interfaces (placas) de rede do
sistema e outras opções úteis para a configuração/segurança da rede.



 etc-network-interfaces">###Arquivo <filename>/etc/network/interfaces</filename>

Este é o arquivo de configuração usado pelos programas <command>ifup
e <command>ifdown, respectivamente para ativar e desativas as
interfaces de rede.


O que estes utilitários fazem na realidade é carregar os utilitários
<command>ifconfig e <command>route através dos argumentos
passados do arquivo <filename>/etc/network/interfaces</filename>, permitindo
que o usuário iniciante configure uma interface de rede com mais facilidade.


Abaixo um exemplo do arquivo <filename>interfaces</filename> é o seguinte:

<screen>
iface eth0 inet static
   address 192.168.1.1
   netmask 255.255.255.0 
   network 192.168.1.0
   broadcast 192.168.1.255


As interfaces e roteamentos são configurados na ordem que aparecem neste
arquivo.  Cada configuração de interface inicia com a palavra chave
<literal>iface.  A próxima palavra é o nome da interface que deseja
configurar (da mesma forma que é utilizada pelos comandos
<command>ifconfig e <command>route).  Você pode também usar
<literal>IP aliases especificando <filename>eth0:0</filename> mas
tenha certeza que a interface real (<filename>eth0</filename>) é inicializada
antes.


A próxima palavra especifica a familia de endereços da interface; Escolha
<literal>inet para a rede TCP/IP, <literal>ipx para
interfaces IPX e <literal>IPv6 para interfaces configuradas com o
protocolo IPV6.


A palavra <literal>static especifica o método que a interface será
configurada, neste caso é uma interface com endereço estático (fixo).


Outros métodos e seus parâmetros são especificados abaixo (traduzido da página
do arquivo <command>interfaces):

<variablelist>
<varlistentry>
<term>O método **loopback**
<listitem>

É usado para configurar a interface **loopback** (lo) IPv4.



<varlistentry>
<term>O método **static**
<listitem>

É usado para configurar um endereço IPv4 fixo para a interface.  As opções que
podem ser usadas com o métodos **static** são as seguintes
(opções marcadas com * no final são requeridas na configuração):

<variablelist>
<varlistentry>
<term>address **endereço** *
<listitem>

Endereço IP da Interface de rede (por exemplo, 192.168.1.1).



<varlistentry>
<term>netmask **máscara** *
<listitem>

Máscara de rede da Interface de rede (por exemplo, 255.255.255.0).



<varlistentry>
<term>broadcast **endereço**
<listitem>

Endereço de Broadcast da interface (por exemplo, 192.168.1.255).



<varlistentry>
<term>network **endereço**
<listitem>

Endereço da rede (por exemplo, 192.168.0.0).



<varlistentry>
<term>gateway **endereço**
<listitem>

Endereço do gateway padrão (por exemplo, 192.168.1.10).  O gateway é o endereço
do computador responsável por conectar o seu computador a outra rede.  Use
somente se for necessário em sua rede.



</variablelist>


<varlistentry>
<term>O método **dhcp**
<listitem>

Este método é usado para obter os parâmetros de configuração através de um
servidor DHCP da rede através das ferramentas: <command>dhclient,
<command>pump (somente Kernels 2.2.x) ou <command>dpcpcp
(somente kernels 2.0.x e 2.2.x)

<variablelist>
<varlistentry>
<term>hostname **nome**
<listitem>

Nome da estação de trabalho que será requisitado.  (pump, dhcpcd)



<varlistentry>
<term>leasehours **leasttime**
<listitem>

Lease time preferida em horas (pump)



<varlistentry>
<term>leasetime **leasetime**
<listitem>

Lease time preferida em segundos (dhcpcd)



<varlistentry>
<term>vendor **vendedor**
<listitem>

Identificador do vendedor (dhcpcd)



<varlistentry>
<term>client **identificação**
<listitem>

Identificação do cliente (dhcpcd)



</variablelist>

Exemplo:

<screen>
iface eth0 inet dhcp
 leasehours 6
 client estacao 10



<varlistentry>
<term>O método **bootp**
<listitem>

Este método pode ser usado para obter um endereço via <command>bootp:

<variablelist>
<varlistentry>
<term>bootfile <filename>arquivo</filename>
<listitem>

Diz ao servidor para utilizar <filename>arquivo</filename> como arquivo de
inicialização



<varlistentry>
<term>server **endereço**
<listitem>

Especifica o endereço do servidor <command>bootp.



<varlistentry>
<term>hwaddr **endereço**
<listitem>

Usa **endereço** como endereço de hardware no lugar do
endereço original.



</variablelist>


</variablelist>

Algumas opções se aplicam a todas as interfaces e são as seguintes:

<variablelist>
<varlistentry>
<term>noauto
<listitem>

Não configura automaticamente a interface quando o <command>ifup ou
<command>ifdown são executados com a opção <literal>-a
(normalmente usada durante a inicialização ou desligamento do sistema).



<varlistentry>
<term>pre-up <literal>comando
<listitem>

Executa o <literal>comando antes da inicialização da interface.



<varlistentry>
<term>up <literal>comando
<listitem>

Executa o <literal>comando após a interface ser iniciada.



<varlistentry>
<term>down <literal>comando
<listitem>

Executa o <literal>comando antes de desativar a interface.



<varlistentry>
<term>pre-down <literal>comando
<listitem>

Executa o <literal>comando após desativar a interface.



</variablelist>

Os comandos que são executados através das opções **up**,
**pre-up** e **down** podem aparecer várias
vezes na mesma interface, eles são executados na seqüência que aparecem.  Note
que se um dos comandos falharem, nenhum dos outros será executado.  Você pode
ter certeza que os próximos comandos serão executados adicionando <literal>||
true ao final da linha de comando.



 etc-networks-options">###Arquivo <filename>/etc/networks/options</filename>

Este arquivo contém opções que serão aplicadas as interfaces de rede durante a
inicialização do sistema.  Este arquivo é lido pelo script de inicialização
<filename>/etc/init.d/network</filename> que verifica os valores e aplica as
modificações apropriadas no kernel.



 etc-pam">###Diretório <filename>/etc/pam.d</filename>

Este diretório possui arquivos de configuração de diversos módulos PAM
existentes em seu sistema.



 etc-ppp">###Diretório <filename>/etc/ppp</filename>

Contém arquivos de configuração usados pelo daemon pppd para fazer uma conexão
com uma rede PPP externa, criados manualmente ou através do
<command>pppconfig.



 etc-security">###Diretório <filename>/etc/security</filename>

Este diretório contém arquivos para controle de segurança e limites que serão
aplicados aos usuários do sistema.  O funcionamento de muitos dos arquivos
deste diretório depende de modificações nos arquivos em
<filename>/etc/pam.d</filename> para habilitar as funções de controle, acesso e
restrições.



 etc-security-access">###Arquivo <filename>/etc/security/access.conf</filename>

É lido no momento do login do usuário e permite definir quem terá acesso ao
sistema e de onde tem permissão de acessar sua conta.  O formato deste arquivo
são 3 campos separados por <literal>:, cada linha contendo uma regra
de acesso.


O primeiro campo deve conter o caracter <literal>+ ou
<literal>- para definir se aquela regra permitirá (+) ou bloqueará(-)
o acesso do usuário.


O segundo campo deve conter uma lista de logins, grupos, usuário@computador ou
a palavra <literal>ALL (confere com tudo) e <literal>EXCEPT
(excessão).


O terceiro campo deve conter uma lista de terminais tty (para logins locais),
nomes de computadores, nomes de domínios (iniciando com um
<literal>.), endereço IP de computadores ou endereço IP de redes
(finalizando com <literal>.).  Também pode ser usada a palavra
<literal>ALL, <literal>LOCAL e <literal>EXCEPT
(atinge somente máquinas locais conhecidas pelo sistema).


Abaixo um exemplo do <filename>access.conf</filename>

<screen>
# Somente permite o root entrar em tty1
#
-:ALL EXCEPT root:tty1

# bloqueia o logins do console a todos exceto whell, shutdown e sync.
#
-:ALL EXCEPT wheel shutdown sync:console

# Bloqueia logins remotos de contas privilegiadas (grupo wheel).
#
-:wheel:ALL EXCEPT LOCAL .win.tue.nl

# Algumas contas não tem permissão de acessar o sistema de nenhum lugar:
#
-:wsbscaro wsbsecr wsbspac wsbsym wscosor wstaiwde:ALL

# Todas as outras contas que não se encaixam nas regras acima, podem acessar de 
# qualquer lugar



 etc-securith-limits">###Arquivo <filename>/etc/security/limits.conf</filename>

Defini limites de uso dos recursos do sistema para cada usuário ou grupos de
usuários.  Os recursos são descritos em linhas da seguinte forma:

<screen>
#&lt;dominio&gt;          &lt;tipo&gt;  &lt;item&gt;  &lt;valor&gt;


O <literal>domínio pode ser um nome de usuário, um grupo
(especificado como <literal>@grupo) ou o coringa
<literal>*.


O <literal>tipo pode ser <literal>soft para o limite
mínimos e <literal>hard para o limite máximo.  O campo
<literal>item pode ser um dos seguintes:

<itemizedlist>
<listitem>

<literal>core - limita o tamanho do arquivo core (KB)


<listitem>

<literal>data - tamanho máximo de dados (KB)


<listitem>

<literal>fsize - Tamanho máximo de arquivo (KB)


<listitem>

<literal>memlock - Espaço máximo de endereços bloqueados na memória
(KB)


<listitem>

<literal>nofile - Número máximo de arquivos abertos


<listitem>

<literal>rss - Tamanho máximo dos programas residentes (KB)


<listitem>

<literal>stack - Tamanho máximo de pilha (KB)


<listitem>

<literal>cpu - Tempo máximo usado na CPU (MIN)


<listitem>

<literal>nproc - Número máximo de processos


<listitem>

<literal>as - Limite de espaço de endereços


<listitem>

<literal>maxlogins - Número máximo de logins deste usuário


<listitem>

<literal>priority - Prioridade que os programas deste usuário serão
executados




Abaixo um exemplo de arquivo <filename>/etc/security/limits.conf</filename>:

<screen>
 
#&lt;dominio&gt;      &lt;tipo&gt;  &lt;item&gt;         &lt;valor&gt;

*               soft    core            0
*               hard    rss             10000
@student        hard    nproc           20
@faculty        soft    nproc           20
@faculty        hard    nproc           50
ftp             hard    nproc           0
@student        -       maxlogins       4



 etc-crontab">###Arquivo <filename>/etc/crontab</filename>

Arquivo que contém a programação de programas que serão executados em
horários/datas programadas.


Veja <xref linkend="manut-cron"para mais detalhes sobre o formato deste
arquivo e outras opções.



 s28.16">###Arquivo <filename>/etc/fstab</filename>

Contém detalhes para a montagem dos sistemas de arquivos do sistema.  Veja
<xref linkend="disc-fstab"para detalhes sobre o formato deste arquivo.



 s28.17">###Arquivo <filename>/etc/group</filename>

Lista de grupos existentes no sistema.  Veja <xref linkend="cmdc-incluirgrupo"para mais detalhes sobre o formato deste arquivo.



 etc-gshadow">###Arquivo <filename>/etc/gshadow</filename>

Senhas ocultas dos grupos existentes no sistema (somente o usuário
<literal>root pode ter acesso a elas).  Use o utilitário
<command>shadowconfig para ativar/desativar o suporte a senhas
ocultas.



 s28.19">###Arquivo <filename>/etc/host.conf</filename>

Veja <xref linkend="rede-dns-a-hostconf"/>.



 s28.20">###Arquivo <filename>/etc/hostname</filename>

Arquivo lido pelo utilitário <command>hostname para definir o nome de
sua estação de trabalho.



 s28.21">###Arquivo <filename>/etc/hosts</filename>

Banco de dados DNS estático que mapeia o nome ao endereço IP da estação de
trabalho (ou vice versa).  Veja <xref linkend="rede-dns-a-hosts"para mais
detalhes sobre o formato deste arquivo.



 s28.22">###Arquivo <filename>/etc/hosts.allow</filename>

Controle de acesso do wrapper TCPD que permite o acesso de determinadas de
determinados endereços/grupos aos serviços da rede.  Veja <xref linkend="rede-seg-tcpd-a"para detalhes sobre o formato deste arquivo.



 s28.23">###Arquivo <filename>/etc/hosts.deny</filename>

Controle de acesso do wrapper TCPD que bloqueia o acesso de determinados
endereços/grupos aos serviços da rede.  Este arquivo é somente lido caso o
<filename>/etc/hosts.allow</filename> não tenha permitido acesso aos serviços
que contém.  Um valor padrão razoavelmente seguro que pode ser usado neste
arquivo que serve para a maioria dos usuários domésticos é:

<screen>
ALL: ALL


caso o acesso ao serviço não tenha sido bloqueado no
<filename>hosts.deny</filename>, o acesso ao serviço é permitido.


Veja <xref linkend="rede-seg-tcpd-d"para detalhes sobre o formato deste
arquivo.



 s28.24">###Arquivo <filename>/etc/hosts.equiv</filename>

Veja <xref linkend="rede-seg-tcpd-e"/>.



 s28.25">###Arquivo <filename>/etc/inetd.conf</filename>

Veja <xref linkend="rede-servicos-inetd-c"/>.



 etc-inittab">###Arquivo <filename>/etc/inittab</filename>

Este é o arquivo de configuração utilizado pelo programa
<command>init para a inicialização do sistema.  Para mais detalhes
sobre o formato deste arquivo, consulte a página de manual do
**inittab**.



 etc-inputrc">###Arquivo <filename>/etc/inputrc</filename>

Este arquivo contém parâmetros para a configuração do teclado.  Veja o final da
seção <xref linkend="cfg-acentuacao-t"e a página de manual do
**inputrc** para mais detalhes.



 etc-issue">###Arquivo <filename>/etc/issue</filename>

Contém um texto ou mensagem que será mostrada antes do login do sistema.



 etc-issue-n">###Arquivo <filename>/etc/issue.net</filename>

Mesma utilidade do <filename>/etc/issue</filename> mas é mostrado antes do
login de uma seção <command>telnet.  Outra diferença é que este
arquivo aceita os seguintes tipos de variáveis:

<itemizedlist>
<listitem>

<literal>%t - Mostra o terminal tty atual.


<listitem>

<literal>%h - Mostra o nome de domínio completamente qualificado
(FQDN).


<listitem>

<literal>%D - Mostra o nome do domínio NIS.


<listitem>

<literal>%d - Mostra a data e hora atual.


<listitem>

<literal>%s - Mostra o nome do Sistema Operacional.


<listitem>

<literal>%m - Mostra o tipo de hardware do computador.


<listitem>

<literal>%r - Mostra a revisão do Sistema Operacional.


<listitem>

<literal>%v - Mostra a versão do Sistema Operacional.


<listitem>

<literal>%% - Mostra um simples sinal de porcentagem (%).





 s28.30">###Arquivo <filename>/etc/lilo.conf</filename>

Arquivo de configuração do gerenciador de partida <command>lilo.
Veja <xref linkend="boot-lilo"e <xref linkend="boot-lilo-exemplo"/>.



 etc-login-d">###Arquivo <filename>/etc/login.defs</filename>

Definições de configuração para o pacote login



 s28.32">###Arquivo <filename>/etc/modules</filename>

Veja <xref linkend="kern-arquivos-modules"/>.



 s28.33">###Arquivo <filename>/etc/modules.conf</filename>

Veja <xref linkend="kern-arquivos-modulesconf"/>.



 etc-motd">###Arquivo <filename>/etc/motd</filename>

Mostra um texto ou mensagem após o usuário se logar com sucesso no sistema.
Também é usado pelo telnet, ftp, e outros servidores que requerem autenticação
do usuário (nome e senha).



 etc-mtab">###Arquivo <filename>/etc/mtab</filename>

Lista os sistemas de arquivos montados atualmente no sistema.  Sua função é
idêntica ao <filename>/proc/mounts</filename>.



 s28.36">###Arquivo <filename>/etc/networks</filename>

Veja <xref linkend="rede-dns-a-networks"/>.



 etc-passwd">###Arquivo <filename>/etc/passwd</filename>

É o arquivo mais cobiçado por Hackers porque contém os dados pessoais do
usuário como o login, uid, telefone e senha (caso seu sistema esteja usando
senhas ocultas, a senha terá um <literal>* no lugar e as senhas reais
estarão armazenadas no arquivo <filename>/etc/shadow</filename>).



 etc-printcap">###Arquivo <filename>/etc/printcap</filename>

Banco de dados de configuração da impressora, usado por daemons de impressão
como o <command>lpr e <command>lprng.



 s28.39">###Arquivo <filename>/etc/protocols</filename>

Veja <xref linkend="rede-outros-protocols"/>.



 s28.40">###Arquivo <filename>/etc/resolv.conf</filename>

Veja <xref linkend="rede-dns-a-resolv"/>.



 serial-c">###Arquivo <filename>/etc/serial.conf</filename>

Configurações das portas seriais do sistema.  Veja a página de manual do
**serial.conf** e a página de manual do utilitário
<command>setserial para detalhes de como configurar adequadamente a
taxa de transmissão serial conforme seu dispositivo.



 s28.42">###Arquivo <filename>/etc/services</filename>

Veja <xref linkend="rede-outros-services"/>.



 etc-shadow">###Arquivo <filename>/etc/shadow</filename>

Este arquivo armazena as senhas criptografadas caso estiver usando o recurso de
senhas ocultas.  Este arquivo somente pode ser lido pelo usuário
<literal>root.



 etc-shells">###Arquivo <filename>/etc/shells</filename>

Contém uma lista de interpretadores de comando (shells) válidos no sistema.



 etc-syslog-c">###Arquivo <filename>/etc/syslog.conf</filename>

Contém configurações para definir o que será registrado nos arquivos de log em
<filename>/var/log</filename> do sistema.  Veja a página de manual
**syslog.conf** e dos programas <command>klog e
<command>syslogd para entender o formato usado neste arquivo.



 etc-timezones">###Arquivo <filename>/etc/timezone</filename>

Contém a sua localização para cálculo correto do seu fuso-horário local.



