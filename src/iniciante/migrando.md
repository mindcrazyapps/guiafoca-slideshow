<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" d-l">###Para quem esta migrando (ou pensando em migrar) do DOS/Windows para o Linux

Este capítulo explica as diferenças e particularidades do sistema
<command>GNU/Linux comparado ao <command>Windows,
<command>DOS e uma lista de equivalência entre comandos e programas
executados no <command>CMD do
<command>Windows/<command>DOS e
<command>GNU/Linux, que pode servir de comparação para que o usuário
possa conhecer e utilizar os comandos/programas <command>GNU/Linux
que tem a mesma função no ambiente <command>DOS/Windows.



 d-l-compar">###Quais as diferenças iniciais
<itemizedlist>
<listitem>

Quando entrar pela primeira vez no <command>GNU/Linux (ou qualquer
outro <command>UNIX, a primeira coisa que verá será a palavra
<literal>login: escrita na tela.


A sua aventura começa aqui, você deve ser uma pessoa cadastrada no sistema (ter
uma conta) para que poder entrar.  No <literal>login você digita seu
nome (por exemplo, gleydson) e pressiona Enter.  Agora será lhe pedida a senha,
repare que a senha não é mostrada enquanto é digitada, isto serve de segurança
e para enganar pessoas que estão próximas de você "tocando" algumas teclas a
mais enquanto digita a senha e fazendo-as pensar que você usa uma grande senha
;-) (com os asteriscos aparecendo isto não seria possível).


Caso cometa erros durante a digitação da senha, basta pressionar a tecla
<literal>Back Space para apagar o último caracter digitado e terminar
a entrada da senha.


Pressione Enter, se tudo ocorrer bem você estará dentro do sistema e será
presenteado com o símbolo # (caso tenha entrado como usuário
<literal>root) ou $ (caso tenha entrado como um usuário normal).


Existe um mecanismo de segurança que te alerta sobre eventuais tentativas de
entrada no sistema por intrusos usando seu <literal>login, faça um
teste: entre com seu login e digite a senha errada, na segunda vez entre com a
senha correta no sistema.  Na penúltima linha das mensagens aparece uma
mensagem "1 failure since last login", o que quer dizer "1 falha desde o último
login".  Isto significa que alguém tentou entrar 1 vez com seu nome e senha no
sistema, sem sucesso.


<listitem>

A conta <literal>root não tem restrições de acesso ao sistema e pode
fazer tudo o que quiser, é equivalente ao usuário normal do
<command>DOS e <command>Windows.  Use a conta
<literal>root somente para manutenções no sistema e instalação de
programas, qualquer movimento errado pode comprometer todo o sistema.  Para
detalhes veja <xref linkend="perm-root"/>.


<listitem>

No <command>GNU/Linux os diretório são identificados por uma
<filename>/</filename> e não por uma <filename>\</filename> como acontece no
<command>DOS.  Para entrar no diretório <filename>/bin</filename>,
você deve usar <literal>cd /bin.


<listitem>

Os comandos são <literal>case-sensitive, o que significa que ele
diferencia as letras maiúsculas de minúsculas em arquivos e diretórios.  O
comando <literal>ls e <literal>LS são completamente
diferentes.


<listitem>

A multitarefa lhe permite usar vários programas simultaneamente (não pense que
multitarefa somente funciona em ambientes gráficos, pois isto é errado!).  Para
detalhes veja <xref linkend="run"/>.


<listitem>

Os dispositivos também são identificados e uma forma diferente que no
<command>DOS por exemplo:

<screen>
 DOS/Windows        Linux
-------------  --------------- 
A:             /dev/fd0
B:             /dev/fd1
C:             /dev/hda1 ou /dev/sda1
LPT1           /dev/lp0
LPT2           /dev/lp1
LPT3           /dev/lp2
COM1           /dev/ttyS0
COM2           /dev/ttyS1
COM3           /dev/ttyS2
COM4           /dev/ttyS3


<listitem>

Os recursos multiusuário lhe permitem acessar o sistema de qualquer lugar sem
instalar nenhum driver, ou programa gigante, apenas através de conexões TCP/IP,
como a Internet.  Também é possível acessar o sistema localmente com vários
usuários (cada um executando tarefas completamente independente dos outros)
através dos Terminais Virtuais.  Faça um teste: pressione ao mesmo tempo a
tecla <literal>ALT e <literal>F2 e você será levado para o
segundo Terminal Virtual, pressione novamente <literal>ALT e
<literal>F1 para retornar ao anterior.


