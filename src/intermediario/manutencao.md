<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> <!--- / version="5.0" manut"> ---/--->###Manutenção do Sistema

Este capítulo descreve como fazer a manutenção de seu sistema de arquivos e os
programas de manutenção automática que são executados periodicamente pelo
sistema.


 manut-checagem">###Checagem dos sistemas de arquivos

A checagem do sistema de arquivos permite verificar se toda a estrutura para
armazenamento de arquivos, diretórios, permissões, conectividade e superfície
do disco estão funcionando corretamente.  Caso algum problema exista, ele
poderá ser corrigido com o uso da ferramenta de checagem apropriada.  As
ferramentas de checagem de sistemas de arquivos costumam ter seu nome iniciado
por <literal>fsck e terminados com o nome do sistema de arquivos que
verifica, separados por um ponto:

<itemizedlist>
<listitem>

<literal>fsck.ext2 - Verifica o sistema de arquivos
<literal>EXT2 ou <literal>EXT3.  Pode também ser encontrado
com o nome <command>e2fsck.


<listitem>

<literal>fsck.ext3 - Um alias para <command>fsck.ext3.


<listitem>

<literal>fsck.minix - Verifica o sistema de arquivos
<literal>Minix.


<listitem>

<literal>fsck.msdos - Verifica o sistema de arquivos
<literal>Msdos.  Pode também ser encontrado com o nome
<command>dosfsck.




Para verificar um sistema de arquivos é necessário que ele esteja desmontado
caso contrário poderá ocorrer danos em sua estrutura.  Para verificar o sistema
de arquivos raíz (que não pode ser desmontado enquanto o sistema estiver sendo
executado) você precisará inicializar através de um disquete e executar o
<command>fsck.ext2.


 manut-checagem-ext2">###fsck.ext2

Este utilitário permite verificar erros em sistemas de arquivos
<literal>EXT2 e <literal>EXT3 (**Linux
Native**).


<command>fsck.ext2 [**opções**]
[**dispositivo**]


Onde:

<variablelist>
<varlistentry>
<term>dispositivo
<listitem>

É o local que contém o sistema de arquivos <literal>EXT2/EXT3 que
será verificado (partições, disquetes, arquivos).



<varlistentry>
<term>opções
<term>-c
<listitem>

Faz o <command>fsck.ext2 verificar se existem agrupamentos
danificados na unidade de disco durante a checagem.



<varlistentry>
<term>-d
<listitem>

Debug - Mostra detalhes de processamento do <command>fsck.ext2.



<varlistentry>
<term>-f
<listitem>

Força a checagem mesmo se o sistema de arquivos aparenta estar em bom estado.
Por padrão, um sistema de arquivos que aparentar estar em bom estado não são
verificados.



<varlistentry>
<term>-F
<listitem>

Grava os dados do cache no disco antes de iniciar.



<varlistentry>
<term>-l [arquivo]
<listitem>

Inclui os blocos listados no [arquivo] como blocos defeituosos no sistema de
arquivos.  O formato deste arquivo é o mesmo gerado pelo programa
<command>badblocks.



<varlistentry>
<term>-L [arquivo]
<listitem>

Faz o mesmo que a opção <literal>-l, só que a lista de blocos
defeituosos do dispositivo é completamente limpa e depois a lista do [arquivo]
é adicionada.



<varlistentry>
<term>-n
<listitem>

Faz uma verificação de <literal>somente leitura no sistema de
arquivos.  Com esta opção é possível verificar o sistema de arquivos montado.
Será assumido <literal>não para todas as perguntas e nenhuma
modificação será feita no sistema de arquivos.


Caso a opção <literal>-c seja usada junto com <literal>-n,
<literal>-l ou <literal>-L, o sistema de arquivos será
verificado e permitirá somente a atualização dos setores danificados não
alterando qualquer outra área.



<varlistentry>
<term>-p
<listitem>

Corrige automaticamente o sistema de arquivos sem perguntar.  É recomendável
fazer isto manualmente para entender o que aconteceu, em caso de problemas com
o sistema de arquivos.



<varlistentry>
<term>-v
<listitem>

