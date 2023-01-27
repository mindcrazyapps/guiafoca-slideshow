<!-- Converted by db4-upgrade version 1.0 -->
chapter <!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" impr">###Impressão

Este capitulo descreve como imprimir em seu sistema
<command>GNU/Linux e as formas de impressão via spool, rede, gráfica,
etc.


Antes de seguir os passos descritos neste capítulo, tenha certeza que seu
kernel foi compilado com o suporte a impressora USB e/ou paralela ativado, caso
contrário até mesmo a impressão direta para a porta de impressora falhará.
<!-- [ %INTERMEDIARIO [ --> Para detalhes veja <xref linkend="kern-recompilando"/>. <!-- ]]> -->



 impr-portas">###Portas de impressora

Uma porta de impressora é o local do sistema usado para se comunicar com a
impressora.  Em sistemas <command>GNU/Linux, a porta de impressora
paralela é identificada como <filename>lp0, lp1, lp2</filename> no diretório
<filename>/dev</filename>, caso a impressora seja USB, o dispositivo será o
mesmo, mas estará disponível no diretório <filename>/dev/usb</filename>.  Os
dispositivos <filename>lp0, lp1 e lp2</filename> correspondem respectivamente a
<filename>LPT1</filename>, <filename>LPT2</filename> e
<filename>LPT3</filename> no <command>DOS e
<command>Windows.  Recomendo que o suporte a porta paralela esteja
compilado como módulo no kernel.




 impr-direta">###Imprimindo diretamente para a porta de impressora

Isto é feito direcionando a saída ou o texto com <literal>&gt;
diretamente para a porta de impressora no diretório <filename>/dev</filename>.


Supondo que você quer imprimir o texto contido do arquivo
<filename>trabalho.txt</filename> e a porta de impressora em seu sistema é
<filename>/dev/usb/lp0</filename>, você pode usar os seguintes comandos:

<itemizedlist>
<listitem>

<literal>cat trabalho.txt &gt;/dev/usb/lp0 - Direciona a saída do
comando <command>cat para a impressora USB conectada em lp0.


<listitem>

<literal>cat &lt;trabalho.txt &gt;/dev/usb/lp0.  Faz a mesma coisa
que o acima.


<listitem>

<literal>cat -n trabalho.txt &gt;/dev/usb/lp0 - Numera as linhas
durante a impressão.


<listitem>

<literal>head -n 30 trabalho.txt &gt;/dev/usb/lp0 - Imprime as 30
linhas iniciais do arquivo.


<listitem>

<literal>cat trabalho.txt|tee /dev/usb/lp0 - Mostra o conteúdo do
<command>cat na tela e envia também para a impressora USB.




Os métodos acima servem somente para imprimir em modo texto (letras, números e
caracteres semi-gráficos).


OBS: Note que a impressora somente imprimirá diretamente a partir da porta,
caso ela seja uma impressora com firmware interna (impressora inteligente).
Algumas impressoras mais recentes (principalmente os modelos mais baratos)
somente imprimem caso estejam configuradas com o respectivo driver (Win
Printers ou impressoras via software), e nunca aceitarão o comando diretamente
para a porta de impressão.  Para **Win Printers**, a melhor
alternativa de configuração de funcionamento será através do CUPS (Common Unix
Print System).




 impr-spool">###Imprimindo via spool

A impressão via spool (fila de impressão) tem por objetivo liberar logo o
programa do serviço que está fazendo a impressão deixando um outro programa
especifico tomar conta.


Este programa é chamado de **daemon de impressão**,
normalmente é o <command>lpr ou o <command>lprng
(recomendado) em sistemas <command>GNU/Linux.


Logo após receber o arquivo que será impresso, o programa de spool gera um
arquivo temporário (normalmente localizado em
<filename>/var/spool/lpd</filename>) que será colocado em fila para a impressão
(um trabalho será impresso após o outro, em seqüência).  O arquivo temporário
gerado pelo programa de spool é apagado logo após concluir a impressão.


Antes de se imprimir qualquer coisa usando os daemons de impressão, é preciso
configurar os parâmetros de sua impressora no arquivo
<filename>/etc/printcap</filename>.  Um arquivo
<filename>/etc/printcap</filename> para uma impressora local padrão se parece
com o seguinte:

<screen>
lp|Impressora compatível com Linux
 :lp=/dev/lp0
 :sd=/var/spool/lpd/lp
 :af=/var/log/lp-acct
 :lf=/var/log/lp-errs
 :pl#66
 :pw#80
 :pc#150
 :mx#0
 :sh