<listitem>

Para reiniciar o computador, você pode pressionar CTRL+ALT+DEL (como usuário
<literal>root) ou digitar <literal>shutdown -r now.  Veja
<!-- [ %INICIANTE [ --> <xref linkend="introducao-reiniciando"para detalhes. <!-- ]]> -->


<listitem>

Para desligar o computador, digite <literal>shutdown -h now e espere
o aparecimento da mensagem <literal>Power Down para apertar o botão
LIGA/DESLIGA do computador.  
<!-- [ %INICIANTE [ --> Veja <xref linkend="introducao-desligando"para detalhes. <!-- ]]> -->






 d-l-comandos">###Comandos equivalentes entre DOS/CMD do Windows e o Linux

Esta seção contém os comandos equivalentes entre estes dois sistemas e a
avaliação entre ambos.  Grande parte dos comandos podem ser usados da mesma
forma que no <command>DOS, mas os comandos <command>Linux
possuem avanços para utilização neste ambiente multiusuário/multitarefa.


O objetivo desta seção é permitir as pessoas com experiência em
<command>DOS fazer rapidamente no <command>GNU/Linux as
tarefas que fazem no <command>DOS.  A primeira coluna tem o nome do
comando no <command>DOS, a segunda o comando que possui a mesma
função no <command>GNU/Linux e na terceira coluna as diferenças.

<screen>
  DOS       Linux                        Diferenças
--------  ------------ --------------------------------------------------
cls       clear        Sem diferenças.
dir       ls -la       A listagem no Linux possui mais campos (as 
                       permissões de acesso) e o total de espaço ocupado 
                       no diretório e livre no disco deve ser visto 
                       separadamente usando o comando du e df.
                       Permite também listar o conteúdo de diversos 
                       diretórios com um só comando (ls /bin /sbin /...).
dir/s     ls -lR       Sem diferenças.
dir/od    ls -tr       Sem diferenças.
cd        cd           Poucas diferenças. cd sem parâmetros retorna ao 
                       diretório de usuário e também permite o uso 
                       de "cd -" para retornar ao diretório anteriormente 
                       acessado.
del       rm           Poucas diferenças. O rm do Linux permite 
                       especificar diversos arquivos que serão apagados 
                       (rm arquivo1 arquivo2 arquivo3). Para ser mostrados 
                       os arquivos apagados, deve-se especificar o 
                       parâmetro "-v" ao comando, e "-i" para pedir 
                       a confirmação ao apagar arquivos. 
md        mkdir        Uma só diferença: No Linux permite que vários 
                       diretórios sejam criados de uma só vez 
                       (mkdir /tmp/a /tmp/b...). 
copy      cp           Poucas diferenças. Para ser mostrados os arquivos 
                       enquanto estão sendo copiados, deve-se usar a 
                       opção "-v", e para que ele pergunte se deseja 
                       substituir um arquivo já existente, deve-se usar 
                       a opção "-i".
echo      echo         Sem diferenças.
path      path         No Linux deve ser usado ":" para separar os 
                       diretórios e usar o comando 
                       "export PATH=caminho1:/caminho2:/caminho3:"
                       para definir a variável de ambiente PATH.
                       O path atual pode ser visualizado através 
                       do comando "echo $PATH".
ren       mv           Poucas diferenças. No Linux não é possível 
                       renomear vários arquivos de uma só vez 
                       (como "ren *.txt *.bak"). É necessário usar 
                       um shell script para fazer isto. 
type      cat          Sem diferenças. 
ver       uname -a     Poucas diferenças (o uname tem algumas opções 
                       a mais).
date      date         No Linux mostra/modifica a Data e Hora do sistema.
time      date         No Linux mostra/modifica a Data e Hora do sistema.
attrib    chmod        O chmod possui mais opções por tratar as permissões 
                       de acesso de leitura, gravação e execução para 
                       donos, grupos e outros usuários. 
chkdsk    fsck         O fack é mais rápido e a checagem mais abrangente.
scandisk  fsck         O fsck é mais rápido e a checagem mais abrangente.
doskey    -----        A memorização de comandos é feita automaticamente pelo 
                       bash.
