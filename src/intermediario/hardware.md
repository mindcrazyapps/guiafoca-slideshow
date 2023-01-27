<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inter;avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" hardw">###Hardware

Hardware é tudo que diz respeito a parte física do computador.  Nesta seção
serão abordados assuntos relacionados com a configuração de hardwares, escolha
de bons hardwares, dispositivos for Windows, etc.

 hardw-placas">###Placa de expansão

É um circuito eletrônico encaixado na placa mãe que tem por objetivo adicionar
novas funcionalidades ao computador.  Esta placa pode ser uma:

<itemizedlist>
<listitem>

<literal>placa de som - para fazer o computador emitir sons, músicas,
ligar um joystick, etc.


<listitem>

<literal>Placa de vídeo 3D - Para obter imagens mais rápidas para
jogos e ambientes de desktop 3 dimensões


<listitem>

<literal>Placa de captura - Para assistir televisão/rádio e gravar a
programação de TV em seu micro.


<listitem>

<literal>fax-modem - para enviar/receber fax, conectar-se a internet,
acesso remoto, bina, etc.


<listitem>

<literal>rede - para permitir a comunicação com outros computadores
em uma rede interna


<listitem>

<literal>controladora de periféricos - Para ligar discos rígidos,
unidades de disquete, impressora, mouse, joystick, etc.


<listitem>

<literal>SCSI - Para ligar unidades de disco rígidos e periféricos de
alto desempenho.


<listitem>

<literal>Controladora de Scanner - Para ligar um Scanner externo ao
micro computador.




O encaixe da placa mãe que recebe as placas de expansão são chamados de
**Slots**.



 hardw-nomesdisp">###Nomes de dispositivos

Seria terrível se ao configurar CADA programa que utilize o mouse ou o modem
precisássemos nos se referir a ele pela IRQ, I/O, etc...  para evitar isso são
usados os **nomes de dispositivos**.


Os **nomes de dispositivos** no sistema
<command>GNU/Linux são acessados através do diretório
<filename>/dev</filename>.  Após configurar corretamente o modem, com sua porta
I/O 0x2F8 e IRQ 3, ele é identificado automaticamente por
<filename>/dev/ttyS1</filename> (equivalente a <filename>COM2</filename> no
<command>DOS).  Daqui para frente basta se referir a
<filename>/dev/ttyS1</filename> para fazer alguma coisa com o modem.


Você também pode fazer um link de <filename>/dev/ttyS1</filename> para um
arquivo chamado <filename>/dev/modem</filename> usando: <literal>ln -s
/dev/ttyS1 /dev/modem, faça a configuração dos seus programas usando
<filename>/dev/modem</filename> ao invés de <filename>/dev/ttyS1</filename> e
se precisar reconfigurar o seu modem e a porta serial mudar para
<filename>/dev/ttyS3</filename>, será necessário somente apagar o link
<filename>/dev/modem</filename> antigo e criar um novo apontando para a porta
serial <filename>/dev/ttyS3</filename>.


Não será necessário reconfigurar os programas que usam o modem pois eles estão
usando <filename>/dev/modem</filename> que está apontando para a localização
correta.  Isto é muito útil para um bom gerenciamento do sistema.


Abaixo uma tabela com o nome do dispositivo no <command>GNU/Linux,
portas I/O, IRQ, DMA e nome do dispositivo no <command>DOS (os nomes
de dispositivos estão localizados no diretório <filename>/dev</filename>):

<screen>
Dispos.   Dispos.
 Linux     DOS       IRQ     DMA     I/O

ttyS0      COM1       4       -      0x3F8
ttyS1      COM2       3       -      0x2F8
ttyS2      COM3       4       -      0x3E8
ttyS3      COM4       3       -      0x2E8
lp0        LPT1       7      3(ECP)  0x378
lp1        LPT2       5      3(ECP)  0x278
/dev/hda1  C:        14       -      0x1F0,0x3F6
/dev/hda2  D: *      14       -      0x1F0,0x3F6
/dev/hdb1  D: *      15       -      0x170,0x376


* A designação de letras de unidade do <command>DOS não segue o
padrão do <command>GNU/Linux e depende da existência de outras
unidades físicas/lógicas no computador.



 hardw-cfg">###Configuração de Hardware

A configuração consiste em ajustar as opções de funcionamento dos dispositivos
(periféricos) para comunicação com a placa mãe bem como a configuração do
software correspondente para fazer acesso ao hardware.  Um sistema bem
configurado consiste em cada dispositivo funcionando com suas portas I/O, IRQ,
DMA bem definidas, não existindo conflitos com outros dispositivos.  Isto
também permitirá a adição de novos dispositivos ao sistema sem problemas.


Dispositivos PCI, PCI Express, AMR, CNR possuem configuração automática de
recursos de hardware, podendo apenas ser ligados na máquina para serem
reconhecidos pela placa mãe.  Após isso deverá ser feita a configuração do
módulo do kernel para que o hardware funcione corretamente.


Os parâmetros dos módulos do kernel usados para configurar dispositivos de
hardware são a **IRQ**, **DMA** e
**I/O**.  Para dispositivos plug and play, como hardwares PCI,
basta carregar o módulo para ter o hardware funcionando.

 hardw-cfg-irq">###IRQ - Requisição de Interrupção

Existem dois tipos básicos de interrupções: as usadas por dispositivos (para a
comunicação com a placa mãe) e programas (para obter a atenção do processador).
As **interrupções de software** são mais usadas por programas,
incluindo o sistema operacional e **interrupções de hardware**
mais usado por periféricos.  Daqui para frente será explicado somente detalhes
sobre interrupções de hardware.


Os antigos computadores 8086/8088 (XT) usavam somente <literal>8
interrupções de hardware operando a 8 bits.  Com o surgimento do AT foram
incluídas 8 novas interrupções, operando a 16 bits.  Os computadores 286 e
superiores tem <literal>16 interrupções de hardware numeradas de 0 a
15.  No kernel 2.4 e superiores do Linux, a função APIC (**Advanced
Programmable Interruption Controller**) permite gerenciar de forma
avançada mais de 15 interrupções no sistema operacional.  Estas interrupções
oferecem ao dispositivo associado a capacidade de interromper o que o
processador estiver fazendo, pedindo atenção imediata.


As interrupções do sistema podem ser visualizadas no kernel com o comando
<literal>cat /proc/interrupts.  Abaixo um resumo do uso mais comum
das 16 interrupções de hardware:

<screen>
0     Timer do Sistema  - Fixa

01    Teclado - Fixa

02    Controlador de Interrupção Programável - Fixa. 
      Esta interrupção é usada como ponte para a IRQ 9 e vem dos 
      antigos processadores 8086/8088 que somente tinham 8 IRQs. 
      Assim, pera tornar processadores 8088 e 80286 comunicáveis, 
      a IRQ 2 é usada como um redirecionador quando se utiliza uma
      interrupção acima da 8. 

03    Normalmente usado por /dev/ttyS1 mas seu uso depende dos 
      dispositivos instalados em seu sistema (como fax-modem,  
      placas de rede 8 bits, etc). 

04    Normalmente usado por /dev/ttyS0 e quase sempre usada pelo mouse 
      serial a não ser que um mouse PS2 esteja instalado no sistema. 

05    Normalmente a segunda porta paralela. Muitos micros não tem a segunda 
      porta paralela, assim é comum encontrar placas de som e outros 
      dispositivos usando esta IRQ. 

06    Controlador de Disquete - Esta interrupção pode ser compartilhada 
      com placas aceleradoras de disquete usadas em tapes (unidades de fita). 

07    Primeira porta de impressora. Pessoas tiveram sucesso compartilhando 
      esta porta de impressora com a segunda porta de impressora. 
      Muitas impressoras não usam IRQs. 

08    Relógio em tempo real do CMOS - Não pode ser usado por nenhum 
      outro dispositivo.

09    Esta é uma ponte para IRQ2 e deve ser a última IRQ a ser 
      utilizada. No entanto pode ser usada por dispositivos. 

10   Interrupção normalmente livre para dispositivos. O controlador
     USB utiliza essa interrupção quando presente, mas não é regra.

11   Interrupção livre para dispositivos

12   Interrupção normalmente livre para dispositivos. O mouse PS/2, 
     quando presente, utiliza esta interrupção. 

13   Processador de dados numéricos - Não pode ser usada ou compartilhada 

14  Esta interrupção é usada pela primeira controladora de discos 
    rígidos e não pode ser compartilhada. 

15  Esta é a interrupção usada pela segunda controladora de discos 
    e não pode ser compartilhada. Pode ser usada caso a segunda 
    controladora esteja desativada.


Dispositivos ISA, VESA, EISA, SCSI não permitem o compartilhamento de uma mesma
IRQ, talvez isto ainda seja possível caso não haja outras opções disponíveis
e/ou os dois dispositivos não acessem a IRQ ao mesmo tempo, mas isto é uma
solução precária.


Conflitos de IRQ ocorriam nesse tipo de hardware acima ocasionando a parada ou
mal funcionamento de um dispositivo e/ou de todo o sistema.  Para resolver um
conflito de IRQs, deve-se conhecer quais IRQs estão sendo usadas por quais
dispositivos (usando <literal>cat /proc/interrupts) e configurar as
interrupções de forma que uma não entre em conflito com outra.  Isto
normalmente é feito através dos jumpers de placas ou através de software (no
caso de dispositivos jumperless ou plug-and-play).


Dispositivos PCI, PCI Express são projetados para permitir o compartilhamento
de interrupções.  Se for necessário usar uma interrupção normal, o chipset (ou
BIOS) mapeará a interrupção para uma interrupção normal do sistema (normalmente
usando alguma interrupção entre a IRQ 9 e IRQ 12) ou usando APIC (se estiver
configurado).

 s3.3.1.1">###Prioridade das Interrupções

