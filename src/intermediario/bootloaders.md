<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" boot">###Gerenciadores de Partida (boot loaders)

**Gerenciadores de Partida** são programas que carregam um
sistema operacional e/ou permitem escolher qual será iniciado.  Normalmente
este programas são gravados no **setor de boot**
(inicialização) da partição ativa ou no **master boot record**
(MBR) do disco rígido.


Este capitulo explica o funcionamento de cada um dos principais gerenciadores
de partida usados no <command>GNU/Linux, em que situações é
recomendado seu uso, as características, como configura-lo e alguns exemplos de
configuração.

 boot-lilo">###LILO

O <command>LILO (**Linux Loader**) é sem dúvida o
gerenciador de partida padrão para quem deseja iniciar o
<command>GNU/Linux através do disco rígido.  Ele permite selecionar
qual sistema operacional será iniciado (caso você possua mais de um) e funciona
tanto em discos rígidos **IDE** como
**SCSI**.


A seleção de qual sistema operacional e a passagem de parâmetros ao kernel pode
ser feita automaticamente ou usando o aviso de <literal>boot: do
<command>LILO.

 boot-lilo-cfg">###Criando o arquivo de configuração do LILO

Os dados para a criação do novo **setor de boot** que
armazenará o gerenciador de partida são lidos do arquivo
<filename>/etc/lilo.conf</filename> Este arquivo pode ser criado em qualquer
editor de textos (como o <command>ae ou <command>vi).
Normalmente ele é criado durante a instalação de sua distribuição
<command>GNU/Linux mas por algum motivo pode ser preciso modifica-lo
ou personaliza-lo (para incluir novos sistemas operacionais, mensagens, alterar
o tempo de espera para a partida automática, etc).


O arquivo <filename>/etc/lilo.conf</filename> é dividido em duas seções:
**Geral** e **Imagens**.  A seção
**Geral** vem no inicio do arquivo e contém opções que serão
usadas na inicialização do <command>Lilo e parâmetros que serão
passados ao kernel.  A seção **Imagens** contém opções
especificas identificando qual a partição que contém o sistema operacional,
como será montado inicialmente o sistema de arquivos, tabela de partição, o
arquivo que será carregado na memória para inicializar o sistema, etc.  Abaixo
um modelo do arquivo <filename>/etc/lilo.conf</filename> para sistemas que só
possuem o <command>GNU/Linux instalado:

<screen>
boot=/dev/hda1
compact
install=text
map=/boot/map
vga=normal
delay=20
lba32

image=/vmlinuz
    root=/dev/hda1
    label=Linux
    read-only


Para criar um novo gerenciador de partida através do arquivo
<filename>/etc/lilo.conf</filename> , execute o comando
<literal>lilo.


No exemplo acima, o gerenciador de partida será instalado em
<filename>/dev/hda1</filename> (veja <xref linkend="disc-id"/>) , utilizará um
setor de boot compacto (compact), modo de vídeo VGA normal (80x25), esperará 2
segundos antes de processar automaticamente a primeira seção
<literal>image= e carregará o kernel <filename>/vmlinux</filename> de
<filename>/dev/hda1</filename>.  Para detalhes sobre opções que podem ser
usadas neste arquivo veja <xref linkend="boot-lilo-opcoes"/>.


Para mostrar o aviso de <literal>boot:, você deverá ligar as teclas
Caps Lock ou Scrool lock na partida ou pressionar a tecla
<literal>Shift durante os dois segundos de pausa.  Outro método é
incluir a opção <literal>prompt na seção **global**
para que o aviso de <literal>boot: seja mostrado automaticamente após
carregar o <command>Lilo.


Abaixo uma configuração para computadores com mais de um sistema operacional
(Usando <command>GNU/Linux e <command>DOS):

<screen>
boot=/dev/hda1
compact
lba32
install=menu
map=/boot/map
vga=normal
delay=20
prompt

image=/vmlinuz
    root=/dev/hda1
    label=linux
    read-only

other=/dev/hda2
 table=/dev/hda
 label=dos


O exemplo acima é idêntico ao anterior, o que foi acrescentado foi a opção
<literal>prompt na seção **geral** (para que seja
mostrado imediatamente o aviso de <literal>boot: no momento em que o
<command>LILO for carregado), e incluída uma imagem de disco
<command>DOS localizado em <filename>/dev/hda2</filename>.  No
momento da inicialização é mostrada a mensagem <literal>boot: e caso
seja digitado <literal>DOS e pressionado ENTER, o sistema iniciará o
<command>DOS.  Caso a tecla Enter seja pressionada sem especificar a
imagem, a primeira será carregada (neste caso o <command>GNU/Linux).


Você pode substituir a palavra <literal>GNU/Linux da opção
<literal>label por o número <literal>1 e
<literal>DOS por <literal>2, desta forma o número pode ser
digitado para iniciar o sistema operacional.  Isto é muito útil para construir
um menu usando a opção <literal>message.  Para detalhes veja <xref linkend="boot-lilo-opcoes"/>.


A seção **Geral** vem do inicio do arquivo até a palavra
<literal>delay=20.  A partir do primeiro aparecimento da palavra
<literal>image, <literal>other ou <literal>range,
tudo o que vier abaixo será interpretado como imagens de inicialização.


Por padrão, a imagem carregada é a especificada por <literal>default=
ou a primeira que aparece no arquivo (caso <literal>default= não seja
especificado).  Para carregar o outro sistema (o <command>DOS),
digite o nome da imagem de disco no aviso de <literal>boot:
(especificada em <literal>label=) que será carregada.  Você também
pode passar parâmetros manualmente ao kernel digitando o nome da imagem de
disco e uma opção do kernel ou através do arquivo
<filename>/etc/lilo.conf</filename> (veja <xref linkend="boot-lilo-opcoes"/>).


O <command>LILO pode inicializar o seguintes tipos de imagens:

<itemizedlist>
<listitem>

Imagens do kernel de um arquivo.  Normalmente usado para iniciar o
<command>GNU/Linux pelo disco rígido e especificado pelo parâmetro
<literal>image=.


<listitem>

Imagens do kernel de um dispositivo de bloco (como um disquete).  Neste caso o
número de setores a serem lidos devem ser especificados na forma
**PRIMEIRO-ÚLTIMO** ou **PRIMEIRO+NÚMERO de setores a
serem lidos**.


É necessário especificar o parâmetro <literal>image= e
<literal>range=, por exemplo:

