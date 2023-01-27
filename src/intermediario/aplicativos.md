<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" aplic">###Aplicativos para Linux

Este capítulo traz uma lista de aplicativos e suas características e tem como
objetivo servir de referência para a escolha de um programa que atenda as suas
necessidades específicas.


Os programas descritos aqui são "Clientes", ou seja, fazem acesso a um programa
"Servidor" (como é o caso dos navegadores) para funcionarem.  Os programas
servidores estão descritos na versão **Avançado** do guia, de
forma passo a passo, características e métodos de configuração recomendados.


Se você conhece um bom programa e acha que ele deveria estar aqui, me avise
pelo email <email>gleydson@guiafoca.org.


 aplic-b">###Aplicativos Básicos

São aplicativos que fazem parte do cotidiano da maioria dos usuários domésticos
e de empresas.


 aplic-b-editores">###Editores de Texto
<variablelist>
<varlistentry>
<term>vi
<listitem>

Modo Texto - (existem algumas versões adaptadas para o modo gráfico).  É um dos
editores padrões dos sistemas <command>GNU/Linux e sua interface é
complexa e possui muitas funções (usuários <command>GNU/Linux
avançados adoram a quantidade de funções deste programa).  Recomendo que
aprenda o básico sobre ele, pois sempre estará disponível caso ocorra algum
problema no sistema.


Para sair do editor <command>vi sem salvar pressione
<literal>ESC e digite <literal>:q!.  Para sair do editor e
salvar pressione <literal>ESC e digite <literal>:wq.



<varlistentry>
<term>elvis
<listitem>

Modo Texto - possui boa interface de comunicação com o usuário, suporte a HTML
e Metacaracteres.



<varlistentry>
<term>ae
<listitem>

Modo Texto - é um dos editores padrões dos sistemas
<command>GNU/Linux (encontrado nas distribuições
<command>Debian e baseadas).  Sua interface é mais fácil que o
<command>vi.  Também recomendo que aprenda o básico sobre ele, pois é
requerido para a manutenção do sistema.


Para sair do <command>ae sem salvar pressione
<literal>CTRL+Q, para salvar o texto pressione
<literal>CTRL+X e <literal>CTRL+W (após isto se quiser sair
do editor, pressione <literal>CTRL+Q).



<varlistentry>
<term>jed
<listitem>

Modo Texto - Recomendável para aqueles que estão acostumados com o EDIT do
<command>DOS e gostam de menus suspensos.  Sua interface é de fácil
operação.


O <command>jed possui recursos poderosos para programadores de C e
outras linguagens que faz auto-tabulação, auto-identação e delimitação de
blocos de código através de cores.



<varlistentry>
<term>mcedit
<listitem>

Modo Texto - Muito fácil de utilizar e possui interface em Português do Brasil,
em geral não requer um tutorial para aprendizado.  Este programa faz parte do
pacote **Midnight Commander** (conhecido também como
<command>mc).


Você utiliza as teclas de função (F1 a F10) para salvar o texto, procurar
palavras no texto, pedir ajuda, sair, etc.  Ele possui recursos para colorir
blocos de código (testado com arquivos HTML e SGML).



<varlistentry>
<term>joe
<listitem>

Modo Texto - É um editor muito versátil e você pode escolher inclusive sua
interface.



<varlistentry>
<term>gedit
<listitem>

Modo Gráfico - editor do Gnome, sua interface de comunicação é ótima e
recomendado para aqueles que gostam de trabalhar com muitos arquivos abertos,
copiar e colar, etc.  Possui muitos recursos de operação de arquivo,
tabulações, browser, diff de documentos, etc.



<varlistentry>
<term>gxedit
<listitem>

Modo Gráfico - Editor no estilo do <command>gedit, sua interface de
comunicação com o usuário é ótima, possui suporte a e-mail, mede o número de
toques por minuto do usuário (digitação), suporte a tags HTML, audio, rede,
correção ortográfica, etc.



</variablelist>


 aplic-b-escritorio">###Aplicativos para Escritório
<variablelist>
<varlistentry>
<term>Open Office
<listitem>

Modo Gráfico - Pacote de Escritório contendo editor de texto, planilha de
cálculo, banco de dados, digitalizador de imagens, editor gráfico, calculadora,
navegador, e-mail, abre todos os arquivos do MS Office 2000 e sua interface é
idêntica aos programas do Office, não requerendo novo treinamento dos usuários.
Todos os programas do <command>Open Office são iniciados através de
uma interface virtual idêntica ao Windows (com menu iniciar e tudo mais).


Possui versão em Português e sua versão atual é a 1.0.  Além da impressionante
integração entre os programas que compõem o conjunto, o <command>Open
Office possui um frame de navegação com centenas de modelos, barra de
desktop, localização fácil de arquivos e abertura instantânea.


O <command>Open Office possui mais recursos que o Office e não custa
nada!  Seu tamanho para download é de 80MB e não requer o pagamento de licenças
para a instalação em computadores de empresas ou domésticos.


O equipamento mínimo que recomendo para a execução do <command>Open
Office é um 586 com 64 MB de memória RAM e 200 MB Livres no disco
rígido.  Sua instalação é feita em modo gráfico e o tamanho ocupado no disco
depende dos componentes selecionados.



<varlistentry>
<term>Abiword
<listitem>

Modo Gráfico - é um editor de Textos mais simples que o <command>Star
Office e uma boa interface de operação que possui suporte a arquivos
do Office 2000.


O equipamento mínimo que recomendo para a execução do
<command>Abiword é um 486 com 8 MB de memória RAM e 7 MB de espaço
livre no disco rígido (ele pode ocupar menos espaço caso as bibliotecas
compartilhados que utiliza já estiverem instaladas).



<varlistentry>
<term>Corel Word Perfect
<listitem>

Modo Gráfico - Pacote de escritório da Corel.  Uma alternativa ao <command>Open
Office.  Ele requer o pagamento de licenças para seu uso.



</variablelist>


 aplic-b-internet">###Internet
<variablelist>
<varlistentry>
<term>Netscape 4.73
<listitem>

Modo Gráfico - Versão do Netscape Communicator para
<command>GNU/Linux, com criptografia forte, programa de e-mail, news,
editor interativo de páginas HTML, catálogo de endereços.  Também possui
suporte a rede proxy e conexão via firewall.


Equipamento mínimo recomendável: 486 com 32 MB de RAM e 40 MB de espaço em
disco livre.



<varlistentry>
<term>Mozilla
<listitem>

Modo Gráfico - Navegador que inspirou a construção do Netscape, foi o primeiro
navegador gráfico e hoje a versão do Netscape 6.0 é baseada no Mozilla.  Se
gosta de frescuras na aparência do navegador escolha este mas o desempenho do
Netscape 4.73 é melhor...  Também possui suporte a rede proxy e conexão via
firewall


Equipamento mínimo recomendado: 486 com 48 MB de RAM e 40 MB de espaço em disco
livre.



<varlistentry>
<term>Arena
<listitem>

Modo Gráfico - navegador pequeno, sem suporte a Java e Frames, ideal para
computadores menos potentes.  Recomendo o <command>Lynx!


Equipamento mínimo recomendado: 386 com 8 MB de RAM e 12 MB de disco



<varlistentry>
<term>Opera
<listitem>

Modo Gráfico - Navegador pequeno, sem suporte a Java e Frames, ideal para
computadores menos potentes.  Ainda recomendo o <command>Lynx!



<varlistentry>
<term>Lynx
<listitem>

Modo Texto - Agora sim!  Navegador pequeno, não tem suporte a frames mas exibe
uma listagem permitindo selecionar qual será aberto, sem suporte a Java e muito
flexível em sua configuração (dê uma olhada na quantidade de opções no arquivo
<filename>/etc/lynx.cfg</filename>).  Também funciona via proxy tradicional ou
firewall.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 2 MB de disco.



<varlistentry>
<term>Pine
<listitem>

Modo Texto - Programa de E-Mail muito usado entre os usuários
<command>GNU/Linux, mas não é gratuito...  Possui suporte a
criptografia PGP e HTML em sua nova versão.



<varlistentry>
<term>Mutt
<listitem>

Modo Texto - Outro programa de E-mail muito usado pelos usuários do
<command>GNU/Linux.  Possui suporte a criptografia PGP, cores de
destaque nas mensagens e processamento de links HTML.  É muito personalizável
(veja a quantidade de opções no arquivo de configuração
<filename>/etc/Muttrc</filename>).  Sua interface é em Português.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 2 MB de disco.



<varlistentry>
<term>ftp
<listitem>

Modo Texto - O próprio!  faz cópias de arquivos de um site remoto para seu
disco local ou vice versa.  Veja <xref linkend="cmdn-ftp"para mais detalhes.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 1 MB de disco.



<varlistentry>
<term>telnet
<listitem>

Modo Texto - Conexão ao terminal virtual remotamente.  Permite controlar seu
terminal remotamente através de uma conexão via rede TCP/IP.  Veja <xref linkend="cmdn-telnet"para mais detalhes.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 1 MB de disco.



<varlistentry>
<term>talk
<listitem>

Modo Texto - Permite conversar com outros usuários <command>GNU/Linux
conectados através de uma rede TCP/IP no estilo do Bate Papo ou do Chat do ICQ.
Veja <xref linkend="cmdn-talk"para mais detalhes.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 1 MB de disco.



<varlistentry>
<term>fetchmail
<listitem>

Modo Texto - Permite baixar as mensagens de seu servidor de e-mail para o seu
diretório de usuário no sistema.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 1 MB de disco.



<varlistentry>
<term>procmail
<listitem>

Modo Texto - Organiza mensagens em arquivos separados de acordo com a
origem/assunto/conteúdo.  O <command>procmail é muito flexível e
também permite resposta automática de acordo com alguns tipos de mensagens e a
criação de filtros de mensagens muito poderosos caso você conheça e saiba
integrar as ferramentas do sistema.



<varlistentry>
<term>bitchx
<listitem>

Programa de IRC muito complexo e poderoso.  Ele opera em modo texto e em modo
gráfico (xbitchx).  Tem que ter disposição de hacker para aprender o que
significam cada uma das 4 telas de comandos obtidos com o /help.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 4 MB de disco.



<varlistentry>
<term>xchat
<listitem>

Programa de IRC muito fácil de usar e com muitos recursos.  Ele possui versões
para modo texto e gráfico e possui suporte a scripts Perl e Python,
personalização de menus, comandos, etc.  Sua flexibilidade é muito boa para
quem conhece os comandos dos clientes IRC.  Também permite o log das conversas
públicas e privadas.  Também funciona via proxy tradicional ou Firewall.


Equipamento mínimo recomendado: 386 com 8 MB de RAM e 3 MB de disco.



<varlistentry>
<term>licq
<listitem>

Modo gráfico - Programa de ICQ gráfico para <command>GNU/Linux.
Apesar de ter muitos recursos, sua interface é muito organizada e possui
suporte a seleção de sua aparência (**Skins**).  Emite avisos
sonoros e levanta-se sobre as outras janelas durante o recebimento de
mensagens.  Também funciona via proxy tradicional ou Firewall.


Equipamento mínimo recomendado: 486 com 16 MB de RAM e 10 MB de disco.



<varlistentry>
<term>gaim
<listitem>

Modo gráfico - Possui suporte a múltiplos protocolos, podendo se conectar ao
ICQ, MSN, Jabber, e outros.


Equipamento mínimo recomendado: 486 com 16 MB de RAM e 20 MB de disco.



<varlistentry>
<term>zicq
<listitem>

Modo Texto - Programa de ICQ em modo Texto.


Equipamento mínimo recomendado: 386 com 2 MB de RAM e 1 MB de disco.



<varlistentry>
<term>amsn
<listitem>

Modo Gráfico - Suporta protocolo MSN.


Equipamento mínimo recomendado: 486 com 16 MB de RAM e 8 MB de disco.



</variablelist>


 aplic-b-emuladores">###Emuladores
<variablelist>
<varlistentry>
<term>DosEmu
<listitem>

Emulador do DOS.  Permite executar aplicativos e jogos de DOS no
<command>GNU/Linux


Equipamento mínimo recomendado: 486 com 8 MB de RAM e 4 MB de disco.



<varlistentry>
<term>Wine
<listitem>

Emulador de Windows.  Permite executar aplicativos desenvolvidos para Windows
3.1X, 9X, NT e 200x no <command>GNU/Linux.


Equipamento mínimo recomendado: 486 com 16 MB de RAM e 12 MB de disco.



</variablelist>


 aplic-b-utils">###Utilitários
<variablelist>
<varlistentry>
<term>Midnight Commander
<listitem>

Gerenciador de Arquivos no estilo do **Norton Commander** e
**Far**.  Opera tanto em modo texto e gráfico e possui todas
as qualidades dos gerenciadores acima, mais o suporte ao painel FTP, permissões
de arquivos e dicas sobre o sistema.  Simples, prático e útil.


Equipamento mínimo recomendado: 386 com 4 MB de RAM e 2 MB de disco.



<varlistentry>
<term>wget
<listitem>