Cada IRQ no sistema tem um número que identifica a prioridade que será atendida
pelo processador.  Nos antigos sistemas XT as prioridades eram identificadas em
seqüência de acordo com as interrupções existentes:

<screen>
IRQ 0 1 2 3 4 5 6 7 8 
PRI 1 2 3 4 5 6 7 8 9


Com o surgimento do barramento AT (16 bits), as interrupções passaram a ser
identificadas da seguinte forma:

<screen>
IRQ 0  1  2  (9  10  11  12  13  14  15)  3  4  5  6  7  8 
PRI 1  2  3   4   5   6   7   8   9  10  11 12 13 14 15 16


Note que a prioridade segue em seqüência através da <literal>ponte da
IRQ 2 para IRQ 9.  Os dispositivos com prioridade mais baixa são atendidos
primeiro, mas é uma diferença de desempenho praticamente imperceptível de ser
notada nos sistemas atuais.





 hardw-cfg-dma">###DMA - Acesso Direto a Memória

A **DMA** é usada para permitir a transferência de dados entre
dispositivos I/O e a memória sem precisar do processador para fazê-lo.  Ele
livra esta carga do processador e resulta em uma rápida transferência de dados.


O PC padrão tem dois controladores de DMA.  O primeiro controla os canais
<literal>0, 1, 2, 3 e o segundo os canais <literal>4, 5, 6,
7, assim temos <literal>8 canais.  No entanto, o canal
<literal>4 é perdido porque é usado pelo **controlador de
acesso direto a memória**.  Os canais 0-3 são chamados de canais
baixos porque podem somente mover um byte (**8 bits**) por
transferência enquanto canais altos movem 2 bytes (**16
bits**) por transferência.


Os dados movidos usando a DMA **não** são
movidos através do controlador de DMA.  Isto oferece uma limitação porque a DMA
somente podem mover dados entre os dispositivos (portas I/O) e a memória.  Não
é possível mover dados entre as portas ou entre a memória.


Existem dois controladores de DMA nos computadores AT e superiores.  Ao
contrário do que acontece com os dois controladores de IRQ, o primeiro
controlador é ligado ao segundo e não o segundo ao primeiro.  Os canais de DMA
altos (5 ao 7) somente podem ser acessados por dispositivos de 16 bits (aqueles
que utilizam a segunda parte do slot AT).  Como resultado temos 8 canais de
DMA, de 0 a 7, sendo que a DMA 4 é usada como ligação entre eles.


Os canais de DMA em uso no sistema podem ser visualizados com <literal>cat
/proc/dma.  Abaixo uma listagem de uso mais comum dos canais de DMA.

<screen>
DMA    Barram.    Uso
0        -        Usada pelo circuito de refresh da memória DRAM
1     8/16 bits   Normalmente usado por placas de som (canal 8 bits), 
                  porta paralela ECP, adaptadoras SCSI, placas de rede ou 
                  controladora de scanner. 
2     8/16 bits   Normalmente usado pela controladora de disquetes ou 
                  controladoras de tapes. 
3     8/6 bits    Usado pela porta paralela ECP, placa de som, 
                  controladoras de tapes, controladoras SCSI ou 
                  controladora de scanner antiga. 
4        -        Usada como ponte para a outra controladora de DMA (0-3)
5     16 bits     Normalmente usada pela placa de som (canal 16 bits), 
                  placas controladoras SCSI, placas de rede ou 
                  controladora de scanner. 
6     16 bits     Placa de som (canal 16 bits), controladora de scanner  
                  ou placa de rede. 
7     16 bits     Placa de som (canal 16 bits), controladora de scanner 
                  ou placa de rede.


Somente dispositivos ISA e derivados dele, como o EISA e VESA, usam os canais
de DMA padrão.  Os atuais dispositivos de alta taxa de transferência
(normalmente PCI) possuem seu próprio controlador de DMA embutido, muito mais
rápido do que a DMA padrão.  Este controlador de DMA é chamado de **Bus
Mastering** e muito usado nos discos rígidos atuais e pode atingir
taxas de 33,3MB/s (no modo 2) e 66MB/s (no modo 4 - requer um cabo IDE com
aterramento para evitar interferências de ruídos externos).

 s3.3.2.1">###Conflitos de DMA

Um canal de DMA não pode ser compartilhado entre dispositivos.  Ainda é
possível configurar dois dispositivos para usarem um mesmo canal de DMA, desde
que ele não seja usado ao mesmo tempo.  Isto acontece com Scanners paralelos
que compartilham a mesma porta paralela com a impressora.  Se você for uma
pessoa que explora os recursos de multitarefa de seu Linux e seu desempenho,
evite estes tipos de dispositivos, prefira aqueles que utilizam seus próprios
recursos.


Quando ocorre um conflito de DMA, os dados podem ser misturados e ocorrerem
coisas estranhas até o travamento total do sistema.  Este tipo de conflito é
difícil de se diagnosticar, a não ser que o técnico seja experiente o bastante
e tenha desconfiado do que o problema se trata...





 hardw-cfg-io">###I/O - Porta de Entrada/Saída

Cada dispositivo possui um endereço de porta.  O endereço é uma localização da
memória usada pelo computador para enviar dados ao dispositivo e onde o
dispositivo envia dados ao computador.  Ao contrários da IRQ e DMA, o
dispositivo pode usar mais de uma porta de Entrada/Saída ou uma faixa de
endereços.  Por exemplo, uma placa de som padrão usa as portas 0x220, 0x330 e
0x388, respectivamente <literal>audio digital,
<literal>midi e <literal>opl3.


As placas de rede normalmente transferem grandes quantidades de dados, assim
ocupam uma faixa de endereços.  Uma NE2000, por exemplo, ocupa a faixa de
endereços 0x260 a 0x27F (0x260-0x27F).  O tamanho da faixa de endereços varia
de acordo com o tipo de dispositivo.


Os endereços de **I/O** em uso no sistema podem ser
visualizados com o comando <literal>cat /proc/ioports.


Endereços das portas de entrada/saída não podem ser compartilhados





 hardw-metodoscfg">###Hardwares configuráveis por jumpers, dip-switches, jumperless e Plug-and-Play.
 hardw-metodoscfg-jumpers">###Jumpers

Hardwares configuráveis por **jumpers** (pinos metálicos
protegidos por uma capa plástica) tem sua configuração alterada através da
colocação, retirada ou mudança de posição física do pino.  Este tipo de
hardware, antigamente presente em placas ISA e VESA, não é mais usado
atualmente devido a configuração Plug and Play de dispositivos PCI, PCI
express, etc.


As disposição dos jumpers são normalmente definidas em
**fechado/aberto** e **multi-posição**.  Na
disposição **fechado/aberto**, o jumper pode ou não ser
colocado, definindo a configuração do dispositivo:

<screen>
::|::


Esta disposição é facilmente encontrada na seleção de IRQ e I/O em placas de
fax-modem.


Na disposição **multi-posição**, os pinos de encaixe são
numerados de 1 a 3 (ou 1 a 4, 1 a 5, etc) e os pinos podem ou não ser colocados
na placa e a posição que são colocados também influencia os valores escolhidos
para o funcionamento do dispositivo (a posição 1-2 especificam um valor
enquanto 2-3 especificam outro).  A associação entre a posição dos jumpers e a
configuração desejada é feita consultando o mapa desenhado no circuito impresso
da placa ou o manual de instruções da placa.


A configuração de jumper através de multi-posição é normalmente usada em placas
mãe para definir a **freqüência de operação do barramento**, a
**freqüência de multiplicação** ou o **tipo do
processador**.


Se não possuir o mapa de configuração de sua placa e/ou o manual de instruções,
será necessário fazer um mapeamento manual da placa, mas para isto você
precisará conhecer detalhadamente a configuração de portas I/O, DMA, IRQ usadas
na máquina que será usada e anotar as diferenças obtidas através da modificação
da pinagem do dispositivo.  Isto não é fácil, mas técnicos de informática
experientes conhecerão as <literal>armadilhas encontradas pelo
mapeamento manual de placas e farão o esquema de configuração completo do
dispositivo, obtendo um excelente manual de instruções.  Nesta hora a
experiência conta mais que o uso de programas de diagnóstico.


Outra característica de hardwares configurados através de jumpers é que
raramente apresentam problemas de funcionamento, a não ser que seus parâmetros
como IRQ, DMA, ou I/O estejam em conflitos com outro dispositivo, mas isso não
é culpa do fabricante e nem mesmo do dispositivo...



 hardw-metodoscfg-dipswitche">###Dip-Switches

É a mesma coisa que os hardwares configuráveis por jumpers exceto que são
usados **dip-switches** no lugar de jumpers.  O
**dip-switches** é um conjunto de chaves numeradas que podem
ser colocadas para cima ou para baixo (como um disjuntor ou vários
interruptores **LIGA/DESLIGA** colocados um ao lado do outro)
para se modificar a configuração do dispositivo.



 hardw-metodoscfg-jumperless">###Jumperless (sem jumper)

Os hardwares **jumperless** não possuem jumpers e são
configurados através de um programa que acompanha a própria placa.  Neste
programa é escolhida a IRQ, DMA, I/O e a configuração é salva na própria placa
ou restaurada após cada inicialização por um programa carregado na memória.
Devido a configuração via software, se obtém uma configuração fixa com muito
mais facilidade do que via jumpers (por não haver a necessidade de se retirar a
placa).