É possível também compartilhar a impressora para a impressão em sistemas
remotos, isto será visto em uma seção separada neste guia.


Usando os exemplos anteriores da seção <literal>Imprimindo diretamente para uma
porta de impressora, vamos acelerar as coisas:

<itemizedlist>
<listitem>

<literal>cat trabalho.txt |lpr - Direciona a saída do comando
<command>cat para o programa de spool <command>lpr.


<listitem>

<literal>cat &lt;trabalho.txt |lpr.  Faz a mesma coisa que o acima.


<listitem>

<literal>cat -n trabalho.txt |lpr - Numera as linhas durante a
impressão.


<listitem>

<literal>head -n 30 trabalho.txt |lpr - Imprime as 30 linhas iniciais
do arquivo.




A fila de impressão pode ser controlada com os comandos:

<itemizedlist>
<listitem>

<literal>lpq - Mostra os trabalhos de impressão atuais


<listitem>

<literal>lprm - Remove um trabalho de impressão




Ou usado o programa de administração <command>lpc para gerenciar a
fila de impressão (veja a página de manual do <command>lpc ou digite
<literal>? ao iniciar o programa para detalhes).

<!-- [ %INTER-AVANC [ -->

OBS1: Se a impressora não imprimir ou não for possível compartilhar a porta de
impressora paralela com outros dispositivos (tal como o
**plip**), verifique se o módulo
**parport_pc** foi carregado e com os valores de irq e I/O
corretos (por exemplo, <literal>modprobe parport_pc io=0x378 irq=7).
Muitas vezes sua porta paralela pode funcionar sem problemas durante a
impressão, mas se ao utilizar plip ocorrerem erros, a causa pode ser essa.  
<!-- [ %DEBIAN [ --> Na distribuição <command>Debian, use o programa
<command>modconf para configurar os valores permanentemente para o
módulo parport_pc. <!-- ]]> -->


OBS2: Se tiver mais de uma impressora instalada na máquina, será necessário
especificar a opção "-P impressora" para especificar qual impressora deseja
imprimir/controlar.

<!-- ]]> -->



 impr-graficos">###Impressão em modo gráfico

A impressão em modo gráfico requer que conheça a marca e modelo de sua
impressora e os métodos usados para imprimir seus documentos.  Este guia
abordará somente a segunda recomendação :-)



 impr-ghostscript">###Ghost Script

O método mais usados pelos aplicativos do <command>GNU/Linux para a
impressão de gráficos do **Ghost Script**.  O Ghost Script
(chamado de **gs**) é um interpretador do formato
**Pos Script** (arquivos <filename>.ps</filename>) e pode
enviar o resultado de processamento tanto para a tela como impressora.  Ele
está disponível para diversas plataformas e sistema operacionais além do
<command>GNU/Linux, inclusive o <command>DOS,
<command>Windows, <command>OS/2, etc.


O formato <filename>.ps</filename> esta se tornando uma padronização para a
impressão de gráficos em <command>GNU/Linux devido a boa qualidade da
impressão, liberdade de configuração, gerenciamento de impressão feito pelo
**gs** e por ser um formato universal, compatíveis com outros
sistemas operacionais.


Para imprimir um documento via Ghost Script, você precisará do pacote
<systemitem role="package">gs</systemitem>, <systemitem role="package">gsfonts</systemitem> (para a distribuição
<command>Debian e distribuições baseadas, ou outros de acordo com sua
distribuição Linux) e suas dependências.  A distribuição
<command>Debian vem com vários exemplos Pos Script no diretório
<filename>/usr/share/doc/gs/example</filename> que são úteis para o aprendizado
e testes com o Ghost Script.


Hora da diversão:

<itemizedlist>
<listitem>

Copie os arquivos <filename>tiger.ps.gz</filename> e
<filename>alphabet.ps.gz</filename> do diretório
<filename>/usr/share/doc/gs/examples</filename> (sistemas
<command>Debian) para <filename>/tmp</filename> e descompacte-os com
o comando <command>gzip -d tiger.ps.gz e gzip -d alphabet.ps.gz.  Se
a sua distribuição não possui arquivos de exemplo ou você não encontra nenhuma
referência de onde se localizam, mande um e-mail que os envio os 2 arquivos
acima (são 32Kb).


<listitem>

O Ghost Script requer um monitor EGA, VGA ou superior para a visualização dos
seus arquivos (não tenho certeza se ele funciona com monitores CGA ou Hércules
Monocromático) .


Para visualizar os arquivos na tela digite:

<screen>
gs tiger.ps 
gs alphabet.ps


