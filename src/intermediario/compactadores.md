<!-- Converted by db4-upgrade version 1.0 -->
<!--- chapter  userlevel='inter' ---><!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cpctd">###Compactadores

Esta seção explica o que são e como usar programas compactadores no
<command>GNU/Linux, as características de cada um, como identificar
um arquivo compactado e como descompactar um arquivo compactado usando o
programa correspondente.


A utilização de arquivos compactados é método útil principalmente para reduzir
o consumo de espaço em disco ou permitir grandes quantidades de texto serem
transferidas para outro computador através de disquetes.


 cpctd-oque">###O que fazem os compactadores/descompactadores?

Compactadores são programas que diminuem o tamanho de um arquivo (ou arquivos)
através da substituição de caracteres repetidos.  Para entender melhor como
eles funcionam, veja o próximo exemplo:

<screen>
compactadores compactam e deixam arquivos compactados.

-- após a compactação da frase --

%dores %m e deixam arquivos %dos


O que aconteceu realmente foi que a palavra <literal>compacta se
encontrava 3 vezes na frase acima, e foi substituída por um sinal de
<literal>%.  Para descompactar o processo seria o contrário: Ele
substituiria % por <literal>compacta e nós temos a frase novamente
restaurada.


Você deve ter notado que o tamanho da frase <literal>compactada caiu
quase pela metade.  A quantidade de compactação de um arquivo é chamada de
**taxa de compactação**.  Assim se o tamanho do arquivo for
diminuído a metade após a compactação, dizemos que conseguiu uma **taxa
de compactação** de 2:1 (lê-se dois para um), se o arquivo diminuiu 4
vezes, dizemos que conseguiu uma compactação de 4:1 (quatro para um) e assim
por diante.


Para controle dos caracteres que são usados nas substituições, os programas de
compactação mantém cabeçalhos com todas as substituições usadas durante a
compactação.  O tamanho do cabeçalho pode ser fixo ou definido pelo usuário,
depende do programa usado na compactação.


Este é um exemplo bem simples para entender o que acontece durante a
compactação, os programas de compactação executam instruções muito avançadas e
códigos complexos para atingir um alta taxa de compactação.


Observações:

<itemizedlist>
<listitem>

Não é possível trabalhar diretamente com arquivos compactados!  É necessário
descompactar o arquivo para usa-lo.  Note que alguns programas atualmente
suportam a abertura de arquivos compactados, mas na realidade eles apenas
simplificam a tarefa descompactando o arquivo, abrindo e o recompactando assim
que o trabalho estiver concluído.


<listitem>

Arquivos de texto tem uma taxa de compactação muito melhor que arquivos
binários, porque possuem mais caracteres repetidos.  É normal atingir taxas de
compactação de 10 para 1 ou mais quando se compacta um arquivo texto.  Arquivos
binários, como programas, possuem uma taxa de compactação média de 2:1.


<listitem>

Note que também existem programas compactadores especialmente desenvolvidos
para compactação de músicas, arquivos binários, imagens, textos.




 cpctd-tipos">###Tipos de compactação

Existem basicamente dois tipos de compactação, a compactação **sem
perdas** e a compactação **com perdas**.


Os exemplos a seguir tentam explicar de forma simples os conceitos envolvidos.


A compactação sem perdas, como o próprio nome diz não causa nenhuma perda nas
informações contidas no arquivo.  Quando você compacta e descompacta um
arquivo, o conteúdo é o mesmo do original.


A compactação com perdas é um tipo específico de compactação desenvolvido para
atingir altas taxas, porém com perdas parciais dos dados.  É aplicada a tipos
de arquivos especiais, como músicas e imagens ou arquivos que envolvam a
percepção humana.


Sabe-se que o ouvido humano não é tão sensível a determinados sons e
freqüências, então a compactação de um arquivo de música poderia deixar de
gravar os sons que seriam pouco percebidos, resultando em um arquivo menor.
Uma compactação do tipo **ogg** ou **mp3**
utiliza-se destes recursos.  O arquivo resultante é muito menor que o original,
porém alguns dados sonoros são perdidos.  Você só notaria se estivesse
reproduzindo a música em um equipamento de alta qualidade e se tivesse um
ouvido bem aguçado.  Para efeitos práticos, você está ouvindo a mesma música e
economizando muito espaço em disco.


Outro exemplo de compactação com perdas são as imagens
**jpg**.  Imagine que você tem uma imagem com 60000 tons de
cor diferentes, mas alguns tons são muito próximos de outros, então o
compactador resume para 20000 tons de cor e a imagem terá 1/3 do tamanho
original e o nosso olho conseguirá entender a imagem sem problemas e quase não
perceberá a diferença.  Exemplos de extensões utilizadas em imagens compactadas
são **jpg**, **png**,
**gif**.


