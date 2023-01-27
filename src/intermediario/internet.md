<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" inter">###Conectando seu computador a Internet

Este capítulo descreve como configurar seu sistema para se conectar a Internet,
navegar, enviar/receber mensagens, etc.


 inter-conectando">###Conectando-se a Internet

 inter-conectando-adsl">###Conectando através de ADSL

A conexão através de banda larga em sistemas <command>Debian é
realizada através do programa <command>pppoeconf ou modificando
manualmente os arquivos de configuração em <filename>/etc/ppp</filename>.  Esta
seção explicará como configurar a conexão em modo bridge e assume que você já
tem o modem conectado e sua placa de rede configurada.  Para criar uma conexão
internet através do <command>pppoeconf entre como usuário root no
sistema, digite <literal>pppoeconf e siga os passos de configuração:

<orderedlist numeration="arabic">
<listitem>

Na primeira tela, ele perguntará se deseja que o modem seja detectado
automaticamente.  Selecione sim.  O sistema procurará e detectará o modem no
sistema (assegure-se que ele esteja ligado durante essa etapa).


<listitem>

Ao detectar o modem siga adiante e informe o nome de usuário para conexão


<listitem>

Em seguida informe a senha usada para autenticação


<listitem>

Nas próximas telas, selecione o valor padrão para MTU e MSS (a não ser que seu
provedor DSL solicite a alteração).


<listitem>

Na tela sobre se a conexão deve ser iniciada na inicialização do sistema,
selecione "Sim".


</orderedlist>


 inter-conectando-ppp">###Conectando através de Internet Discada

Para conectar usando internet discada é utilizada a placa de Fax-Modem.  A
conexão através de sistemas <command>Debian é fácil, e todo o
trabalho de configuração pode ser feito através do programa
<command>pppconfig ou modificando manualmente os arquivos em
<filename>/etc/ppp</filename>.  Para criar uma conexão internet através do
<command>pppconfig, entre como usuário root no sistema, digite
<literal>pppconfig e siga os passos de configuração (esta
configuração serve para usuários domésticos e assume que você possui o kernel
com suporte a PPP):

<orderedlist numeration="arabic">
<listitem>

No primeiro menu, escolha a opção <literal>Create para criar uma nova
conexão.  As outras opções disponíveis são <literal>Change para
modificar uma conexão a Internet criada anteriormente,
<literal>Delete para apagar uma conexão.  A opção
<literal>Quit sai do programa.


<listitem>

Agora o sistema perguntará qual será o nome da conexão que será criada.  O nome
<literal>provider é o padrão, e será usado caso digite
<literal>pon para iniciar uma conexão internet sem nenhum argumento.


<listitem>

O próximo passo é especificar como os servidores de nomes serão acessados.
Escolha <literal>Static se não tiver nenhum tipo de rede local ou
<literal>None para usar os servidores especificados no arquivo
<filename>/etc/resolv.conf</filename>.


Aperte a tecla <literal>TAB e tecle <literal>ENTER para
seguir para o próximo passo.


<listitem>

Agora digite o endereço do servidor DNS especificado pelo seu provedor de
acesso.  Um servidor DNS converte os nomes como
<literal>www.blablabla.com.br para o endereço IP correspondente para
que seu computador possa fazer conexão.


Tecle <literal>ENTER para seguir para o próximo passo.


<listitem>

Você pode digitar um endereço de um segundo computador que será usado na
resolução de nomes DNS.  Siga as instruções anteriores caso tiver um segundo
servidor de nomes ou <literal>ENTER para continuar.


<listitem>

Agora você precisará especificar qual é o método de autenticação usado pelo seu
provedor de acesso.  O **Password Autentication Protocol** é
usado pela maioria dos provedores de acesso.  Desta forma escolha a opção
<literal>PAP


<listitem>

Agora entre com o seu login no provedor de acesso, ou seja, o nome para acesso
ao sistema que escolheu no momento que fez sua assinatura.


<listitem>

Agora especifique a sua senha.


<listitem>

O próximo passo será especificar a taxa de transmissão da porta serial do
micro.  O valor de 115200 deve funcionar com todas as configurações mais
recentes.


Uma configuração serial DTE detalhada pode ser feita com a ferramenta
<command>setserial.


<listitem>

Agora será necessário selecionar o modo de discagem usado pelo seu fax-modem.
Escolha <literal>tone para linha digital e <literal>pulse
se possuir uma linha telefônica analógica.


Pressione <literal>TAB e tecle <literal>ENTER para
prosseguir.


<listitem>

Agora digite o número do telefone para fazer conexão com o seu provedor de
acesso.


<listitem>

