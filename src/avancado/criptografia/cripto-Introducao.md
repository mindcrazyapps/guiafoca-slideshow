<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" d-cripto">###Introdução ao uso de criptografia para transmissão/armazenamento de dados

Este capítulo explica como dados transmitidos em uma rede pode ser capturados,
isto ajudará a entender a vulnerabilidade de serviços comuns que não utilizam
criptografia para a transmissão de dados e alternativas/programas equivalentes
que fazem transmissão de dados usando métodos criptográficos para deixar a
mensagem somente legível para origem e destino.

 d-cripto-intro">###Introdução

Quando enviamos um tráfego de nossa máquina para outra (e-mails, mensagens de
ICQ, navegação, ftp, etc) os dados passam por várias máquinas até atingir o seu
destino (isto se chama roteamento).  Se algum cracker instalou algum capturador
de pacotes (sniffer) em alguma das máquinas de nossa rota os dados poderão
facilmente visualizados.


Crackers normalmente configuram estes programas a procura de campos como
"passwd" e outras expressões que sejam úteis para acesso ao seu sistema ou
espionagem.  Quem gosta de ter sua privacidade violada?  A internet
definitivamente é uma rede insegura e nem todos os administradores de
servidores são responsáveis o suficiente para fazer uma configuração restrita
para evitar acesso de pessoas mal intencionadas.


Este capítulo mostra (na prática) como um sniffer funciona para captura de
pacotes, isto ajudará a entender como serviços que enviam seus dados em forma
texto plano são vulneráveis a isto e alternativas para transmissão segura de
dados.  Este capítulo tem a intenção de mostrar alternativas seguras de
proteção dos dados que trafegam em sua rede e a segurança de suas instalações.



 d-cripto-sniffer">###Sniffer

O sniffer (farejador) é um programa que monitoram/registram a passagem de dados
entre as interfaces de rede instaladas no computador.  Os dados coletados por
sniffers são usados para obtenção de detalhes úteis para solução de problemas
em rede (quando usado com boas intenções pelo administrador do sistema) ou para
ataques ao sistema (quando usado pelo cracker para obter nomes/senhas e outros
detalhes úteis para espionagem).


Os sniffers mais conhecidos para sistemas <command>Linux são
<command>tcpdump, <command>ethereal.  Este último apresenta
uma interface gráfica GTK para fácil operação em máquinas que executam o
servidor X.  Para explicar o funcionamento de um sniffer, vou assumir o
<command>ethereal instalado (ele não requer modificações no sistema
além de ser fácil de executar e fazer pesquisa de expressões específicas).
Instale o <command>ethereal com o comando <literal>apt-get install
ethereal.


Agora vamos a prática para entender como o sniffer funciona e a importância da
criptografia de dados (só assim mesmo, não da para entender falando muita
teoria :-):

<orderedlist numeration="arabic">
<listitem>

Conecte-se a Internet


<listitem>

Execute o <command>ethereal como usuário <literal>root.


<listitem>

Pressione <literal>CTRL+K para abrir a tela de captura de pacotes.
Em <literal>Interface selecione sua interface de internet.  Nesta
tela clique no botão "FILE" e coloque um nome de arquivo que a captura será
gravada.  Opcionalmente marque a opção "Update list of packets in real time"
para monitorar a passagem de pacotes em tempo real.


<listitem>

Clique em "OK".  A captura de pacotes será iniciada


<listitem>

Conecte-se a um site ftp qualquer (digamos ftp.debian.org.br).  Entre com o
usuário "anonymous" e senha "minhasenha@segura.com.br"


<listitem>

Finalize a captura de pacotes clicando no botão "STOP"


</orderedlist>

Agora vá em "File"/"Open" e abra o arquivo capturado.  Ele está no formato
usado pelo sniffer <command>tcpdump como padrão.  Procure no campo
"INFO" a linha "Request: USER anonymous", logo abaixo você verá a senha
digitada pelo usuário.  Entendeu agora a importância da criptografia na
transferência segura de dados?  não só o nome/senha pode ser capturado mas toda
a seções feitas pelo usuário.  Scanners como o <command>tcpdump e
<command>ethereal são flexivelmente configuráveis para procurar por
dados específicos nas conexões e salva-los para posterior recuperação.

 d-cripto-sniffer-detect">###Detectando a presença de sniffers

Uma característica comum de sniffers é mudar o modo de operação das interfaces
monitoradas para o "Modo Promíscuo" com o objetivo de analisar todo o tráfego
que passa por aquele segmento de rede (mesmo não sendo destinados para aquela
máquina).


A entrada/saída de interfaces no modo promíscuo é monitorada nos logs do
sistema:

<screen>
Sep 25 16:53:37 myserver kernel: device eth0 left promiscuous mode
Sep 25 16:53:56 myserver kernel: device eth0 entered promiscuous mode
Sep 25 16:54:18 myserver kernel: device eth0 left promiscuous mode
Sep 25 16:54:31 myserver kernel: device eth0 entered promiscuous mode


