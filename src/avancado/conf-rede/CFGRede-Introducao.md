<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='avanc'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cfgrede">###Configurações especiais de Rede

Este capítulo descreve alguns tipos de configurações que podem ser feitas em
rede utilizando os recursos disponíveis do <command>Linux.  Aqui não
estão todas as aplicações, pois o sistema é bastante flexível e o próprio time
de desenvolvimento do kernel não demonstrou limitações quanto as formas de se
construir uma rede :-)


 cfgrede-ipalias">###IP Alias

Este recurso permite configurar uma interface de rede para responder por um ou
mais IPs, que não precisam pertencer a mesma faixa.  Para usuários externos, a
impressão é que a rede tem "muitas" máquinas, quando na realidade apenas uma
responde por todos estes endereços virtuais.  Podemos citar algumas utilizações
úteis deste recurso:

<itemizedlist>
<listitem>

Simular uma rede com diversas máquinas


<listitem>

Construir virtual hosts baseados em IP


<listitem>

Definir endereçamentos secundários para fins de análise e depuração de pacotes
(principalmente como armadilhas para trojans)


<listitem>

Colocação de serviços com operação restritas a interfaces em funcionamento
através de faixas específicas usando as configurações da interface virtual


<listitem>

Transição de IP de servidores de forma transparente


<listitem>

Entre muitas outras.  A idéia aqui é mostrar a simplicidade de se configurar
este recurso e entender o processo, que é bastante simples.




Para configurar o recurso de **IP Alias** é necessário apenas
que a opção **IP Aliasing Support** seja habilitada no kernel
(como módulo ou embutida).  Em nosso exemplo abaixo, temos uma rede com a
interface <filename>eth0</filename> configurada com o IP
**192.168.1.1** (classe C privada) e queremos adicionar uma
interface virtual que atenda pelo IP **172.16.0.1** (classe B
privada) e depois seguir os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

Ative a interface de rede com <command>ifconfig ou
<command>ifup (caso esteja usando a <command>Debian).


<listitem>

Crie uma interface virtual usando o comando <literal>ifconfig eth0:0
172.16.0.1.  Isto criará uma nova interface chamada
<literal>eth0:0 que passará a responder pelo IP 172.6.0.1.  É
permitido o uso de nomes para especificar a interface virtual, como:
<literal>eth0:rede1, <literal>eth0:rede2,
<literal>eth0:escritório.


<listitem>

Digite <literal>ifconfig para ver as configurações de sua nova
interface de rede.  Use o ping também para vê-la: <literal>ping
172.16.0.1.

<screen>
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:80:AE:B3:AA:AA
          inet end.: 192.168.1.1  Bcast:192.168.1.255  Masc:255.255.255.0
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          colisões:1 txqueuelen:100 
          RX bytes:71516 (69.8 Kb)  TX bytes:1146031 (1.0 Mb)
          IRQ:10 Endereço de E/S:0x300 

eth0:0    Encapsulamento do Link: Ethernet  Endereço de HW 00:80:AE:B3:AA:AA
          inet end.: 192.168.1.10  Bcast:192.168.1.255  Masc:255.255.255.0
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          IRQ:10 Endereço de E/S:0x300


Note que o MAC Address da placa <filename>eth0</filename> e
<filename>eth0:0</filename> são o mesmo, indicando que a mesma interface atende
ambos os IPs.


<listitem>

Se necessário ajuste as rotas ou gateway com o comando <command>route
(veja <xref linkend="rede-rota-c"/>).


</orderedlist>

Para desativar uma interface de rede virtual, utilize a sintaxe:
<literal>ifconfig eth0:0 down ou <literal>ifdown eth0:0
(caso esteja usando a <command>Debian).


Se o teste com o <command>ping não funcionar, verifique se possui o
suporte a **IP Alias** no kernel, se o módulo precisa ser
carregado manualmente (caso seu kernel não esteja compilado com o
<command>kmod) ou se existe um firewall restritivo bloqueando seu IP.


Na distribuição <command>Debian a configuração de uma interface
virtual pode ser feita de forma idêntica a interfaces estáticas padrão:

<screen>
auto eth0
iface eth0 inet static
 address 192.168.1.1
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255

auto eth0:0
iface eth0:0 inet static
 address 172.16.0.1
 netmask 255.255.0.0
 network 172.16.0.1
 broadcast 172.16.255.255


**OBS1:** Quando você desativa uma interface
física (<filename>eth0</filename>), todas as interfaces virtuais também são
desativadas.


**OBS2:** Caso utilize um firewall
(principalmente com a política padrão permissiva), esteja atento as
modificações que precisa realizar para não comprometer a segurança de sua
máquina.  Caso tenha dados considerados seguros em sua máquina e esteja em
dúvida sobre as implicações de segurança do **IP Alias** em
sua máquina, consulte seu administrador de redes.


**OBS3:** Note que somente os 4 primeiros
caracteres serão mostrados na saída do <command>ifconfig, desta forma
procure utilizar no máximo esta quantidade de caracteres para evitar problemas
durante uma futura administração do servidor, no caso de esquecimento do nome
completo da interface virtual).



 cfgs-bridge">###Bridge

Uma **bridge** é uma interface de rede lógica composta por uma
ou mais interfaces de rede física operando em nível 2 (enviando pacotes através
de **MAC adresses**, veja <xref linkend="rede-camadas"/>).


Sua operação é transparente na rede, podendo ser usada como um switch/firewall,
estação de monitoração, etc.  Aqui descreverei como montar uma bridge simples e
uma aplicação de firewall simples.  As possibilidades são diversas e uma
configuração bem feita pode detectar ataques, protocolos desconhecidos até
vírus complexos de rede.

 cfgs-bridge-req">###Requerimentos para a Instalação

É necessário um dos seguintes requerimentos para se montar uma bridge:

<itemizedlist>
<listitem>

Kernel com suporte a bridge ativado (na configuração de rede)


<listitem>

O pacote <systemitem role="package">bridge-utils</systemitem> instalado.


<listitem>

patch bridge-nf se desejar usar o netfilter com as interfaces de entrada e
saída (como antes de usar a bridge) ao invés de controlar o tráfego apenas pela
interface criada pela bridge.




Ative a opção <literal>802.1d Ethernet Bridging na seção
<literal>Networking Options, recompile e instale seu novo kernel.
Caso tenha aplicado o patch **bridge nf**, aparecerá uma sub
opção chamada <literal>netfilter (firewalling) support que permitirá
que o firewall trabalhe com as interfaces físicas ao invés de somente através
da interface virtual criada pela bridge.


**OBS:** O patch **bridge nf**
viola a RFC de bridges.  Mesmo assim ela é a única opção em muitas aplicações,
principalmente quando se deseja controlar o tráfego que atravessam as
interfaces.  Após isto instale o pacote <systemitem role="package">bridge-utils</systemitem>, ele possui os utilitários necessários
para ativar, configurar e monitorar o funcionamento de sua bridge.


Não é necessária ativação do **ip_forward** para o
funcionamento da bridge, uma vez que ela funcionará como uma interface lógica
que reúne interfaces de rede físicas.



 cfgs-bridge-cfg">###Configuração da bridge

Nos exemplos abaixo, eu assumirei a utilização do nome de dispositivo
<filename>br0</filename> para se referir a bridge no sistema.  Siga estes
passos para configurar uma bridge em sistemas <command>Debian:

<itemizedlist>
<listitem>

Primeiro, desative os blocos no arquivo
<filename>/etc/network/interfaces</filename> que configuram as interfaces que
serão usadas na bridge (por exemplo, <filename>eth0</filename> e
<filename>eth1</filename>).  Elas podem ser comentadas, removidas, ou você
poderá comentar a linha **auto eth0** e **auto
eth1** para que ele não ative automaticamente estas interfaces com o
<literal>ifup -a (executado durante a inicialização).  Desta forma, a
inicialização destas interfaces poderá somente ser feita manualmente.

<screen>
auto br0
iface br0 inet static
    address 192.168.1.2
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    bridge_ports eth0 eth1