Para sair do <command>Ghost Script pressione
<literal>CTRL+C.  Neste ponto você deve ter visto um desenho de um
tigre e (talvez) letras do alfabeto.


Se o comando <literal>gs alphabet.ps mostrou somente uma tela em
branco, você se esqueceu de instalar as fontes do Ghost Script (estão
localizadas no pacote <systemitem role="package">gsfonts</systemitem> na
distribuição Debian).


<listitem>

Para imprimir o arquivo <filename>alphabet.ps</filename> use o comando:

<screen>
gs -q -dSAFER -dNOPAUSE -sDEVICE=epson -r240x72 -sPAPERSIZE=legal -sOutputFile=/dev/lp0 
alphabet.ps


O arquivo <filename>alphabet.ps</filename> deve ser impresso.  Caso aparecerem
mensagens como <literal>Error: /invalidfont in findfont no lugar das
letras, você se esqueceu de instalar ou configurar as fontes do Ghost Script.
Instale o pacote de fontes (<systemitem role="package">gsfonts</systemitem> na
<command>Debian) ou verifique a documentação sobre como configurar as
fontes.


Cada uma das opções acima descrevem o seguinte:

<itemizedlist>
<listitem>

<literal>-q, -dQUIET - Não mostra mensagens de inicialização do Ghost
Script.


<listitem>

<literal>-dSAFER - É uma opção para ambientes seguros, pois desativa
a operação de mudança de nome e deleção de arquivo e permite somente a abertura
dos arquivos no modo somente leitura.


<listitem>

<literal>-dNOPAUSE - Desativa a pausa no final de cada página
processada.


<listitem>

<literal>-sDEVICE=dispositivo - Dispositivo que receberá a saída do
Ghost Script.  Neste local pode ser especificada a marca o modelo de sua
impressora ou um formato de arquivo diferente (como pcxmono, bmp256) para que o
arquivo <filename>.ps</filename> seja convertido para o formato designado.


Para detalhes sobre os dispositivos disponíveis em seu Ghost Script, digite
<literal>gs --help|less ou veja a página de manual.  Normalmente os
nomes de impressoras e modelos são concatenados, por exemplo, bjc600 para a
impressora **Canon BJC 600**, epson para impressoras padrão
epson, stcolor para **Epson Stylus color**, etc.


O Hardware-HOWTO contém referências sobre hardware suportados pelo
<command>GNU/Linux, tal como impressoras e sua leitura pode ser útil.


<listitem>

<literal>-r&lt;ResH&gt;x&lt;ResV&gt; - Define a resolução de
impressão (em dpi) Horizontal e Vertical.  Os valores dependem de sua
impressora.


<listitem>

<literal>-sPAPERSIZE=tamanho - Tamanho do papel.  Podem ser usados
a4, legal, letter, etc.  Veja a página de manual do gs para ver os outros tipos
suportados e suas medidas.


<listitem>

<literal>-sOutputFile=dispositivo - Dispositivo que receberá a saída
de processamento do gs.  Você pode especificar

<itemizedlist>
<listitem>

<literal>arquivo.epson - Nome do arquivo que receberá todo o
resultado do processamento.  O <filename>arquivo.epson</filename> terá toda a
impressão codificada no formato entendido por impressoras epson e poderá ser
impresso com o comando <literal>cat arquivo.epson &gt;/dev/lp0.


Uma curiosidade útil: É possível imprimir este arquivo em outros sistemas
operacionais, tal como o <command>DOS digitando: <literal>copy /b
arquivo.eps prn (lembre-se que o <command>DOS tem um limite
de 8 letras no nome do arquivo e 3 na extensão.  Você deve estar compreendendo
a flexibilidade que o <command>GNU/Linux e suas ferramentas permitem,
isso é só o começo.


<listitem>

<literal>impressao%d.epson - Nome do arquivo que receberá o resultado
do processamento.  Cada página será gravada em arquivos separados como
<filename>impressao1.epson</filename>, <filename>impressao2.epson</filename>.


Os arquivos podem ser impressos usando os mesmos métodos acima.


<listitem>

<literal>/dev/lp0 para uma impressora em
<filename>/dev/lp0</filename>


<listitem>

<literal>- para redirecionar a saída de processamento do
<command>gs para a saída padrão.  É útil para usar o gs com pipes
<literal>|.


<listitem>

<literal>\|lpr - Envia a saída do Ghost Script para o daemon de
impressão.  O objetivo é deixar a impressão mais rápida.




Se você é curioso ou não esta satisfeito com as opções mostradas acima, veja a
página de manual do <command>gs.










 impr-magicfilter">###Magic Filter

O **Magic Filter** é um filtro de impressão inteligente.  Ele
funciona acionado pelo spool de impressão (mais especificamente o arquivo
<filename>/etc/printcap</filename>) e permite identificar e imprimir arquivos
de diversos tipos diretamente através do comando <literal>lpr
arquivo.


É um ótimo programa e **ALTAMENTE RECOMENDADO**
se você deseja apenas clicar no botão imprimir e deixar os programas fazerem o
resto :-) A intenção do programa é justamente automatizar os trabalhos de
impressão e spool.