<screen>
image=/dev/fd0
   range=1+512


Todas as opções do kernel podem ser usadas na inicialização por dispositivo.


<listitem>

O setor de boot de outro sistema operacional (como o <command>DOS,
<command>OS/2, etc).  O setor de partida é armazenado junto com a
tabela de partição no arquivo <filename>/boot/map</filename>.  É necessário
especificar o parâmetro <literal>OTHER=dispositivo ou
<literal>OTHER=arquivo e a inicialização através de um setor de
partida possui algumas opções especiais como o <literal>TABLE= (para
especificar a tabela de partição) e o <literal>MAP-DRIVE=
(identificação da unidade de discos pelo sistema operacional).  Veja o exemplo
desta configuração abaixo:

<screen>
other=/dev/hda2
  table=/dev/hda
  label=DOS
  map-drive=0x80
   to = 0x81
  map-drive=0x81
   to = 0x80




Observações:

<itemizedlist>
<listitem>

Caso o gerenciador de partida seja instalado no MBR do disco rígido
(boot=/dev/hda), o setor de boot do antigo sistema operacional será
substituído, retire uma cópia do setor de boot para um disquete usando o
comando <literal>dd if=/dev/hda of=/floppy/mbr bs=512 count=1 no
<command>GNU/Linux para salvar o setor de boot em um disquete e
<literal>dd if=/floppy/mbr of=/dev/hda bs=446 count=1 para
restaura-lo.  No <command>DOS você pode usar o comando <command>fdisk
/mbr para criar um novo Master Boot Record.


<listitem>

Após qualquer modificação no arquivo <filename>/etc/lilo.conf</filename> , o
comando <literal>lilo deverá ser novamente executado para atualizar o
setor de partida do disco rígido.  Isto também é válido caso o kernel seja
atualizado ou a partição que contém a imagem do kernel desfragmentada.


<listitem>

A limitação de 1024 cilindros do <command>Lilo não existe mais a
partir da versão 21.4.3 (recomendada, por conter muitas correções) e
superiores.


<listitem>

A reinstalação, formatação de sistemas <command>DOS e
<command>Windows pode substituir o setor de partida do HD e assim o
gerenciador de partida, tornando impossível a inicialização do
<command>GNU/Linux.  Antes de reinstalar o <command>DOS ou
<command>Windows, verifique se possui um disquete de partida do
<command>GNU/Linux.


Para gerar um novo boot loader, coloque o disquete na unidade e após o aviso
<literal>boot: ser mostrado, digite <literal>linux
root=/dev/hda1 (no lugar de <filename>/dev/hda1</filename> você
coloca a partição raiz do <command>GNU/Linux), o sistema iniciará.
Dentro do <command>GNU/Linux, digite o comando
<command>lilo para gerar um novo setor de partida.


Agora reinicie o computador, tudo voltará ao normal.





 boot-lilo-opcoes">###Opções usadas no LILO

Esta seção traz opções úteis usadas no arquivo <filename>lilo.conf</filename>
com explicações sobre o que cada uma faz.  As opções estão divididas em duas
partes: As usadas na seção **Global** e as da seção
**Imagens** do arquivo <filename>lilo.conf</filename>.


<literal>Global

<itemizedlist>
<listitem>

<literal>backup=[arquivo/dispositivo] - Copia o setor de partida
original para o arquivo ou dispositivo especificado.


<listitem>

<literal>boot=dispositivo - Define o nome do dispositivo onde será
gravado o setor de partida do <command>LILO (normalmente é usada a
partição ativa ou o Master Boot Record - MBR).  Caso não seja especificado, o
dispositivo montado como a partição raiz será usado.


<listitem>

<literal>compact - Tenta agrupar requisições de leitura para setores
seguintes ao sendo lido.  Isto reduz o tempo de inicialização e deixa o mapa
menor.  É normalmente recomendado em disquetes.


<listitem>

<literal>default=imagem - Usa a imagem especificada como padrão ao
invés da primeira encontrada no arquivo <filename>lilo.conf</filename>.


<listitem>

<literal>delay=[num] - Permite ajustar o número de segundos (em
décimos de segundos) que o gerenciador de partida deve aguardar para carregar a
primeira imagem de disco (ou a especificada por <literal>default=).
Esta pausa lhe permite selecionar que sistema operacional será carregado.


<listitem>

<literal>install=interface - Especifica que interface será usada para
exibição de menu com as opções de inicialização ao usuário.  As seguintes
opções são permitidas:

<itemizedlist>
<listitem>

<literal>text - Exibe uma mensagem de texto (exibida através do
parâmetro **message=**) na tela.  Esta é a recomendada para
terminais.


<listitem>

<literal>menu - Exibe um menu que lhe permite selecionar através de
uma interface de menu a opção de inicialização.  Esta é a padrão.


<listitem>

<literal>bmp - Exibe um bitmap gráfico com a resolução de 640x480 com
16 ou 256 cores.




<listitem>

<literal>lba32 - Permite que o <command>LILO quebre o
limite de 1024 cilindros do disco rígido, inicializando o
<command>GNU/Linux em um cilindro acima deste através do acesso .
Note que isto requer compatibilidade com o BIOS, mais especificamente que tenha
suporte a chamadas int 0x13 e AH=0x42.  É recomendado o seu uso.


<listitem>

<literal>map=arquivo-mapa - Especifica a localização do arquivo de
mapa (<filename>.map</filename>).  Se não for especificado,
<filename>/boot/map</filename> é usado.


<listitem>

<literal>message=arquivo - Especifica um arquivo que contém uma
mensagem que será mostrada antes do aviso de <literal>boot:.  Nenhuma
mensagem é mostrada até que seja pressionada a tecla <literal>Shift
após mostrar a palavra <literal>LILO.  O tamanho da mensagem deve ser
no máximo 65535 bytes.  O arquivo de mapa deve ser novamente criado caso a
mensagem seja retirada ou modificada.  Na mensagem, o caracter
<literal>FF (CTRL+L) limpa a tela.


<listitem>

<literal>nowarn - Não mostra mensagens de alerta.


<listitem>

<literal>password=senha - Permite proteger todas as imagens de disco
com uma única senha.  Caso a senha esteja incorreta, o LILO é novamente
carregado.


<listitem>

<literal>prompt - Mostra imediatamente o aviso de
<literal>boot: ao invés de mostrar somente quando a tecla
<literal>Shift é pressionada.