Note que a interface virtual da brigde (<filename>br0</filename>) deve ser
configurada com parâmetros válidos de interfaces (assim com uma interface de
rede padrão).  Note a adição da linha <literal>bridge_ports que
indica que interfaces de rede serão usadas para fazer a bridge.  Caso seja
usado o parâmetro **all**, todas as interfaces físicas de rede
serão usadas para fazer bridge (excluindo a <filename>lo</filename>).


<listitem>

Execute o <literal>ifdown -a (para desativar as interfaces antigas.


<listitem>

Execute o <literal>ifup br0 para levantar as interface
<filename>br0</filename>.  O sistema poder demorar um pouco para levantar a
bridge (as vezes até 40 segundos) mas isto é normal.




Pronto, você terá uma bridge simples já configurada e funcionando em seu
sistema!  As interfaces físicas serão configuradas com o IP 0.0.0.0 e estarão
operando em modo promíscuo.



 cfgs-bridge-cfgadv">###Configurações mais avançadas de bridge

A bridge permite ainda definir prioridade para utilização de interfaces, além
de outras funcionalidades que lhe permitem ajustar a performance da máquina de
acordo com sua rede.  Um bom exemplo, é quando você deseja criar 2 bridges em
uma mesma máquina envolvendo interfaces de rede específicas, uma atendendo a
rede 192.168.0.x e outra a rede 192.168.1.x:

<screen>
auto br0
iface br0 inet static
    address 192.168.0.2
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    bridge_ports eth0 eth1

auto br1
iface br1 inet static
    address 192.168.1.2
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.0.1
    bridge_ports eth2 eth3 eth4


No exemplo acima, as interfaces <filename>eth0</filename> e
<filename>eth1</filename> fazem parte da bridge <filename>br0</filename> e as
demais (<filename>eth2</filename>, <filename>eth3</filename> e
<filename>eth4</filename> da bridge <filename>br1</filename>.

<screen>
    bridge_ports eth2 eth3
    bridge_bridgeprio 16385
    bridge_portprio eth1 100
    bridge_fd 5



 cfgs-bridge-cfgmanual">###Configuração manual da bridge

Internamente, o que o <filename>ifup</filename> faz é interpretar os parâmetros
no arquivo de configuração e executar os comandos do pacote <systemitem role="package">bridge-utils</systemitem> para ativar a interface da bridge.  O
utilitário responsável por este processo é o <command>brctl.  Será
documentado aqui como ativar uma bridge através deste programa (que servirá
para fazer uma bridge em qualquer sistema <command>Linux).

<screen>
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
ifconfig br0 192.168.0.4


O comando acima ativa uma bridge simples, como o primeiro exemplo.  Tenha
certeza que as interfaces físicas de rede estão desativadas antes de executar
este comando.


Outros parâmetros que podem ser usados com o <command>brctl:

<variablelist>
<varlistentry>
<term>setbridgeprio [bridge] [prioridade]
<listitem>

Define a prioridade da bridge, o valor deve estar entre 0 e 65536 (16 bits).
Valores menores definem uma prioridade maior.



<varlistentry>
<term>setfd [bridge] [tempo]
<listitem>

Ajusta o delay da bridge especificada em [tempo] segundos.



<varlistentry>
<term>setmaxage [bridge] [tempo]
<listitem>

Ajusta o tempo máximo de vida da bridge para [tempo] segundos.



<varlistentry>
<term>setportprio [bridge] [interface] [prioridade]
<listitem>

Ajusta a prioridade da [interface] especificada na [bridge].  O valor de
prioridade deve estar entre 0 e 255 (8 bits).  Quanto menor o valor maior a
prioridade.  Isto é útil para otimizações o volume de tráfego em máquinas que
possuem diversas interfaces configuradas fazendo parte da bridge.



</variablelist>
<screen>
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
brctl setportprio br0 eth0 50
brctl setportprio br0 eth1 80
brctl setfd br0 2

ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
ifconfig br0 192.168.0.4



 cfgs-bridge-fw">###Usando o iptables para construir um firewall na máquina da bridge

A construção de um firewall em uma bridge não tem maiores segredos, basta
referir-se a interface lógica da bridge para construir suas regras (tendo em
mente como uma bridge funciona e como os pacotes atravessarão as interfaces).


Caso aplique o patch **bridge nf**, será possível referir-se
as interfaces locais de rede e também a da bridge.  Neste caso a interface da
bridge será identificada como interface **IN** ou
**OUT** **PHYSIN** e as interfaces físicas
como **PHYSOUT**:

<screen>
Oct 22 09:19:24 router kernel: IN=br0 PHYSIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d4:7d:ff:ff:ff:08:00 SRC=192.168.0.4 DST=1982.168.255.255 LEN=238 TOS=0x00 PREC=0x00 TTL=128 ID=23383 PROTO=UDP SPT=138 DPT=138 LEN=218


Mesmo que a bridge não necessite de **ip_forward** ativado
para redirecionar os pacotes através das interfaces, isto será necessário para
habilitar o uso do firewall para controlar o tráfego que atravessa as
interfaces.



 cfgs-bridge-filternoip">###Filtrando pacotes não IP na bridge

Para fazer esta tarefa, utilize a ferramenta <command>ebtables
disponível em http://www.w3.org/1999/xlink) [](http://users.pandora.be/bart.de.schuymer/ebtables)http://users.pandora.be/bart.de.schuymer/ebtables/).





 cfgs-plip">###Conectando dois computadores usando a porta paralela

O <command>Linux é bastante poderoso quando se trata de métodos para
se conectar duas ou mais máquinas em rede.  Uma brincadeira que é levada a
sério é que qualquer coisa que ligue uma máquina a outra possui um controlador
desenvolvido por alguém para fazer uma rede :)


Usando o <filename>plip</filename> (**Parallel Line Internet
Protocol**) permite <literal>criar uma interface de rede
para a porta paralela que utiliza todos os recursos de uma rede normal.  Esta
interface será identificada por <filename>plip?</filename>, onde
<literal>? é o número da porta paralela, recém configurada.


A rede via porta paralela pode atingir até 1Mb/s e mesmo esta velocidade
parecer aparentemente baixa apresenta diversas vantagens por sua escalabilidade
e pode lhe salvar em muitas situações de problemas.  Algumas características
deste tipo de rede:

<itemizedlist>
<listitem>

Pode ser configurado em qualquer máquina, pois sempre haverá uma porta
paralela.


<listitem>

É útil para fazer instalação de <command>Linux em máquinas sem
CD-ROM.  No momento da instalação é preciso somente alternar para um console,
executar os passos descritos aqui e continuar com o processo de instalação
normal :)