A maioria dos programas para ambiente gráfico X11, incluindo o Netscape, Word
Perfect, Gimp e Star Office trabalham nativamente com o
<command>magicfilter.

 impr-magicfilter-i">###Instalação e configuração do Magic Filter

O Magic Filter é encontrado no pacote <systemitem role="package">magicfilter</systemitem> da distribuição
<command>Debian e baseadas.


Sua configuração pode ser feita com o programa
<command>magicfilterconfig que torna o processo de configuração
rápido e fácil para quem não conhece a sintaxe do arquivo
<filename>/etc/printcap</filename> ou não tem muitas exigências sobre a
configuração detalhada da impressora.


Após instalar o <command>magicfilter reinicie o daemon de impressão
(se estiver usando a <command>Debian, entre no diretório
<filename>/etc/init.d</filename> e como usuário <literal>root digite
<literal>./lpr restart ou <literal>./lprng restart).


Para testar o funcionamento do <command>magicfilter, digite
<literal>lpr alphabet.ps e <literal>lpr tiger.ps, os
arquivos serão enviados para o <command>magicfilter que identificará
o arquivo como **Pos Script**, executará o Ghost Script e
retornará o resultado do processamento para o daemon de impressão.  O resultado
será visto na impressora.


Se tiver problemas, verifique se a configuração feita com o
<command>magicfilterconfig está correta.  Caso precise re-configurar
o <command>magicfilter, digite <literal>magicfilterconfig
--force (lembre-se que a opção --force substitui qualquer
configuração personalizada que tenha adicionado ao arquivo
<filename>/etc/printcap</filename>).




 impr-magicfilter-c">###Outros detalhes técnicos sobre o Magic Filter

Durante a configuração do <command>magicfilter, a seguinte linha é
adicionada ao arquivo <filename>/etc/printcap</filename>:

<screen>
:if=/etc/magicfilter/epson9-filter


Não tenho nenhum contrato de divulgação com a **epson** :-)
estou usando esta marca de impressora porque é a mais tradicional e facilmente
encontrada.  A linha que começa com <literal>:if no
<command>magicfilter identifica um arquivo de filtro de impressão.


O arquivo <filename>/etc/magicfilter/epson9-filter</filename> é criado usando o
formato do magicfilter, e não é difícil entender seu conteúdo e fazer algumas
modificações:

<screen>
#! /usr/sbin/magicfilter
#
# Magic filter setup file for 9-pin Epson (or compatible) printers
#
# This file is in the public domain.
#
# This file has been automatically adapted to your system.
#
# wild guess: native control codes start with ESC
0       \033            cat

# PostScript
0 %! filter /usr/bin/gs -q -dSAFER -dNOPAUSE -r120x72 -sDEVICE=epson -sOutputFile=- - -c quit 
0 \004%! filter	/usr/bin/gs -q -dSAFER -dNOPAUSE -r120x72 -sDEVICE=epson -sOutputFile=- - -c quit 

# PDF
0 %PDF fpipe /usr/bin/gs -q -dSAFER -dNOPAUSE -r120x72 -sDEVICE=epson -sOutputFile=- $FILE -c quit 

# TeX DVI
0 \367\002 fpipe /usr/bin/dvips -X 120  -Y 72  -R -q -f 

# compress'd data
0 \037\235 pipe	/bin/gzip  -cdq 

# packed, gzipped, frozen and SCO LZH data
0 \037\036 pipe	/bin/gzip  -cdq 
0 \037\213 pipe	/bin/gzip  -cdq 
0 \037\236 pipe	/bin/gzip  -cdq 
0 \037\240 pipe	/bin/gzip  -cdq 

0 BZh	pipe	/usr/bin/bzip2  -cdq 

# troff documents
0 .\?\?\040	fpipe 	`/usr/bin/grog  -Tps $FILE` 
0 .\\\"		fpipe 	`/usr/bin/grog  -Tps $FILE` 
0 '\\\"		fpipe 	`/usr/bin/grog  -Tps $FILE` 
0 '.\\\"		fpipe 	`/usr/bin/grog  -Tps $FILE` 
0  \\\"		fpipe 	`/usr/bin/grog  -Tps $FILE`


