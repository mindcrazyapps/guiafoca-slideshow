<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inter;avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" log">###Arquivos e daemons de Log

A atividade dos programas são registradas em arquivos localizados em
<filename>/var/log</filename> .  Estes arquivos de registros são chamados de
**logs** e contém a data, hora e a mensagem emitida pelo
programa (violações do sistema, mensagens de erro, alerta e outros eventos)
entre outros campos.  Enfim, muitos detalhes úteis ao administrador tanto para
acompanhar o funcionamento do seu sistema, comportamento dos programas ou
ajudar na solução e prevenção de problemas.


Alguns programas como o <command>Apache, <command>exim,
<command>ircd e <command>squid criam diversos arquivos de
log e por este motivo estes são organizados em sub-diretórios (a mesma técnica
é usada nos arquivos de configuração em <filename>/etc</filename>, conforme a
padrão FHS atual).


 s18.1">###Formato do arquivo de log

Um arquivo de log é normalmente composto pelos seguintes campos:

<screen>
Data|Hora|Máquina|daemon|mensagem


O campo **máquina** é o nome do computador que registrou a
mensagem (a máquina pode atuar como um servidor de logs registrando mensagens
de diversos computadores em sua rede).  O campo **daemon**
indica qual programa gravou a **mensagem**.


O uso dos utilitários do console pode ajudar muito na pesquisa e monitoração
dos logs, por exemplo, para obter todas as mensagens do daemon
<command>kernel da estação de trabalho <literal>wrk1,
eliminando os campos "wrk1" e "kernel":