Ativa o modo verbose (mais mensagens são mostradas durante a execução do
programa).



<varlistentry>
<term>-y
<listitem>

Assume <literal>sim para todas as questões.



</variablelist>

Caso sejam encontrados arquivos problemáticos e estes não possam ser
recuperados, o <command>fsck.ext2 perguntará se deseja salva-los no
diretório <filename>lost+found</filename>.  Este diretório é encontrado em
todas as partições **ext2**.  Não há risco de usar o
<command>fsck.ext3 em uma partição <literal>EXT2.


Após sua execução é mostrado detalhes sobre o sistema de arquivos verificado
como quantidade de blocos livres/ocupados e taxa de fragmentação.


Exemplos: <literal>fsck.ext2 /dev/hda2, <literal>fsck.ext2 -f
/dev/hda2, <literal>fsck.ext2 -vrf /dev/hda1.





 manut-checagem-reiserfsck">###reiserfsck

Verifica um sistema de arquivos <command>reiserfs em sistema de
arquivos.


<command>reiserfsck [**opções**]
[**dispositivo**]

<variablelist>
<varlistentry>
<term>**dispositivo**
<listitem>

Dispositivo que contém o sistema de arquivos <command>reiserfs que
será verificado.



<varlistentry>
<term>**opções**
<term>-a
<listitem>

Mostra detalhes sobre o sistema de arquivos e sai



<varlistentry>
<term>-j arquivo
<listitem>

Especifica um arquivo de Journal alternativo usado pelo sistema de arquivos.



<varlistentry>
<term>-q quiet
<listitem>

Não exibe mensagens sobre o status da checagem do sistema de arquivos.



<varlistentry>
<term>-S
<listitem>

Constrói a árvore de todos os blocos do dispositivo.



</variablelist>

O <command>reiserfsck possui outros modos de operação além de
checagem (o padrão), para detalhes veja a página de manual do programa.


Exemplos: <literal>reiserfsck /dev/hda1, <literal>reiserfsck -S
/tmp/arq-reiserfs.



 manut-checagem-minix">###fsck.minix

Verifica o sistema de arquivos **minix** em um dispositivo.


<command>fsck.minix [**opções**]
[**dispositivo**]


Onde:

<variablelist>
<varlistentry>
<term>dispositivo
<listitem>

Partição, disquete ou arquivo que contém o sistema de arquivos
<literal>Minix que será verificado



<varlistentry>
<term>opções
<term>-f
<listitem>

Verifica o sistema de arquivos mesmo se ele estiver perfeito.



<varlistentry>
<term>-r
<listitem>

Permite reparo manual do sistema de arquivos



<varlistentry>
<term>-a
<listitem>

Permite um reparo automático do sistema de arquivos.  É recomendado fazer o
reparo manual.



<varlistentry>
<term>-v
<listitem>

Verbose - Mostra detalhes durante a execução do programa



<varlistentry>
<term>-s
<listitem>

Exibe detalhes sobre os blocos de root.



</variablelist>

Exemplo: <literal>fsck.minix -f /dev/hda8, <literal>fsck.minix -vf
/dev/hda8



 manut-badblocks">###badblocks

Procura blocos defeituosos em um dispositivo.  Note que este **apenas** pesquisa por blocos defeituosos, sem alterar a
configuração do disco.  Para marcar os blocos defeituosos para não serem mais
usados, utilize a opção <literal>-l do <command>fsck (veja
<xref linkend="manut-checagem-ext2"/>).


<command>badblocks [**opções**] [**dispositivo**]


Onde:

<variablelist>
<varlistentry>
<term>dispositivo
<listitem>

Partição, disquete ou arquivo que contém o sistema de arquivos que será
verificado.



<varlistentry>
<term>opções
<term>-b [tamanho]
<listitem>

Especifica o [tamanho] do bloco do dispositivo em bytes



<varlistentry>
<term>-o [arquivo]
<listitem>

Gera uma lista dos blocos defeituosos do disco no [arquivo].  Este lista pode
ser usada com o programa <command>fsck.ext2 junto com a opção
<literal>-l.



<varlistentry>
<term>-s
<listitem>

