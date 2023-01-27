<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inter;avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" deb">###A distribuição Debian GNU/Linux

Este capítulo traz algumas características sobre a distribuição <command>Debian
GNU/Linux, programas de configuração e particularidades.  A maioria
dos trechos aqui descritos, também se aplicam a distribuições baseadas na
<command>Debian, como o **Kurumin** e o
**Ubuntu**.


Você deve estar se perguntando <literal>mas porque um capítulo falando sobre a
distribuição Debian se eu uso outra?.  Bem, a partir da versão
**Intermediário** do **Foca Linux** existem
algumas partes que são especificas de algumas distribuições Linux e que não se
aplicam a outras, como a localização dos arquivos de configuração, nomes dos
programas de configuração e outros detalhes específicos e esta versão é a
baseada na <command>Debian.  Pegue na página do Foca Linux (
    ("http://www.w3.org/1999/xlink) []( [guiafoca](http://www.guiafoca.org)   [guiafoca](http://www.guiafoca.org) )) uma versão
Intermediário /Avançado do guia específico para sua distribuição.


 deb-carac">###Porque usar a Debian?

A <command>Debian é a distribuição que mais cresce no mundo, cada
versão é somente lançada após rigorosos testes de segurança e correção de
falhas fazendo desta a mais segura e confiável dentre todas as outras
distribuições Linux.  É reconhecida como a mais segura, maior e atualizada mais
freqüentemente entre as outras distribuições <command>Linux, além de
ser a única sem fins comerciais.


É a única que adota o estilo de desenvolvimento aberto e não é mantida por uma
empresa comercial (note que o endereço do WebSite da <command>Debian
termina com <filename>.org</filename>), ao invés disso é mantida por
programadores, hackers e especialistas de segurança espalhados ao redor do
mundo, seguindo o estilo de desenvolvimento do Linux.  Possui suporte a mais de
12 arquiteturas e 15 sub-arquiteturas (entre elas, Intel x86, Alpha, VMS,
Sparc, Macintosh (m68k), Power Pc, ARM, etc).


Suas atualizações são constantes e não é necessário adquirir um novo CD para
fazer upgrades.  Meu sistema é atualizado semanalmente e de forma segura
através de 2 simples comandos.  Veja <xref linkend="dpkg-apt"as instruções
de como fazer isto.


Cada pacote da distribuição é mantida por uma pessoa, o que garante uma boa
qualidade, implementações de novos recursos e rápida correção de falhas.
Qualquer pessoa com bons conhecimentos no sistema e inglês pode se tornar um
**Debian Developer**, para detalhes consulte a lista de
discussão **debian-user-portuguese** (veja <xref linkend="ajuda-listas"/>) ou veja a página oficial da
<command>Debian: ("http://www.w3.org/1999/xlink) [](http://www.debian.org)http://www.debian.org/.


A distribuição apresenta compatibilidade com outros sistemas a partir da
instalação até a seleção de programas e execução do sistema, sua instalação
está até mesmo disponível desde computadores 386 que utilizam unidades de
disquetes de 5 1/4 polegadas até para computadores UDMA66, instalando através
de DVD e pen drives.  Com a Debian é possível iniciar a instalação usando um
pen drive e continuar usando a internet.


É a distribuição mais indicada para uso em servidores devido ao seu desempenho,
segurança e programas úteis de gerenciamento e monitoração da rede,
recomendados por especialistas que participam de seu desenvolvimento.


Não existem versões separadas da Debian para servidores, uso pessoal, etc, ao
invés disso a distribuição usa perfis de usuário (dependendo da função do
usuário) e perfis de computador (dependendo do que deseja fazer), podendo ser
selecionado mais de um perfil de usuário/computador.


Os perfis selecionam automaticamente os pacotes mais úteis para a instalação.
Os pacotes existentes em cada perfil foram escolhidos através de debates entre
usuários que trabalham ativamente naquela área, resultando em uma seleção de
pacotes de alta produtividade.


Para os usuários avançados e exigentes, também é possível selecionar os pacotes
individualmente via <command>dselect, o que resultará em uma
instalação somente com pacotes úteis e melhor configurada.



 deb-pacotes">###Pacotes existentes na Debian

O número de pacotes existentes na distribuição atual da
<command>Debian (**Buster** - 10) é de 59000.


A <command>Debian (como a <command>Red Hat) usa um formato
próprio para armazenar os programas: o formato <filename>.deb</filename>.  Este
formato permite a declaração, resolução e checagem automática de dependências,
pacotes sugeridos, opcionais e outras características que o torna atraente para
o desenvolvimento, gerenciamento e manutenção do sistema.


Estes pacotes são gerenciados através do programa <command>dpkg
(**Debian Package**) ou através de front-ends como o
<command>dselect ou <command>apt (para detalhes veja <xref linkend="dpkg"/>).



 deb-suf">###O que é sid/testing/frozen/stable?

Para o lançamento de uma nova distribuição <command>Debian, o
seguinte processo ocorre: <literal>sid =&gt; testing =&gt; stable (sendo a
**stable** sempre o lançamento oficial e sem bugs da
distribuição).

<variablelist>
<varlistentry>
<term>sid
<listitem>

Durante o desenvolvimento de uma nova distribuição <command>Debian,
ela é chamada de **sid**.  A **sid** é a
versão **Unstable**, isto não significa instabilidade, mas sim
que a distribuição esta sofrendo modificações para se tornar uma versão
estável, recebendo novos pacotes, etc.


Quando os pacotes não são modificados após um determinado período, os scripts
da Debian copiam estes pacotes (novos ou atualizados) para a
**testing**.


Não use a distribuição **sid** (**unstable**)
ao menos que tenha experiência no <command>Linux para corrigir
problemas, que certamente aparecerão.



<varlistentry>
<term>testing
<listitem>

A **testing** recebe os pacotes que não são modificados
durante algum tempo da **unstable**, isto significa que eles
possuem alguma estabilidade.


A **testing** é uma espécie de congelamento permanente
(freeze) durante o desenvolvimento da **Unstable**.


Os novos pacotes que entram na **unstable** também caem na
**testing** após certo tempo.


Mesmo assim, podem existir falhas graves na **testing**, se
você precisa de um ambiente realmente livre de falhas, use a
**stable**.



<varlistentry>
<term>frozen (congelada)
<listitem>

Na data programada pela equipe de lançamento da <command>Debian, a
distribuição **testing** é congelada: nenhum pacote novo da
**unstable** cai na **testing** e começa a
procura de falhas na distribuição **testing**.  Nenhuma nova
característica é implementada nos pacotes (a não ser que seja extremamente
necessário) e os developers se dedicam a correção de erros nos pacotes.


A distribuição **testing** congelada se tornará a futura
**stable** após todas as falhas serem corrigidas.  É
considerado seguro usar a **frozen** após 1 mês de
"congelamento".


Quando a **testing** é congelada, o ciclo de desenvolvimento
da **unstable** continua para que a próxima distribuição da
<command>Debian seja lançada.



<varlistentry>
<term>stable
<listitem>

Quando todos os bugs da **testing** congelada são eliminados,
ela é lançada como **stable**, a nova **versão
Oficial** da <command>Debian.


A **stable** é o resultado final do desenvolvimento, das
correção de falhas/segurança e que passou por todos os ciclos de testes para
ser lançada.  Resumindo é a distribuição pronta para ser usada com toda a
segurança.



</variablelist>


 deb-obtendo">###Como obter a Debian

A instalação da distribuição pode ser obtida através de Download de ("http://www.w3.org/1999/xlink) [](ftp://ftp.debian.org//debian/dists/stable/main/disks-i386">ftp://ftp.debian.org//debian/dists/stable/main/disks-i386
(para Intel x86), seus programas diversos estão disponíveis em ("http://www.w3.org/1999/xlink) [](ftp://ftp.debian.org//debian/dists/stable/main/binary-i386">ftp://ftp.debian.org//debian/dists/stable/main/binary-i386.



 deb-prgnconfig">###Programas de configuração
<itemizedlist>
<listitem>

<command>aptitude - Seleciona pacote para instalação/desinstalação


<listitem>

<command>pppconfig - Configura o computador para se conectar a
Internet usando conexão discada.  Após isto, use <literal>pon para se
conectar a Internet, <literal>poff para se desconectar e
<literal>plog para monitorar a conexão.


<listitem>

<command>pppoeconf - Configura o computador para conectar a internet
usando ADSL


<listitem>

<command>modconf - Permite selecionar os módulos que serão
automaticamente carregados na inicialização do sistema.  Se requerido pelos
módulos os parâmetros I/O, IRQ e DMA também podem ser especificados.


<listitem>

<command>shadowconfig - Permite ativar ou desativar o suporte a
senhas ocultas (shadow password).  Com as senhas ocultas ativadas, as senhas
criptografadas dos usuários e grupos são armazenadas nos arquivos
<filename>shadow</filename> e <filename>gshadow</filename> respectivamente, que
somente podem ser acessadas pelo usuário root.


Isto aumenta consideravelmente a segurança do sistema pois os arquivos
<filename>passwd</filename> e <filename>group</filename> contém dados de
usuários que devem ter permissão de leitura de todos os usuários do sistema.


<listitem>

<command>tasksel - Permite selecionar/modificar de forma fácil a
instalação de pacotes em seu sistema através da função que sua máquina terá ou
do seu perfil de usuário.


<listitem>

<command>tzconfig - Permite modificar/selecionar o fuso-horário usado
na distribuição.




Além destes, a Debian conta com o sistema de configuração baseado no
<literal>dpkg-reconfigure que permite configurar de forma fácil e
rápida aspecto de pacotes: <literal>dpkg-reconfigure xserver-xorg.



 deb-startup">###Arquivos de inicialização

Os arquivos de inicialização da distribuição <command>Debian (e
baseadas nela) estão localizados no diretório <filename>/etc/init.d</filename>.
Cada daemon (programa residente na memória) ou configuração específica possui
um arquivo de onde pode ser ativado/desativado.  Os sistemas residentes neste
diretório não são ativados diretamente, mas sim através de links existentes nos
diretórios <filename>/etc/rc?.d</filename> onde cada diretório consiste em um
nível de execução do sistema (veja também a <xref linkend="deb-runlevels"/>).


Por padrão, você pode usar as seguintes palavras chaves com os arquivos de
configuração:

<itemizedlist>
<listitem>

<literal>start - Inicia o daemon ou executa a configuração


<listitem>

<literal>stop - Interrompe a execução de um daemon ou desfaz a
configuração feita anteriormente (se possível).


<listitem>

<literal>restart - Reinicia a execução de um daemon.  É equivalente
ao uso de <literal>stop e <literal>start mas se aplicam
somente a alguns daemons e configurações, que permitem a interrupção de
execução e reinicio.




Por exemplo, para reconfigurar as interfaces de rede do computador, podemos
utilizar os seguintes comandos:

<screen>
cd /etc/init.d
./networking restart



 deb-runlevels">###Níveis de Execução

Os **Níveis de execução** (run levels) são diferentes modos de
funcionamento do <command>GNU/Linux com programas, daemons e recursos
específicos.  Em geral, os sistemas <command>GNU/Linux possuem sete
níveis de execução numerados de 0 a 6.  O daemon <command>init é o
primeiro programa executado no <command>GNU/Linux (veja através do
<literal>ps ax|grep init) e responsável pela carga de todos daemons
de inicialização e configuração do sistema.


O nível de execução padrão em uma distribuição <command>GNU/Linux é
definido através do arquivo de configuração do
<filename>/etc/inittab</filename> (<xref linkend="etc-inittab"/>) através da
linha

<screen>
id:2:initdefault:


 deb-runlevels-e">###Entendendo o funcionamento dos níveis de execução do sistema (runlevels)

Os nível de execução atual do sistema pode ser visualizado através do comando
<command>runlevel e modificado através dos programas
<command>init ou <command>telinit.  Quando é executado, o
<command>runlevel lê o arquivo <filename>/var/run/utmp</filename> e
adicionalmente lista o nível de execução anterior ou a letra
<literal>N em seu lugar (caso ainda não tenha ocorrido a mudança do
nível de execução do sistema).


Na <command>Debian, os diretórios <filename>/etc/rc0.d</filename> a
<filename>/etc/rc6.d</filename> contém os links simbólicos para arquivos em
<filename>/etc/init.d</filename> que são acionados pelo nível de execução
correspondente.


Por exemplo, o arquivo <filename>S10sysklogd</filename> em
<filename>/etc/rc2.d</filename>, é um link simbólico para
<filename>/etc/init.d/sysklogd</filename>.


O que aconteceria se você removesse o arquivo
<filename>/etc/rc2.d/S10sysklogd</filename>?  Simplesmente o daemon
<command>sysklogd deixaria de ser executado no nível de execução 2 do
sistema (que é o padrão da <command>Debian).


A <command>Debian segue o seguinte padrão para definir se um link
simbólico em <filename>/etc/rc[0-6].d</filename> iniciará ou interromperá a
execução de um serviço em <filename>/etc/init.d</filename>, que é o seguinte:

<itemizedlist>
<listitem>

Se um link é iniciado com a letra <literal>K (kill), quer dizer que o
serviço será interrompido naquele nível de execução.  O que ele faz é executar
o daemon em <filename>/etc/init.d</filename> seguido de
<literal>stop.


<listitem>

Se um link é iniciado com a letra <literal>S (start), quer dizer que
o serviço será iniciado naquele nível de execução (é equivalente a executar o
daemon seguido de <literal>start).




Primeiro os links com a letra <literal>K são executado e depois os
<literal>S.  A ordem que os links são executados dependem do valor
numérico que acompanha o link, por exemplo, os seguintes arquivos são
executados em seqüência:

<screen>
S10sysklogd
S12kerneld
S20inetd
S20linuxlogo
S20logoutd
S20lprng
S89cron
S99xdm


Note que os arquivos que iniciam com o mesmo número (<literal>S20*)
são executados alfabeticamente.  O nível de execução do sistema pode ser
modificado usando-se o comando <command>init ou
<command>telinit.  Os seguinte níveis de execução estão disponíveis
na <command>Debian:

<itemizedlist>
<listitem>

<literal>0 - Interrompe a execução do sistema.  todos os programas e
daemons finalizados.  É acionado pelo comando <literal>shutdown -h


<listitem>

<literal>1 - Modo monousuário, útil para manutenção dos sistema.


<listitem>

<literal>2 - Modo multiusuário (padrão da Debian)


<listitem>

<literal>3 - Modo multiusuário


<listitem>

<literal>4 - Modo multiusuário


<listitem>

<literal>5 - Modo multiusuário com login gráfico


<listitem>

<literal>6 - Reinicialização do sistema.  Todos os programas e
daemons são encerrados e o sistema é reiniciado.  É acionado pelo comando
<literal>shutdown -r e o pressionamento de
<literal>CTRL+<literal>ALT+<literal>DEL.




Por exemplo, para listar o nível de execução atual do sistema digite:
<literal>runlevel.  O <command>runlevel deverá listar algo
como:

<screen>
N 2


Agora para mudar para o nível de execução 1, digite: <literal>init 3.
Agora confira a mudança digitando: <literal>runlevel.  Você deverá
ver este resultado:

<screen>
2 3


Isto quer dizer que o nível de execução anterior era o <literal>2 e o
atual é o <literal>3.





 deb-rede">###Rede no sistema Debian

O local que contém as configurações de rede em um sistema
<command>Debian é o <filename>/etc/network/interfaces</filename>.  O
formato deste arquivo é descrito em <xref linkend="etc-network-interfaces"/>.



 deb-bts">###Bug tracking system

É o sistema para relatar bugs e enviar sugestões sobre a distribuição.  Para
relatar um bug primeiro você deve saber inglês (é a língua universal entendida
pelos desenvolvedores) e verificar se o bug já foi relatado.  O Debian
**Bug tracking system** pode ser acessado pelo endereço:
("http://www.w3.org/1999/xlink) [](http://bugs.debian.org)http://bugs.debian.org/.


Para relatar uma falha/sugestão, envie um e-mail para:
<email>submit@bugs.debian.org, com o assunto referente a falha/sugestão
que deseja fazer e no corpo da mensagem:

<screen>
Package: pacote
Severity: normal/grave/wishlist
Version: versão do pacote

E o relato do problema


O bug será encaminhado diretamente ao mantenedor do pacote que verificará o
problema relatado.  Os campos <literal>Package e
<literal>Severity são obrigatórios para definir o nome do pacote
(para endereçar o bug para a pessoa correta) e versão do pacote (esta falha
pode ter sido relatada e corrigida em uma nova versão).



 deb-download">###Onde encontrar a Debian para Download?

No endereço ("http://www.w3.org/1999/xlink) [](ftp://ftp.debian.org)ftp://ftp.debian.org/.
Outros endereços podem ser obtidos na página oficial da
<command>Debian http://www.w3.org/1999/xlink) [](http://www.debian.org)http://www.debian.org/) clicando no link
<literal>Download e <literal>mirrors.


A distribuição Etch (4.0) completa, com 18830 pacotes ocupa em torno de 10 GB.
Você também pode optar por fazer a instalação dos pacotes opcionais via
Internet através do método apt.  Para detalhes veja o guia do dselect ou envie
uma mensagem para a lista de discussão
<email>debian-user-portuguese@lists.debian.org (veja <xref linkend="ajuda-listas"para detalhes).



 deb-lista-pacotes">###Lista de pacotes para uma instalação rápida e manual

Esta seção contém uma lista de pacotes necessários que atendem a maioria dos
usuários normais da <command>Debian em um **sistema padrão** sem desperdício de espaço e sabendo
exatamente o que está instalando.


Estou assumindo que você concluiu a instalação da <command>Debian 10.0
(Buster) mas preferiu pular o passo de seleção de pacotes do
<command>dselect e fazer uma instalação manual.


A lista de pacotes está dividida por categorias e você precisa ter o programa
<command>apt configurado corretamente para que os comandos funcionem
(veja <xref linkend="dpkg-apt"para detalhes).


Se pretende usar a lista de pacotes para fazer a instalação da
<command>Debian em muitos computadores, você tem duas opções:

<orderedlist numeration="arabic">
<listitem>

Copiar o conteúdo das seções que seguem e fazer um script de instalação
personalizado para automatizar a instalação de pacotes da
<command>Debian em outras máquinas


<listitem>

Após a instalação dos pacotes no computador, utilize o comando <literal>dpkg
--get-selections &gt;Lista-Pacotes.txt para gerar o arquivo
<filename>Lista-Pacotes.txt</filename> contendo a lista de pacotes instalados.


Então no computador que pretende fazer a instalação de pacotes, use o comando
<literal>dpkg --set-selections &lt;Lista-Pacotes.txt e então digitar
<literal>apt-get -f install ou escolher a opção
<literal>Install no <command>dselect.


</orderedlist>

Para mais detalhes veja <xref linkend="dpkg-get-selections"e a <xref linkend="dpkg-set-selections"/>.  É importante usar o comando <literal>apt-get
clean após a instalação de pacotes para remover os pacotes baixados
pelo <command>apt de <filename>/var/cache/apt/archives</filename>
(exceto na instalação de pacotes através do disco rígido local).


 s20.11.1">###Pacotes Básicos (Altamente Recomendado)
<screen>
apt-get install cpio info libident libncurses4 man-db manpages whois vim
                hdparm mc postfix linuxlogo less kbd mutt bzip2 
                cron gpm 



 s20.11.2">###Compilação do Kernel e programas em linguagem C
<screen>
apt-get install perl, gcc libc6-dev bin86 make


Se pretender utilizar o <systemitem role="package">kernel-package</systemitem>
para compilar o kernel mais facilmente, então você precisará dos seguintes
pacotes:

<screen>
apt-get install kernel-package dpkg-dev


Veja <xref linkend="kern-recompilando"para entender como compilar seu
próprio kernel.



 s20.11.3">###X11 (básico)
<screen>
apt-get install xbase-clients xserver-xorg xfonts-75dpi xfonts-base 
                xserver-common xterm xfstt xdm


Caso suas fontes sejam mostradas em tamanho exagerado, remova o pacotes
<systemitem role="package">xfonts-100dpi</systemitem> ou ajuste a seção
<literal>Files do arquivo <filename>/etc/X11/xorg.conf</filename>
apropriadamente.



 s20.11.4">###Window Managers para o X
<screen>
apt-get install wmaker wmakerconf wmaker-data wmavload 
                eterm enlightenment enlightenment-theme-bluesteel asclock
		afterstep


OBS: Existem também gerenciadores de seção como o <command>gnome,
<command>kde, ocupam bastante espaço em disco



 s20.11.5">###Impressão (texto e gráfico com sistema de spool)
<screen>
apt-get install lprng magicfilter gs gsfonts



 s20.11.6">###Som (mixer, mp3, Midi, wav, CD-Player)
<screen>
xmms playmidi cam aumix alsa-base alsa-oss alsamixergui xmcd sox



 s20.11.7">###Programas de Internet (clientes)
<screen>
apt-get install xchat gaim firefox fetchmail procmail mime-support



 s20.11.8">###Acessórios
<screen>
apt-get install gimp gimp-nonfree gnotepad openoffice freefont



 s20.11.9">###Rede
<screen>
apt-get install finger, talk, talkd, telnet