O próximo passo será a identificação do seu fax-modem, escolha
<literal>YES para que seja utilizada a auto-detecção ou
<literal>NO para especificar a localização do seu fax-modem
manualmente.


<listitem>

Se você quiser especificar mais detalhes sobre sua configuração, como strings
de discagem, tempo de desconexão, auto-discagem, etc., faça isto através do
menu <literal>Advanced.


Escolha a opção <literal>Finished para salvar a sua configuração e
retornar ao menu principal.  Escolha a opção <literal>Quit para sair
do programa.


</orderedlist>

Pronto!  todos os passos para você se conectar a Internet estão concluídos,
basta digitar <literal>pon para se conectar e <literal>poff
para se desconectar da Internet.  Caso tenha criado uma conexão com o nome
diferente de <literal>provider você terá que especifica-la no comando
<command>pon (por exemplo, <literal>pon provedor2).


A conexão pode ser monitorada através do comando <command>plog e os
pacotes enviados/recebidos através do <command>pppconfig.


Para uma navegação mais segura, é recomendável que leia e compreenda alguns
ítens que podem aumentar consideravelmente a segurança do seu sistema em <xref linkend="rede-seg"/>, <xref linkend="rede-seg-tcpd-a"/>, <xref linkend="rede-seg-tcpd-d"/>.  A seção <xref linkend="rede-dns-a-resolv"pode
ser também útil.





 inter-navegando">###Navegando na Internet

Existem diversos tipos de navegadores web para <command>GNU/Linux e a
escolha depende dos recursos que pretende utilizar (e do poder de processamento
de seu computador).


Para navegar na Internet com muitos recursos, você pode usar o navegador
<command>Firefox, ele suporta plug-ins, extensões adicionais, java,
flash, etc.  Você também tem a escolha do <command>Mozilla que
inspirou a criação do <command>Netscape e outros navegadores
derivados.


O <command>dillo é uma boa alternativa para aqueles que desejam um
navegador em modo gráfico, mas eles não tem suporte a Java e Frames.


Os usuários e administradores de servidores que operam em modo texto e precisam
de navegadores para testes, podem optar pelo <command>Lynx ou o
<command>links.  
Uma listagem mais detalhada e recursos requeridos por cada navegador podem ser 
encontrados em <xref linkend="aplic-b-internet"/>. 




 inter-emails-r">###Recebimento de E-Mails através do <command>fetchmail

É o programa mais tradicional no recebimento de mensagens através dos serviços
**pop3**, **imap**,
**pop2**, etc.  no <command>GNU/Linux.  Ele pega as
mensagens de seu servidor **pop3** e as entrega ao MDA local
ou nos arquivos de e-mails dos usuários do sistema em
<filename>/var/mail</filename>


Todo o funcionamento do <command>fetchmail é controlado pelo arquivo
<filename>~/.fetchmailrc</filename>.  Segue abaixo um modelo padrão deste
arquivo:

<screen>
 poll pop3.seuprovedor.com.br protocol pop3
   user gleydson password sua_senha keep fetchall is gleydson here


Este arquivo é lido pelo <command>fetchmail na ordem que foi escrito.
Veja a explicação abaixo sobre o arquivo exemplo:

<itemizedlist>
<listitem>

A palavra <literal>poll especifica o servidor de onde suas mensagens
serão baixadas, o servidor especificado no exemplo é
<literal>pop3.seuprovedor.com.bt.  A palavra <literal>skip
pode ser especificada, mas as mensagens no servidor especificado por
<literal>skip somente serão baixadas caso o nome do servidor de
mensagens for especificado através da linha de comando do
<command>fetchmail.


<listitem>

<literal>protocol é o protocolo que será usado para a transferência
de mensagens do servidor.  O <command>fetchmail utilizará a
auto-detecção de protocolo caso este não seja especificado.


<listitem>

<literal>user define o nome do usuário no servidor
pop3.seuprovedor.com.br, que no exemplo acima é <literal>gleydson.


<listitem>

<literal>password define a senha do usuário
<literal>gleydson (acima), especificada como
<literal>sua_senha no exemplo.


<listitem>

<literal>keep é opcional e serve para não apagar as mensagens do
servidor após baixa-las (útil para testes e acesso a uma única conta de e-mail
através de vários locais, como na empresa e sua casa por exemplo).


<listitem>

<literal>fetchall baixa todas as mensagens do provedor marcadas como
lidas e não lidas.


<listitem>

<literal>is gleydson here é um modo de especificar que as mensagens
obtidas de <literal>pop3.seuprovedor.com.br do usuário
<literal>gleydson com a senha <literal>sua_senha serão
entregues para o usuário local <literal>gleydson no diretório
<filename>/var/mail/gleydson</filename>.


