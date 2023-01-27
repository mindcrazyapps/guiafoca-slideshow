<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cfg">###Configuração do sistema

Este capítulo traz explicações sobre algumas configurações úteis que podem ser
feitas no sistema.  Neste documento assumimos que o kernel do seus sistema já
possui suporte a página de código 860 (Portuguesa) e o conjunto de caracteres
<literal>ISO-8859-1.



 userlevel='inic;inter' cfg-acentuacao">###Acentuação

Permite que o <command>GNU/Linux use a acentuação.  A acentuação do
modo texto é independente do modo gráfico; você pode configurar tanto um como o
outro ou ambos.  Para maiores detalhes veja <xref linkend="cfg-acentuacao-t"/>
e/ou <xref linkend="cfg-acentuacao-g"/>.

<!-- [ %OBS [ -->

Note que os mapas de teclado usados em modo texto são diferentes dos usados em
modo gráfico.  Geralmente os mapas de teclados para o modo gráfico tem uma
letra <literal>X no nome.

<!-- ]]> -->


	<!-- [ %DEBIAN [ -->

 cfg-acentuacao-t">###Acentuação em modo Texto

Caso sua distribuição <command>Debian esteja acentuando corretamente
no modo texto você não precisará ler esta seção.  Antes de prosseguir,
verifique se você possui o pacote <systemitem role="package">console-data</systemitem> instalado em seu sistema com o
comando: <literal>dpkg -l console-data.  Caso não existam, alguns
programas de configuração e arquivos de fontes não estarão disponíveis.


Siga os passos abaixo para colocar e acentuação em funcionamento para o modo
Texto na <command>Debian:

<variablelist>
<varlistentry>
<term>**Mapa de Teclados**
<listitem>
<variablelist>
<varlistentry>
<term>Debian 4 ou 5
<listitem>

Digite <literal>dpkg-reconfigure console-data.  Após a tela inicial,
selecione a opção <literal>Selecionar o mapa de teclados da lista de
arquiteturas, <literal>qwerty e selecione os passos
seguintes de acordo com seu tipo de teclado:

<itemizedlist>
<listitem>

<literal>US american - Selecione <literal>US American na
lista de opções e em seguida <literal>Standard e <literal>US
International (ISO-8859-1).


<listitem>

<literal>ABNT2 (com cedilha) - Selecione <literal>Brazilian
na lista de opções.





</variablelist>

Após isso, o mapa de teclados correto será carregado de
<filename>/usr/share/keymaps</filename> e será ativado no sistema.


Se desejar usar o comando <literal>loadkeys manualmente , você
precisa copiar o mapa de teclados para um local conhecido no sistema, então
copie o arquivo <filename>arquivo.kmap</filename> para
<filename>/usr/share/keymaps/i386/qwerty</filename> (em sistemas Debian) ou
algum outro local apropriado.  
<!-- [ %INTERMEDIARIO [ --> Note que o arquivo pode ser compactado pelo
<command>gzip e copiado para
<filename>/usr/share/keymaps/i386/qwerty</filename> que será lido sem problemas
pelo sistema encarregado de configurar o teclado e acentuação. <!-- ]]> -->



<varlistentry>


<term>**Configurando a fonte de Tela**
<listitem>

Descomente a linha <literal>SCREEN_FONT=LatArCyrHeb-16 e modifique-a
para <literal>CONSOLE_FONT=lat1u-16.psf no arquivo
<filename>/etc/console-tools/config</filename>.


Esta linha diz ao sistema que **fonte** deve carregar para
mostrar os caracteres na tela.  A fonte de caracteres deve ser compatível com o
idioma local, pois nem todas suportam caracteres acentuados.  A fonte
preferível para exibir os caracteres acentuados usando padrão ISO é a
<filename>lat1u-16</filename>, o <filename>-16</filename> no nome do arquivo
significa o tamanho da fonte.  As fontes de tela estão disponíveis no diretório
<filename>/usr/share/consolefonts</filename>.


Neste ponto você pode verificar se o seu sistema esta reconhecendo corretamente
a acentuação entrando no editor de textos <command>ae e digitando:
<literal>áãâà.  Se todos os acentos apareceram corretamente,
parabéns!  você já passou pela parte mais difícil.  Agora o próximo passo é a
acentuação no <command>Bash.



<varlistentry>
<term>**Acentuação no aviso de comando (<command>bash)**
<listitem>

Para acentuar no <command>Bash (interpretador de comandos) é
necessário alterar o arquivo <filename>/etc/inputrc</filename> e fazer as
seguintes modificações:

<orderedlist numeration="arabic">
<listitem>

Descomente a linha: <literal>"#set convert-meta off" você faz isto
apagando o símbolo "#" antes do nome.


Um comentário faz com que o programa ignore linha(s) de comando.  É muito útil
para descrever o funcionamento de comandos/programas (você vai encontrar muito
isso no sistema <command>GNU/Linux, tudo é muito bem documentado).


<listitem>

Inclua a seguinte linha no final do arquivo:


set meta-flag on


<listitem>

O conteúdo deste arquivo deve ficar assim:

<screen>
set convert-meta off
set input-meta on
set output-meta on


<listitem>

Digite <literal>exit ou pressione
<literal>CTRL+<literal>D para fazer o logout.  Entre
novamente no sistema para que as alterações façam efeito.


</orderedlist>


</variablelist>

Pronto!  você já esta acentuando em modo texto!.  Talvez seja necessário que
faça alguma alteração em arquivos de configuração de outros programas para que
possa acentuar corretamente (veja se existe algum arquivo com o nome
correspondente ao programa no diretório <filename>/etc</filename>).


A distribuição <command>Debian também traz o utilitário
<command>kbdconfig que também faz a configuração do mapa de teclados
de forma interativa e gravando automaticamente o mapa de teclados em
<filename>/etc/kbd/default.map.gz</filename>.  Se preferir usar o
<command>kbdconfig ainda será necessário executar os passos acima
para habilitação da fonte <filename>lat1u-16</filename> e acentuação no
<command>bash.


	<!-- ]]> -->


 cfg-acentuacao-g">###Acentuação em modo gráfico