A maioria das placas jumperless podem funcionar também como Plug-and-Play.
Existem muitas placas de rede, fax-modem, scanner jumperless no mercado.



 hardw-metodoscfg-plug-and-play">###Plug-and-Play

O **Plug-and-Play** é um protocolo que lê os valores de
operação disponíveis para a placa e permitem que o usuário possa especificar
facilmente qual será sua IRQ, DMA, I/O.  Hardwares PCI possuem configuração
Plug-and-Play nativa, registrando suas interrupções, portas e dma na tabela de
hardwares PCI do sistema.


A diferença em relação ao modo jumperless é que toda a configuração do hardware
(IRQ, DMA e I/O) é feita pelo kernel do <command>Linux, onde ele
passa a configuração detectada durante a inicialização do sistema para os
módulos carregados, garantindo o perfeito funcionamento do dispositivos e
evitando conflitos.  Na época de hardwares ISA e VESA, o programa
<command>isapnp era a preferencia para a configuração de placas ISA
Plug and Play.


Veja a próxima seção para entender como funciona o arquivo de configuração
<filename>isapnp.conf</filename> e assim poder ativar seu dispositivo
Plug-and-Play.





 hardw-findhw">###Listando as placas e outros hardwares em um computador

Administradores e técnicos ao configurar uma máquina precisarão saber quais os
hardwares ela possui, periféricos e até mesmo a revisão de dispositivos e clock
para configurar as coisas e ver a necessidade de atualizações de dispositivos
atuais.


Dispositivos PCI/AMR/CNR podem ser listados executando o comando <literal>cat
/proc/pci.  Outra forma de listar tais dispositivos é usando o
<command>lspci, se você precisa de mais detalhes como o mapeamento de
memória, use <literal>lspci -vv.


O mapeamento de memória de dispositivos podem ser mostrados com o comando
<literal>cat /proc/ioports, ou usando o comando
<command>lsdev.


O barramento USB e dispositivos conectados a ele podem ser listados com o
comando <command>lsusb ou com <literal>cat
/proc/bus/usb/devices.


Hardwares disponíveis na máquina, como placa mãe, clock multiplicador, discos,
placas diversas, versões e números seriais de dispositivos podem ser mostrados
através do comando <command>lshw.  Use <literal>lshw -html
para produzir a listagem em formato HTML, bem interessante para relatórios :-)



 hardw-conflitos">###Conflitos de hardware

Ocorre quando um ou mais dispositivos usam a mesma **IRQ**,
**I/O** ou **DMA**.  Um sistema com
configurações de hardware em conflito tem seu funcionamento instável,
travamentos constantes, mal funcionamento de um ou mais dispositivos e até
mesmo, em casos mais graves, a perda de dados.  Conflitos geralmente ocorriam
em placas ISA, VESA onde era necessário conhecer e usar uma tabela de valores
padrões para a configuração de periféricos (como a mostrada no inicio desse
capítulo).


Para resolver conflitos de hardware é necessário conhecer a configuração de
cada dispositivo em seu sistema.  Os comandos <literal>cat
/proc/interrupts, <literal>cat /proc/dma e <literal>cat
/proc/ioports podem ser úteis para se verificar as configurações
usadas.



 hard-barramento">###Barramento

O tipo de **slot** varia de acordo com o barramento usado no
sistema, que pode ser um(s) do(s) seguinte(s):

<variablelist>
<varlistentry>
<term>ISA 8 Bits
<listitem>

<literal>Industry Standard Architecture - É o padrão mais antigo,
encontrado em computadores PC/XT.



<varlistentry>
<term>ISA 16 Bits
<listitem>

Evolução do padrão ISA 8 Bits, possui um conector maior e permite a conexão de
placas de 8 bits.  Sua taxa de transferência chega a 2MB/s.



<varlistentry>
<term>VESA
<listitem>

<literal>Video Electronics Standard Association - É uma interface
feita inicialmente para placas de vídeo rápidas.  O barramento VESA é
basicamente um ISA com um encaixe extra no final.  Sua taxa de transferência
pode chegar a 132MB/s.



<varlistentry>
<term>EISA
<listitem>

<literal>Enhanced Industry Standard Architecture - É um barramento
mais encontrado em servidores.  Tem a capacidade de bus mastering, que
possibilita a comunicação das placas sem a interferência da CPU.



<varlistentry>
<term>MCA
<listitem>

<literal>Micro Channel Architecture - Barramento 32 bits proprietário
da IBM.  Você não pode usar placas ISA nele, possui a característica de bus
mastering, mas pode procurar por dispositivos conectados a ele, procurando
configuração automática.


Este barramento estava presente no PS/1 e PS/2, hoje não é mais usado.



<varlistentry>
<term>PCI
<listitem>

<literal>Peripheral Component Interconnect - É outro barramento
rápido produzido pela Intel com a mesma velocidade que o VESA.  O barramento
possui um chipset de controle que faz a comunicação entre os slots PCI e o
processador.  O barramento se configura automaticamente (através do
Plug-and-Play).  O PCI é o barramento mais usado por Pentiums e está se
tornando uma padrão no PC.



<varlistentry>
<term>PCI Express
<listitem>

<literal>Peripheral Component Interconnect Express - Identico ao
barramento PCI, funcionando nativamente no clock de 64 bits.



<varlistentry>
<term>AGP
<listitem>

<literal>Accelerated Graphics Port - É um novo barramento criado
exclusivamente para a ligação de placas de video.  É um slot marrom (em sua
maioria) que fica mais separado do ponto de fixação das placas no chassis
(comparado ao PCI).  Estas placas permitem obter um desempenho elevado de vídeo
se comparado as placas onboards com memória compartilhada e mesmo PCI externas.
O consumo de potência em placas AGP x4 podem chegar até a 100W, portanto é
importante dimensionar bem o sistema e ter certeza que a fonte de alimentação
pode trabalhar com folga.



<varlistentry>
<term>PCMCIA
<listitem>

<literal>Personal Computer Memory Card International Association - É
um slot especial usado para conexões de placas externas (normalmente revestivas
de plástico) e chamadas de **cartões PCMCIA**.  Estes cartões
podem adicionar mais memória ao sistema, conter um fax-modem, placa de rede,
disco rígido, etc.


Os cartões PCMCIA são divididos em 3 tipos:

<variablelist>
<varlistentry>
<term><literal>Tipo 1
<listitem>

Tem a espessura de 3.3 milímetros, e podem conter mais memória RAM ou memória
Flash.



<varlistentry>
<term><literal>Tipo 2
<listitem>

Tem a espessura de 5 milímetros e capacidade de operações I/O.  É um tipo usado
para placas de fax-modem, rede, som.  Computadores que aceitam cartões PCMCIA
do tipo 2, mantém a compatibilidade com o tipo 1.



<varlistentry>
<term><literal>Tipo 3
<listitem>

Tem a espessura de 10.5 milímetros e normalmente usado para discos rígidos
PCMCIA.  Slots PCMCIA do tipo 3 mantém a compatibilidade com o tipo 2 e 1.



</variablelist>


<varlistentry>
<term>AMR
<listitem>