<screen>
cat /var/log/*|grep 'wrk1'|grep 'kernel'|awk '{print $1 $2 $3 $6 $7 $8 $9 $10 $11 $12}'


Os parâmetros "$1", "$2" do comando <command>awk indica que campos
serão listados, (omitimos $4 e $5 que são respectivamente "wrk1" e "kernel").
Um bom utilitário para monitoração de logs está documentado em <xref linkend="log-uteis-logcheck"/>.



 s18.2">###Daemons de log do sistema

Os daemons de log do sistema registram as mensagens de saída do kernel
(<command>klogd) e sistema (<command>syslogd) nos arquivos
em <filename>/var/log</filename> .


A classificação de qual arquivo em <filename>/var/log</filename> receberá qual
tipo de mensagem é controlado pelo arquivo de configuração
<filename>/etc/syslog.conf</filename> através de
**facilidades** e **níveis** (veja <xref linkend="log-syslogd-exemplo"para detalhes).


 log-syslogd">###syslogd

Este daemon controla o registro de logs do sistema.


<command>syslogd [**opções**]

<variablelist>
<varlistentry>
<term>**opções**
<term>-f
<listitem>

Especifica um arquivo de configuração alternativo ao
<filename>/etc/syslog.conf</filename>.



<varlistentry>
<term>-h
<listitem>

Permite redirecionar mensagens recebidas a outros servidores de logs
especificados.



<varlistentry>
<term>-l [computadores]
<listitem>

Especifica um ou mais computadores (separados por ":") que deverão ser
registrados somente com o nome de máquina ao invés do FQDN (nome completo,
incluindo domínio).



<varlistentry>
<term>-m [minutos]
<listitem>

Intervalo em **minutos** que o syslog mostrará a mensagem
<literal>--MARK--.  O valor padrão padrão é 20 minutos, 0 desativa.



<varlistentry>
<term>-n
<listitem>

Evita que o processo caia automaticamente em background.  Necessário
principalmente se o <command>syslogd for controlado pelo
<command>init.



<varlistentry>
<term>-p [soquete]
<listitem>

Especifica um soquete UNIX alternativo ao invés de usar o padrão
<filename>/dev/log</filename>.



<varlistentry>
<term>-r
<listitem>

Permite o recebimento de mensagens através da rede através da porta UDP 514.
Esta opção é útil para criar um servidor de logs centralizado na rede.  Por
padrão, o servidor <command>syslog rejeitará conexões externas.



<varlistentry>
<term>-s [domínios]
<listitem>

Especifica a lista de domínios (separados por ":") que deverão ser retirados
antes de enviados ao log.



<varlistentry>
<term>-a [soquetes]
<listitem>

Especifica soquetes adicionais que serão monitorados.  Esta opção será
necessária se estiver usando um ambiente <command>chroot.  É possível
usar até 19 soquetes adicionais



<varlistentry>
<term>-d
<listitem>

Ativa o modo de depuração do <command>syslog.  O syslog permanecerá
operando em primeiro plano e mostrará as mensagens no terminal atual.



</variablelist>

Na distribuição <command>Debian, o daemon <command>syslogd
é iniciado através do script <filename>/etc/init.d/sysklogd</filename>.


 log-syslogd-exemplo">###Arquivo de configuração <filename>syslog.conf</filename>

O arquivo de configuração <filename>/etc/syslog.conf</filename> possui o
seguinte formato:

<screen>
facilidade.nível                    destino


A **facilidade** e **nível** são separadas
por um "."  e contém parâmetros que definem o que será registrado nos arquivos
de log do sistema:

<itemizedlist>
<listitem>

<literal>facilidade - É usada para especificar que tipo de programa
está enviando a mensagem.  Os seguintes níveis são permitidos (em ordem
alfabética):

<itemizedlist>
<listitem>

<literal>auth - Mensagens de segurança/autorização (é recomendável
usar authpriv ao invés deste).


<listitem>

<literal>authpriv - Mensagens de segurança/autorização (privativas).


<listitem>

<literal>cron - Daemons de agendamento (<command>cron e
<command>at).


<listitem>

<literal>daemon - Outros daemons do sistema que não possuem
facilidades específicas.


<listitem>

<literal>ftp - Daemon de ftp do sistema.


<listitem>

<literal>kern - Mensagens do kernel.


<listitem>

<literal>lpr - Subsistema de impressão.


<listitem>

<literal>local0 a local7 - Reservados para uso local.


<listitem>

<literal>mail - Subsistema de e-mail.


<listitem>

<literal>news - Subsistema de notícias da USENET.


<listitem>

<literal>security - Sinônimo para a facilidade
<literal>auth (evite usa-la).


<listitem>

<literal>syslog - Mensagens internas geradas pelo
<command>syslogd.


<listitem>

<literal>user - Mensagens genéricas de nível do usuário.


<listitem>

<literal>uucp - Subsistema de UUCP.


<listitem>

<literal>* - Confere com todas as facilidades.




Mais de uma facilidade pode ser especificada na mesma linha do
<filename>syslog.conf</filename> separando-as com ",".


<listitem>

<literal>nível - Especifica a importância da mensagem.  Os seguintes
níveis são permitidos (em ordem de importância invertida; da mais para a menos
importante):

<itemizedlist>
<listitem>

<literal>emerg - O sistema está inutilizável.


<listitem>

<literal>alert - Uma ação deve ser tomada imediatamente para resolver
o problema.


<listitem>

<literal>crit - Condições críticas.


<listitem>

<literal>err - Condições de erro.


<listitem>

<literal>warning - Condições de alerta.


<listitem>

<literal>notice - Condição normal, mas significante.


<listitem>

<literal>info - Mensagens informativas.


<listitem>

<literal>debug - Mensagens de depuração.


<listitem>

<literal>* - Confere com todos os níveis.


<listitem>

<literal>none - Nenhuma prioridade.




Além destes níveis os seguintes sinônimos estão disponíveis:

<itemizedlist>
<listitem>

<literal>error - Sinônimo para o nível err.


<listitem>

<literal>panic - Sinônimo para o nível emerg.


<listitem>

<literal>warn - Sinônimo para o nível warning.




<listitem>

<literal>destino - O destino das mensagens pode ser um arquivo, um
pipe (se iniciado por um "|"), um computador remoto (se iniciado por uma "@"),
determinados usuários do sistema (especificando os logins separados por
vírgula) ou para todos os usuários logados via <command>wall (usando
"*").




Todas as mensagens com o nível especificado e superiores a esta especificadas
no <command>syslog.conf serão registradas, de acordo com as opções
usadas.  Conjuntos de **facilidades** e
**níveis** podem ser agrupadas separando-as por ";".


OBS1: Sempre use TABS ao invés de espaços para separar os parâmetros do
<filename>syslog.conf</filename>.


OBS2: Algumas facilidades como <literal>security, emitem um beep de
alerta no sistema e enviam uma mensagem para o console, como forma de alerta ao
administrador e usuários logados no sistema.


Existem ainda 4 caracteres que garantes funções especiais: "*", "=", "!"  e
"-":

<itemizedlist>
<listitem>

"*" - Todas as mensagens da **facilidade** especificada serão
redirecionadas.


<listitem>

"=" - Somente o **nível** especificado será registrado.


<listitem>

"!"  - Todos os **níveis** especificados e maiores NÃO serão
registrados.


<listitem>

"-" - Pode ser usado para desativar o sync imediato do arquivo após sua
gravação.




Os caracteres especiais "=" e "!"  podem ser combinados em uma mesma regra.


Exemplo: Veja abaixo um exemplo de um arquivo
<filename>/etc/syslog.conf</filename> padrão de sistemas
<command>Debian

<screen>
#
# Primeiro alguns arquivos de log padrões. Registrados por facilidade
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          /var/log/mail.log
user.*                          -/var/log/user.log
uucp.*                          -/var/log/uucp.log

#
# Registro de logs do sistema de mensagens. Divididos para facilitar
# a criação de scripts para manipular estes arquivos.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

# Registro para o sistema de news INN
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Alguns arquivos de registro "pega-tudo".
# São usadas "," para especificar mais de uma prioridade (por 
# exemplo, "auth,authpriv.none") e ";" para especificar mais de uma 
# facilidade.nível que será gravada naquele arquivo.
# Isto permite deixar as regras consideravelmente menores e mais legíveis
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergências são enviadas para qualquer um que estiver logado no sistema. Isto
# é feito através da especificação do "*" como destino das mensagens e são
# enviadas através do comando wall.
#
*.emerg                         *

#
# Eu gosto de ter mensagens mostradas no console, mas somente em consoles que 
# não utilizo.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# O pipe /dev/xconsole é usado pelo utilitário "xconsole". Para usa-lo,
# você deve executar o "xconsole" com a opção "-file":
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTA: ajuste as regras abaixo, ou ficará maluco se tiver um um site 
# muito movimentado...
#
daemon.*;mail.*;\
        news.crit;news.err;news.notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

# A linha baixo envia mensagens importantes para o console em que 
# estamos trabalhando logados (principalmente para quem gosta de ter 
# controle total sobre o que está acontecendo com seu sistema).
*.err;kern.debug;auth.notice;mail.crit	/dev/console





 log-klogd">###klogd

Este daemon controla o registro de mensagens do kernel.  Ele monitora as
mensagens do kernel e as envia para o daemon de monitoramento
<command>syslogd, por padrão.


<command>klogd [**opções**]

<variablelist>
<varlistentry>
<term>**opções**
<term>-d
<listitem>

Ativa o modo de depuração do daemon



<varlistentry>
<term>-f [arquivo]
<listitem>

Envia as mensagens do kernel para o arquivo especificado ao invés de enviar ao
daemon do <command>syslog



<varlistentry>
<term>-i
<listitem>

Envia um sinal para o daemon recarregar os símbolos de módulos do kernel.



<varlistentry>
<term>-I
<listitem>

Envia um sinal para o daemon recarregar os símbolos estáticos e de módulos do
kernel.



<varlistentry>
<term>-n
<listitem>

Evita a operação em segundo plano.  Útil se iniciado pelo
<command>init



<varlistentry>
<term>-k [arquivo]
<listitem>

Especifica o arquivo que contém os símbolos do kernel.  Exemplos deste arquivo
estão localizados em <filename>/boot/System.map-xx.xx.xx</filename>.



<varlistentry>
<term>-o
<listitem>

Faz com que o daemon leia e registre todas as mensagens encontradas nos buffers
do kernel, após isto o daemon é encerrado.



<varlistentry>
<term>-p
<listitem>

Ativa o modo paranóia.  Isto fará o <command>klogd somente carregar
detalhes sobre os módulos quando os caracteres <literal>Oops forem
detectados nas mensagens do kernel.  É recomendável ter sempre a última versão
do klogd e evitar a utilização desta opção em ambientes críticos.



<varlistentry>
<term>-s
<listitem>

Força a utilização da interface de chamadas do sistema para comunicação com o
kernel.



<varlistentry>
<term>-x
<listitem>

Esconde tradução EIP, assim ele não lê o arquivo
<filename>/boot/System.map-xx-xx-xx</filename>.



</variablelist>

A especificação de um arquivo com a opção <literal>-k é necessária se
desejar que sejam mostradas a tabela de símbolos ao invés de endereços
numéricos do kernel.






 log-logger">###logger

Este comando permite enviar uma mensagem nos log do sistema.  A mensagem é
enviada aos logs via daemon <command>syslogd ou via soquete do
sistema, é possível especificar a prioridade, nível, um nome identificando o
processo, etc.  Seu uso é muito útil em shell scripts ou em outros eventos do
sistema.


<command>logger [**opções**] [**mensagem**]


Onde:

<variablelist>
<varlistentry>
<term>**mensagem**
<listitem>

Mensagem que será enviada ao daemon **syslog**



<varlistentry>
<term>**opções**
<term>-i
<listitem>

Registra o PID do processo



<varlistentry>
<term>-s
<listitem>

Envia a mensagem ambos para a saída padrão (STDOUT) e syslog.



<varlistentry>
<term>-f [arquivo]
<listitem>

Envia o conteúdo do arquivo especificado como **mensagem** ao
syslog.



<varlistentry>
<term>-t [nome]
<listitem>

Especifica o nome do processo responsável pelo log que será exibido antes do
PID na mensagem do syslog.



<varlistentry>
<term>-p [prioridade]
<listitem>

Especifica a prioridade da mensagem do syslog, especificada como
<literal>facilidade.nível.  Veja os tipos de prioridade/níveis em
<xref linkend="log-syslogd-exemplo"/>.  O valor padrão
**prioridade.nível** é **user.notice**



<varlistentry>
<term>-u [soquete]
<listitem>

Envia a mensagem para o [soquete] especificado ao invés do syslog



</variablelist>

Mais detalhes sobre o funcionamento sobre o daemon de log do sistema
<command>syslogd, pode ser encontrado em <xref linkend="log-syslogd"/>


Exemplos: <literal>logger -i -t focalinux Teste teste teste,
<literal>logger -i -f /tmp/mensagem -p security.emerg




 log-uteis">###Programas úteis para monitoração e gerenciamento de arquivos de logs
 log-uteis-logcheck">###logcheck

É um programa usado para enviar um e-mail periodicamente ao administrador do
sistema (através do <command>cron ou outro daemon com a mesma função)
alertando sobre os eventos que ocorreram desde a última execução do programa.
As mensagens do <command>logcheck são tratadas por arquivos em
<filename>/etc/logcheck</filename> e organizadas em categorias antes de ser
enviada por e-mail, isto garante muita praticidade na interpretação dos eventos
ocorridos no sistema.


As categorias são organizadas da mais importantes para a menos importante, e
vão desde "Hacking em andamento" (providências devem ser tomadas imediatamente
para resolver a situação) até "eventos anormais do sistema" (mensagens de
inicialização, mensagens dos daemons do sistema, etc.).


O tipo de mensagem que será incluída/ignorada nos logs enviados podem ser
personalizadas pelo administrador do sistema através dos arquivos/diretórios
dentro de <filename>/etc/logcheck</filename>.  Nomes de arquivos/diretórios
contendo a palavra "ignore" são usados para armazenar expressões regulares que
NÃO serão enviadas pelo <command>logcheck.  É permitido o uso de
expressões regulares <command>perl/sed para especificar as mensagens
nos arquivos de log.



 log-uteis-logrotate">###logrotate

Usado para fazer backups dos logs atuais do sistema (programado via
<command>cron, ou outro daemon com a mesma função) e criando novos
arquivos de logs que serão usados pelo sistema.  Opcionalmente os arquivos de
logs antigos serão compactados para diminuir a utilização de espaço em disco ou
enviados por e-mail ao administrador.  A rotação dos arquivos de logs
proporciona maior agilidade quando precisamos encontrar algum detalhe útil (que
seria mais difícil de se achar em um arquivo de log de 10MB ou maior).


A rotação de logs é feita de acordo com o tamanho do arquivo de logs
especificado, mas a opção **-f** pode ser usada para "forçar"
a rotação de logs.  A opção **-d** fornece mais detalhes sobre
o que o <command>logrotate está fazendo.  Seu arquivo principal de
configuração é o <filename>/etc/logrotate.conf</filename>.  Um modelo deste
tipo de arquivo é o seguinte:

<screen>
#### Estas opções afetam globalmente o funcionamento do logrotate
# roda os arquivos de log semanalmente
weekly

# mantém as últimas 4 cópias de logs anteriores
rotate 4

# Erros de não existência dos logs são enviados para o usuário root
mail root

# Cria novos arquivos de log (vazios) após rodar os antigos
create

# Descomente isso se desejar seus arquivos de logs compactados. O parâmetro
# delaycompress é usado para que o primeiro log rodado seja mantido 
# descompactado
compress
delaycompress

# Executam os scripts em prerotate e postrotate a cada vez que os logs 
# forem rodados. 
nosharedscripts

# Definimos um diretório que poderá conter definições individuais para 
# diversos serviços no sistema, eles podem ir neste arquivo mas 
# diversas configurações individuais podem deixar a interpretação
# deste arquivo confusa.
include /etc/logrotate.d


# Define opções específicas para a rotação mensal de /var/log/wtmp, o novo arquivo 
# de log somente será rodados caso tenha mais de 5MB (size 5M), será criado 
# com a permissão 0664 e pertencerá ao usuário root grupo utmp
# (create 0664 root utmp) e será mantida somente uma cópia do log anterior.
# (rotate 1)
/var/log/wtmp {
    monthly
    create 0664 root utmp
    size 5M
    rotate 1
}

# Define opções específicas para a rotação mensal de /var/log/btmp, se o arquivo 
# não existir não será necessário gerar alertas (missinkok) que serão enviados 
# ao administrador. O novo arquivo criado deverá ter a permissão 0664 com o 
# dono root e grupo utmp (create 0664 root utmp) e será 
# mantida somente uma cópia do log anterior.
/var/log/btmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

# Define opções específicas para a rotação mensal de /var/log/lastlog, o novo 
# arquivo será criado com a permissão 0664 com o dono root e grupo 
# utmp e será mantida somente uma cópia do arquivo de log anterior 
# (rotate 1).
/var/log/lastlog {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

# Define opções específicas para a rotação diária de /var/log/messages, o 
# arquivo será rodado se atingir o tamanho de 1Mb, então o
# novo arquivo será criado com as mesmas permissões do arquivo anterior. 
# O comando killall -1 syslogd será executado após a rotação 
# para que o daemon syslogd funcione corretamente mas somente uma vez
# durante a rotação de vários arquivos de logs (sharedscripts). 
# Serão mantidas as 10 últimas cópias do arquivo /var/log/messages 
# compactadas (o parâmetro compress foi especificado na seção global deste
# arquivo de configuração).
/var/log/messages {
    daily
    size 1M
    sharedscripts
    postrotate
      /sbin/killall -1 syslogd
    endscript
    rotate 10
}

# Define opções específicas para a rotação mensal dos arquivos em /var/log/mirror/*, 
# a falta desses arquivos não precisa ser notificada ao administrador (missingok), 
# mesmo assim o parâmetro "nomail" evitará isto de qualquer forma. Os logs 
# rodados não serão compactados (nocompress) e serão mantidas as últimas 7 cópias
# dos logs.
/var/log/mirror/* {
   montly
   nomail
   missingok
   nocompress
   rotate 7
}
	    
# logs específicos do sistema podem ser configurados aqui. As opções padrões e 
# definidas na seção global deste arquivo serão usadas para processar os 
# arquivos de logs restantes.


Qualquer definição de parâmetro especificado no arquivo de configuração,
substituirá as definições anteriores.  Quando o número máximo de logs mantidos
pela opção **rotate [num]** é atingida, os logs eliminados
serão enviados para o usuário especificado na opção **mail
[email]**.  A utilização da diretiva **nomail** evita
isso.


Quando for utilizar coringas para se referir a determinados arquivos dentro de
um diretório, não utilize a sintaxe "log-xxx-*" porque isto forçaria a
recompactação de arquivos ".gz" já feitas, gerando arquivos do tipo
<filename>.gz.gz...</filename> e derrubando o processamento da sua máquina
gerada por um loop de compactação e enchendo as entradas de diretório.  Prefira
usar a sintaxe <filename>log-xxx-*.log</filename> (ou outra, modificando a
configuração do programa que gera os logs).


**OBS:** É importante enviar um sinal HUP ao
programa que grava para aquele arquivo de log para que não ocorram problemas
após a rotação, isto é feito usando o parâmetro
**postrotate**.





 log-server">###Configurando um servidor de logs

As mensagens das máquinas de sua rede podem ser centralizadas em uma única
máquina, isto facilita o gerenciamento, análise e solução de problemas que
ocorrem nas máquinas da rede.  Mais importante ainda é que qualquer invasão a
estação de trabalho não será registrada localmente (podendo ser apagada
posteriormente pelo invasor, isso é comum).

<variablelist>
<varlistentry>
<term>Configurando o servidor de logs
<listitem>

Adicione a opção **-r** ao iniciar o daemon
<command>syslogd para aceitar logs enviados das máquinas clientes.
Na distribuição <command>Debian modifique o arquivo
<filename>/etc/init.d/sysklogd</filename> colocando a opção
**-r** na variável <replaceable>SYSLOGD</replaceable> e
reinicie o serviço usando <literal>./sysklogd restart.


Adicionalmente poderão ser usadas as opções **-l máquina** (é
um "L" minúsculo não uma letra "I") para registrar o nome FQDN da máquina e
**-h** para redirecionar conexões a outros servidores de logs
(veja <xref linkend="log-syslogd"/>).



<varlistentry>
<term>Configurando máquinas cliente
<listitem>

Modifique o arquivo <filename>/etc/syslogd.conf</filename> (veja <xref linkend="log-syslogd-exemplo"colocando o nome do computador seguido de "@"
para redirecionar as mensagens dos logs:

<screen>
auth,authpriv.*                 @servlog
*.*;auth,authpriv.none          @servlog
cron.*                          @servlog
daemon.*                        @servlog
kern.*                          -/var/log/kern.log
kern.*						@servlog
lpr.*                           @servlog
mail.*                          /var/log/mail.log
user.*                          -/var/log/user.log
user.*						@servlog
uucp.*                          -/var/log/uucp.log


E reinicie o daemon <command>syslogd da máquina cliente para re-ler o
arquivo de configuração: <literal>killall -HUP syslogd ou
<literal>/etc/init.d/sysklogd restart.



</variablelist>

**OBS1:** Mantenha o relógio do servidor de logs
sempre atualizado (use o <command>chrony ou outro daemon de
sincronismo NTP para automatizar esta tarefa).


**OBS2:** É interessante compilar um daemon
<command>syslogd personalizado modificando o nome e localização do
arquivo <filename>/etc/syslog.conf</filename> para enganar possíveis invasores.
Isto pode ser modificado no arquivo <filename>syslogd.c</filename> na linha:

<screen>
#define _PATH_LOGCONF   "/etc/syslog.conf"


Use a imaginação para escolher um nome de arquivo e localização que dificulte a
localização deste arquivo.


**OBS3:** Em uma grande rede, é recomendável
configurar um computador dedicado como servidor de log (desativando qualquer
outro serviço) e configurar o <command>iptables para aceitar somente
o tráfego indo para a porta UDP 514 (syslogd):

<screen>
iptables -P INPUT DROP
iptables -A INPUT -p udp --dport 514 -j ACCEPT