Modo Texto - Permite a cópia completa de sites remotos e também pode ser usado
como mirror.  Com o simples comando <literal>wget
 [guiafoca](http://www.guiafoca.org) ), todo o site do guia **Foca
Linux** será gravado em seu disco.  O <command>wget também
tem a característica de resumir downloads interrompidos e copiar somente
arquivos mais novos.


Gostou da idéia?  Isto é só o começo!  existem ferramentas mais poderosas no
<command>GNU/Linux :-)


Equipamento mínimo recomendado: 386 com 4 MB de RAM e disco dependendo do
tamanho do site que deseja copiar (um disco maior que 540 MB exige uma placa
mãe com suporte a LBA :-)



</variablelist>


 aplic-b-admin">###Administração do Sistema
<variablelist>
<varlistentry>
<term>logcheck
<listitem>

Envia um E-Mail periodicamente ao usuário alertando sobre ocorrências especiais
encontradas nos logs do sistema, como tentativas de invasão sem sucesso,
tentativas de acesso ao usuário root do sistema, erros nos dispositivos,
mensagens dos daemons, inetd, etc.



</variablelist>




 s42.2">###Listagem de Aplicativos para <command>GNU/Linux

Esta seção contém uma listagem dos mais diversos tipos de
aplicativos/ferramentas/scripts/suites/servidores, etc.  para
<command>GNU/Linux com sua respectiva descrição.  A listagem está
organizada em ordem alfabética e subseções para facilitar a sua navegação e
localização do aplicativo desejado.


Alguns aplicativos marcados com <literal>(D) no final da descrição
são **Docks** que são executados como ícones no gerenciador de
janelas.

 aplic-l-perifericos">###Periféricos / Gerenciamento de Hardware
<itemizedlist>
<listitem>

<literal>3c5x9utils - Utilitários de configuração e diagnóstico para
placas 3Com 5x9


<listitem>

<literal>apcupsd - Gerenciamento de Energia para No Breaks APC


<listitem>

<literal>buffer - Programa de buffering/reblocking para backup em
tapes, impressão, etc


<listitem>

<literal>dds2tar - Ferramenta para usar características DDS de
unidades DAT com o programa tar da GNU


<listitem>

<literal>dtlk -Controlador de dispositivo Linux para o DoubleTalk PC


<listitem>

<literal>eject - ejeta CDs e opera CD-Changers sob o Linux


<listitem>

<literal>estic - Programa de administração para ISDN PABX ISTEC
1003/1008


<listitem>

<literal>gatos - Software de captura TV All-in-Wonder da ATI


<listitem>

<literal>genpower - Monitor de No Break e manipulador de falhas de
energia


<listitem>

<literal>hdparm - Permite fazer um ajuste fino na performance do
disco rígido


<listitem>

<literal>hpscanpbm - Utilitário para o Scanner HP ScanJet


<listitem>

<literal>hwtools - Coleção de ferramentas para o gerenciamento em
baixo nível do hardware


<listitem>

<literal>isapnp - Permite configurar recursos de dispositivos
Plug-and-Play no Linux


<listitem>

<literal>jazip - monta e desmonta Zip drives Iomega e/ou Jaz


<listitem>

<literal>jaztool - Utilitário para manipular drives Iomega


<listitem>

<literal>joystick -Ferramentas de teste e calibragem de Joysticks


<listitem>

<literal>lcdproc - Daemon de tela LCD


<listitem>

<literal>lm-sensors - Utilitários para ler a
temperatura/voltagem/sensores da ventoinha da CPU


<listitem>

<literal>mtx - Controla unidades tape autochangers


<listitem>

<literal>pciutils - Utilitários PCI para o Linux (para kernels
2.[123].x )


<listitem>

<literal>powstatd - Daemon de monitoramento de No Breaks configurável


<listitem>

<literal>prime-net - Permite doar ciclos da CPU não usados - Cliente
PrimeNet GIMPS


<listitem>

<literal>sane-gimp1.1 - Interface para Scanners no gimp


<listitem>

<literal>sane - Interface para Scanners.  Permite a comunicação e uso
de diversos tipos de scanners diferentes.


<listitem>

<literal>setcd - Controla características de funcionamento de sua
unidade de CD-ROM (auto-lock, auto-eject, etc)


<listitem>

<literal>sformat - Formatador de discos SCSI e ferramenta de reparo


<listitem>

<literal>svgatextmode - Executa o modo de texto em alta resolução


<listitem>

<literal>synaptics - Configura um TouchPad da Synaptics


<listitem>

<literal>upsd - Programa monitor de No Breaks


<listitem>

<literal>wanpipe - Utilitários de configuração para placas Sangoma
S508/S514 WAN


<listitem>

<literal>wdsetup - Utilitário de configuração para placas ethernet
Western Digital e SMC


<listitem>

<literal>xsane-gimp1.1 - Uma interface X11 baseada no GTK para o SANE
(Scanner Access Now Easy)


<listitem>

<literal>xsane - Uma interface X11 baseada no GTK para o SANE
(Scanner Access Now Easy)


<listitem>

<literal>xviddetect - Detecta o modelo da placa de vídeo e indica
servidores X associados a placa





 aplic-l-internet">###Internet
<itemizedlist>
<listitem>

<literal>arena - um navegador WWW compatível com HTML 3.0 para o X


<listitem>

<literal>bezerk - Cliente IRC baseado em GTK


<listitem>

<literal>bitchx - Cliente IRC Avançado


<listitem>

<literal>bitchx-gtk - Interface gráfica GTK para o BitchX


<listitem>

<literal>cftp - Cliente ftp de tela cheia


<listitem>

<literal>chimera2 - Navegador Web para o X


<listitem>

<literal>dxftp - Cliente FTP Darxite baseado em linha de comando


<listitem>

<literal>epic4 - Cliente irc epic irc client, versão 4


<listitem>

<literal>epic - Cliente ircII modificado com funcionalidades
adicionais


<listitem>

<literal>everybuddy - Cliente ICQ, AOL, Yahoo (tudo em 1)


<listitem>

<literal>express - Navegador web baseado em GTK para o GNOME


<listitem>

<literal>filerunner - Programa FTP e Gerenciador de Arquivos baseado
em X


<listitem>

<literal>ftp - O cliente FTP padrão


<listitem>

<literal>ftp-upload - Envia arquivos FTP através de um script


<listitem>

<literal>gaim - Um clone GTK do AOL Instant Messenger


<listitem>

<literal>gftp - Cliente FTP do X/GTK+


<listitem>

<literal>gnap - Cliente Gnome para o Napster


<listitem>

<literal>gnapster - Cliente Napster para Linux - localiza arquivos
MP3 na Internet


<listitem>

<literal>gnomeicu - Clone pequeno, rápido e funcional do Mirabilis
ICQ


<listitem>

<literal>gnome-napster - Cliente Napster para Linux - localiza
arquivos MP3 na Internet


<listitem>

<literal>gpppon - Um applet do gnome que funciona como uma interface
ao pon e poff


<listitem>

<literal>gzilla - Um navegador web baseado em GTK


<listitem>

<literal>irssi - Cliente IRC para Gnome


<listitem>

<literal>isdnbutton - Inicia e Interrompe conexões ISDN e mostra
status


<listitem>

<literal>licq-data - Arquivos de daods para o Licq


<listitem>

<literal>licq-plugin-qt2 - Interface gráfica para o Licq usando
bibliotecas QT2


<listitem>

<literal>licq - Programa ICQ gráfico para Linux


<listitem>

<literal>lynx - Navegador WWW em modo texto


<listitem>

<literal>micq - Cliente ICQ baseado em texto com muitas
características


<listitem>

<literal>mosaic - Navegador WWW Gráfico


<listitem>

<literal>mozilla - Um Navegador WWW de código aberto para o X e GTK+


<listitem>

<literal>ncftp2 - Um cliente FTP com interface fácil e com muitas
características


<listitem>

<literal>ncftp - Um cliente FTP com interface fácil e com muitas
características


<listitem>

<literal>Netscape - Navegador gráfico com programa de e-mail, news,
livro de endereços, editor de páginas HTML.  Suporta Java, tabelas, frames,
CSS, proxy, etc...


<listitem>

<literal>ppxp - Programa PPP


<listitem>

<literal>ppxp-tcltk - Console tk do ppxp


<listitem>

<literal>ppxp-x11 - Console X do ppxp


<listitem>

<literal>quickppp - Ferramenta de configuração PPP


<listitem>

<literal>realplayer - Real Player


<listitem>

<literal>sysnews - Mostra noticias do sistema (de /var/news)


<listitem>

<literal>talk - Permite conversar com outro usuário conectado ao
sistema ou via rede TCP/IP


<listitem>

<literal>tftp - Programa trivial file transfer


<listitem>

<literal>tik - Cliente Tcl/Tk do serviço AOL Instant Messenger


<listitem>

<literal>utalk - programa parecido com o talk com características
adicionais


<listitem>

<literal>vrwave - Navegador baseado em VRML 2.0 java


<listitem>

<literal>vrweb - Um navegador VRML e editor


<listitem>

<literal>wvdial - Discador PPP com inteligência embutida.


<listitem>

<literal>wxftp-gtk - Um programa ftp gráfico com a interface GTK


<listitem>

<literal>xchat - Cliente IRC para X similar ao AmIRC


<listitem>

<literal>xchat-gnome - Cliente IRC para o GNOME similar ao AmIRC


<listitem>

<literal>xisp - Uma interface X amigável ao pppd/chat


<listitem>

<literal>xitalk - Programa talk que lista usuários atuais do sistema.
Ele também pode iniciar uma seção talk, tocar som, executar um aplicativo, etc.
durante uma requisição talk


<listitem>

<literal>xrn - Leitor de news NNTP baseado em X


<listitem>

<literal>xtalk - Um cliente X-Window BSD talk, escrito em Python


<listitem>

<literal>ytalk - Programa talk avançado com suporte ao X


<listitem>

<literal>zicq - Cliente ICQ baseado em ncurses





 aplic-l-conferencia">###Conferência de audio/vídeo via Internet/Intranet
<itemizedlist>
<listitem>

<literal>camediaplay - Interface de Câmera Digital


<listitem>

<literal>cqcam - Programa de Controle da Câmera Colorida QuickCam
(PC/Paralela)


<listitem>

<literal>gphoto - Aplicativo Universal para câmeras digitais


<listitem>

<literal>gstalker - Stock and commodity price charting utility


<listitem>

<literal>photopc - Interface para câmeras digitais


<listitem>

<literal>phototk - Interface gráfica para câmeras digitais


<listitem>

<literal>qcam - Capturador de Imagens da QuickCam


<listitem>

<literal>qvplay - Ferramenta de comunicação para a câmera Casio QV


<listitem>

<literal>rat - RAT - Ferramenta de conferência de audio unicast e
multicast


<listitem>

<literal>Vat - Ferramenta de audio conferência via rede/Internet


<listitem>

<literal>vic - Ferramenta de vídeo conferência


<listitem>

<literal>wbd - Prancha de Desenho para Multicast


<listitem>

<literal>webcam - Captura e faz o upload automático de imagens para
um servidor web





 aplic-l-webhtml">###Gerenciamento de WebSites / Linguagem HTML
<itemizedlist>
<listitem>

<literal>adacgi - Interface CGI para o Ada


<listitem>

<literal>amaya - Editor HTML Gráfico da w3.org


<listitem>

<literal>analog - Analiza arquivos de log de servidores www


<listitem>

<literal>bk2site - Utilitário para tornar bookmarks em páginas
parecidas com o yahoo/Slashdot


<listitem>

<literal>bluefish - Um editor HTML baseado em Gtk+


<listitem>

<literal>bookmarker - Gerenciamento de bookmark baseado em WWW,
ferramenta de recuperação e procura


<listitem>

<literal>bookmarks - Outra coleção de bookmarks


<listitem>

<literal>browser-history - Daemon do usuário que captura URLs
procuradas e as registra


<listitem>

<literal>c2html - Destaca códigos em C para apresentação em WWW


<listitem>

<literal>cgic-capture - Captura de ambiente CGI para depuração


<listitem>

<literal>cgiemail - Conversor de formulário CGI para E-Mail


<listitem>

<literal>cgilib - Biblioteca CGI simples


<listitem>

<literal>cgiwrap - Permite usuários ordinários executar seus próprios
Scripts CGI


<listitem>

<literal>checkbot - Verificador de links WWW


<listitem>

<literal>cocoon - Um Framework de publicação XML/XSL


<listitem>

<literal>cronolog - Um roteador de arquivos de log para servidores
web


<listitem>

<literal>curl - Copia um arquivo de um servidor FTP, GOPHER, ou HTTP
(sem suporte a ssl)


<listitem>

<literal>cvs2html - Cria versões em html dos logs do CVS


<listitem>

<literal>faqomatic - FAQ cgi online e interativa


<listitem>

<literal>freetable - Um script em Perl que facilita a produção de
tabelas HTML


<listitem>

<literal>gifsicle - Poderoso programa para a manipulação de imagens
GIF


<listitem>

<literal>giftrans - Converte qualquer arquivo GIF em um GIF89a


<listitem>

<literal>gnujsp - Uma implementação gratuita do Sun's Java Server
Pages (JSP 1.0)


<listitem>

<literal>gtml - Um pré-processador HTML


<listitem>

<literal>htdig - Sistema de procura WWW para a Intranet ou uma
pequena internet


<listitem>