<listitem>

É uma boa solução quando as duas máquinas estão próximas


<listitem>

O custo para montagem desta rede é extremamente baixo, bastando um cabo Lap
Link Paralelo que custa no máximo R$20,00 o de 1,5M ou se gosta de eletrônica,
montar seu próprio cabo usando o esquema que descrevo em <xref linkend="cfgs-plip-cabo"/>.


<listitem>

Você poderá fazer qualquer coisa que faria em uma rede normal (incluindo
MASQUERADING, roteamento entre redes, etc) sendo bastante interessante para
testes práticos dos exemplos do Foca Linux Avançado ;-)


<listitem>

Ficará admirado com as capacidade de rede existente no <command>Linux
e feliz por ter colocado mais uma configuração em funcionamento :)




Agora, os contras da conexão via porta paralela:

<itemizedlist>
<listitem>

A porta paralela não estará disponível para ser usada em impressoras, conexão
de câmeras.


<listitem>

O cabo não pode ter mais de 4,5 metros.  Acima dessa comprimento, você pode
colocar sua controladora em risco além da perda de sinal.  Por segurança, o
tamanho recomendável é 2,5 metros.


<listitem>

Quando toda a banda do cabo é utilizada, algumas CPUs se tornam extremamente
lentas.




Para configurar uma conexão via cabo paralelo (plip) entre duas máquinas, vamos
assumir que a primeira máquina terá o IP 192.168.1.1 e a segunda máquina
192.168.1.2:

<orderedlist numeration="arabic">
<listitem>

Conecte o cabo Lap Link em cada uma das portas de impressora.  Caso saiba fazer
conexões eletrônicas ou goste do assunto, veja <xref linkend="cfgs-plip-cabo"/>.


<listitem>

Verifique se o seu kernel está compilado com o suporte a rede
<filename>plip</filename>.  Caso não esteja, a configuração da interface
<filename>plip</filename> falhará no passo do <command>ifconfig.


<listitem>

Se o sistema executa algum daemon de impressão, interrompa antes de usar a
porta paralela.  Alguns tipos de serviços de impressão interferem no
funcionamento do <filename>plip</filename>.


<listitem>

Configure o módulo <filename>parport_pc</filename> passando o parâmetro
<literal>irq=7 (a IRQ que sua porta de impressora utiliza).  Esta
configuração é necessária pois em algumas máquinas isso faz que o
<filename>plip</filename> não funcione ou aconteçam somente timeouts de
transmissão.


<listitem>

Execute o comando <literal>ifconfig plip0 192.168.1.1.  Verifique se
a interface foi ativada com o comando <literal>ifconfig plip0.


<listitem>

Nesse ponto a interface está ativa, mas a nossa máquina não conhece nada sobre
a rede ou como alcançar a máquina 192.168.1.2.  Como a conexão é ponto a ponto,
precisamos adicionar uma rota direta para esta máquina com o comando:
<literal>route add -host 192.168.1.2 plip0.


Este comando diz para criar uma rota com o destino
<literal>192.168.1.2 usando a interface <filename>plip0</filename>.


<listitem>

Configure a outra máquina seguindo os passos acima, apenas invertendo os 2
endereços IPs usados.


</orderedlist>

Pronto, agora verifique se cada uma das máquinas se comunica com a outra usando
o comando <literal>ping 192.168.1.x.  Se ocorrer um erro de timeout
na transmissão, leia atentamente os passos acima e refaça a configuração em
ambas as máquinas.  Ainda não funcionando, verifique se existe um firewall
bloqueando os pacotes da nova interface e se o cabo Lap Link está em bom
estado, o problema pode estar ai.


O número máximo de interfaces <filename>plip?</filename> está limitado ao
número máximo suportado pela máquina.  O padrão em sistemas padrão IBM/PC é de
3 (<filename>plip0</filename>, <filename>plip1</filename>,
<filename>plip2</filename>).


Para desativar uma rede plip, utilize o comando <literal>ifconfig plip0
down, remova o módulo <filename>plip</filename> (<literal>rmmod
plip).  Após isto, a porta paralela será liberada para uso por outros
aplicativos.

 cfgs-plip-cabo">###Construindo um cabo LapLink Paralelo

Se você tem experiência com eletrônica, poderá construir seu próprio cabo
LapLink Paralelo para fazer os testes desta seção.  Os materiais necessários
são:

<itemizedlist>
<listitem>

<literal>2 Conectores DB25 macho


<listitem>

<literal>2 Capas para os conectores acima.


<listitem>

Fio para ligação dos conectores (15 ligações).  No meu caso utilizei 2 metros
de um rolo de cabo SCSI de 50 vias para fazer as ligações, que é uma boa
alternativa para manter o cabo bonito e os fios juntos.




Este é o conector macho DB25 (a tomada que liga no computador) visto por trás
(minha namorada já disse que não sou bom em arte ASCII).  Bom, não custa tentar
de novo:

<screen>
  -------------------------------
13  \ o o o o o o o o o o o o o / 1
25  \ o o o o o o o o o o o o / 14
     -------------------------


A figura acima mostra a posição dos pinos como referência para a soldagem dos
terminais.  A tabela abaixo mostra a ligação dos fios nos cabos das 2 pontas do
cabo:

<screen>
+---------+---------+
| Ponta 1 | Ponta 2 |
+---------+---------+
|    1    |     1   |
|    2    |    15   |
|    3    |    13   |
|    4    |    12   |
|    5    |    10   |
|    6    |    11   |
|   10    |     5   |
|   11    |     6   |
|   12    |     4   |
|   13    |     3   |
|   14    |    14   |
|   15    |     2   |
|   16    |    16   |
|   17    |    17   |
|   25    |    25   |
+---------+---------+





 cfgs-slattach">###Conectando dois computadores usando a porta serial

Este método permite criar uma rede ponto a ponto usando a porta serial da
máquina, que funcionará de forma semelhante a mostrada em <xref linkend="cfgs-plip"/>.


O método que irei descrever é bastante simples e utiliza o
<command>slattach e o protocolo **slip** para
comunicação entre as duas máquinas, mas nada impede que seja usado o
**ppp** para comunicação, apenas acrescentará um pouco mais de
complexibilidade para esta configuração para obter o mesmo resultado.


Usando o método descrito, será criada uma interface chamada
<filename>sl?</filename> (interface SLIP, onde <literal>? é o número
da interface recém configurada).


A rede via porta serial pode atingir em média 115.200kbps/s mas é prático
quando não tem outras opções para fazer uma rede ponto a ponto.  Segue algumas
características deste tipo de rede:

<itemizedlist>
<listitem>

Pode ser configurado em qualquer máquina, pois sempre haverá uma porta serial
disponível.


<listitem>

É possível fazer a instalação de <command>Linux em máquinas sem
CD-ROM e acesso a rede, onde não é possível gerar disquetes para instalar o
resto dos pacotes necessários, embora seja limitado a 11Kb/s.  No momento da
instalação é preciso somente alternar para um console, executar os passos
descritos aqui e continuar com o processo de instalação normal :)


<listitem>

É uma boa solução quando as duas máquinas até em ambientes próximos.


<listitem>

O custo para montagem desta rede é extremamente baixo, bastando um cabo Lap
Link Serial custa em média R$20,00 o cabo de 4 metros.  Se você também é um
amante da eletrônica, estou descrevendo o esquema de montagem do cabo em <xref linkend="cfgs-slattach-cabo"/>.


<listitem>

Você poderá fazer qualquer coisa que faria em uma rede normal (incluindo
roteamento entre redes, MASQUERADING, etc)


<listitem>

É mais uma prova das capacidades de rede que é possível usando o
<command>Linux.




Agora, os contras da conexão via porta serial:

<itemizedlist>
<listitem>

A porta serial não estará disponível para ser usada para conexão de mouses,
impressoras seriais, dispositivos eletrônicos e inteligentes, etc.


<listitem>

O comprimento máximo do cabo é de 15 metros.  Acima dessa comprimento, você
pode colocar sua controladora em risco além da perda de sinal.  Por segurança,
o tamanho máximo recomendável é 13 metros




Para configurar uma conexão via cabo serial entre duas máquinas, vamos assumir
que a primeira máquina terá o IP 192.168.2.1 e a segunda máquina 192.168.2.2:

<orderedlist numeration="arabic">
<listitem>

Conecte o cabo Lap Link serial em cada uma das portas seriais.


<listitem>

Verifique se o seu kernel está compilado com o suporte a rede
<filename>slip</filename> e também com suporte a <literal>cslip (slip
compactado, que melhora a taxa de transferência dependendo dos dados sendo
transmitidos).  Caso não tenha o suporte a **slip**, você
poderá usar o **ppp** nas duas pontas do link fazendo algumas
adaptações para usar a interface <filename>ppp?</filename>, como é simples não
será descrito neste guia :) (veja o manual do <command>slattach)


<listitem>

Interrompa qualquer programa que esteja usando a porta serial.


<listitem>