Apesar das vantagens da grande taxa de compactação conseguida nos processos com
perdas, nem sempre podemos utilizá-lo.  Quando compactamos um texto ou um
programa, não podemos ter perdas, senão o nosso texto sofre alterações ou o
programa não executa.  Nem mesmo podemos tem perdas quando compactamos imagens
ou musicas que serão utilizadas em processos posteriores de masterização,
mixagem ou impressão em alta qualidade.





 cpctd-extensoes">###Extensões de arquivos compactados

As extensões identificam o tipo de um arquivo e assim o programa o programa
necessário para trabalhar com aquele tipo de arquivo.  Existem dezenas de
extensões que identificam arquivos compactados.  Quando um arquivo (ou
arquivos) é compactado, uma extensão correspondente ao programa usado é
adicionada ao nome do arquivo (caso o arquivo seja compactado pelo
<command>gzip receberá a extensão <filename>.gz</filename>, por
exemplo).  Ao descompactar acontece o contrário: a extensão é retirada do
arquivo.  Abaixo segue uma listagem de extensões mais usadas e os programas
correspondentes:

<itemizedlist>
<listitem>

<filename>.gz</filename> - Arquivo compactado pelo <command>gzip.
Use o programa <command>gzip para descompacta-lo (para detalhes veja
<xref linkend="cpctd-gzip"/>).  <filename>.bz2</filename> - Arquivo compactado
pelo <command>bzip2.  Use o programa <command>bzip2 para
descompacta-lo (para detalhes veja <xref linkend="cpctd-bzip2"/>).


<listitem>

<filename>.Z</filename> - Arquivo compactado pelo programa
<command>compress.  Use o programa <command>uncompress para
descompacta-lo.


<listitem>

<filename>.zip</filename> - Arquivo compactado pelo programa
<command>zip.  Use o programa <command>unzip para
descompacta-lo.


<listitem>

<filename>.rar</filename> - Arquivo compactado pelo programa
<command>rar.  Use o programa <command>rar para
descompacta-lo.


<listitem>

<filename>.tar.gz</filename> - Arquivo compactado pelo programa
<command>gzip no utilitário de arquivamento <command>tar.
Para descompacta-lo, você pode usar o <command>gzip e depois o
<command>tar ou somente o programa <command>tar usando a
opção <literal>-z.  Para detalhes veja <xref linkend="cpctd-gzip"e
<xref linkend="cpctd-tar"/>.


<listitem>

<filename>.tgz</filename> - Abreviação de <filename>.tar.gz</filename>.


<listitem>

<filename>.tar.bz2</filename> - Arquivo compactado pelo programa
<command>bzip2 no utilitário de arquivamento <command>tar.
Para descompacta-lo, você pode usar o <command>bzip2 e depois o
<command>tar ou somente o programa <command>tar usando a
opção <literal>-j.  Para detalhes veja <xref linkend="cpctd-bzip2"/>
e <xref linkend="cpctd-tar"/>.


<listitem>

<filename>.tar.Z</filename> - Arquivo compactado pelo programa
<command>compress no utilitário de arquivamento
<command>tar.  Para descompacta-lo, você pode usar o
<command>uncompress e depois o <command>tar ou somente o
programa <command>tar usando a opção <literal>-Z.  Para
detalhes veja <xref linkend="cpctd-tar"/>.





 cpctd-gzip">###gzip

É praticamente o compactador padrão do <command>GNU/Linux, possui uma
ótima taxa de compactação e velocidade.  A extensão dos arquivos compactados
pelo <command>gzip é a <filename>.gz</filename>, na versão para
<command>DOS, <command>Windows NT é usada a extensão
<filename>.z</filename>.


<command>gzip [**opções**] [**arquivos**]


Onde:

<variablelist>
<varlistentry>
<term>arquivos
<listitem>

Especifica quais arquivos serão compactados pelo <command>gzip.  Caso
seja usado um <literal>-, será assumido a entrada padrão.  coringas
podem ser usados para especificar vários arquivos de uma só vez (veja <xref linkend="basico-coringas"/>).



<varlistentry>
<term>Opções
<term>-d, --decompress [arquivo]
<listitem>

Descompacta um arquivo.



<varlistentry>
<term>-f
<listitem>

Força a compactação, compactando até mesmo links.



<varlistentry>
<term>-l [arquivo]
<listitem>

Lista o conteúdo de um arquivo compactado pelo <command>gzip.



<varlistentry>
<term>-r
<listitem>

Compacta diretórios e sub-diretórios.



<varlistentry>
<term>-c [arquivo]
<listitem>

Descompacta o arquivo para a saída padrão.



<varlistentry>
<term>-t [arquivo]
<listitem>

Testa o arquivo compactado pelo <command>gzip.



<varlistentry>
<term>-[num], --fast, --best
<listitem>

Ajustam a taxa de compactação/velocidade da compactação.  Quanto melhor a taxa
menor é a velocidade de compactação e vice versa.  A opção
<literal>--fast permite uma compactação rápida e tamanho do arquivo
maior.  A opção <literal>--best permite uma melhor compactação e uma
velocidade menor.