<listitem>

<literal>verbose=[num] - Ativa mensagens sobre o processamento do
<command>LILO.  Os números podem ser especificados de 1 a 5, quanto
maior o número, maior a quantidade de detalhes mostrados.


<listitem>

<literal>timeout=[num] - Ajusta o tempo máximo de espera (em décimos
de segundos) de digitação no teclado.  Se nenhuma tecla é pressionada no tempo
especificado, a primeira imagem é automaticamente carregada.  Igualmente a
digitação de senha é interrompida se o usuário estiver inativo por este
período.




Adicionalmente as opções de imagem do kernel <literal>append, ramdisk,
read-only, read-write, root e vga podem ser especificadas na seção
**global**.  <literal>Opções por Imagem


As opções por imagem iniciam com uma das seguintes opções:
<literal>image=, <literal>other= ou
<literal>range=.  Opções usadas por cada imagem:

<itemizedlist>
<listitem>

<literal>table=dispositivo - Indica o dispositivo que contém a tabela
de partição para aquele dispositivo.  Necessário apenas para imagens
especificadas por <literal>other=.


<listitem>

<literal>unsafe - Não acessa o setor de boot no momento da criação do
mapa.  Isto desativa algumas checagens, como a checagem da tabela de partição.
<literal>unsafe e <literal>table= são incompatíveis.


<listitem>

<literal>label=[nome] - Permite especificar um nome para a imagem.
Este nome será usado na linha <literal>boot: para inicializar o
sistema.


<listitem>

<literal>alias=[nome] - Apelido para a imagem de disco.  É como um
segundo <literal>label.


<listitem>

<literal>optional - Ignora a imagem caso não estiver disponível no
momento da criação do mapa.  É útil para especificar kernels que não estão
sempre presentes no sistema.


<listitem>

<literal>password=senha - Protege a imagem atual com a senha.  Caso a
senha esteja incorreta, o setor de partida do <command>Lilo é
novamente carregado.


<listitem>

<literal>restricted - A senha somente é pedida para iniciar a imagem
se o sistema for iniciado no modo single.




Também podem ser usados parâmetros de inicialização do kernel no arquivo
<filename>/etc/lilo.conf</filename>, veja a seção <xref linkend="boot-kernelparam"para maiores detalhes.



 boot-lilo-exemplo">###Um exemplo do arquivo de configuração lilo.conf

Abaixo um exemplo do arquivo <filename>/etc/lilo.conf</filename> que poderá ser
usado em instalações <command>GNU/Linux com o <command>DOS.

<screen>
boot=/dev/hda1        #Instala o LILO em /dev/hda1
compact               
install=menu
map=/boot/map
message=/etc/lilo.message  #mensagem que será mostrada na tela
default=1          #Carrega a Imagem especificada por label=1 como padrão
vga=normal         #usa o modo de video 80x25 ao iniciar o Linux
delay=20           #aguarda 2 segundos antes de iniciar a imagem padrão 
lba32              #permite quebrar o limite de 1024 cilindros na inicialização
prompt             #mostra o aviso de "boot:" logo que o LILO é carregado

image=/vmlinuz     #especifica o arquivo que contém a primeira imagem
  root=/dev/hda1   #partição onde a imagem acima esta localizada
  label=1          #identificação da imagem de disco
  read-only        #monta inicialmente como somente leitura
  password=12345   #Usa a senha 12345
  restricted       #somente quando iniciar com o parâmetro single

other=/dev/hda2    #especifica outro sistema que será carregado
 table=/dev/hda    #a tabela de partição dele está em /dev/hda
 label=2           #identificação desta imagem de disco
 password=12345    #pede a senha antes de iniciar este sistema


Você pode usar o exemplo acima como base para construir sua própria
configuração personalizada do <filename>/etc/lilo.conf</filename> mas não se
esqueça de modificar as tabelas de partições para seu sistema.  Se você usa o
<command>Windows NT 4.0, <command>Windows NT 5.0 (Windows
2000) ou o <command>OS/2, recomendo ler o
<literal>DOS+Windows+OS/2-HOWTO.


Após criar seu arquivo <filename>/etc/lilo.conf</filename> , execute o comando
<literal>lilo e se tudo ocorrer bem, o <command>LILO será
instalado.





 boot-grub">###GRUB

(Os detalhes contidos na seção sobre o <command>GRUB, foram
integralmente desenvolvidos por Alexandre Costa
<email>alebyte@bol.com.br como contribuição ao guia FOCA GNU/Linux.)


O <command>GRUB (**Grand Unified Boot Loader**) é
mais uma alternativa como gerenciador de boot e apresenta alguns recursos
extras com relação as outras opções disponíveis.  Ele é flexível, funcional e
poderoso, podendo inicializar sistemas operacionais como o
<command>Windows (9x, ME, NT, 2000 e XP), <command>Dos,
<command>Linux, <command>GNU Hurd, <command>*BSD,
<command>OS/2 e etc.  Podemos destacar também o suporte aos sistemas
de arquivos ext2 (Linux), ext3 e reiserfs (novos sistemas de arquivos
journaling do Linux), FAT16 e FAT32 (Win 9x/ME), FFS (Fast File System usado no
*BSD), minix (MINIX OS) e etc.


Por utilizar o padrão Multiboot ele é capaz de carregar diversas imagens de
boot e módulos.  Por esse motivo ele é o único gerenciador de inicialização
capaz de carregar o conjunto de servidores do GNU Hurd.  O GRUB também permite
buscar imagens do kernel pela rede, por cabo seriais, suporta discos rígidos
IDE e SCSI, detecta toda a memória RAM disponível no sistema, tem interface
voltada para linha de comandos ou menus de escolha, além de suportar sistemas
sem discos e terminais remotos.


Como possui inúmeros recursos, será apresentada sua utilização básica, ficando
como sugestão ao leitor procurar se aprofundar mais em suas possibilidades de
uso e configuração.

 boot-grub-part">###Como o GRUB trabalha com discos e partições

O GRUB trabalha com uma notação diferente para apontar discos e partições sendo
necessário algumas explicações antes de prosseguir.  Veja a tabela comparativa:

<screen>
No Linux                No GRUB

/dev/hda                (hd0)
/dev/hda1               (hd0,0)
/dev/hda2               (hd0,1)

/dev/hdb                (hd1)
/dev/hdb1               (hd1,0)
/dev/hdb2               (hd1,1)