<literal>Audio Modem Raise - Pequeno barramento criado pela Intel
para a conexão de placas de som e modem.  Placas de som e modem AMR usam o HSP
(host signal processor) e são como as Placas on-board e todo o processamento é
feito pela CPU do computador (veja detalhes em <xref linkend="hard-onoffboard"e <xref linkend="hard-forwindows"/>.


Sua vantagem é o preço: um modem ou placa de som AMR custa em torno de R$
25,00.



<varlistentry>
<term>CNR
<listitem>

<literal>Communication and Networking Rise - Pequeno barramento
criado pela Intel para a conexão de placas de som, modens e placas de rede.
Este é um pequenino slot marrom que é localizado no ponto de fixação das placas
no chassis do gabinete.  Elas são como as Placas on-board e todo o
processamento é feito pela CPU do computador (veja detalhes em <xref linkend="hard-onoffboard"e <xref linkend="hard-forwindows"/>.



</variablelist>


 hard-onoffboard">###Placas on-board / off-board

Placas **on-board** são embutidas na placa mãe
(**motherboard**).  Placas **off-board** são
placas externas encaixadas nos slots de expansão da placa mãe.


No inicio da era do PC/XT todos as placas eram embutidas na placa mãe (na época
eram somente a placa de vídeo e controladora).  Com o surgimento do padrão AT,
diversas empresas de informática desenvolveram dispositivos concorrentes e
assim o usuário tinha a liberdade de escolha de qual dispositivo colocar em sua
placa mãe (ou o mais barato ou o de melhor qualidade e desempenho), isto
permitiu a adição de periféricos de qualidade sem romper com seu orçamento
pessoal (comprando uma placa de som, depois uma de fax-modem, placa de vídeo
melhor, etc).


Atualmente parece que voltamos ao ponto de partida e tudo vem embutido na placa
mãe (**on-board**) e o usuário não tem como escolher qual
dispositivo usar em seu computador.  É muito difícil (praticamente impossível)
encontrar uma placa mãe que satisfaça completamente as necessidades do usuário
ou recomendações de um bom técnico de informática (a não ser que seja um
técnico experiente e encontre alguma alternativa).


Certamente o único dispositivo que funciona melhor se embutido na placa mãe é a
**placa controladora de periféricos**.  Esta placa é usada
para se conectar unidades de disquete, discos rígidos, CD-ROM, portas seriais,
paralelas, joystick ao computador.  Os HDs conectados em uma controladora
embutida conseguem ter um desempenho muito maior do que em placas conectadas
externamente, sem causar nenhum tipo de problema.


Hardwares embutidos na placa mãe (como fax-modem, vídeo, som) são em média 30%
mais baratos que os vendidos separadamente mas quase sempre são usados
dispositivos de baixo desempenho e qualidade para reduzir o preço da placa mãe
e quase sempre usados hardwares <literal>For Windows.


Hoje em dia por causa do preço da placa mãe, é comum encontrar pessoas que
verificam somente o preço e sequer procuram saber ou conhecem a qualidade das
placas embutidas na placa mãe.  Pior ainda é encontrar vendedores despreparados
que sequer sabem explicar o porque que uma placa de som Sound Blaster 128 é
mais cara que uma de modelo genérico...


Geralmente dispositivos on-board trazem problemas caso tal dispositivo queime e
geralmente é colocado um hardware de baixa qualidade para baratear o custo de
placas mãe, que na maioria das vezes também oferece grande dificuldade para ser
configurada no <command>Linux.


Outro periférico que traz problemas e carga para o processador é o fax-modem
for Windows, HSP, AMR, micromodem, etc.  utilizando o processador do sistema
para realizar seu trabalho e algumas vezes não trazem nem mesmo o chip UART.
Isso resulta em perda de qualidade na conexão e maior consumo telefônico.


Se você estiver em uma situação destas, certamente os computadores de menor
potência e com hardwares inteligentes (que possuem seus próprios chips de
controle e processamento) não terão o desempenho comprometido.  O preço pode
ser maior mas você estará pagando por um dispositivo de melhor qualidade e que
certamente trará benefícios a você e ao seu sistema.


Consulte um técnico em informática experiente para te indicar uma placa mãe de
bom preço e de qualidade.  É muito comum encontrar falta de profissionalismo em
pessoas que não sabem distinguir as características, funções e vantagens entre
uma placa de boa qualidade e um hardware for Windows a não ser o preço mais
barato.



 hard-forwindows">###Hardwares específicos ou "For Windows"

Esta seção foi retirada do manual de instalação da Debian GNU/Linux.  Uma
tendência que perturba é a proliferação de Modens e impressoras específicos
para Windows.  Em muitos casos estes são especialmente fabricados para operar
com o Sistema Operacional Microsoft Windows e costumam ter a legenda
<literal>WinModem, <literal>for Windows, ou <literal>Feito
especialmente para computadores baseados no Windows.


Geralmente estes dispositivos são feitos retirando os processadores embutidos
daquele hardware e o trabalho deles são feitos por drivers do Windows que são
executados pelo processador principal do computador.  Esta estratégia torna o
hardware menos caro, mas o que é poupado não é passado para o usuário e este
hardware pode até mesmo ser mais caro quanto dispositivos equivalentes que
possuem inteligência embutida.


Você deve evitar o hardware baseado no Windows por duas razões:

<orderedlist numeration="arabic">
<listitem>

O primeiro é que aqueles fabricantes não tornam os recursos disponíveis para
criar um driver para Linux.  Geralmente, o hardware e a interface de software
para o dispositivo é proprietária, e a documentação não é disponível sem o
acordo de não revelação, se ele estiver disponível.  Isto impede seu uso como
software livre, desde que os escritores de software grátis descubram o código
fonte destes programas.


<listitem>

A segunda razão é que quando estes dispositivos tem os processadores embutidos
removidos, o sistema operacional deve fazer o trabalho dos processadores
embutidos, freqüentemente em prioridade de tempo real, e assim a CPU não esta
disponível para executar programas enquanto ela esta controlando estes
dispositivos.


Assim o usuário típico do Windows não obtém um multi-processamento tão
intensivo como um usuário do Linux, o fabricante espera que aquele usuário do
Windows simplesmente não note a carga de trabalho que este hardware põe naquela
CPU.  No entanto, qualquer sistema operacional de multi-processamento, até
mesmo Windows 9X, XP e Vista, são prejudicados quando fabricantes de
periféricos retiram o processador embutido de suas placas e colocam o
processamento do hardware na CPU.


</orderedlist>

Você pode ajudar a reverter esta situação encorajando estes fabricantes a
lançarem a documentação e outros recursos necessários para nós desenvolvermos
drivers para estes hardwares, mas a melhor estratégia é simplesmente evitar
estes tipos de hardwares até que ele esteja listado no HOWTO de hardwares
compatíveis com Linux.


Note que hoje já existem muitos drivers para WinModems e outros hardwares for
Windows para o Linux.  Veja a lista de hardwares compatíveis no HARDWARE-HOWTO
ou procure o driver no site do fabricante de seu dispositivo.  Mesmo assim a
dica é evitar hardwares for Windows e comprar hardwares inteligentes onde cada
um faz sua função sem carregar a CPU.



 s3.10">###Dispositivos específicos para GNU/Linux

Esta seção foi retirada do manual de instalação da Debian GNU/Linux.  Existem
diversos vendedores, agora, que vendem sistemas com a <command>Debian
ou outra distribuição do GNU/Linux pré-instaladas.  Você pode pagar mais para
ter este privilégio, mas compra um nível de paz de mente, desde então você pode
ter certeza que seu hardware é bem compatível com GNU/Linux.  Praticamente
todas as placas que possuem processadores próprios funcionam sem nenhum
problema no Linux (algumas placas da <literal>Turtle Beach e
<literal>mwave tem suporte de som limitado).


Se você tiver que comprar uma máquina com Windows instalado, leia
cuidadosamente a licença que acompanha o Windows; você pode rejeitar a licença
e obter um desconto de seu vendedor.


Se não estiver comprando um computador com <command>GNU/Linux
instalado, ou até mesmo um computador usado, é importante verificar se os
hardwares existentes são suportados pelo kernel do
<command>GNU/Linux.  Verifique se seu hardware é listado no
**Hardware Compatibility HOWTO**, na documentação do código
fonte do kernel no diretório <filename>Documentation/sound</filename> ou
consulte um técnico de <command>GNU/Linux experiente.


Deixe seu vendedor (se conhecer) saber que o que está comprando é para um
sistema <command>GNU/Linux.  Desta forma isto servirá de experiência
para que ele poderá recomendar o mesmo dispositivo a outras pessoas que
procuram bons dispositivos para sistemas <command>GNU/Linux.  Apóie
vendedores de hardwares amigos do <command>GNU/Linux.



 hardw-cfgdisp">###Configurações de Dispositivos

As seções abaixo explicam como fazer configurações em dispositivos diversos no
sistema <command>Linux como placas de rede, som, gravador de CD entre
outras.

 hardw-cfgdisp-rede">###Configurando uma placa de rede

Para configurar sua placa de rede no <command>Linux siga os passos a
seguir:

<orderedlist numeration="arabic">
<listitem>

Identifique se sua placa de rede é ISA ou PCI.  Caso seja ISA, pode ser preciso
alterar a configuração de jumpers ou plug-and-play, evitando conflitos de
hardware ou o não funcionamento da placa (veja como configura-la em <xref linkend="hardw-metodoscfg"/>.


<listitem>

Identifique a marca/modelo de sua placa.  O programa <command>lshw é
útil para isto.  Caso sua placa seja PCI ou CNR, execute o comando
<command>lspci e veja a linha "Ethernet".


Em último caso, abra a máquina e procure a marca na própria placa.  Quase todos
os fabricantes colocam a marca da placa no próprio circuito impresso ou no CI
principal da placa (normalmente é o maior).


<listitem>

Depois de identificar a placa, será preciso carregar o módulo correspondente
para ser usada no <command>Linux.  Em algumas instalações padrões o
suporte já pode estar embutido no kernel, neste caso, você poderá pular este
passo.


Para carregar um módulo, digite o comando <literal>modprobe modulo
(Veja <xref linkend="kern-modprobe"/>) .  Em placas ISA, geralmente é preciso
passar a IRQ e porta de I/O como argumentos para alocar os recursos
corretamente.  O <command>modprobe tentará auto-detectar a
configuração em placas ISA, mas ela poderá falhar por algum motivo.  Por
exemplo, para uma NE 2000: <literal>modprobe ne io=0x300 irq=10.


Para evitar a digitação destes parâmetros toda vez que a máquina for iniciada é
recomendável coloca-lo no arquivo <filename>/etc/modules.conf</filename> da
seguinte forma:

<screen>
options ne io=0x300 irq=10


A partir de agora, você pode carregar o módulo de sua placa NE 2000 apenas com
o comando <literal>modprobe ne.  O parâmetro <literal>io=0x300
irq=10 será automaticamente adicionado.  Em sistemas
<command>Debian, o local correto para colocar as opções de um módulo
é em arquivos separados localizados dentro de
<filename>/etc/modutils</filename>.  Crie um arquivo chamado
<filename>/etc/modutils/ne</filename> e coloque a linha:

<screen>
options ne io=0x300 irq=10


Depois disso, execute o comando <literal>update-modules para o
sistema gerar um novo arquivo <filename>/etc/modules.conf</filename> com todos
os módulos de <filename>/etc/modutils</filename> e substituir o anterior.


<listitem>

Após carregar o módulo de sua placa de rede, resta apenas configurar seus
parâmetros de rede para coloca-la em rede.  Veja <xref linkend="rede-interfaces-c"/>.


</orderedlist>


 hardw-cfgdisp-som">###Configurando uma placa de SOM no Linux

A configuração de dispositivos de audio no Linux é simples, bastando carregar o
módulo da placa e ajustar o mixer.  Atualmente existem 2 padrões de som no
sistema Linux: OSS (Open Sound System) e ALSA (Advanced Linux Sound
Architecture).


O OSS foi o primeiro padrão adotado em sistemas <command>Linux, que
tinha como grande limitação a dificuldade em usar diversas placas e a
impossibilidade dos programas utilizaram ao mesmo tempo a placa de som.  O ALSA
é mais novo, suporta full duplex e outros recursos adicionais, além de manter a
compatibilidade com OSS.  O ALSA é um padrão mais moderno e garante mais
performance para a CPU da máquina, principalmente para a exibição de vídeos,
etc.

 hardw-cfgdisp-som-oss">###Configurando uma placa de som usando o padrão OSS

OSS é o presente por padrão desde que o suporte a som foi incluído no kernel.
Para configurar uma placa de som para usar este sistema de som, primeiro
compile seu kernel com o suporte ao módulo de sua placa de som.  Caso seja uma
placa ISA, você provavelmente terá que habilitar a seção "Open Sound System"
para ver as opções disponíveis (entre elas, a Sound Blaster e compatíveis).
Uma olhada na ajuda de cada módulo deve ajuda-lo a identificar quais placas
cada opção do kernel suporta.


Caso seu kernel seja o padrão de uma distribuição <command>Linux,
provavelmente terá o suporte a todas as placas de som possíveis.  Siga o passo
a passo abaixo para configurar sua placa de som no sistema:

<orderedlist numeration="arabic">
<listitem>

Primeiro descubra se sua placa de som é ISA.  Caso seja, verifique se os seus
recursos estão alocados corretamente (veja <xref linkend="hardw-conflitos"/>).
Caso seja PCI, AMR, execute o comando <command>lspci, procure pela
linha "Multimedia" e veja o nome da placa.  Você também poderá executar o
comando <command>lshw para descobrir qual placa você possui (veja
<xref linkend="hardw-findhw"/>) para detalhes.


<listitem>

Carregue o módulo da placa de som com o comando <literal>modprobe
módulo (veja <xref linkend="kern-modprobe"/>).  Na
<command>Debian, você pode executar o comando
<command>modconf para navegar visualmente entre os módulos
disponíveis e carregar os módulos necessários.


Algumas placas (principalmente ISA) requerem que seja especificado o recurso de
hardware sejam passados para seu módulo, ou simplesmente você quer especificar
isto para manter o uso de hardware sobre seu controle.  Alguns dos parâmetros
mais usados em placas Sound Blaster são os seguintes:

<screen>
modprobe sb io=0x220 irq=5 dma=1 dma16=5 mpu_io=0x330


Para evitar ter que passar estes parâmetros todas as vezes para o módulo, você
poderá coloca-los no arquivo <filename>/etc/modules.conf</filename> da seguinte
forma:

<screen>
options sb io=0x220 irq=5 dma=1 dma16=5 mpu_io=0x330


Assim, quando der o comando <command>modprobe sb ele será carregado
com as opções acima.  Na distribuição <command>Debian, você deverá
criar um arquivo chamado <filename>/etc/modutils/sb</filename> contendo a linha
acima, depois execute o <command>update-modules para "juntar" todos
os arquivos do <filename>/etc/modutils</filename> e criar o
<filename>/etc/modules.conf</filename>.


<listitem>

Após carregar o módulo correto de sua placa de som, seu sistema de som deverá
estar funcionando.  Se você utiliza uma distribuição <command>Linux,
os dispositivos de som como <filename>/dev/audio</filename>,
<filename>/dev/dsp</filename>, <filename>/dev/mixer</filename> estarão criados
e então poderá passar para o próximo passo.  Caso não existam, entre no
diretório <filename>/dev</filename> e execute o comando <literal>MAKEDEV
audio.


<listitem>

O próximo passo consiste em instalar um programa para controle de volume,
tonalidade e outros recursos de sua placa de som.  O recomendado é o
<command>aumix por ser simples, pequeno e funcional, e permitindo
restaurar os valores dos níveis de volumes na inicialização (isso evita que
tenha que ajustar o volume toda vez que iniciar o sistema).


Caso o <command>aumix apareça na tela, sua placa de som já está
funcionando!  Caso acesse o sistema como usuário, não se esqueça de adicionar
seu usuário ao grupo audio para ter permissão de usar os dispositivos de som:
<literal>adduser usuario audio .


</orderedlist>




 hardw-cfgdisp-cdwritter">###Configurando um gravador de CD/DVD no Linux

Caso seu gravador seja IDE, veja <xref linkend="hardw-cfgdisp-cdwritter-ide"/>
caso seja um autêntico gravador com barramento SCSI, vá até <xref linkend="hardw-cfgdisp-cdwritter-scsi"/>.

 hardw-cfgdisp-cdwritter-ide">###Configurando o suporte a um gravador IDE

Caso tenha um gravador IDE e use um kernel 2.6 ou superior, não é necessário
fazer qualquer configuração, pois seu gravador já está pronto para ser usado,
sendo acessado através de seu dispositivo tradicional
(<filename>/dev/hdc</filename>, <filename>/dev/hdd</filename>, etc).  De
qualquer forma, você poderá realizar a configuração da unidade IDE com emulação
SCSI, assim como utilizava no kernel 2.4 e inferiores seguindo as instruções
abaixo.


Para configurar seu gravador de CD/DVD IDE para ser usado no
<command>Linux usando o método para o kernel 2.4 e inferiores, siga
os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

Tenha certeza que compilou o suporte as seguintes características no kernel:

<screen>
Em "ATA/IDE/MFM/RLL support" marque as opções:
* Include IDE/ATAPI CDROM support
* SCSI emulation support

Depois em "SCSI support" marque as opções:
* SCSI support
M SCSI CD-ROM Support
M SCSI Generic Support


As opções marcadas como "*" serão embutidas no kernel e as "M" como módulos.
Note que ambas as opções "IDE/ATAPI CDROM" e "SCSI Emulation" foram marcadas
como embutidas.  Isto faz com que o driver ATAPI tenha prioridade em cima do
SCSI, mas vou explicar mais adiante como dizer para o kernel para carregar o
suporte a SCSI para determinada unidade.  Isto é útil quando temos mais de 1
unidade de CD IDE no sistema e queremos configurar somente o gravador para
SCSI, pois alguns aplicativos antigos não se comunicam direito tanto com
gravadores SCSI como emulados.


Você também pode marcar somente a opção "SCSI Emulation" para que sua(s)
unidade(s) seja(m) automaticamente emulada(s) como SCSI.  Caso tenha usado esta
técnica, vá até a seção <xref linkend="hardw-cfgdisp-cdwritter-teste"/>.


<listitem>

O próximo passo é identificar o dispositivo de CD/DVD.  Isto é feito através do
comando <literal>dmesg.  Supondo que sua unidade de CD é "hdc"
(primeiro disco na segunda controladora IDE) e que compilou ambos o suporte a
"IDE ATAPI" e "SCSI emulation" no kernel, adicione o argumento "hdc=ide-scsi"
no <filename>/etc/lilo.conf</filename> ou no <command>grub:

<screen>
# Lilo
vmlinuz=/vmlinuz
append="hdc=ide-scsi"


</orderedlist>

Isto diz para o kernel que a unidade "hdc" usará emulação "ide-scsi".  Caso
tenha outras unidades de CD no sistema, estas ainda utilização ATAPI como
protocolo de comunicação padrão.  Execute o <command>lilo para gerar
novamente o setor de inicialização com as modificações e reinicie o computador.


**OBS:** Cuidado ao colocar um disco rígido IDE
como <filename>hdc</filename>!  A linha <literal>hdc=ide-scsi deverá
ser retirada, caso contrário, seu disco rígido não será detectado.


Agora, siga até <xref linkend="hardw-cfgdisp-cdwritter-teste"/>.



 hardw-cfgdisp-cdwritter-scsi">###Configurando o suporte a um gravador SCSI

Caso tenha um autentico gravador SCSI, não será preciso fazer qualquer
configuração de emulação, a unidade estará pronta para ser usada, desde que seu
suporte esteja no kernel.  As seguintes opções do kernel são necessárias para
funcionamento de gravadores SCSI:

<screen>
Depois em "SCSI support" marque as opções:
* SCSI support
M SCSI CD-ROM Support
M SCSI Generic Support


Além disso, deve ser adicionado o suporte EMBUTIDO no kernel a sua controladora
SCSI.  Se o seu disco rígido também é SCSI, e seu CD está ligado na mesma
controladora SCSI, ela já está funcionando e você poderá seguir para o passo
<xref linkend="hardw-cfgdisp-cdwritter-teste"/>.  Caso contrário carregue o
suporte da sua placa adaptadora SCSI antes de seguir para este passo.



 hardw-cfgdisp-cdwritter-teste">###Testando o funcionamento

Para testar se o seu gravador, instale o pacote <systemitem role="package">wodim</systemitem> e execute o comando: <literal>wodim
-scanbus para verificar se sua unidade de CD-ROM é detectada.


Você deverá ver uma linha como:

<screen>
scsibus0:
    0,0,0     0) 'CREATIVE' 'CD-RW RWXXXX   ' '1.00' Removable CD-ROM
    0,1,0     1) *
    0,2,0     2) *