O uso da opção <literal>-[número] permite especificar uma compactação
individualmente usando números entre 1 (menor compactação) e 9 (melhor
compactação).  É útil para buscar um bom equilibro entre taxa de
compactação/velocidade (especialmente em computadores muito lentos).



</variablelist>

Quando um arquivo é compactado pelo <command>gzip, é automaticamente
acrescentada a extensão <filename>.gz</filename> ao seu nome.


O <command>gzip também reconhece arquivos compactados pelos programas
<command>zip, <command>compress, <command>compress
-H e <command>pack.  As permissões de acesso dos arquivos
são também armazenadas no arquivo compactado.


Exemplos:

<itemizedlist>
<listitem>

<literal>gzip -9 texto.txt - Compacta o arquivo
<filename>texto.txt</filename> usando a compactação máxima (compare o tamanho
do arquivo compactado usando o comando <literal>ls -la).


<listitem>

<literal>gzip -d texto.txt.gz - Descompacta o arquivo
<filename>texto.txt</filename>


<listitem>

<literal>gzip -c texto.txt.gz - Descompacta o arquivo
<filename>texto.txt</filename> para a tela


<listitem>

<literal>gzip -9 *.txt - Compacta todos os arquivos que terminam com
<filename>.txt</filename>


<listitem>

<literal>gzip -t texto.txt.gz - Verifica o arquivo
<filename>texto.txt.gz</filename>.





 cpctd-zip">###zip

Utilitário de compactação compatível com <command>pkzip (do
<command>DOS) e trabalha com arquivos de extensão
<filename>.zip</filename>.  Possui uma ótima taxa de compactação e velocidade
no processamento dos arquivos compactados (comparando-se ao
<command>gzip).


<command>zip [**opções**] [**arquivo-destino**] [**arquivos-origem**]


Onde:

<variablelist>
<varlistentry>
<term>arquivo-destino
<listitem>

Nome do arquivo compactado que será gerado.



<varlistentry>
<term>arquivos-origem
<listitem>

Arquivos/Diretórios que serão compactados.  Podem ser usados coringas para
especificar mais de um arquivo de uma só vez (veja <xref linkend="basico-coringas"/>).



<varlistentry>
<term>opções
<term>-r
<listitem>

Compacta arquivos e sub-diretórios.



<varlistentry>
<term>-e
<listitem>

Permite encriptar o conteúdo de um arquivo <filename>.zip</filename> através de
senha.  A senha será pedida no momento da compactação.



<varlistentry>
<term>-f
<listitem>

Somente substitui um arquivo compactado existente dentro do arquivo
<filename>.zip</filename> somente se a versão é mais nova que a atual.  Não
acrescenta arquivos ao arquivo compactado.  Deve ser executado no mesmo
diretório onde o programa <command>zip foi executado anteriormente.



<varlistentry>
<term>-F
<listitem>

Repara um arquivo <filename>.zip</filename> danificado.



<varlistentry>
<term>-[NUM]
<listitem>

Ajusta a qualidade/velocidade da compactação.  Pode ser especificado um número
de 1 a 9.  O 1 permite mínima compactação e máxima velocidade, 9 permite uma
melhor compactação e menor velocidade.



<varlistentry>
<term>-i [arquivos]
<listitem>

Compacta somente os [arquivos] especificados.



<varlistentry>
<term>-j
<listitem>

Se especificado, não armazena caminhos de diretórios.



<varlistentry>
<term>-m
<listitem>

Apaga os arquivos originais após a compactação.



<varlistentry>
<term>-T [arquivo]
<listitem>

Procura por erros em um arquivo <filename>.zip</filename>.  Caso sejam
detectados problemas, utilize a opção <literal>-F para corrigi-los.



<varlistentry>
<term>-y
<listitem>

Armazena links simbólicos no arquivo <filename>.zip</filename>.  Por padrão, os
links simbólicos são ignorados durante a compactação.



<varlistentry>
<term>-k [arquivo]
<listitem>

Modifica o [arquivo] para ter compatibilidade total com o
<command>pkzip do <command>DOS.



<varlistentry>
<term>-l
<listitem>

Converte saltos de linha <command>UNIX (LF) para o formato CR+LF
(usados pelo <command>DOS).  Use esta opção com arquivos Texto.



<varlistentry>
<term>-ll
<listitem>

Converte saltos de linha <command>DOS (CR+LF) para o formato
<command>UNIX (LF).  Use esta opção com arquivos texto.



<varlistentry>
<term>-n [extensão]
<listitem>

Não compacta arquivos identificados por [extensão].  Ele é armazenado sem
compactação no arquivo <filename>.zip</filename>, muito útil para uso com
arquivos já compactados.