<literal>htget - Um capturador de arquivos que obtém arquivos atraes
de servidores HTTP


<listitem>

<literal>htmldoc - Processador HTML que gera arquivos HTML, PS, e PDF
indexados


<listitem>

<literal>htmlgen - Geração de documentos HTML com scripts em Python


<listitem>

<literal>htp - Um pré-processador HTML


<listitem>

<literal>http-analyze - Um analizador rápido de logs de servidores
WWW


<listitem>

<literal>hypermail - Cria arquivos HTML de listas de discussões por
E-Mail


<listitem>

<literal>imaptool - Uma ferramenta para a criação de mapas de imagens
do lado cliente


<listitem>

<literal>imgsizer - Adiciona os atributos WIDTH e HEIGHT a tags IMG
tags em arquivos HTML


<listitem>

<literal>imho - Módulo de E-Mail baseado na Web para o Roxen (usando
IMAP)


<listitem>

<literal>imp - Programa de E-Mail baseado em IMAP para a Web


<listitem>

<literal>java2html - Destaca códigos em Java e C++ para apresentação
via WWW


<listitem>

<literal>jserv - Motor Java Servlet 2.0 com um módulo Apache
adicional


<listitem>

<literal>junkbuster - O Junkbuster da Internet!


<listitem>

<literal>latte - A linguagem para transformação de texto (atualmente
para html)


<listitem>

<literal>linbot - Verificador de links de sites WWW


<listitem>

<literal>lists-archives - Arquivo Web para listas de discussão por
E-Mail


<listitem>

<literal>mailto - Ligação de formulários WWW com o programa de E-Mail


<listitem>

<literal>muffin - Um proxy Web pessoal e extensível


<listitem>

<literal>pas2html - Destaca fontes do Pascal e Modula para
apresentação via WWW


<listitem>

<literal>pcd2html - Scripts para converter imagens PCD para páginas
HTML comentadas


<listitem>

<literal>perl2html - Destaca fontes do Perl para apresentação via WWW


<listitem>

<literal>php3 - Uma linguagem script embutida em HTML - lado do
servidor


<listitem>

<literal>php4 - Uma linguagem script embutida em HTML - lado do
servidor


<listitem>

<literal>phplib - Biblioteca para escrever aplicações para a Web
facilmente


<listitem>

<literal>plugger - Plug-in Mime do Netscape


<listitem>

<literal>rpm2html - Gera índices HTML dos diretórios de RPMs


<listitem>

<literal>screem - Um ambiente de desenvolvimento de website


<listitem>

<literal>sitecopy - Um programa para gerenciar um site WWW via FTP


<listitem>

<literal>squishdot - Sistema de discussão/news baseado na Web


<listitem>

<literal>swish-e - Sistema simples de indexação Web para Humanos


<listitem>

<literal>swish++ - Sistema simples de indexação Web para Humanos++


<listitem>

<literal>tidy - Verificador de sintaxe HTML e reformatador do código


<listitem>

<literal>w3mir - Ferramenta de cópia completa HTTP e mirror


<listitem>

<literal>wdg-html-validator - Verificador de arquivos HTML


<listitem>

<literal>webalizer - Programa de análise arquivos de log do servidor
Web


<listitem>

<literal>weblint - Um verificador de sintaxe e estilo mínimo para
HTML


<listitem>

<literal>webmagick - Cria uma galeria de thumbnails para website


<listitem>

<literal>websec - Secretária Web


<listitem>

<literal>wget - Utilitário para copiar arquivos atraes da WWW via
HTTP e FTP com suporte a reinicio do ponto de interrupção do download.


<listitem>

<literal>wmf - Web Mail Folder


<listitem>

<literal>wml - Website META Language por Ralf Engelschall


<listitem>

<literal>wwwcount - Contador de acessos a páginas Web


<listitem>

<literal>wwwoffle - Explorer OFFline da World Wide Web


<listitem>

<literal>wwwtable - Um script em Perl que facilita a produção de
tabelas em HTML


<listitem>

<literal>xsitecopy - Um programa para gerenciar um site WWW via FTP
(versão GNOME)


<listitem>

<literal>zope - O Ambiente de Publicação de Objetos Z





 aplic-l-multimidia">###Multimídia
<itemizedlist>
<listitem>

<literal>gxanim - Interface em GTK para o xanim


<listitem>

<literal>smpeg-gtv - Exibe arquivos MPEG de audio/vídeo com interface
em GTK+


<listitem>

<literal>smpeg-plaympeg - Exibe arquivos MPEG de audio/vídeo através
da linha de comando


<listitem>

<literal>streamer - Programa de captura de vídeo para a bt848 a
video4linux


<listitem>

<literal>tkxanim - Interface Tcl/Tk para o xanim


<listitem>

<literal>ucbmpeg - Encoder de vídeo MPEG e ferramentas de análise


<listitem>

<literal>ucbmpeg-play - Exibe arquivos de vídeo MPEG


<listitem>

<literal>vstream - Utilitário de captura de vídeo bttv para a criação
de MPEGs


<listitem>

<literal>xanim - Exibe arquivos multimídia (animações, filmes e sons)


<listitem>

<literal>xanim-modules - Instalação de binários de xanim - somente
módulos





 aplic-l-som">###Som
<itemizedlist>
<listitem>

<literal>ascdc - CD changer ideal para ser usado no After Step junto
com o módulo wharf


<listitem>

<literal>ascd - CD Player e mixer para Window Maker e After Step (D)


<listitem>

<literal>aumix - Mixer em modo texto que permite modificar, salvar e
restaurar a configuração de som na inicialização do sistema


<listitem>

<literal>bplay - Player/Gravador wav que opera em modo texto (root)


<listitem>

<literal>cam - Mixer para modo texto com controle completo da placa
de som.  Também permite salvar e restaurar a configuração de som, embora isto
seja mais simples através do aumix.


<listitem>

<literal>cdda2wav - Extrai audio do CD para arquivos wav e mp3


<listitem>

<literal>cd-diskio - Obtem dados do CDDB sobre o CD de audio


<listitem>

<literal>cdparanoia - Extrai dados de CD para wav


<listitem>

<literal>cdtool - Utilitários para manipulação de CD player em modo
texto


<listitem>

<literal>dtmfdial - Gera tons de discagem para linhas tom


<listitem>

<literal>festival - Lê textos para a placa de som do sistema


<listitem>

<literal>freeamp - Player mp2/mp3


<listitem>

<literal>gramofile - Programa de gravação de músicas de disco de
vinil para wav com filtros para retirada de ruídos


<listitem>

<literal>graudio - Permite controlar placas de rádio FM


<listitem>

<literal>grip - CD-Ripper e CD-Player (do CD paranoia)


<listitem>

<literal>gtick - Gera ruídos de batida em <filename>/dev</filename> e
<filename>/dsp</filename>


<listitem>

<literal>id3 - Modifica cabeçalhos de identificação de arquivos mp3


<listitem>

<literal>maplay - Decoder mp3 que permite a decodificação para a
saída padrão


<listitem>

<literal>mctools - CDplayer e mixer


<listitem>

<literal>mixer.app - Mixer para Window Maker (D)


<listitem>

<literal>mp3blaster - Player mp3 para console


<listitem>

<literal>mp3info - Mostra cabeçalho de arquivos mp3


<listitem>

<literal>nas - Network Audio Server - Sistema de audio através da
rede


<listitem>

<literal>playmidi - Toca musicas .mid


<listitem>

<literal>recite - Lê textos para a placa de som do sistema


<listitem>

<literal>rplay - Toca sons através da rede


<listitem>

<literal>s3mod - Player para arquivos de música s3m e mod


<listitem>

<literal>saytime - Diz as horas na placa de som


<listitem>

<literal>snack - Adiciona suporte a som na linguagem TCL/TK


<listitem>

<literal>soundtracker - Módulos para edição.  suporta módulos .xt e
instrumentos .xi


<listitem>

<literal>sox - Tradutor universal de sons


<listitem>

<literal>splay - Toca arquivos mp1, mp2, mp3


<listitem>

<literal>synaesthesia - Osciloscópio musical


<listitem>

<literal>timitidy - Midi sequencer.  Também faz a conversão de
arquivos .mid para .wav


<listitem>

<literal>tkmixer - Mixer em TCL/TK


<listitem>

<literal>transcriber - Permite gravar notas durante a descrição de
programas


<listitem>

<literal>vkeybd - Teclado virtual (requer placa awe)


<listitem>

<literal>wav2cdr - Converte wav em arquivos cdr.  Permite edição de
músicas


<listitem>

<literal>wavtools - Ferramentas para arquivos wav (player, recorder,
compactação)


<listitem>

<literal>wmcdplayer - Módulo de Cd player para Window Maker


<listitem>

<literal>wmxmms-spectrum - Spectrum analizador para Window Maker (D)


<listitem>

<literal>workbone - CD player para modo texto operado através do
teclado numérico


<listitem>

<literal>wosundprefs - Preferências musicais para o Window Maker


<listitem>

<literal>wsoundserver - Servidor de som para Window Maker


<listitem>

<literal>xcolmix - Um mixer colorido RGB


<listitem>

<literal>xfreecd - Programa para tocar CDS


<listitem>

<literal>xmcd - CD player/changer muito completo com suporte ao CDDB


<listitem>

<literal>xmix - Mixer para o X


<listitem>

<literal>xmp - Player mod, s3m, 669, mtm, ptm, okt, far, wow, amd,
rad, alm





 aplic-l-comm">###Comunicação/Fax
<itemizedlist>
<listitem>

<literal>adbbs - AD BBS, uma BBS baseada em perl ou menu de sistema
fácil


<listitem>

<literal>efax - Programas para enviar e receber mensagens de fax


<listitem>

<literal>hylafax-client - Programa HylaFAX cliente


<listitem>

<literal>hylafax-server - Programa HylaFAX servidor


<listitem>

<literal>lrzsz - Ferramentas para a transferência de arquivos através
de zmodem/xmodem/ymodem


<listitem>

<literal>mgetty-fax - Ferramentas de Fax para o mgetty


<listitem>

<literal>mgetty - Substituição ao getty


<listitem>

<literal>mgetty-viewfax - Programa para mostrar arquivos de fax sob o
X


<listitem>

<literal>mgetty-voice -Secretária Eletrônica para o mgetty


<listitem>

<literal>minicom - Clone do "Telix" - um programa de comunicação do
DOS


<listitem>

<literal>mserver - Servidor de Modem para a Rede


<listitem>

<literal>seyon - Programa de comunicação nativo completo nativo do
X11


<listitem>

<literal>smsclient - Um programa para enviar mensagens curtas para
telefones móveis/Pagers (SM / SMS)


<listitem>

<literal>speaker - Aplicativo Viva Voz baseado em Tcl/Tk


<listitem>

<literal>tkhylafax - Uma interface td ao hylafax


<listitem>

<literal>xringd - Daemon de chamadas Extendida - Monitora toques do
telefone e executa alguma ação





 aplic-l-x11">###X Window
<itemizedlist>
<listitem>

<literal>asclock - Relógio do After Step


<listitem>

<literal>dfm - Gerenciador de Arquivos/Desktop


<listitem>

<literal>dgs - Visualizador de arquivos do Ghost Script


<listitem>

<literal>dxpc - Compactador do protocolo X para linhas lentas


<listitem>

<literal>floatbg - Modifica lentamente a cor do fundo da janela do
root


<listitem>

<literal>gdm - Gerenciador de seção do GNOME - Substituição ao xdm


<listitem>

<literal>gentoo - Um gerenciador de arquivos totalmente configurável
para o X usando o GTK+


<listitem>

<literal>gtkcookie - Editor de arquivos cookie


<listitem>

<literal>gtkfind - Localizador de arquivos completo


<listitem>

<literal>gtkfontsel - Visualizador de fontes


<listitem>

<literal>ical - Um aplicativo de calendário baseado em X11/Tk


<listitem>

<literal>regexplorer - Explorer visual de expressões regulares


<listitem>

<literal>rt - Mostra arquivos de log selecionados na janela raíz do X


<listitem>

<literal>sclient - Um cliente MUD baseado em gtk.


<listitem>

<literal>sfm - Um gerenciador de arquivos baseado em texto usando o
GTK+


<listitem>

<literal>tkdesk - Um gerenciador de Desktop/Arquivos X11 baseado em
TCL/TK


<listitem>

<literal>tkvnc - Mostra uma lista de máquinas definidas para iniciar
o VNC


<listitem>

<literal>tkworld - Uma interface gráfica para comandos do shell


<listitem>

<literal>tuxeyes - Uma versão do xeyes para o penguim


<listitem>

<literal>ude - Ambiente desktop do Unix


<listitem>

<literal>unclutter - Oculta o mouse no X após um período de
inatividade


<listitem>

<literal>uwm - Gerenciador de janelas ultimate para o UDE


<listitem>

<literal>vreng - Motor de realidade virtual


<listitem>

<literal>wdm - Substituição ao XDM com visual do Window Maker,
animações e suporte a seleção do gerenciador de janelas


<listitem>

<literal>wmanager - Permite selecionar o gerenciador de janelas após
o login do xdm


<listitem>

<literal>wmapm - Mostra o status da bateria, gerenciamento de energia
do sistema (D)


<listitem>

