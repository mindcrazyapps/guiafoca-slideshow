<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" disc">###Discos e Partições

Este capítulo traz explicações de como manipular discos rígidos e partições no
sistema <command>GNU/Linux e como acessar seus discos de CD-ROM e
partições <command>DOS, <command>Windows 9X/XP/Vista/Seven/Oito/10
no <command>GNU/Linux.

<para userlevel="inter" >
Também será ensinado como formatar uma partição ou arquivo em formato
<literal>EXT2, <literal>EXT3, <literal>reiserfs,
<literal>xfs e usar a ferramenta <command>mkswap (para
criar uma partição ou arquivo de memória virtual).


 disc-particoes">###Partições

São divisões existentes no disco rígido que marcam onde começa onde termina um
sistema de arquivos.  As partições nos permitem usar mais de um sistema
operacional no mesmo computador (como o <command>GNU/Linux,
<command>Windows e <command>DOS), ou dividir o disco rígido
em uma ou mais partes para ser usado por um único sistema operacional ou até
mesmo por diferentes arquiteturas (32 e 64 bits).


<!-- [ %DESCRICAOD [ -->
<para userlevel="inter" >
Para gravar os dados, o disco rígido deve ser primeiro particionado (usando o
<command>cfdisk, <command>parted,
<command>diskdruid, <command>fdisk), escolher o tipo da
partição (**Linux Native**, **Linux Swap**,
etc) e depois aquela partição deve ser formatada com o
<command>mkfs.ext3 (veja <xref linkend="disc-ext3"/>).

<para userlevel="inter" >
Após criada e formatada, a partição será automaticamente identificada como um
dispositivo no diretório <filename>/dev</filename> 
(veja <xref linkend="disc-id"/>) .  e deverá ser montada 
(<xref linkend="disc-montagem"/>) para permitir seu uso no sistema. 


Uma partição de disco não interfere em outras partições existentes, por este
motivo é possível usar o <command>Windows,
<command>GNU/Linux e qualquer outro sistema operacional no mesmo
disco.  Para escolher qual deles será inicializado, veja <xref linkend="boot"/>.


Para particionar (dividir) o disco rígido em uma ou mais partes é necessário o
uso de um programa de particionamento.  Os programas mais conhecidos para
particionamento de discos no <command>GNU/Linux são
<command>fdisk, <command>cfdisk e o <command>Disk
Druid.

<!-- [ %OBS [ -->

Lembre-se:

<itemizedlist>
<listitem>

Quando se apaga uma partição, você estará apagando TODOS os arquivos existentes
nela!


<listitem>

A partição do tipo **Linux Native** (Tipo 83) é a usada para
armazenar arquivos no <command>GNU/Linux, tanto ext2, ext3, ext4,
reiserfs, xfs, etc.  Para detalhes veja <xref linkend="disc-ext2"/>.


<listitem>

A partição do tipo **Linux Swap** (Tipo 82) é usada como
memória virtual.  Para detalhes veja <xref linkend="disc-swap"/>.


<listitem>

Em sistemas novos, é comum encontrar o <command>Windows instalado em
uma partição que consome TODO o espaço do disco rígido.  Uma solução para
instalar o <command>GNU/Linux é apagar a partição
<command>Windows e criar três com tamanhos menores (uma para o
<command>Windows, uma para o <command>GNU/Linux e outra
para a **Memória Virtual do Linux (SWAP)**.  Ou criar apenas 2
se você não quiser mais saber mais do <command>Windows ;-)


A outra solução é usar o <command>parted (e
<command>gparted sua versão gráfica), que trabalha com
<literal>FAT16, <literal>FAT32, <literal>NTFS.
Esta técnica também é chamada de <literal>Reparticionamento não
destrutivo (e o outro obviamente <literal>Reparticionamento
destrutivo).  Para sistemas que foram formatados em <command>Windows
XP e superiores, é possível que o <command>parted não
consiga redimensionar o sistema, neste caso você pode reparticionar usando
ferramentas como o <command>ntfsresize ou <literal>Partition
Magic (para <command>Windows).



<!-- ]]> -->

Para mais detalhes sobre discos, partições ou como particionar seu disco, veja
algum bom documento sobre particionamento (como a página de manual e
documentação do <command>fdisk, <command>cfdisk,
<command>parted ou <command>Disk Druid).



 userlevel="inter" disc-sistarq">###Sistema de Arquivos

É criado durante a "formatação" da partição de disco (quando se usa o comando
<command>mkfs.ext3).  Após a formatação toda a estrutura para
leitura/gravação/permissões de arquivos e diretórios pelo sistema operacional
estará pronta para ser usada.  Normalmente este passo é feito durante a
instalação de sua distribuição <command>GNU/Linux.


Cada sistema de arquivos tem uma característica em particular mas seu propósito
é o mesmo: Oferecer ao sistema operacional a estrutura necessária para
ler/gravar os arquivos/diretórios.


Entre os sistemas de arquivos existentes posso citar:

<itemizedlist>
<listitem>

<literal>Ext2 - Usado em partições **Linux Nativas**
para o armazenamento de arquivos.  É identificado pelo código 83.  Seu tamanho
deve ser o suficiente para acomodar todo os arquivos e programas que deseja
instalar no <command>GNU/Linux (você encontra isto no manual de sua
distribuição).  Você deverá usar preferencialmente o <literal>ext3
para a instalação de seu sistema operacional.  Para detalhes veja <xref linkend="disc-ext2"/>.


<listitem>

<literal>Ext3 - Este sistema de arquivos possui melhorias em relação
ao ext2, como destaque o recurso de jornaling e suporte a arquivos de até 16Gb.
Ele também é identificado pelo tipo 83 e totalmente compatível com o ext2 em
estrutura.  O journal mantém um log de todas as operações no sistema de
arquivos, caso aconteça uma queda de energia elétrica (ou qualquer outra
anormalidade que interrompa o funcionamento do sistema), o
<command>fsck verifica o sistema de arquivos no ponto em que estava
quando houve a interrupção, evitando a demora para checar todo um sistema de
arquivos (que pode levar minutos em sistemas de arquivos muito grandes).  Para
detalhes veja <xref linkend="disc-ext3"/>.


<listitem>

<literal>Reiserfs - Possui os mesmos recursos do ext3, mas seu design
é bastante diferente.  Bastante recomendavel para sistemas que possuem muitos
arquivos pequenos (servidor web, etc).  Possui o tempo de recuperação em caso
de queda de energia menor que o ext3.  Para detalhes veja <xref linkend="disc-reiserfs"/>.


<listitem>

<literal>Swap - Usado em partições **Linux Swap**
para oferecer memória virtual ao sistema.  Note que é altamente recomendado o
uso de uma partição Swap no sistema (principalmente se você tiver menos que
16MB de memória RAM).  Este tipo de partição é identificado pelo código 82.
Para detalhes veja <xref linkend="disc-swap"/>.


<listitem>

<literal>proc - Sistema de arquivos do kernel (veja <xref linkend="disc-proc"/>).


<listitem>

<literal>FAT12 - Usado em disquetes no <command>DOS.  Não
possui suporte a permissões, journaling.


<listitem>

<literal>FAT16 - Usado no <command>DOS e oferece suporte
até discos de 2GB.  Não possui suporte a permissões e journaling.


<listitem>

<literal>FAT32 - Também usado no <command>DOS e oferece
suporte a discos de até 2 Terabytes.  Não possui suporte a permissões e
journaling.  <literal>NTFS - Formato nativo de discos de sistemas
operacionais Windows XP e superiores.  Possui suporte a permissões de acesso e
compactação nativa.






 userlevel="inter" disc-ext2">###Partição EXT2 (Linux Native)

A partição <literal>EXT2 é o tipo usado para criar o sistema de
arquivos <command>Linux Native usado para armazenar o sistema de
arquivos <literal>EXT2 (após a formatação) e permitir o armazenamento
de dados.  Para detalhes de como criar uma partição EXT2 veja <xref linkend="disc-ext2-criando-p"/>.


Este tipo de partição é normalmente identificado pelo código 83 nos programas
de particionamento de disco.  Note que também é possível criar um sistema de
arquivos <literal>EXT2 em um arquivo (ao invés de uma partição) que
poderá ser montado e acessado normalmente pelo sistema de arquivos (veja <xref linkend="disc-ext2-criando-a"/>.


Logo que foi inventado, o <command>GNU/Linux utilizava o sistema de
arquivos **Minix** (e consequentemente uma partição
**Minix**) para o armazenamento de arquivos.  Com a evolução
do desenvolvimento, foi criado o padrão **EXT**
(**Extended Filesystem**) e logo evoluiu para o
**EXT2** (**Second Extended Filesystem**).  O
padrão mais usado nos dias de hoje é o **EXT3** devido ao
Journaling (será abordado no próximo capítulo).


Entre as vantagens do EXT2 para armazenamento de arquivos estão: é o mais
rápido devido ao não uso de journaling (principalmente para Netbooks e
dispositivos flash), não se fragmenta tão facilmente pois permite a localização
do melhor lugar onde o arquivo se encaixa no disco, etc.  Isto é útil para
grandes ambientes multiusuário onde várias pessoas gravam/apagam arquivos o
tempo todo.



 userlevel="inter"  disc-ext2-criando-p">###Criando um sistema de arquivos EXT2 em uma partição

O utilitário usado para formatar uma partição <literal>EXT2 é o
<command>mkfs.ext2.  Após terminar este passo, seu sistema de
arquivos <literal>EXT2 estará pronto para ser usado.


Após particionar seu disco rígido e criar uma (ou várias) partições
<literal>EXT2, use o comando:


<literal>mkfs.ext2 /dev/sda?


Onde a "?"  em <literal>sda? significa o número da partição que será
formatada.  A identificação da partição é mostrada durante o particionamento do
disco, anote se for o caso.  <literal>sda normalmente é o primeiro
disco rígido SATA, <literal>sdb é o segundo disco rígido SATA.
Discos IDE normalmente são identificados por <literal>hda?,
<literal>hdb?, etc.  
Para detalhes sobre a identificação de discos,
veja <xref linkend="disc-id"/>.


Algumas opções são úteis ao <command>mkfs.ext2:

<itemizedlist>
<listitem>

<literal>-c Procura blocos danificados na partição antes de criar o
sistema de arquivos.


<listitem>

<literal>-L NOME Coloca um nome (label) no sistema de arquivos.


<listitem>

<literal>-b NUM Define o tamanho do bloco, em bytes.


<listitem>

<literal>-m NUM Define a porcentagem de espaço em disco reservada
para manutenção (por padrão reservado para o root, mas isto é alterável).




Agora para acessar a partição deverá ser usado o comando: <literal>mount
/dev/sda?  /mnt -t ext2


Para mais detalhes veja <xref linkend="disc-montagem"/>. 

<!-- [ %OBS [ --> 

Note que é possível criar um sistema de arquivos no disco rígido sem criar uma
partição usando <filename>/dev/sda</filename>, <filename>/dev/sdb</filename>,
etc.  **EVITE FAZER ISSO!** Como não estará
criando uma partição, o disco estará divido de maneira incorreta, você não
poderá apagar o sistema de arquivos completamente do disco caso precise
(lembre-se que você não criou uma partição), e a partição possui uma assinatura
apropriada que identifica o sistema de arquivos.


O espaço padrão reservado na partição para o usuário root é de 5%.  Em sistemas
com partições maiores que 10Gb, isso pode representar uma grande quantidade de
espaço em disco não utilizada por outros usuários.  Veja a opção
<literal>-m sobre como fazer esta modificação.  Caso já tenha criado
a partição, isto pode ser feito no <command>tune2fs com a opção
<literal>-m.

<!-- ]]> -->



 userlevel="inter" disc-ext2-criando-a">###Criando um sistema de arquivos EXT2 em um arquivo

É possível criar um sistema de arquivos EXT2 em um arquivo que poderá ser
montado e acessado normalmente como se fosse uma partição normal.  Isto é
possível por causa do recurso <literal>loop oferecido pelo kernel do
<command>GNU/Linux.  Os dispositivos de <literal>loop estão
disponíveis no diretório <filename>/dev</filename> com o nome
<filename>loop?</filename> (normalmente estão disponíveis 8 dispositivos de
<literal>loop).


Isto é possível usando o comando <command>dd e o
<command>mkfs.ext2.  Veja passo a passo como criar o sistema de
arquivos <literal>EXT2 em um arquivo:

<orderedlist numeration="arabic">
<listitem>

Use o comando <literal>dd if=/dev/zero of=/tmp/arquivo-ext2 bs=1024
count=10000 para criar um arquivo <filename>arquivo-ext2</filename>
vazio de 10Mb de tamanho em <filename>/tmp</filename>.  Você pode modificar os
parâmetros de <literal>of para escolher onde o arquivo será criado, o
tamanho do arquivo poderá ser modificado através de <literal>count


<listitem>

Formate o arquivo com <literal>mkfs.ext2 /tmp/arquivo-ext2.  Ele
primeiro dirá que o arquivo <filename>arquivo-ext2</filename> não é um
dispositivo de bloco especial (uma partição de disco) e perguntará se deve
continuar, responda com <literal>y.


O sistema de arquivos EXT2 será criado em
<filename>/tmp/arquivo-ext2</filename> e estará pronto para ser usado.


<listitem>

Monte o arquivo <filename>arquivo-ext2</filename> com o comando: <literal>mount
/tmp/arquivo-ext2 /mnt -o loop=/dev/loop1.  Note que foi usado o
parâmetro <literal>-o loop para dizer ao comando
<command>mount para usar os recursos de <literal>loop do
kernel para montar o sistema de arquivos.


<listitem>

Confira se o sistema de arquivos <literal>EXT2 em
<filename>arquivo-ext2</filename> foi realmente montado no sistema de arquivos
digitando <literal>df -T.  
Para detalhes, veja <xref linkend="cmdv-df"/>. 


</orderedlist>

Pronto!  o que você gravar para <filename>/mnt</filename> será gravado dentro
do arquivo <filename>/tmp/arquivo-ext2</filename>.  Como foi criado um sistema
de arquivos <literal>EXT2 em <filename>arquivo-ext2</filename>, você
poderá usar todos os recursos da partição <literal>EXT2 normal, como
permissões de arquivos e diretórios, links simbólicos, etc.


O uso da opção <literal>loop=/dev/loop1 permite que o dispositivo
<filename>/dev/loop1</filename> seja associado ao arquivo
<filename>/arquivo-ext2</filename> e assim permitir sua montagem e uso no
sistema.


<!-- [ %OBS [ -->
<itemizedlist>
<listitem>

Você poderá usar apenas <literal>-o loop com o comando
<command>mount, assim o kernel gerenciará automaticamente os
dispositivos de <literal>loop.


<listitem>

Caso faça isto manualmente, lembre-se de usar dispositivos
<literal>/dev/loop? diferentes para cada arquivo que montar no
sistema.  Pois cada um faz referência a um único arquivo.



<!-- ]]> -->





 userlevel="inter" disc-journal">###Journaling

O sistema de journaling grava qualquer operação que será feita no disco em uma
área especial chamada "journal", assim se acontecer algum problema durante
alterações no disco, ele pode voltar ao estado anterior do arquivo, ou
finalizar a operação.


Desta forma, o journal acrescenta ao sistema de arquivos o suporte a alta
disponibilidade e maior tolerância a falhas.  Após uma falha de energia, por
exemplo, o journal é analisado durante a montagem do sistema de arquivos e
todas as operações que estavam sendo feitas no disco são verificadas.
Dependendo do estado da operação, elas podem ser desfeitas ou finalizadas.  O
retorno do servidor é praticamente imediato (sem precisar a enorme espera da
execução do fsck em partições maiores que 10Gb), garantindo o rápido retorno
dos serviços da máquina.


Outra situação que pode ser evitada é com inconsistências no sistema de
arquivos do servidor após a situação acima, fazendo o servidor ficar em estado
'single user' e esperando pela intervenção do administrador.  Este capítulo do
guia explica a utilização de journaling usando o sistema de arquivos
**ext3** e **reiserfs** (veja <xref linkend="disc-ext3"para detalhes).




 userlevel="inter" disc-ext3">###Partição EXT3 (Linux Native)

O sistema de arquivos **ext3** faz parte da nova geração
extended file system do <command>Linux, sendo o padrão atual e tem
como seu maior benefício o suporte a journaling e armazenamento eficiente de
arquivos com até 16Gb de tamanho.


O uso deste sistema de arquivos comparado ao **ext2**, na
maioria dos casos, melhora o desempenho do sistema de arquivos através da
gravação seqüencial dos dados na área de metadados e acesso mhash a sua árvore
de diretórios.  Mas pode trazer impactos na performance no caso de dispositivos
de memória flash e quando utiliza arquivos para armazenar o sistema de
arquivos.


A estrutura da partição <command>ext3 é semelhante a
<command>ext2, o journaling é feito em um arquivo chamado
<filename>.journal</filename> que fica oculto pelo código
**ext3** na raiz da partição (desta forma ele não poderá ser
apagado, comprometendo o funcionamento do sistema).  A estrutura idêntica da
partição **ext3** com a **ext2** torna mais
fácil a manutenção do sistema, já que todas as ferramentas para recuperação
**ext2** funcionarão sem problemas.


 userlevel="inter" disc-ext3-criando-p">###Criando um sistema de arquivos EXT3 em uma partição

Para criar uma partição **ext3**, utilize o comando
<command>mkfs.ext3 ou o <command>mkfs.ext2 junto com a
opção **-j**.  

<!-- [ %DESCRICAOD [ --> As opções usadas pelo
<command>mkfs.ext3 são idênticas a do <command>mkfs.ext2
(documentado em <xref linkend="disc-ext2-criando-p"/>).  A única vantagem desta
ferramenta comparada ao <command>mkfs.ext2 é que a opção
**-j** é automaticamente adicionada a linha de comando para
criar um sistema de arquivos com journal.  Se você é daqueles que querem ter um
controle maior sobre o tamanho do arquivo de journal, use a opção **-J
[tam]** (onde tamanho é o tamanho em Megabytes). <!-- ]]> -->


Quando uma partição **ext3** é criada, o arquivo
<filename>.journal</filename> é criado no raíz da partição, sendo usado para
gravar os metadados das transações de journaling.  A estrutura da partição ext2
não difere em nada da ext3, a não ser este arquivo e a opção "has_journal" que
é passada a partição.


Por exemplo, para criar uma partição ext3 em <filename>/dev/sda1</filename>:

<screen>
 mkfs.ext3 /dev/sda1

ou

 mkfs.ext2 -j /dev/sda1


Basta agora montar a partição com o comando <literal>mount /dev/sda1 /teste -t
ext3 (para montar a partição em <filename>/teste</filename>.  Após
isto, modifique o <filename>/etc/fstab</filename> para montar a partição como
**ext3** quando o <command>Linux for iniciado.  
<!-- [ %INIC-INTER [ --> Para mais detalhes veja <xref linkend="disc-montagem"/>. <!-- ]]> --> ). 
Caso o suporte a **ext3** tenha sido compilado no kernel, ele tentará detectar
e montar a partição como **ext3**, caso contrário, ele usará
**ext2**.


Sua partição agora está montada como **ext3**, para conferir
digite: <literal>df -T.

<!-- [ %OBS [ -->

**OBS:** Quando criar um sistema de arquivos
**ext3** em uma partição raíz (<literal>/), tenha
certeza de incluir o suporte a **ext3** embutido no kernel,
caso contrário a partição será montada como **ext2**.

<!-- ]]> -->



 userlevel="inter" disc-ext3-criando-a">###Criando um sistema de arquivos EXT3 em um arquivo

As instruções para criar um sistema de arquivos <literal>ext3 em um
arquivo não difere muito das instruções de <xref linkend="disc-ext2-criando-a"/>, apenas utilize a opção **-j**
ou **-J [tamanho_em_mb]** (como explicado em <xref linkend="disc-ext3-criando-p"/>).




 userlevel="inter" disc-ext3-conv2-3">###Fazendo a conversão do sistema de arquivos EXT2 para EXT3

Se você já possui um uma partição **ext2** e deseja
converte-la para **ext3** isto poderá ser feito facilmente, de
forma segura (sem qualquer risco de perda de dados) e você poderá voltar para o
sistema ext2 caso deseje (veja <xref linkend="disc-ext3-conv3-2"/>).


Primeiro, execute o comando <command>tune2fs na partição que deseja
converter com a opção **-j** ou **-J
[tamanho_journal]** para adicionar o suporte a Journaling na partição.
Este comando poderá ser executado com segurança em uma partição
**ext2** montada, após converter remontar a partição usando os
comandos <literal>umount /particao e <literal>mount
/particao.


Após a conversão para **ext3** é desnecessária a checagem
periódica do sistema de arquivos (que por padrão é após 20 montagens e a cada
30 dias).  Você pode desativar a checagem após o número máximo de montagens com
a opção **-c [num_vezes]**, e o número de dias máximos antes
de verificar novamente com a opção **-i [num_dias]** (o uso de
0 desativa).  Por exemplo:

<screen>
tune2fs -c 0 -i 90 /dev/sda2


Desativa a checagem após número máximo de montagens (<literal>-c 0) e
diz para a partição ser verificada a cada 90 dias (<literal>-i 90).


O último passo é modificar o <filename>/etc/fstab</filename> para que a
partição seja montada como **ext3** na inicialização e depois
desmontar (<literal>umount /dev/sda2 e remonta-la (mount /dev/sda2)
para usar o suporte **ext3**.  Confira se ela está usando
**ext3** usando o comando <literal>df -T.

<!-- [ %OBS [ -->

**OBS:** Caso a partição convertida para
**ext3** seja a raíz (<literal>/), tenha certeza de
incluir o suporte a **ext3** embutido no kernel, caso
contrário, a partição será montada como **ext2**.

<!-- ]]> -->



 userlevel="inter" disc-ext3-conv3-2">###Convertendo de EXT3 para EXT2

Remover o suporte a **ext3** de uma partição é simples, rápido
e seguro.  Execute os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

Execute o comando <literal>tune2fs -O^has_journal /dev/sdxx na
partição que deseja remover o Journal.  Este comando poderá ser executado em
uma partição montada.


<listitem>

Modifique o <filename>/etc/fstab</filename> e altere a partição para
**ext2**.


<listitem>

Desmonte e monte novamente a partição com os comandos: <literal>umount
/dev/hdxx e <literal>mount /dev/sdxx.


<listitem>

Pronto!  a partição agora é novamente uma partição **ext2**
normal, confira digitando <literal>df -T.


</orderedlist>

Pronto, o suporte a **ext3** foi removido do seu sistema e
agora poderá usar a partição como **ext2** normalmente
(confira digitando <literal>df -T).




 userlevel="inter" disc-e2label">###Nomeando uma partição de disco ext2/ext3

O comando <command>e2label é usado para esta função.


<command>e2label [**dispositivo**][**nome**]

<!-- [ %OPCOES [ --> 

Onde:

<variablelist>
<varlistentry>
<term>**dispositivo**
<listitem>

Partição que terá o nome modificado



<varlistentry>
<term>**nome**
<listitem>

Nome que será dado a partição (máximo de 16 caracteres).  Caso seja usado um
nome de volume com espaços, ele deverá ser colocado entre "aspas".



</variablelist>
<!-- ]]> -->

Se não for especificado um nome, o nome atual da partição será mostrado.  O
nome da partição também pode ser visualizado através do comando
<command>dumpe2fs (veja <xref linkend="disc-dumpe2fs"/>).

<!-- [ %OBS [ -->

Exemplo: <literal>e2label /dev/sda1 FocaLinux, <literal>e2label
/dev/sda1 "Foca Linux"

<!-- ]]> -->



 userlevel="inter" disc-mklost-found">###Criando o diretório especial <filename>lost+found</filename>

O utilitário <command>mklost+found cria o diretório especial
<filename>lost+found</filename> no diretório atual.  
<!-- [ %DESCRICAOD [ --> O diretório
<filename>lost+found</filename> é criado automaticamente após a formatação da
partição com o <command>mkfs.ext2, a função deste diretório é
pré-alocar os blocos de arquivos/diretório durante a execução do programa
<command>fsck.ext2 na recuperação de um sistema de arquivos (veja
<xref linkend="manut-checagem"/>).  Isto garante que os blocos de disco não
precisarão ser diretamente alocados durante a checagem.
 <!-- ]]> -->

<literal>mklost+found

<!-- [ %OBS [ -->

OBS: Este comando só funciona em sistemas de arquivos ext2/3/4 <!-- ]]> -->

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>cd /tmp;mklost+found;ls -a

<!-- ]]> -->



 userlevel="inter" disc-dumpe2fs">###dumpe2fs

Mostra detalhes sobre uma partição <command>Linux.


<command>dumpe2fs [**opções**] [**partição**]

<!-- [ %OPCOES [ --> 

Onde:

<variablelist>
<varlistentry>
<term>**partição**
<listitem>

Identificação da partição que será usada.



<varlistentry>
<term>**opções**
<term>-b
<listitem>

Mostra somente os blocos marcado como defeituosos no sistema de arquivos
especificado.



</variablelist>
<!-- ]]> -->

Este comando lista diversas opções úteis do sistema de arquivos como o tipo do
sistema de arquivos, características especiais, número de inodos, blocos
livres, tamanho do bloco, intervalo entre checagens automáticas, etc.

<!-- [ %OBS [ --> 

Exemplo: <literal>dumpe2fs /dev/sda1, <literal>dumpe2fs -b
/dev/sda1

<!-- ]]> -->



 userlevel="inter" disc-ext2xarquivo">###Partição EXT2 ou Arquivo?

Criar uma partição <literal>EXT2 ou um arquivo usando o
<literal>loop?  Abaixo estão algumas considerações:

<itemizedlist>
<listitem>

A partição <literal>EXT2 é o método recomendado para a instalação do
<command>GNU/Linux.


<listitem>

O desempenho da partição <literal>EXT2 é bem melhor se comparado ao
arquivo porque é acessada diretamente pelo Kernel (SO).


<listitem>

O arquivo <literal>EXT2 é útil para guardarmos dados confidenciais em
disquetes ou em qualquer outro lugar no sistema.  Você pode perfeitamente
gravar seus arquivos confidenciais em um arquivo chamado
<filename>libBlaBlaBla-2.0</filename> no diretório <filename>/lib</filename> e
ninguém nunca suspeitará deste arquivo (acho que não...).  Também é possível
criptografa-lo para que mesmo alguém descobrindo que aquilo não é uma lib, não
poder abri-lo a não ser que tenha a senha (isto é coberto no documento
<filename>Loopback-encripted-filesystem.HOWTO</filename>).


<listitem>

O uso do arquivo <literal>EXT2 é útil quando você está perdendo
espaço na sua partição <literal>EXT2 e não quer re-particionar seu
disco pois teria que ser feita uma re-instalação completa e tem muito espaço em
um partição de outro SO (como o Windows).


Você poderia facilmente copiar o conteúdo de <filename>/var</filename>, por
exemplo, para o arquivo <literal>EXT2 <filename>ext2-l</filename>
criado no diretório Raíz do Windows, apagar o conteúdo de
<filename>/var</filename> (liberando muito espaço em disco) e então montar
<filename>ext2-l</filename> como <filename>/var</filename>.  A partir de agora,
tudo o que for gravado em <filename>/var</filename> será na realidade gravado
no arquivo <filename>ext2-l</filename>.


Para o sistema acessar o arquivo, deve passar pelo sistema de arquivos
<literal>loop e <literal>FAT32, isto causa um desempenho
menor.








 userlevel="inter" disc-reiserfs">###Sistema de arquivos reiserfs

Este é um sistema de arquivos alternativo ao **ext2/3/4** que
também possui suporte a journaling.  Entre suas principais características,
estão que ele possui tamanho de blocos variáveis, suporte a arquivos maiores
que 2 Gigabytes e o acesso mhash a árvore de diretórios é um pouco mais rápida
que o **ext3**.


Para utilizar <command>reiserfs, tenha certeza que seu kernel possui
o suporta habilitado (na seção <literal>File Systems) e instale o
pacote <command>reiserfsprogs que contém utilitários para formatar,
verificar este tipo de partição.



 userlevel="inter" disc-reiserfs-criando-p">###Criando um sistema de arquivos reiserfs em uma partição

Para criar uma partição **reiserfs**, primeiro instale o
pacote <systemitem role="package">reiserfsprogs</systemitem> (<literal>apt-get
install reiserfsprogs).


Para criar uma partição **reiserfs**, primeiro crie uma
partição **ext2** normal, e então use o comando:


<literal>mkreiserfs /dev/sda?


Onde a "?"  em <literal>sda? significa o número da partição que será
formatada com o sistema de arquivos **reiserfs**.  A
identificação da partição é mostrada durante o particionamento do disco, anote
se for o caso.  <literal>sda é o primeiro disco rígido SATA,
<literal>sdb é o segundo disco rígido SATA.  Discos IDE são
identificados por <literal>hda?, <literal>hdb?, etc.  
<!-- [ %INIC-INTER [ --> Para detalhes sobre a identificação de discos, veja <xref linkend="disc-id"/>. <!-- ]]> -->


Algumas opções são úteis ao <command>mkreiserfs:

<itemizedlist>
<listitem>

<literal>-s [num] - Especifica o tamanho do arquivo de journal em
blocos.  O valor mínimo é 513 e o máximo 32749 Kb.  O valor padrão é 8193.


<listitem>

<literal>-l [NOME] - Coloca um nome (label) no sistema de arquivos.


<listitem>

<literal>-f - Força a execução do <command>mkreiserfs.


<listitem>

<literal>-d - Ativa a depuração durante a execução do
<command>mkreiserfs.




Agora para acessar a partição deverá ser usado o comando: <literal>mount
/dev/sda?  /mnt -t reiserfs

<!-- [ %INIC-INTER [ -->

Para mais detalhes veja <xref linkend="disc-montagem"/>.

<!-- ]]> -->
<!-- [ %OBS [ -->

Note que é possível criar um sistema de arquivos no disco rígido sem criar uma
partição usando <filename>/dev/sda</filename>, <filename>/dev/sdb</filename>,
etc.  usando a opção <literal>-f **EVITE FAZER
ISSO!** Como não estará criando uma partição, o disco estará preparado
para uso de maneira incorreta, você não poderá apagar o sistema de arquivos
completamente do disco caso precise (lembre-se que você não criou uma
partição), e a partição possui uma assinatura apropriada que identifica o
sistema de arquivos.

<!-- ]]> -->




 userlevel="inter" disc-reiserfs-criando-a">###Criando um sistema de arquivos reiserfs em um arquivo

O sistema de arquivos <command>reiserfs também poderá ser criado em
um arquivo, usando os mesmos benefícios descritos em <xref linkend="disc-ext2-criando-a"/>.  Para fazer isso execute os seguintes passos
em seqüência:

<orderedlist numeration="arabic">
<listitem>

Use o comando <literal>dd if=/dev/zero of=/tmp/arquivo-reiserfs bs=1024
count=33000 para criar um arquivo
<filename>arquivo-reiserfs</filename> vazio de 33Mb de tamanho em
<filename>/tmp</filename>.  Você pode modificar os parâmetros de
<literal>of para escolher onde o arquivo será criado, o tamanho do
arquivo poderá ser modificado através de <literal>count.  Note que o
tamanho mínimo do arquivo deve ser de 32Mb, devido aos requerimentos do
<command>reiserfs.


<listitem>

Formate o arquivo com <literal>mkreiserfs -f /tmp/arquivo-reiserfs.
Ele primeiro dirá que o arquivo <filename>arquivo-reiserfs</filename> não é um
dispositivo de bloco especial (uma partição de disco) e perguntará se deve
continuar, responda com <literal>y.


O sistema de arquivos ReiserFS será criado em
<filename>/tmp/arquivo-reiserfs</filename> e estará pronto para ser usado.


<listitem>

Monte o arquivo <filename>arquivo-reiserfs</filename> com o comando:
<literal>mount /tmp/arquivo-reiserfs /mnt -t reiserfs -o
loop=/dev/loop1.  Note que foi usado o parâmetro <literal>-o
loop para dizer ao comando <command>mount para usar os
recursos de <literal>loop do kernel para montar o sistema de
arquivos.  O parâmetro <literal>-t reiserfs poderá ser omitido, se
desejar.


<listitem>

Confira se o sistema de arquivos <literal>ReiserFS em
<filename>arquivo-reiserfs</filename> foi realmente montado no sistema de
arquivos digitando <literal>df -T.  
<!-- [ %INIC-INTER [ --> Para detalhes, veja <xref linkend="cmdv-df"/>. <!-- ]]> -->


</orderedlist>


Pronto!  o que você gravar para <filename>/mnt</filename> será gravado dentro
do arquivo <filename>/tmp/arquivo-reiserfs</filename>.  Você poderá usar todos
os recursos de um sistema de arquivos <literal>reiserfs como
permissões de arquivos e diretórios, links simbólicos, etc.


O uso da opção <literal>loop=/dev/loop1 permite que o dispositivo
<filename>/dev/loop1</filename> seja associado ao arquivo
<filename>/arquivo-reiserfs</filename> e assim permitir sua montagem e uso no
sistema.


<!-- [ %OBS [ -->
<itemizedlist>
<listitem>

Você poderá usar apenas <literal>-o loop com o comando
<command>mount, assim o kernel gerenciará automaticamente os
dispositivos de <literal>loop.


<listitem>

Caso faça isto manualmente, lembre-se de usar dispositivos
<literal>/dev/loop? diferentes para cada arquivo que montar no
sistema.  Pois cada um faz referência a um único arquivo.



<!-- ]]> -->





 userlevel="inter" disc-swap">###Partição Linux Swap (Memória Virtual)

Este tipo de partição é usado para oferecer o suporte a **memória
virtual** ao <command>GNU/Linux em adição a
**memória RAM** instalada no sistema.  Este tipo de partição é
identificado pelo tipo 82 nos programas de particionamento de disco para
<command>Linux.  Para detalhes de como criar uma partição
<literal>Linux Swap veja <xref linkend="disc-swap-criando-p"/>.


Somente os dados na memória RAM são processados pelo processador, por ser mais
rápida.  Desta forma quando você está executando um programa e a memória RAM
começa a encher, o <command>GNU/Linux move automaticamente os dados
que não estão sendo usados para a partição Swap e libera a memória RAM para a
continuar carregando os dados necessários pelo.  Quando os dados movidos para a
partição Swap são solicitados, o <command>GNU/Linux move os dados da
partição Swap para a Memória.  Por este motivo a partição Swap também é chamada
<literal>de Troca ou <literal>memória virtual.


A partição swap é otimizada para permitir alta velocidade para mover dados da
memória RAM para ela e vice versa.  Note também que é possível criar o sistema
de arquivos **Swap** em um arquivo ao invés de uma partição
(veja <xref linkend="disc-swap-criando-a"/>).



 userlevel="inter" disc-swap-criando-p">###Criando sistema de arquivos Swap em uma partição

O programa usado para formatar uma partição Swap é o <command>mkswap.
Seu uso é simples:


<literal>mkswap /dev/sda?


<!-- [ %INIC-INTER [ --> Novamente veja <xref linkend="disc-id" caso não souber 
identificar seus discos e partições. <!-- ]]> --> O nome do dispositivo da partição 
<literal>Swap pode ser visualizado através de seu programa de particionamento, 
você pode usar o comando <literal>fdisk -l /dev/sda para listar as partições 
no primeiro disco rígido e assim verificar qual dispositivo corresponde a partição
Swap.


A opção <literal>-c também pode ser usada com o
<command>mkswap para checar se existem agrupamentos danificados na
partição.  A opção <literal>-v1 permite a criação da swap usando mais
de 128Mb (esta opção é a padrão).


Com a partição Swap formatada, use o comando: <literal>swapon
/dev/sda? para ativar a partição Swap (lembre-se de substituir ?
pelo número de sua partição Swap).


<!-- [ %OBS [ -->

Observações:


Versões antigas do kernel do <command>GNU/Linux 2.0.xx e anteriores
somente suportavam partições Swap de até 128MB.  Nos novos kernels foi
introduzida uma nova versão da swap.  Para converter a swap antiga para uma
nova versão reformate-a usando <command>mkswap -v1 /dev/sda? (onde
<filename>/dev/sda?</filename> especifica sua partição swap, obtida com o
<literal>fdisk -l /dev/sda).


Se utilizar mais que 1 partição <literal>Swap, pode ser útil o uso da
opção <literal>-p NUM que especifica a prioridade em que a partição
Swap será usada.  Pode ser usado um valor de prioridade entre 0 e 32767,
partições com número maior serão usadas primeiro, sendo que na montagem
automática através de "mount -a" podem ser designados números negativos.


Procure usar o número maior para partições mais rápidas (elas serão acessadas
primeiro) e números maiores para partições mais lentas.  <!-- ]]> -->

Caso precise desativar a partição Swap, use o comando: <literal>swapoff /dev/sda?.





 userlevel="inter" disc-swap-criando-a">###Criando um sistema de arquivos Swap em um arquivo

Também é possível criar um arquivo que poderá ser usado como memória virtual.
Veja passo a passo como fazer isso:

<orderedlist numeration="arabic">
<listitem>

Use o comando <literal>dd if=/dev/zero of=/tmp/troca bs=1024
count=64000 para criar um arquivo chamado <filename>troca</filename>
vazio de 64Mb de tamanho em <filename>/tmp</filename>.  Você pode modificar os
parâmetros de <literal>of para escolher onde o arquivo será criado, o
tamanho do arquivo poderá ser modificado através de <literal>count.


<listitem>

Execute <literal>mkswap /tmp/troca para formatar o arquivo.  Após
concluir este passo, o sistema de arquivos <literal>Swap estará
criado e pronto para ser usado.


<listitem>

Digite <literal>sync para sincronizar os buffers para o disco, assim
você não terá problemas em um servidor com muito I/O.


<listitem>

Ative o arquivo de troca com o comando <literal>swapon /tmp/troca.


<listitem>

Confira se o tamanho da memória virtual foi modificado digitando <literal>cat
/proc/meminfo ou <literal>free.


</orderedlist>

<!-- [ %OBS [ -->

Observações:

<itemizedlist>
<listitem>

Podem ser usadas partições de troca e arquivos de troca juntos, sem problemas.


<listitem>

Caso seu sistema já tenha uma partição de <literal>Swap, é
recomendável deixar o acesso ao arquivo <literal>Swap com uma
prioridade menor (usando a opção -p NUM com o comando
<command>swapon).



<!-- ]]> -->



 userlevel="inter" disc-swap-swapxarquivo">###Partição Swap ou Arquivo?

Criar uma partição de Troca ou um arquivo de troca?  Abaixo algumas vantagens e
desvantagens:

<itemizedlist>
<listitem>

A partição Swap é mais rápida que o arquivo Swap pois é acessada diretamente
pelo Kernel.  Se o seu computador tem pouca memória (menos que 512Mb) ou você
tem certeza que o sistema recorre freqüentemente a memória virtual para
executar seus programas, é recomendável usar uma partição Swap.


<listitem>

O arquivo de troca permite que você crie somente uma partição <literal>Linux
Native e crie o arquivo de troca na partição <literal>EXT2.


<listitem>

Você pode alterar o tamanho do arquivo de troca facilmente apagando e criando
um novo arquivo como descrito em <xref linkend="disc-swap-criando-a"/>.


<listitem>

É possível criar um arquivo de troca em outros tipos de partições como
<literal>FAT16, <literal>FAT32, <literal>NTFS,
etc.


<listitem>

O arquivo de troca estará disponível somente após o sistema de arquivos que o
armazena (<literal>ext2, <literal>fat32, etc) estar
montado.  Isto é um problema para sistemas com pouca memória que dependem do
arquivo de troca desde sua inicialização.








 userlevel="inter" disc-proc">###O sistema de arquivos <filename>/proc</filename>

É o sistema de arquivos do Kernel do <command>GNU/Linux.  Ele oferece
um método de ler, gravar e modificar dinamicamente os parâmetros do kernel,
muito útil para pessoas que gostam de entender como as coisas funcionam (como
eu) e programas de configuração.  A modificação dos arquivos do diretório
<filename>/proc</filename> é o método mais usado para modificar a configuração
do sistema e muitos programas também dependem deste diretório para funcionar.


Nele você tem todo o controle do que o seus sistema operacional está fazendo, a
configuração dos hardwares, interrupções, sistema de arquivos montado, execução
de programas, memória do sistema, rede, etc.


Agora entre no diretório <filename>/proc</filename> digite
<literal>ls e veja a quantidade de arquivos e diretórios que ele
possui, dê uma passeada por eles.  Abaixo a descrição de alguns deles (todos
podem ser visualizados pelo comando <command>cat):

<itemizedlist>
<listitem>

<literal>Diretórios com números - Estes identificam os parâmetros de
um processo em execução.  Por exemplo, se o PID (identificação do processo) do
<command>inetd for <literal>115, você pode entrar no
diretório <literal>115 e verificar as opções usadas para execução
deste programa através de cada arquivos existente dentro do diretório.  Alguns
são:

<itemizedlist>
<listitem>

<filename>cmdline</filename> - O que foi digitado para iniciar o processo (pode
também ter sido iniciado através de um programa ou pelo kernel).


<listitem>

<filename>environ</filename> - Variáveis de Ambiente existentes no momento da
execução do processo.


<listitem>

<filename>status</filename> - Dados sobre a execução do Processo (PID, status
da execução do programa, memória consumida, memória executável, UID, GID, etc).




<listitem>

<filename>apm</filename> - Dados sobre o gerenciamento de energia


<listitem>

<filename>cmdline</filename> - Linha de comando usada para inicializar o Kernel
<command>GNU/Linux.  Os parâmetros são passados através do programa
de inicialização, como o <command>LILO, <command>LOADLIN,
<command>SYSLINUX.


<listitem>

<filename>cpuinfo</filename> - Detalhes sobre a CPU do sistema


<listitem>

<filename>devices</filename> - Dispositivos usados no sistema


<listitem>

<filename>dma</filename> - Canais de DMA usados por dispositivos


<listitem>

<filename>filesystems</filename> - Sistemas de arquivos em uso atualmente


<listitem>

<filename>interrupts</filename> - Interrupções usadas por dispositivos


<listitem>

<filename>ioports</filename> - Portas de Entrada e Saída usadas pelos
dispositivos do sistema


<listitem>

<filename>kcore</filename> - Este arquivo corresponde a toda a memória RAM em
seu sistema.  Seu tamanho é correspondente a memória RAM do micro


<listitem>

<filename>kmsg</filename> - Permite visualizar mensagens do Kernel (use o
comando <literal>cat &lt; kmsg para visualiza-lo e pressione CTRL+C
para cancelar


<listitem>

<filename>loadavg</filename> - Média de Carga do sistema


<listitem>

<filename>meminfo</filename> - Dados de utilização da memória do sistema


<listitem>

<filename>misc</filename> - Outras configurações


<listitem>

<filename>modules</filename> - Módulos atualmente carregados no kernel


<listitem>

<filename>mounts</filename> - Sistemas de Arquivos atualmente montados


<listitem>

<filename>pci</filename> - Detalhes sobre dispositivos PCI do sistema


<listitem>

<filename>rtc</filename> - Relógio em Tempo real do sistema


<listitem>

<filename>uptime</filename> - Tempo de execução do sistema


<listitem>

<filename>version</filename> - Versão atual do Kernel, programa usado na
compilação, etc


<listitem>

Diretório <filename>net</filename> - Dados sobre a rede do sistema


<listitem>

Diretório <filename>sys</filename> - Dados sobre outras áreas do sistema


<listitem>

Diretório <filename>scsi</filename> - Detalhes sobre dispositivos SCSI do
sistema




Note que o diretório <filename>proc</filename> e os arquivos existentes dentro
dele estão localizados no diretório raiz (<filename>/</filename>), mas não
ocupa nenhum espaço no disco rígido.




 userlevel="inter" disc-lvm">###LVM - Logical Volume Manager

O <command>lvm (**Logical Volume Manager**) faz a
associação entre dispositivos/partições físicas (incluindo discos RAID, MO,
mass storages diversos, MD, e loop) e dispositivos lógicos.  O método
tradicional faz a alocação de todo espaço físico ao tamanho da partição do
disco (o método tradicional), o que traz muito trabalho quando o espaço esgota,
cópia de dados ou planejamento de uso de máquina (que pode mudar com o passar
do tempo).  O sistema de <command>lvm soluciona os seguintes
problemas:

<itemizedlist>
<listitem>

Uso eficaz de disco, principalmente quando há pouco espaço para criação de
partições independentes.


<listitem>

Permite aumentar/diminuir dinamicamente o tamanho das partições sem
reparticionamento do disco rígido usando o espaço livre em outras partições ou
utilizando o espaço livre reservado para o uso do LVM.


<listitem>

Uma partição de disco é identificada por um nome de volume e não pelo
dispositivo.  Você pode então se referir aos volumes como: usuários, vendas,
diretoria, etc.


<listitem>

Sua divisão em 3 camadas possibilita a adição/remoção de mais discos de um
conjunto caso seja necessário mais espaço em volumes, etc.


<listitem>

Permite selecionar o tamanho do cluster de armazenamento e a forma que eles são
acessados entre os discos, possibilitando garantir a escolha da melhor opção
dependendo da forma que os dados serão manipulados pelo servidor.


<listitem>

Permite snapshots dos volumes do disco rígido.




As 3 camadas do LVM são agrupadas da seguinte forma:

<itemizedlist>
<listitem>

<literal>PV (Phisical Volume) - Corresponde a todo o disco
rígido/partição ou dispositivo de bloco que será adicionado ao LVM.  Os
aplicativos que manipulam o volume físico, começam com as letras
<filename>pv*</filename>.  O espaço disponível no PV é dividido em PE (Phisical
Extends, ou extensões físicas).  O valor padrão do PE é de 4MB, possibilitando
a criação de um VG de 256Gb.


Por exemplo: <filename>/dev/hda1</filename>


<listitem>

<literal>VG (Volume Group) - Corresponde ao grupo de volumes físicos
que fazem parte do LVM.  Do grupo de volume são alocados os espaços para
criação dos volumes lógicos.  Os aplicativos que manipulam o o grupo de volume,
começam com as letras <filename>vg*</filename>.


Por exemplo: <filename>/dev/lvmdisk0</filename> <literal>LV (Logical
Volume) - Corresponde a partição lógica criada pelo LVM para gravação
de dados.  ao invés de ser identificada por nomes de dispositivos, podem ser
usados nomes comuns para se referir as partições (tmp,usr,etc.).  O Volume
lógico é a área onde o sistema de arquivo é criado para gravação de dados,
seria equivalente a partição em um sistema **SEM LVM** só que
lógica ao invés de física.  O volume lógico tem seu espaço dividido em LE
(Logical Extends, ou extensões lógicas) que correspondem aos PE's alocados.


Exemplos: <filename>/dev/lvmdisk/usr</filename>,
<filename>/dev/lvmdisk/tmp</filename>, etc.





 userlevel="inter" disc-lvm-graph">###Representação gráfica do LVM

Desenvolvi este desenho para representar a idéia de organização de um sistema
LVM para o guia Foca GNU/Linux e apresentar a descrição prática da coisa:

<screen>
+------[ Grupo de Volume (VG) - lvmdsk ]------+
| +--[ PV - hda1 ]---+ +--[ PV - hdb1 ]--+    |
| | PE PE PE PE PE PE| | PE PE PE PE PE  |    |
| +------------------+ +-----------------+    |
|    |  |                   |        |        |
|    |  | +-----------------+        |        |
|    |  +----------------+           |        |
|    |    |              |           |        |
|  +-[ LV - var ]-+    +-[ LV - home ]-+      |
|  | LE LE LE LE  |    | LE LE LE LE   |      |
|  +--------------+    +---------------+      |
+---------------------------------------------+


O gráfico acima representa a seguinte situação:

<orderedlist numeration="arabic">
<listitem>

Nós temos dois volumes físicos representados por <filename>hda1</filename> e
<filename>hdb1</filename>.  Cada um desses volumes físicos tem um Phisical
Extend (PE) de 4M (o padrão).


<listitem>

Estes dois volumes físicos acima representam o espaço total do grupo de volume
**lvmdisk** em <filename>/dev/lvmdisk</filename>.


<listitem>

Do grupo de volume **lvmdisk** são criados dois volumes
lógicos chamados **var** e **home**, estando
disponíveis para particionamento através de
<filename>/dev/lvmdisk/var</filename> e <filename>/var/lvmdisk/home</filename>.


</orderedlist>

Na prática, o espaço do volume lógico é definido alocando-se alguns Phisical
Extends (PE) dos volumes físicos como logical extends (LE) dos volumes lógicos.
Desta forma, o tamanho de todos os PEs e LEs existentes dentro de um mesmo
grupo de volume devem ser iguais.




 userlevel="inter" disc-lvm-perf">###Performance do LVM

Um sistema com LVM tem sua performance um pouco reduzida quanto ao acesso a
disco, devido as camadas adicionais de acesso aos dados, sendo afetadas
operações em caracteres e inteligentes de acesso a dados.


Entretanto, a performance de leitura/gravação de blocos é melhorada
consideravelmente após a adoção do LVM.  O LVM também garante que o sistema não
mostre sintomas de paradas durante o esvaziamento de cache de disco, mantendo
sempre uma certa constância na transferência de dados mesmo em operações
pesadas de I/O no disco.  Depende de você avaliar estes pontos e considerar sua
adoção.




 userlevel="inter" disc-lvm-install">###Instalando LVM em seu sistema

Nesta seção não tenho a intenção de cobrir todos os detalhes técnicos da
implantação do LVM, a idéia aqui é fornecer uma referência básica e prática
para uso em qualquer sistema normal (desconsiderando usos críticos).  A idéia
aqui é mostrar de forma prática como implantar LVM em sua máquina e preparar
seu uso nos discos.


Antes de começar, retire QUALQUER CD que estiver inserido na unidade de CD-ROM,
pois eles podem causar erro no <filename>pvscan</filename>,
<filename>pvdisplay</filename>, etc.

<orderedlist numeration="arabic">
<listitem>

No particionamento, defina as partições do tipo 8E (Linux LVM).  A partição
Linux LVM é exatamente igual a Linux Native (82), a única vantagem é que o LVM
utilizará auto detecção para saber quais partições ele deve utilizar no
<filename>pvscan</filename>.


<listitem>

Instale o pacote <systemitem role="package">lvm2</systemitem> e uma imagem de
kernel 4.x ou 5.x que tenha suporte a LVM, ou compile seu próprio kernel (caso
goste de máquinas turbinadas :-)


<listitem>

Execute o <command>pvscan para detectar as partições marcadas como
LVM e criar sua configuração em <filename>/etc/lvmtab.d</filename>.


**OBS:** É normal o sistema procurar
dispositivos de CD-ROM durante a execução do <command>pvscan, apenas
não deixe um CD na unidade para evitar grandes sustos se estiver desatento com
os passos :-)


<listitem>

Rode o <command>pvcreate no disco ou partição para dizer que ela será
um volume físico do LVM: <literal>pvcreate /dev/sda1 ou
<literal>pvcreate /dev/sda


Em caso de dúvida sobre qual é a partição LVM, digite: <literal>fdisk -l
/dev/sda (supondo que <filename>/dev/sda</filename> é o disco rígido
que está configurando o LVM).


<listitem>

Rode o pvdisplay /dev/hda1 para verificar se o volume físico foi criado.
Recomendo que deixe a partição raíz (<literal>/) de fora do LVM para
não ter futuros problemas com a manutenção do seu sistema, a menos que tenha
muitas opções de inicialização com suporte a LVM em mãos :-)


<listitem>

Crie o grupo de volume na partição <literal>vgcreate lvmdisk /dev/sda1
/dev/sdb7.  Note que partições de discos diferentes podem fazer parte
de um mesmo grupo de volume (VG) do LVM.  Caso use o <literal>devfs
ou em algumas versões do <literal>udev, será preciso usar o caminho
completo do dispositivo ao invés do link: <literal>vgcreate lvmdisk
/dev/ide/host0/bus0/target0/lun0/part1


O valor padrão do "Phisical Extend" é de 4MB mas pode ser alterado pelo
parâmetro "-s tamanho", assim o tamanho máximo do grupo de volume será de 256GB
(4MB * 64.000 extends que são suportados por volume lógico).  Os valores do
Phisical Extend (PE) pode ser de 8k a 16GB.  Não é possível modificar o tamanho
do PE após ele ser definido.


<listitem>

Verifique o grupo de volume (VG) recém criado com o comando:
<command>vgdisplay ou <command>vgdisplay /dev/sda7.  Atente
para a linha "Free PE / tamanho", que indica o espaço livre restante para criar
os volumes lógicos (LV).


<listitem>

Crie o volume lógico (LV) com o comando: <literal>lvcreate -L1500 -ntmp
lvmdisk Que vai criar uma partição LVM de 1500MB (1,5GB) com o nome
**tmp** (acessível por <filename>/var/lvmdisk/tmp</filename>)
dentro do grupo **lvmdisk**.  Você deverá fazer isso com as
outra partições.


<listitem>

Agora resta criar um sistema de arquivos (**ext3**,
**reiserfs**, **xfs**,
**jfs**, etc) como faria com qualquer partição física normal:


<literal>mkfs.ext3 /dev/lvmdisk/tmp ou <literal>mkfs.reiserfs
/dev/lvmdisk/tmp


</orderedlist>
<!-- [ %OBS [ -->

**OBS:** Caso  deseje montar automaticamente o
volume LVM, coloque o caminho completo do LVM ao invés do volume físico no
<filename>/etc/fstab</filename>: <filename>/dev/lvmdisk/tmp</filename>.

<!-- ]]> -->



 userlevel="inter" disc-lvm-grow">###Aumentando o tamanho de um volume lógico

O processo para aumentar o tamanho do volume lógico consiste em primeiro
aumentar o tamanho do VG com o <command>lvextend e depois ajustar o
tamanho do sistema de arquivos:

<screen>
# Aumenta o espaço do volume lógico tmp para 1G
lvextend -L1G /dev/lvmdisk/tmp

# Aumenta em 200MB o espaço no volume lógico tmp
lvextend -L+200M /dev/lvmdisk/tmp


As unidades <literal>Kk,Mm,Gg,Tt podem ser usadas para especificar o
espaço.  Após modificar o volume lógico, será preciso aumentar o tamanho do
sistema de arquivos para ser exatamente igual ao tamanho do LV.  Isto depende
do seu sistema de arquivos:

<variablelist>
<varlistentry>
<term>ext2/3
<listitem>

resize2fs /dev/lvmdisk/tmp


O **ext2/3** ainda vem com o utilitário
<command>e2fsadm que executa os dois comandos
(<command>lvextend e <command>resize2fs) de uma só vez:
<literal>e2fsadm -L+1G /dev/lvmdisk/tmp


**OBS:** Você deverá desmontar o sistema de
arquivos antes de alterar o tamanho de um sistema de arquivos
**ext2** ou **ext3**.  Em kernels da serie
2.6.17 e superiores, a alteração pode ser feita on-line (devido ao patch
ext2online incorporado ao kernel).



<varlistentry>
<term>reiserfs
<listitem>

resize_reiserfs -f /dev/lvmdisk/tmp


O tamanho do sistema de arquivos <command>reiserfs poderá ser
modificado on-line, assim não precisa parar seu servidor para esta operação.



<varlistentry>
<term>xfs
<listitem>

xfs_growfs /tmp


Note que deve ser especificado o ponto de montagem ao invés do dispositivo.  O
sistema de arquivos deverá ser montado antes de ser modificado e incluido no
<filename>/etc/fstab</filename>.



</variablelist>


 userlevel="inter" disc-lvm-shrink">###Diminuindo um volume lógico

Para diminuir o tamanho de um volume lógico, certifique-se de ter calculado o
espaço corretamente para acomodar todos os dados que já existem na partição.  A
diferença para o processo de aumentar o LV é que primeiramente o sistema de
arquivos é reduzido primeiro e depois o LV (pois o LV que acomoda o sistema de
arquivos):

<variablelist>
<varlistentry>
<term>ext2/3/4
<listitem>

<literal>resize2fs /dev/lvmdisk/tmp 4G e depois <literal>lvreduce
-L-1G /dev/lvmdisk/tmp


Podem ser usados K, M ou G para especificar o novo tamanho.  Caso esteja usando
um kernel 2.6.17 ou superior, o tamanho poderá ser ajustado com o sistema de
arquivos on-line (sem desmontar).



<varlistentry>
<term>reiserfs
<listitem>

<literal>resize_reiserfs -s-1G /dev/lvmdisk/tmp e depois
<literal>lvreduce -L-1G /dev/lvmdisk/tmp


O tamanho do sistema de arquivos <command>reiserfs poderá ser
modificado on-line, assim não precisa parar seu servidor para a modificação.



<varlistentry>
<term>xfs
<listitem>

Não é possível diminuir o tamanho de um sistema de arquivos XFS em sua versão
atual (12/2006).



</variablelist>






 userlevel="inic;inter" disc-formatando">###Formatando Pen-drives/Disquetes

As subseções seguintes explicarão maneiras de formatar seu pen-drive, memória
flash, e outras tecnologias (incluindo disquetes) para serem usados no
<command>GNU/Linux e <command>DOS/Windows.


 userlevel="inic;inter" disc-formatando-l">###Formatando pen-drives para serem usados no Linux

Para formatar pen-drives para serem usados no <command>GNU/Linux use
o comando:


<command>mkfs.ext2 [**-c**] [**/dev/sde1**]


Em alguns sistemas você deve usar <command>mke2fs no lugar de
<command>mkfs.ext2.  A opção <literal>-c faz com que o
<command>mkfs.ext2 procure por blocos danificados no pen-drive.  Caso
deseje formatar um disquete, especifique o dispositivo
<filename>/dev/fd0</filename> ao inves de <filename>/dev/sdb1</filename>.


Note que o nome de dispositivo que é conectado varia de acordo com o sistema e
quantidade de discos rígidos que sua máquina possui portanto tenha
**ATENCÃO** para não formatar o dispositivo incorreto (que
pode ser justamente seu disco rígido principal).  Para maior segurança,
ao identificar o pen-drive, digite <literal>dmesg ao conectar o
pen-drive para visualizar o dispositivo correto ou fique atento as mensagens do
console que mostrará o dispositivo que foi associado ao pen-drive.

<!-- [ %OBS [ -->

OBS: Este comando cria um sistema de arquivos **ext2** no
pen-drive e permite usar características como permissões de acesso e outras.
Isto também faz com que o pen-drive NÃO possa ser lido pelo
<command>DOS/Windows.  Para formatar um pen-drive no
<command>GNU/Linux usando o **FAT16** ou
**FAT32** (compatível com o DOS/Windows) veja próxima seção.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>mkfs.ext2 -c /dev/sde1

<!-- ]]> -->


 userlevel="inic;inter"  disc-formatando-d">###Formatando pen-drives compatíveis com o Windows

A formatação de pen-drives para serem usados no <command>Windows é
feita usando o comando <command>mkfs.msdos que é geralmente incluído
no pacote <systemitem role="package">dosfstools</systemitem>.  
<!-- [ %DESCRICAOD [ --> O <command>mkfs.msdos permite tanto a criação de sistemas de arquivos
FAT16 ou FAT32. <!-- ]]> -->


<command>mkfs.msdos [opções] [**dispositivo**]

<!-- [ %OPCOES [ -->
<variablelist>
<varlistentry>
<term>**dispositivo**
<listitem>

Pen-drive que será formatado.  Normalmente <filename>/dev/sdb1</filename>
(dependendo do dispositivo detectado via comando <literal>dmesg).



<varlistentry>
<term>**opções**
<term>-F [num]
<listitem>

Especifica o tipo de FAT que será usado na formatação.  Podem ser usados os
valores 12 (para formatação usando FAT12, limitado a 12MB), 16 (para formatação
usando FAT16, limitado a 2Gb) e 32 (para formatação FAT32, limitado a 128Gb).



<varlistentry>
<term>-n [nome]
<listitem>

Atribui o <literal>[nome] de volume ao dispositivo.



<varlistentry>
<term>-c
<listitem>

Faz uma pesquisa por bad blocks antes da criação do sistema de arquivos no
dispositivo.  Os setores defeituosos encontrados serão automaticamente marcados
para não serem utilizadas.



<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>-m [arquivo_mensagem]
<listitem>

Especifica o arquivo que contém a mensagem que será exibida ao usuário caso o
disco não seja inicializável.  A mensagem não pode exceder 418 bytes.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

Note que não se deve montar o pen-driv / disquete para formata-lo.

<!-- [ %OBS [ -->

Segue abaixo exemplos de como formatar seu pen-drive
<command>mkfs.msdos:

<itemizedlist>
<listitem>

<literal>mkfs.msdos /dev/sdc1 - Formata o pen-drive no terceiro
dispositivo SCSI Genérico, como FAT32 e usando os valores padrões.


<listitem>

<literal>mkfs.msdos -F 16 /dev/sdc1 - Faz a mesma coisa que o acima,
mas formata o pen-drive como FAT16.


<listitem>

<literal>mkfs.msdos -n teste -F 16 /dev/sdc1 - Formata o pen-drive no
terceiro dispositivo SCSI genérico, como FAT16 e cria o nome de volume
<literal>teste.



<!-- ]]> -->



 userlevel="inic;inter" disc-formatando-g">###Programas de Formatação Gráficos

Além de programas de formatação em modo texto, existem outros para ambiente
gráfico (X11) que permitem fazer a mesma tarefa.


Entre os diversos programas destaco o <command>gfloppy que além de
permitir selecionar se o disquete será formatado para o
<command>GNU/Linux (ext2), <command>DOS (FAT12) e permite
selecionar a capacidade e formatação rápida do disco.






 userlevel="inic;inter" disc-pontomontagem">###Pontos de Montagem

O <command>GNU/Linux acessa as partições existente em seus discos
rígidos e disquetes através de diretórios.  Os diretórios que são usados para
acessar (montar) partições são chamados de **Pontos de
Montagem**.  Para detalhes sobre montagem de partições, veja <xref linkend="disc-montagem"/>.


No <command>DOS cada letra de unidade (C:, D:, E:) identifica uma
partição de disco, no <command>GNU/Linux os pontos de montagem fazem
parte da grande estrutura do sistema de arquivos raiz.

<!-- [ %INTERMEDIARIO [ -->

Existem muitas vantagens de se usar **pontos de montagem** ao
invés de unidade de disco para identificar partições (método usado no
<command>Windows):

<itemizedlist>
<listitem>

Você pode montar a partição no diretório que quiser.


<listitem>

Em caso de um sistema de arquivos cheio, você pode copiar o conteúdo de um
grande diretório para outro sistema de arquivos, apagar o conteúdo do diretório
original e montar o disco onde foram copiados os arquivos naquele local (caso
não use um sistema de LVM).


<listitem>

Reduz riscos de corrompimento do sistema operacional.  Caso isto aconteça, será
necessário apenas restaurar o backup do sistema de arquivos afetado.


<listitem>

Tempo de boot reduzido quando um sistema de arquivos for verificado por
ferramentas como o <command>fsck.


<listitem>

O uso de **pontos de montagem** torna o gerenciamento mais
flexível.


<listitem>

A adição de novas partições ou substituição de discos rígidos não afeta a ordem
de identificação dos discos e pontos de montagem (como não acontece no
<command>DOS).



<!-- ]]> -->



 userlevel="inic;inter" disc-id">###Identificação de discos e partições em sistemas Linux

No <command>GNU/Linux, os dispositivos existentes em seu computador
(como discos rígidos, pen-drives, flash, storages remotas, disquetes, tela, portas de
impressora, modem, etc) são identificados por um arquivo referente a este
dispositivo no diretório <filename>/dev</filename>.


A identificação de discos rígidos no <command>GNU/Linux é feita da
seguinte forma:

<screen>
/dev/sda1
|    | ||
|    | ||_Número que identifica o número da partição no disco rígido.
|    | |
|    | |_Letra que identifica o disco rígido (a=primeiro, b=segundo, etc...).
|    |
|    |_Sigla que identifica o tipo do disco rígido (sd=SATA/SCSI, sd=IDE, xt=MFM).
|
|_Diretório onde são armazenados os dispositivos existentes no sistema.


Abaixo algumas identificações de discos e partições em sistemas Linux:

<itemizedlist>
<listitem>

**/dev/fd0** - <literal>Primeira unidade de
disquetes.


<listitem>

**/dev/fd1** - <literal>Segunda unidade de
disquetes.


<listitem>

**/dev/sda** - <literal>Primeiro disco rígido na primeira
controladora SATA ou SCSI.


<listitem>

**/dev/sda1** - <literal>Primeira partição do primeiro disco
rígido SATA ou.


<listitem>

**/dev/sdb** - <literal>Segundo disco rígido na primeira
controladora SATA ou SCSI.


<listitem>

**/dev/sdb1** - <literal>Primeira partição do segundo disco
rígido SATA ou SCSI.


<listitem>

**/dev/sr0** - <literal>Primeiro CD-ROM SATA ou
SCSI.


<listitem>

**/dev/sr1** - <literal>Segundo CD-ROM SATA ou SCSI.


<listitem>

**/dev/hda** - <literal>Primeiro disco rígido na primeira
controladora IDE do micro (primary master).


<listitem>

**/dev/hda1** - <literal>Primeira partição do primeiro disco
rígido IDE.


<listitem>

**/dev/hdb** - <literal>Segundo disco rígido na primeira
controladora IDE do micro (primary slave).


<listitem>

**/dev/hdb1** - <literal>Primeira partição do segundo disco
rígido IDE.


<listitem>

**/dev/xda** - <literal>Primeiro disco rígido XT.


<listitem>

**/dev/xdb** - <literal>Segundo disco rígido XT.




As letras de identificação de discos rígidos podem ir além de
<literal>sdb, por exemplo, caso utilize pen-drives, memória flash, as
unidades serão detectadas como <literal>sdc, <literal>sdd e
assim por diante.


É importante entender como os discos e partições são identificados no sistema,
pois será necessário usar os parâmetros corretos para monta-los.




 userlevel="inic;inter" disc-montagem">###Montando (acessando) uma partição de disco

Você pode acessar uma partição de disco usando o comando
<command>mount.


<command>mount [**dispositivo**] [**ponto de
montagem**] [**opções**]

<!-- [ %OPCOES [ --> 

Onde:

<variablelist>
<varlistentry>
<term>**dispositivo**
<listitem>

Identificação da unidade de disco/partição que deseja acessar (como
<literal>/dev/hda1 (disco rígido) ou <literal>/dev/fd0
(primeira unidade de disquetes).



<varlistentry>
<term>**ponto de montagem**
<listitem>

Diretório de onde a **unidade de disco/partição** será
acessado.  O diretório deve estar vazio para montagem de um sistema de arquivo.
Normalmente é usado o diretório <filename>/mnt</filename> para armazenamento de
pontos de montagem temporários.



<varlistentry>
<term>-t [tipo]
<listitem>

Tipo do sistema de arquivos usado pelo **dispositivo**.  São
aceitos os sistemas de arquivos:

<itemizedlist>
<listitem>

**ext2** - Para partições <command>GNU/Linux usando
o Extended File System versão 2 (a mais comum).


<listitem>

**ext3** - Para partições <command>GNU/Linux usando
o Extended File System versão 3, com suporte a journaling.


<listitem>

**ext4** - Para partições <command>GNU/Linux usando
o Extended File System versão 4, com suporte a journaling.


<listitem>

**reiserfs** - Para partições reiserfs, com suporte a
journaling.


<listitem>

**xfs** - Para partições xfs, com suporte a journaling.


<listitem>

**vfat** - Para partições <command>Windows 95 que
utilizam nomes extensos de arquivos e diretórios.


<listitem>

**msdos** - Para partições <command>DOS normais.


<listitem>

**iso9660** - Para montar unidades de
<command>CD-ROM.  É o padrão.




Na maioria das vezes, caso o sistema de arquivos não seja especificado, o
<command>mount utilizará a auto-detecção e montará a partição usando
o sistema de arquivos correto.  Para mais detalhes sobre opções usadas com cada
sistema de arquivos, veja a página de manual **mount**.



<varlistentry>
<term>-r
<listitem>

Caso for especificada, monta a partição somente para leitura.



<varlistentry>
<term>-w
<listitem>

Caso for especificada, monta a partição como leitura/gravação.  É o padrão.



</variablelist>
<!-- ]]> -->

Existem muitas outras opções que podem ser usadas com o comando
<command>mount, mas aqui procurei somente mostrar o básico para
"montar" seus discos e partições no <command>GNU/Linux (para mais
opções, veja a página de manual do <literal>mount).  Caso você
digitar <literal>mount sem parâmetros, serão mostrados que sistemas de
arquivos estão atualmente montados no sistema.  Esta mesma listagem pode ser vista em
<filename>/etc/mtab</filename>.  

<!-- [ %EXEMPLO [ --> 
A remontagem de partição também é muito útil,
especialmente após reparos nos sistema de arquivos do disco rígido.  Veja
alguns exemplos de remontagem abaixo.


É necessário permissões de root para montar partições, a não ser que tenha
especificado a opção <literal>user no arquivo
<filename>/etc/fstab</filename> (veja <xref linkend="disc-fstab"/>).


Exemplo de Montagem:

<itemizedlist>
<listitem>

Montar uma partição Windows (vfat) de <filename>/dev/sda1</filename> em
<filename>/mnt</filename> somente para leitura: <literal>mount /dev/sda1 /mnt
-r -t vfat


<listitem>

Montar um pen-drive detectado em <filename>/dev/sdc1</filename> em
<filename>/mnt</filename>: <literal>mount /dev/sdc1 /mnt -t vfat


<listitem>

Montar uma partição DOS localizada em um segundo disco rígido
<filename>/dev/hdb1</filename> em <filename>/mnt</filename>: <literal>mount
/dev/hdb1 /mnt -t msdos.


<listitem>

Remontar a partição raíz como somente leitura: <literal>mount -o remount,ro
/


<listitem>

Remontar a partição raíz como **leitura/gravação** (a opção -n
é usada porque o <command>mount não conseguirá atualizar o arquivo
<filename>/etc/mtab</filename> devido ao sistema de arquivos
<filename>/</filename> estar montado como somente leitura atualmente:
<literal>mount -n -o remount,rw /.



<!-- ]]> -->

 userlevel="inic;inter" disc-fstab">###fstab

O arquivo <filename>/etc/fstab</filename> permite que as partições do sistema
sejam montadas facilmente especificando somente o dispositivo ou o ponto de
montagem.  Este arquivo contém parâmetros sobre as partições que são lidos pelo
comando <command>mount.  Cada linha deste arquivo contém a partição
que desejamos montar, o ponto de montagem, o sistema de arquivos usado pela
partição e outras opções.  <filename>fstab</filename> tem a seguinte forma:

<screen>
Sistema_de_arquivos Ponto_de_Montagem Tipo    Opções           dump ordem
/dev/sda1           /                 ext3    defaults           0    1
/dev/sda2           /boot             ext3    defaults           0    2
/dev/sda3           /dos              msdos   defaults,noauto,rw 0    0
/dev/hdg            /cdrom            iso9660 defaults,noauto    0    0


Onde:

<variablelist>
<varlistentry>
<term>Sistema de Arquivos
<listitem>

Partição que deseja montar.



<varlistentry>
<term>Ponto de montagem
<listitem>

Diretório do <command>GNU/Linux onde a partição montada será
acessada.



<varlistentry>
<term>Tipo
<listitem>

Tipo de sistema de arquivos usado na partição que será montada.  Para partições
<command>GNU/Linux use **ext3**,
**reiserfs**, **xfs** (de acordo com o tipo
de partição selecionada durante a formatação), para partições
<command>DOS (sem nomes extensos de arquivos) use
**msdos**, para partições <command>Win 95 (com
suporte a nomes extensos de arquivos) use **vfat**, para
unidades de CD-ROM use **iso9660**.



<varlistentry>
<term>Opções
<listitem>

Especifica as opções usadas com o sistema de arquivos.  Abaixo, algumas opções
de montagem para ext2/3/4 (a lista completa pode ser encontrada na página de
manual do <command>mount):

<itemizedlist>
<listitem>

<literal>defaults - Utiliza valores padrões de montagem.


<listitem>

<literal>noauto - Não monta os sistemas de arquivos durante a
inicialização (útil para CD-ROMS e disquetes).


<listitem>

<literal>ro - Monta como somente leitura.


<listitem>

<literal>user - Permite que usuários montem o sistema de arquivos
(não recomendado por motivos de segurança).


<listitem>

<literal>sync é recomendado para uso com discos removíveis
(disquetes, zip drives, nfs, etc) para que os dados sejam gravados
imediatamente na unidade (caso não seja usada, você deve usar o comando <xref linkend="cmdv-sync"antes de retirar o disquete da unidade.





<varlistentry>
<term>dump
<listitem>

Especifica a frequência de backup feita com o programa <command>dump
no sistema de arquivos.  0 desativa o backup.



<varlistentry>
<term>Ordem
<listitem>

Define a ordem que os sistemas de arquivos serão verificados na inicialização
do sistema.  Se usar 0, o sistema de arquivos não é verificado.  O sistema de
arquivos raíz que deverá ser verificado primeiro é o raíz "/" 
<!-- [ %INTERMEDIARIO [ --> (a não ser quevocê tenha um sistema de arquivos de outro 
tipo que não é montado dentro do diretório raíz e possui seu suporte embutido 
no kernel). <!-- ]]> -->



</variablelist>

Após configurar o <filename>/etc/fstab</filename>, basta digitar o comando
<literal>mount /dev/hdg ou <literal>mount /cdrom para que a
unidade de CD-ROM seja montada.  Você deve ter notado que não é necessário
especificar o sistema de arquivos da partição pois o <command>mount
verificará se ele já existe no <filename>/etc/fstab</filename> e caso existir,
usará as opções especificadas neste arquivo.  Para maiores detalhes veja as
páginas de manual <filename>fstab</filename> e <command>mount.





 userlevel="inic;inter" disc-desmontagem">###Desmontando uma partição de disco

Utilize o comando <command>umount para desmontar um sistema de
arquivos que foi montado com o <command>mount.  Você deve ter
permissões de root para desmontar uma partição.


<command>umount [**dispositivo**/**ponto de montagem**]


Você pode tanto usar <literal>umount /dev/sda1 como <literal>umount
/mnt para desmontar um sistema de arquivos
<filename>/dev/sda1</filename> montado em <filename>/mnt</filename>.

<!-- [ %OBS [ --> 

**Observação:** O comando <command>umount executa o
<command>sync automaticamente no momento da desmontagem, para
garantir que todos os dados ainda em memória RAM sejam salvos.
 