Caso sejam especificados diversas extensões de arquivos, elas devem ser
separadas por <literal>: - Por exemplo, <literal>zip -n .zip:.tgz
arquivo.zip *.txt.



<varlistentry>
<term>-q
<listitem>

Não mostra mensagens durante a compactação do arquivo.



<varlistentry>
<term>-u
<listitem>

Atualiza/adiciona arquivos ao arquivo <filename>.zip</filename>



<varlistentry>
<term>-X
<listitem>

Não armazena detalhes de permissões, UID, GID e datas dos arquivos.



<varlistentry>
<term>-z
<listitem>

Permite incluir um comentário no arquivo <filename>.zip</filename>.



</variablelist>

Caso o nome de arquivo de destino não termine com <filename>.zip</filename>,
esta extensão será automaticamente adicionada.  Para a descompactação de
arquivos <filename>.zip</filename> no <command>GNU/Linux, é
necessário o uso do utilitário <command>unzip.  Exemplos:

<itemizedlist>
<listitem>

<literal>zip textos.zip *.txt - Compacta todos os arquivos com a
extensão <filename>.txt</filename> para o arquivo
<filename>textos.zip</filename> (compare o tamanho do arquivo compactado
digitando <literal>ls -la).


<listitem>

<literal>zip -r textos.zip /usr/*.txt - Compacta todos os arquivos
com a extensão <filename>.txt</filename> do diretório <filename>/usr</filename>
e sub-diretórios para o arquivo <filename>textos.zip</filename>.


<listitem>

<literal>zip -9 textos.zip * - Compacta todos os arquivos do
diretório atual usando a compactação máxima para o arquivo
<filename>textos.zip</filename>.


<listitem>

<literal>zip -T textos.zip - Verifica se o arquivo
<filename>textos.zip</filename> contém erros.





 cpctd-unzip">###unzip

Descompacta arquivos <filename>.zip</filename> criados com o programa
<command>zip.  Este programa também é compatível com arquivos
compactados pelo <command>pkzip do <command>DOS.


<command>unzip [**opções**] [**arquivo.zip**]
[**arquivos-extrair**] [**-d
diretório**]


Onde:

<variablelist>
<varlistentry>
<term>arquivo.zip
<listitem>

Nome do arquivo que deseja descompactar.  Podem ser usados coringas para
especificar mais de um arquivo para ser descompactado.



<varlistentry>
<term>arquivos-extrair
<listitem>

Nome dos arquivos (separados por espaço) que serão descompactados do arquivo
<filename>.zip</filename>.  Caso não seja especificado, é assumido
<literal>* (todos os arquivos serão descompactados).


Se for usado <literal>-x arquivos, os arquivos especificados não
serão descompactados.  O uso de coringas é permitido.



<varlistentry>
<term>-d diretório
<listitem>

Diretório onde os arquivos serão descompactados.  Caso não for especificado, os
arquivos serão descompactados no diretório atual.



<varlistentry>
<term>opções
<term>-c
<listitem>

Descompacta os arquivos para stdout (saída padrão) ao invés de criar arquivos.
Os nomes dos arquivos também são mostrados (veja a opção
<literal>-p).



<varlistentry>
<term>-f
<listitem>

Descompacta somente arquivos que existam no disco e mais novos que os atuais.



<varlistentry>
<term>-l
<listitem>

Lista os arquivos existentes dentro do arquivo <filename>.zip</filename>.



<varlistentry>
<term>-M
<listitem>

Efetua uma pausa a cada tela de dados durante o processamento (a mesma função
do comando <command>more).



<varlistentry>
<term>-n
<listitem>

Nunca substitui arquivos já existentes.  Se um arquivo existe ele é pulado.



<varlistentry>
<term>-o
<listitem>

Substitui arquivos existentes sem perguntar.  Tem a função contrária a opção
<literal>-n.



<varlistentry>
<term>-P [SENHA]
<listitem>

Permite descompactar arquivos <filename>.zip</filename> usando a [SENHA].
CUIDADO!  qualquer usuário conectado em seu sistema pode ver a senha digitada
na linha de comando digitada.



<varlistentry>
<term>-p
<listitem>

Descompacta os arquivos para stdout (saída padrão) ao invés de criar arquivos.
Os nomes dos arquivos não são mostrados (veja a opção <literal>-c).



<varlistentry>
<term>-q
<listitem>

Não mostra mensagens.



<varlistentry>
<term>-t
<listitem>

Verifica o arquivo <filename>.zip</filename> em busca de erros.



<varlistentry>
<term>-u
<listitem>

Idêntico a opção <literal>-f só que também cria arquivos que não
existem no diretório.



<varlistentry>
<term>-v
<listitem>

Mostra mais detalhes sobre o processamento do <command>unzip.



<varlistentry>
<term>-z
<listitem>

Mostra somente o comentário existente no arquivo.



</variablelist>

Por padrão o <command>unzip também descompacta sub-diretórios caso o
arquivo <filename>.zip</filename> tenha sido gerado com <command>zip
-r.


Exemplos:

<itemizedlist>
<listitem>

<literal>unzip texto.zip - Descompacta o conteúdo do arquivo
<filename>texto.zip</filename> no diretório atual.


<listitem>

<literal>unzip texto.zip carta.txt - Descompacta somente o arquivo
<filename>carta.txt</filename> do arquivo <filename>texto.zip</filename>.


<listitem>

<literal>unzip texto.zip -d /tmp/texto - Descompacta o conteúdo do
arquivo <filename>texto.zip</filename> para o diretório
<filename>/tmp/texto</filename>.


<listitem>

<literal>unzip -l texto.zip - Lista o conteúdo do arquivo
<filename>texto.zip</filename>.


<listitem>

<literal>unzip -t texto.zip - Verifica o arquivo
<filename>texto.zip</filename>.






 cpctd-tar">###tar

Na verdade o <command>tar não é um compactador e sim um "arquivador"
(ele junta vários arquivos em um só), mas pode ser usado em conjunto com um
compactar (como o <command>gzip ou <command>zip) para
armazena-los compactados.  O <command>tar também é muito usado para
cópias de arquivos especiais ou dispositivos do sistema.  É comum encontrar
arquivos com a extensão <filename>.tar</filename>,
<filename>.tar.gz</filename>, <filename>.tgz</filename>,
<filename>.tar.bz2</filename>, <filename>.tar.Z</filename>,
<filename>.tgZ</filename>, o primeiro é um arquivo normal gerado pelo
<command>tar e todos os outros são arquivos gerados através
<command>tar junto com um programa de compactação
(<command>gzip (<filename>.gz</filename>), <command>bzip2
(<filename>.bz2</filename>) e <command>compress
(<filename>.Z</filename>).


<command>tar [**opções**]
[**arquivo-destino**]
[**arquivos-origem**]


Onde:

<variablelist>
<varlistentry>
<term>arquivo-destino
<listitem>

É o nome do arquivo de destino.  Normalmente especificado com a extensão
<filename>.tar</filename> caso seja usado somente o arquivamento ou
<filename>.tar.gz</filename>/<filename>.tgz</filename> caso seja usada a
compactação (usando a opção <literal>-z).



<varlistentry>
<term>arquivos-origem
<listitem>

Especifica quais arquivos/diretórios serão compactados.



<varlistentry>
<term>opções
<term>-c, --create
<listitem>

Cria um novo arquivo <filename>.tar</filename>



<varlistentry>
<term>-t, --list
<listitem>

Lista o conteúdo de um arquivo <filename>.tar</filename>



<varlistentry>
<term>-u, --update
<listitem>

Atualiza arquivos compactados no arquivo <filename>.tar</filename>



<varlistentry>
<term>-f, --file [HOST:]F
<listitem>

Usa o arquivo especificado para gravação ou o dispositivo
<filename>/dev/rmt0</filename>.



<varlistentry>
<term>-j, --bzip2
<listitem>

Usa o programa <command>bzip2 para processar os arquivos do
<command>tar



<varlistentry>
<term>-l, --one-file-system
<listitem>

Não processa arquivos em um sistema de arquivos diferentes de onde o
<command>tar foi executado.



<varlistentry>
<term>-M, --multi-volume
<listitem>

Cria/lista/descompacta arquivos em múltiplos volumes.  O uso de arquivos em
múltiplos volumes permite que uma grande cópia de arquivos que não cabe em um
disquete, por exemplo, seja feita em mais de um disquete.



<varlistentry>
<term>-o
<listitem>

Grava o arquivo no formato VT7 ao invés do ANSI.



<varlistentry>
<term>-O, --to-stdout
<listitem>

Descompacta arquivos para a saída padrão ao invés de gravar em um arquivo.



<varlistentry>
<term>--remove-files
<listitem>

Apaga os arquivos de origem após serem processados pelo <command>tar.



<varlistentry>
<term>-R, --record-number
<listitem>

Mostra o número de registros dentro de um arquivo <filename>tar</filename> em
cada mensagem.



<varlistentry>
<term>--totals
<listitem>

Mostra o total de bytes gravados com a opção <literal>--create.



<varlistentry>
<term>-v
<listitem>

Mostra os nomes dos arquivos enquanto são processados.



<varlistentry>
<term>-V [NOME]
<listitem>

Inclui um [NOME] no arquivo <command>tar.



<varlistentry>
<term>-W, --verify
<listitem>

Tenta verificar o arquivo gerado pelo <command>tar após grava-lo.



<varlistentry>
<term>x
<listitem>

Extrai arquivos gerados pelo <command>tar



<varlistentry>
<term>-X [ARQUIVO]
<listitem>

Tenta apagar o [ARQUIVO] dentro de um arquivo compactado
<filename>.tar</filename>.



<varlistentry>
<term>-Z
<listitem>

Usa o programa <command>compress durante o processamento dos
arquivos.



<varlistentry>
<term>-z
<listitem>

Usa o programa <command>gzip durante o processamento dos arquivos.



<varlistentry>
<term>--use-compress-program [PROGRAMA]
<listitem>

Usa o [PROGRAMA] durante o processamento dos arquivos.  Ele deve aceitar a
opção <literal>-d.



<varlistentry>
<term>-[0-7][lmh]
<listitem>

Especifica a unidade e sua densidade.



</variablelist>

A extensão precisa ser especificada no arquivo de destino para a identificação
correta:

<itemizedlist>
<listitem>

Arquivos gerados pelo <command>tar precisam ter a extensão
<filename>.tar</filename>


<listitem>

Caso seja usada a opção <literal>-j para compactação, a extensão
deverá ser <filename>.tar.bz2</filename>


<listitem>

Caso seja usada a opção <literal>-z para compactação, a extensão
deverá ser <filename>.tar.gz</filename> ou <filename>.tgz</filename>


<listitem>

Caso seja usada a opção <literal>-Z para a compactação, a extensão
deverá ser <filename>.tar.Z</filename> ou <filename>.tgZ</filename>




É importante saber qual qual o tipo de compactador usado durante a geração do
arquivo <filename>.tar</filename> pois será necessário especificar a opção
apropriada para descompacta-lo (para detalhes veja <xref linkend="cpctd-extensoes"/>).


Exemplos:

<itemizedlist>
<listitem>

<literal>tar -cf index.txt.tar index.txt - Cria um arquivo chamado
<filename>index.txt.tar</filename> que armazenará o arquivo
<filename>index.txt</filename>.  Você pode notar digitando <literal>ls
-la que o arquivo <filename>index.txt</filename> foi somente
arquivado (sem compactação), isto é útil para juntar diversos arquivos em um
só.


<listitem>

<literal>tar -xf index.txt.tar - Desarquiva o arquivo
<filename>index.txt</filename> criado pelo comando acima.


<listitem>

<literal>tar -czf index.txt.tar.gz index.txt - O mesmo que o exemplo
de arquivamento anterior, só que agora é usado a opção <literal>-z
(compactação através do programa <command>gzip).  Você agora pode
notar digitando <literal>ls -la que o arquivo
<filename>index.txt</filename> foi compactado e depois arquivado no arquivo
<filename>index.txt.tar.gz</filename> (você também pode chama-lo de
<filename>index.txt.tgz</filename> que também identifica um arquivo
<filename>.tar</filename> compactado pelo <command>gzip)


<listitem>

<literal>tar -xzf index.txt.tar.gz - Descompacta e desarquiva o
arquivo <filename>index.txt.tar.gz</filename> criado com o comando acima.


<listitem>

<literal>gzip -dc index.tar.gz | tar -xf - - Faz o mesmo que o
comando acima só que de uma forma diferente: Primeiro descompacta o arquivo
<filename>index.txt.tar.gz</filename> e envia a saída do arquivo descompactado
para o <command>tar que desarquivará o arquivo
<filename>index.txt</filename>.


<listitem>

<literal>tar -cjf index.txt.tar.bz2 index.txt - Arquiva o arquivo
<filename>index.txt</filename> em <filename>index.txt.tar.bz2</filename>
compactando através do <command>bzip2 (opção -j).


<listitem>

<literal>tar -xjf index.txt.tar.bz2 - Descompacta e desarquiva o
arquivo <filename>index.txt.tar.bz2</filename> criado com o comando acima.


<listitem>

<literal>bzip2 -dc index.txt.tar.bz2 | tar -xf - - Faz o mesmo que o
comando acima só que de uma forma diferente: Primeiro descompacta o arquivo
<filename>index.txt.tar.bz2</filename> e envia a saída do arquivo descompactado
para o <command>tar que desarquivará o arquivo
<filename>index.txt</filename>.


<listitem>

<literal>tar -t index.txt.tar - Lista o conteúdo de um arquivo
<filename>.tar</filename>.


<listitem>

<literal>tar -tz index.txt.tar.gz - Lista o conteúdo de um arquivo
<filename>.tar.gz</filename>.






 cpctd-bzip2">###bzip2

É um novo compactador que vem sendo cada vez mais usado porque consegue atingir
a melhor compactação em arquivos texto se comparado aos já existentes (em
conseqüência sua velocidade de compactação também é menor; quase duas vezes
mais lento que o <command>gzip).  Suas opções são praticamente as
mesmas usadas no <command>gzip e você também pode usa-lo da mesma
forma.  A extensão dos arquivos compactados pelo <command>bzip2 é a
<filename>.bz2</filename>


<command>bzip2 [**opções**]
[**arquivos**]


Onde:

<variablelist>
<varlistentry>
<term>arquivos
<listitem>

Especifica quais arquivos serão compactados pelo <command>bzip2.
Caso seja usado um <literal>-, será assumido a entrada padrão.
coringas podem ser usados para especificar vários arquivos de uma só vez (veja
<xref linkend="basico-coringas"/>).



<varlistentry>
<term>Opções
<term>-d, --decompress [arquivo]
<listitem>

Descompacta um arquivo.



<varlistentry>
<term>-f
<listitem>

Força a compactação, compactando até mesmo links.



<varlistentry>
<term>-l [arquivo]
<listitem>

Lista o conteúdo de um arquivo compactado pelo <command>bzip2.



<varlistentry>
<term>-r
<listitem>

Compacta diretórios e sub-diretórios.



<varlistentry>
<term>-c [arquivo]
<listitem>

Descompacta o arquivo para a saída padrão.



<varlistentry>
<term>-t [arquivo]
<listitem>

Testa o arquivo compactado pelo <command>bzip2.



<varlistentry>
<term>-[num], --fast, --best
<listitem>

Ajustam a taxa de compactação/velocidade da compactação.  Quanto melhor a taxa
menor é a velocidade de compactação e vice versa.  A opção
<literal>--fast permite uma compactação rápida e tamanho do arquivo
maior.  A opção <literal>--best permite uma melhor compactação e uma
velocidade menor.


O uso da opção <literal>-[número] permite especificar uma compactação
individualmente usando números entre 1 (menor compactação) e 9 (melhor
compactação).  É útil para buscar um bom equilibro entre taxa de
compactação/velocidade (especialmente em computadores muito lentos).



</variablelist>

Quando um arquivo é compactado pelo <command>bzip2, é automaticamente
acrescentada a extensão <filename>.bz2</filename> ao seu nome.  As permissões
de acesso dos arquivos são também armazenadas no arquivo compactado.


Exemplos:

<itemizedlist>
<listitem>

<literal>bzip2 -9 texto.txt - Compacta o arquivo
<filename>texto.txt</filename> usando a compactação máxima (compare o tamanho
do arquivo compactado usando o comando <literal>ls -la).


<listitem>

<literal>bzip2 -d texto.txt.bz2 - Descompacta o arquivo
<filename>texto.txt</filename>


<listitem>

<literal>bzip2 -c texto.txt.bz2 - Descompacta o arquivo
<filename>texto.txt</filename> para a saída padrão (tela)


<listitem>

<literal>bzip2 -9 *.txt - Compacta todos os arquivos que terminam com
<filename>.txt</filename>


<listitem>

<literal>bzip2 -t texto.txt.bz2 - Verifica o arquivo
<filename>texto.txt.bz2</filename>.






 cpctd-rar">###rar

<command>rar é um compactador desenvolvido por <literal>Eugene
Roshal e possui versões para <command>GNU/Linux,
<command>DOS, <command>Windows, <command>OS/2 e
<command>Macintosh.  Trabalha com arquivos de extensão
<filename>.rar</filename> e permite armazenar arquivos compactados em vários
disquetes (múltiplos volumes).  Se trata de um produto comercial, mas decidi
coloca-lo aqui porque possui boas versões Shareware e pode ser muito útil em
algumas situações.


<command>rar [**ações**] [**opções**]
[**arquivo-destino.rar**]
[**arquivos-origem**]


Onde:

<variablelist>
<varlistentry>
<term>arquivo-destino.rar
<listitem>

É o nome do arquivo de destino



<varlistentry>
<term>arquivos-origem
<listitem>

Arquivos que serão compactados.  Podem ser usados coringas para especificar
mais de um arquivo.



<varlistentry>
<term>ações
<term>a
<listitem>

Compacta arquivos



<varlistentry>
<term>x
<listitem>

Descompacta arquivos



<varlistentry>
<term>d
<listitem>

Apaga arquivos especificados



<varlistentry>
<term>t
<listitem>

Verifica o arquivo compactado em busca de erros.



<varlistentry>
<term>c
<listitem>

Inclui comentário no arquivo compactado



<varlistentry>
<term>r
<listitem>

Repara um arquivo <filename>.rar</filename> danificado



<varlistentry>
<term>l
<listitem>

Lista arquivos armazenados no arquivo compactado



<varlistentry>
<term>u
<listitem>

Atualiza arquivos existentes no arquivo compactado.



<varlistentry>
<term>m
<listitem>

Compacta e apaga os arquivos de origem (move).



<varlistentry>
<term>e
<listitem>

Descompacta arquivos para o diretório atual



<varlistentry>
<term>p
<listitem>

Mostra o conteúdo do arquivo na saída padrão



<varlistentry>
<term>rr
<listitem>

Adiciona um registro de verificação no arquivo



<varlistentry>
<term>s
<listitem>

Converte um arquivo <filename>.rar</filename> normal em arquivo auto-extráctil.
Arquivos auto-extrácteis são úteis para enviar arquivos a pessoas que não tem o
programa <command>rar.  Basta executar o arquivo e ele será
automaticamente descompactado (usando o sistema operacional que foi criado).
Note que esta opção requer que o arquivo <filename>default.sfx</filename>
esteja presente no diretório home do usuário.  Use o comando
<command>find para localiza-lo em seu sistema.



<varlistentry>
<term>opções
<term>o+
<listitem>

Substitui arquivos já existentes sem perguntar



<varlistentry>
<term>o-
<listitem>

Não substitui arquivos existentes



<varlistentry>
<term>sfx
<listitem>

Cria arquivos auto-extrácteis.  Arquivos auto-extrácteis são úteis para enviar
arquivos a pessoas que não tem o programa <command>rar.  Basta
executar o arquivo e ele será automaticamente descompactado.  Note que este
processo requer que o arquivo <filename>default.sfx</filename> esteja presente
no diretório home do usuário.  Use o comando <command>find para
localiza-lo em seu sistema.



<varlistentry>
<term>y
<listitem>

Assume <literal>sim para todas as perguntas



<varlistentry>
<term>r
<listitem>

Inclui sub-diretórios no arquivo compactado



<varlistentry>
<term>x [ARQUIVO]
<listitem>

Processa tudo menos o [ARQUIVO].  Pode ser usados coringas



<varlistentry>
<term>v[TAMANHO]
<listitem>

Cria arquivos com um limite de tamanho.  Por padrão, o tamanho é especificado
em bytes, mas o número pode ser seguido de <literal>k (kilobytes) ou
<literal>m(megabytes).


Exemplo: <literal>rar a -v1440k ... ou <literal>rar a -v10m
...



<varlistentry>
<term>p [SENHA]
<listitem>

Inclui senha no arquivo.  CUIDADO, pessoas conectadas em seu sistema podem
capturar a linha de comando facilmente e descobrir sua senha.



<varlistentry>
<term>m [0-5]
<listitem>

Ajusta a taxa de compactação/velocidade de compactação.  0 não faz compactação
alguma (mais rápido) somente armazena os arquivos, 5 é o nível que usa mais
compactação (mais lento).



<varlistentry>
<term>ed
<listitem>

Não inclui diretórios vazios no arquivo



<varlistentry>
<term>isnd
<listitem>

Ativa emissão de sons de alerta pelo programa



<varlistentry>
<term>ierr
<listitem>

Envia mensagens de erro para stderr



<varlistentry>
<term>inul
<listitem>

Desativa todas as mensagens



<varlistentry>
<term>ow
<listitem>

Salva o dono e grupo dos arquivos.



<varlistentry>
<term>ol
<listitem>

Salva links simbólicos no arquivo ao invés do arquivo físico que o link faz
referência.



<varlistentry>
<term>mm[f]
<listitem>

Usa um método especial de compactação para arquivos multimídia (sons, vídeos,
etc).  Caso for usado <literal>mmf, força o uso do método multimídia
mesmo que o arquivo compactado não seja deste tipo.



</variablelist>

Os arquivos gerados pelo <command>rar do <command>GNU/Linux
podem ser usados em outros sistemas operacionais, basta ter o
<command>rar instalado.  Quando é usada a opção <literal>-v
para a criação de múltiplos volumes, a numeração dos arquivos é feita na forma:
<filename>arquivo.rar</filename>, <filename>arquivo.r00</filename>,
<filename>arquivo.r01</filename>, etc, durante a descompactação os arquivos
serão pedidos em ordem.  Se você receber a mensagem <literal>cannot modify
volume durante a criação de um arquivo <filename>.rar</filename>,
provavelmente o arquivo já existe.  Apague o arquivo existente e tente
novamente.


Exemplos:

<itemizedlist>
<listitem>

<literal>rar a texto.rar texto.txt - Compacta o arquivo
<filename>texto.txt</filename> em um arquivo com o nome
<filename>texto.rar</filename>


<listitem>

<literal>rar x texto.rar - Descompacta o arquivo
<filename>texto.rar</filename>


<listitem>

<literal>rar a -m5 -v1400k textos.rar * - Compacta todos os arquivos
do diretório atual, usando a compactação máxima no arquivo
<filename>textos.rar</filename>.  Note que o tamanho máximo de cada arquivo é
1440 para ser possível grava-lo em partes para disquetes.


<listitem>

<literal>rar x -v -y textos.rar - Restaura os arquivos em múltiplos
volumes criados com o processo anterior.  Todos os arquivos devem ter sido
copiados dos disquetes para o diretório atual antes de prosseguir.  A opção
<literal>-y é útil para não precisar-mos responder
<literal>yes a toda pergunta que o <command>rar fizer.


<listitem>

<literal>rar t textos.rar - Verifica se o arquivo
<filename>textos.rar</filename> possui erros.


<listitem>

<literal>rar r textos.rar - Repara um arquivo
<filename>.rar</filename> danificado.