<literal>wmdate - Mostra a data/dia da semana (D)


<listitem>

<literal>wmifs - Monitor das interfaces de rede com indicador de
atividade das interfaces (envio/recebimento) gráfico de atividade na rede e
indicador de interface ativa (D)


<listitem>

<literal>wmitime - Relógio analógico+digital+data e hora da Internet.
(D)


<listitem>

<literal>wmload - Mostra a carga da CPU na forma de barras (D)


<listitem>

<literal>wmmail - Monitor de E-mails (D)


<listitem>

<literal>wmmatrix - Mostra um dock do matrix (D)


<listitem>

<literal>wmmixer - Mixer para o Window maker (D)


<listitem>

<literal>wmmoonclock - Relógio da lua (D)


<listitem>

<literal>wmnet - Monitor de interfaces de rede (D)


<listitem>

<literal>wmnetselect - Dispara o netscape através de um ícone (D)


<listitem>

<literal>wmpinboard - Todo list com animações e um excelente visual
(D)


<listitem>

<literal>wmspaceweather - Monitora prótons e elétrons do espaço (D)


<listitem>

<literal>wmtime - Relógio analógico, dia da semana e data (D)


<listitem>

<literal>wmtv - Sintonlizador de TV para Window Maker com suporte a
seleção de canais, sistema de cores PAM-M/Secam/NTSC, ajuste fino, procura de
estações de TV, uso de aplicativos de TV externos e muito mais (D)


<listitem>

<literal>x2x - Liga a imagem de 2 monitores simulando multi-telas


<listitem>

<literal>xautolock - Inicia um programa após certo período de
inatividade do X


<listitem>

<literal>xawtv - Visualizador Video4linux


<listitem>

<literal>xbanner - Deixa a tela de login mais bonita


<listitem>

<literal>xext - Extensões para os servidores X


<listitem>

<literal>xfishtank - Mostra um aquário na janela raíz do X Window


<listitem>

<literal>xfs - Servidor de fontes do X


<listitem>

<literal>xfs-xtt - Servidor de fontes do X com suporte a fontes true
type


<listitem>

<literal>xinput - Configuração em tempo de execução e teste para
dispositivos de entrada do X


<listitem>

<literal>xipmsg - Envia mensagens


<listitem>

<literal>xjscal - Calibrador de Joystick para o X11


<listitem>

<literal>xkbsel - Ferramenta para definir, selecionar e indicar
teclados para o X


<listitem>

<literal>xkbsel-gnome - Ferramenta para definir, selecionar e indicar
teclados para o X (versão para Gnome)


<listitem>

<literal>xkeycaps - Mostra o código de teclas do seu teclado no X
para a construção de um Xmodmap personalizado


<listitem>

<literal>xlockmore-gl - Versão do xlockmore em GL


<listitem>

<literal>xlockmore - Trava a tela do X até que uma senha seja
digitada


<listitem>

<literal>xmaddressbook - Agenda de endereços para o X


<listitem>

<literal>xmanpages - Visualizador de páginas de manual para o X


<listitem>

<literal>xmbdfed - Editor de fontes para o X11


<listitem>

<literal>xmon - Monitor do protocolo X


<listitem>

<literal>xmotd - Navegador da mensagem do dia par ao X


<listitem>

<literal>xodo - Mede a "distância" percorrida pelo cursos do seu
mouse.  É permitido escolher até a unidade de medida da distância


<listitem>

<literal>xpaste - Mostra o conteúdo copiado com CTRL+C


<listitem>

<literal>xrootconsole - Melhora a aparência do desktop


<listitem>

<literal>xscreensaver - Coleção de Screen Savers automático para o X


<listitem>

<literal>xscreensaver-gl - Proteções de tela GL para o xscreensaver


<listitem>

<literal>xsm - Gerenciador de seção do X


<listitem>

<literal>xsnow - Animação de neve para o X (muito legal).


<listitem>

<literal>xt - Traceroute gráfico em GL.  Mostra o caminho percorrido
por sua conexão até chegar ao destino


<listitem>

<literal>xvt - Emulador de terminal do X parecido com o xterm, mas
menor


<listitem>

<literal>xwit - Uma coleção de rotinas simples para chamar algumas
funções do X11


<listitem>

<literal>xwrits - Te lembra para dar uma parada na digitação


<listitem>

<literal>xzoom - Lente de aumento para parte da sua tela do X, com
atualizações rápidas





 aplic-l-edicao">###Editoração Gráfica/Visualizadores
<itemizedlist>
<listitem>

<literal>dia - Editor de Diagramas


<listitem>

<literal>egon - Programa de animações da Siag Office


<listitem>

<literal>gimp - O Programa de Manipulação de Imagens da GNU


<listitem>

<literal>imagemagick - Programas de manipulação de Imagem


<listitem>

<literal>mentor - Uma coleção de algoritmos de animação


<listitem>

<literal>moonlight - Cria e desenha cenas em 3D


<listitem>

<literal>pixmap - Um editor de pixmaps


<listitem>

<literal>qcad - Sistema CAD PROFISSIONAL.


<listitem>

<literal>qiv - Um visualizador rápido de imagens para o X


<listitem>

<literal>saoimage - Utilitário para mostrar e processar imagens
atronômicas


<listitem>

<literal>sced - Um programa para criar cenas em 3D


<listitem>

<literal>sketch - Um programa de desenho interativo do X11


<listitem>

<literal>terraform - Um programa para geração/manipulação de mapas
Tridimensionais da Terra


<listitem>

<literal>tgif - Programa para desenhos 2-D sob o X11


<listitem>

<literal>whirlgif - Cria GIFs animadas


<listitem>

<literal>xbmbrowser - Navegador para Pixmaps e Bitmaps


<listitem>

<literal>xfig - Facilita a geração de figuras interativamente sob o
X11


<listitem>

<literal>xli - Visualiza imagens sob o X11


<listitem>

<literal>xloadimage - Visualizador de arquivos gráficos sob o X11


<listitem>

<literal>xpcd - Coleção de ferramentas PhotoCD: Básico


<listitem>

<literal>xpcd-gimp - Coleção de ferramentas PhotoCD: Suporte ao Gimp


<listitem>

<literal>xpcd-svga - Coleção de ferramentas PhotoCD: Visualizador
SVGA


<listitem>

<literal>xv-doc - Documentação do XV em Posscript e HTML.


<listitem>

<literal>xv - Uma visualizador e manipulador de imagens para o X
Window System


<listitem>

<literal>xwpick - Captura uma tela X11 e armazena em arquivos





 aplic-l-emul">###Emuladores/Ferramentas p/ Interação com outros SO
<itemizedlist>
<listitem>

<literal>doschk - Verifica a compatibilidade de arquivos SYSV e DOS


<listitem>

<literal>dosemu - Emulador de DOS para Linux


<listitem>

<literal>dosfstools-Utilitários para criar e checar sistemas de
arquivos DOS FAT


<listitem>

<literal>hfsutils - Ferramenta para ler e gravar volumes Macintosh.


<listitem>

<literal>hfsutils-tcltk -Interface Tcl/Tk para ler e gravar volumes
Macintosh


<listitem>

<literal>macutils - Conjunto de ferramentas para negociar com
arquivos especiais do Macintosh


<listitem>

<literal>mcvert - Ferramenta para negociar com arquivos encodificados
especiais do Macintosh


<listitem>

<literal>mixal - Um emulador MIX e interpretador MIXAL


<listitem>

<literal>mtools - Ferramenta para manipulação de arquivos do DOS


<listitem>

<literal>p3nfs - Monta unidades da séria Psion 3[ac], 5


<listitem>

<literal>simh - Um emulador de vários computadores DEC


<listitem>

<literal>stella - Emulador do video game Atari 2600 Emulator para X
Windows


<listitem>

<literal>uae-exotic - O Emulador Amiga Ubiquitous: Binários exóticos


<listitem>

<literal>uae - O Emulador Amiga Ubiquitous: Básico


<listitem>

<literal>uae-suid - O Emulador Amiga Ubiquitous: Binários Suid root


<listitem>

<literal>umsdos - Utilitários para o sistema de arquivos UMSDOS


<listitem>

<literal>vice - Emulador versátil do commodore


<listitem>

<literal>wine - Emulador do Windows (Emulador Binário)


<listitem>

<literal>xapple2 - Emulador do Apple


<listitem>

<literal>xcopilot - Emulador do Pilot


<listitem>

<literal>xspectemu - Emulador do Spectrim Fast 48k ZX para X11


<listitem>

<literal>xtrs - Emulador para os computadores TRS-80 Modelos
I/III/4/4P


<listitem>

<literal>xzx - Emulador de espectro baseado em ZX para o X11





 aplic-l-prog">###Programação / Bancos de Dados / Acesso a Dados
<itemizedlist>
<listitem>

<literal>bcc - Compilador C 16 Bits


<listitem>

<literal>bin86 - Assembler 16 bits e carregador


<listitem>

<literal>binutils - Assembler da GNU, linker e utilitários binários


<listitem>

<literal>clc-intercal - Compilador para a linguagem Intercal


<listitem>

<literal>cmucl - Compilador lisp CMUCL e sistema de desenvolvimento


<listitem>

<literal>colorgcc - Colore mensagens de alerta/erro do GCC


<listitem>

<literal>cutils - Utilitários de código fonte C


<listitem>

<literal>cvs - Concurrent Versions System


<listitem>

<literal>cvsweb - uma interface CGI ao seu repositório CVS


<listitem>

<literal>cxref - Gera documentação em latex e HTML para seus
programas em C


<listitem>

<literal>dbf2pg - Converte arquivos do xBase para PostgreSQL


<listitem>

<literal>dbf - Pacote de manipulação de arquivos xbase


<listitem>

<literal>dbview - Visualiza arquivos do dBase III


<listitem>

<literal>dialog - Permite adicionar o recurso de caixas de diálogo em
shell scripts como "Yes/No", "Ok", "Cancelar", etc.


<listitem>

<literal>dist - Ferramentas para desenvolver, manter e distribuir
softwares


<listitem>

<literal>doc++ - Um sistema de documentação para C/C++ e Java


<listitem>

<literal>f2c -Um tradutor do Fortran77 para C/C++ com bibliotecas
estáticas e compartilhadas


<listitem>

<literal>f77reorder - Um script de compilação Fortran chamando o
f2c/gcc


<listitem>

<literal>fp-api -Units Livres da API do Pascal


<listitem>

<literal>fp-compiler - Compilador Livre do Pascal


<listitem>

<literal>fp-extra - Pacotes Extras do Pascal Livre


<listitem>

<literal>fp-fcl - Pascal Livre - Biblioteca de Componentes Livres


<listitem>

<literal>fp-gtk - Ligações Pascal - GTK


<listitem>

<literal>fp-utils - Units do Pascal Livre


<listitem>

<literal>freetds-jdbc - Driver JDBC Java puro para MS SQL e Sybase


<listitem>

<literal>g77 - Compilador GNU Fortran 77.


<listitem>

<literal>gbdk-dev - Kit de desenvolvimento do GameBoy - pacotes de
desenvolvimento


<listitem>

<literal>gbdk-examples - Kit de desenvolvimento do GameBoy - pacote
de exemplos


<listitem>

<literal>gbdk -Kit de desenvolvimento GameBoy - pacote binário


<listitem>

<literal>gcc272-docs - Documentação para compiladores gcc (gcc272,
g++272)


<listitem>

<literal>gcc-i386-gnu - Cheap cross-compiler para GNU/Hurd


<listitem>

<literal>gcc - O compilador C da GNU


<listitem>

<literal>g++ - Compilador GNU C++


<listitem>

<literal>gdb - O depurador GNU


<listitem>

<literal>gengetopt - Gerador de estrutura main.c


<listitem>

<literal>global - Ferramenta de procura e navegação do código fonte


<listitem>

<literal>gpc - Compilador Pascal da GNU


<listitem>

<literal>gprolog - Compilador GNU Prolog


<listitem>

<literal>gtksql - Interface gráfica GTK para o banco de dados
posgress SQL


<listitem>

<literal>guavac - Compilador java


<listitem>

<literal>hello-debhelper - O programa inicial e um bom exemplo


<listitem>

<literal>hello - O programa inicial e um bom exemplo


<listitem>

<literal>indent - Programa de formatação do código fonte em linguagem
C


<listitem>

<literal>inform - Compilador para jogos de aventura


<listitem>

<literal>jitterbug - Um ferramenta cgi-bin para relato de problemas e
teste


<listitem>

<literal>lclint - Uma ferramenta para checagem estática de programas
em C


<listitem>

<literal>liwc - Ferramentas para manipular o código fonte em C


<listitem>

<literal>mercury - Nova linguagem de programação lógica/funcional


<listitem>

<literal>mmake - Gerador Makefile para programas em java


<listitem>

<literal>mpsql - Uma interface gráfica ao PostgreSQL


<listitem>

<literal>mysql-client - Binários cliente do banco de dados mysql


<listitem>

<literal>mysql-gpl-client - Binários cliente do banco de dados mysql


<listitem>

<literal>mysql-manual - Documentação não oficial do MySQL 3.20


<listitem>

<literal>mysql-server 3.22.32-1 - binários do servidor do banco de
dados mysql


<listitem>