O que significa que sua unidade foi reconhecida perfeitamente pelo sistema e já
pode ser usada para gravação.  Vá até a seção <xref linkend="tasks-cdwriting"/>
para aprender como gravar CDs no <command>Linux.  Note que gravadores
IDE nativos, não são listados com esse comando.





 hardw-cfgdisp-apm">###Configurando o gerenciamento de energia usando o APM

O APM (**Advanced Power Management** - **Gerenciamento
Avançado de Energia**) permite que sistemas gerenciem características
relacionadas com o uso e consumo de energia do computador.  Ele opera a nível
de BIOS e tenta reduzir o consumo de energia de várias formas quando o sistema
não estiver em uso (como reduzindo o clock da CPU, desligar o HD, desligar o
monitor, etc.).


O uso de advanced power management também permite que computadores com fonte de
alimentação ATX sejam desligados automaticamente quando você executa o comando
<command>halt.  Caso sua máquina tenha suporte a
**ACPI**, este deverá ser usado como preferência ao invés do
APM por ter recursos mais sofisticados (veja <xref linkend="hardw-cfgdisp-acpi"/>).


Para ativar o suporte a APM no <command>Linux, compile seu kernel com
o suporte embutido a APM e também a "Advanced Power Management" (senão sua
máquina não desligará sozinha no halt).  Caso deseje compilar como módulo,
basta depois carregar o módulo <filename>apm</filename> adicionando no arquivo
<filename>/etc/modules</filename>.  Depois disso instale o daemon
<command>apmd para gerenciar as características deste recurso no
sistema.