/dev/sda                (hd0)   # Disco SCSI ID 0
/dev/sda1               (hd0,0) # Disco SCSI ID 0, partição 1
/dev/sda2               (hd0,1) # Disco SCSI ID 0, partição 2

/dev/sdb                (hd1)   # Disco SCSI ID 1
/dev/sdb1               (hd1,0) # Disco SCSI ID 1, partição 1
/dev/sdb2               (hd1,1) # Disco SCSI ID 1, partição 2

/dev/fd0                (fd0)


**OBS:** Os discos **IDE** e
**SCSI** são referenciados ambos como (<literal>hd?)
pelo <command>GRUB.  Não há distinção entre os discos e de modo geral
a identificação de unidades IDE é menor do que qualquer tipo de drive SCSI,
salvo se você alterar a seqüência de inicialização (boot) na BIOS.


Para saber como o Linux trabalha com partições veja <xref linkend="disc-id"/>.



 boot-grub-install">###Instalando o GRUB

A instalação do <command>GRUB ao contrário da instalação do
<command>LILO (<xref linkend="boot-lilo"/>), só precisa ser executada
uma única vez.  Caso seja necessária alguma mudança como por exemplo adicionar
uma nova imagem, esta pode ser feita apenas editando o arquivo de configuração
<filename>menu.lst</filename>.

 boot-grub-install-mbr">###No MBR

Um método simples de adicionar o <command>GRUB para gerenciar seu MBR
(**Master Boot Record**) é rodando o seguinte comando (como
superusuário):

<screen>
# /sbin/grub-install /dev/hda


Este comando grava o <command>GRUB no MBR do primeiro disco e cria o
diretório <filename>/boot/grub</filename> onde estarão os arquivos necessários
para o seu funcionamento.  Neste ponto o <command>GRUB já está
instalado e quando você reiniciar seu computador irá se deparar com uma linha
de comandos, onde terá que carregar a imagem do kernel manualmente.  Mais
adiante será explorada a utilização desta linha de comando que é muito
eficiente.


Provavelmente você achará mais interessante copiar o arquivo de configuração de
exemplos do <command>GRUB e otimizá-lo às suas necessidades.  Note
que isto não exclui a possibilidade de utilizar a linha de comando, apenas cria
uma interface de menus onde você pode configurar várias opções de boot de uma
forma organizada, automatizada e funcional.  Copie este arquivo para o
diretório <filename>/boot/grub</filename> com o seguinte comando:

<screen>
# cp /usr/share/doc/grub/examples/menu.lst /boot/grub


Por ser um arquivo de exemplos será necessário otimizá-lo de acordo com suas
necessidades, o que será abordado mais a frente.





 boot-grub-install-fd-cmd">###No disco flexível (somente linha de comando)

Quando criamos um disquete de partida, este funcionará em um sistema qualquer,
podendo utilizar este disquete em várias máquinas diferentes ou em uma máquina
em que tenha tido algum problema com o <command>GRUB no MBR.  Coloque
um disquete virgem e digite os seguintes comandos:

<screen>
# dd if=/usr/lib/grub/i386-pc/stage1 of=/dev/fd0 count=1
# dd if=/usr/lib/grub/i386-pc/stage2 of=/dev/fd0 seek=1


Estes comandos permitem que seja apresentada a linha de comando do grub quando
este disco for utilizado para boot.



 boot-grub-install-fd-menu">###No disco flexível (com interface de menu)

Quando foi criado o disquete de partida anteriormente, este só nos permitia
utilizar a linha de comando sendo necessário carregar o
<filename>menu.lst</filename> pelo disco rígido (o qual deve estar presente).
Em alguns casos este disco satisfaz as necessidades básicas mas pode haver um
momento em que você deseje ter um disquete que funcione com vários sistema e
não dependa de um disco fixo.


Digite os seguintes comandos:

<screen>
# mke2fs /dev/fd0
# mount /dev/fd0 /floppy -t ext2
# mkdir /floppy/grub
# cp /usr/lib/grub/i386-pc/stage[12] /floppy/grub
# cp /usr/share/doc/grub/examples/menu.lst /floppy/grub
# umount /floppy
# /sbin/grub


Este último comando disponibiliza a linha de comando do GRUB.  Digite os
seguintes comandos:

<screen>
grub&gt; install (fd0)/grub/stage1 d (fd0) (fd0)/grub/stage2 p (fd0)/grub/menu.lst
grub&gt; quit


Neste momento o disquete está pronto.  Note que o <filename>menu.lst</filename>
que foi copiado para ele é um arquivo de exemplo, sendo necessário que você o
configure de acordo com suas necessidades.



 boot-grub-opcoescfg">###Opções do arquivo de configuração

Esta seção descreve o arquivo <filename>menu.lst</filename> com explicações
sobre as opções mais usadas.  Este arquivo é dividido em parâmetros Globais,
que afetam o arquivo todo e parâmetros que só tem efeito para as imagens do
sistema que será carregado.  Algumas opções podem ser passadas para o kernel do
Linux no momento do boot, algumas delas também serão detalhadas.

<variablelist>
<varlistentry>
<term>Parâmetros Globais
<listitem>
<itemizedlist>
<listitem>

<literal>timeout = Define um tempo (em segundos) de espera.  Se
nenhuma tecla for pressionada, carrega a imagem padrão.


<listitem>

<literal>default = Define qual será a opção padrão que deve ser
automaticamente selecionada quando nenhuma outra for especificada em um tempo
definido por timeout.


<listitem>

<literal>fallback = Caso ocorra algum erro inesperado e a opção
padrão não possa ser carregada, este parâmetro define qual a outra opção deve
ser utilizada.


<listitem>

<literal>color = Permite que você escolha as cores usadas no menu de
boot.


<listitem>

<literal>password = Permite que você especifique uma senha.  Está
será solicitada sempre que houver necessidade de realizar uma função que não
seja carregar as imagens disponíveis, como por exemplo acessar a linha de
comandos do GRUB.  Você pode utilizar também o parâmetro password para esconder
um arquivo que contenha outras configurações, como um menu.lst secreto.  O
arquivo pode ter um nome qualquer.

<screen>
Ex.: password = senha (hd0,0)/boot/grub/secret.conf


Você pode ter várias entradas do parâmetro "password" em um mesmo arquivo sendo
que uma delas é usada para bloquear o acesso as imagens/linha de comandos e as
outras usadas para carregar arquivos de opções do GRUB.  Quando você digitar
<literal>p para entrar com a senha, você pode digitar a senha que
protege as imagens/linha de comandos ou a que é utilizada para carregar os
arquivos de opções.