Mostra o número de blocos checados durante a execução do
<command>badblocks.



<varlistentry>
<term>-v
<listitem>

Modo verbose - São mostrados mais detalhes.



<varlistentry>
<term>-w
<listitem>

Usa o modo leitura/gravação.  Usando esta opção o <command>badblocks
procura por blocos defeituosos gravando alguns padrões (0xaa, 0x55, 0xff, 0x00)
em cada bloco do dispositivo e comparando seu conteúdo.


Nunca use a opção <literal>-w em um dispositivo que contém arquivos
pois eles serão apagados!



</variablelist>

Exemplo: <literal>badblocks -s /dev/hda6, <literal>badblocks -s -o
bad /dev/hda6



 manut-defrag">###defrag

Permite desfragmentar uma unidade de disco.  A fragmentação é o armazenamento
de arquivos em áreas não seqüenciais (uma parte é armazenada no começo a outra
no final, etc), isto diminui o desempenho da unidade de disco porque a leitura
deverá ser interrompida e feita a movimentação da cabeça para outra região do
disco onde o arquivo continua, por este motivo discos fragmentados tendem a
fazer um grande barulho na leitura e o desempenho menor.


A desfragmentação normalmente é desnecessária no <command>GNU/Linux
porque o sistema de arquivos **ext2** procura automaticamente
o melhor local para armazenar o arquivo.  Mesmo assim, é recomendável
desfragmentar um sistema de arquivos assim que sua taxa de fragmentação subir
acima de 10%.  A taxa de fragmentação pode ser vista através do
<command>fsck.ext2.  Após o <command>fsck.ext2 ser
executado é mostrada a taxa de fragmentação seguida de
<literal>non-contiguos.


A ferramenta de desfragmentação usada no <command>GNU/Linux é o
<command>defrag que vem com os seguintes programas:

<itemizedlist>
<listitem>

<literal>e2defrag - Desfragmenta sistemas de arquivos
**Ext2**.


<listitem>

<literal>defrag - Desfragmenta sistemas de arquivos
**Minix**.


<listitem>

<literal>xdefrag - Desfragmenta sistemas de arquivos
**Xia**.




O sistema de arquivos deve estar desmontado ao fazer a desfragmentação.  Se
quiser desfragmentar o sistema de arquivos raíz (<filename>/</filename>), você
precisará inicializar através de um disquete e executar um dos programas de
desfragmentação apropriado ao seu sistema de arquivos.  A checagem individual
de fragmentação em arquivos pode ser feita com o programa
<command>frag.


ATENÇÃO: Retire cópias de segurança de sua unidade antes de fazer a
desfragmentação.  Se por qualquer motivo o programa de desfragmentação não
puder ser completado, você poderá perder dados!


<command>e2defrag [**opções**] [**dispositivo**]


Onde:

<variablelist>
<varlistentry>
<term>dispositivo
<listitem>

Partição, arquivo, disquete que contém o sistema de arquivos que será
desfragmentado.



<varlistentry>
<term>-d
<listitem>

Debug - serão mostrados detalhes do funcionamento



<varlistentry>
<term>-n
<listitem>

Não mostra o mapa do disco na desfragmentação.  É útil quando você inicializa
por disquetes e recebe a mensagem "Failed do open term Linux" ao tentar
executar o <command>e2defrag.



<varlistentry>
<term>-r
<listitem>

Modo somente leitura.  O defrag simulará sua execução no sistema de arquivos
mas não fará nenhuma gravação.  Esta opção permite que o defrag seja usado com
sistema de arquivos montado.



<varlistentry>
<term>-s
<listitem>

Cria um sumário da fragmentação do sistema de arquivos e performance do
desfragmentador.



<varlistentry>
<term>-v
<listitem>

Mostra detalhes durante a desfragmentação do sistema de arquivos.  Caso mais de
uma opção -v seja usada, o nível de detalhes será maior.



<varlistentry>
<term>-i [arquivo]
<listitem>