Você pode desativar o uso de APM de 3 formas: removendo seu suporte do kernel,
passando o argumento <literal>apm=off (quando compilado estaticamente
no kernel) ou removendo o nome do módulo do arquivo
<filename>/etc/modules</filename> (quando compilado como módulo).  Depois disso
remova o daemon <command>apmd.



 hardw-cfgdisp-acpi">###Configurando o gerenciamento de energia usando ACPI

O ACPI (**Advanced Configuration and Power Interface** -
**Interface de Configuração e Gerenciamento de Energia
Avançado**) é uma camada de gerenciamento de energia que opera a nível
de sistema operacional.  Apresenta os mesmos recursos que o APM, e outros como
o desligamento da máquina por teclas especiais de teclado, controle de brilho e
contraste de notebooks, suspend para RAM, suspend para disco, redução de
velocidade de CPU manualmente, monitoramento de periféricos, temperatura,
hardwares, etc.


Desta forma, o ACPI varia de sistema para sistema em questões relacionadas com
suporte a recursos especiais, estes dados são armazenados em tabelas chamadas
DSDT.  O <command>Linux inclui suporte a recursos ACPI genéricos
entre placas mãe, recursos específicos devem ser extraídos diretamente da BIOS
e disassemblados manualmente para a construção de um kernel com suporte
específico a tabela DSDT do hardware (não falarei das formas de se fazer disso
aqui, somente do suporte genérico).


Quanto mais nova a versão do kernel, maiores as chances do seu hardware ser
suportado plenamente pelo ACPI, principalmente no caso de notebooks.  Para
compilar estaticamente, marque com <literal>Y a opção ACPI, depois
marque os módulos que você quer que ele monitore: <literal>button
(botão power), <literal>fan (ventoinhas), etc.  Se compilou como
módulo, adicione o nome do módulo <literal>acpi no arquivo
<filename>/etc/modules</filename>.  Não há problema em compilar também o
suporte a APM, pois não causará problemas com um kernel com ACPI também
compilado.


Caso não saiba quais módulos ACPI seu sistema aceita, marque o suporte a todos
e carregue-os.  Após isto, entre no diretório <filename>/proc/acpi</filename> e
de um <literal>ls entrando nos diretórios e vendo se existem arquivos
dentro deles.  Remova o módulo correspondente daqueles que não tiver conteúdo.


Após isto, instale o daemon <command>acpid e configure-o para
monitorar algumas características do seu sistema.  Por padrão o
<command>acpid monitora o botão POWER, assim se você pressionar o
power, seu sistema entrará automaticamente em run-level 0, fechando todos os
processos e desligando sua máquina.


O suporte a ACPI pode ser desativado de 3 formas: Removendo seu suporte do
kernel, passando o argumento <literal>acpi=off ao kernel (caso esteja
compilado estaticamente) ou removendo o módulo de
<filename>/etc/modules</filename> (caso tenha compilado como módulo.  Após
isto, remova o daemon <command>acpid do seu sistema.



 hardw-cfgdisp-wol">###Ativando WakeUP on Lan

Algumas placas mãe ATX possuem suporte a este interessante recurso, que permite
sua máquina ser ligada através de uma rede.  Isto é feito enviando-se uma
seqüência especial de pacotes diretamente para o MAC (endereço físico) da placa
de rede usando um programa especial.


Para usar este recurso, seu sistema deverá ter as seguintes características:

<itemizedlist>
<listitem>

Placa mãe ATX


<listitem>

Fonte de alimentação ATX compatível com o padrão 2.0, com fornecimento de pelo
menos 720ma de corrente na saída +3v.


<listitem>

Placa de rede com suporte a WakeUP-on-Lan (WOL), você poderá confirmar isto
vendo um conector branco de 3 terminais instalado na placa que é o local onde o
cabo wake-up é conectado.


<listitem>

Suporte na BIOS também deverá ter a opção para WakeUP-on-Lan.




Com todos esses ítens existentes, instale em uma máquina da rede o pacote
<systemitem role="package">etherwake</systemitem>.  Depois disso, pegue o MAC
address a placa de rede da máquina que tem o wakeup on lan e na máquina da rede
onde instalou o pacote execute o seguinte comando:

<screen>
ether-wake AA:BB:CC:DD:EE:FF


Onde <literal>AA:BB:CC:DD:EE:FF é o endereço MAC da placa de rede.  A
máquina deverá ligar e realizar o procedimento padrão de POST normalmente.


Algumas das situações onde o WOL não funciona é quando sua rede é controlada
por Switches (devido a natureza de funcionamento deste equipamentos) ou caso
esteja atrás de um roteador que não faz proxy arp.





 hard-aterram">###Aterramento

O aterramento correto da instalação elétrica é **essencial**
para garantir a proteção de seu microcomputador (e outros aparelhos que
requerem isto).  Muitos usuários simplesmente removem o pino central da tomada
de seu computador, ou ligam o terra junto ao neutro da rede elétrica, isto é
errado e pode trazer sérias conseqüências.  O computador possui componentes
sensíveis que geram descargas estáticas durante seu funcionamento (fonte,
discos, placas, etc), estas descargas e ruídos são absorvidas pelo sistema de
aterramento (que é ligado no gabinete do computador e outros componentes
internos).  Sem aterramento o seu gabinete passará a dar choques elétricos
(teste com uma chave de testes, ela acenderá indicando a circulação de corrente
elétrica) e a corrente acumulada poderá queimar componentes internos sensíveis
(placa mãe, HD, memórias, placas expansoras).


A ligação do terra ao neutro da rede é menos perigosa em condições normais, mas
se um raio cair na rede elétrica as conseqüências poderão ser piores.  Mesmo a
rede de iluminação pública tendo aterramento em cada poste isto pode não ser o
suficiente para reduzir a carga de um raio que caia nas proximidades.


O sistema de aterramento residencial para PC deve ser feito com uma estaca de
cobre com no mínimo 2 metros de altura.  O cobre é um ótimo condutor de
eletricidade, perdendo somente para a prata (veja <xref linkend="hard-aterram-condut"/>).  Cave um buraco no solo com a ajuda de uma
cavadeira (hehe, nunca ouviu falar nisso?  :-), se estiver com dificuldades
para cavar por causa de solo ressecado, molhe a terra para facilitar as coisas.
Com a estaca enterrada, prenda um cabo elétrico em sua extremidade.


O ideal para testar este sistema de aterramento seria ter um equipamento
chamado <literal>terrômetro (medidor de aterramento), mas
utilizaremos 2 alternativas mais acessíveis:

<itemizedlist>
<listitem>

Ligue uma lâmpada incandescente de 100W em um bocal com uma ponta ligada na
extremidade positiva da rede elétrica (fase) e a outra ponta no fio da barra de
cobre.  O aterramento está bem feito quando a lâmpada acender quase em sua
potência total.  Ligue o fio do aterramento no pino central da tomada de seu
computador.


**OBS:** Cuidado para não tomar um baita choque
durante esta operação em alguns casos pode ser fatal.  Utilize sandalhas ou
sapatos de borracha (materiais isolantes) isto evitará tomar o choque caso
aconteça.


<listitem>

Ligue a outra extremidade do fio que vem da barra de cobre no pino central da
tomada de seu computador e ligue-o.  Consiga um multímetro (analógico ou
digital) e coloque para medir em escala DC 10V.  Coloque a ponta negativa
(preta) no **neutro** da rede elétrica e encoste a ponta
positiva (vermelha) no gabinete de seu computador.  O aterramento estará
aprovado caso o valor medido seja de no máximo 2.5 volts.




Caso algo ocorra errado, cheque novamente os passos acima.  Se desconfiar das
condições do solo, use uma barra maior ou ligue 2 barras de cobre juntas.

 hard-aterram-condut">###Condutores de eletricidade

A tabela abaixo está classificada em ordem do material que possui melhor
condução de eletricidade (elétrons com circulaçãos livres) baseada no fator
mm2/m.  (da mais condutora para a menos condutora).

<orderedlist numeration="arabic">
<listitem>

Prata - 0,0164


<listitem>

Cobre - 0,0172


<listitem>

Ouro - 0,0230


<listitem>

Alumínio - 0,0283


<listitem>

Zinco - 0,0600


<listitem>

Platina - 0,0950


<listitem>

Ferro - 0,1200


<listitem>

Chumbo - 0,2100


<listitem>

mercúrio - 0,9680


</orderedlist>




 hard-tomadas">###Tomadas

As tomadas elétricas de 127V ou 220V AC 60Hz de três pinos, pelas normas
técnicas da ABNT, no.  ABNT 6147 devem ficar distantes no máximo a 1,5 metro
dos equipamentos e com terceiro pino ligado à terra.  É interessante que a
tensão das tomadas esteja identificada nas mesmas, em caso de mais de uma
voltagem fornecida no local, evitando a queima de equipamentos.


Segue abaixo um exemplo de tomada fêmea e a recomendação para sua montagem.
Note que a entrada para o pino terra é voltado para cima, pois o caimento dos
fios da maioria dos equipamentos fabricados estarão desta forma voltados para
baixo.

<screen>
               127v                              220v
           +-----------+                     +-----------+
 Terra  ---+----(_)    |           Terra  ---+----(_)    |
           |   _   _   |                     |   _   _   |
           | _| | | |_ |                     | _| | | |_ |
 Fase   ---+(_  | |  _)+--- Neutro   Fase ---+(_  | |  _)+--- Fase
           |  |_| |_|  |                     |  |_| |_|  |
           |     _     |                     |     _     |
           +-----------+                     +-----------+


Como comentando anteriormente, não utilize como ponto de terra os sistemas de
aterramento das companhias de eletricidade, telefonia, ar condicionado e
sistema de pára-raios.



 hard-descestat">###Descargas estáticas

É a energia que se acumula durante o choque das moléculas de ar seco ou atrito
com outros objetos.  Pode acontecer de em dias secos você tomar um "choque" ao
abrir seu carro ou tocar em algum objeto metálico, isto é uma descarga
estática.  Na realidade você não tomou um choque, ao tocar em um objeto
metálico esta energia é descarregada violentamente.  Esta energia pode chegar
na ordem de 5 mil volts quando acumulada (assustador não?).


É por este motivo que caminhões que transportam combustível
<literal>arrastam uma corrente no chão, esta corrente funciona como
um aterramento (veja <xref linkend="hard-aterram"/>) eliminando descargas
estáticas que possam gerar faíscas e causar um desastre.  Pulseiras, cordões,
objetos metálicos podem ser usados para eliminar descargas estáticas de
pessoas.  O contato freqüente com o solo é um método muito útil.  Existem casos
em que um colar salvou a vida de pessoas atingidas por raio, justamente pelas
explicações acima.  O colar derrete com a drenagem da eletricidade do raio mas
a pessoa tem mais chances de sair viva.


Em indivíduos realmente sensíveis, uma chapinha de metal pode ser colocada no
sapato fazendo contato com o calcanhar drenando constantemente estas descargas,
isto é eficaz e bem melhor que sair arrastando correntes por ai :-)


