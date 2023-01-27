<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" tasks">###Executando tarefas diversas no Linux

Este capítulo explica como realizar tarefas específicas no sistema, como gravar
um CD, assistir filmes, etc.  Ele também contém nomes de programas recomendados
tanto em modo texto como modo gráfico.


 tasks-cdwriting">###Gravando CDs e DVDs no Linux

A gravação de CDs no <command>Linux pode ser feita através dos
programas <command>cdrecord ou <command>CDRDAO e a gravação
de DVDs usando o <command>dvd+rw-tools.  Neste capítulo vou explicar
a gravação usando o <command>cdrecord para gravar um CD de dados e
audio e o <command>growisofs para a gravação de DVDs de dados.
Primeiro instale o <command>cdrecord, <command>mkisofs,
<command>dvd+rw-tools e <command>cdda2wav em sua máquina
(<literal>apt-get install cdrecord dvd+rw-tools mkisofs cdda2wav).


 tasks-cdwriting-data">###Gravando CDs / DVDs de dados

O processo de gravação de um CD/DVD de dados é feito em 2 etapas: primeiro é
gerado um arquivo ISO com o programa <command>mkisofs que será a
imagem exata do CD que será gravado e a gravação usando o
<command>cdrecord ou <command>growisofs (DVD).  Caso ainda
não tenha configurado seu gravador no <command>Linux ou não tem
certeza do seu funcionamento, veja <xref linkend="hardw-cfgdisp-cdwritter"/>.


Vou assumir que os dados que deseja gravar estão no diretório
<filename>/dados</filename>.  Primeiro gere o arquivo ISO:

<screen>
cd /dados
mkisofs -r -o dados.iso -J -V"CD_DADOS" .


Na linha acima, você permite que todos possam ler o CD alterando as permissões
(<literal>-r), o arquivo de saída será <filename>dados.iso</filename>
(<literal>-o <filename>dados.iso</filename>), os nomes também terão o
índice no formato Joliet (<command>Windows) (<literal>-J),
o nome de volume será **CD_DADOS**
(<literal>-V"CD_DADOS").  Foi colocado <literal>. para o
diretório raíz porque estamos dentro do diretório que queremos gravar dados.
Não us e "*" para especificar os arquivos, a não ser que queira que todos os
arquivos do seus subdiretórios fiquem dentro do raíz do CD :-)


Antes de gravar você pode testar se o conteúdo do CD está OK montando a imagem
ISO:

<screen>
mkdir /tmp/iso
mount /dados/dados.iso /tmp/iso -o loop -t iso9660


Você poderá entrar no diretório <filename>/tmp/iso</filename> e ver como está o
conteúdo do seu CD antes da gravação.  Qualquer modificação deverá ser feita no
diretório <filename>/dados</filename> e depois gerar novamente o iso com
<command>mkisofs.  Desmonte o arquivo ISO antes de gravar o CD.


Agora, para gravar um CD (750Mb) execute o comando:

<screen>
cdrecord -v -dev=/dev/hdc -data /dados/dados.iso


O <literal>-v mostra a progressão da gravação.  Caso seu gravador de
CD esteja configurado com emulação SCSI ou SCSI, o número passado como
argumento a <literal>-dev deverá ser obtido pelo comando
<literal>cdrecord -scanbus (por ex.  <literal>0,0,0).  A
opção <literal>-data especifica o arquivo iso que contém os dados que
serão gravados.


Para gravar um DVD, execute o comando:

<screen>
growisofs -Z /dev/hdc=/dados/dados.iso


Após isto seu CD ou DVD estará gravado e pronto para uso.



 tasks-cdwriting-audio">###Gravando um CD de audio

A gravação de um CD de audio se divide em 2 etapas: Extração das trilhas de
audio para um diretório em formato <replaceable>wav</replaceable> e a gravação.
Após inserir o CD de audio na unidade, a extração é feita pelo programa
<command>cdda2wav da seguinte forma:

<screen>
mkdir /audio
cd /audio
cdda2wav -x -D/dev/cdrom -d99999 -S4 -Owav -B audio


A opção <literal>-x extrai usando máxima qualidade,
<literal>-D/dev/cdrom diz qual é o dispositivo onde o CD de audio
está inserido, <literal>-d99999 diz a duração total da extração
(99999 é um valor que garante a extração de TODO o CD), <literal>-S4
diz que a velocidade de extração será de 4X, a <literal>-B audio diz
para criar arquivos contendo as faixas seqüencialmente como
<filename>audio01.wav</filename>, <filename>audio02.wav</filename>, etc.


Após extrair, você deverá executar o comando:

<screen>
cdrecord -v -dev=/dev/hdc -dao -useinfo *.wav


O comando acima usa o dispositivo gravador /dev/hdc para fazer a gravação do CD
de audio.  O formato usado é o DAO (<literal>-dao), o que garante que
não haverá intervalo entre as faixas de CD, útil em CDs ao vivo e que os
arquivos <filename>*.inf</filename> contendo os dados das faixas serão usados
para controlar a duração de cada uma (-useinfo *.wav).


Se você quer gravar uma seleção de arquivos <filename>.wav</filename> ou
<filename>.cdr</filename>, será preciso faze-lo em modo TAO (track at once),
mantendo a pausa de 2 segundos entre as músicas.  Isto é feito pelo comando:

<screen>
cdrecord -v -dev=/dev/hdc -pad -audio *.wav


Estamos dizendo para o <command>cdrecord gravar diversos arquivos de
audio (<literal>-audio *.wav) e preencher os intervalos dos arquivos
de audio com zeros (<literal>-pad) pois nem sempre os arquivos tem o
múltiplo de setores requeridos para a gravação de arquivos de audio.



 tasks-cdwriting-cdcd">###Cópia de CD para CD no mesmo gravador