edit      vi, ae,      O edit é mais fácil de usar, mas usuário
        emacs, mcedit experientes apreciarão os recursos do vi ou 
                       o emacs (programado em lisp).
fdisk    fdisk, cfdisk Os particionadores do Linux trabalham com 
                       praticamente todos os tipos de partições de 
                       diversos sistemas de arquivos diferentes.
format    mkfs.ext3    Poucas diferenças, precisa apenas que seja 
                       especificado o dispositivo a ser formatado 
                       como "/dev/fd0" ou "/dev/hda10" (o 
                       tipo de identificação usada no Linux), ao 
                       invés de "A:" ou "C:". 
help      man, info    Sem diferenças.
interlnk  plip         O plip do Linux permite que sejam montadas 
                       redes reais a partir de uma conexão via Cabo 
                       Paralelo ou Serial. A máquina pode fazer tudo 
                       o que poderia fazer conectada em uma rede 
                       (na realidade é uma rede e usa o TCP/IP como 
                       protocolo) inclusive navegar na Internet, enviar 
                       e-mails, irc, etc. 
intersvr  plip         Mesmo que o acima.
keyb      loadkeys     Sem diferenças (somente que a posição das 
                       teclas do teclado pode ser editada. 
                       Desnecessário para a maioria dos usuários).
label     e2label      É necessário especificar a partição que terá 
                       o nome modificado.
mem       cat /proc/meminfo Mostra detalhes sobre a quantidade de dados 
          top          em buffers, cache e memória virtual (disco). 
more      more, less   O more é equivalente a ambos os sistemas, mas 
                       o less permite que sejam usadas as setas para 
                       cima e para baixo, o que torna a leitura do 
                       texto muito mais agradável. 
move      mv           Poucas diferenças. Para ser mostrados os arquivos 
                       enquanto estão sendo movidos, deve-se usar a 
                       opção "-v", e para que ele pergunte se deseja 
                       substituir um arquivo já existente deve-se usar 
                       a opção "-i". 
scan      clamav       Os principais fabricantes disponibilizam anti-virus
                       para Linux, na maioria das vezes para integrar a 
                       servidores de arquivos, e-mails, protegendo estações
                       Windows. Infecções por vírus são raras no Linux devido 
                       as restrições do usuário durante execução de 
                       programas (quando corretamente utilizadas). 
backup    tar          O tar permite o uso de compactação (através do 
                       parâmetro -z) e tem um melhor esquema de 
                       recuperação de arquivos corrompidos que já 
                       segue evoluindo há 30 anos em sistemas UNIX. 
print     lpr          O lpr é mais rápido e permite até mesmo 
                       impressões de gráficos ou arquivos compactados 
                       diretamente caso seja usado o programa 
                       magicfilter. É o programa de Spool de 
                       impressoras usados no sistema Linux/Unix. 
vol       e2label      Sem diferenças.
xcopy     cp -R        Pouca diferença, requer que seja usado a 
                       opção "-v" para mostrar os arquivos que 
                       estão sendo copiados e "-i" para pedir 
                       confirmação de substituição de arquivos.



 s4.2.1">###Arquivos de configuração

Os arquivos <filename>config.sys</filename> e <filename>autoexec.bat</filename>
são equivalentes aos arquivos do diretório <filename>/etc</filename>
especialmente o <filename>/etc/inittab</filename> e arquivos dentro do
diretório <!-- [ %DEBIAN [ --> /etc/init.d <!-- ]]> --> .






 d-l-mtools">###Usando a sintaxe de comandos DOS no Linux

Você pode usar os comandos do pacote <systemitem role="package">mtools</systemitem> para simular os comandos usados pelo
<command>DOS no <command>GNU/Linux, a diferença básica é
que eles terão a letra <literal>m no inicio do nome.  Os seguintes
comandos são suportados:

<itemizedlist>
<listitem>

<literal>mattrib - Ajusta modifica atributos de arquivos


<listitem>

<literal>mcat - Mostra os dados da unidade de disquete em formato RAW


<listitem>

<literal>mcd - Entra em diretórios


<listitem>

<literal>mcopy - Copia arquivos/diretórios


<listitem>

<literal>mdel - Exclui arquivos


<listitem>

<literal>mdeltree - Exclui arquivos, diretórios e sub-diretórios