<literal>nosql - um sistema de Gerenciamento de Banco de Dados
Relacional para Unix


<listitem>

<literal>p2c - Tradutor Pascal para C


<listitem>

<literal>pentium-builder - Força a compilação otimizada para
computadores Pentium


<listitem>

<literal>pgaccess - Interface gráfica Tk/Tcl para o banco de dados
PostgreSQL


<listitem>

<literal>phylip - [Biology] A program package for inferring
phylogenies


<listitem>

<literal>postgresql - Banco de dados SQL relacionado a objetos,
descendente do POSTGRES


<listitem>

<literal>postgresql-client - Programas de interface para o PostgreSQL


<listitem>

<literal>postgresql-contrib - Facilidades adicionais para o
PostgreSQL


<listitem>

<literal>postgresql-test - Conjunto de testes de regressão para o
PostgreSQL


<listitem>

<literal>smalleiffel - Compilador Eiffel GNU


<listitem>

<literal>solid-desktop - Servidor SQL Sólido


<listitem>

<literal>solid-devel - Desenvolvimento do Servidor SQL Sólido


<listitem>

<literal>solid-doc-Documentação do servidor sólido SQL


<listitem>

<literal>solid-tools - Ferramentas do servidor sólido SQL


<listitem>

<literal>www-mysql - Uma interface WWW interface para o banco de
dados TCX mySQL


<listitem>

<literal>www-pgsql - Uma interface WWW para o banco de dados
PostgreSQL


<listitem>

<literal>xmysqladmin - Interface gráfica para o mysql (3.22.xx)


<listitem>

<literal>xxgdb - Interface gráfica para o GNU debugger gdb





 aplic-l-impressao">###Impressão
<itemizedlist>
<listitem>

<literal>apsfilter - Um filtro de linha de impressão para sistemas
com lpd/lpr


<listitem>

<literal>cupsys-bsd - Common UNIX Printing System(tm) - comandos BSD


<listitem>

<literal>cupsys - Common UNIX Printing System(tm) - básico


<listitem>

<literal>djtools - Ferramentas para a impressora HP Deskjet


<listitem>

<literal>ifhp - Filtro para impressoras HP LaserJet


<listitem>

<literal>lprng - Sistema de spooling de impressão lpr/lpd


<listitem>

<literal>lpr - Sistema de spooling da linha de impressão estilo BSD


<listitem>

<literal>magicfilter - Filtro automático de impressora


<listitem>

<literal>mpage - Mostra múltiplas páginas em uma impressora
PostScript


<listitem>

<literal>printop - Interface gráfica para o daemon de impressão LPRng


<listitem>

<literal>printtool - Ferramenta de administração de impressoras


<listitem>

<literal>psptools - Ferramentas para impressoras PostScript e
dispositivos


<listitem>

<literal>rlpr -Um utilitário para impressão do ldp sem usar o
/etc/printcap


<listitem>

<literal>wip - Pacote de para ploters gráficos com alta qualidade de
saída





 aplic-l-texto">###Texto
<itemizedlist>
<listitem>

<literal>1a2ps - Conversor GNU de "tudo para PostScript" e impressão


<listitem>

<literal>abc2ps - Traduz arquivos de descrição de música ABC para
PostScript


<listitem>

<literal>acroread - Adobe Acrobat Reader: Visualizador de arquivos
Portable Document Format


<listitem>

<literal>aspell - Uma substituição mais inteligente para o
verificador ortográfico ispell


<listitem>

<literal>brazilian-conjugate - Conjugador de verbos Portugues do
Brasil


<listitem>

<literal>catdoc - Conversor de arquivos MS-Word para TeX ou texto
plano


<listitem>

<literal>colortail - tail que colore os padrões que conferem


<listitem>

<literal>cost - Ferramenta de pós processamento SGML de propósito
geral


<listitem>

<literal>debiandoc-sgml -DTD DebianDoc SGML e ferramentas de
formatação


<listitem>

<literal>docbook - DTD SGML para a documentação de software


<listitem>

<literal>dog - Substituição avançada para o cat


<listitem>

<literal>figlet - Cria palavras usando tabelas de caracteres ASCII


<listitem>

<literal>flip - Converte arquivos de texto entre os formatos DOS e
Unix


<listitem>

<literal>ghostview - Um visualizador PostScript para o X11


<listitem>

<literal>gnuhtml2latex - Um Script Perl que converte arquivos html em
latex


<listitem>

<literal>gs-aladdin - Interpretador PostScript com suporte a X11 e
preview svgalib


<listitem>

<literal>gsfonts - Fontes para o interpretador ghostscript


<listitem>

<literal>gs - Interpretador PostScript com suporte a X11 e preview
svgalib


<listitem>

<literal>gtkdiff - Ferramenta de comparação de texto gráfica


<listitem>

<literal>help2man - Gerador automático de páginas de manual


<listitem>

<literal>html2ps - Conversor HTML para PostScript


<listitem>

<literal>iamerican - Um dicionário de Inglês Americano para o ispell


<listitem>

<literal>ibrazilian - Um dicionário do Brasileiro para o ispell


<listitem>

<literal>ispell - International Ispell (um corretor ortográfico
interativo)


<listitem>

<literal>less - Programa de paginação de arquivos, parecido com o
more


<listitem>

<literal>lincredits - Gera versões com melhor formatação do arquivo
CREDITS do Linux


<listitem>

<literal>lookup - utilitário para procurar arquivos de texto
rapidamente e com muitos recursos


<listitem>

<literal>lout - Sistema de Digitação, uma alternativa ao (La)TeX


<listitem>

<literal>lv - Um poderoso visualizador de arquivos multi-língua


<listitem>

<literal>lyx - Processador de textos de alto nível


<listitem>

<literal>mgdiff - clone do xdiff


<listitem>

<literal>mswordview - Um conversor de arquivos MS Word 97/2000 para
HTML


<listitem>

<literal>ndtpd - Servidor CD-ROM books


<listitem>

<literal>par - Reformatador de parágrafo


<listitem>

<literal>pbm2ppa - Conversor PBM para PPA


<listitem>

<literal>perlsgml - Ferramentas para construir e analizar DTDs SGML


<listitem>

<literal>perspic - Programa indexador de textos e localizador de
palavras


<listitem>

<literal>poster - Faz grandes posters de páginas PostScript


<listitem>

<literal>ppd-gs - Arquivos de descrição de impressora PostScript para
o Ghostscript


<listitem>

<literal>pstotext - Extrai textos de arquivos PostScript e PDF


<listitem>

<literal>recode - Utilitário de conversão do conjunto de caracteres


<listitem>

<literal>sgml-base - Utilitário para manter o arquivo de catálogo
SGML


<listitem>

<literal>sgml-data - Dados comuns entre DTDs SGML e entities


<listitem>

<literal>sgml-tools - Conversores SGML somente par ao DTD linuxdoc


<listitem>

<literal>spell - Spell GNU, um clone do "spell" para Unix


<listitem>

<literal>sufary - Ferramentas de procura em texto completo usando uma
array de sufixos


<listitem>

<literal>sufary-tcltk - Interface Tcl/Tk para o SUFARY


<listitem>

<literal>tcs - Tradutor de conjunto de caracteres


<listitem>

<literal>tkdiff - Utilitário "diff" gráfico


<listitem>

<literal>trueprint - Imprime de forma organizada o código fonte


<listitem>

<literal>word2x - Traduz arquivos do Word em texto ascii ou LaTeX


<listitem>

<literal>xpdf - Visualizador do formato Portable Document Format para
X11


<listitem>

<literal>xpw - O processador de textos Patético





 aplic-l-kernel">###Kernel
<itemizedlist>
<listitem>

<literal>adjtimex - Mostra e configura variáveis do kernel


<listitem>

<literal>autofs - Montador automático baseado no kernel para Linux


<listitem>

<literal>kernellab - Gerencia facilmente configurações do kernel em
muitas máquinas


<listitem>

<literal>kernel-package - Scripts de construção do pacote de kernel
para a Debian


<listitem>

<literal>knl - Obtém/ajusta parâmetros de imagem do kernel


<listitem>

<literal>ksymoops - Interpreta mensagens oops e de erro do kernel


<listitem>

<literal>psmisc - Utilitários que utilizam o sistema de arquivos
/proc


<listitem>

<literal>systune - Ajuste fino do kernel através do sistema de
arquivos /proc





 aplic-l-notebooks">###Notebooks
<itemizedlist>
<listitem>

<literal>apmd - Utilitário para gerenciamento avançado de energia
(APM) em Notebooks


<listitem>

<literal>toshutils - Utilitários para Note Books Toshiba


<listitem>

<literal>wmbattery - Mostra o status/carga da bateria (D)





 aplic-l-cdrec">###Gravação de CD/DVD
<itemizedlist>
<listitem>

<literal>cdrdao - Grava CDs de audio ou tipos de dados diversos no
disco de uma só vez


<listitem>

<literal>cdrecord - Ferramenta de gravação de CD/DVD


<listitem>

<literal>cdrtoaster - Interface gráfica em Tcl/Tk para gravar CD-ROMs


<listitem>

<literal>cdwrite - Ferramenta de gravação de CD para unidades CD-R
Orange Book


<listitem>

<literal>cdlabelgen - Gera capa e fundo para CDs


<listitem>

<literal>gtoaster - Gnome Toaster, uma interface gráfica para
gravação de CD's


<listitem>

<literal>mkhybrid - Cria imagens do sistema de arquivos CD-ROM


<listitem>

<literal>mkisofs - Cria imagens do sistema de arquivos CD-ROM
ISO-9660


<listitem>

<literal>tkcdlayout - Programa simples em X para criar capas de CDs


<listitem>

<literal>xcdroast - Software de gravação de CDs baseado no X





 aplic-l-cluster">###Computação Paralela/Clusters
<itemizedlist>
<listitem>

<literal>lam2-dev - Ativa processamento paralelo entre múltiplos
processadores


<listitem>

<literal>mpich - Sistema de computação Paralela


<listitem>

<literal>pvm - Máquina Virtual Paralela - binários e bibliotecas
compartilhadas





 aplic-l-handhelds">###PalmTop / Palm Pilot / Computadores de Mão
<itemizedlist>
<listitem>

<literal>imgvtopgm -Utilitário de conversão de imagem PalmPilot/III


<listitem>

<literal>jpilot -Um utilitário GTK para modificar o conteúdo de seus
Bancos de Dados no Pilot.


<listitem>

<literal>lpkg - Carregador do pacotes de mensagens para o PDA Newton
MessagePad


<listitem>

<literal>lx-gdb - Mostra e carrega banco de dados do palmtop da HP


<listitem>

<literal>lxtools -Permite o gerenciamento de arquivos em palmtops
HP100/200LX


<listitem>

<literal>palm-doctoolkit - Ferramentas de texto eletrônico para
usuários PalmPilot


<listitem>

<literal>picasm -Assembler para a familia de controladores Microchip
PIC


<listitem>

<literal>pilot-link -Ferramentas para se comunicar com um Pilot 3COM
PDA através de uma porta serial


<listitem>

<literal>pilot-manager - PalmPilot PIM, UI, e gerenciador de conduíte


<listitem>

<literal>pilot-template - Gerador de código para programas do
PalmPilot


<listitem>

<literal>pilrc - Compilador de recursos e editor do PalmPilot/PalmIII


<listitem>

<literal>pose - Emulador PalmOS


<listitem>

<literal>prc-tools - GCC, GDB, binutils, etc.  para o PalmPilot e
Palm III


<listitem>

<literal>pyrite - Kit da plataforma de comunicação Palm Computing(R)
para Python





 aplic-l-backup">###Backup
<itemizedlist>
<listitem>

<literal>afbackup-client - Sistema de backup cliente-servidor (lado
Cliente)


<listitem>

<literal>afbackup - Sistema de backup cliente-servidor (lado
Servidor)


<listitem>

<literal>amanda-client - Advanced Maryland Automatic Network Disk
Archiver (Cliente)


<listitem>

<literal>amanda-common - Advanced Maryland Automatic Network Disk
Archiver (Libs)


<listitem>

<literal>amanda-server - Advanced Maryland Automatic Network Disk
Archiver (Servidor)


<listitem>

<literal>floppybackup - Backup em disquetes usando diversos tipos de
formatos de disquetes


<listitem>

<literal>taper - Utilitário de backup do sistema em tela cheia


<listitem>

<literal>tob - Programa pequeno e poderoso orientado a backup de
tapes





 aplic-l-uteis">###Utilitários
<itemizedlist>
<listitem>

<literal>afio - Programa de manipulação de arquivos


<listitem>

<literal>aish - Conversor ish/base64/uuencoded_file


<listitem>

<literal>alien - Instala pacotes da Red Hat, Stampede e Slackware com
o dpkg


<listitem>

<literal>ascii - Mostra aliases e tabela para caracteres ASCII


<listitem>

<literal>autoconf - Script de configuração automático


<listitem>

<literal>autogen - Gerador automático de arquivos texto


<listitem>

<literal>automake - Gerador automático de scripts Makefile


<listitem>

<literal>autoproject - Cria um esqueleto de pacote fonte para um novo
programa


<listitem>

<literal>barcode - Cria código de barras no formato .ps


<listitem>

<literal>binstats - Ferramenta de estatística para programas
instalados