A acentuação no modo gráfico é feita de maneira simples:
<!-- [ %DEBIAN [ -->

<variablelist>
<varlistentry>
<term>**Configuração do mapa de teclados**
<listitem>

Execute o comando <literal>dpkg-reconfigure xserver-xorg e informe o
tipo de teclado quando perguntado pelo sistema de configuração.  A configuração
será gravada na seção <literal>InputDevice do arquivo
<filename>/etc/X11/xorg.conf</filename> e poderá ser modificada manualmente se
necessário.



</variablelist>
<!-- ]]> -->



	<!-- ]]> -->


	<!-- [ %INIC-INTER [ -->
 cfg-cores">###Número de Cores do ambiente gráfico

O número de cores do ambiente gráfico pode ser alterado facilmente.
Normalmente as distribuições realizam a instalação usando o padrão VESA (que é
compatível com qualquer placa de vídeo) usando 65.000 cores (16 bits), mas por
usar VESA são deixados de lado recursos como aceleração de hardware, XV, e
recursos 3D necessário pela maioria dos jogos e aplicativos de vídeo atuais.


A configuração apropriada do driver exige que você execute novamente o
procedimento de configuração da distribuição usando o comando
<literal>dpkg-reconfigure xserver-xorg.


Por exemplo, para configurar minha placa de vídeo Intel 810, é necessário
selecionar o driver i810 na tela de seleção do driver de video do
<literal>dpkg-reconfigure xserver-xorg.  O programa
<command>xresprobe pode ser útil caso deseja fazer manualmente
ajustes finos na configuração do <filename>/etc/X11/xorg.conf</filename>.  O
monitor também poderá ser configurado de acordo com o tamanho da tela (em
polegadas).


Com uma configuração correta é possível atingir até 32 bits de cores (pocket
pixel) no X.  A configuração do X utiliza o **número de bits**
ao invés do número de cores na sua configuração.  Abaixo uma tabela
comparativa:

<screen>
  Bits      Número Max. Cores  Memória mínima requerida na Placa de Vídeo
-------     -----------------  -----------------------------------------
 4 bits         16 cores                          256Kb
 8 bits        256 cores                          512Kb
16 bits      32.384/65536 cores                   1MB
24 bits      16 milhões de cores (pixel menor)    1MB
32 bits      16 milhões de cores                  1MB


Lembre-se que a tabela acima leva em consideração a resolução de vídeo de
640x480.  Caso utilizar uma resolução de 800x600, 1024x768 ou superior, os
requerimentos de **memória de vídeo** para mostrar o número de
cores da tabela acima serão maiores.  Para mostrar 1024x768 - 16 milhões de
cores serão necessários 2MB de memória de vídeo, por exemplo.  A resolução de
24 bits normalmente traz problemas em alguns chipsets, considere a utilização
da resolução de 16 ou 32 bits.


O uso de uma resolução de vídeo como 800x600 ou superior, também depende do
monitor de vídeo.  Nem todos os monitores VGA e SVGAs do mercado suportam
resoluções acima de 640x480.

<!-- [ %OBS [ -->

OBS: Se tiver escolha, prefira placas de vídeo independentes da placa mãe.
Normalmente as placas de vídeo on-board usam parte da memória RAM como memória
de vídeo (memória compartilhada) e isto diminui a performance de vídeo e a
performance do sistema porque se você estiver usando 2MB de memória de vídeo,
terá 2 MB a menos para executar seus programas.  O preço destas placas
geralmente diminui na proporção do desempenho que oferecem.

<!-- ]]> -->

Uma boa escolha para uma melhor qualidade e maior velocidade é **16
bits**.  O motivo disto é que quanto maior a qualidade e a resolução,
mais tempo será levado para os pixels serem atualizados no monitor.  Veja
abaixo como configurar o número de cores para quem esta iniciando o X-Window
pelo modo texto e <command>XDM.



 cfg-cores-t">###Configurando o número de cores para quem inicia pelo prompt

Após configurar corretamente a resolução de vídeo aceita pelo seu servidor X
com <literal>dpkg-reconfigure xserver-xorg (Debian 4.0) use o comando
<literal>startx -- -bpp 8 no lugar de <literal>startx.
Note que estou usando 256 cores como exemplo (veja a tabela acima), se quiser
usar mais cores e sua placa de vídeo tiver memória suficiente, use 16, 24 ou
32.


Uma maneira mais prática de iniciar sempre com uma mesma resolução é incluir um
<command>alias no arquivo <filename>.bashrc</filename> em seu
diretório: <literal>alias startx='startx -- -bpp 8'


Desta forma toda a vez que se digitar <literal>startx, será executado
o comando da direita do sinal de igual.

<!-- [ %OBS [ -->

OBS: Se alguma coisa der errado e a imagem aparecer distorcida ou simplesmente
não aparecer, não se desespere!  Pressione simultaneamente
<literal>CTRL+ALT+Back Space, esta é a combinação de teclas finaliza
imediatamente o servidor X.

<!-- ]]> -->



 cfg-configurando-g">###Configurando o número de cores para quem inicia pelo XDM

Assumindo que o seu arquivo <filename>/etc/X11/xorg.conf</filename> foi gerado
corretamente, modifique o arquivo 
<!-- [ %DEBIAN [ --> <filename>/etc/X11/xdm/Xservers</filename> <!-- ]]> --> e
altere o final da linha colocando <literal>-bpp resolução.  Por
exemplo, a última linha de meu arquivo <filename>Xservers</filename> era:

<screen>
:0 local /usr/bin/X11/X vt7 

 eu a modifiquei para 

:0 local /usr/bin/X11/X vt7 -bpp 16


Pronto, basta reiniciar o servidor X (usando <literal>CTRL+ALT+Back
Space) 
<!-- [ %DEBIAN [ --> ou reiniciando através do arquivo
<filename>/etc/init.d/xdm</filename> usando <literal>xdm restart <!-- ]]> --> 
e seu sistema passará a usar 65.000 cores de vídeo.

<!-- [ %OBS [ -->

OBS: Lembre-se de salvar todos os seus arquivos antes de reiniciar o servidor
X, pois todos os programas que estiverem abertos no sistema serão imediatamente
fechados.

<!-- ]]> -->



 s24.2.3">###Ajustando o alinhamento da imagem no X e outras configurações

Após você ter criado o arquivo de configuração do X com o
<literal>dpkg-reconfigure xserver-xorg, é possível que a configuração
precise de um ajuste fino para o alinhamento correto da imagem no monitor.
Muitos monitores modernos possuem teclas para esta função, mas desde que
monitor esteja com sua imagem aparecendo corretamente em modo texto, o ajuste
deverá ser feito no servidor X.  Este ajuste é feito através do utilitário
<command>xvidtune.


Entre no modo gráfico como usuário <literal>root, abra o
<command>xterm e digite <literal>xvidtune uma tela
aparecerá com um aviso sobre o uso do programa, clique em
<command>OK.  Recomendo que ative o botão <literal>AUTO
para que a tela vá se ajustando na medida que você mexe nos ajustes.


Para restaurar a configuração anterior, pressione o botão
<literal>Restore (não faz efeito caso o botão
<literal>Apply tenha sido pressionado).  Clicando em
<literal>Quit, você sai do <command>xvidtune sem salvar a
configuração.  Quando estiver satisfeito com a sua configuração/alinhamento da
imagem, clique em <literal>Apply, a configuração escolhida estará
salva.




	<!-- ]]> -->