<listitem>

<literal>hiddenmenu = Está opção faz com que o menu de opções não
seja mostrado e de boot na imagem especificada por "default" depois de expirado
o tempo definido em <literal>timeout.  O usuário pode requisitar o
menu com as opções pressionando a tecla &lt;ESC&gt; antes que o tempo definido
em timeout expire.





<varlistentry>
<term>Parâmetros que afetam apenas as imagens
<listitem>
<itemizedlist>
<listitem>

<literal>title = Define um texto que será apresentado no menu de boot
para identificar o sistema a ser inicializado.


<listitem>

<literal>root = Determina qual a partição raiz do sistema a ser
inicializada.


<listitem>

<literal>rootnoverify = Idêntica a opção <literal>root, mas
não tenta montar a partição-alvo, o que é necessário para alguns sistemas como
<command>Dos e <command>Windows.


<listitem>

<literal>kernel = Nesta opção você informa qual o kernel vai ser
inicializado.  Você pode passar parâmetros diretamente para o kernel também.

<screen>
Ex.: kernel (hd0,0)/boot/vmlinuz-2.4.16 vga=6


<listitem>

<literal>module = Faz com que algum módulo necessário para o boot
seja carregado.  Lembre-se que estes não são módulos do kernel (módulos de som,
rede, etc.) e sim módulos necessários ao boot de alguns sistemas, como por
exemplo o <command>GNU Hurd.


<listitem>

<literal>lock = Quando você quiser controlar se uma pessoa pode
iniciar um sistema que esteja listado nas opções do menu de boot, você pode
utilizar esta opção que faz com que a senha especificada com o comando
"password" seja solicitada no momento em que se tentar carregar a imagem em
questão.


<listitem>

<literal>pause = Emite uma mensagem na tela e espera uma tecla ser
pressionada.


<listitem>

<literal>makeactive = Torna a partição ativa.  Este comando está
limitado a partições primárias dos discos.


<listitem>

<literal>chainloader = Alguns sistemas como o Windows ou Dos
armazenam seu próprio gerenciador de boot no início da partição em que ele está
instalado.  Para efetuar o boot destes sistemas através do GRUB, você precisa
pedir para que o gerenciador de boot de tal sistema seja carregado e faça seu
trabalho, dando o boot.


<listitem>

<literal>hide e <literal>unhide = Esconde e mostra partição
respectivamente.  Estas duas opções são necessárias quando houver mais de uma
versão do Dos ou Windows na máquina em partições diferentes, já que estes
sistemas detectam automaticamente a partição e quase sempre o fazem de modo
errado.  Suponha o Windows na primeira partição primária (hd0,0) e o Dos na
segunda partição primária (hd0,1).  Quando quisermos carregar estes sistemas
devemos proceder da seguinte maneira:

<screen>
title Windows
hide (hd0,1)
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader  +1
makeactive

title Dos
hide (hd0,0)
unhide (hd0,1)
rootnoverify (hd0,1)
chainloader  +1
makeactive


<listitem>

<literal>map = Alguns sistemas não permitem ser inicializados quando
não estão no primeiro disco (Dos, Win 9x, etc.).  Para resolver esta e outras
situações o <command>GRUB tem um comando que permite enganar tal
sistema mapeando as unidades de disco do modo como lhe for mais conveniente.


Imagine que você tenha o primeiro disco (hd0) com o GNU/Linux instalado e em um
outro disco (hd1) com o Windows/Dos instalado.  O Windows/Dos não permitem
serem inicializados desta forma e como solução você poderia usar a seguinte
entrada no arquivo de configurações do GRUB:

<screen>
title Windows
unhide (hd1,0)
rootnoverify (hd1,0)
chainloader +1
map (hd1) (hd0)
makeactive


Isso faz com que o disco (hd1), onde esta o Windows/Dos, seja apresentado a
este sistema como (hd0) "enganado" o mesmo e possibilitando o boot.





<varlistentry>
<term>Parâmetros enviados diretamente ao kernel
<listitem>

Pode ser necessário passar alguns parâmetros para o kernel no momento do boot.
Para maiores informações ver a seção <xref linkend="boot-kernelparam"/>.  Você
pode passar os parâmetros da seguinte maneira:

<screen>
# Exemplo de entrada no 'menu.lst'.
title Linux 2.4.16
root (hd0,0)
kernel (hd0,0)/boot/vmlinuz-2.4.16 vga=6 mem=512M ramdisk=0


Neste exemplo, a linha com o comando "kernel" é usada para indicar qual imagem
deve ser carregada.  As opções que seguem (vga, mem e ramdisk) são parâmetros
que devem ser passados diretamente ao kernel do sistema a ser carregado.



</variablelist>


 boot-grub-exemplo">###Um exemplo de arquivo de configuração
<screen>
# Exemplo de arquivo de configuração do GRUB.
# Note que você pode usar o  caracter '#' para fazer comentários.

# Se após 30 segundos nenhuma tecla for pressionada, carrega a imagem padrão.
timeout 30

# Define a primeira imagem como padrão.
default 0

# Caso a imagem padrão não funcione carrega a imagem definida aqui.
fallback 1

# Define as cores que serão usadas no menu.
color light-cyan/black white/blue

# Permite utilizar uma senha.
password minha-senha-secreta
password minha-senha (hd0,0)/boot/grub/secret.conf

# Para boot com o GNU/Hurd
title GNU/Hurd
root (hd0,0)
kernel /boot/gnumach.gz root=hd0s1
module /boot/serverboot.gz

# Para boot com o GNU/Linux
title Linux 2.4.16
# Pede a senha configurada em "password" antes de carregar esta imagem.
lock
root (hd0,0)
# Atente as opções passadas diretamente para o kernel (vga, mem, etc.).
kernel (hd0,0)/boot/vmlinuz-2.4.16 vga=6 mem=512M ramdisk=0

# Para boot com o Mach (obtendo o kernel de um disquete)
title Utah Mach4 multiboot
root (hd0,2)
pause Insira o disquete agora!!!
kernel (fd0)/boot/kernel root=hd0s3
module (fd0)/boot/bootstrap

# Para boot com FreeBSD
title FreeBSD 3.4
root (hd0,2,a)
kernel /boot/loader