<listitem>

<literal>birthday - Alerta sobre eventos pendentes no login


<listitem>

<literal>blinkd -Pisca LEDS do teclado para uma secretária eletrônica
ou máquina de fax


<listitem>

<literal>bl - Pisca seqüencialmente os LEDs do teclado


<listitem>

<literal>bsdmainutils - Mais utilitários do 4.4BSD-Lite


<listitem>

<literal>btoa - Converte binário para ascii e vice versa


<listitem>

<literal>cbb - Um clone do Quicken


<listitem>

<literal>chase - Segue um link simbólico e mostra seu arquivo alvo


<listitem>

<literal>dgpsip - Corrige localização GPS com o sinal DGPS da
internet


<listitem>

<literal>diffstat - produz gráficos das alterações introduzidas por
um arquivo diff


<listitem>

<literal>dotfile-bash - Gerador de arquivos dotfile, módulo para o
bash


<listitem>

<literal>dotfile -Configuração fácil de programas populares através
da interface Tcl/Tk


<listitem>

<literal>dotfile-elm - Gerador de arquivos dotfile, módulo para o elm


<listitem>

<literal>dotfile-fvwm1 - Gerador de arquivos dotfile, módulo para o
fvwm1


<listitem>

<literal>dotfile-fvwm2 - Gerador de arquivos dotfile, módulo para o
fvwm2


<listitem>

<literal>dotfile-ipfwadm - Gerador de arquivos dotfile, módulo para o
ipfwadm


<listitem>

<literal>dotfile-procmail - Gerador de arquivos dotfile, módulo para
o procmail


<listitem>

<literal>dotfile-rtin - Gerador de arquivos dotfile, módulo para o
rtin


<listitem>

<literal>dotfile-tcsh - Gerador de arquivos dotfile, módulo para o
tcsh


<listitem>

<literal>dump - 4.4bsd dump e restore para sistema de arquivos ext2


<listitem>

<literal>fastjar - Utilitário de criação de arquivos Jar


<listitem>

<literal>fdupes - Identifica arquivos duplicados residindo nos
diretórios especificados


<listitem>

<literal>fdutils - Utilitários de disquete do Linux


<listitem>

<literal>file - Determina o tipo de arquivo usando números "mágicos"


<listitem>

<literal>gcal - Mostra um calendário


<listitem>

<literal>gettext - Utilitários de internacionalização da GNU


<listitem>

<literal>gfloppy - Interface gráfica para a formatação de disquetes


<listitem>

<literal>git - Ferramentas interativas da GNU


<listitem>

<literal>glimpse - Ferramentas de indexação e localização em tela
cheia


<listitem>

<literal>gmc - Midnight Commander - Um poderoso gerenciador de
arquivos - Versão gnome


<listitem>

<literal>gmemusage -Mostra um gráfico detalhando a utilização de
memória por cada processo


<listitem>

<literal>gnotes - Applet de notas Yellow sticky para o GNOME


<listitem>

<literal>gnucash - Um programa de tratamento de finanças pessoais


<listitem>

<literal>gpm - Daemon de mouse para modo texto


<listitem>

<literal>grep-dctrl - Versão do gru para informações de pacotes da
Debian


<listitem>

<literal>gtktalog - Catálogo de Disco


<listitem>

<literal>guitar - Ferramenta de extração/visualização de arquivos em
GTK+


<listitem>

<literal>gxset - Interface gráfica baseada em GTK a ferramenta de
linha de comando xset


<listitem>

<literal>hextype - Hexdump de acordo com o formato de saída do antido
Debug do DOS


<listitem>

<literal>iraf - Redução de Imagem e Facilidade de Análise
(astronomia/imagem)


<listitem>

<literal>jdresolve - Alternativa rápida ao logresolve do Apache


<listitem>

<literal>kbd - Utilitários de fonte e mapas de teclado para o console
do Linux


<listitem>

<literal>launcher - Seleciona que programa carregar de acordo com a
extensão


<listitem>

<literal>lavaps - Uma lâmpada de lava dos processos atualmente
executados


<listitem>

<literal>leave - Te lembra quando deve deixar o sistema (muito útil
para quem gosta do Linux :-)


<listitem>

<literal>linuxlogo - Logotipo do Sistema Colorido em ANSI


<listitem>

<literal>loadwatch - Executa um programa usando somente ciclos
ociosos da CPU


<listitem>

<literal>makepatch - gera/aplica arquivos de patch com mais
funcionalidade que o diff plano


<listitem>

<literal>mc-common - Arquvios comuns par ao mc e gmc


<listitem>

<literal>mc - Midnight Commander - Um poderoso gerenciador de
arquivos


<listitem>

<literal>mirrordir - Duplica um diretório fazendo um mínimo de
modificações


<listitem>

<literal>ncdt - Mostra a árvore de diretórios


<listitem>

<literal>netplan - Servidor de rede para o "plan"


<listitem>

<literal>nwrite - Substituição avançada ao comando write


<listitem>

<literal>patch - Aplica um arquivo gerado pelo diff a um original


<listitem>

<literal>pcal - Cria calendários imprimíveis via PostScript sem o X


<listitem>

<literal>perforate - Utilitários para salvar espaço em disco


<listitem>

<literal>pgrep - utilitário grep que usa expressões regulares
compatíveis com o Perl


<listitem>

<literal>plan - Planejamento diário baseado em X/Motif (compilado
dinamicamente com LessTif)


<listitem>

<literal>pointerize - Utilitários de internacionalização baseado no
gettext


<listitem>

<literal>popularity-contest - Vote em seus pacotes favoritos
automaticamente


<listitem>

<literal>pydf - Clone df com saída em cores


<listitem>

<literal>rtlinux - Linux em Tempo Real


<listitem>

<literal>set6x86 -Ferramenta de configuração para CPUs Cyrix/IBM
5x86/6x86


<listitem>

<literal>splitvt - Executa dois programas em uma tela dividida


<listitem>

<literal>statserial - Mostra a linha de status da porta serial do
modem


<listitem>

<literal>strace - Um traçador de chamadas do sistema


<listitem>

<literal>sunclock - Mostra porção iluminada do planeta terra


<listitem>

<literal>symlinks - procura/modifica links simbólicos


<listitem>

<literal>tleds - Pisca LEDs do teclado indicando Envio e Recebimento
de pacotes da rede


<listitem>

<literal>tree - Mostra a árvore de diretórios em cores


<listitem>

<literal>units - conversor entre diferentes unidades de sistema


<listitem>

<literal>uptimed - Utilitário para registrar seus maiores tempos de
utilização do sistema


<listitem>

<literal>urlview - Extrai URLs de textos


<listitem>

<literal>vold - Daemon de volume para unidades de CDROM


<listitem>

<literal>vrms - Virtual Richard M.  Stallman (mostra mensalmente uma
lista de pacotes não-livres instalados em seu sistema)


<listitem>

<literal>wipe - Deleção segura de arquivos (sem possibilidade de
recuperação)


<listitem>

<literal>xcal - Um calendário gráfico com alarmes de alerta


<listitem>

<literal>xplanet - Cria imagens do planeta Terra


<listitem>

<literal>xvmount - Pequeno utilitário gráfico para a montagem de
dispositivos pelos usuários





 aplic-l-compactadores">###Compactadores/Descompactadores/Arquivadores
<itemizedlist>
<listitem>

<literal>bzip2 - Um ótimo compactador de arquivos texto - utilitários


<listitem>

<literal>gzip - Compactador de arquivos de formato .gz


<listitem>

<literal>lha - Compactador de arquivos no formato .lha ou .  lzh


<listitem>

<literal>lzop - Um compactador em tempo real


<listitem>

<literal>ncompress - Compress / Uncompress original para a
transferência de News, etc.


<listitem>

<literal>rar - Compactador/Descompactador de arquivos .rar


<listitem>

<literal>tar - Utilitário de arquivamento de arquivos


<listitem>

<literal>unarj - Descompactador de arquivos .arj


<listitem>

<literal>unzip - Descompactador de arquivos .zip


<listitem>

<literal>zoo - Manipula arquivos compactados no formato .zoo





 aplic-l-x10">###Dispositivos X-10 (Controle de eletrodomésticos e aparelhos via PC)
<itemizedlist>
<listitem>

<literal>bottlerocket - Utilitário para controle de dispositivos X10


<listitem>

<literal>heyu - Comunicação X10 de dois pontos para o CM11A


<listitem>

<literal>wmx10 - Permite controlar uma casa através de módulos x10.
Este aplicativo permite controlar até 8 dispositivos por casa (D)


<listitem>

<literal>x10 - Opera módulos de controle de força elétrica


<listitem>

<literal>X10x10-automate - Interface gráfica para o utilitário de
controle de força de linha X10


<listitem>

<literal>xtend - Daemon monitor de status X10





 aplic-l-outros">###Outros
<itemizedlist>
<listitem>

<literal>acs - Simulador de Circuito Al's


<listitem>

<literal>avra - Montador para microcontroladoras AVR Atmel


<listitem>

<literal>avrp - Programador para microcontroladoras AVR Atmel


<listitem>

<literal>chipmunk-log - Ferramenta de captura esquemática e ambiente
de simulação


<listitem>

<literal>cracklib2-dev - Uma biblioteca de checagem de senhas


<listitem>

<literal>cracklib2 - Uma biblioteca de checagem de senhas


<listitem>

<literal>cracklib-runtime - Uma biblioteca de checagem de senhas


<listitem>

<literal>display-dhammapada - Mostra versos do Dhammapada


<listitem>

<literal>fastdnaml - [Biologia] Uma ferramenta para construção de
árvores da seqüência do DNA


<listitem>

<literal>geda - GNU EDA -- Software de design eletrônico


<listitem>

<literal>gwave - Um visualizador waveform para simuladores spice


<listitem>

<literal>megahal - Um simulador de conversação que pode aprender


<listitem>

<literal>mime-support - Arquivos MIME "mime.types" e "mailcap", e
programas


<listitem>

<literal>nitpic - Simulador para o Microcontrolador Microchip
PIC16C84


<listitem>

<literal>pcb - Programa de Design de Placas de Circuito Impresso


<listitem>

<literal>puzzle - [Biology] Reconstruction of phylogenetic trees by
maximum likelihood


<listitem>

<literal>readseq - [Biologia] Conversão entre formatos em seqüência


<listitem>

<literal>savant - Analizador VHDL 93 livre da University de
Cincinnati's


<listitem>

<literal>screen - Um gerenciador de tela com a emulação de terminal
VT100/ANSI


<listitem>

<literal>seaview - [Biologia] Um editor de alinhamento em múltiplas
seqüências


<listitem>

<literal>simulpic - Simulador de dispositivo PIC Microchip


<listitem>

<literal>smtm - Show Me The Money is a configurable Perl/Tk stock
ticker program


<listitem>

<literal>spim - Emulador MIPS R2000/R3000


<listitem>

<literal>xacc-smotif -Um programa de tratamento de finanças pessoais


<listitem>

<literal>xacc - Um programa de tratamento de finanças pessoais


<listitem>

<literal>xcircuit - Esquemas de circuitos de desenho de quase tudo





 aplic-l-admin">###Administração do Sistema/Servidor
<itemizedlist>
<listitem>

<literal>acct - Utilitários para manipulação de contas


<listitem>

<literal>anacron - Programa estilo cron para sistemas que ficam pouco
tempo ligado


<listitem>

<literal>aptitude - Interface baseada em console para o programa apt


<listitem>

<literal>at - Executa tarefas em determinado horário


<listitem>

<literal>autolog - Finaliza a conexão de usuários ociosos


<listitem>

<literal>chrony - Sincroniza o relógio de seu computador através de
servidores de hora na Internet/Rede


<listitem>

<literal>crashme - Testes estressantes para testar a estabilidade do
sistema operacional


<listitem>

<literal>cron - Executa aplicativos em data/horas determinadas


<listitem>

<literal>defrag - Desfragmentador de sistemas de arquivos ext2 minix
xiafs


<listitem>

<literal>dialdcost - Estimador de custo e painel do controle X para o
DIALD


<listitem>

<literal>divine - Detecção automática de configuração IP para
notebooks


<listitem>

<literal>eql - Ferramenta de balanceamento de carga para conexões
seriais


<listitem>

<literal>ext2resize - Modifica o tamanho de um sistema de arquivos
ext2


<listitem>

<literal>fakeroot - Oferece um falso ambiente root


<listitem>

<literal>falselogin - Shell de login Falso


<listitem>

<literal>fbgetty - Um console getty com e sem capacidade fremebuffer


<listitem>

<literal>fbset - Programa de manutenção de dispositivos Framebuffer


<listitem>

<literal>genromfs - É um equivalente ao mkfs para o sistema de
arquivos rom


<listitem>

<literal>gnome-apt - Interface gráfica do Gnome para o apt


<listitem>

<literal>gnome-print - Arquitetura de impressão para o GNOME


<listitem>

<literal>gpart - Analiza tabela de partição do PC e procura por
partições perdidas


<listitem>

<literal>gps - PS gráfico usando GTK


<listitem>

<literal>gtop - Variante gráfico do comando top


<listitem>

<literal>libpam-ldap - Módulo de Autenticação Plugável permitindo
interfaces LDAP