A cópia de CD/DVD de dados para outro é feita em duas etapas: A extração do
arquivo ISO e a gravação do CD.  Esse recurso é útil pela economia de tempo que
proporciona e porque mantém características especiais do CD como setor de boot.


Primeiro, extraia o conteúdo do CD/DVD em format raw com o comando:

<screen>
dd if=/dev/cdrom of=/dados/arquivo.iso


Confira se no final o número de bytes conferem, isso diz que a extração foi
feita com sucesso.  O parâmetro <literal>if= indica o arquivo de
entrada e <literal>of= o arquivo de saída.  Depois disso grave o CD
ou DVD com o comando:

<screen>
(Para gravação de CD (750Mb)
cdrecord -v -dev=/dev/hdc -data /dados/dados.iso

(Para gravação de DVD)
groisofs -Z /dev/hdc=/dados/dados.iso


Veja a explicação dos parâmetros em <xref linkend="tasks-cdwriting-data"/>.
Note que você também poderá gravar o CD usando o comando <command>dd:

<screen>
dd if=/dados/arquivo.iso of=/dev/sr0



 tasks-cdwriting-massivewrite">###Gravação massiva de CDs

Isso é feito pelo programa <command>cdcontrol que permite a gravação
de CDs paralelamente, sendo bastante útil para gerar CDs para install fests,
distribuições comerciais em massa.  Ele mantém um relatório de CDs totais por
unidade de disco e também de falhas, também permite a cópia de CDs de
inicialização.  Ele está disponível em ("http://www.w3.org/1999/xlink) [](http://cdcontrol.sourceforge.net)http://cdcontrol.sourceforge.net/.
Ele também está disponível como pacote <filename>.deb</filename>
(<literal>apt-get install cdcontrol).



 tasks-cdwriting-cdfrommp3">###Gravação de CDs diretamente através de arquivos mp3 ou Ogg

Utilize o aplicativo <command>mp3burn para fazer isto.  Por exemplo:

<screen>
mp3burn -o "-v -dev=/dev/hdc" *.mp3


A opção <literal>-o indica as opções que devem ser passadas ao
<command>cdrecord.  A opção <literal>-audio e
<literal>-pad são adicionadas automaticamente.



 tasks-cdwriting-backupcd">###Backup de dados para 1 ou mais CDs

O programa <command>multicd é a ferramenta que permite esta função.



 tasks-cdwriting-graphicapps">###Aplicações gráficas para gravação de CDs

Os seguintes aplicativos são interfaces gráficas e amigáveis que usam o
<command>cdrecord, <command>cdda2wav e
<command>mkisofs para fazer a gravação de seus CDs.  Normalmente eles
acrescentam uma carga maior para a máquina, mas se você gosta de uma interface
amigável para fazer as coisas, ter animações, etc.  o preço que paga é a
performance :-)


Entre os principais programas, destaco os seguintes:
<command>cdrtoaster, <command>cdbakeoven,
<command>kreatecd, <command>gcombust.



 tasks-cdwriting-cover">###Criar a capa de frente e verso do CD/DVD

Capas de frente e verso podem ser produzidas com o
<command>cdlabelgen.





 tasks-cdwriting-rundivx">###Executando vídeos DIVX

O programa mais recomendado é o <command>mplayer.  Após instalar,
execute o comando: <literal>mplayer -framedrop -vo xv arquivo.avi.  A
opção <literal>-framedrop diz ao <command>mplayer pular
frames que ele não conseguir exibir (útil em sistemas que tem CPU lenta).


O <command>gmplayer é a interface gráfica do
<command>mplayer e aceita todos os seus parâmetros.



 tasks-rundvd">###Assistindo DVDs

Para assistir filmes em DVD recomendo os seguintes programas:
<command>ogle, <command>xine e <command>mplayer.
Lembre-se de fazer um link de <filename>/dev/dvd</filename> para seu
dispositivo leitor de DVD antes de executar um destes programas.



 tasks-wavtomp3">###Convertendo músicas no formato wav para mp3

A conversão é explicada aqui usando o programa <command>bladeenc.
Você pode baixa-lo de ("http://www.w3.org/1999/xlink) [](http://bladeenc.mp3.no)http://bladeenc.mp3.no/.  O
<command>bladeenc foi o escolhido por apresentar a melhor performance
e qualidade para conversão da músicas, que é importante para quem tem máquinas
menos potentes e processamento leve é valioso para você :-)


A conversão é feita da seguinte forma:

<screen>
bladeenc -progress=4 -del *.wav


A opção <literal>-del diz para apagar os arquivos
<filename>.wav</filename> a medida que são convertidos e
<literal>-progress=4 para mostrar uma barra de progresso total e
outra do arquivo que está sendo processado.



 tasks-mp3cdr">###Convertendo músicas do formato mp3 para cdr

Esta conversão necessária quando deseja gravar um CD de audio a partir de uma
seleção de músicas MP3.  As explicações aqui são baseadas no programa
<command>mpg123, que pode ser instalado com <literal>apt-get install
mpg123.  Execute o seguinte comando para fazer a conversão:

<screen>
mpg123 --cdr - arquivo.mp3 &gt;arquivo.cdr


Para fazer a conversão de todos os arquivos <filename>mp3</filename> dentro de
um diretório, use o comando:

<screen>
for MUSICA in *.mp3; do
 mpg123 --cdr - "$MUSICA" &gt;"${VAR}.cdr"
done


Após feita a conversão de músicas necessárias para completar um CD (normalmente
600MB), vá até <xref linkend="tasks-cdwriting-audio"/>.