# Para boot com OS/2
title OS/2
root (hd0,1)
makeactive
chainloader +1
chainloader /boot/chain.os2

# Para boot com Windows 9x, ME, NT, 2000, XP.
title Windows 9x, ME, NT, 2000, XP
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader  +1
makeactive

# Para instalar o GRUB no disco rígido.
title = Instala o GRUB no disco rígido
root = (hd0,0)
setup = (hd0)

# Muda as cores.
title Mudar as cores
color light-green/brown blink-red/blue



 boot-grub-cmdline">###Usando a linha de comandos do GRUB

O <command>GRUB possui inúmeros recursos, mas com certeza um dos mais
importantes e que merece destaque é sua linha de comandos.  A maioria dos
comandos usados no arquivo de configuração <filename>menu.lst</filename> são
válidos aqui e muitos outros estão disponíveis.  Uma breve apresentação da
linha de comandos será dada, ficando por conta do leitor se aprofundar o quanto
achar necessário em sua flexibilidade.


Quando o <command>GRUB é inicializado você pode se deparar com sua
linha de comandos ou se possuir o arquivo <filename>menu.lst</filename>
configurado, um menu de escolha.  Mesmo usando os menus de escolha você pode
utilizar a linha de comandos, bastando para isso seguir as instruções no rodapé
da tela onde o <command>GRUB nos informa que podemos digitar
<literal>e para editar as entradas de boot ou <literal>c
para ter acesso a linha de comandos (lembre-se que pressionar
<literal>&lt;ESC&gt; faz com que você volte aos menus de escolha).


Caso a opção <literal>password tenha sido especificada no arquivo
<filename>menu.lst</filename>, será necessário antes de acessar as outras
opções (que estarão desabilitadas) pressionar <literal>p e entrar com
a senha correta.


Agora, com acesso a linha de comandos, você pode verificar os comandos
disponíveis pressionando duas vezes a tecla &lt;TAB&gt;.  Note que você também
pode utilizar esta tecla para completar nomes de comandos bem como parâmetros
de alguns comandos.


Alguns comandos disponíveis:

<itemizedlist>
<listitem>

<literal>cat = Este comando permite verificar o conteúdo de um
arquivo qualquer, o qual deve estar gravado em um dispositivo ligado a sua
máquina.  Embora seja um recurso útil, nenhuma permissão de acesso é verificada
e qualquer pessoa que tenha acesso a linha de comandos do GRUB pode listar o
conteúdo de arquivos importantes.  Para contornar este problema o parâmetro
<literal>password é utilizado no arquivo
<filename>menu.lst</filename> e faz com que uma senha seja solicitada antes de
liberar o acesso a linha de comandos.  Não esqueça que ainda é possível
utilizar um disquete com o <command>GRUB para dar boot na máquina o
que permite usar a linha de comandos pelo disquete.

<screen>
Ex.: grub&gt; cat (hd0,0)/etc/passwd


<listitem>

<literal>cmp = Este comando é utilizado para comparar dois arquivos.

<screen>
Ex.: grub&gt; cmp (hd0,0)/arquivo1 (hd0,0)/arquivo2


<listitem>

<literal>configfile = Carrega um arquivo de configuração do GRUB.

<screen>
Ex.: grub&gt; configfile (hd0,0)/boot/grub/menu.lst


<listitem>

<literal>displayapm = Mostra informações sobre APM.


<listitem>

<literal>displaymem = Mostra informações sobre a memória RAM.


<listitem>

<literal>find = Permite encontrar um arquivo.  A saída deste comando
disponibiliza o nome completo do caminho para o arquivo e a partição onde o
mesmo está localizado.

<screen>
Ex.: grub&gt; find stage1


<listitem>

<literal>geometry = Mostra informações sobre a geometria reconhecida
de seu drive e permite que você escolha a geometria desejada caso esta esteja
sendo reconhecida erroneamente.


<listitem>

<literal>help = help "comando" para ver a ajuda.

<screen>
Ex.: help color


<listitem>

<literal>install = Instala o GRUB, embora não seja recomendado o uso
deste comando diretamente, pois é possível esquecer ou trocar facilmente um
parâmetro e sobrescrever a tabela de partições de seu disco.

<screen>
Ex.: install (fd0)/grub/stage1 d (fd0) (fd0)/grub/stage2 p (fd0)/grub/menu.lst


<listitem>

<literal>setup = Você pode usar este comando para instalar o GRUB.
Note que sua sintaxe é menos complexa do que a usada em
<literal>install.

<screen>
Ex.: 
grub&gt; root = (hd0,0)
grub&gt; setup = (hd0)


<listitem>

<literal>quit = Abandona a linha de comandos do GRUB.


<listitem>

<literal>reboot = Reinicia o computador.


<listitem>

<literal>boot = Efetua o boot.  Suponha o Linux instalado em (hd0,0),
podemos passar os seguintes comandos na linha de comandos para efetuar o boot
de uma imagem do GNU/Linux:

<screen>
grub&gt; root (hd0,0)
grub&gt; kernel (hd0,0)/boot/vmlinuz-2.4.16 vga=6
grub&gt; boot




Muitos outros comandos estão disponíveis tanto na linha de comandos do
<command>GRUB quanto no arquivo de configuração
<filename>menu.lst</filename>.  Estes comandos adicionais podem ser necessários
apenas para algumas pessoas e por isso não serão explicados.



 boot-grub-removendo">###Removendo o GRUB do MBR

Não existe a necessidade de se remover o <command>GRUB do MBR pois
não há utilização para o mesmo vazio.  Para substituir o
<command>GRUB do MBR é necessário apenas que outro gerenciador de
boot escreva algo nele.  Você pode seguir o procedimento de instalação do
<command>LILO para escrever algo no MBR ou usar o comando
<literal>fdisk /mbr do DOS.



 boot-grub-detalhes">###Como obter informações mais detalhadas

Para obter informações mais detalhadas sobre o <command>GRUB é
recomendado o site oficial do mesmo, o qual está disponível apenas na língua
inglesa.  Os seguintes sites foram utilizados na pesquisa:

<itemizedlist>
<listitem>