Permite definir uma lista de prioridades em que um arquivo será gravado no
disco, com isto é possível determinar se um arquivo será gravado no começo ou
final da unidade de disco.  Esta lista é lida do [arquivo] e deve conter uma
lista de prioridades de -100 a 100 para cada inodo do sistema de arquivos.
Arquivos com prioridade alta serão gravados no começo do disco.


Todos os inodos terão prioridade igual a zero caso a opção
<literal>-i não seja usada ou o inodo não seja especificado no
[arquivo].  O [arquivo] deverá conter uma série de linhas com um número (inodo)
ou um número prefixado por um sinal de igual seguido da prioridade.



<varlistentry>
<term>-p [numero]
<listitem>

Define o [numero] de buffers que serão usados pela ferramenta de
desfragmentação na realocação de dados, quanto mais buffers mais eficiente será
o processo de realocação.  O número depende de quantidade memória RAM e Swap
você possui.  Por padrão 512 buffers são usados correspondendo a 512Kb de
buffer (em um sistema de arquivos de blocos com 1Kb).



</variablelist>

Exemplo: <literal>e2defrag -n -v /dev/hdb4, <literal>e2defrag -r
/dev/hda1



 manut-hdbadblocks">###Verificando e marcando setores danificados em um HD

Um dos sintomas de um disco rígido que contém setores danificados (bad blocks)
é a mudança repentina do sistema de arquivos para o modo somente leitura, o
aparecimento de diversas mensagens no syslog indicando falha de leitura do hd,
uma pausa se segundos no sistema junto com o led de atividade de disco ligado.
Se isto acontece com você, uma forma de solucionar este inconveniente é
executar o teste na superfície física do disco para procurar e marcar os blocos
problemáticos como defeituosos.


Em alguns casos, os blocos defeituosos ocorrem isoladamente no disco rígido,
não aumentando mais sua quantidade, entretanto, se o número de blocos
danificados em seu disco está crescendo em um curto espaço de tempo, comece a
pensar na troca do disco rígido por um outro.  Existem empresas que recuperam
HDs mas pelo valor cobrado por se tratar de um serviço delicado, só compensa
caso você não tenha o backup e **realmente**
precisa dos dados do disco.


Para fazer uma checagem de HD no sistema de arquivos <filename>ext2</filename>
ou <filename>ext3</filename>, proceda da seguinte forma:

<itemizedlist>
<listitem>

Se possível, faça um backup de todos os dados ou dos dados essenciais da
partição será checada.


<listitem>

Inicie o sistema por um disquete de boot ou CD de recuperação.  Este passo é
útil pois em alguns casos, pode ocorrer a perda de interrupção do disco rígido
e seu sistema ficar paralisado.  Só o método de checar o HD usando um disquete
de boot lhe fará agendar uma parada no sistema e notificar os usuários,
evitando sérios problemas do que fazendo isto com um sistema em produção.


<listitem>

Execute o <command>badblocks usando a opção <literal>-o
para gravar os possíveis blocos defeituosos encontrados para um arquivo:
<literal>badblocks -v -o blocos-defeituosos.lista /dev/hd??.


Substitua o dispositivo <filename>/dev/hd??</filename> pelo dispositivo que
deseja verificar.  A checagem do <command>badblocks deverá ser feita
para cada partição existente no disco rígido.  O tempo de checagem dependerá da
velocidade do disco rígido, velocidade do barramento, cabo de dados utilizado,
velocidade de processamento e é claro, do estado do disco rígido (quantos
setores defeituosos ele tem).


<listitem>

Após concluir o <command>badblocks, veja se foram encontrados blocos
defeituosos.  Caso tenha encontrado, siga para o próximo passo.


<listitem>

Para marcar os blocos encontrados pelo <command>badblocks como
defeituosos, execute o comando: <literal>fsck.ext3 -l blocos-defeituosos.lista
-f /dev/hd??.


Substitua o dispositivo, pelo dispositivo que verificou com o
<command>badblocks.  O arquivo
<filename>blocos-defeituosos.list</filename> contém a lista de blocos gerada
pelo <command>badblocks que serão marcados como defeituosos.




Para mais detalhes sobre as opções de checagem usada pelos programas, veja
<xref linkend="manut-badblocks"e <xref linkend="manut-checagem-ext2"/>.



 manut-logs-l">###Limpando arquivos de LOGS