<listitem>

<literal>libpam-pwdfile - Módulo PAM permitindo autenticação no
estilo /etc/passwd


<listitem>

<literal>libpam-smb - Módulo PAM permitindo interface com o Samba


<listitem>

<literal>linuxconf-i18n - Arquivos de idiomas internacionais para o
Linuxconf


<listitem>

<literal>linuxconf - Um poderoso kit para administração do Linux


<listitem>

<literal>linuxconf-x - Interface X para o Linuxconf


<listitem>

<literal>loadlin - Um gerenciador de inicialização do Linux através
do DOS


<listitem>

<literal>lockvc - Programa para bloquear seu console do Linux


<listitem>

<literal>logcheck - Envia anomalias nos arquivos de log do sistema
por E-mail ao administrador


<listitem>

<literal>logrotate - Utilitário para rotação de Logs


<listitem>

<literal>lshell - Impõe limites no shell para proteger a integridade
do seu sistema


<listitem>

<literal>lsof-2.2 - Lista arquivos/portas utilizadas


<listitem>

<literal>makepasswd - Gera senhas encriptadas compatíveis com as
usadas no /etc/passwd


<listitem>

<literal>members - Mostra os membros de um grupo; por padrão, todos
os membros


<listitem>

<literal>menu - Oferece funções de atualização de menus para alguns
aplicativos


<listitem>

<literal>mon - Monitora o computador/serviços/tudo e alerta sobre
problemas


<listitem>

<literal>netenv - Configura seu sistema para diferentes ambientes de
rede


<listitem>

<literal>pwgen - Gerador automático de senha


<listitem>

<literal>sac - Contas de Login


<listitem>

<literal>slay - Destrói todos os processos do usuário


<listitem>

<literal>slocate - Uma substituição segura ao comando locale


<listitem>

<literal>stopafter - Destrói processos após um dado tempo


<listitem>

<literal>sudo - Oferece privilégios limitados do root para usuários
específicos


<listitem>

<literal>suidmanager - Gerencia Permissões de arquivos


<listitem>

<literal>syslog-ng - Próxima geração do daemon de LOGs


<listitem>

<literal>syslog-summary - Resume o conteúdo de um arquivo de log do
sistema


<listitem>

<literal>tcpquota - Um pacote de monitoração de discagem/masquerading


<listitem>

<literal>timeoutd - Um daemon de timeout flexível


<listitem>

<literal>tmpreaper - Limpa arquivos de diretórios de acordo com sua
idade


<listitem>

<literal>tripwire - Um verificador de integridade de arquivos e
diretórios


<listitem>

<literal>ttylog - Logger para porta serial


<listitem>

<literal>ttysnoop - TTY Snoop - Permite espionar suas conexões
telnet+serial


<listitem>

<literal>uutraf - Um analizador de tráfego UUCP e estimador de custo


<listitem>

<literal>vlock - Programa de bloqueio para o console virtual


<listitem>

<literal>whowatch - Ferramenta de monitoração em tempo real dos
logins e processos de usuários


<listitem>

<literal>xezmlm - Uma ferramenta de configuração de lista de
discussões para o X Window


<listitem>

<literal>xlogmaster - Um programa para monitorar arquivos de log


<listitem>

<literal>xwatch - Monitora arquivos de log e mostra novos logs em uma
janela do X





 aplic-l-rede">###Rede
 aplic-l-rede-netbios">###NetBios
<itemizedlist>
<listitem>

<literal>gnomba - Navegador Samba para GNOME


<listitem>

<literal>gnosamba - Utilitário de configuração gráfico para o Samba


<listitem>

<literal>linpopup - Versão do programa Winpopup para Xwindow,
executado através do Samba


<listitem>

<literal>samba - Um servidor NetBios/LanManager completo para Unix


<listitem>

<literal>smb2www - Um cliente de rede Windows que é acessível através
de um navegador web


<listitem>

<literal>smbclient -Um cliente NetBios/LanManager para Unix


<listitem>

<literal>smbfs - Comandos para a montagem e desmontagem de sistemas
de arquivos NetBeui no Linux


<listitem>

<literal>smb-nat - Ferramenta de análise de rede SMB


<listitem>

<literal>swat - Ferramenta de Administração Web do Samba


<listitem>

<literal>tkchooser - Permite a comunicação e visualização de recursos
em redes NetBios / outras


<listitem>

<literal>tksmb - Navegador de rede SMB/Netbios (Samba e Windows)





 aplic-l-rede-netware">###NetWare
<itemizedlist>
<listitem>

<literal>ipxripd - Daemon IPX RIP/SAP


<listitem>

<literal>ipx - Utilitários para configura a interface ipx do kernel


<listitem>

<literal>ncpfs - Utilitários para utilização de recursos de
servidores NetWare





 aplic-l-rede-macintosh">###Macintosh
<itemizedlist>
<listitem>

<literal>macgate - Programas user-space para o roteamento IP no
Appletalk


<listitem>

<literal>netatalk - Binários Appletalk do usuários





 aplic-l-rede-mon">###Sniffers/Monitoração/Diagnóstico de rede TCP/IP
<itemizedlist>
<listitem>

<literal>arpwatch - Monitor de atividade na estação Ethernet/FDDI.
Verifica o mapeamento de endereços ARP/Ethernet e envia modificações ao
administrador da rede


<listitem>

<literal>bigbrother - Um monitor do sistema e rede


<listitem>

<literal>bing - Teste de banda Empirical stochastic


<listitem>

<literal>echoping - Uma pequena ferramenta de testes para servidores
TCP


<listitem>

<literal>epan - Analizador de protocolo ethernet offline


<listitem>

<literal>ethereal - Analizador de tráfego da Rede


<listitem>

<literal>fakebo - Programa para detectar scans do Back Orifice e
NetBus


<listitem>

<literal>fping - Envia pacotes ICMP ECHO_REQUEST a computadores da
rede


<listitem>

<literal>hunt - Sniffer de pacotes avançado, hijacking e detecção de
conexões intrusas


<listitem>

<literal>icmpinfo - Interpreta mensagens ICMP


<listitem>

<literal>ipgrab - Utilitário no estilo do Tcpdump que mostra
informações detalhadas do cabeçalho IP


<listitem>

<literal>iplogger - Registro de eventos TCP e ICMP


<listitem>

<literal>ippl - Registrador de protocolos IP


<listitem>

<literal>iptraf - Monitor de rede IP Colorido e Interativo


<listitem>

<literal>jail -Programa de registro de seção ICMP


<listitem>

<literal>karpski -Analizador ethernet e sniffer


<listitem>

<literal>mrtg - Multi Router Traffic Grapher


<listitem>

<literal>mtr - Ncurses em tela cheia ou ferramenta traceroute para o
X11 tool


<listitem>

<literal>netdiag - Diagnósticos da Rede (trafshow, strobe, netwatch,
statnet, tcpspray, tcpblast)


<listitem>

<literal>ngrep - grep para o tráfego na rede


<listitem>

<literal>nmap - Ferramenta de Exploração da rede e scanner de
segurança


<listitem>

<literal>nsmon - Verificador de servidor intranet/internet


<listitem>

<literal>nstreams - Um analizador de saída do tcpdump


<listitem>

<literal>ntop - Mostra o uso da rede em um formato semelhante ao top


<listitem>

<literal>saint - Secure Administrator's Integrated Network Tool -
checagem e scanner de rede


<listitem>

<literal>satan - Security Auditing Tool for Analysing Networks


<listitem>

<literal>shaper - Traffic Shaper para Linux


<listitem>

<literal>sniffit - Sniffer de pacotes e ferramenta de monitoração


<listitem>

<literal>snort - Um sniffer/logger flexível que detecta ataques


<listitem>

<literal>tcpdump - Uma poderosa ferramenta para monitoração da rede e
aquisição de dados


<listitem>

<literal>tcpslice - Extrai peças de e/ou através dos arquivos do
tcpdump


<listitem>

<literal>traceroute - Traça a rota do tráfego de pacotes através de
uma rede TCP/IP


<listitem>

<literal>xnetload - Um Xload para os pacotes das interfaces de rede
taxas/totais





 aplic-l-rede-servidores">###Servidores de serviços TCP/IP - Utilitários dos Servidores
<itemizedlist>
<listitem>

<literal>aolserver-postgres - Driver PostgreSQL para o Servidor da
AOL


<listitem>

<literal>aolserver - Servidor Web da AOL


<listitem>

<literal>apache - Servidor HTTP versável e de alta performance


<listitem>

<literal>arpd - Um daemon ARP user-space


<listitem>

<literal>bind - Servidor de Nomes de Domínio da Internet


<listitem>

<literal>bnetd -Servidor Battle.Net para sistemas baseados no Unix


<listitem>

<literal>boa - Um servidor Web leve e de alta performance


<listitem>

<literal>bootparamd - Servidor de parâmetros de Inicialização


<listitem>

<literal>bootp - Servidor bootp/DHCP


<listitem>

<literal>cern-httpd - O Servidor CERN HTTP (World-Wide Web)


<listitem>

<literal>cfingerd - Daemon seguro do finger configurável


<listitem>

<literal>cucipop - Daemon POP3 da Cubic Circle


<listitem>

<literal>dante-server - Servidor SOCKS


<listitem>

<literal>darxite - Daemon que transfere arquivos via FTP/HTTP em
segundo plano


<listitem>

<literal>dhcp - Servidor DHCP para designação automática de endereços
IP


<listitem>

<literal>dhttpd - Servidor Web com segurança mínima.  Não possui
suporte a cgi-bin!


<listitem>

<literal>diald - Daemon de discagem em demanda para PPP e SLIP


<listitem>

<literal>dnrd - Daemon Proxy DNS


<listitem>

<literal>efingerd - Outro daemon finger para unix capaz de ajuste
fino em sua saída.


<listitem>

<literal>ffingerd - Um daemon seguro do finger


<listitem>

<literal>fingerd - Servidor de dados da conta do usuário


<listitem>

<literal>fspd - Servidor do Protocolo de Serviços de Arquivos (FSP)


<listitem>

<literal>ftpd - Servidor FTP


<listitem>

<literal>icecast-server - Streaming de sons MP3


<listitem>

<literal>ipip - Daemon de Encapsulamento IP sobre IP


<listitem>

<literal>ircd - Daemon do servidor IRC


<listitem>

<literal>ircd-dalnet - DALnet IRCd (Servidor IRC)


<listitem>

<literal>mrouted - Daemon de roteamento Multicast para conectar um
Mbone a sua subrede


<listitem>

<literal>net-acct - Daemon de conta IP em modo do usuário


<listitem>

<literal>netobjd - O daemon agente de objetos da rede


<listitem>

<literal>ntp - Daemon e utilitários para controle completo de
data/hora na rede - NTP v4


<listitem>

<literal>oidentd - Substituição ao daemon do ident


<listitem>

<literal>omirr - Daemon online do Mirror


<listitem>

<literal>pftp - Programa FTP rápido (SEM AUTENTICAÇÃO!)


<listitem>

<literal>pidentd - Servidor do protocolo TCP/IP IDENT


<listitem>

<literal>pkspxy - Daemon do servidor proxy do PGP Public Key


<listitem>

<literal>pptpd - Servidor Point to Point Tunneling


<listitem>

<literal>proftpd - Daemon FTP versátil com suporte a host virtuais
(multihomed)


<listitem>

<literal>qtss - Servidor de streaming multimídia


<listitem>

<literal>rbootd - Daemon de inicialização remota


<listitem>

<literal>rinetd - Servidor de redirecionamento da Internet


<listitem>

<literal>routed - Daemon de roteamento da Rede


<listitem>

<literal>roxen - O Servidor Web Roxem Challenger


<listitem>

<literal>rrlogind - Daemon de Login para o Serviço de Cable Modem
Road Runner


<listitem>

<literal>rsh-server - Servidores rsh


<listitem>

<literal>rusersd - Servidor de usuários logados


<listitem>

<literal>rwhod - Servidor de status do sistema


<listitem>

<literal>snmpd - Agente UCD SNMP (Simple Network Management Protocol)


<listitem>

<literal>snmptraplogd - Um daemon configurável snmp trap


<listitem>

<literal>socks4-server - Servidor SOCKS4 para o proxy de serviços
baseados em IP através de um firewall


<listitem>

<literal>squidclient - Extrai URLs via linha de comando que se
comunica com o squid


<listitem>

<literal>squid - Servidor Proxy de Alto desempenho/Cache de Objetos
da Internet


<listitem>

<literal>talkd - Daemon de monitoração que permite receber avisos de
talk de outros usuários


<listitem>

<literal>telnetd - O servidor telnet


<listitem>

<literal>tftpd - Servidor do protocolo Internet trivial file transfer


<listitem>

<literal>ugidd - Daemon de mapeamento de UID NFS


<listitem>

<literal>umich-ldapd - Servidor LDAP


<listitem>

<literal>urlredir - Utilitário para permitir o redirecionamento de
url ao squid


<listitem>

<literal>vncserver - Sevidor VNC


<listitem>

<literal>wu-ftpd - Um servidor FTP poderoso e muito usado


<listitem>

<literal>xtell - Programa simples de mensagens cliente e servidor


<listitem>