Site oficial do GRUB: ("http://www.w3.org/1999/xlink) [](http://www.gnu.org/software/grub)http://www.gnu.org/software/grub/


<listitem>

Site Debian-br http://www.w3.org/1999/xlink) [](http://www.debianbrasil.org)http://www.debianbrasil.org/), na
parte de suporte, documentação, "Como usar o GRUB: Um guia rápido para usar o
GRUB, feito por Vitor Silva Souza e Gustavo Noronha Silva".







 boot-kernelparam">###Parâmetros de inicialização passados ao kernel

Abaixo algumas das opções mais usadas para passar parâmetros de inicialização
de hardware/características ao kernel.

<itemizedlist>
<listitem>

<literal>append=string - Passa os parâmetros especificados ao kernel.
É extremamente útil para passar parâmetros de hardwares que podem ter problemas
na hora da detecção ou para parâmetros que precisam ser passados constantemente
ao kernel através do aviso <literal>boot:.


Exemplo: <literal>append="mem=32m"


<listitem>

<literal>ramdisk=tamanho - Especifica o tamanho do disco RAM que será
criado.  Caso for igual a zero, nenhum disco RAM será criado.  Se não for
especificado, o tamanho do disco RAM usado na imagem de inicialização do kernel
será usada.


<listitem>

<literal>read-only - Especifica que o sistema de arquivos raiz deverá
ser montado como somente leitura.  Normalmente o sistema de inicialização
remonta o sistema de arquivos como leitura/gravação.


<listitem>

<literal>read-write - Especifica que o sistema de arquivos raiz
deverá ser montado como leitura e gravação.


<listitem>

<literal>root=dispositivo - Especifica o dispositivo que será montado
como raiz.  Se a palavra <literal>current é usada, o dispositivo
atual será montado como raiz.


<listitem>

<literal>vga=modo - Especifica o mode de video texto que será usado
durante a inicialização.

<itemizedlist>
<listitem>

<literal>normal - Usa o modo 80x25 (80 colunas por 25 linhas)


<listitem>

<literal>extended (ou ext) - Usa o modo de texto 80x50


<listitem>

<literal>ask - Pergunta que modo de video usar na inicialização.  Os
modos de vídeo podem ser obtidos pressionando-se enter quando o sistema
perguntar o modo de vídeo.






Uma lista mais detalhada de parâmetros de inicialização pode ser obtida no
documento <literal>Boot-prompt-howto (veja <xref linkend="ajuda-howto"/>).



 boot-loadlin">###LOADLIN

É um gerenciador de partida que permite iniciar o <command>GNU/Linux
a partir do <command>DOS.  A vantagem do uso do
<command>Loadlin é não ser preciso reiniciar o computador para se
entrar no <command>GNU/Linux.  Ele funciona carregando o
<command>kernel (copiado para a partição <command>DOS) para
a memória e inicializando o <command>GNU/Linux.


Outro motivo pelo qual é muito usado é quando o <command>GNU/Linux
não tem suporte a um certo tipo de dispositivo, mas este tem seu suporte no
<command>DOS ou <command>Windows e funciona corretamente
com eles.


O truque é o seguinte: Você inicia normalmente pelo <command>DOS e
após seu dispositivo ser configurado corretamente pelo driver do
<command>DOS e funcionando corretamente, você executa o
<command>Loadlin e o <command>GNU/Linux assim poderá
usa-lo.  Muitos usam o comando <command>Loadlin dentro do arquivo
<filename>autoexec.bat</filename> para iniciar o <command>GNU/Linux
automaticamente após o dispositivo ser configurado pelo <command>DOS.


ATENÇÃO!!!  Não execute o <command>Loadlin dentro do Windows.

 boot-loadlin-opcoes">###Opções do LOADLIN

Abaixo a lista de opções que podem ser usadas com o programa
<command>LOADLIN (note que todas são usadas no
<command>DOS):


<command>loadlin [**imagem_kernel**] [**argumentos**] [**opções**]

<itemizedlist>
<listitem>

<literal>imagem_kernel - Arquivo que contém o kernel.


<listitem>

<literal>root=dispositivo - Especifica o dispositivo que contém o
sistema de arquivos raiz.  É especificado de acordo com a identificação de
dispositivos no <command>GNU/Linux (<filename>/dev/hda1</filename>,
<filename>/dev/hdb1</filename>, etc).


<listitem>

<literal>ro - Diz ao kernel para montar inicialmente o sistema de
arquivos raiz como somente leitura.  Os scripts de inicialização normalmente
modificam o sistema de arquivos para leitura e gravação após sua checagem.


<listitem>

<literal>rw - Diz ao kernel para montar inicialmente o sistema de
arquivos raiz como leitura e gravação.


<listitem>

<literal>initrd=[NUM] - Define o tamanho do disco RAM usado no
sistema.


<listitem>

<literal>-v - Mostra detalhes sobre mensagens e configuração


<listitem>

<literal>-t - Modo de teste, tudo é feito menos a inicialização do
<command>GNU/Linux.


<listitem>

<literal>-d arquivo - Mesma função de <literal>-t, mas
envia a saída para o arquivo


<listitem>

<literal>-txmode - Altera o modo de vídeo para 80x25 antes de
inicializar o kernel.


<listitem>

<literal>-dskreset - Após carregar a imagem do kernel, reseta todos
os discos rígidos antes de inicializar o <command>GNU/Linux.





 boot-loadlin-exemplo">###Exemplo de inicialização com o LOADLIN

Abaixo você encontra um exemplo do comando <literal>loadlin que
poderá ser usado em sua instalação <command>GNU/Linux (precisando
apenas ajustar a localização da partição raiz do <command>GNU/Linux
de acordo com seu sistema).

<screen>
 C:\&gt; LOADLIN vmlinuz root=/dev/hda1 ro
                |        |            |
                |        |            +- Montar como somente leitura
                |        |
                |        +- Partição raiz
                |
                +- Nome do kernel copiado para o DOS





 boot-syslinux">###syslinux

Outro gerenciador de partida que funciona somente com sistemas de arquivos
<command>DOS.  A principal diferença do <command>syslinux
em relação ao <command>LOADLIN é que foi feito especialmente para
funcionar em disquetes formatados no <command>DOS, facilitando a
instalação do <command>GNU/Linux e para a criação de disquetes de
recuperação ou de inicialização.  Um disquete gerado pelo
<command>syslinux é lido sem problemas pelo
<command>DOS/<command>Windows.


<command>syslinux [-s] [**dispositivo**]


A opção <literal>-s instala no disquete uma versão segura, lenta e
estúpida do <command>syslinux.  Isto é necessário para algumas
<literal>BIOS problemáticas.

 boot-syslinux-criando">###Criando um disquete de inicialização com o syslinux

Siga os passos abaixo para criar um disquete de inicialização com o
<command>syslinux:

<orderedlist numeration="arabic">
<listitem>

Formate o disquete no <command>DOS ou com alguma ferramenta
<command>GNU/Linux que faça a formatação de disquetes para serem
usados no <command>DOS.


<listitem>

Copie um ou mais arquivos de <command>kernel para o disquete


<listitem>

Digite <literal>syslinux /dev/fd0 (lembre-se de usar a opção
<literal>-s se tiver problemas de inicialização).  Este comando
modificará o setor de partida do disquete e gravará um arquivo chamado
<filename>LDLINUX.SYS</filename> no diretório raiz do disquete.


Lembre-se: O disquete deve estar desmontado antes de usar o comando
<command>syslinux, caso o disquete estiver montado uma mensagem será
mostrada e o <command>syslinux abortado.


</orderedlist>

Por padrão é carregado o kernel de nome <filename>GNU/Linux</filename>.  Este
padrão pode ser modificado através do arquivo de configuração
<filename>SYSLINUX.CFG</filename> que também é gravado no diretório raiz do
disquete.  Veja <xref linkend="boot-syslinux-opcoes"para detalhes.


Se as teclas Caps Lock ou Scrool Lock estiverem ligadas ou Shift, Alt forem
pressionadas durante o carregamento do <command>syslinux, o
<command>syslinux mostrará um aviso de <literal>boot: no
estilo do <command>LILO.  O usuário pode então digitar o nome do
kernel seguido de qualquer parâmetro para inicializar o
<command>GNU/Linux.



 boot-syslinux-opcoes">###O arquivo SYSLINUX.CFG

Este arquivo é criado no diretório raiz da unidade de disquete e contém as
opções que serão usadas para modificar o funcionamento do
<command>syslinux.  Abaixo a listagem de opções que podem ser
especificadas neste arquivo:

<variablelist>
<varlistentry>
<term>default [kernel] [opções]
<listitem>

Indica o nome do kernel e as opções dele que serão usadas na inicialização,
caso <command>syslinux seja iniciado automaticamente.  Caso não for
especificada, o valor assumido será **linux auto** sem nenhuma
opção de inicialização.



<varlistentry>
<term>append [opções]
<listitem>

Passa uma ou mais opções ao kernel na inicialização.  Elas serão adicionadas
automaticamente para inicializações automáticas e manuais do
<command>syslinux.



<varlistentry>
<term>label [nome]
<term>kernel [kernel]
<term>append [opções]
<listitem>

Nome que identificará o kernel no aviso de <literal>boot: (idêntica a
opção <literal>label= do <command>LILO).  Se a imagem
especificada por <literal>nome for selecionada, o kernel usado será o
especificado pelo parâmetro <literal>kernel e as opções usadas por
<literal>append.


Caso seja passado um hífen <literal>- ao parâmetro
<literal>append, os parâmetros passados pelo
<literal>append global serão anulados.



<varlistentry>
<term>implicit [valor]
<listitem>

Se o [valor] for igual a 0, não carrega a imagem até que seja explicitamente
especificada na opção <literal>label.



<varlistentry>
<term>timeout [tempo]
<listitem>

Indica quanto tempo o <command>syslinux aguardará antes de
inicializar automaticamente (medido em 1/10 de segundos).  Caso alguma tecla
seja pressionada, a inicialização automática é interrompida.  Para desativar
esta característica, use 0 como <literal>timeout.  O valor máximo é
de 35996.



<varlistentry>
<term>font [nome]
<listitem>

Especifica uma fonte (em formato <filename>.psf</filename>) que será usada para
mostrar as mensagens do <command>syslinux (após o aviso de copyright
do programa).  Ele carrega a fonte para a placa de vídeo, se a fonte conter uma
tabela unicode, ela será ignorada.  Somente funciona em placas EGA e VGA.



<varlistentry>
<term>kbdmap [mapa]
<listitem>

Instala um simples mapa de teclado.  O mapa de teclados usado é muito simples:
somente remapeia códigos conhecidos pela <command>BIOS, o que
significa que somente teclas usadas no teclado padrão EUA serão usadas.


O utilitário <command>keytab-lilo.pl da distribuição do
<command>lilo pode ser usado para criar tais mapas de teclado.



<varlistentry>
<term>prompt [valor]
<listitem>

Se [valor] for igual a 1, mostra automaticamente o aviso de
<literal>boot: assim que o <command>syslinux for iniciado.
Caso seja igual a 0, mostra o aviso de <literal>boot: somente se as
teclas Shift ou Alt forem pressionadas ou Caps Lock e Scrool Lock estiverem
ativadas.



<varlistentry>
<term>display [arquivo]
<listitem>

Mostra o conteúdo do [arquivo] durante a inicialização do
<command>syslinux.



<varlistentry>
<term>F1 [arquivo]
<term>F2 [arquivo]
<term>...
<term>F0 [arquivo]
<listitem>

Especifica que arquivos serão mostrados quando as teclas de F1 até F10 forem
pressionadas.  Para detalhes, veja <xref linkend="boot-syslinux-formatacao"/>.



</variablelist>


 boot-syslinux-formatacao">###Formatação dos arquivos de tela do syslinux

Os arquivos de texto que são mostrados na tela pelo <command>syslinux
podem ter suas cores modificadas usando parâmetros simples, isto causa um bom
efeito de apresentação.  Abaixo estão os códigos que podem ser usados para
criar um arquivo texto que será exibido pelo <command>syslinux:

<screen>
CTRL+L - Limpa a tela (semelhante ao que o clear faz). 
CTRL+O[frente][fundo] - Define a cor de frente e fundo, se somente 
                 uma cor for especificada, esta será assumida como frente. 
                 Veja os valores para [frente] e [fundo] abaixo:
                 00 - preto                      08 - cinza escuro
                 01 - azul escuro                09 - azul claro
                 02 - verde escuro               0a - verde claro 
                 03 - ciano escuro               0b - ciano claro
                 04 - vermelho escuro            0c - vermelho claro 
                 05 - purple escuro              0d - purple claro
                 06 - marrom                     0e - amarelo 
                 07 - cinza claro                0f - branco
CTRL+Z       - Equivalente ao fim de arquivo no DOS


O código padrão usado é o 07.  Escolhendo uma cor clara para o fundo (08-0f)
resultará em uma cor piscante correspondente para a texto (00-07).