Se você trabalha com hardwares ou é apenas mais um fuçador de PCs, agora você
entenderá porque é recomendável sempre tocar em partes metálicas do computador
antes de mexer em qualquer placa e porque aquele seu amigo disse que a placa
dele queimou depois que resolveu limpar seus contatos.



 hard-perf">###Melhoria de performance
 hard-perf-part">###Particionamento

Para um melhor desempenho, os dados que são solicitados constantemente deverão
ser armazenados em uma partição no inicio do disco rígido.  Esta área é a mais
rápida e checa a ser 60% mais rápida que o final do HD (em alguns modelos).  Em
especial, a partição de boot, swap e binários do sistema poderão ser
armazenados nesta partição para aumentar a velocidade da carga de programas e
não prejudicar a performance do sistema quando o uso da partição de troca
(swap) for necessária.


Em discos rígidos grandes (6GB ou maiores) é recomendável criar no mínimo uma
partição pequena para <filename>/boot</filename>, outra para
<filename>/</filename>, outra para <literal>swap e outra para
<filename>/usr</filename>.  Ficando distribuídas da seguinte maneira no disco
rígido:

<screen>
BBRRRRRRRRRRRRRRRRRRRRR
RRRRRRRRRRRRRRRRRRRRRRR
SSSSSSSSSSUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU
UUUUUUUUUUUUUUUUUUUUUUU

B - /boot
R - Raíz /
S - Swap
U - /usr


Mas a swap não ficaria ainda mais rápida sendo a primeira partição no disco?
Sim e não: Realmente fica rápida (na teoria conforme explicado acima), mas
levando em consideração que o deslocamento das cabeças de leitura/gravação do
disco rígido leva certo tempo, é mais vantajoso mantê-la entre as 2 partições
mais acessadas, isto diminui o tempo de acesso caso um programa esteja fazendo
uso constante de <filename>/</filename> ou <filename>/usr</filename> e precisar
trocar dados na partição <literal>swap.


Além do mais, a partição <filename>/</filename> geralmente é pequena (no máximo
800M) deixando a swap em uma área muito próxima do inicio do disco rígido.  Com
base nisto, você poderá ter uma melhor visão técnica para a construção de suas
partições dependendo da função do sistema.



 hard-perf-spindles">###Spindles

Em sistemas que utilizam um disco rígido dedicado para fazer
<literal>swap, a ligação deste em uma placa controladora independente
aumentará bastante a performance do sistema, pois enquanto o disco principal
ligado em sua controladora estiver fazendo uma operação de leitura, o outro
poderá estar fazendo sua operação de swap simultaneamente.  O mesmo não
acontece quando dois discos rígidos IDE estão ligados no mesmo cabo (isto não
acontece no SCSI).



 hard-perf-hdparm">###Fazendo ajustes finos de performance do disco

O <command>hdparm é um programa que permite modificar características
diversas da unidade de disco rígido e de CD como modo de transferência de
dados, leitura adiante, dma, cache, leitura simultânea de setores, hibernação,
etc.


Por padrão as transferências de dados entre a controladora do HD (a plaquinha
que fica embaixo dele) e a controladora de periféricos é feita em 16 bits.
Para exibir a configuração atual do disco rígido <filename>/dev/hda</filename>
(por exemplo), digite o seguinte comando: <literal>hdparm /dev/hda