Você deve ter notado que para cada tipo de arquivo existe o respectivo programa
que é executado, basta você modificar as opções usadas nos programas neste
arquivo (como faria na linha de comando) para afetar o comportamento da
impressão.


Por exemplo, modificando a resolução para -r240x72 no processamento de arquivos
Pos Script (gs), a impressora passará a usar esta resolução.






 userlevel='avanc' impr-remota">###Impressão remota

Aqui será explicado como fazer seu sistema <command>Linux atuar como
um servidor de impressão para outras máquinas de sua rede.


 userlevel='avanc' impr-remota-perm">###Dando permissão para impresão remota via lpd/lprng

As máquinas autorizadas a usar a impressora local deverão ter seus nomes
incluídos no arquivo <filename>/etc/hosts.lpd</filename> (para o daemon
<command>lpd padrão) ou <filename>/etc/lprng/lpd.perms</filename>
(para o daemon <command>lpd do pacote <systemitem role="package">lprng</systemitem>).


O arquivo <filename>/etc/lprng/lpd.perms</filename> do <command>lprng
é mais configurável (e complexo), uma linha como:

<screen>
ACCEPT HOST=estacao1.dominio.org SERVICE=X,R,P,Q,M,C


aceitará os serviços (SERVICE) de conexão (X), lpr (R), impressão de trabalhos
(P), lpq (Q), lprm (M) e lpc (C) da máquina
<filename>estacao1.dominio.org</filename>.  Veja os comentários neste arquivo
para entender o funcionamento de suas opções ou a página de manual do
<filename>lpd.perms</filename>.




 userlevel='avanc' impr-remota-rlpr">###Impressão via rlpr

O <command>rlpr redireciona a impressão diretamente ao servidor de
impressão.  Sua vantagem é que a impressão é feita diretamente sem a
necessidade de configurar um arquivo <filename>/etc/printcap</filename> e
dispensar trabalhos adicionais de administração.  Ele envia o trabalho de
impressão diretamente ao daemon <command>lpd na na porta 515 (a
máquina deve estar configurada para aceitar conexões, veja <xref linkend="impr-remota-perm"/>).


Para enviar o arquivo <filename>listagem.txt</filename> para a impressora
**hp** no servidor <filename>impr.meudominio.org</filename>:

<screen>
rlpr -Himpr.meudominio.org -Php listagem.txt


A opção **-H** especifica o nome do servidor de impressão e
**-P** o nome da impressora.  Caso não tenha permissões para
imprimir na impressora remota, uma mensagem será mostrada.




 userlevel='avanc' impr-remota-printacap">###Impressão via printcap

Através deste método, a impressão será tratada através do spool remoto
(<command>lpd ou <command>lprng) e enviada ao servidor de
impressão.  Para que isto funcione, utilize a seguinte configuração no seu
arquivo <filename>/etc/printcap</filename>:

<screen>
  lp:Impressora remota:\
 :sd=/var/spool/lpd/lp:\
 :rm=impr.meudominio.org:\
 :rp=hp:\
 :sh:


Então quando for executado o comando <command>lpr na máquina remota,
o <command>lprng enviará a impressão para a impressora hp
(**rp=hp**) na máquina
<filename>impr.meudominio.org</filename>
(<filename>rm=impr.meudominio.org</filename>).


Caso você tenha a opção de imprimir tanto para uma impressora local quando para
uma remota, você poderá usar uma configuração como a seguinte:

<screen>
lp|hp|Impressora Local:\
 :lp=/dev/lp0:\
 :sd=/var/spool/lpd/hp:\
 :sh:\
 :pw#80:\
 :pl#66: \
 :px#1440:\
 :mx#0:\
 :if=/etc/magicfilter/dj930c-filter:\
 :af=/var/log/lp-acct:\
 :lf=/var/log/lp-errs:
	
hp-r|Impressora Remota:\
 :sd=/var/spool/lpd/lp:\
 :rm=impr.meudominio.org:\
 :rp=hp:\
 :sh:


Para selecionar qual impressora será usada, adicione a opção
**-Pimpressora** na linha de comando dos utilitários
<command>lpr, <command>lpq, <command>lprm (por
exemplo, <literal>lpr -Php-r relatorio.txt.  Quando a opção
**-P** é especificada, a impressora **lp**
será usada por padrão.

<!-- [ %OBS [ -->

**OBS** Lembre-se de reiniciar seu daemon de
impressão toda vez que modificar o arquivo <filename>/etc/printcap</filename>.

<!-- ]]> -->




