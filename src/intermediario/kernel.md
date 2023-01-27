<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" kern">###Kernel e Módulos

Este capítulo descreve em detalhes o que é o kernel, módulos, sua configuração
e programas relacionados.


 kern-kernel">###O Kernel

É a peça central do sistema operacional (o <command>Linux), é ele que
controla os dispositivos e demais periféricos do sistema (como memória, placas
de som, vídeo, discos rígidos, disquetes, sistemas de arquivos, redes e outros
recursos disponíveis).  Muitos confundem isto e chamam a distribuição de
sistema operacional.  Isto é errado!


O **kernel** faz o controle dos periféricos do sistema e para
isto ele deve ter o seu suporte incluído.  Para fazer uma placa de som
**Sound Blaster** funcionar, por exemplo, é necessário que o
kernel ofereça suporte a este placa e você deve configurar seus parâmetros
(como interrupção, I/O e DMA) com comandos específicos para ativar a placa e
faze-la funcionar corretamente.  Existe um documento que contém quais são os
periféricos suportados/ não suportados pelo <command>GNU/Linux, ele
se chama <literal>Hardware-HOWTO.


Suas versões são identificadas por números como 2.2.30, 2.4.33, 2.6.23.6, as
versões que contém um número par entre o primeiro e segundo ponto são versões
estáveis e que contém números ímpares neste mesmo local são versões instáveis
(em desenvolvimento).  Usar versões instáveis não quer dizer que ocorrerá
travamentos ou coisas do tipo, mas algumas partes do kernel podem não estar
testadas o suficiente ou alguns controladores podem ainda estar incompletos
para obter pleno funcionamento.  Se opera sua máquina em um ambiente crítico,
prefira pegar versões estáveis do kernel.


Após inicializar o sistema, o kernel e seus arquivos podem ser acessados ou
modificados através do ponto de montagem <filename>/proc</filename>.  Para
detalhes veja <xref linkend="disc-proc"/>.


Caso você tenha um dispositivo (como uma placa de som) que tem suporte no
<command>GNU/Linux mas não funciona veja <xref linkend="kern-suporte"/>.



 kern-modulos">###Módulos

São partes do kernel que são carregadas somente quando são solicitadas por
algum aplicativo ou dispositivo e descarregadas da memória quando não são mais
usadas.  Este recurso é útil por 2 motivos: Evita a construção de um kernel
grande (estático) que ocupe grande parte da memória com todos os drivers
compilados e permite que partes do kernel ocupem a memória somente quando forem
necessários.