<listitem>

<literal>mdir - Lista arquivos e diretórios


<listitem>

<literal>mdu - Mostra o espaço ocupado pelo diretório do DOS


<listitem>

<literal>mformat - Formatador de discos


<listitem>

<literal>minfo - Mostra detalhes sobre a unidade de disquetes


<listitem>

<literal>mlabel - Cria um volume para unidades DOS


<listitem>

<literal>mmd - Cria diretórios


<listitem>

<literal>mmount - Monta discos DOS


<listitem>

<literal>mmove - Move ou renomeia arquivos/subdiretórios


<listitem>

<literal>mpartition - Particiona um disco para ser usado no DOS


<listitem>

<literal>mrd - Remove um diretório


<listitem>

<literal>mren - Renomeia arquivos


<listitem>

<literal>mtype - Visualiza o conteúdo de arquivos (equivalente ao
cat)


<listitem>

<literal>mtoolstest - Exibe a configuração atual do
<command>mtools


<listitem>

<literal>mshowfat - Mostra a FAT da unidade


<listitem>

<literal>mbadblocks - Procura por setores defeituosos na unidade


<listitem>

<literal>mzip - Altera modo de proteção e ejeta discos em unidades
Jaz/ZIP


<listitem>

<literal>mkmanifest - Cria um shell script para restaurar nomes
extensos usados no UNIX


<listitem>

<literal>mcheck - Verifica arquivos na unidade





 d-l-programas">###Programas equivalentes entre Windows/DOS e o Linux

Esta seção contém programas equivalentes para quem está vindo do
<command>DOS e <command>Windows e não sabe o que usar no
<command>GNU/Linux.  Esta seção também tem por objetivo permitir ao
usuário que ainda não usa <command>GNU/Linux decidir se a passagem
vale a pena vendo se o sistema tem os programas que precisa.


Note que esta listagem mostra os programas equivalentes entre o
<command>DOS/Windows e o <command>GNU/Linux cabendo a você
a decisão final de migrar ou não.  Lembrando que é possível usar o
<command>Windows, <command>OS/2, <command>DOS,
<command>OS/2 e <command>GNU/Linux no mesmo disco rígido
sem qualquer tipo de conflito.  A listagem abaixo pode estar incompleta, se
encontrar algum programa que não esteja listado aqui, por favor entre em
contato pelo E-Mail <email>gleydson@guiafoca.org para inclui-lo na
listagem.

<screen>
DOS/Windows           Linux                         Diferenças
-----------           ----------         -------------------------------
MS Word               Open Office,       O Open Office possui todos os 
                                         recursos do Word além de ter 
                                         a interface gráfica igual, menus 
                                         e teclas de atalho idênticas ao 
                                         Word, o que facilita a migração. 
                                         Também trabalha com arquivos 
                                         no formato Word97/2000 e não 
                                         é vulnerável a vírus de macro.
                                         É distribuído gratuitamente e 
                                         não requer pagamento de licença 
                                         podendo ser instalado em quantos 
                                         computadores você quiser (tanto 
                                         domésticos como de empresas).
MS Excel              Open Office        Mesmos pontos do acima e também 
                                         abre arquivos Excel97/2000. 
MS PowerPoint         Open Office        Mesmos pontos do acima. 
MS Access             MySQL, PostgreSQL  Existem diversas ferramentas de 
                      Oracle             conceito para bancos de dados 
                                         corporativos no Linux. Todos 
                                         produtos compatíveis com outras 
                                         plataformas. 
MS Outlook            Pine, evolution    Centenas de programas de E-Mail
                      mutt, sylpheed,    tanto em modo texto como em 
                      icedove            modo gráfico. Instale, avalie 
                                         e escolha. 
MS Internet Explorer  Firefox, Opera,    Os três primeiros para modo 
                      Mozilla, lynx.     gráfico e o lynx opera em 
                                         modo texto.
ICQ                   LICQ, PIDGIM, SIM  Muito prático e fácil de 
                                         operar. Possibilita a mudança 
                                         completa da aparência do programa 
                                         através de Skins. A organização 
                                         dos menus deste programa é outro 
                                         ponto de destaque. 
MSN                   AMSN, PIDGIM       Permite conversar diretamente com 
                                         usuários do Microsoft MSN.