Tudo que acontece em sistemas <command>GNU/Linux pode ser registrado
em arquivos de log em <filename>/var/log</filename>, como vimos anteriormente.
Eles são muito úteis por diversos motivos, para o diagnóstico de problemas,
falhas de dispositivos, checagem da segurança, alerta de eventuais tentativas
de invasão, etc.


O problema é quando eles começam a ocupar muito espaço em seu disco.  Verifique
quantos Megabytes seus arquivos de LOG estão ocupando através do comando
<literal>cd /var/log;du -hc.  Antes de fazer uma limpeza nos arquivos
de LOG, é necessário verificar se eles são desnecessários e só assim zerar os
que forem dispensáveis.


Não é recomendável apagar um arquivo de log pois ele pode ser criado com
permissões de acesso indevidas (algumas distribuições fazem isso).  Você pode
usar o comando: <literal>echo -n &gt;arquivo ou o seguinte shell
script para zerar todos os arquivos de LOG de uma só vez (as linhas iniciante
com <literal># são comentários):

<screen>
#! /bin/sh
cd /var/log
for l in `ls -p|grep '/'`; do
 echo -n &gt;$l &amp;&gt;/dev/null
 echo Zerando arquivo $l...
done
echo Limpeza dos arquivos de log concluída!


Copie o conteúdo acima em um arquivo com a extensão <filename>.sh</filename>,
dê permissão de execução com o <command>chmod e o execute como
usuário <literal>root.  É necessário executar este script para zerar
arquivos de log em subdiretórios de <filename>/var/log</filename>, caso sejam
usados em seu sistema.


Algumas distribuições, como a <command>Debian GNU/Linux, fazem o
arquivamento automático de arquivos de LOGs em arquivos
<filename>.gz</filename> através de scripts disparados automaticamente pelo
<command>cron.  ATENÇÃO: LEMBRE-SE QUE O SCRIPT ACIMA APAGARÁ TODOS
OS ARQUIVOS DE LOGs DO SEU SISTEMA SEM POSSIBILIDADE DE RECUPERAÇÃO.  TENHA
ABSOLUTA CERTEZA DO QUE NÃO PRECISARÁ DELES QUANDO EXECUTAR O SCRIPT ACIMA!



 manut-recpart">###Recuperando partições apagadas

Caso tenha apagado uma partição acidentalmente ou todas as partições do seu
disco, uma forma simples de recuperar todos os seus dados é simplesmente
recriar todas as partições com o tamanho **EXATAMENTE** igual ao existente anteriormente.  Isto
deve ser feito dando a partida com um disquete ou CD de inicialização.  Após
recriar todas as partições e seus tipos (83, 82 8e, etc), execute novamente o
lilo para recriar o setor de boot do HD e garantir que a máquina dará o boot.


A recuperação desta forma é possível porque quando se cria ou apaga uma
partição, você está simplesmente delimitando espaço onde cada sistema de
arquivos gravará seus dados, sem fazer nenhuma alteração dentro dele.  Assim, é
também útil manter uma cópia dos tamanhos usados durante o processo de criação
das partições para ser usado como recuperação em uma possível emergência.



 manut-senhaperdida">###Recuperando a senha de root perdida

Uma situação que você deve ter se deparado (ou algum dia ainda vai se deparar)
é precisar alterar a senha de root e não sabe ou não lembra a senha atual.
Esta situação também pode ser encontrada quando ocorre uma falha de disco,
falha elétrica, reparos em uma máquina que não detém sua manutenção, etc.  A
melhor notícia é que a alteração da senha de root é possível e não apresenta
problema qualquer para o sistema.  Existem várias formas para se fazer isto, a
forma que descreverei abaixo assume que você tem acesso a um outro dispositivo
de partida que não seja o HD do Linux (**CD-ROM**,
**disquetes**, **outro disco rígido**, etc).
Assim, mesmo que encontre uma senha de BIOS em uma máquina, poderá colocar o
disco rígido em outra máquina e executar estes procedimentos.


**OBS:** Estes procedimentos tens fins didáticos
e administrativos, não sendo escritos com a intenção de fornecer mal uso desta
técnica.  Entender a exposição de riscos também ajuda a desenvolver novas
técnicas de defesa para sistemas críticos, e estas são totalmente possíveis e
as mais usadas documentadas neste guia.

<itemizedlist>
<listitem>

Como primeiro passo consiga um CD de partida ou disquete de uma distribuição
<command>Linux.  Normalmente os mesmos CDs que usou para instalar sua
distribuição também são desenvolvidos para permitir a manutenção do sistema,
contendo ferramentas diversas e um terminal virtual disponível para trabalhos
manuais (tanto de instalação como manutenção).


<listitem>

Vá até a BIOS da máquina e altere a ordem de inicialização para que seu sistema
inicialize a partir do disquete ou CD-ROM (dependendo do método escolhido no
passo anterior).


<listitem>

Inicialize a partir do Disquete/CD-ROM.


<listitem>

Na maioria dos casos você provavelmente estará utilizando o CD-ROM que usou
para instalar sua distribuição.  Imediatamente quando o programa de instalação
for iniciado, pressione **ALT**+**F2** para
alternar para o segundo terminal virtual do sistema.  O segundo terminal esta
sempre disponível nas distribuições distribuições <command>Debian,
<command>Red Hat, <command>Mandriva,
<command>Fedora, etc.


<listitem>

O próximo passo será montar sua partição raíz para ser possível alterar sua
senha de root.  Para isto, crie um diretório onde a partição será montada (por
exemplo, <filename>/target</filename>) e execute o comando mount:
<literal>mount /dev/hda1 /target (assumindo que
<filename>/dev/hda1</filename> é a partição que contém seu sistema de arquivos
raíz (<filename>/</filename>).


<listitem>

Entre no diretório <filename>/target</filename> (<literal>cd /target)
e torne-o seu diretório raíz atual com o comando: <literal>chroot ..


<listitem>

digite <literal>passwd e entre com a nova senha de superusuário.


<listitem>

saia do <command>chroot digitando <literal>exit


<listitem>

Digite <literal>sync para salvar todas as alterações pendentes para o
disco e reinicie o sistema (pressionando-se as teclas
<literal>CTRL+ALT+DEL, <literal>init 6,
<literal>reboot).


<listitem>

Retire o CD da unidade de discos e altere sua BIOS para dar a partida a partir
do disco rígido.


<listitem>

Teste e verifique se a senha de root foi alterada.




Normalmente as distribuições seguem o padrão FHS, mantendo binários de
administração necessários para recuperação do sistema em caso de panes dentro
da partição <filename>/</filename>, se este não for o caso de sua distribuição
(hoje em dia é raro), você terá que montar sistemas de arquivos adicionais
(como o <filename>/usr</filename>, <filename>/var</filename>) ou então o
comando <command>passwd não será encontrado ou terá problemas durante
sua execução.



 manut-tarefas">###Tarefas automáticas de manutenção do sistema

Os arquivos responsáveis pela manutenção automática do sistema se encontram em
arquivos individuais localizados nos diretórios
<filename>/etc/cron.daily</filename>, <filename>/etc/cron.weekly</filename> e
<filename>/etc/cron.montly</filename>.  A quantidade de arquivos depende da
quantidade de pacotes instalado em seu sistema, porque alguns programam tarefas
nestes diretórios e não é possível descrever todas, para detalhes sobre o que
cada arquivo faz veja o cabeçalho e o código de cada arquivo.


Estes arquivos são executados pelo <command>cron através do arquivo
<filename>/etc/crontab</filename>.  Você pode programar quantas tarefas
desejar, para detalhes veja <xref linkend="manut-cron"e <xref linkend="manut-at"/>.  Alguns programas mantém arquivos do
<command>cron individuais em
<filename>/var/spool/cron/crontabs</filename> que executam comandos
periodicamente.



 manut-cron">###cron

O <command>cron é um daemon que permite o agendamento da execução de
um comando/programa para um determinado dia/mês/ano/hora.  É muito usado em
tarefas de arquivamento de logs, checagem da integridade do sistema e execução
de programas/comandos em horários determinados.


As tarefas são definidas no arquivo <filename>/etc/crontab</filename> e por
arquivos individuais de usuários em
<filename>/var/spool/cron/crontabs/[usuário]</filename> (criados através do
programa <command>crontab).  Adicionalmente a distribuição
<command>Debian utiliza os arquivos no diretório
<filename>/etc/cron.d</filename> como uma extensão para o
<filename>/etc/crontab</filename>.


Para agendar uma nova tarefa, basta editar o arquivo
<filename>/etc/crontab</filename> com qualquer editor de texto (como o
<command>ae e o <command>vi) e definir o mês/dia/hora que a
tarefa será executada.  Não é necessário reiniciar o daemon do
<command>cron porque ele verifica seus arquivos a cada minuto.  Veja
a seção <xref linkend="manut-cron-formato"para entender o formato de arquivo
<command>cron usado no agendamento de tarefas.

 manut-cron-formato">###O formato de um arquivo crontab

O arquivo <filename>/etc/crontab</filename> tem o seguinte formato:

<screen>
52  18    1   *   *    root     run-parts --report /etc/cron.montly
|   |     |   |   |      |      |
|   |     |   |   |      |      \_Comando que será executado
|   |     |   |   |      |      
|   |     |   |   |      \_ UID que executará o comando
|   |     |   |   |            
|   |     |   |   \_ Dia da semana (0-7)
|   |     |   |
|   |     |   \_ Mês (1-12)
|   |     |
|   |     \_ Dia do Mês (1-31)
|   |
|   \_ Hora
|
\_ Minuto


Onde:

<variablelist>
<varlistentry>
<term>Minuto
<listitem>

Valor entre 0 e 59



<varlistentry>
<term>Hora
<listitem>

Valor entre 0 e 23



<varlistentry>
<term>Dia do Mês
<listitem>

Valor entre 0 e 31



<varlistentry>
<term>Mês
<listitem>

Valor entre 1 e 12 (identificando os meses de Janeiro a Dezembro)



<varlistentry>
<term>Dia da Semana
<listitem>

Valor entre 0 e 7 (identificando os dias de Domingo a Sábado).  Note que tanto
0 e 7 equivalem a Domingo.



<varlistentry>
<term>usuário
<listitem>

O usuário especificado será usado para executar o comando (o usuário deverá
existir).



<varlistentry>
<term>comando
<listitem>

Comando que será executado.  Podem ser usados parâmetros normais usados na
linha de comando.



</variablelist>

Os campos do arquivo são separados por um ou mais espaços ou tabulações.  Um
asterisco <literal>* pode ser usado nos campos de data e hora para
especificar todo o intervalo disponível.  O hífen <literal>- serve
para especificar períodos de execução (incluindo a o número inicial/final).  A
vírgula serve para especificar lista de números.  Passos podem ser
especificados através de uma <literal>/.  Veja os exemplos no final
desta seção.


O arquivo gerado em <filename>/var/spool/cron/crontabs/[usuário]</filename>
pelo <command>crontab tem o mesmo formato do
<filename>/etc/crontab</filename> exceto por não possuir o campo
<literal>usuário (UID), pois o nome do arquivo já identifica o
usuário no sistema.


Para editar um arquivo de usuário em
<filename>/var/spool/cron/crontabs</filename> ao invés de editar o
<filename>/etc/crontab</filename> use <literal>crontab -e, para
listar as tarefas daquele usuário <literal>crontab -l e para apagar o
arquivo de tarefas do usuário <literal>crontab -r (adicionalmente
você pode remover somente uma tarefa através do <literal>crontab -e e
apagando a linha correspondente).


OBS: Não esqueça de incluir uma linha em branco no final do arquivo, caso
contrário o último comando não será executado.


O <command>cron define o valor de algumas variáveis automaticamente
durante sua execução; a variável <filename>SHELL</filename> é definida como
<literal>/bin/sh, <filename>PATH</filename> como
<literal>/usr/bin:/bin, <filename>LOGNAME</filename>,
<filename>MAILTO</filename> e <filename>HOME</filename> são definidas através
do arquivo <filename>/etc/passwd</filename>.  Os valores padrões destas
variáveis podem ser substituídos especificando um novo valor nos arquivos do
<command>cron.


Exemplos de um arquivo <filename>/etc/crontab</filename>:

<screen>
SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

00 10  * * *  root sync
# Executa o comando sync todo o dia as 10:00
00 06  * * 1  root updatedb
# Executa o comando updatedb toda segunda-feira as 06:00.
10,20,40 *  * * *  root runq
# Executa o comando runq todos os dias e a toda a hora em 10, 20 e 40 minutos. 
*/10 *  * * *  root fetchmail
# Executa o comando fetchmail de 10 em 10 minutos todos os dias
15 0  25 12 * root echo "Feliz Natal"|mail john
# Envia um e-mail as 0:15 todo o dia 25/12 para john desejando um feliz natal. 
30 5  * * 1-6   root  poff
# Executa o comando poff automaticamente as 5:30 de segunda-feira a sábado.





 manut-at">###at

O <command>at agenda tarefas de forma semelhante ao
<command>cron com uma interface que permite a utilização de linguagem
natural nos agendamentos.  Sua principal aplicação é no uso de tarefas que
sejam disparadas somente uma vez.  Uma característica deste programa é a
execução de aplicativos que tenham passado de seu horário de execução, muito
útil se o computador é desligado com freqüência ou quando ocorre uma
interrupção no fornecimento de energia.


Para utilizar o <command>at, instale-o com o comando:
<literal>apt-get install at.  O próximo passo é criar os arquivos
<filename>/etc/at.allow</filename> e <filename>at.deny</filename>.  Estes
arquivos são organizados no formato de um usuário por linha.  Durante o
agendamento, é verificado primeiro o arquivo <filename>at.allow</filename>
(lista de quem pode executar comandos) e depois o <filename>at.deny</filename>
(lista de quem NÃO pode executar comandos).  Caso eles não existam, o
agendamento de comandos é permitido a todos os usuários.


Abaixo seguem exemplos do agendamento através do comando <command>at:

<variablelist>
<varlistentry>
<term>echo ls | at 10am today
<listitem>

Executa as 10 da manha de hoje



<varlistentry>
<term>echo ls | at 10:05 today
<listitem>

Executa as 10:05 da manha de hoje



<varlistentry>
<term>echo ls | at 10:05pm today
<listitem>

Executa as 10:05 da noite de hoje



<varlistentry>
<term>echo ls | at 22:05 today
<listitem>

Executa as 22:05 da noite de hoje



<varlistentry>
<term>echo ls | at 14:50 tomorrow
<listitem>

Executa o comando amanhã as 14:50 da tarde



<varlistentry>
<term>echo ls | at midnight
<listitem>

Executa o comando a meia noite de hoje



<varlistentry>
<term>echo ls | at midnight tomorrow
<listitem>

Executa o comando a meia noite de amanhã



<varlistentry>
<term>echo ls | at noon
<listitem>

Executa o comando de tarde (meio dia).



<varlistentry>
<term>at -f comandos.txt teatime
<listitem>

Executa os comandos especificados no arquivo "comandos.txt" no horário do café
da tarde (as 16:00 horas).



<varlistentry>
<term>at -f comandos.txt +3 minutes
<listitem>

Executa os comandos especificados no arquivo "comandos.txt" daqui a 3 minutos.
Também pode ser especificado "hours" ou "days".



<varlistentry>
<term>at -f comandos.txt tomorrow +3 hours
<listitem>

Executa os comandos especificados no arquivo "comandos.txt" daqui a 3 horas no
dia de amanhã.  (se agora são 10:00, ela será executada amanhã as 13:00 da
tarde).



</variablelist>

Todas as tarefas agendadas são armazenadas em arquivos dentro do diretório
<filename>/var/spool/cron/atjobs</filename>.  A sintaxe de comandos para
gerenciar as tarefas é semelhante aos utilitários do <command>lpd:
Para ver as tarefas, digite <literal>atq.  Para remover uma tarefa,
use o comando <literal>atrm seguido do número da tarefa obtida pelo
<literal>atq.