<literal>zebra - Um daemon de roteamento GPL com capacidades
BGP/OSPF/RIP





 aplic-l-rede-clientes">###Clientes de serviços TCP/IP - Utilitários dos Clientes

Atenção: Clientes de serviços comuns de rede estão listados na seção Internet

<itemizedlist>
<listitem>

<literal>bootpc - Cliente bootp


<listitem>

<literal>dante-client - Oferece um wrapper SOCKS para usuários
através de um firewall


<listitem>

<literal>darxite-applet - Applet do painel do que permite DnD através
do Netscape


<listitem>

<literal>darxite-control - Controle gnome para o darxite


<listitem>

<literal>darxstat - Cliente Darxite que mostra o estado atual


<listitem>

<literal>dhcpcd - Cliente DHCP para configuração automática de redes
IPv4


<listitem>

<literal>dhcp-client - Cliente DHCP


<listitem>

<literal>finger - Programa que visualiza dados da conta do usuário


<listitem>

<literal>hx - Cliente Unix para o Hotline


<listitem>

<literal>icecast-client - Streaming de MP3


<listitem>

<literal>nis - Cliente e daemons para o Serviço de Informações da
Rede (NIS)


<listitem>

<literal>pump - Cliente DHCP/BOOTP simples para kernels da série
2.2.x


<listitem>

<literal>rexec - Cliente de execução remota para um servidor exec


<listitem>

<literal>rsh-client - Clientes rsh


<listitem>

<literal>rstat-client - Um cliente para rstatd


<listitem>

<literal>socks4-clients - Contém ferramentas modificadas para operar
via Socks4 como rtelnet, rftp


<listitem>

<literal>svncviewer - Cliente VNS para SVGA (tela cheia)


<listitem>

<literal>telnet - O cliente telnet


<listitem>

<literal>whois - Cliente whois





 aplic-l-rede-outros">###Outros
<itemizedlist>
<listitem>

<literal>amd - Montador automático 4.4BSD


<listitem>

<literal>asp - Descobre endereço IP atual de computadores que
receberam endereço IP dinâmico


<listitem>

<literal>authbind - Permite programas não-root fazerem o bind() para
portas baixas


<listitem>

<literal>bridge - Programa de controle e documentação para ponte nos
kernels 2.0


<listitem>

<literal>dhcp-dns - Atualizações DNS dinâmicas para o DHCP


<listitem>

<literal>dhcp-relay - Relay para o DHCP


<listitem>

<literal>diskless - Gera a estrutura de arquuivos NFS para uma
inicialização sem disco rígido


<listitem>

<literal>diskless-image-secure - Arquivos requeridos para imagem raíz
segura do NFS


<listitem>

<literal>diskless-image-simple - Arquivos requeridos para imagem raíz
simples do NFS


<listitem>

<literal>dlint - Verifica informações de zonas dns usando chamadas no
servidor de nomes


<listitem>

<literal>dns-browse - Interfaces para a procura DNS


<listitem>

<literal>dnscvsutil - Mantém arquivos de zonas DNS sob o controle do
CVS


<listitem>

<literal>dnsutils - Utilitários para a manipulação de servidores DNS


<listitem>

<literal>dnswalk - Verifica detalhes da zona dns usando chamadas no
servidor de nomes


<listitem>

<literal>dsgtk - Mostra o status da transferência do Darxite em uma
janela GTK


<listitem>

<literal>dxclip - Monitor da área de transferência do Darxite baseado
em GTK


<listitem>

<literal>dxpref - Interface GTK para modificar as preferências do
Darxite


<listitem>

<literal>eggdrop - Robô de IRC Avançado


<listitem>

<literal>fmirror - Programa mirror ftp


<listitem>

<literal>frad - Ferramentas Frame Relay para controladores DLCI/SDLA
nos kernels 2.0/2.1


<listitem>

<literal>fsh - Execução rápida de comandos remotos através de
rsh/ssh/lsh


<listitem>

<literal>fsp - Utilitários clientes para o Protocolo de Serviços de
Arquivos (FSP)


<listitem>

<literal>ftpgrab - Utilitário para mirror de arquivos


<listitem>

<literal>ftpmirror - Faz mirror da árvore de diretórios com FTP


<listitem>

<literal>ftpwatch - Envia notificações de modificações em servidores
ftp remotos


<listitem>

<literal>gfcc - Centro de controle GTK firewall


<listitem>

<literal>gnome-network - Utilitários de rede gnome


<listitem>

<literal>ipac - Configuração de contas IP e ferramenta de estatística


<listitem>

<literal>iproute - Ferramentas profissionais para controlar a rede
nos kernels 2.2.x


<listitem>

<literal>iroffer - Bot de IRC


<listitem>

<literal>madoka - Proxy IRC pessoal, com registro de seções e
programa de bot (pirc)


<listitem>

<literal>mason - Cria interativamente um firewall de filtragem de
pacotes no Linux


<listitem>

<literal>masqdialer - Daemon Cliente-servidor para controle de links
PPP


<listitem>

<literal>mclient - Cliente para o sistema de controle PPP MasqDialer


<listitem>

<literal>midentd - Substituição ao identd com suporte a masquerading


<listitem>

<literal>mirror - Programa de mirror em Perl para manter os arquivos
do FTP sempre atualizados.  Excelente controle e gerenciamento


<listitem>

<literal>netboot - Inicialização de um computador sem disco rígido


<listitem>

<literal>netleds-applet - Applet de LEDs de rede para gnome


<listitem>

<literal>netmask - ajuda a configurar a máscara de rede


<listitem>

<literal>netselect - Seleciona o servidor mais rápido automaticamente


<listitem>

<literal>nfs-common - Arquivos de suporte NFS comuns a cliente e
servidores


<listitem>

<literal>nhfsstone - Programa de benchmark para NFS


<listitem>

<literal>npadmin - Obtém detalhes sobre uma impressora com
características SNMP


<listitem>

<literal>nscd - Biblioteca GNU C: Daemon de Cache do Serviço de Nomes
(manipulação de senhas e chamadas de grupos para serem usados com serviços
lentos como NIS, NIS+ ou LDAP)


<listitem>

<literal>nslint - Verifica a integridade de arquivos DNS


<listitem>

<literal>pkspxyc - Daemon do cliente proxy do PGP Public Key


<listitem>

<literal>plum - Proxy IRC, registro de seções e programa bot (pirc)


<listitem>

<literal>pppoe - Driver do PPP sobre Ethernet


<listitem>

<literal>queso - Guess the operating system of a remote machine


<listitem>

<literal>rdate - Ajusta a data do sistema através de um computador
remoto


<listitem>

<literal>rdist - Distribuição de arquivos remotos cliente e servidor


<listitem>

<literal>redir - Redireciona conexões TCP


<listitem>

<literal>rlinetd - Substituição ao inetd com muitas características


<listitem>

<literal>rstatd - Mostra informações de tempo de execução em máquinas
remotas


<listitem>

<literal>rsync - Programa de cópia rápida de arquivos (como rcp)


<listitem>

<literal>ruptime - Mostra status do host de máquinas locais


<listitem>

<literal>rusers - Mostra quem está logado em máquinas na rede local


<listitem>

<literal>rwalld - Escreve mensagens aos usuários logados atualmente
no computador


<listitem>

<literal>rwall - Envia uma mensagem a usuários logados em um
computador


<listitem>

<literal>rwho - Mostra quem está logado em máquinas locais


<listitem>

<literal>sliplogin - Ferramenta para se conectar a uma interface de
rede serial


<listitem>

<literal>slirp - Emulador SLIP/PPP usando uma conta shell dial up


<listitem>

<literal>snarf - Capturador de URL via linha de comando


<listitem>

<literal>snmp - Aplicativos UCD SNMP (Simple Network Management
Protocol)


<listitem>

<literal>socket - Ferramenta de soquete de múltiplos propósitos


<listitem>

<literal>stone - Repetidor de pacotes TCP/IP na camada do aplicativo


<listitem>

<literal>tcputils - Utilitários para programação TCP em shell scripts


<listitem>

<literal>tn5250 - Emulador telnet 5250 para acessar um IBM AS/400


<listitem>

<literal>umich-ldap-utils - Utilitários LDAP


<listitem>

<literal>uucp - Programa UUCP (Unix to Unix Copy)


<listitem>

<literal>wmppp.app - Um monitor PPP e de carga da rede com o visual
do NeXTStep


<listitem>

<literal>wmppxp - Um console PPxP para Window Maker (D)


<listitem>

<literal>xinetd - Substituição ao inetd com muitos avanços


<listitem>

<literal>zone-file-check - Verificador de sintaxe para arquivos de
zona do BIND







 aplic-l-developer">###Debian Developer
<itemizedlist>
<listitem>

<literal>bug - Ferramenta para Relatório de Falhas que faz interface
com o Debian Bug Tracking System


<listitem>

<literal>dbuild - Ferramenta para criar pacotes binários da Debian
através dos fontes da Debian


<listitem>

<literal>debbugs - O bug tracking system baseado no ativo Debian BTS


<listitem>

<literal>debhelper - programas úteis para debian/rules


<listitem>

<literal>debian-keyring - Chaves do GnuPG (e do obsoleto PGP) de
Desenvolvedores da Debian


<listitem>

<literal>debian-test -Scripts usados para executar testes em um
sistema Debian instalado


<listitem>

<literal>debmake - Ferramenta para criação de pacotes Debian e
automatizar a geração de binários


<listitem>

<literal>devscripts - Scripts para deixar a vida de um maintainer de
pacotes Debian mais fácil


<listitem>

<literal>dh-make - Ferramenta para criação de pacotes para o
debhelper


<listitem>

<literal>dpkg-cross - Ferramentas para cross compiling de pacotes
Debian


<listitem>

<literal>dupload - Utilitário para o envio de pacotes Debian


<listitem>

<literal>lintian - Verificador de pacotes Debian


<listitem>

<literal>reportbug - Permite relatar bugs na distribuição Debian


<listitem>

<literal>theme-converters - Converte temas do
WindowMaker/GTK+/Sawmill para arquivos .deb





 aplic-l-diag">###Status do Sistema/Diagnóstico/Benchmarch
<itemizedlist>
<listitem>

<literal>bonnie - Medidor de Performance do sistema de arquivos


<listitem>

<literal>bonnie++ - Programa de teste do desempenho do disco rígido


<listitem>

<literal>gmemusage -Mostra um gráfico detalhando a utilização de
memória por cada processo


<listitem>

<literal>grmonitor - Monitor Gráfico de Processos


<listitem>

<literal>linuxinfo - Mostra informações extendidas do sistema


<listitem>

<literal>loadmeter - Meditor de carga atrativo para X11


<listitem>

<literal>procmeter3 - Monitor de status do sistema baseado em X


<listitem>

<literal>qps - Monitor de processos baseado em Qt


<listitem>

<literal>wmcpu - Mostra o status da CPU/ Swap/Memória e o tempo de
execução do sistema (D)


<listitem>

<literal>wmfire - Mostra a carga da CPU como chamas (D)


<listitem>

<literal>wmloadavg - Mede a média de carga do sistema (D)


<listitem>

<literal>wmmon - Monitora carga da CPU e carga média do sistema


<listitem>

<literal>wmmount - Utilitário de montagem e ferramenta de monitoração
do espaço livre, estilo NeXTStep


<listitem>

<literal>wmsysmon - Monitora a memória, carga da CPU, swap, tempo de
execução do sistema, I/O dos discos, e interrupções de hardware (D)


<listitem>

<literal>xengine - Ferramenta de Benchmarking


<listitem>

<literal>xmcpustate - Mostra carga da CPU/Swap/Memória/Rede


<listitem>

<literal>xmem - Monitor de memória para o X


<listitem>

<literal>xosview - Monitor do sistema baseado em X


<listitem>

<literal>xsysinfo - Mostra alguns dos parâmetros do kernel de forma
gráfica


<listitem>

<literal>zcav - Testa a taxa de leitura de um disco rígido em
diferentes trilhas





 aplic-l-criptografia">###Criptografia
<itemizedlist>
<listitem>

<literal>fsh - Execução rápida de comandos sob rsh/ssl/lsh


<listitem>

<literal>gnupg - Programa de criptografia Open PGP (compatível com
PGP 5.0)


<listitem>

<literal>gpgp - Interface gráfica para o gpg


<listitem>

<literal>gs-pdfencrypt - Oferece suporte para visualizar arquivos PDF
criptografados


<listitem>

<literal>lynx-ssl - Lynx com suporte a SSL (https)


<listitem>

<literal>nessusd - Daemon do nessus


<listitem>

<literal>nessus-plugins - Plugins do nessus


<listitem>

<literal>nessus - Segurança em rede


<listitem>

<literal>openssl - Secure Sockets Layer


<listitem>

<literal>ssh - Secure Shell


<listitem>

<literal>sshwrap - Encriptação simples de serviço TCP usando TLS/SSL


<listitem>

<literal>telnetd-ssl - Daemon do Telnet com suporte a SSL


<listitem>

<literal>telnet-ssl - Telnet com suporte a SSL


<listitem>

<literal>tkpgp -Um script em Tcl/Tk script que serve como um shell
gráfico para o PGP e GnuPG


<listitem>

<literal>xpdf-i - Visualizador PDF para o X com suporta a decriptação