As palavras <literal>is e <literal>here são completamente
ignoradas pelo <command>fetchmail, servem somente para dar um tom de
linguagem natural na configuração do programa e da mesma forma facilitar a
compreensão da configuração.




Se possuir várias contas no servidor
<literal>pop3.seuprovedor.com.br, não é necessário repetir toda a
configuração para cada conta, ao invés disso especifique somente os outros
usuários do mesmo servidor:

<screen>
poll pop3.seuprovedor.com.br protocol pop3
 user gleydson password sua_senha keep fetchall is gleydson here
 user conta2 password sua_senha2 fetchall is gleydson here
 user conta3 password sua_senha3 fetchall is gleydson here


Note que todos os e-mails das contas <literal>gleydson,
<literal>conta2 e <literal>conta3 do servidor de mensagens
<literal>pop3.seuprovedor.com.br são entregues ao usuário local
<literal>gleydson (arquivo <filename>/var/mail/gleydson</filename>).


Agora você pode usar um programa MUA como o <command>mutt ou
<command>pine para ler localmente as mensagens.  O armazenamento de
mensagens no diretório <filename>/var/mail</filename> é preferido pois permite
a utilização de programas de notificação de novos e-mais como o
<command>comsat, <command>mailleds,
<command>biff, etc.


Também é possível utilizar um processador de mensagens ao invés do MTA para a
entrega de mensagens.  O programa <command>procmail é um exemplo de
processador de mensagens rápido e funcional que pode separar as mensagens em
arquivos de acordo com sua origem, destino, assunto, enviar respostas
automáticas, listas de discussão, envio de arquivos através de requisição, etc.
Veja <xref linkend="inter-procmail"para detalhes.


Para mais detalhes sobre outras opções específicas de outros protocolos,
checagem de mensagens, criptografia, etc, veja a página de manual do
<command>fetchmail.


 inter-procmail">###Processamento de mensagens através do procmail

O processamento de mensagens pode ser usado para inúmeras finalidades, dentre
elas a mais comum é separar uma mensagem em arquivos/diretórios de acordo com
sua origem, prioridade, assuntos, destinatário, conteúdo, etc., programar
auto-respostas, programa de férias, servidor de arquivos, listas de discussão,
etc.


O <command>procmail é um programa que reúne estas funções e permitem
muito mais, dependendo da habilidades e conhecimento das ferramentas
<command>GNU/Linux para saber integra-las corretamente.  Toda a
operação do <command>procmail é controlada pelo arquivo
<filename>/etc/procmailrc</filename> e <filename>~/.procmailrc</filename>.
Abaixo um modelo do arquivo <filename>~/.procmailrc</filename> usado para
enviar todas as mensagens contendo a palavra <literal>GNU/Linux no
assunto para o arquivo <filename>mensagens-linux</filename>:

<screen>
PATH=/usr/bin:/bin:/usr/local/bin:
MAILDIR=$HOME/Mail
DEFAULT=$MAILDIR/mbox
LOGFILE=$MAILDIR/log

:0: 
* ^Subject:.*Linux
mensagens-linux


A variável de ambiente <filename>MAILDIR</filename> especifica o diretório que
serão armazenadas as mensagens e logs das operações do
<command>procmail.  A variável <filename>DEFAULT</filename>
especifica a caixa de correio padrão onde todas as mensagens que não se
encaixam nas descrições do filtro do <filename>procmailrc</filename> serão
enviadas.  A variável <filename>LOGFILE</filename> especifica o arquivo que
registrará todas as operações realizadas durante o processamento de mensagens
do <command>procmail.


O arquivo <filename>mensagens-linux</filename> é criado dentro do diretório
especificado por <filename>MAILDIR</filename>.


Para que o <command>procmail entre em ação toda vez que as mensagens
forem baixadas via <command>fetchmail, é preciso modificar o arquivo
<filename>.fechmailrc</filename> e incluir a linha <literal>mda
/usr/bin/procmail -d %T no final do arquivo e retirar as linhas
<literal>is [usuáriolocal] here para que o processamento das
mensagens seja feita pelo MDA local (neste caso, o
<command>procmail).


Se quiser que o <command>procmail seja executado pelo MDA local,
basta criar um arquivo <filename>~/.forward</filename> no diretório do usuário
e incluir a linha <literal>exec /usr/bin/procmail (note que em
algumas implementações do <command>exim, o
<command>procmail é executado automaticamente caso um arquivo
<filename>~/.procmailrc</filename> seja encontrado, caso contrário será
necessário adicionar a linha "/usr/bin/procmail" ao arquivo
<filename>~/.forward</filename> (somente <command>exim).


Para mais detalhes, veja a página de manual do <command>procmail,
<command>procmailrc e HOWTOs relacionados com e-mails no
<command>GNU/Linux.