<screen>
/dev/hdb:
 multcount    =  0 (off)
 I/O support  =  0 (16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (off)
 keepsettings =  0 (off)
 nowerr       =  0 (off)
 readonly     =  0 (off)
 readahead    =  8 (on)


Imediatamente podemos modificar os seguintes campos para melhorar sensivelmente
o desempenho do disco rígido:

<variablelist>
<varlistentry>
<term>multcount
<listitem>

Pode ser modificada com **-m[num]** e especifica o número
máximo de setores que serão acessados de uma só vez na operação de leitura da
unidade.  O valor máximo recomendado é igual a capacidade máxima suportada pelo
seu disco rígido, que pode ser obtida com o comando: <literal>hdparm -i
/dev/hda

<screen>
 Model=TS6324A2, FwRev=.340    , SerialNo=A99B99JA
 Config={ HardSect NotMFM HdSw&gt;15uSec Fixed DTR&gt;10Mbs RotSpdTol&gt;.5% }
 RawCHS=13228/15/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=256kB, MaxMultSect=16, MultSect=16
 CurCHS=13228/15/63, CurSects=12500460, LBA=yes, LBAsects=12500460
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes: pio0 pio1 pio2 pio3 pio4 
 DMA modes: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5


O campo **MaxMultSect=16** indica o valor de 16 como máximo
suportado em uma única operação pela unidade.  Valores maiores poderão ser
especificados mas não trarão ganho de performance.  Para discos rígidos
**Western Digital** é recomendável deixar este valor como
<literal>0, porque eles possuem um mecanismo embutido para leitura de
setores.  Para experimentar valores fora dos padrões, coloque seu sistema de
arquivos como somente leitura para não perder dados caso algo saia errado.


Note que o comando <literal>hdparm -i mostra alguns detalhes
interessantes sobre a configuração do disco rígido e modos de operação
suportados.



<varlistentry>
<term>I/O support
<listitem>

Modificado com **-c[num]**.  O número especificado pode ser
<literal>0 para transferência de dados em 16 bits,
<literal>1 para 32 bits e <literal>3 para 32 bits com uma
seqüencia especial de sincronismo (alguns chips requerem esta ao invés da
<literal>1).



<varlistentry>
<term>using_dma
<listitem>

Modificado com **-d[num]**.  Habilita ou não o uso de DMA para
a transferência de dados do HD, ativando o controle de algumas operações pelo
chipset livrando a CPU para processamento.  <literal>0 desativa DMA e
<literal>1 ativa.  Note que nem todos os chipsets aceitam esta
operação.  Esta usada em conjunto com a opção <literal>-X oferece um
excelente ganho de performance pelo uso correto de sua controladora.


A ativação de dma também pode ser feita automaticamente na recompilação do
kernel ou especificando o parâmetro **ideX=dma**
(<literal>X é o número da controladora IDE) na linha de comando de
<literal>boot: ou no arquivo <filename>/etc/lilo.conf</filename>.



<varlistentry>
<term>xfermode
<listitem>

Modificado pela opção **-X[num]**.  Permite selecionar o
melhor modo de transferência de dados do seu disco rígido, é nesta parte onde
você seleciona o modo UltraDMA para transferência de dados, caso seu HD/CD-ROM
suporte.  Os seguintes valores são válidos:

<screen>
32 - PIO Mode 0
33 - PIO Mode 1
34 - PIO Mode 2
35 - PIO Mode 3
36 - PIO Mode 4
64 - Ultra DMA Mode 0
65 - Ultra DMA Mode 1
66 - Ultra DMA Mode 2
67 - Ultra DMA Mode 3
68 - Ultra DMA Mode 4
69 - Ultra DMA Mode 5
70 - Ultra DMA Mode 6


Para descobrir os modos PIO e UltraDMA do seu HD, utilize o comando
<literal>hdparm -I /dev/hd?.  NÃO UTILIZE UM MODO PIO/ULTRA DMA NÃO
SUPORTADO PELA SUA CONTROLADORA.  CASO SUA PLACA CONTROLADORA DO HD SUPORTE UM
MODO ALTO PIO/ULTRADMA MAS SUA CONTROLADORA IDE NÃO SUPORTA, VOCÊ DEVERÁ
UTILIZAR O VALOR MAIS ADEQUADO PARA AMBAS.  FAÇA TESTES SEMPRE QUE ALTERAR O
MODO DE FUNCIONAMENTO E ESTEJA ATENTO A MENSAGENS DE ERROS PARA QUE NÃO TENHA
PERDA DE DADOS!!!



<varlistentry>
<term>unmaskirq
<listitem>

Modificado com **-u[num]**.  Habilita ou não o controlador de
disco mascarar as interrupções de processador durante o processamento das
interrupções de disco.  <literal>0 desativa esta função e
<literal>1 ativa.  Use esta opção com cuidado e sob seu próprio
risco: algumas placas controladores de HD e controladoras de periféricos não
trabalham bem com a taxa de transferência aumentada, podem ocorrer perda de
dados.  Coloque o sistema de arquivos como somente leitura antes de testar esta
característica.



<varlistentry>
<term>readonly
<listitem>

Modificado com **-r[num]**.  Coloca o disco em modo somente
leitura.  A montagem da partição com a opção **ro** no
<filename>/etc/fstab</filename> é preferida.



<varlistentry>
<term>readahead
<listitem>

Modificado com **-a[num]**.  Configura o número de blocos que
serão lidos antecipadamente no sistema de arquivos (por padrão é usado 8 blocos
- 4 Kb).  Este número poderá ser modificado para se adequar a utilização do
computador.  Em sistemas com muita procura de arquivos pequenos (servidores
web), um valor pequeno (como o padrão) é recomendável.  Se a máquina é um
servidor de arquivos dedicado, um valor maior trará maiores benefícios.



</variablelist>

Veja mais detalhes sobre o comando <command>hdparm em sua página de
manual.  Depois de selecionado o melhor valor de performance, você deverá
salvar em um arquivo que será lido na inicialização para ativação destes
valores.  Para fazer teste de performance de leitura bruta utilize o comando
<literal>hdparm -t /dev/hd?, para fazer testes com o uso de cache,
use o comando <literal>hdparm -T /dev/hd?.


**OBS:** Se o <command>Linux resetar o
disco rígido, a maioria das configurações retornarão ao seu valor padrão.  Isto
ocorre devido a opções mau utilizadas no <command>hdparm, não
suportadas pelo disco rígido ou por problemas no HD/controladora.

<screen>
Exemplos:

# Ajusta o número de setores simultâneos para 16 e o modo de transferência para 
# 32 bits no disco rígido /dev/hda
hdparm -c1 -m16 /dev/hda

# Programa a leitura adiante do HD para 64 blocos (32Kb), o modo de transferência 
# para 32 bits, usar DMA, e 16 setores simultâneos.
hdparm -c1 -d1 -m16 -a64 /dev/hda

#Mostra os valores de configuração atuais do disco rígido
hdparm /dev/hda



 hard-perf-atime">###Data de acesso a arquivos/diretórios

Toda vez que acessamos um arquivo ou diretório da máquina
<command>Linux a data/hora é atualizada.  Em máquinas normais isto é
OK mas em servidores onde o acesso a arquivos é constante (como no diretório
<filename>/var/spool</filename> em servidores de e-mail ou
<filename>/usr/</filename> em servidores diskless) é recomendável desativar
esta característica.  Isto reduzirá a quantidade de buscas das cabeças do disco
rígido para a atualização deste atributo e conseqüentemente aumentará a
performance na gravação de arquivos (o disco rígido usa o sistema mecânico para
ler/gravar dados, muito mais lento que a memória RAM eletrônica).

<screen>
chattr -R +A /var/spool


O atributo <literal>+A desativa a gravação da "data de acesso" dos
arquivos e sub-diretórios dentro de <filename>/var/spool</filename>.  Para
desativar a atualização da "data de acesso" para toda a partição, você pode
incluir a opção de montagem <literal>noatime no seu
<filename>/etc/fstab</filename>:

<screen>
/dev/hda1     /var/spool    ext2   defaults,noatime   0   1


**OBS:** O <command>Linux utiliza três
atributos de data para controle de arquivos:

<itemizedlist>
<listitem>

<literal>atime - Data/Hora de acesso: é atualizado toda vez que o
arquivo é lido ou executado.


<listitem>

<literal>mtime - Data/Hora da modificação, atualizado sempre que
alguma modificação ocorre no arquivo ou no conteúdo do diretório.  Esta é mais
interessante que a <literal>ctime principalmente quando temos
hardlinks.


<listitem>

<literal>ctime - Data/Hora da última modificação do inodo do arquivo.




Em partições onde a gravação é freqüente (como na própria
<filename>/var/spool</filename>) a desativação do atributo
<literal>atime além de melhorar o desempenho do disco, não fará muita
falta.





 hard-perf-SATA">###Periféricos SATA

Hardwares SATA (Serial ATA) representam a próxima geração em tecnologia usada
para a transferência de dados em alta velocidade a baixo custo.  Hoje está se
tornando o padrão de indústria a utilização de dispositivos SATA em micros em
substituição a dispositivos IDE.  Dispositivos IDE tradicionais são chamados de
PATA (parallel ATA, ou ATA paralelo).


Estes dispositivos são classificados em 2 tipos:

<itemizedlist>
<listitem>

<literal>SATA I - Esta se tornando alternativa a discos IDE (PATA).
Possui taxa de transferência de até 150Mb/s


<listitem>

<literal>SATA II - Esta se tornando alternativa a discos IDE (PATA).
Possui taxa de transferência de até 300Mb/s




Um cabo SATA tende a ter o mesmo comprimento de um cabo IDE, raramente
excedendo 50 centimetros.



 hard-perf-SCSI">###Periféricos SCSI

Hardwares SCSI (Small Computer System Interfaces) representam a tecnologia
ideal para a transferência de dados em alta velocidade e ligação de vários
periféricos.  A taxa de transferência especificada para dispositivos SCSI é
sempre a padrão se comparada a dispositivos IDE (quando uma taxa de 66Mb/s
quase nunca é atingida).


Estes dispositivos são classificados em 3 categorias:

<itemizedlist>
<listitem>

<literal>SCSI I - Usa um cabo de 25 condutores para a ligação de
periféricos.  Normalmente usado em scanners, impressoras e outros dispositivos.
A taxa de transferência não é muito alta se comparado aos outros tipos SCSI.


<listitem>

<literal>SCSI II - Também chamado de **Fast SCSI**.
Usa um cabo de 50 condutores para a ligação de periféricos.  Permite que sejam
ligados até 7 periféricos em uma mesma controladora (veja <xref linkend="hard-perf-SCSI-IDcfg"/>).  É o mais comum encontrado hoje em dia, mas
vem perdendo espaço aos poucos para a tecnologia <literal>SCSI III.


<listitem>

<literal>SCSI III - Também chamado de **Fast SCSI
SE** ou **LVD**.  Usa um cabo de 68 condutores para
ligação de periféricos (veja <xref linkend="hard-perf-SCSI-IDcfg"/>).  Permite
que sejam ligados até 16 periféricos em uma mesma controladora.


<listitem>

<literal>SATA I - Esta se tornando alternativa a discos IDE (PATA).
Possui taxa de transferência de até 150Mb/s


<listitem>

<literal>SATA II - Esta se tornando alternativa a discos IDE (PATA).
Possui taxa de transferência de até 300Mb/s




Um cabo SCSI pode ter o comprimento de até 5 metros de extensão.  Os
periféricos SCSI são identificados através de números chamados de identificador
SCSI ou SCSI ID.  Estes números vão de 0 a 6 para o padrão **SCSI
2** e de 0 a 15 para o padrão **SCSI 3**.


Placas SCSI como a **Adaptec UV 19160** permitem a ligação de
periféricos SCSI 2 e SCSI 3 na mesma placa com a taxa de transmissão de 160
MB/s por periférico, além de possuir um "setup" próprio para configurar as
opções dos dispositivos da placa e a operação da própria.  A tecnologia SCSI é
algo realmente rápido para a transferência de dados e cara também, seu uso é
muito recomendado em servidores críticos.  Os próprios dispositivos SCSI como
discos rígidos, gravadores de CD, cd-rom, etc.  são construídos de tal forma
que tem a durabilidade maior que periféricos comuns, garantindo a máxima
confiança para operação/armazenamento de dados em longos períodos de operação.

 hard-perf-SCSI-IDcfg">###Configurando uma SCSI ID e terminação

Uma SCSI ID é configurada independentemente por dispositivo e consiste em 3
jumpers (ou dip switches) que possuem os valores <literal>1,
<literal>2 e <literal>4.  Veja o exemplo abaixo de uma
unidade de CD SCSI 2:

<screen>
+--------------------------------------------
|
|
|
|SCSI ID
|   |
| _____ TERM
| | | | |
| o o o o o o 
| o o o o o o
| 1 2 4 T
|
+---------------------------------------------


Se você deixar os 3 jumpers da SCSI ID abertos, o dispositivo usará a SCSI ID
0.  Colocando o jumper na posição 1, a unidade terá a SCSI ID 1.  Se você
colocar um jumper na posição 1 e outro na 4, a unidade será identificada pela
SCSI ID 5 (quando mais de um jumper é ligado, os números serão somados).


A terminação SCSI funciona de forma semelhante a de uma rede BNC, o último
periférico do cabo SCSI deve ter o jumper de terminação colocado para indicar
que é o último periférico do cabo e evitar deflexão de dados.  Algumas placas
SCSI modernas ajustam automaticamente a terminação de periféricos sem
necessidade de ajustar manualmente.