Execute o comando <literal>slattach -s 115200 /dev/ttyS1 &amp;.  A função
do <command>slattach é associar uma interface de rede a um
dispositivo, neste caso associamos o dispositivo
<filename>/dev/ttyS1</filename> (segunda porta serial) a interface
<filename>sl0</filename> (verifique se a interface foi criada usando o comando
<literal>ifconfig sl0.


A opção <literal>-p especifica um protocolo alternativo para o
<command>slattach, o padrão é o **cslip**.  Outros
tipos disponíveis são **slip**, **adaptive**
**ppp** e **kiss** (usado em conexões de
rádio AX.25).  Recomendo ver a página de manual do <command>slattach.


<listitem>

Nesse ponto a interface está ativa, mas a nossa máquina não conhece nada sobre
a rede ou como alcançar a máquina 192.168.2.2.  Como a conexão é ponto a ponto,
precisamos adicionar uma rota direta para esta máquina com o comando:
<literal>route add -host 192.168.2.2 sl0.


Este comando diz para criar uma rota com o destino
<literal>192.168.2.2 usando a interface <filename>sl0</filename>.


<listitem>

Configure a outra máquina seguindo os passos acima, apenas invertendo os 2
endereços IPs usados.


</orderedlist>

Pronto, agora verifique se cada uma das máquinas se comunica com a outra usando
o comando <literal>ping 192.168.2.x.  Se ocorrer um erro, verifique
os seguintes ítens:

<itemizedlist>
<listitem>

Se as velocidade e o protocolo especificado em ambos os lados do link estão
iguais.


<listitem>

Se já existe um processo <command>slattach rodando em segundo plano.


<listitem>

Se existe um firewall bloqueando os pacotes da nova interface


<listitem>

Se o cabo Lap Link serial está em bom estado.




O número máximo de interfaces <filename>sl?</filename> depende da quantidade de
portas seriais da sua máquina.  Caso utilize uma placa multi serial, o número
máximo de conexões de rede se torna grande (mas isto é apenas para curiosidade,
pois não compensa uma multi serial para ligar uma quantidade grande de máquinas
a baixa velocidade).


Para derrubar a conexão, basta derrubar a interface serial com o
<literal>ifconfig sl0 down, dar um kill no daemon do
<command>slattach e remover o módulo <filename>slip</filename> e
<filename>cslip</filename> com o comando <command>rmmod.  Assim sua
porta serial será liberada e poderá ser usada por outros aplicativos.

 cfgs-slattach-cabo">###Construindo um cabo LapLink Serial

Se você é uma pessoa que sabe mexer com eletrônica, poderá construir seu
próprio cabo LapLink serial para fazer os testes desta seção.  Os materiais
necessários são:

<itemizedlist>
<listitem>

<literal>2 - Conectores seriais DB9 fêmea


<listitem>

<literal>2 - Capas para os conectores acima.


<listitem>

Fios para ligação dos conectores.  Uma forma que utilizei para montar este cabo
foi aproveitar um carretel de cabo SCSI aproveitando 10 metros desfiando
somente 9 dos 50 fios que acompanha o cabo (deixei um fio extra no caso de
algum outro se romper).


<listitem>

Ferro de solda e solda para as ligações.


<listitem>

Concentração e paciência para a confecção correta dos cabos.




Este é o conector fêmea DB9 (tomada que liga na máquina) visto por trás (hora
de mostrar novamente meu talento com arte ASCII :))

<screen>
  --------------
1 \ o o o o o  / 5
6  \ o o o o  / 9
    ----------


A figura acima mostra a posição dos pinos como referência para a soldagem dos
terminais.  A tabela abaixo mostra a ligação dos fios nos cabos das 2 pontas.
Note que cada ponta pode ter a opção da serial de 9 ou 25 pinos (ou as duas):

<screen>
 
+--------+--------+---------+
|Ponta 1 |        |  Ponta 2|
+---+----+--------+----+----+
| 9 | 25 |        | 25 |  9 |
+---+----+--------+----+----+
| 5 |  7 |        |  7 |  5 |
| 3 |  2 |        |  3 |  2 |
| 7 |  4 |        |  5 |  8 |
| 6 |  6 |        | 20 |  4 |
| 2 |  3 |        |  2 |  3 |
| 8 |  5 |        |  4 |  7 |
| 4 | 20 |        |  6 |  6 |
+---+----+--------+----+----+