Os módulos do kernel estão localizados no diretório
<filename>/lib/modules/versão_do_kernel/*</filename> (onde
<literal>versão_do_kernel é a versão atual do kernel em seu sistema,
caso seja <literal>2.6.23.6 o diretório que contém seus módulos será
<filename>/lib/modules/2.6.23.6</filename>.


Os módulos são carregados automaticamente quando solicitados através do
programa <command>kmod ou manualmente através do arquivo
<filename>/etc/modules</filename> , <command>insmod ou
<command>modprobe.  Atenção: Não compile o suporte ao seu sistema de
arquivos raíz como módulo, isto o tornará inacessível, a não ser que esteja
usando initrd.



 kern-suporte">###Como adicionar suporte a Hardwares e outros dispositivos no kernel

Quando seu hardware não funciona mas você tem certeza que é suportado pelo
<command>GNU/Linux, é preciso seguir alguns passos para faze-lo
funcionar corretamente:

<itemizedlist>
<listitem>

Verifique se o kernel atual foi compilado com suporte ao seu dispositivo.
Também é possível que o suporte ao dispositivo esteja compilado como módulo.
Dê o comando <literal>dmesg para ver as mensagens do kernel durante a
inicialização e verifique se aparece alguma coisa referente ao dispositivo que
deseja instalar (alguma mensagem de erro, etc).  Caso não aparecer nada é
possível que o driver esteja compilado como módulo, para verificar isto entre
no diretório <filename>/lib/modules/versao_do_kernel</filename> e veja se
encontra o módulo correspondente ao seu dispositivo (o módulo da placa
**NE 2000** tem o nome de <filename>ne.ko</filename> e o da
placa **Sound Blaster** de <filename>sb.ko</filename>, por
exemplo).


**OBS:** Nos kernel 2.4 e anteriores, a extensão dos módulos
era <filename>.o</filename>.


Caso o kernel não tiver o suporte ao seu dispositivo, você precisará recompilar
seu kernel ativando seu suporte.  Veja <xref linkend="kern-recompilando"/>.


<listitem>

Caso seu hardware esteja compilado no kernel, verifique se o módulo
correspondente está carregado (com o comando <command>lsmod).  Caso
não estiver, carregue-o com o <command>modprobe (por exemplo,
<literal>modprobe sb io=0x220 irq=5 dma=1 dma16=5 mpuio=0x330), para
detalhes veja <xref linkend="kern-modprobe"/>.


O uso deste comando deverá ativar seu hardware imediatamente, neste caso
configure o módulo para ser carregado automaticamente através do programa
<command>modconf ou edite os arquivos relacionados com os módulos
(veja <xref linkend="kern-arquivos"/>).  Caso não tenha sucesso, será retornada
uma mensagem de erro.





 kern-kmod">###kmod

Este é o programa usado para carregar os módulos automaticamente quando são
requeridos pelo sistema.  Ele é um daemon que funciona constantemente fazendo a
monitoração, quando verifica que algum dispositivo ou programa está solicitando
o suporte a algum dispositivo, ele carrega o módulo correspondente.


Ele pode ser desativado através da recompilação do kernel, dando um
<command>kill no processo ou através do arquivo
<filename>/etc/modules</filename> (veja <xref linkend="kern-arquivos-modules"/>.  Caso seja desativado, é preciso carregar
manualmente os módulos através do <command>modprobe ou
<command>insmod.



 kern-lsmod">###lsmod

Lista quais módulos estão carregados atualmente pelo kernel.  O nome
<literal>lsmod é uma contração de
<literal>ls+<literal>módulos - Listar Módulos.  A listagem
feita pelo <command>lsmod é uma alternativa ao uso do comando
<literal>cat /proc/modules.


A saída deste comando tem a seguinte forma:

<screen>
Module            Size  Pages    Used by
nls_iso8859_1     8000      1          1 (autoclean)
nls_cp437         3744      1          1 (autoclean)
ne                6156      2          1
8390              8390      2     [ne] 0


A coluna **Module** indica o nome do módulo que está
carregado, a coluna **Used** mostra qual módulos está usando
aquele recurso.  O parâmetro **(autoclean)** no final da
coluna indica que o módulo foi carregado manualmente (pelo
<command>insmod ou <command>modprobe) ou através do
<command>kmod e será automaticamente removido da memória quando não
for mais usado.


No exemplo acima os módulos **ne** e **8390**
não tem o parâmetro **(autoclean)** porque foram carregados
pelo arquivo <filename>/etc/modules</filename> (veja <xref linkend="kern-arquivos-modules"/>).  Isto significa que não serão removidos da
memória caso estiverem sem uso.


Qualquer módulo carregado pode ser removido manualmente através do comandos
<command>rmmod.



 kern-insmod">###insmod

Carrega um módulo manualmente.  Para carregar módulos que dependem de outros
módulos para que funcionem, você duas opções: Carregar os módulos manualmente
ou usar o <command>modprobe que verifica e carrega as dependências
correspondentes.


A sintaxe do comando é: <command>insmod [**módulo**]
[**opções_módulo**]


Onde:

<variablelist>
<varlistentry>
<term>módulo
<listitem>

É o nome do módulo que será carregado.



<varlistentry>
<term>opções_módulo
<listitem>

Opções que serão usadas pelo módulo.  Variam de módulo para módulo, alguns
precisam de opções outros não, tente primeiro carregar sem opções, caso seja
mostrada uma mensagem de erro verifique as opções usadas por ele.  Para
detalhes sobre que opções são suportadas por cada módulo, veja a sua
documentação no código fonte do kernel em
<filename>/usr/src/linux/Documentation</filename>



</variablelist>

Exemplo: <literal>insmod ne io=0x300 irq=10



 kern-rmmod">###rmmod

Remove módulos carregados no kernel.  Para ver os nomes dos módulos atualmente
carregados no kernel digite <literal>lsmod e verifique na primeira
coluna o nome do módulo.  Caso um módulo tenha dependências e você tentar
remover suas dependências, uma mensagem de erro será mostrada alertando que o
módulo está em uso.


Exemplo: <literal>rmmod ne



 kern-modprobe">###modprobe

Carrega um módulo e suas dependências manualmente.  Este comando permite
carregar diversos módulos e dependências de uma só vez.  O comportamento do
<command>modprobe é modificado pelo arquivo
<filename>/etc/modules.conf</filename> .


A sintaxe deste comando é: <command>modprobe [**módulo**]
[**opções_módulo**]


Onde:

<variablelist>
<varlistentry>
<term>módulo
<listitem>

É o nome do módulo que será carregado.



<varlistentry>
<term>opções_módulo
<listitem>

Opções que serão usadas pelo módulo.  Variam de módulo para módulo, alguns
precisam de opções outros não, tente primeiro carregar sem opções, caso seja
mostrada uma mensagem de erro verifique as opções usadas por ele.  Para
detalhes sobre que opções são suportadas por cada módulo, veja a sua
documentação no código fonte do kernel em
<filename>/usr/src/linux/Documentation</filename>



</variablelist>

Nem todos os módulos são carregados corretamente pelo
<command>modprobe, o <filename>plip</filename>, por exemplo, mostra
uma mensagem sobre porta I/O inválida mas não caso seja carregado pelo
<command>insmod.


Exemplo: <literal>modprobe ne io=0x300 irq=10, <literal>modprobe sb
io=0x220 irq=5 dma=1 dma16=5 mpuio=0x330



 kern-depmod">###depmod

Verifica a dependência de módulos.  As dependências dos módulos são verificadas
pelos scripts em <filename>/etc/init.d</filename> usando o comando
<literal>depmod -a e o resultado gravado no arquivo
<filename>/lib/modules/versao_do_kernel/modules.dep</filename>.  Esta checagem
serve para que todas as dependências de módulos estejam corretamente
disponíveis na inicialização do sistema.  O comportamento do
<command>depmod pode ser modificado através do arquivo
<filename>/etc/modules.conf</filename> .  É possível criar a dependência de
módulos imediatamente após a compilação do kernel digitando <command>depmod -a
[**versão_do_kernel**].


Exemplo: <literal>depmod -a



 kern-modconf">###modconf

Este programa permite um meio mais fácil de configurar a ativação de módulos e
opções através de uma interface através de menus.  Selecione a categoria de
módulos através das setas acima e abaixo e pressione enter para selecionar os
módulos existentes.  Serão pedidas as opções do módulo (como DMA, IRQ, I/O)
para que sua inicialização seja possível, estes parâmetros são específicos de
cada módulo e devem ser vistos na documentação do código fonte do kernel no
diretório <filename>/usr/src/linux/Documentation</filename>.  Note que também
existem módulos com auto-detecção mas isto deixa o sistema um pouco mais lento,
porque ele fará uma varredura na faixa de endereços especificados pelo módulo
para achar o dispositivo.  As opções são desnecessárias em alguns tipos de
módulos.


As modificações feitas por este programa são gravadas no diretório
<filename>/etc/modutils</filename> em arquivos separados como
<filename>/etc/modutils/alias</filename> - alias de módulos,
<filename>/etc/modutils/modconf</filename> - opções usadas por módulos,
<filename>/etc/modutils/paths</filename> - Caminho onde os módulos do sistema
são encontrados.  Dentro de <filename>/etc/modutils</filename> é ainda
encontrado um sub-diretório chamado <filename>arch</filename> que contém opções
específicas por arquiteturas.


A sincronização dos arquivos gerados pelo <command>modconf com o
<filename>/etc/modules.conf</filename> é feita através do utilitário
<command>update-modules.  Ele é normalmente executado após
modificações nos módulos feitas pelo <command>modconf.



 kern-recompilando">###Recompilando o Kernel

Será que vou precisar recompilar o meu kernel?  você deve estar se perguntando
agora.  Abaixo alguns motivos para esclarecer suas dúvidas:

<itemizedlist>
<listitem>

Melhora o desempenho do kernel.  O kernel padrão que acompanha as distribuições
<command>GNU/Linux foi feito para funcionar em qualquer tipo de
sistema e garantir seu funcionamento e inclui suporte a praticamente tudo.
Isto pode gerar desde instabilidade até uma grade pausa do kernel na
inicialização quando estiver procurando pelos dispositivos que simplesmente não
existem em seu computador!


A compilação permite escolher somente o suporte aos dispositivos existentes em
seu computador e assim diminuir o tamanho do kernel, desocupar a memória RAM
com dispositivos que nunca usará e assim você terá um desempenho bem melhor do
que teria com um kernel pesado.


<listitem>

Incluir suporte a alguns hardwares que estão desativados no kernel padrão (SMP,
APM, ACPI, Virtualização, Firewall, Bridge, memory cards, drivers
experimentais, etc).


<listitem>

Se aventurar em compilar um kernel (sistema operacional) personalizado em seu
sistema.


<listitem>

Tornar seu sistema mais seguro


<listitem>

Impressionar os seus amigos, tentando coisas novas.




Serão necessários uns 300Mb de espaço em disco disponível para copiar e
descompactar o código fonte do kernel e alguns pacotes de desenvolvimento como
o <command>gcc, <command>cpp, <command>binutils,
<command>gcc-i386-gnu, <command>bin86,
<command>make, <command>dpkg-dev, <command>perl,
<command>kernel-package (os três últimos somente para a distribuição
<command>Debian).


Na distribuição <command>Debian, o melhor método é através do
<command>kernel-package que faz tudo para você (menos escolher o que
terá o não o suporte no kernel) e gera um pacote <command>.deb que
poderá ser usado para instalar o kernel em seu sistema ou em qualquer outro que
execute a <command>Debian ou distribuições baseadas
(<command>Ubuntu, etc).  Devido a sua facilidade, a compilação do
kernel através do <filename>kernel-package</filename> é muito recomendado para
usuários iniciantes e para aqueles que usam somente um kernel no sistema (é
possível usar mais de dois ao mesmo tempo, veja o processo de compilação manual
adiante neste capítulo).  Siga este passos para recompilar seu kernel através
do <filename>kernel-package</filename>:

<orderedlist numeration="arabic">
<listitem>

Descompacte o código fonte do kernel (através do arquivo
linux-2.6.XX.XX.tar.bz2) para o diretório <filename>/usr/src</filename>.  Caso
use os pacotes da <command>Debian eles terão o nome de
<filename>kernel-source-2.6.XX.XX</filename>, para detalhes de como instalar um
pacote, veja <xref linkend="dpkg-instalar"/>.


<listitem>

Após isto, entre no diretório onde o código fonte do kernel foi instalado com
<literal>cd /usr/src/linux (este será assumido o lugar onde o código
fonte do kernel se encontra).


<listitem>

Como usuário <literal>root, digite <literal>make config.
Você também pode usar <literal>make menuconfig (configuração através
de menus) ou <literal>make xconfig (configuração em modo gráfico) mas
precisará de pacotes adicionais para que estes dois funcionem corretamente.


Serão feitas perguntas sobre se deseja suporte a tal dispositivo, etc.
Pressione <literal>Y para incluir o suporte diretamente no kernel,
<literal>M para incluir o suporte como módulo ou <literal>N
para não incluir o suporte.  Note que nem todos os drivers podem ser compilados
como módulos.


Escolha as opções que se encaixam em seu sistema.  se estiver em dúvida sobre a
pergunta digite <literal>? e tecle Enter para ter uma explicação
sobre o que aquela opção faz.  Se não souber do que se trata, recomendo incluir
a opção (pressionando <literal>Y ou <literal>M.  Este passo
pode levar entre 5 minutos e 1 Hora (usuários que estão fazendo isto pela
primeira vez tendem a levar mais tempo lendo e conhecendo os recursos que o
<command>GNU/Linux possui, antes de tomar qualquer decisão).  Não se
preocupe se esquecer de incluir o suporte a alguma coisa, você pode repetir o
passo <literal>make config (todas as suas escolhas são gravadas no
arquivo <filename>.config</filename>), recompilar o kernel e instalar em cima
do antigo a qualquer hora que quiser.


<listitem>

Após o <literal>make config chegar ao final, digite
<literal>make-kpkg clean para limpar construções anteriores do
kernel.


<listitem>

Agora compile o kernel digitando <literal>make-kpkg --revision=teste.1.0
kernel-image.  A palavra <literal>teste pode ser
substituída por qualquer outra que você quiser e número da versão
<literal>1.0 serve apenas como controle de suas compilações (pode ser
qualquer número).


Observação: Não inclua hífens (<literal>-) no parâmetro --revision,
use somente pontos.


<listitem>

Agora após compilar, o kernel será gravado no diretório superior (..) com um
nome do tipo <literal>linux-image-2.6.23.6-i386_teste.1.0.deb.  Basta
você digitar <literal>dpkg -i
kernel-image-2.6.23.6-i386_teste.1.0.deb e o <command>dpkg
fará o resto da instalação do kernel para você e perguntará se deseja criar um
disquete de inicialização (recomendável).


<listitem>

Reinicie seu computador, seu novo kernel iniciará e você já perceberá a
primeira diferença pela velocidade que o <command>GNU/Linux é
iniciado (você inclui somente suporte a dispositivos em seu sistema).  O
desempenho dos programas também melhorará pois cortou o suporte a
dispositivos/funções que seu computador não precisa.


Caso alguma coisa sair errada, coloque o disquete que gravou no passo anterior
e reinicie o computador para fazer as correções.


</orderedlist>

Para recompilar o kernel usando o método manual, siga os seguintes passos:

<orderedlist numeration="arabic">
<listitem>

Descompacte o código fonte do kernel (através do arquivo
linux-2.6.XX.XX.tar.bz2) para o diretório <filename>/usr/src</filename>.  O
código fonte do kernel pode ser encontrado em ("http://www.w3.org/1999/xlink) [](ftp://ftp.kernel.org)ftp://ftp.kernel.org/.


<listitem>

Após isto, entre no diretório onde o código fonte do kernel foi instalado com
<literal>cd /usr/src/linux (este será assumido o lugar onde o código
fonte do kernel se encontra).


<listitem>

Como usuário <literal>root, digite <literal>make config.
Você também pode usar <literal>make menuconfig (configuração através
de menus) ou <literal>make xconfig (configuração em modo gráfico) mas
precisará de pacotes adicionais.


Serão feitas perguntas sobre se deseja suporte a tal dispositivo, etc.
Pressione <literal>Y para incluir o suporte diretamente no kernel,
<literal>M para incluir o suporte como módulo ou <literal>N
para não incluir o suporte.  Note que nem todos os drivers podem ser compilados
como módulos.


Escolha as opções que se encaixam em seu sistema.  se estiver em dúvida sobre a
pergunta digite <literal>? e tecle Enter para ter uma explicação
sobre o que aquela opção faz.  Se não souber do que se trata, recomendo incluir
a opção (pressionando <literal>Y ou <literal>M.  Este passo
pode levar entre 5 minutos e 1 Hora (usuários que estão fazendo isto pela
primeira vez tendem a levar mais tempo lendo e conhecendo os recursos que o
<command>GNU/Linux possui antes de tomar qualquer decisão).  Não se
preocupe se esquecer de incluir o suporte a alguma coisa, você pode repetir o
passo <literal>make config, recompilar o kernel e instalar em cima do
antigo a qualquer hora que quiser.


<listitem>

Caso esteja compilando um kernel 2.4 ou inferior, Digite o comando
<literal>make dep para verificar as dependências dos módulos.  Se
estiver compilando um kernel 2.6 ou superior, pule esse comando.


<listitem>

Digite o comando <literal>make clean para limpar construções
anteriores do kernel.


<listitem>

Digite o comando <literal>make para iniciar a compilação do kernel e
seus módulos.  Aguarde a compilação, o tempo pode variar dependendo da
quantidade de recursos que adicionou ao kernel, a velocidade de seu computador
e a quantidade de memória RAM disponível.


Caso tenha acrescentado muitos ítens no Kernel, é possível que o comando
<literal>make zImage falhe no final (especialmente se o tamanho do
kernel estático for maior que 505Kb).  Neste caso use <literal>make
bzImage.  A diferença entre **zImage** e
**bzImage** é que o primeiro possui um limite de tamanho
porque é descompactado na memória básica (recomendado para alguns Notebooks),
já a **bzImage**, é descompactada na memória estendida e não
possui as limitações da **zImage**.


<listitem>

A compilação neste ponto está completa, você agora tem duas opções para
instalar o kernel: Substituir o kernel anterior pelo recém compilado ou usar os
dois.  A segunda questão é recomendável se você não tem certeza se o kernel
funcionará corretamente e deseja iniciar pelo antigo no caso de alguma coisa
dar errado.


Se você optar por substituir o kernel anterior:

<orderedlist numeration="arabic">
<listitem>

É recomendável renomear o diretório
<filename>/lib/modules/versão_do_kernel</filename> para
<filename>/lib/modules/versão_do_kernel.old</filename>, isto será útil para
restauração completa dos módulos antigos caso alguma coisa der errado.


<listitem>

Execute o comando <literal>make modules_install para instalar os
módulos do kernel recém compilado em
<filename>/lib/modules/versão_do_kernel</filename>.


<listitem>

Copie o arquivo <filename>zImage</filename> que contém o kernel de
<filename>/usr/src/linux/arch/i386/boot/zImage</filename> para
<filename>/boot/vmlinuz-2.XX.XX</filename> (**2.XX.XX** é a
versão do kernel anterior)


<listitem>

Verifique se o link simbólico <filename>/vmlinuz</filename> aponta para a
versão do kernel que compilou atualmente (com <literal>ls -la /).
Caso contrário, apague o arquivo <filename>/vmlinuz</filename> do diretório
raíz e crie um novo link com <literal>ln -s /boot/vmlinuz-2.XX.Xx
/vmlinuz apontando para o kernel correto.


<listitem>

Execute o comando <literal>lilo para gerar um novo setor de partida
no disco rígido.  Para detalhes veja <xref linkend="boot-lilo"/>.


<listitem>

Reinicie o sistema (<literal>shutdown -r now).


<listitem>

Caso tudo esteja funcionando normalmente, apague o diretório antigo de módulos
que salvou e o kernel antigo de <filename>/boot</filename>.  Caso algo tenha
dado errado e seu sistema não inicializa, inicie a partir de um disquete,
apague o novo kernel, apague os novos módulos, renomeie o diretório de módulos
antigos para o nome original, ajuste o link simbólico
<filename>/vmlinuz</filename> para apontar para o antigo kernel e execute o
<literal>lilo.  Após reiniciar seu computador voltará como estava
antes.


</orderedlist>

Se você optar por manter o kernel anterior e selecionar qual será usado na
partida do sistema (útil para um kernel em testes):

<orderedlist numeration="arabic">
<listitem>

Execute o comando <literal>make modules_install para instalar os
módulos recém compilados do kernel em
<filename>/lib/modules/versao_do_kernel</filename>.


<listitem>

Copie o arquivo <filename>zImage</filename> que contém o kernel de
<filename>/usr/src/linux/arch/i386/boot/zImage</filename> para
<filename>/boot/vmlinuz-2.XX.XX</filename> (**2.XX.XX** é a
versão do kernel anterior)


<listitem>

Crie um link simbólico no diretório raíz (<filename>/</filename>) apontando
para o novo kernel.  Como exemplos será usado
<filename>/vmlinuz-novo</filename>.


<listitem>

Modifique o arquivo <filename>/etc/lilo.conf</filename> para incluir a nova
imagem de kernel.  Por exemplo:

<screen>
Antes da modificação:

boot=/dev/hda
prompt
timeout=200
delay=200
map=/boot/map
install=menu

image = /vmlinuz
  root = /dev/hda1
  label = 1
  read-only

Depois da modificação:

boot=/dev/hda
prompt
timeout=200
delay=200
map=/boot/map
install=menu

image = /vmlinuz
  root = /dev/hda1
  label = 1
  read-only

image = /vmlinuz-new
  root = /dev/hda1
  label = 2
  read-only


Se você digitar <literal>1 no aviso de <literal>boot: do
<command>Lilo, o kernel antigo será carregado, caso digitar
<literal>2 o novo kernel será carregado.  Para detalhes veja <xref linkend="boot-lilo-cfg"e <xref linkend="boot-lilo-exemplo"/>.


<listitem>

Execute o comando <literal>lilo para gravar o novo setor de boot para
o disco rígido.


<listitem>

Reinicie o computador


<listitem>

Carregue o novo kernel escolhendo a opção <literal>2 no aviso de
<literal>boot: do <command>Lilo.  Caso tiver problemas,
escolha a opção <literal>1 para iniciar com o kernel antigo e
verifique os passos de configuração (o arquivo <filename>lilo.conf</filename>
foi modificado corretamente?.


</orderedlist>

</orderedlist>

Em alguns casos (como nos kernels empacotados em distribuições
<command>GNU/Linux) o código fonte do kernel é gravado em um
diretório chamado <filename>kernel-source-xx.xx.xx</filename>.  É recomendável
fazer um link com um diretório <filename>GNU/Linux</filename>, pois é o padrão
usado pelas atualização do código fonte através de patches (veja <xref linkend="kern-patches"/>).


Para criar o link simbólico, entre em <filename>/usr/src</filename> e digite:
<literal>ln -s kernel-source-xx.xx.xx linux.


Se quiser mais detalhes sobre a compilação do kernel, consulte o documento
**kernel-howto**.



 kern-arquivos">###Arquivos relacionados com o Kernel e Módulos

Esta seção descreve os arquivos usados pelo kernel e módulos, a função de cada
um no sistema, a sintaxe, etc.

 kern-arquivos-modules">###/etc/modules

A função deste arquivo é carregar módulos especificados na inicialização do
sistema e mantê-los carregado todo o tempo.  É útil para módulos de placas de
rede que precisam ser carregados antes da configuração de rede feita pela
distribuição e não podem ser removidos quando a placa de rede estiver sem uso
(isto retiraria seu computador da rede).


Seu conteúdo é uma lista de módulos (um por linha) que serão carregados na
inicialização do sistema.  Os módulos carregados pelo arquivo
<filename>/etc/modules</filename> pode ser listados usando o comando
<command>lsmod (veja <xref linkend="kern-lsmod"/>.


Se o parâmetro <literal>auto estiver especificado como um módulo, o
<command>kmod será ativado e carregará os módulos somente em demanda,
caso seja especificado <literal>noauto o programa
<command>kmod será desativado.  O <command>kmod é ativado
por padrão nos níveis de execução 2 ao 5.


Ele pode ser editado em qualquer editor de textos comum ou modificado
automaticamente através do utilitário <command>modconf.



 kern-arquivos-modulesconf">###modules.conf

O arquivo <filename>/etc/modules.conf</filename> permite controlar as opções de
todos os módulos do sistema.  Ele é consultado pelos programas
<command>modprobe e <command>depmod.  As opções
especificadas neste arquivo facilita o gerenciamento de módulos, evitando a
digitação de opções através da linha de comando.


Note que é recomendado o uso do utilitário <command>modconf para
configurar quaisquer módulos em seu sistema e o utilitário
<command>update-modules para sincronização dos arquivos gerados pelo
<command>modconf em <filename>/etc/modutils</filename> com o
<filename>/etc/modules.conf</filename> (geralmente isto é feito automaticamente
após o uso do <command>modconf).  Por este motivo não é recomendável
modifica-lo manualmente, a não ser que seja um usuário experiente e saiba o que
está fazendo.  Veja <xref linkend="kern-modconf"/>


Por exemplo: adicionando as linhas:

<screen>
alias sound sb 
options sb io=0x220 irq=5 dma=1 dma16=5 mpuio=0x330


permitirá que seja usado somente o comando <literal>modprobe sb para
ativar a placa de som.





 kern-patches">###Aplicando Patches no kernel

**Patches** são modificações geradas pelo programa
<command>diff em que servem para atualizar um programa ou texto.
Este recurso é muito útil para os desenvolvedores, pois podem gerar um arquivo
contendo as diferenças entre um programa antigo e um novo (usando o comando
<command>diff) e enviar o arquivo contendo as diferenças para outras
pessoas.


As pessoas interessadas em atualizar o programa antigo, podem simplesmente
pegar o arquivo contendo as diferenças e atualizar o programa usando o
<command>patch.


Isto é muito usado no desenvolvimento do kernel do <command>GNU/Linux
em que novas versões são lançadas freqüentemente e o tamanho kernel completo
compactado ocupa cerca de 18MB.  Você pode atualizar seu kernel pegando um
patch seguinte a versão que possui em ("http://www.w3.org/1999/xlink) [](ftp://ftp.kernel.org)ftp://ftp.kernel.org/.


Para aplicar um patch que atualizará seu kernel 2.6.23 para a versão 2.6.24
você deve proceder da seguinte forma:

<itemizedlist>
<listitem>

Descompacte o código fonte do kernel 2.6.23 em
<filename>/usr/src/linux</filename> ou certifique-se que existe um link
simbólico do código fonte do kernel para <filename>/usr/src/linux</filename>.


<listitem>

Copie o arquivo <filename>patch-2.6.24.gz</filename> de ("http://www.w3.org/1999/xlink) [](ftp://ftp.kernel.org)ftp://ftp.kernel.org/ para
<filename>/usr/src</filename>.


<listitem>

Use o comando <literal>gzip -dc patch-2.6.24|patch -p0 -N -E para
atualizar o código fonte em <filename>/usr/src/linux</filename> para a versão
2.6.24.


Alternativamente você pode primeiro descompactar o arquivo
<filename>patch-2.6.24.gz</filename> com o <command>gzip e usar o
comando <literal>patch -p0 -N -E &lt;patch-2.6.24 para atualizar o
código fonte do kernel.  O <command>GNU/Linux permite que você
obtenha o mesmo resultado através de diferentes métodos, a escolha é somente
sua.




Caso deseja atualizar o kernel 2.6.20 para 2.6.24, como no exemplo acima, você
deverá aplicar os patches em seqüência (do patch 2.6.20 ao 2.6.24).  Vale a
pena observar se o tamanho total dos patches ultrapassa ou chega perto o
tamanho do kernel completo, pois dependendo da quantidade de alterações pode
ser mais viável baixar diretamente a nova versão.