Photo Shop            The Gimp           Fácil de usar, possui 
                                         muitos scripts que permitem 
                                         a criação rápida e fácil de 
                                         qualquer tipo de efeito 
                                         profissional pelo usuário 
                                         mais leigo. Acompanha centenas
                                         de efeitos especiais e um 
                                         belo manual em html com muitas 
                                         fotos (aproximadamente 20MB) que 
                                         mostra o que é possível se fazer 
                                         com ele. 
Corel Photo Paint     GIMP               Corel Photo-Paint para 
Corel Draw            Inkscape, Sodipodi Programas equivalentes
Autocad               Qcad               Programa com funções genéricas
Visio                 dia                Possui funcionalidades identicas
                                         e ótimo conjunto de ícones
winamp                xmms               Possui todos os recursos do 
                                         programa para Windows além 
                                         de filtros que permite acrescentar 
                                         efeitos digitais da música (em 
                                         tempo real), eco, etc. 
media player          mplayer,playmidi   Programas para execução de 
                      xwave,             arquivos de música e videos 
                                         multimídia. Existem outras 
                                         alternativas, a escolha 
                                         depende de seu gosto e da 
                                         sofisticação do programa.
Agente de Sistema     cron               Pouca diferença. O cron
                                         da mais liberdade na programação 
                                         de tarefas a serem executadas 
                                         pelo Linux. 
Mixer                 aumix, cam         Sem diferenças. 
Bate-Papo             talk, ytalk        O talk e o ytalk permite a 
                                         conversa de dois usuários não 
                                         só através de uma rede local, 
                                         mas de qualquer parte do 
                                         planeta, pois usa o protocolo 
                                         tcp/ip para comunicação. Muito 
                                         útil e fácil de usar. 
MIRC                  Bitchx, xchat      Clientes IRC para Linux
IIS, Pers. Web Server Apache             O apache é o servidor WEB mais 
                                         usado no mundo (algo em torno 
                                         de 75% das empresas), muito 
                                         rápido e flexível de se 
                                         configurar. 
Exchange, NT Mail     Postfix, Sendmail  72% da base de servidores de 
                      Exim, Qmail        emails no mundo atualmente roda
                                         em software livre. Os mais recomendados
					                               são o Postfix e o qmail, devido a 
					                               segurança, velocidade e integridade
					                               de mensagem
Wingate, MS Proxy     Squid, Apache,     A migração de um servidor proxy
                      ip masquerade,     para Linux requer o uso de 
                      nat, diald,        vários programas separados para 
                      exim,              que se tenha um resultado 
                                         profissional. Isto pode parecer 
                                         incomodo no começo, mas você logo
                                         perceberá que a divisão de serviços 
                                         entre programas é mais produtivo. 
                                         Quando desejar substituir um 
                                         deles, o funcionamento dos 
                                         outros não serão afetados. 
                                         Não vou entrar em detalhes sobre os 
                                         programas citados ao lado, mas o squid 
                                         é um servidor proxy Web (HTTP e 
                                         HTTPS) completo e também apresenta um 
                                         excelente serviço FTP. 
                                         Possui outros módulos como dns, ping, 
                                         restrições de acesso, limites de 
                                         tamanho de arquivos, cache, etc. 
MS Frontpage          Mozilla            Sem comentários... todas são 
                      e muitas outras    ferramentas para a geração 
                      ferramentas para   de grandes Web Sites. O wdm, 
                      geração de conteúdo por exemplo, é usado na geração
                      WEB (como zope,    do site da distribuição Debian 
                      php3, php4, wdm,   (http://www.debian.org) em 30
                      htdig)             idiomas diferentes. 
MS Winsock            Sem equivalente    O Linux tem suporte nativo a 
                                         tcp/ip desde o começo de sua 
                                         existência e não precisa de 
                                         nenhuma camada de comunicação 
                                         entre ele e a Internet. A 
                                         performance é aproximadamente 
                                         10% maior em conexões Internet
                                         via fax-modem e outras redes tcp/ip. 
AVG, Viruscan,        Clamavis, AVG      Os maiores fabricantes de anti-virus
norton, F-PROT, CPAV. F-Prot, ViruScan   disponibilizam versões para Linux, 
                                         que podem ser instaladas em servidores
                                         de E-Mail, servidores de arquivos, 
                                         aumentando o nível de proteção dos 
                                         usuários.