O <command>logcheck monitora estas atividades e classificam esta
mensagem como prioridade "Violação" (dependendo da configuração dos seus
filtros em <filename>/etc/logcheck</filename>.  Veja <xref linkend="log-uteis-logcheck"para detalhes sobre este programa.


**OBS:** A utilização de
<literal>switches dificulta a captura de pacotes em redes
distribuídas porque somente os dados destinados a máquina onde o sniffer está
instalado poderão ser capturados.





 d-cripto-alt">###Alternativas seguras a serviços sem criptografia
 d-cripto-http">###http

O uso de alternativas seguras é indispensável em servidores que servem páginas
de comércio eletrônico, banco de dados, sistemas bancários, administração via
web ou que tenham dados que oferecem risco, se capturados.


Existem duas alternativas: instalar o servidor Apache-ssl (pacote <systemitem role="package">apache-ssl</systemitem> ou adicionar o módulo
<filename>mod-ssl</filename> na instalação padrão do <command>Apache.
Esta segunda é a preferida por ser mais rápida e simples de se administrar, por
usar o servidor Web <command>Apache padrão e sua configuração.  Veja
<xref linkend="s-apache-ssl"para detalhes de como configurar um servidor Web
para transmissão de dados criptografados.



 d-cripto-emails">###Transmissão segura de e-mails

A codificação padrão usada para o envio de mensagens em muitos clientes de
e-mail é o MIME/base64.  Isto não oferece muita segurança porque os dados podem
ser facilmente descriptografados se pegos por sniffers (veja <xref linkend="d-cripto-sniffer"/>) ou abertos por administradores não confiáveis no
diretório de spool do servidor.


Existem uma diversidade de servidores SMTP, POP, IMAP do
<command>Linux que já implementam o protocolo de autenticação
**SSL**/**TLS**, exigindo login/senha para o
envio/recepção de mensagens, cabeçalhos de autenticação (aumentando um pouco
mais a confiança sobre quem enviou a mensagem).  Em especial, a autenticação é
útil quando desejamos abrir nossas contas de e-mail para a Internet, por algum
motivo, e não queremos que outros façam relay sem nossa autorização.


Outra forma de garantir a segurança da mensagem/arquivos através do correio
eletrônico é usando o PGP (veja <xref linkend="d-cripto-gpg"/>) em conjunto com
um MUA (Mail User Agent - cliente de e-mails) que suporte o envio de mensagens
criptografadas/assinadas usando PGP.  A vantagem do GPG em cima da autenticação
SSL é que você tem garantidas da autenticidade da mensagem e você pode
verificar sua integridade.  Os dois programas mais usados em sistemas
<command>Unix são o <command>mutt e o
<command>sylpheed.  O <command>mutt é um MUA para modo
texto e o <command>sylpheed para modo gráfico.  Ambos são muito
flexíveis, permitem uma grande variedade de configurações, personalizações,
possuem agenda de endereços e gerenciam diversas contas de e-mails em um só
programa.


Para encriptar/assinar uma mensagem no <command>mutt escreva/responda
seu e-mail normalmente, quando aparecer a tela onde você tecla "y" para enviar
a mensagem, tecle "p" e selecione uma das opções para criptografar/assinar uma
mensagem.


Para fazer a mesma operação no <command>sylpheed, escreva/responda
seu e-mail normalmente e clique no menu "Mensagem" e marque "assinar",
"criptografar" ou ambos.  A chave pública deverá estar disponível para tal
operação (veja <xref linkend="d-cripto-gpg-c-a"e <xref linkend="d-cripto-gpg-c-e"/>).



 d-cripto-pop3">###Servidor pop3

A alternativa mais segura é a utilização do protocolo <command>IMAP
com suporte a ssl.  Nem todos os clientes de e-mail suportam este protocolo.



 d-cripto-ftp">###Transferência de arquivos

Ao invés do <command>ftp, use o <command>scp ou o
<command>sftp para transferência segura de arquivos.  Veja <xref linkend="s-ssh-cliente-scp"e <xref linkend="s-ssh-cliente-sftp"/>.  Uma
outra alternativa é a configuração de uma VPN entre redes para garantir não só
a transferência de arquivos, mas uma seção em cima de um tunel seguro entre
duas pontas.



 d-cripto-rlogin">###login remoto

Ao invés do uso do <command>rlogin, <command>telnet e
<command>rsh utilize o <command>ssh (veja <xref linkend="s-ssh-cliente-ssh"/>) ou o telnet com suporte a ssl (veja <xref linkend="s-telnet-install"/>).



 d-cripto-irc">###Bate papo via IRC

O programa <command>SILC (Secure Internet Live Conference) realiza a
criptografia de dados durante o bate papo entre diversos usuários conectados
via rede.



 d-cripto-icq">###Transmissão de mensagens via ICQ

O protocolo ICQ trabalha de forma plana para transmissão de suas mensagens,
inclusive as senhas.  Clientes anteriores ainda usavam o UDP (até a versão 7)
para envio de mensagens, piorando um pouco mais a situação e deixando o cliente
mais vulnerável a falsificações de pacotes.  Outro ponto fraco é que se alguma
coisa acontecer com os pacotes UDP, eles serão simplesmente descartados
perdendo a mensagem.


Ao invés do ICQ, você poderá usar algum cliente do protocolo
<command>Jabber (como o <command>gaim,
<command>gaber ou <command>gossip) ou o LICQ mais atual com
suporte a ssl compilado.  O problema do LICQ com ssh, é que as duas pontas
deverão ter este suporte compilado e funcionando.





 d-cripto-criptofs">###Sistemas de arquivos criptográfico

Esta é uma forma excelente para armazenamento seguro de seus dados, pois
estarão criptografados e serão somente acessados após fornecer uma senha que só
você conhece.  O sistema usado é a montagem de um arquivo comum como um sistema
de arquivos via loopback (veja <xref linkend="disc-ext2-criando-a"/>) você pode
escolher um nome de arquivo discreto para dificultar sua localização (use a
imaginação) e poderá ser armazenado até mesmo em partições não-ext2.  Siga
estes passos para criar seu sistema de arquivos criptografado (baseado no
<literal>Loopback-Encripted-Filesystem):

<variablelist>
<varlistentry>
<term>Suporte no kernel
<listitem>

Baixe o patch criptográfico de ("http://www.w3.org/1999/xlink) [](ftp://ftp.kernel.org/pub/linux/kernel/crypto">ftp://ftp.kernel.org/pub/linux/kernel/crypto
de acordo com a sua versão do kernel e aplique os patches.  Este suporte não
pode ser incluído nativamente no kernel devido a restrições de uso e importação
de criptografia impostas pelos EUA e outros países, com este suporte embutido o
kernel não poderia ser distribuído livremente.


Se o patch para seu kernel não existir, pegue a versão anterior mais próxima
(se não existir o patch para seu kernel <literal>2.2.19, pegue a
versão <literal>2.2.18 do patch internacional).  Isto certamente
funcionará.



<varlistentry>
<term>Opções de compilação do kernel
<listitem>

Na seção <literal>Crypto Support ative <literal>Crypto
Ciphers e ative o suporte aos ciphers <literal>Twofish,
<literal>blowfish, <literal>cast128, e
<literal>serpent (estes são distribuídos livremente e sem
restrições).  Todos possuem cifragem de 128 bits, exceto o
<literal>blowfish que é 64 bits.  Também é recomendado ativar os
módulos em <literal>Digest algorithms.


Na seção <literal>Block Devices: ative o suporte a
<literal>loopback (necessário para montar arquivos como dispositivos
de bloco) e <literal>Use relative block numbers as basis for transfer
functions (isto permite que um backup do sistema de arquivos
criptografado seja restaurado corretamente em outros blocos ao invés dos
originais).  Ative também o suporte para <literal>General encription
support e o suporte aos cyphers <literal>cast128 e
<literal>twofish.


Não ative as opções de criptografia para a seção "Networking" (a não ser que
saiba o que está fazendo).  Recompile e instale seu kernel (veja <xref linkend="kern-recompilando"/>).



<varlistentry>
<term>Crie um arquivo usando os números aleatórios de <filename>/dev/urandom</filename>:
<listitem>

<literal>dd if=/dev/urandom of=/pub/swap-fs bs=1M count=15


Será criado um arquivo chamado <filename>swap-fs</filename> (um arquivo de
troca tem características que ajudam a esconder um sistema de arquivos
criptografado que é o tamanho e não poderá ser montado pelo usuário comum,
evitando desconfianças).


O processo de criação deste arquivo é lento, em média de 1MB a cada 10 segundos
em um Pentium MMX.



<varlistentry>
<term>Monte o arquivo como um sistema de arquivos loop
<listitem>

<literal>losetup -e twofish /dev/loop0 /pub/swap-fs


O algoritmo de criptografia é selecionado pela opção **-e**.
Algoritmos recomendados são o <literal>serpent e
<literal>twofish (ambos possuem cifragem de 128 bits), sendo o
serpent o preferido.  O gerenciamento do sistema loop encriptado é feito
através do módulo <filename>loop_gen</filename>.


Quando é executado pela primeira vez, será lhe pedida uma senha que será usada
para montagens futuras de seu sistema de arquivos.  Digite-a com atenção pois
ela será lhe pedida apenas uma vez.  Para desativar o sistema de arquivos loop,
execute o comando:


<literal>losetup -d /dev/loop0


**OBS:** Se errou a senha será necessário
desmontar, apagar o arquivo criado e repetir o procedimento.



<varlistentry>
<term>Crie um sistema de arquivos ext2 para armazenamento de dados
<listitem>

<literal>mkfs -t ext2 /dev/loop0 ou <literal>mkfs.ext2
/dev/loop0



<varlistentry>
<term>Monte o sistema de arquivos
<listitem>

Crie um diretório que será usado para montagem do seu sistema de arquivos, se
preferir monta-lo dentro de seu diretório pessoal para armazenar seus arquivos,
crie um diretório com as permissões "0700".


mount /pub/swap-fs /pub/criptofs -t ext2 -o loop


Agora poderá gravar seus arquivos dentro deste diretório normalmente como
qualquer outro.  O comando <literal>df -hT listará a partição loop
como uma partição do tipo <literal>ext2 comum.



<varlistentry>
<term>Desmontando/Protegendo os dados
<listitem>

Após usar o sistema de arquivos criptográfico, desmonte-o e desative o
dispositivo loopback:

<screen>
umount /pub/criptofs
losetup -d /dev/loop0



<varlistentry>
<term>Remontando o sistema de arquivos criptografado
<listitem>

Execute novamente os comandos:

<screen>
losetup -e twofish /dev/loop0 /pub/swap-fs
mount /pub/swap-fs /pub/criptofs -t ext2 -o loop


Será pedida a senha que escolheu e seu sistema de arquivos será montado em
<filename>/pub/swap-fs</filename>.



</variablelist>

Com este sistema, seus dados estarão protegidos mesmo do usuário
<literal>root.



 d-cripto-gpg">###Usando pgp (<command>gpg)para criptografia de arquivos

O <command>gpg (GNU pgp, versão livre da ferramenta pgp) permite
encriptar dados, assim somente o destinatário terá acesso aos dados,
adicionalmente poderá verificar se a origem dos dados é confiável (através da
assinatura de arquivos).  O sistema PGP se baseia no conceito de chave
**pública** e **privada**: Sua chave
**pública** é distribuída para as pessoas que deseja trocar
dados/mensagens e a chave **privada** fica em sua máquina (ela
não pode ser distribuída).  As chaves públicas e privadas são armazenadas nos
arquivos <filename>pubring.gpg</filename> e <filename>secring.gpg</filename>
respectivamente, dentro do subdiretório <filename>~/.gnupg</filename>.  Veja
<xref linkend="d-cripto-gpg-criando"para criar este par de chaves.


Os dados que recebe de outra pessoa são criptografados usando sua chave pública
e somente você (de posse da chave privada) poderá desencriptar os dados.
Quando assina um arquivo usando o pgp, ele faz isto usando sua chave privada, o
destinatário de posse da chave pública poderá então confirmar que a origem dos
dados é confiável.


O <command>gpg vem largamente sendo usado para transmissão segura de
dados via internet.  Muitos programas de e-mails como o <command>mutt
e <command>sylpheed incluem o suporte a pgp embutido para envio de
mensagens assinadas/encriptadas (MIME não tem uma codificação segura e não
garante que a mensagem vem de quem realmente diz ser).  Um servidor de e-mail
no <command>Linux configurado como as mesmas configurações/endereços
do provedor da vítima pode enganar com sucesso um usuário passando-se por
outro.

 d-cripto-gpg-pacote">###Instalando o PGP

apt-get install gnupg


Após instalar o <systemitem role="package">gnupg</systemitem>, execute o
comando <command>gpg para criar o diretório
<filename>~/.gnupg</filename> que armazenará as chaves pública e privada.



 d-cripto-gpg-criando">###Criando um par de chaves pública/privada

Para gerar um par de chaves pessoais use o comando <literal>gpg
--gen-key.  Ele executará os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

<literal>Chave criptográfica - Selecione **DSA e
ELGamal** a não ser que tenha necessidades específicas.


<listitem>

<literal>Tamanho da chave - 1024 bits traz uma boa combinação de
proteção/velocidade.


<listitem>

<literal>Validade da chave - 0 a chave não expira.  Um número
positivo tem o valor de dias, que pode ser seguido das letras
<literal>w (semanas), <literal>m (meses) ou
<literal>y (anos).  Por exemplo, "7m", "2y", "60".


Após a validade, a chave será considerada inválida.


<listitem>

<literal>Nome de usuário - Nome para identificar a chave


<listitem>

<literal>E-mail - E-mail do dono da chave


<listitem>

<literal>comentário - Uma descrição sobre a chave do usuário.


<listitem>

<literal>Confirmação - Tecle "O" para confirmar os dados ou uma das
outras letras para modificar os dados de sua chave.


<listitem>

<literal>Digite a FraseSenha - Senha que irá identificá-lo(a) como
proprietário da chave privada.  É chamada de FraseSenha pois pode conter
espaços e não há limite de caracteres.  Para alterá-la posteriormente, siga as
instruções em <xref linkend="d-cripto-gpg-chpasswd"/>.


<listitem>

<literal>Confirme e aguarde a geração da chave pública/privada.


</orderedlist>


 d-cripto-gpg-e">###Encriptando dados

Use o comando <literal>gpg -e arquivo faz a encriptação de dados:

<screen>
gpg -e arquivo.txt


Será pedida a identificação de usuário, digite o nome que usou para criar a
chave.  O arquivo criado será encriptado usando a chave pública do usuário
(<filename>~/.gnupg/pubring.gpg</filename>) e terá a extensão
<filename>.gpg</filename> adicionada (<filename>arquivo.txt.gpg</filename>).
Além de criptografado, este arquivo é compactado (recomendável para grande
quantidade de textos).  A opção **-a** é usada para criar um
arquivo criptografado com saída ASCII 7 bits:

<screen>
gpg -e -a arquivo.txt


O arquivo gerado terá a extensão <filename>.asc</filename> acrescentada
(<filename>arquivo.txt.asc</filename>) e não será compactado.  A opção
**-a** é muito usada para o envio de e-mails.


Para criptografar o arquivo para ser enviado a outro usuário, você deverá ter a
chave pública do usuário cadastrado no seu chaveiro (veja <xref linkend="d-cripto-gpg-c-a"/>) e especificar a opção **-r**
seguida do nome/e-mail/ID da chave pública:

<screen>
gpg -r kov -e arquivo.txt


O exemplo acima utiliza a chave pública de kov para encriptar o arquivo
<filename>arquivo.txt</filename> (somente ele poderá decriptar a mensagem
usando sua chave privada).


**OBS:** É recomendável especificar o nome de
arquivo sempre como último argumento.



 d-cripto-gpg-d">###Decriptando dados com o gpg

Agora vamos fazer a operação reversa da acima, a opção **-d**
é usada para decriptar os dados usando a chave privada:

<screen>
gpg -d arquivo.txt.asc &gt;arquivo.txt
gpg -d arquivo.txt.gpg &gt;arquivo.txt


Descriptografa os arquivos <filename>arquivo.txt.asc</filename> e
<filename>arquivo.txt.gpg</filename> recuperando seu conteúdo original.  A sua
"FraseSenha" será pedida para descriptografar os dados usando a chave privada
(<filename>~/.gnupg/secring.gpg</filename>).



 d-cripto-gpg-a">###Assinando arquivos

Assinar um arquivo é garantir que você é a pessoa que realmente enviou aquele
arquivo.  Use a opção **-s** para assinar arquivos usando sua
chave privada:

<screen>
gpg -s arquivo.txt


A "FraseSenha" será pedida para assinar os dados usando sua chave privada.
Será gerado um arquivo <filename>arquivo.txt.gpg</filename> (assinado e
compactado).  Adicionalmente a opção **--clearsign** poderá
ser usada para fazer uma assinatura em um texto plano, este é um recurso muito
usado por programas de e-mails com suporte ao gpg:

<screen>
gpg -s --clearsign arquivo.txt


Será criado um arquivo chamado <filename>arquivo.txt.asc</filename> contendo o
arquivo assinado e sem compactação.



 d-cripto-gpg-a-c">###Checando assinaturas

A checagem de assinatura consiste em verificar que quem nos enviou o arquivo é
realmente quem diz ser e se os dados foram de alguma forma alterados.  Você
deverá ter a chave pública do usuário no seu chaveiro para fazer esta checagem
(veja <xref linkend="d-cripto-gpg-c-a"/>).  Para verificar os dados assinados
acima usamos a opção **--verify**:

<screen>
gpg --verify arquivo.txt.asc


Se a saída for "Assinatura Correta", significa que a origem do arquivo é segura
e que ele não foi de qualquer forma modificado.

<screen>
gpg --verify arquivo.txt.gpg


Se a saída for "Assinatura INCORRETA" significa que ou o usuário que enviou o
arquivo não confere ou o arquivo enviado foi de alguma forma modificado.



 d-cripto-gpg-c-e">###Extraindo sua chave pública do chaveiro

Sua chave pública deve ser distribuída a outros usuários para que possam enviar
dados criptografados ou checar a autenticidade de seus arquivos.  Para exportar
sua chave pública em um arquivo que será distribuído a outras pessoas ou
servidores de chaves na Internet, use a opção **--export**:

<screen>
gpg --export -a usuario &gt;chave-pub.txt


Ao invés do nome do usuário, poderá ser usado seu e-mail, ID da chave, etc.  A
opção **-a** permite que os dados sejam gerados usando bits
ASCII 7.



 d-cripto-gpg-c-a">###Adicionando chaves públicas ao seu chaveiro pessoal

Isto é necessário para o envio de dados criptografados e checagem de assinatura
do usuário, use a opção **--import**:

<screen>
gpg --import chave-pub-usuario.txt


Assumindo que o arquivo <filename>chave-pub-usuario.txt</filename> contém a
chave pública do usuário criada em <xref linkend="d-cripto-gpg-c-e"/>.  O
<command>gpg detecta chaves públicas dentro de textos e faz a
extração corretamente.  Minha chave pública pode ser encontrada em <xref linkend="apend-pgp"ou ("http://www.w3.org/1999/xlink) [](http://pgp.ai.mit.edu">http://pgp.ai.mit.edu.



 d-cripto-gpg-c-l">###Listando chaves de seu chaveiro

Use o comando <literal>gpg --list-keys para listar as chaves pública
do seu chaveiro.  O comando <literal>gpg --list-secret-keys lista
suas chaves privadas.



 d-cripto-gpg-c-d">###Apagando chaves de seu chaveiro

Quando uma chave pública é modificada ou por qualquer outro motivo deseja
retira-la do seu chaveiro público, utilize a opção
**--delete-key**:

<screen>
gpg --delete-key usuario


Pode ser especificado o nome de usuário, e-mail IDchave ou qualquer outro
detalhe que confira com a chave pública do usuário.  Será pedida a confirmação
para excluir a chave pública.


**OBS:** A chave privada pode ser excluída com a
opção **--delete-secret-key**.  Utilize-a com o máximo de
atenção para excluir chaves secretas que não utiliza (caso use mais de uma), a
exclusão acidental de sua chave secreta significa é como perder a chave de um
cofre de banco: você não poderá descriptografar os arquivos enviados a você e
não poderá enviar arquivos assinados.


Mesmo assim se isto acontecer acidentalmente, você poderá recuperar o último
backup da chave privada em <filename>~/.gnupg/secring.gpg~</filename>.



 d-cripto-gpg-chpasswd">###Mudando sua FraseSenha

Execute o comando <literal>gpg --edit-key usuário, quando o programa
entrar em modo de comandos, digite <literal>passwd.  Será lhe pedida
a "Frase Senha" atual e a nova "Frase Senha".  Digite "save" para sair e salvar
as alterações ou "quit" para sair e abandonar o que foi feito.


O <literal>gpg --edit-key permite gerenciar diversos aspectos de suas
chaves é interessante explora-lo digitando "?"  para exibir todas as opções
disponíveis.



 d-cripto-gpg-sign">###Assinando uma chave digital

A assinatura de chaves é um meio de criar laços de confiança entre usuários
PGP.  Assinar uma chave de alguém é algo sério, você deve ter noção do que isto
significa e das conseqüências que isto pode trazer antes de sair assinando
chaves de qualquer um.


O próprio teste para desenvolvedor da distribuição <command>Debian
requer como primeiro passo a identificação do candidato, caso sua chave pgp
seja assinada por algum desenvolvedor desta distribuição, imediatamente o teste
de identificação é completado.  A partir disso você deve ter uma noção básica
do que isto significa.  Para assinar uma chave siga os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

Importe a chave pública do usuário (veja <xref linkend="d-cripto-gpg-c-a"/>).


<listitem>

Execute o comando <literal>gpg --edit-key usuario (onde
**usuario** é o nome do usuário/e-mail/IDchave da chave
pública importada).


<listitem>

Digite <literal>list, e selecione a chave pública (pub) do usuário
com o comando <literal>uid [numero_chave].  Para assinar todas as
chaves públicas do usuário, não selecione qualquer chave com o comando
<literal>uid.


<listitem>

Para assinar a chave pública do usuário digite <literal>sign, será
perguntado se deseja realmente assinar a chave do usuário e então pedida a
"FraseSenha" de sua chave privada.


<listitem>

Digite "list", repare que existe um campo chamado <literal>trust: n/q
no lado direito.  O primeiro parâmetro do "trust" indica o valor de confiança
do dono e o segundo (após a <literal>/) o valor de confiança
calculado automaticamente na chave.  As seguintes possuem o seguinte
significado:

<itemizedlist>
<listitem>

<literal>- - Nenhum dono encontrado/confiança não calculada.


<listitem>

<literal>e - Chave expirada/falha na checagem de confiança.


<listitem>

<literal>q - Quando não conhece o usuário.


<listitem>

<literal>n - Quando não confia no usuário (é o padrão).


<listitem>

<literal>m - Pouca confiança no usuário.


<listitem>

<literal>f - Totalmente confiável.


<listitem>

<literal>u - Indiscutivelmente confiável.  Somente usado para
especificar a chave pública do próprio usuário.




O valor de confiança da chave pode ser modificado com o comando
<literal>trust e selecionando uma das opções de confiança.  Os
valores de confiança para a chave pública pessoal é <literal>-/u (não
é necessário calcular a confiança/indiscutivelmente confiável).


</orderedlist>


 d-cripto-gpg-c-sign-l">###Listando assinaturas digitais

Execute o comando <literal>gpg --list-sigs para listas todas as
assinaturas existentes no seu chaveiro.  Opcionalmente pode ser especificado um
parâmetro para fazer referência a assinatura de um usuário:<literal>gpg
--list-sigs usuario.


O comando <literal>gpg --check-sigs adicionalmente faz a checagem de
assinaturas.



 d-cripto-gpg-c-sign-guia">###Recomendações para a assinatura de chaves gpg

Este texto foi divulgado por uma pessoa que pediu para permanecer anônima na
lista <email>debian-user-portuguese@lists.debian.org explicando os
procedimentos de segurança para a troca de chaves públicas individuais e em
grupo de usuários.  Ele é um pouco longo mas a pessoa é especializada no
assunto, e seu foco é a segurança na troca de chaves e o que isto significa.
Após consulta ao autor do texto, o texto foi reproduzido na íntegra, mantendo
os padrões de formatação da mensagem.

<screen>
Trocando assinaturas de chaves digitais

Direitos de republicação cedidos ao domínio público, contanto que o texto
seja reproduzido em sua íntegra, sem modificações de quaisquer espécie, e
incluindo o título e nome do autor.


1. Assinaturas digitais
2. Chaves digitais e a teia de confiança
3. Trocando assinaturas de chaves digitais com um grupo de pessoas


1. Assinaturas digitais

Uma assinatura digital é um número de tamanho razoável (costuma ter de 128 a
160 bits) que representa um bloco bem maior de informação, como um e-mail.

Pense numa assinatura como se ela fosse uma versão super-comprimida de um
texto.  Se você muda alguma coisa (por menor que seja) no texto que uma
assinatura "assina", essa assinatura se torna inválida: ela não mais
representa aquele texto.

Existe uma relação direta entre uma assinatura e informação que ela assina.
Se uma das duas for modificada, elas passam a não mais "combinar" uma com a
a outra. Um programa de computador pode detectar isso, e avisar que a
assinatura é "inválida".

Os algoritmos mais usados para criar e verificar assinaturas digitais são o
SHA-1, RIPEM160 e MD5.  O MD5 não é considerado tão bom quanto os outros
dois.

Assinaturas digitais também funcionam com arquivos "binários", ou seja:
imagens, som, planilhas de cálculo... e chaves digitais.


2. Chaves digitais e a teia de confiança

Chaves digitais são fáceis de falsificar, você só precisa criar uma chave
nova no nome de sicrano, por um endereço de e-mail novinho em folha daqueles
que você consegue nesses webmail da vida, e pronto.  Agora é só espalhar
essa chave por aí que os bestas vão usá-la pensando que é de sicrano.

A menos que os "bestas" não sejam tão bestas assim, tenham lido o manual do
seu software de criptografia, e saibam usar assinaturas e a teia de
confiança para verificar se a tal chave é de sicrano mesmo.

Programas de criptografia (os bons, tipo PGP e GNUpg) usam um sistema de
assinaturas nas chaves digitais para detectar e impedir esse tipo de
problema:  Ao usuário é dado o poder de "assinar" uma chave digital, dizendo
"sim, eu tenho certeza que essa chave é de fulano, e que o e-mail de fulano é
esse que está na chave".

Note bem as palavras "certeza", e "e-mail".  Ao assinar uma chave digital,
você está empenhando sua palavra de honra que o _nome_ do dono de verdade
daquela chave é o nome _que está na chave_, e que o endereço de e-mail
daquela chave é da pessoa (o "nome") que também está na chave.

Se todo mundo fizer isso direitinho (ou seja, não sair assinando a chave de
qualquer um, só porque a outra pessoa pediu por e-mail, ou numa sala de
chat), cria-se a chamada teia de confiança.

Numa teia de confiança, você confia na palavra de honra dos outros para
tentar verificar se uma chave digital é legítima, ou se é uma "pega-bobo".

Suponha que Marcelo tenha assinado a chave de Cláudia, e que Roberto, que
conhece Marcelo pessoalmente e assinou a chave de Marcelo, queira falar com
Cláudia.  

Roberto sabe que Marcelo leu o manual do programa de criptografia, e que ele
não é irresponsável.  Assim, ele pode confiar na palavra de honra de Marcelo
que aquela chave digital da Cláudia é da Cláudia mesmo, e usar a chave pra
combinar um encontro com Cláudia.

Por outro lado, Roberto não conhece Cláudia (ainda), e não sabe que tipo de
pessoa ela é. Assim, rapaz prevenido, ele não confia que Cláudia seja uma
pessoa responsável que verifica direitinho antes de assinar chaves.

Note que Roberto só confiou na assinatura de Marcelo porque, como ele já
tinha assinado a chave de Marcelo, ele sabe que foi Marcelo mesmo quem
assinou a chave de Cláudia.  

Enrolado? Sim, é um pouco complicado, mas desenhe num papel as flechinhas de
quem confia em quem, que você entende rapidinho como funciona.

O uso da assinatura feita por alguém cuja chave você assinou, para validar
a chave digital de um terceiro, é um exemplo de uma pequena teia de
confiança.


3. Trocando assinaturas de chaves digitais com um grupo de pessoas

Lembre-se: ao assinar uma chave digital, você está empenhando sua palavra de
honra que toda a informação que você assinou naquela chave é verdadeira até
onde você pode verificar, _e_ que você tentou verificar direitinho.

Pense nisso como um juramento: "Eu juro, em nome da minha reputação
profissional e pessoal, que o nome e endereços de e-mail nessa chave são
realmente verdadeiros até onde posso verificar, e que fiz uma tentativa real
e razoável de verificar essa informação."

Sim, é sério desse jeito mesmo. Você pode ficar muito "queimado" em certos
círculos se você assinar uma chave falsa, pensando que é verdadeira:  a sua
assinatura mal-verificada pode vir a prejudicar outros que confiaram em
você.

Bom, já que o assunto é sério, como juntar um grupo de pessoas numa sala, e
trocar assinaturas de chaves entre si?  Particularmente se são pessoas que
você nunca viu antes? Siga o protocolo abaixo, passo a passo, e sem pular ou
violar nenhum dos passos.


  1 -  Reúna todos em uma sala, ou outro local não tumultuado, pressa e
       bagunça são inimigas da segurança.
  
  2 -  Cada um dos presentes deve, então, ir de um em um e:
  
       2.1 -  Apresentar-se, mostrando _calmamente_ documentação original
              (nada de fotocópia) comprovando sua identidade.  RG, CPF,
              passaporte, certidão de nascimento ou casamento, carteira de
              motorista, cartão de crédito são todos bons exemplos. Só o RG
              sozinho não é -- tem muito RG falsificado por aí -- mas o RG
              junto com o cartão de banco já seria suficiente.  Se nenhum
              documento tiver foto, também não é o bastante.
              
              * Se alguém pedir o documento na mão, para verificar
              direitinho, não leve pro lado pessoal. Deixe a pessoa
              verificar até estar satisfeita (mas não descuide do
              documento). Isso só significa que ela leva muito a sério a
              responsabilidade de assinar chaves.

       2.2 -  Entregar um papel com as informações da chave: Nome
              (QUE OBRIGATORIAMENTE PRECISA SER O MESMO NOME CONSTANTE NOS
              DOCUMENTOS APRESENTADOS EM 2.1), e-mail, número da chave
              (keyID), e fingerprint da chave (assinatura digital da chave)

              RECIPIENTE DO PAPEL: Se você achar que os documentos que te
              apresentaram não são prova suficiente, talvez porque o nome
              não bate com o da chave, ou porque uma foto nos documentos não
              está parecida com quem mostrou os documentos, marque
              discretamente no papel, porque você NÃO deve assinar essa
              chave.   Se achar que o outro vai engrossar, não diga para ele
              que não vai assinar a chave dele.

  3 -  Pronto. Podem ir embora, porque o resto dos passos deve ser feito com
       calma, em casa.  Lembre-se que você não vai estar efetuando nenhum
       julgamento moral a respeito de quem você assinar a chave. Você só irá
       afirmar que a chave de sicrano é realmente aquela, e mais nada.

  4 -  Para cada uma das chaves que você marcou no papel que "posso assinar":
  
       4.1 -  Peça para o seu programa de criptografia mostrar a chave e sua
              assinatura (fingerprint).
              
              SE: O nome no papel for exatamente igual ao nome na chave
              (user ID/UID da chave). E: A assinatura no papel for
              exatamente igual à assinatura na chave (fingerprint).  ENTÃO:
              Vá para o passo 4.3.

       4.2 -  As informações não bateram, por isso você não deve assinar a
              chave.  Se quiser, envie um e-mail avisando que não poderá
              assinar a chave. Não aceite tentativas de retificação por
              e-mail ou telefone. Um outro encontro face-à-face, refazendo
              todos os passos 2.1 e 2.2 é o único jeito de retificar
              o problema.

       4.3 -  As informações bateram, o que garante que o *nome* está
              correto. Agora é preciso ter certeza do endereço de e-mail.
              Para isso, envie uma e-mail *CIFRADA* pela chave que você está
              testando, para o endereço de e-mail constante na chave.  Nessa
              e-mail, coloque uma palavra secreta qualquer e peça para o
              destinatário te responder dizendo qual a palavra secreta que
              você escreveu. Use uma palavra diferente para cada chave que
              estiver testando, e anote no papel daquela chave qual palavra
              você usou.

       4.4 -  Se você receber a resposta contendo a palavra secreta correta,
              você pode assinar a chave. Caso contrário, não assine a chave -- 
              o endereço de e-mail pode ser falso.


Comandos do gpg (GNUpg) correspondentes a cada passo:
  2.2 -       gpg --fingerprint &lt;seu nome ou 0xSuaKEYID&gt;
              (retorna as informações que devem estar no papel a ser
              entregue no passo 2.2)

  4.1 -       gpg --receive-key &lt;0xKEYID&gt;
              (procura a chave especificada nos keyservers)
              gpg --sign-key &lt;0xKEYID&gt;
              (assina uma chave)

              Assume-se que você sabe cifrar e decifrar mensagens. Caso
              não saiba, ainda não é hora de querer sair assinando chaves.





