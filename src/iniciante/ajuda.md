
chapter <!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" ajuda">###Como obter ajuda

Dúvidas são comuns durante o aprendizado e uso do <command>Linux e existem
várias maneiras de se obter ajuda e encontrar a resposta para algum problema.
O <command>GNU/Linux é um sistema bem documentado, e ter um programa
bem documentado é o princípio para seu sucesso junto a utilizadores e desenvolvedores,
pois demonstra a dedicação de seu desenvolvedor em garantir boa usabilidade.
Abaixo segue algumas formas úteis para encontrar a solução de sua dúvida, vale
a pena conhece-las.



 ajuda-man">###Páginas de Manual

As **páginas de manual** acompanham quase todos os programas
<command>GNU/Linux. Elas trazem uma descrição básica do
comando/programa e detalhes sobre o funcionamento de opção.  

<para condition='descricaod'>
É mais comum fazer a visualização de uma página de manual em modo texto, com 
rolagem vertical, em geral com a aparência de arquivos
visualizados com os comandos <command>less e <command>more.  
Também documenta parâmetros usados em alguns arquivos de configuração. 


A utilização da página de manual é simples, digite:


<command>man [**seção**]
[**comando/arquivo**]

<!-- [ %OPCOES [ --> 

**onde:**

<variablelist>
<varlistentry>
<term>**seção**
<listitem>

É a seção de manual que será aberta, se omitido, mostra a
**primeira** seção sobre o comando encontrada (em ordem
crescente).



<varlistentry>
<term>**comando/arquivo**
<listitem>

Comando/arquivo que deseja pesquisar.



</variablelist>
<!-- ]]> -->

A navegação dentro das páginas de manual é feita usando-se as teclas abaixo:

<itemizedlist>
<listitem>

q - Sai da página de manual


<listitem>

PageDown ou f - Rola uma página abaixo (25 linhas em consoles tradicionais 80x25)


<listitem>

PageUP ou w - Rola uma página acima (25 linhas em consoles tradicionais 80x25)


<listitem>

SetaAcima ou k - Rola 1 linha acima


<listitem>

SetaAbaixo ou e - Rola 1 linha abaixo


<listitem>

r - Redesenha a tela (refresh)


<listitem>

p ou g - Inicio da página


<listitem>

h - Ajuda sobre as teclas e atalhes da página de manual


<listitem>

s - Salva a página de manual em formato texto no arquivo especificado (por
exemplo: <filename>/tmp/ls</filename>).




Cada seção da página de manual contém explicações sobre uma determinada parte
do sistema.  As seções são organizadas em diretórios separados e localizadas no
diretório 
<!-- [ %DEBIAN [ --> <filename>/usr/man</filename> <!-- ]]> -->.  Os programas/arquivos são
classificados nas seguintes seções:

<orderedlist numeration="arabic">
<listitem>

Programas executáveis ou comandos internos


<listitem>

Chamadas do sistema (funções oferecidas pelo kernel)


<listitem>

Chamadas de Bibliotecas (funções dentro de bibliotecas do sistema)


<listitem>

Arquivos especiais (normalmente encontrados no diretório
<filename>/dev</filename>)


<listitem>

Formatos de arquivos e convenções (<filename>/etc/inittab</filename> por
exemplo).


<listitem>

Jogos


<listitem>

Pacotes de macros e convenções (por exemplo <command>man)


<listitem>

Comandos de Administração do sistema (normalmente usados pelo root)


<listitem>

Rotinas do kernel (não padrões)


</orderedlist>

A documentação de um programa também pode ser encontrada em 2 ou mais
categorias, como é o caso do arquivo <filename>host_access</filename> que é
documentado na seção 3 (bibliotecas) e 5 (formatos de arquivo e convenções).  Por 
este motivo é necessário digitar <literal>man 5 hosts_access para ler a
página sobre o formato do arquivo, porque o comando <command>man
procura a página de manual nas seções em ordem crescente e a digitação do
comando <command>man hosts_access abriria a seção 3.


As páginas de manual contém algumas regras para facilitar a compreensão do
comando:

<itemizedlist>
<listitem>

Texto Negrito - Deve ser digitado exatamente como é mostrado


<listitem>

[bla bla bla] - Qualquer coisa dentro de <literal>[] são opcionais



<!-- [ %EXEMPLO [ --> 

Exemplo, <literal>man ls, <literal>man 5 hosts_access.

<!-- ]]> -->



 ajuda-info">###Info Pages

Idêntico as páginas de manual, mas utiliza a ligação (links) em textos
indicados por um '*', levando diretamente a ítens da infopage, ou para
outras info pages relacionadas com o tópico estudado.
Se pressionarmos &lt;Enter&gt; em cima 
de uma palavra destacada, a <command>infopages nos levará a seção 
correspondente.  

<para condition='descricaod'>
A **info pages** é útil quando sabemos o nome do comando e queremos saber para
o que ele serve.  Assim como o <command>man, também traz explicações 
detalhadas sobre uso, opções e comandos. 


Para usar a info pages, digite:


<command>info [**comando/programa**]


Se o nome do **comando/programa** não for digitado, a info
pages mostra a lista de todos os manuais de
**comandos/programas** disponíveis.  A **info
pages** possui algumas teclas de navegação úteis:

<itemizedlist>
<listitem>

q - Sai da info pages


<listitem>

?  - Mostra a tela de ajuda (que contém a lista completa de teclas de navegação
e muitos outras opções).


<listitem>

n - Avança para a próxima página


<listitem>

p - Volta uma página


<listitem>

u - Sobre um nível do conteúdo (até checar ao índice de documentos)


<listitem>

m - Permite usar a localização para encontrar uma página do
<command>info.  Pressione <literal>m, digite o comando e
tecle &lt;Enter&gt; que será levado automaticamente a página correspondente. 
Caso não digite nada e aperte a tecla <literal>TAB, o <command>info
lhe mostrará todas as opções disponíveis de busca.


<listitem>

d - Volta ao índice de documentos.




Existem muitos outras teclas de navegação úteis na info pages, mas estas são as
mais usadas.  Para mais detalhes, entre no programa <command>info e
pressione <literal>?.

<para condition='exemplos'>
Exemplo, <literal>info cvs.




 ajuda-helponline">###Ajuda na própria linha de comandos

Ajuda rápida, sendo útil para sabermos quais opções podem ser usadas com o
comando/programa.  

<para condition='descricaod'>
Quase todos os comandos/programas
<command>GNU/Linux oferecem este recurso útil para consultas
rápidas (e quando não precisamos dos detalhes das páginas de manual).  Deve 
quando se sabe o nome do programa. 
 Para acionar a **ajuda on line**, digite:


[**comando**] --help

<!-- [ %OPCOES [ --> 

**comando** - é o comando/programa que desejamos ter uma
explicação rápida.
 <!-- ]]> -->

<para condition='obs'>
O Help on Line não funciona com comandos internos (embutidos no Bash), devendo 
ser usado o comando <literal>man builtins ou o <literal>help comando
para obter ajuda.

<!-- ]]> -->
<!-- [ %EXEMPLO [ --> 

Por exemplo, <literal>ls --help.

<!-- ]]> -->



 ajuda-help">###help

Ajuda rápida, útil para saber que opções podem ser usadas com os
**comandos internos** do interpretador de comandos.  
<!-- [ %DESCRICAOD [ --> O comando <command>help somente mostra a ajuda para 
comandos internos, para ter uma ajuda similar para comandos externos, veja <xref linkend="ajuda-helponline"/>. <!-- ]]> -->
Para usar o <command>help digite:


<command>help [**comando**]

<!-- [ %EXEMPLO [ -->

Por exemplo, <literal>help echo, <literal>help exit

<!-- ]]> -->



 ajuda-apropos">###apropos

Apropos procura por **programas/comandos** através da
descrição.  
<!-- [ %DESCRICAOD [ --> É útil quando precisamos fazer alguma coisa mas não sabemos qual
comando usar.  Ele faz sua pesquisa nas páginas de manual existentes no sistema
e lista os comandos/programas que atendem a consulta.  <!-- ]]> --> Para usar o comando
<command>apropos digite:


<command>apropos [**descrição**]

<!-- [ %EXEMPLO [ --> 

Digitando <literal>apropos copy, será mostrado todos os comandos que
tem a palavra <literal>copy em sua descrição (provavelmente os
programas que copiam arquivos, mas podem ser mostrados outros também).

<!-- ]]> -->


 ajuda-whatis">###whatis

O <command>whatis exibe a função do comando especificado como argumento. 
<!-- [ %DESCRICAOD [ --> Útil quando estamos na dúvida sobre o que determinado programa faz. <!-- ]]> -->
Para usar o comando <command>whatis digite:


<command>whatis [**programa/comando**]

<!-- [ %EXEMPLO [ --> 

Digitando <literal>whatis ls, lhe será mostrada a descrição do comando 
<command>ls.

<!-- ]]> -->


 ajuda-locate">###locate

Localiza uma palavra na estrutura de arquivos/diretórios do sistema.  
<!-- [ %DESCRICAOD [ --> É útil quando queremos localizar onde um comando ou programa se encontra (para
copia-lo, curiosidade, etc).  A pesquisa é feita em um banco de dados
construído com o comando <command>updatedb sendo feita a partir do
diretório raíz <literal>/ e sub-diretórios. <!-- ]]> --> Para fazer uma consulta
com o <command>locate usamos:


<command>locate [**expressão**]


A **expressão** deve ser o nome de um arquivo diretório ou
ambos que serão procurados na estrutura de diretórios do sistema.  Como a
consulta por um programa costuma localizar também sua página de manual, é
recomendável usar **"pipes"** para filtrar a saída do comando
<!-- [ %INIC-INTER [ --> (para detalhes veja <xref linkend="redir-pipe"<!-- ]]> -->.

<!-- [ %EXEMPLO [ -->

Por exemplo, para listar os diretórios que contém o nome
"**cp**": <literal>locate cp.  Agora mostrar somente
arquivos binários, usamos: <literal>locate cp|grep bin/

<!-- ]]> -->


 ajuda-which">###which

Localiza um programa na estrutura de diretórios do path.  
<!-- [ %DESCRICAOD [ --> É muito semelhante ao
<command>locate, mas a busca é feita no <literal>path do
sistema e somente são mostrados arquivos executáveis. 

<!-- ]]> -->

<command>which [**programa/comando**].



 ajuda-howto">###Documentos HOWTO's

São documentos em formato **texto**,
**html**, etc, que explicam como fazer determinada tarefa ou
como um programa funciona.  
<!-- [ %DESCRICAOD [ --> Normalmente são feitos na linguagem <command>SGML e 
convertidos para outros formatos (como o texto, HTML, Pos Script) depois de prontos.


Estes trazem explicações detalhadas desde como usar o <command>bash
até sobre como funciona o modem ou como montar um **servidor internet
completo**. <!-- ]]> --> 

Os HOWTO´s podem ser encontrados no diretório do projeto
de documentação do <command>GNU/Linux (LDP) em ("http://www.w3.org/1999/xlink) [](ftp://metalab.unc.edu/pub/Linux/docs/HOWTO)ftp://metalab.unc.edu/pub/Linux/docs/HOWTO/
ou traduzidos para o Português pelo LDP-BR em ("http://www.w3.org/1999/xlink) [](http://www.tldp.org/projetos/howto/traduzidos.php">http://www.tldp.org/projetos/howto/traduzidos.php.
Caso tenha optado por instalar o pacote de HOWTO's de sua distribuição
<command>GNU/Linux, eles podem ser encontrados em:
<filename>/usr/doc/how-to</filename>



 userlevel='inter' ajuda-howto-listagem">###Listagem de HOWTO's

Esta seção tem a intenção de facilitar a localização de um documento que trata
do assunto desejado ou te despertar a curiosidade sobre alguns assuntos do
SO-GNU/Linux através da descrição contida nos documentos.  Segue abaixo uma
listagem de HOWTO's do projeto LDP organizadas por sub-seções com a descrição
do assunto que cada um deles aborda.


 userlevel='inter' s43.8.1.1">###Introdução ao Sistema / Instalação / Configurações / Kernel
<variablelist>
<varlistentry>
<term>Access-HOWTO
<listitem>

O HOWTO de Acesso ao <command>GNU/Linux cobre o uso de tecnologia
adaptada para tornar o <command>GNU/Linux acessível àqueles que não o
utilizam.  Ele cobre áreas onde ele pode usar soluções tecnológicas adaptadas.



<varlistentry>
<term>Bash-Prompt-HOWTO
<listitem>

Explica como criar e controlar um terminal e aviso de comando xterm, incluindo
seqüências de escape incorporadas para passar o nome do usuário, diretório
atual, hora, uso de cores ANSI, etc.



<varlistentry>
<term>Bootdisk-HOWTO
<listitem>

Explica como criar seu próprio disco de inicialização/raíz para o
<command>GNU/Linux.



<varlistentry>
<term>BootPrompt-HOWTO
<listitem>

Este documento reúne a maioria dos parâmetros de inicialização que podem ser
passados ao kernel do <command>GNU/Linux durante a inicialização do
sistema.  Também explica como o kernel classifica os argumentos de
inicialização e também os softwares usados para inicialização do kernel do
GNU/Linux.



<varlistentry>
<term>Compaq-Remote-Insight-Board-HOWTO
<listitem>

Descreve como instalar o Linux no servidor Compaq ProLiant.



<varlistentry>
<term>Config-HOWTO
<listitem>

Este documento ensina como fazer um ajuste fino em sua máquina
<command>GNU/Linux recém instalada rápido e fácil.  Neste documento
você encontrará um conjunto de configurações para as aplicações e serviços mais
populares.



<varlistentry>
<term>Distribution-HOWTO
<listitem>

Este documento tem a intenção de ajudar novos usuários escolherem uma
distribuição <command>GNU/Linux e ajudar usuários experientes a
avaliar o estado do marketing no <command>GNU/Linux Ele não planeja
ser uma lista completa de distribuições <command>GNU/Linux para todas
as plataformas, mas ao invés disso se focaliza nas distribuições em Inglês
baseadas no processador Intel, disponíveis em CD-ROM e acessíveis a usuários
novatos no sistema.



<varlistentry>
<term>From-PowerUp-To-Bash-Prompt-HOWTO
<listitem>

Contém uma breve descrição sobre o que acontece no sistema
<command>GNU/Linux, do momento que liga o seu computador até o login
no aviso do bash.  Ele é organizado por pacotes para torna-lo fácil para
pessoas que desejam construir um sistema através do código fonte.  Entendendo
isto será útil quando precisar resolver problemas ou configurar o seu sistema.



<varlistentry>
<term>Installation-HOWTO
<listitem>

Este documento descreve como obter e instalar o software
<command>GNU/Linux.  Ele é o primeiro documento que um novo usuário
<command>GNU/Linux dev ler para iniciar no sistema.



<varlistentry>
<term>INFO-SHEET
<listitem>

Este documento oferece informações básicas sobre o sistema operacional
<command>GNU/Linux, incluindo uma explicação sobre o sistema, uma
lista de características, alguns requerimentos e alguns recursos.



<varlistentry>
<term>Kernel-HOWTO
<listitem>

Este é um guia detalhado de configuração do kernel, compilação, upgrades e
problemas para sistemas baseados.



<varlistentry>
<term>PLIP-Install-HOWTO
<listitem>

Descreve como instalar uma distribuição GNU/Linux em um computador sem placa
Ethernet, ou CD-ROM, mas apenas com uma unidade de disquetes local e um
servidor NFS remoto conectado via um cabo paralelo.



<varlistentry>
<term>Reading-List-HOWTO
<listitem>

Lista os livros mais valiosos para uma pessoa que deseja aprender o sistema
operacional Unix (especialmente o <command>GNU/Linux).



<varlistentry>
<term>Software-Building-HOWTO
<listitem>

Guia compreensivo de como construir e instalar distribuições de softwares
"genéricas" UNIX sob o <command>GNU/Linux.  Adicionalmente existe
alguma cobertura dos binários pré-empacotados "rpm" e "deb".



<varlistentry>
<term>Tips-HOWTO
<listitem>

Este documento descreve algumas dicas difíceis de encontrar e truques que fazem
o GNU/Linux um pouco melhor.



<varlistentry>
<term>Unix-and-Internet-Fundamentals-HOWTO
<listitem>

Este documento descreve a base de funcionamento dos computadores da classe PC,
sistemas operacionais Unix e a Internet em linguagem não técnica.



<varlistentry>
<term>User-Authentication-HOWTO
<listitem>

Explica como as informações de usuário e grupo são armazenadas e como os
usuários são autenticados no sistema <command>GNU/Linux (PAM) e como
melhorar a autenticação de seu sistema.



</variablelist>


 userlevel='inter' s43.8.1.2">###Adaptação do <command>GNU/Linux para idiomas específicos
<variablelist>
<varlistentry>
<term>Belarusian-HOWTO
<listitem>

Adicionando o suporte ao idioma Belarusian no Linux.



<varlistentry>
<term>Belgian-HOWTO
<listitem>

Este documento ensina a configuração do sistema <command>GNU/Linux
para o idioma Belgo.



<varlistentry>
<term>Chinese-HOWTO
<listitem>

Este documento explica como configurar o idioma Chinês no
<command>GNU/Linux.



<varlistentry>
<term>Cyrillic-HOWTO
<listitem>

Explica como utilizar o <command>GNU/Linux com o idioma Russo.



<varlistentry>
<term>Danish-HOWTO
<listitem>

Descreve como configurar o <command>GNU/Linux e vários aplicativos
<command>GNU/Linux para este idioma.



<varlistentry>
<term>Esperanto-HOWTO
<listitem>

Configuração do GNU/Linux para o idioma Esperanto.



<varlistentry>
<term>Finnish-HOWTO
<listitem>

Descreve como usar o sistema <command>GNU/Linux no idioma Finlandês.



<varlistentry>
<term>Francophones-HOWTO
<listitem>

Descreve como usar o <command>GNU/Linux no idioma Francês.



<varlistentry>
<term>German-HOWTO
<listitem>

Descreve como usar o GNU/Linux com o idioma Alemão.



<varlistentry>
<term>Hebrew-HOWTO
<listitem>

Descreve como configurar o GNU/Linux para exibir caracteres Hebreus no X-Window
e Console.



<varlistentry>
<term>Hellenic-HOWTO
<listitem>

Guia para configuração do GNU/Linux.



<varlistentry>
<term>Italian-HOWTO
<listitem>

Descreve como configurar o GNU/Linux no idioma Italiano.



<varlistentry>
<term>Polish-HOWTO
<listitem>

Configurando seu sistema GNU/Linux para o idioma Polonês.



<varlistentry>
<term>Portuguese-HOWTO
<listitem>

Configurando seu sistema GNU/Linux para o idioma Português.



<varlistentry>
<term>Serbian-HOWTO
<listitem>

Configurando seu sistema GNU/Linux para o idioma Servio.



<varlistentry>
<term>Slovenian-HOWTO
<listitem>

Como configurar os parâmetros do sistema GNU/Linux para este idioma.



<varlistentry>
<term>Spanish-HOWTO
<listitem>

Configurando o sistema GNU/Linux para o idioma Espanhol.



<varlistentry>
<term>Thai-HOWTO
<listitem>

Descreve como usar o idioma Tailandês com o <command>GNU/Linux.



<varlistentry>
<term>Turkish-HOWTO
<listitem>

Configurando o GNU/Linux para o idioma Turco.



</variablelist>


 userlevel='inter' s43.8.1.3">###Discos / Sistemas de Arquivos / Desempenho
<variablelist>
<varlistentry>
<term>Filesystems-HOWTO
<listitem>

Descreve sistemas de arquivos e o acesso aos sistemas de arquivos.



<varlistentry>
<term>Large-Disk-HOWTO
<listitem>

Tudo sobre a geometria e o limite de 1024 cilindros para os discos.



<varlistentry>
<term>LVM-HOWTO
<listitem>

Um HOWTO descritivo sobre o GNU/Linux LVM.



<varlistentry>
<term>Loopback-Encrypted-Filesystem-HOWTO
<listitem>

Este documento explica como criar e utilizar um sistema de arquivos que, quando
montado por um usuários, encripta transparentemente e dinamicamente seu
conteúdo.  O sistema de arquivos é armazenado em um arquivo regular, que pode
ser oculto ou nomeado para algo que não chama a atenção, como algo que nunca
seria procurado.  Isto permite um alto nível de segurança dos dados
armazenados.



<varlistentry>
<term>Multi-Disk-HOWTO
<listitem>

Este documento descreve como utilizar da melhor maneira múltiplos discos e
partições em um sistema <command>GNU/Linux.  Muitos dos detalhes
descritos aqui podem também ser aplicados a outros sistemas operacionais
multi-tarefas.



<varlistentry>
<term>MultiOS-HOWTO
<listitem>

Este documento cobre os procedimentos para utilizar discos rígidos removíveis
para instalar e gerenciar múltiplos sistemas operacionais alternativos enquanto
deixa um disco rígido simples fixo para proteger o sistema operacional
primário.  É muito escalável e oferece uma boa grade de proteção e um ambiente
de disco estável para o sistema operacional primário.



<varlistentry>
<term>Optical-Disk-HOWTO
<listitem>

Este documento descreve a instalação e configuração de unidades de disco óticos
para <command>GNU/Linux.



<varlistentry>
<term>Root-RAID-HOWTO
<listitem>

Este documento somente se aplica a ferramentas RAID ANTIGAS, versão 0.50 e
inferiores.  Os detalhes contidos neste documento se tornaram obsoletos com a
vasta melhoria das ferramentas RAID 0.90 e acompanhadas do patch nos kernels
das séries 2.0.37, 2.2x e 2.3x.



<varlistentry>
<term>SCSI-Programming-HOWTO
<listitem>

Este documento fala sobre a programação da interface SCSI genérica no
<command>GNU/Linux.



<varlistentry>
<term>UMSDOS-HOWTO
<listitem>

O UMSDOS é um sistema de arquivos <command>GNU/Linux.  Ele oferece
uma alternativa do sistema de arquivos EXT2.  Sua maior característica é a
coexistência com os dados DOS existentes, compartilhando a mesma partição.



</variablelist>


 userlevel='inter' s43.8.1.4">###Escrita de Documentação / Editores
<variablelist>
<varlistentry>
<term>C-editing-with-VIM-HOWTO
<listitem>

Oferece dicas para editar arquivos desta linguagem e com sintaxe similar como
<command>C++ e <command>Java.



<varlistentry>
<term>Emacs-Beginner-HOWTO
<listitem>

Este documento introduz os usuários <command>GNU/Linux no editor
Emacs.  Ele assume o mínimo de conhecimento com o editor de texto
<command>vi ou similar.



<varlistentry>
<term>Emacspeak-HOWTO
<listitem>

Este documento descreve como um usuário pode usar o sistema com um sintetizador
de voz no lugar do monitor de vídeo.  Ele descreve como ter o
<command>GNU/Linux rodando em seu PC e como configura-lo para falar.
Ele também sugere como aprender sobre o Unix.



<varlistentry>
<term>HOWTO-HOWTO
<listitem>

Lista de ferramentas, processos e dicas para ajudar os autores de HOWTO's
aumentarem sua produtividade.



<varlistentry>
<term>LinuxDoc+Emacs+Ispell-HOWTO
<listitem>

Este documento é de interesse de escritores e tradutores dos HOWTO's do
<command>GNU/Linux ou qualquer outro papel para o Projeto de
Documentação do GNU/Linux.  Ele oferece dicas sobre o uso de ferramentas
incluindo o Emacs e Ispell.



<varlistentry>
<term>TeTeX-HOWTO
<listitem>

Este documento cobre a instalação básico e uso das implementações TeTeX, TeX e
LaTeX sob as maiores distribuições de <command>GNU/Linux Inglesas e
pacotes auxiliares como o GhostScript.



<varlistentry>
<term>Vim-HOWTO
<listitem>

Este documento é uma guia para configurar rapidamente o editor colorido Vim nos
sistemas Unix e GNU/Linux.  Os detalhes aqui aumentarão a produtividade dos
programadores porque o editor Vim suporta a colorização de código e fontes
negrito, aumentando a "legibilidade" do código do programa.  A produtividade do
programador aumenta de 2 a 3 vezes com um editor colorido como Vim.



</variablelist>


 userlevel='inter' s43.8.1.5">###Hardware
<variablelist>
<varlistentry>
<term>3Dfx-HOWTO
<listitem>

Este documento descreve o suporte do <command>GNU/Linux aos chips
aceleradores 3Dfx.  Também lista alguns hardwares suportados, descreve como
configurar os drivers e responde perguntas freqüêntes.



<varlistentry>
<term>4mb-Laptops
<listitem>

Como instalar o Linux em um notebook com 4MB de RAM e com HDs menores que 200
MB.



<varlistentry>
<term>Acer Laptop-HOWTO
<listitem>

Descreve como instalar o Linux em notebooks Acer.



<varlistentry>
<term>Busmouse-HOWTO
<listitem>

Descreve como instalar, configurar e usar um barramento de mouse sob o
<command>GNU/Linux.  Ele contém uma lista de barramentos suportados e
tenta responder as questões mais freqüêntes relacionadas ao assunto.



<varlistentry>
<term>CDServer-HOWTO
<listitem>

Oferece as dicas e passos para criar um servidor de CD no
<command>Linux para serem compartilhados via rede com
<command>Windows e outros sistemas operacionais.



<varlistentry>
<term>CPU-Design-HOWTO
<listitem>

Oferece referências para mostrar como uma CPU é projetada e fabricada.
Bastante interessante para estudantes de computação e outros profissionais da
área.



<varlistentry>
<term>Ftape-HOWTO
<listitem>

Este HOWTO discute o controlador de unidades tape para
<command>GNU/Linux.



<varlistentry>
<term>HP-HOWTO
<listitem>

Este documento descreve o uso dos produtos disponíveis no catálogo
Hewlett-Packard (HP) com o <command>GNU/Linux e alguns programas free
software.  Ele explica o estado do suporte para hardwares, softwares utilizados
e respostas para alguns questões freqüêntes.



<varlistentry>
<term>Hardware-HOWTO
<listitem>

Este documento lista a maioria dos hardware suportados pelo
<command>GNU/Linux e lhe ajuda a localizar os controladores
necessários.



<varlistentry>
<term>Jaz-Drive-HOWTO
<listitem>

Este HOWTO cobre a configuração e uso dos drivers Iomega 1Gb e 2Gb sob o
<command>GNU/Linux.



<varlistentry>
<term>Kodak-Digitalcam-HOWTO
<listitem>

Fazendo uma câmera Kodak digital funcionar sob GNU/GNU/Linux.



<varlistentry>
<term>Laptop-HOWTO
<listitem>

Os Notebooks são diferentes de computadores desktops/torres.  Eles usam certos
hardwares como cartões PCMCIA, portas infravermelho, baterias, estações de
encaixe.  Freqüentemente seus hardwares são mais limitados (i.e.  espaço em
disco, velocidade da CPU) então sua performance se torna menor.  Em algumas
instâncias, os notebooks podem se tornar uma substituição ao sistema desktop.
O suporte de hardware para o <command>GNU/Linux (e outros sistemas
operacionais) é algumas vezes mais limitado (i.e.  chips gráficos, modens
internos).  Os Notebooks freqüentemente utilizam hardware especializado, no
qual a localização de um controlador adequado pode se tornar uma dificuldade.
Os Notebooks são utilizados em ambientes móveis, assim existe a necessidade de
múltiplas configurações e estratégias adicionais de segurança.



<varlistentry>
<term>Modem-HOWTO
<listitem>

Ajuda com a seleção, conexão, configuração, resolução de problemas e
compreensão de modens de um PC.  Veja o Serial-HOWTO para detalhes sobre
múltiplas placas seriais.



<varlistentry>
<term>PCI-HOWTO
<listitem>

Informações sobre o que funciona com o <command>GNU/Linux e placas
<command>PCI e que o não funciona.



<varlistentry>
<term>Plug-and-Play-HOWTO
<listitem>

Este documento ajuda a compreensão e operação do Plug-and-Play e como incluir o
suporte do seu sistema <command>GNU/Linux ao Plug-and-Play.



<varlistentry>
<term>Serial-HOWTO
<listitem>

Este documento descreve características da porta serial ao invés de outros
detalhes que devem ser cobertos pelos documentos Modem-HOWTO, PPP-HOWTO,
Serial-Programming-HOWTO, ou Text-Terminal-HOWTO.  Ele lista detalhes sobre
múltiplas placas seriais contendo informações técnicas detalhadas sobre a
própria porta serial em mais detalhes do que os encontrados nos HOWTO's acima e
deve ser o suficiente para correção de problemas quando o problema é a própria
porta serial.  Se estiver trabalhando com um Modem, PPP (usado para acesso a
Internet através de uma Linha telefônica), ou um Terminal baseado em modo
texto, seus respectivos HOWTO's devem ser primeiramente consultados.



<varlistentry>
<term>Serial-Programming-HOWTO
<listitem>

Explica como programar comunicações com dispositivos através de uma porta
serial em um computador com o <command>GNU/Linux.



<varlistentry>
<term>UPS-HOWTO
<listitem>

Este documento te ajudará a conectar um uninterruptable power supply (No Break)
em seu computador <command>GNU/Linux...  se tiver a sorte de possuir
um...



<varlistentry>
<term>Wacom-Tablet-HOWTO
<listitem>

Instalação do (não somente) Wacom graphic tablets sob o
<command>GNU/Linux e / ou xfree86.



<varlistentry>
<term>Wearable-HOWTO
<listitem>

Computação móvel com <command>GNU/Linux.



<varlistentry>
<term>Winmodems-and-Linux-HOWTO
<listitem>

Este documento contém detalhes sobre a configuração de Winmodems no
<command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.1.6">###Software
<variablelist>
<varlistentry>
<term>AI-Alife-HOWTO
<listitem>

Este howto contém informações primárias sobre, e links para, várias bibliotecas
relacionadas com o AI, aplicativos, etc.  que funcionam na plataforma
GNU/Linux.  Todos eles (pelo menos) livres para uso pessoal.



<varlistentry>
<term>Apache-Overview-HOWTO
<listitem>

Oferece uma visão do servidor Web Apache e projetos relacionados.



<varlistentry>
<term>Commercial-HOWTO
<listitem>

Este documento contém uma listagem de programas comerciais e aplicações que são
oferecidas para o <command>GNU/Linux



<varlistentry>
<term>Glibc2-HOWTO
<listitem>

Este documento cobre a instalação e uso da Biblioteca GNU C versão 2 nos
sistemas GNU/Linux.



<varlistentry>
<term>RPM-HOWTO
<listitem>

Explica como utilizar o sistema de gerenciamento de pacotes RPM.



<varlistentry>
<term>Program-Library-HOWTO
<listitem>

Este documento para programadores discute como criar e usar bibliotecas no
<command>GNU/Linux.  Estas incluem bibliotecas estáticas, bibliotecas
compartilhadas e bibliotecas carregadas dinamicamente.



<varlistentry>
<term>Secure-Programs-HOWTO
<listitem>

Este documento oferece um conjunto de designs e regras de implementação para
escrever programas seguros para os sistemas Unix e Linux.  Tais programas
incluem programas aplicativos usados para visualizadores de dados remotos,
scripts CGI, servidores de rede, programas setuid/setgid.  Guias específicos
sobre C, C++, Java, Perl, Python, e Ada95 estão incluídos.



<varlistentry>
<term>Software-RAID-0.4x-HOWTO
<listitem>

RAID significa "Redundant Array of Inexpensive Disks", e significa ser um
método de criar um rápido e confiável subsistema de unidades de disco ao invés
de discos individuais.  O RAID pode se prevenir de falhas de disco e pode
também aumentar a performance obtida através de uma simples unidade de disco.
Este documento é um tutorial/HOWTO/FAQ para usuários do kernel do Linux com
extensões MD, as ferramentas associadas, e seu uso.  A extensão MD implementa o
RAID-0 (striping), RAID-1 (mirroring), RAID-4 e RAID-5 no software.  O que
significa que, com MD, nenhum hardware especial ou controladoras de disco são
requeridas para obter muitos dos benefícios do RAID.



<varlistentry>
<term>Software-RAID-HOWTO
<listitem>

Este documento descreve como usar o software RAID sob o GNU/Linux.  Ele
endereça uma versão específica da camada de software do RAID, nomeada camada
RAID 0.90, feita por Ingo Molnar e outros.  Esta é a camada RAID que será
padronizada no Linux-2.4, e também é a versão usada por kernels 2.2 do
<command>GNU/Linux vendidos por alguns vendedores.  O suporte RAID
0.90 está disponível com patches para os kernels do 2.0 e 2.2 do
<command>GNU/Linux e também é considerado ser mais estável que o
antigo suporte RAID já incluído nestes kernels.



<varlistentry>
<term>Software-Release-Practice-HOWTO
<listitem>

Este documento descreve boas práticas de lançamento para o projeto de
código-aberto <command>GNU/Linux.  Seguindo estas práticas, será
fácil e possível para os usuários construir seu código e usa-lo, e para outros
desenvolvedores entender seu código e cooperar com você para melhora-lo.  Este
documento deve ser lido por desenvolvedores iniciantes.  Desenvolvedores
experientes devem revisa-lo quando desejarem lançar um novo projeto.  Este
documento é revisado periodicamente para refletir a evolução das boas práticas
de lançamento.



</variablelist>


 userlevel='inter' s43.8.1.7">###Plataformas não Intel (x86)
<variablelist>
<varlistentry>
<term>Alpha-HOWTO
<listitem>

Este documento é uma visão rápida das CPUs Alpha, chipsets e sistemas
existentes.



<varlistentry>
<term>MILO-HOWTO
<listitem>

Este documento descreve o MIniLOader, um programa para sistemas baseados na
arquitetura Alpha que pode ser usado para inicializar a máquina e carregar o
<command>GNU/Linux.  O Linux Miniloader do Alpha (seu nome completo)
é também conhecido como MILO.



<varlistentry>
<term>MIPS-HOWTO
<listitem>

Esta FAQ descreve o porte do MIPS para o sistema operacional Linux, problemas
comuns e suas soluções, disponibilidade e mais.  Ele também tenta ser um pouco
útil a outras pessoas que desejam ler esta FAQ em uma tentativa de encontrar
informações que atualmente seriam cobertas em outro lugar.



<varlistentry>
<term>SRM-HOWTO
<listitem>

Este documento descreve como inicializar no <command>Linux/Alpha
usando o console SRM, que é a firmware de console também usada para inicializar
o Unix Compaq Tru64 (também conhecido com Digital Unix e OSF/1) e OpenVMS.



</variablelist>


 userlevel='inter' s43.8.1.8">###Programação / Compiladores / Banco de Dados
<variablelist>
<varlistentry>
<term>Assembly-HOWTO
<listitem>

Este documento descreve como programar em linguagem Assembler usando
ferramentas de programação livres, focalizando-se no desenvolvimento para ou do
Sistema Operacional <command>GNU/Linux, mais na plataforma IA-32
(i386).



<varlistentry>
<term>Bash-Prog-Intro-HOWTO
<listitem>

Este documento tem a intenção de te ajudar a iniciar na programação de shell
scripts.  Ele não tem a intenção de ser uma documento avançado.



<varlistentry>
<term>C++Programming-HOWTO
<listitem>

Discute os métodos para evitar problemas de memória no C++ e também te ajudará
a programar corretamente na linguagem C++.  As informações contidas neste
documento se aplicam a todos os sistemas operacionais que são
<command>GNU/Linux, <command>DOS, <command>BeOS,
<command>Apple Macintosh OS, <command>Windows
95/98/NT/2000, <command>OS/2, <command>Sistemas
IBM (MVS, AS/400, etc...), <command>VAX VMS,
<command>Novell Netware, todos os tipos de Unix como o Solaris, HPUX,
AIX, SCO, Sinix, BSD, etc., e todos os outros sistemas operacionais que
suportam o compilador "C++" (quase todos os sistemas operacionais deste
planeta!).



<varlistentry>
<term>C-C++Beautifier-HOWTO
<listitem>

Este documento ajudará a formatar (de forma organizada) os programas C/C++
assim será mais legível e seguirá os padrões de codificação C/C++.  As
informações deste documento se aplica a quase todos os sistemas operacionais do
planeta!



<varlistentry>
<term>DB2-HOWTO
<listitem>

Este documento explica como instalar o DB2 Universal Database versão 7.1 para
<command>GNU/Linux nas seguintes distribuições baseadas no Intel x86:
Caldera Caldera OpenLinux 2.4, Debian, Red Hat Linux 6.2, SuSE Linux 6.2 e 6.3,
e TurboLinux 6.0.  Após instalar o DB2, você pode usar um banco de dados de
exemplo, conectar-se ao servidor DB2 de uma máquina remota e administrar o DB2
usando o DB2 Control Center.



<varlistentry>
<term>Enterprise-Java-for-Linux-HOWTO
<listitem>

Como configurar um ambiente Java Enterprise no <command>GNU/Linux
incluindo o Java Development Kit, um servidor Web, suportando Java servlets,
acessando um banco de dados via JDBC e suportado Enterprise Java Beans (EJBs).



<varlistentry>
<term>GCC-HOWTO
<listitem>

Este documento explica como configurar o compilador GNU C e bibliotecas de
desenvolvimento sob o <command>GNU/Linux e te dá uma visão de
compilação, linkagem, execução e programas de depuração.



<varlistentry>
<term>IngresII-HOWTO
<listitem>

Este documento cobre a instalação do Ingres II Relational Database management
System no <command>GNU/Linux.  Ele cobre a configuração de ambos o
Kit de desenvolvimento e versão completa do Ingres.  Algumas seções explicam
como iniciar o uso do Ingres.



<varlistentry>
<term>Oracle-7-HOWTO
<listitem>

Um guia para instalar e configurar o Servidor do Banco de Dados Oracle em um
sistema <command>GNU/Linux.



<varlistentry>
<term>Oracle-8-HOWTO
<listitem>

Com este HOWTO, é um pouco de sorte, você será capaz de ter o Oracle 8i
Enterprise Edition para GNU/Linux instalado, criar um banco de dados e conectar
a ele através de um computador remoto.  O foco principal deste guia é o RedHat
6.0, no entanto ele pode funcionar em outros distribuições recentes após
algumas modificações.



<varlistentry>
<term>PHP-HOWTO
<listitem>

Ensina como desenvolver programas em PHP e também migrar todas as aplicações
GUI do Windows 95 para o poderoso conjunto PHP + HTML + DHTML + XML + Applets
Java + Javascript.  As explicações descritas neste documento se aplicam a todo
os sistemas operacionais para onde o PHP está portado que são: Linux, Windows
95/98/NT/2000, OS/2, todos os tipos de Unix como o Solaris, HPUX, AIX, SCO,
Sinix, BSD, etc...



<varlistentry>
<term>PostgreSQL-HOWTO
<listitem>

Este documento é um "guia prático" para rapidamente colocar para funcionar um
banco de dados SQL e suas ferramentas de comunicação em um sistema Unix.  Ele
também discute a linguagem padrão Internacional ANSI/ISO SQL e revisa os
méritos/vantagens do SQL Database engine desenvolvido pela Internet ao redor do
mundo em um ambiente de desenvolvimento aberto.  Também como configurar a
próxima geração do banco de dados relacional a objetos SQL "PostgreSQL" em um
sistema Unix que pode ser usado como um Servidor de Aplicativos de banco de
dados ou como um Servidor de banco de dados Web.



<varlistentry>
<term>TclTk-HOWTO
<listitem>

Este documento descreve o uso do Tcl no <command>GNU/Linux, uma
linguagem de scripting.  Ela é uma linguagem interpretada fácil de aprender que
usa pouca digitação para obter um alto nível de programação e desenvolvimento
rápido de aplicativos (RAD).  O Tk toolkit é um ambiente de programação para
criar interfaces gráficas do usuário (GUI) sob o Sistema X Window.  Suas
capacidades incluem a possibilidade de estender e incluir em outros
aplicativos, desenvolvimento rápido e fácil de usar.  Juntos o Tcl e Tk
oferecem muitos benefícios para o desenvolvedor e usuário.  As interfaces
baseadas no Tk tendem a ser mais personalizáveis e dinâmicas que aquelas feitas
de toolkits C ou C++.  O Tk implementa o Visual e Uso do Motif.  Um grande
número de aplicações X interessantes são implementadas completamente em Tk, com
nenhum comandos específicos de aplicativo.



</variablelist>


 userlevel='inter' s43.8.1.9">###Computação Paralela / Clusters
<variablelist>
<varlistentry>
<term>Beowulf-HOWTO
<listitem>

Este documento é uma introdução a arquitetura de Supercomputador Beowulf e
oferece informações sobre programação paralela, incluindo links para documentos
mais específicos e páginas internet.



<varlistentry>
<term>Cluster-HOWTO
<listitem>

Como configurar clusters de computador GNU/Linux de alta performance.



<varlistentry>
<term>Parallel-Processing-HOWTO
<listitem>

O Processamento Paralelo é uma forma de acelerar a execução de um programa
dividindo o programa em múltiplos fragmentos que podem ser executados
simultaneamente, cada um em seu próprio processador.  Um programa sendo
executado em N processadores pode ser executado N vezes mais rápido que seria
usando somente um processador.  Este documento discute os quatro métodos para
realizar processamento paralelo que estão disponíveis aos usuários do sistema
operacional GNU/Linux: Sistemas Linux SMP, Sistemas Linux em Clusters de rede,
execução paralela usando as instruções multimídia do processador (i.e.  MMX) e
processadores (paralelos) conectados no sistema <command>GNU/Linux.



<varlistentry>
<term>SMP-HOWTO
<listitem>

Este HOWTO revisa principais assuntos (e eu espero que soluções) relacionadas
com as configurações SMP sob o <command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.1.10">###Configuração de Teclado / Vídeo / Console
<variablelist>
<varlistentry>
<term>Font-HOWTO
<listitem>

Como usar e configurar corretamente tipos de fontes no ambiente GNU/Linux.



<varlistentry>
<term>Framebuffer-HOWTO
<listitem>

Descreve como utilizar dispositivos framebuffer no <command>GNU/Linux
com uma variedade de plataformas.  Isto também inclui como ajustar telas
multi-headed.



<varlistentry>
<term>Keyboard-and-Console-HOWTO
<listitem>

Este documento contém algumas informações sobre o teclado e console no
<command>GNU/Linux, e o uso de caracteres não-ASCII.  Ele descreve o
<command>GNU/Linux 2.0.



<varlistentry>
<term>Text-Terminal-HOWTO
<listitem>

Explica o que são os terminais texto, como funcionam, como instalar e
configura-los e oferece muitos detalhes de como conserta-los.  Se não tiver um
manual do terminal, poderá ser de grande ajuda.  Enquanto é escrito para
terminais reais no sistema <command>GNU/Linux alguns deles também são
aplicáveis a emulação de terminal e pode ser útil para sistemas não Linux.



<varlistentry>
<term>Unicode-HOWTO
<listitem>

Explica como alterar seu sistema <command>GNU/Linux para utilizar a
codificação de texto baseada no UTF-8.  -



</variablelist>


 userlevel='inter' s43.8.1.11">###Ambiente Gráfico
<variablelist>
<varlistentry>
<term>MGR-HOWTO
<listitem>

O MGR (ManaGeR) é um sistema de janelas gráfico.  O servidor MGR oferece um
gerenciador de janelas embutido e emulação de terminal gráfico em janela em
monitor colorido ou monocromático.  O MGR é controlado por menus pop-up, por
interação do teclado e por seqüencias de escapa escrita em pseudo-terminais
pelo software cliente.



<varlistentry>
<term>XFree86-HOWTO
<listitem>

Este documento descreve como obter, instalar e configurar a versão 4.0 do
XFree86 do X Window System (X11R6) para sistemas <command>GNU/Linux.
Ele é um guia passo a passo para configurar o XFree86 em seu sistema.



<varlistentry>
<term>XFree86-Touch-Screen-HOWTO
<listitem>

Descreve como configurar um dispositivo de entrada touch screen sob o XFree86.



<varlistentry>
<term>XFree86-Video-Timings-HOWTO
<listitem>

Como configurar os modos de vídeo de sua placa/monitor sob o XFree86.



<varlistentry>
<term>XWindow-User-HOWTO
<listitem>

Este documento contém detalhes sobre a configuração do ambiente X Windows para
o usuário <command>GNU/Linux, também como o administrador de sistemas
iniciantes tentando aprender os mais diversos tipos de opções de configuração e
detalhes do X Window.  É assumido um conhecimento básico de configurações de
software e instalação.



<varlistentry>
<term>Xinerama-HOWTO
<listitem>

Este documento descreve como configurar o XFree86 versão 4.0 com monitores
multimídia com as extensões Xinerama.



</variablelist>


 userlevel='inter' s43.8.1.12">###Suporte ao Sistema / Grupos de Usuários / Listas de Discussão
<variablelist>
<varlistentry>
<term>Consultants-HOWTO
<listitem>

Contém uma lista de empresas e consultores oferecendo suporte comercial
relacionado ao sistema <command>GNU/Linux.



<varlistentry>
<term>Online-Troubleshooting-HOWTO
<listitem>

Este documento direciona usuários <command>GNU/Linux a lugares
disponíveis na Internet que oferecem acesso a uma vasta quantidade de
documentos úteis relacionados ao sistema em situações de problema.



<varlistentry>
<term>User-Group-HOWTO
<listitem>

Este documento descreve como fundar, manter e organizar um grupo de usuários
<command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.1.13">###Migração / Convivência com Outras Plataformas
<variablelist>
<varlistentry>
<term>DOS-Win-to-Linux-HOWTO
<listitem>

Este documento tem a intenção de ajudar o leitor traduzir seu conhecimento do
DOS e Windows para o ambiente <command>GNU/Linux, também como
oferecer dicas de manipulação de arquivos e utilização de recursos entre os
dois sistemas.



<varlistentry>
<term>VMS-to-Linux-HOWTO
<listitem>

Este documento é escrito para todos aqueles que tem usado o VMS e agora
precisam migrar para o <command>GNU/Linux um clone gratuito do
<command>UNIX.  A transição é feita (felizmente) através de uma
comparação passo a passo de comandos e ferramentas existentes.



</variablelist>


 userlevel='inter' s43.8.1.14">###Tarefas Específicas
<variablelist>
<varlistentry>
<term>Astronomy-HOWTO
<listitem>

Este documento compartilha dicas e recursos para utilizar soluções do
<command>GNU/Linux no mundo da Astronomia.



<varlistentry>
<term>CD-Writing-HOWTO
<listitem>

Este documento explica como gravar CD-ROMs sob o <command>GNU/Linux.



<varlistentry>
<term>CDROM-HOWTO
<listitem>

Este documento descreve como instalar, configurar e usar uma unidade de CD-ROM
sob o <command>GNU/Linux.  Ele lista hardwares suportados e responde
a um número de questões freqüêntes.



<varlistentry>
<term>CVS-RCS-HOWTO
<listitem>

Este documento é um **guia prático** para rapidamente
configurar o sistema de controle do código fonte CVS/RCS.  Este documento
também possui shell scripts personalizados que são trocados no topo do CVS.
Estes scripts oferecem uma interface fácil entre o usuário e o CVS.



<varlistentry>
<term>DVD-Playing-HOWTO
<listitem>

Uma explicação fácil de seguir de como obter seu DVD funcionando no
<command>GNU/Linux.



<varlistentry>
<term>Diskless-HOWTO
<listitem>

Este documento descreve como configurar uma máquina sem disco rígido no
<command>GNU/Linux.



<varlistentry>
<term>Java-Decompiler-HOWTO
<listitem>

Este documento te ajudará a descompilar programas class feitos em Java.  Este
documento contém uma lista de descompiladores que podem reverter o engineer os
arquivos Java class e gerar arquivos de código fonte Java.  Isto é muito útil
se você não tem o arquivo com o código fonte Java.



<varlistentry>
<term>JavaStation-HOWTO
<listitem>

Este HOWTO descreve como ativar o SO GNU/Linux no NC Sun Java Station.



<varlistentry>
<term>KickStart-HOWTO
<listitem>

Este documento descreve como usar o sistema Linux RedHat para instalar
rapidamente o sistema em um grande número de máquinas
<command>GNU/Linux.



<varlistentry>
<term>Kiosk-HOWTO
<listitem>

Este documento oferece um guia para ajustar um kiosk baseado em WWW usando o
<command>GNU/Linux, X11R6, FVWM2, Netscape Navigator 4.X e um
trackball customizado.



<varlistentry>
<term>Linux-From-Scratch-HOWTO
<listitem>

Este documento descreve o processo de criar seu próprio sistema
<command>GNU/Linux do nada através de uma distribuição já instalada,
usando nada mais que o código fonte dos softwares que precisamos.



<varlistentry>
<term>MP3-HOWTO
<listitem>

Este documento descreve o hardware, software e processos necessários, para
encodificar, tocar, mixar e decodificar arquivos de som MP3 sob o
<command>GNU/Linux.



<varlistentry>
<term>Majordomo-MajorCool-HOWTO
<listitem>

Este documento tem a intenção de guiar o usuário através do software de
gerenciamento de listas de discussão Majordomo e MajorCool.  O MajorCool é um
utilitário para gerenciar listas Majordomo via script CGI; muitas pessoas que
não estão familiar com o Majordomo baseado em modo texto podem preferir uma
interface mais amigável via web do MajorCool.



<varlistentry>
<term>Mutt-GnuPG-PGP-HOWTO
<listitem>

Este documento explica como configurar rapidamente o Mutt-i, PGP e GnuPG em
suas diferentes versões (2.6.x, 5.x e GnuPG), nada dos problemas que podem
ocorrer enquanto envia e-mails criptografados e assinados para ser lidos por
clientes de e-mail que não são compatíveis com PGP/MIME como definido na RFC
2015 e em outros sistemas operacionais.



<varlistentry>
<term>NC-HOWTO
<listitem>

Este documento tenta descrever como colocar uma Netstation da IBM em sua rede
local usando um computador <command>GNU/Linux como servidor.



<varlistentry>
<term>NCD-HOWTO
<listitem>

Este documento tenta descreve como colocar uma ThinSTAR NCD em sua rede local
usando um computador <command>GNU/Linux como servidor.



<varlistentry>
<term>PalmOS-HOWTO
<listitem>

Este documento explica como usar seu dispositivo Palm OS com um sistema
<command>GNU/Linux.  Este HOWTO não aborda somente o sistema
operacional <command>GNU/Linux.



<varlistentry>
<term>Printing-HOWTO
<listitem>

Este é o Printing HOWTO do <command>GNU/Linux, uma coleção de
informações sobre como gerar, ver, imprimir e enviar fax de tudo sob o
<command>GNU/Linux (e outros UNIXes em geral).



<varlistentry>
<term>Printing-Usage-HOWTO
<listitem>

Descreve como usar o sistema de spooling oferecido pelo sistema operacional
<command>GNU/Linux.  Este HOWTO é um documento suplementar ao Linux
Printing Setup, que discute a instalação e configuração do sistema de impressão
do <command>GNU/Linux.



<varlistentry>
<term>Psion-HOWTO
<listitem>

Este documento descreve como usar Palmtops Psion com o
<command>GNU/Linux, mas não cobre a execução do Linux no Palmtop
Psion.  Veja o projeto **Linux 7k** em ("http://www.w3.org/1999/xlink) [](http://www.calcaria.net">http://www.calcaria.net.



<varlistentry>
<term>Quake-HOWTO
<listitem>

Este documento explica como instalar, executar e corrigir problemas no Quake,
QuakeWorld e Quake II em um sistema <command>GNU/Linux Intel.



<varlistentry>
<term>RedHat-CD-HOWTO
<listitem>

Descreve como fazer seus próprios CDs da distribuição Red Hat, a estrutura da
distribuição e também como incluir RPMs atualizados na distribuição.



<varlistentry>
<term>Sound-HOWTO
<listitem>

Este documento descreve o suporte ao som no <command>GNU/Linux,
arquiteturas de som suportadas e como incluir o suporte ao som no kernel.  Este
documento também responde algumas questões freqüêntes sobre o suporte ao som no
<command>GNU/Linux.



<varlistentry>
<term>Sound-Playing-HOWTO
<listitem>

Este documento lista aplicativos que podem tocar vários formatos de sons no
<command>GNU/Linux.



<varlistentry>
<term>VME-HOWTO
<listitem>

Este documento mostra como executar o <command>GNU/Linux em seu
Pentium VMEbus e outros barramentos PCI baseados no design de processador
VMEbus.



</variablelist>


 userlevel='inter' s43.8.1.15">###Rede / Administração / Firewall / Proxy / Segurança
<variablelist>
<varlistentry>
<term>AX25-HOWTO
<listitem>

Talvez o <command>GNU/Linux seja o único sistema operacional no mundo
que possui suporte nativo e padrão ao protocolo de pacotes de rádio AX.25 usado
por Operadores de Rádio Amador ao redor do mundo.  Este documento explica como
instalar e configurar este suporte.



<varlistentry>
<term>Adv-Routing-HOWTO
<listitem>

Roteamento avançado.  Explicações sobre o <command>iproute2,
<command>traffic shaper e <command>netfilter.



<varlistentry>
<term>Bandwidth-Limiting-HOWTO
<listitem>

Descreve como configurar o servidor Linux para limitar banda.



<varlistentry>
<term>BRIDGE-STP-HOWTO
<listitem>

Este documento explica o que é uma ponte entre redes e como criar uma
utilizando o Spanning Tree Protocol (STP).  Este é um método de manter os
dispositivos Ethernet conectados e funcionando em múltiplos caminhos.  Os
participantes negociam a troca através do caminho mais curto através do STP.



<varlistentry>
<term>Cable-Modem
<listitem>

Fornece instruções de como usar o Linux para se conectar a um provedor de Cable
modem.



<varlistentry>
<term>Chroot-BIND8-HOWTO
<listitem>

Este documento descreve a instalação do servidor de nomes BIND 8 para ser
executado em uma jaula chroot e como um usuário não-root, para oferecer
segurança adicional e minimizar efeitos potenciais que podem comprometer a
segurança.



<varlistentry>
<term>Cyrus-IMAP
<listitem>

Um guia compreensivo para a instalação, configuração e execução do
<command>Cyrus Imap e <command>Cyrus SASL.



<varlistentry>
<term>DNS-HOWTO
<listitem>

Como configurar seu servidor DNS em pouco tempo.



<varlistentry>
<term>Diald-HOWTO
<listitem>

Este documento mostra alguns cenários típicos para iniciar o uso do
<command>Diald facilmente.  Este cenários incluem uma conexão de um
computador local a um provedor usando o PPP através de um modem sem usar o
pon/poff ou ppp-pon/ppp-off para um servidor proxy/firewall com diferentes
conexões Internet através de vários provedores.



<varlistentry>
<term>Diskless-root-NFS-HOWTO
<listitem>

Explica como configurar um servidor e clientes para operação sem disco através
de uma rede.



<varlistentry>
<term>DSL-HOWTO
<listitem>

Este documento examina a família DSL de serviços Internet de alta velocidade.
Descreve como instalar, configurar depurar.



<varlistentry>
<term>Ethernet-HOWTO
<listitem>

Este documento é uma coleção de dados sobre dispositivos Ethernet que podem ser
usados no <command>GNU/Linux e como configura-los.  Note que este
HOWTO está focalizado no hardware e aspectos de baixo nível de controladores
das placas ethernet e não cobre assuntos de software como os programas
<command>ifconfig e <command>route (veja o Network-HOWTO se
procura por estes materiais).



<varlistentry>
<term>Firewall-HOWTO
<listitem>

Descreve os sistemas básicos de firewall e alguns detalhes de como ajustar
firewalls proxy e de filtragem de pacotes em sistemas baseados no
<command>GNU/Linux.



<varlistentry>
<term>IP-Masquerade-HOWTO
<listitem>

Este documento descreve como ativar a característica IP Masquerade no
<command>GNU/Linux.  O IP Masquerade é uma forma do Network Address
Translation ou NAT que permite que computadores conectados internamente que não
tem um ou mais endereços Internet registrados ter a habilidade de se comunicar
com a Internet via uma única máquina <command>GNU/Linux com um único
endereço IP.



<varlistentry>
<term>IPCHAINS-HOWTO
<listitem>

Descreve como obter, instalar e configurar o programa avançado de firewall para
o <command>GNU/Linux e algumas idéia de como usa-lo.



<varlistentry>
<term>IPX-HOWTO
<listitem>

Descreve como obter, instalar e configurar as várias ferramentas disponíveis
para o sistema operacional <command>GNU/Linux para utilizar o suporte
do protocolo IPX no kernel do <command>GNU/Linux.



<varlistentry>
<term>Infrared-HOWTO
<listitem>

Uma introdução ao <command>GNU/Linux e dispositivos infra-vermelho e
como usar programas oferecidos pelo projeto Linux/IrDA.



<varlistentry>
<term>ISP-Hookup-HOWTO
<listitem>

Descreve como usar o <command>GNU/Linux para conectar a um Provedor
Internet via modem dial-up via conexão TCP/IP.  Também como o procedimento de
discagem inicial e estabelecimento de IP, recebimento de email e news.



<varlistentry>
<term>ISP-Setup-RedHat-HOWTO
<listitem>

Descreve como configurar serviços de ISP no Red Hat.  Domínios, virtual hosts,
pop3 e emails.



<varlistentry>
<term>Intranet-Server-HOWTO
<listitem>

Este documento descreve como configurar uma Intranet usando o
<command>GNU/Linux como um servidor que se comunica com Unix,
Netware, NT e Windows.



<varlistentry>
<term>Java-CGI-HOWTO
<listitem>

Este documento explica como configurar seu servidor para permitir programas CGI
escritos em Java e como usar Java para escrever programas CGI.



<varlistentry>
<term>LDAP-HOWTO
<listitem>

Informações sobre a instalação, configuração, execução e manutenção de um
Servidor LDAP (Lightweight Directory Access Protocol) em uma máquina
<command>GNU/Linux é descrita neste documento.  Existe também
detalhes sobre como criar bancos de dados LDAP, como atualizar e apagar
informações no banco de dados, como implementar roaming access e como usar o
Livro de Endereços do Netscape.



<varlistentry>
<term>LDAP-Implementation-HOWTO
<listitem>

Descreve aspectos técnicos de armazenamento de dados de aplicações em um
servidor LDAP.



<varlistentry>
<term>Mail-Administrator-HOWTO
<listitem>

Este documento descreve a configuração e uso do Correio Eletrônico (E-mail) sob
o <command>GNU/Linux.  É primariamente mais indicado para
administradores do que usuários.



<varlistentry>
<term>Mail-User-HOWTO
<listitem>

Este documento é uma introdução ao mundo do Correio Eletrônico sob o
<command>GNU/Linux



<varlistentry>
<term>Masquerading-Simple-HOWTO
<listitem>

Descreve de forma prática como conectar diversas máquinas de sua rede Interna a
Internet.



<varlistentry>
<term>MindTerm-SSH-HOWTO
<listitem>

Este documento descreve como usar o SSH o programa MindTerm baseado em Java
para criar de forma rápida, segura e confiável uma VPN sobre redes inseguras.



<varlistentry>
<term>Multicast-HOWTO
<listitem>

Este HOWTO tenta cobrir muitos aspectos relacionados com o multicast sobre
redes TCP/IP.  Assim, muitas informações que não são específicas do sistema
Linux (apenas no caso de não usar o GNU/Linux...  ainda).



<varlistentry>
<term>NFS-HOWTO
<listitem>

Como configurar servidores e clientes NFS&gt;



<varlistentry>
<term>NetMeeting-HOWTO
<listitem>

Descreve como fazer o Microsoft NetMeeting se integrar com o Linux.



<varlistentry>
<term>NIS-HOWTO
<listitem>

Este documento descreve como configurar o <command>GNU/Linux como um
cliente NIS (YS) ou NIS+ e como instala-lo como um servidor NIS.



<varlistentry>
<term>Network-boot-HOWTO
<listitem>

Descreve como configurar um servidor Linux para permitir que estações sem disco
rígido façam boot via rede e iniciem o sistema Linux (é uma regravação parcial
do Diskless-howto).



<varlistentry>
<term>Net-HOWTO
<listitem>

Este documento cobre as área de software e tecnologias de rede no
<command>GNU/Linux.



<varlistentry>
<term>Networking-Overview-HOWTO
<listitem>

O propósito deste documento é lhe oferecer uma visão das capacidades de rede do
sistema operacional <command>GNU/Linux e oferecer ponteiros para
outros documentos e detalhes de implementação.



<varlistentry>
<term>PPP-HOWTO
<listitem>

Este documento mostra como conectar seu PC <command>GNU/Linux a um
servidor PPP (Protocolo Ponto a Ponto), como usar o PPP para ligar duas redes e
oferece um método de configurar seu computador <command>GNU/Linux
como um servidor PPP.  Este documento também oferece ajuda na solução de
problemas relacionados com o PPP.



<varlistentry>
<term>Qmail-VMailMgr-Courier-imap-HOWTO
<listitem>

Este documento é sobre a construção de um servidor de e-mail que suportará
hospedagem de domínios dinâmicos e oferecerá os serviços smtp, pop3 e imap,
usando uma poderosa alternativa ao sendmail.



<varlistentry>
<term>Remote-Serial-Console-HOWTO
<listitem>

A porta RS232 permite que o Linux ser controlado de um terminal ou modem
conectado a uma porta serial assíncrona.  Este documento descreve como
configurar o Linux para se conectar ao console serial.



<varlistentry>
<term>Sat-HOWTO
<listitem>

Descreve base e referências sober a tecnologia SAP, as características de larga
banda para download, etc.



<varlistentry>
<term>Serial-Laplink-HOWTO
<listitem>

Descreve como criar uma conexão serial entre dois computadores para
compartilhamento de dados.  Este permite também efetuar conexões seriais entre
outros tipos de sistemas operacionais como Windows 9X, NT.



<varlistentry>
<term>SMB-HOWTO
<listitem>

Este é o HOWTO SMB.  Ele descreve como usar o protocolo Server Message Block
(SMB), também chamado de Session Message Block, NetBIOS ou protocolo
LanManager, com o <command>GNU/Linux e usando o Samba.



<varlistentry>
<term>Securing-Domain-HOWTO
<listitem>

Este documento descreve as coisas que provavelmente deve fazer quando desejar
configurar uma rede de computadores sob seu próprio domínio.  Ele cobre a
configuração de parâmetros de rede, serviços de rede e configurações de
segurança.



<varlistentry>
<term>Security-HOWTO
<listitem>

Este documento é uma visão geral dos assuntos de segurança que enfrente o
administrador de sistemas <command>GNU/Linux Ele cobre a filosofia
geral de segurança e um número de exemplos específicos de como melhorar a
segurança de seu sistema <command>GNU/Linux Também estão incluídos
ponteiros para materiais relacionados com programas e segurança.



<varlistentry>
<term>Shadow-Password-HOWTO
<listitem>

Este documento tenta descrever como obter, instalar e configurar o Linux
password Shadow Suite.  Também discute como obter e reinstalar outros softwares
e daemons de rede que requerem acesso as senhas do usuário.



<varlistentry>
<term>SSL-RedHat-HOWTO
<listitem>

Fornece referências sobre como o PKI e SSL funcionam juntos



<varlistentry>
<term>Tango-HOWTO
<listitem>

Descreve a instalação, configuração e correção de problemas básicos do
Pervasive Software's Tango Application Server no Sun Solaris e vários sabores
de <command>GNU/Linux.



<varlistentry>
<term>Thinclient-HOWTO
<listitem>

Como converter computadores comuns em rápidos terminais usando o poder de seu
computador principal, você precisará de: Um computador rápido para atuar como
servidor, um computador cliente (antigo e não desejado).  Placas de rede
compatíveis com o <command>GNU/Linux.  Uma conexão entre os
computadores.  Como centralizar a administração do sistema usando o NFS (i.e.
colocando todo o sistema de arquivos de um cliente rápido no servidor).



<varlistentry>
<term>UUCP-HOWTO
<listitem>

Este documento descreve a configuração do UUCP sob o
<command>GNU/Linux.  Você deve ler este documento se planejar
conectar a sites remotos via UUCP via modem, conexão direta ou via Internet.
Provavelmente não precisará ler este documento se não souber o que é UUCP ou se
seu computador não possuir este suporte.



<varlistentry>
<term>VMailMgr-HOWTO
<listitem>

Explica como configurar o suporte ao VMailMgr serviços de domínio virtual pop3
em conjunto com o Qmail.



<varlistentry>
<term>VoIP-HOWTO
<listitem>

Ensina como configurar o sistema Linux para comunicação via voz usando a
Internet.  Descreve protocolos e métodos para transmissão de voz aproveitando
recursos de redes de baixa velocidade.



<varlistentry>
<term>VPN-HOWTO
<listitem>

Descreve como configurar uma Virtual Private Network com o
<command>GNU/Linux.



<varlistentry>
<term>VPN-Masquerade-HOWTO
<listitem>

Descreve como configurar um Firewall <command>GNU/Linux para o
masquerade em tráfego baseado no IPsec- e PPTP Virtual Private Network Traffic,
permitindo estabelecer uma conexão VPN sem perder a segurança e flexibilidade
de sua conexão Internet com o firewall <command>GNU/Linux e
permitindo fazer um servidor VPN disponível que não possui um endereço IP
registrado na Internet.  Também estão incluídos detalhes de como configurar um
cliente e servidor VPN.



<varlistentry>
<term>Virtual-Services-HOWTO
<listitem>

Este documento fala sobre tudo que precisa saber para virtualizar um serviço.



<varlistentry>
<term>Windows-LAN-Server-HOWTO
<listitem>

Ajuda na configuração do Linux em ambientes onde existiam primariamente
máquinas executando o Windows 9x.



<varlistentry>
<term>Wireless-HOWTO
<listitem>

Explica como como configurar uma rede sem fio em ambiente Linux, limitações,
requerimentos, etc.



<varlistentry>
<term>WWW-HOWTO
<listitem>

Explica como configurar serviços WWW sob o <command>GNU/Linux (ambos
cliente e servidor).  Ele não tenta ser um manual detalhada mas uma visão e um
bom ponto de referência.



<varlistentry>
<term>WWW-mSQL-HOWTO
<listitem>

Descreve como construir um banco de dados cliente/servidor usando a WWW e HTML
para a interface com o usuário.



<varlistentry>
<term>phhttpd-HOWTO
<listitem>

O phttpd é um acelerador HTTP.  Ele serve uma rápida requisição estática HTTP
através de um sistema de arquivos locai e passa as requisições menos dinâmicas
para um servidor de espera.  Suas características são uma compreensão do I/O e
um cache de conteúdo agressivo que o ajuda a fazer um trabalho eficiente.



</variablelist>


 userlevel='inter' s43.8.1.16">###Outros
<variablelist>
<varlistentry>
<term>Benchmarking-HOWTO
<listitem>

Este documento discute assuntos relacionados ao desempenho dos sistemas Linux e
recomenda algumas ferramentas para medida do desempenho do sistema.



<varlistentry>
<term>DOSEMU-HOWTO
<listitem>

Ensina como utilizar, configurar o emulador do ambiente DOS para Linux.



<varlistentry>
<term>Ecology-HOWTO
<listitem>

Este documento discute métodos de como os computadores com o
<command>GNU/Linux podem ser usados para proteger nosso ambiente,
usando características como economia de energia ou papel.  Como ele não requer
grandes requerimentos de hardware, o <command>GNU/Linux pode ser
usado com computadores antigos e tornar seu ciclo de vida longo.  Os jogos
podem ser usados em ambientes educativos e estão disponíveis programas para
simular os processos ecológicos.



<varlistentry>
<term>Process-Monitor-HOWTO
<listitem>

Este documento descreve como monitorar os processos (programas) no
<command>Linux/Unix e como reinicia-los automaticamente se eles são
destruídos sem intervenção manual.  Este documento também tem URLs para FAQs
sobre "Processos no Unix".



<varlistentry>
<term>VAR-HOWTO
<listitem>

Contém uma lista de empresas de serviço que não fabricam hardwares ou criam
pacotes de softwares, mas incluem valores ao produtos existentes.



</variablelist>




 userlevel='inter' ajuda-howto-listagem-m">###Listagem de Mini-HOWTO's

Segue abaixo uma listagem de Mini-HOWTO's do projeto LDP organizados por
sub-seções com a descrição do assunto que cada um deles aborda.


 userlevel='inter' s43.8.2.1">###Introdução ao Sistema / Instalação / Configuração / Kernel
<variablelist>
<varlistentry>
<term>Alsa-sound
<listitem>

Descreve a instalação dos controladores de som ALSA para Linux.  Estes
controladores de som podem ser usados em substituição aos controladores de com
regular, como são totalmente compatíveis.



<varlistentry>
<term>Install-From-ZIP
<listitem>

Descreve como instalar o <command>GNU/Linux através de um zip drive
conectado a porta paralela usando a distribuição Slackware do
<command>GNU/Linux.



<varlistentry>
<term>Install-Strategies
<listitem>

Descreve algumas formas de instalação para aqueles que tem a intenção de fazer
dual boot entre o Linux e Windows.



<varlistentry>
<term>Lego
<listitem>

Mostra soluções em software livre para utilização com os kits de robótica da
The Lego Group's Mindstorm Robotics Invention System (RIS).



<varlistentry>
<term>Kerneld
<listitem>

Explica como configurar e utilizar o daemon kerneld.



<varlistentry>
<term>Loadlin+Win95
<listitem>

Este documento descreve como usar o Loadlin com o Windows 95 para inicializar o
<command>GNU/Linux.



<varlistentry>
<term>Modules
<listitem>

Explica como incluir seu suporte no kernel, configurar e utilizar módulos no
<command>GNU/Linux.



<varlistentry>
<term>Path
<listitem>

Descreve truques comuns e problemas com as variáveis de ambiente no
<command>GNU/Linux/<command>Unix, especialmente a variável
PATH.  PATH é uma lista de diretórios onde os comandos são pesquisados.  Os
detalhes se aplicam a distribuição <command>Debian 1.3.



<varlistentry>
<term>Pre-Installation-Checklist
<listitem>

Você é um novato no Linux?  Você é um guru no Linux?  Em ambos os casos esta
checklist será de grande ajuda para você.  Quantas vezes você se encontrou com
problemas no meio de um processo de instalação do <command>GNU/Linux
porque algum detalhe vital sobre o hardware alvo não é conhecido?



<varlistentry>
<term>Post-Installation-Checklist
<listitem>

Lembra alguns passos que devem ser verificados logo após a instalação de um
novo sistema Linux.



<varlistentry>
<term>RPM+Slackware
<listitem>

Este documento descreve como ter o RPM instalado e funcionando corretamente sob
o Slackware.



<varlistentry>
<term>Update
<listitem>

Descreve como se manter atualizado sobre o desenvolvimento no mundo
<command>GNU/Linux.



<varlistentry>
<term>Upgrade
<listitem>

Dicas e truques de como atualizar de uma distribuição
<command>GNU/Linux para outra.



<varlistentry>
<term>VAIO+Linux
<listitem>

Explica a instalação do <command>GNU/Linux em computadores Sony VAIO.



</variablelist>


 userlevel='inter' s43.8.2.2">###Discos / Sistema de Arquivos / Desempenho
<variablelist>
<varlistentry>
<term>Automount
<listitem>

Descreve a montagem automática de sistemas de arquivos autofs, como
configura-lo e alguns problemas que devem ser evitados.



<varlistentry>
<term>Ext2fs-Undeletion
<listitem>

Imagina isto: Você passou os últimos três dias sem dormir, sem comer.  Sua
compulsão hacker foi paga: você finalizou aquele programa que lhe dará fama e
reconhecimento.  Todo o que você precisa fazer é coloca-lo no Metalab.  Oh, e
apagar aqueles arquivos de backup do Emacs.  Assim você fadigado digita
<literal>rm * ~..  E bem mais tarde você notou o espaço extra naquele
comando.  Você simplesmente apagou todo o seu trabalho!  Mas a ajuda está na
mão.  Este documento oferece uma discussão de como recuperar arquivos apagados
através do Second Extend File System (EXT2).  Talvez, você será capaz de lançar
aquele programa depois disso...



<varlistentry>
<term>Ext2fs-Undeletion-Dir-Struct
<listitem>

Fornece um complemento ao ext2-undeletion-howto e descreve formas de recuperar
estrutura de diretórios de forma segura.



<varlistentry>
<term>Hard-Disk-Upgrade
<listitem>

Como copiar um sistema <command>GNU/Linux de um disco para outro.



<varlistentry>
<term>Loopback-Root-FS
<listitem>

Este documento explica como usar o dispositivo de loopback do Linux para criar
um formato nativo de sistema de arquivos através de uma partição DOS sem
reparticionamento.



<varlistentry>
<term>Partition-Rescue-mini-HOWTO
<listitem>

Como recuperar uma partição pelo <command>GNU/Linux.



<varlistentry>
<term>Quota
<listitem>

Descreve como ativar a quota nos sistemas de arquivos para usuários e grupos de
uma máquina <command>GNU/Linux.



<varlistentry>
<term>Swap-Space
<listitem>

Descreve como compartilhar sua partição swap do <command>GNU/Linux
com o Windows.



<varlistentry>
<term>Ultra-DMA
<listitem>

Explica como usar Ultra-DMA como discos rígidos e interfaces Ultra ATA, Ultra
33 e Ultra66 com o <command>GNU/Linux.



<varlistentry>
<term>ZIP-Drive
<listitem>

Este documente oferece uma referência rápida para a configuração e uso da
unidade de ZIP drive Iomega com o <command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.2.3">###Escrita de Documentação / Editores
<variablelist>
<varlistentry>
<term>DocBook-Install
<listitem>

Descreve de forma rápida e prática como ajustar novatos a ter de forma rápida o
DocBook instalado para processamento de arquivos SGML em HTML.



<varlistentry>
<term>Howtos-with-LinuxDoc
<listitem>

Descreve como escrever documentos HOWTOs usando o LinuxDoc (referência para
iniciantes).



<varlistentry>
<term>Man-Page
<listitem>

Descreve o que deve ter em mente quando estiver escrevendo documentação on-line
-- também chamada de página de manual (man page).



</variablelist>


 userlevel='inter' s43.8.2.4">###Hardware
<variablelist>
<varlistentry>
<term>3-Button-Mouse
<listitem>

Como ter um mouse serial de 3 botões funcionando no
<command>GNU/Linux.



<varlistentry>
<term>ACP-Modem
<listitem>

Descreve como configurar e utilizar a característica ACP (Mwave) de máquinas
IBM, como o IBM Thinkpad.



<varlistentry>
<term>BTTV-Mini-HOWTO-0.3
<listitem>

Este documento descreve o hardware, software e procedimentos necessários para
se usar um chipset baseado no bt8x8 frame grabber ou placa sintonizadora de TV
sob o <command>GNU/Linux.



<varlistentry>
<term>Boca
<listitem>

Instalando uma placa serial Boca 16-portas (Boca 2016) no
<command>GNU/Linux.



<varlistentry>
<term>GTEK-BBS-550
<listitem>

Ensina como configurar a placa serial de 8 portas GTEK's BBS-550 com 16C550
UARTS.  Somente uma IRQ pode ser usada para todas 8 portas.  Ele não requer
qualquer controlador no <command>GNU/Linux no entanto o kernel
precisa ter o suporte a portas seriais.



<varlistentry>
<term>Handspring-Visor
<listitem>

Usando o Visor com o <command>GNU/Linux e sua porta USB.



<varlistentry>
<term>IO-Port-Programming
<listitem>

Este documento descreve a programação de portas I/O de hardware.



</variablelist>


 userlevel='inter' s43.8.2.5">###Software
<variablelist>
<varlistentry>
<term>ADSM-Backup
<listitem>

Descreve como instalar e usar um cliente para o sistema de backup comercial
ADSM para Linux Intel.



<varlistentry>
<term>Bzip2
<listitem>

Explica como usar o programa de compactação <command>bzip2.



<varlistentry>
<term>GIS-GRASS
<listitem>

Este documento descreve como adquirir, instalar e configurar o poderoso sistema
de informações científicas e geográficas de domínio público (GIS): o Geographic
Resources Analysis Support System (GRASS).



<varlistentry>
<term>LILO
<listitem>

O <command>LILO é o gerenciador de inicialização mais usado na
plataforma Intel do Linux.  Este documento descreve alguns tipos de instalações
do LILO.



</variablelist>


 userlevel='inter' s43.8.2.6">###Plataformas não Intel (x86)
<variablelist>
<varlistentry>
<term>Mac-Terminal
<listitem>

Descreve o 1,002nd uso para um Macintosh (grin) morto: como configurar o Mac
para uso como um terminal <command>GNU/Linux.



</variablelist>


 s43.8.2.7">###Programação / Compiladores / Banco de Dados
<variablelist>
<varlistentry>
<term>Programming-Languages
<listitem>

Uma breve comparação das maiores linguagens de programação para o
<command>GNU/Linux e maiores bibliotecas para para criação de
interfaces gráficas com o usuário (GUIs) sob o <command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.2.8">###Configuração de Teclado / Video / Console
<variablelist>
<varlistentry>
<term>Intkeyb
<listitem>

Mini-Howto experimental para o <command>GNU/Linux para a configuração
de teclados.



</variablelist>


 userlevel='inter' s43.8.2.9">###Ambiente Gráfico
<variablelist>
<varlistentry>
<term>3D-Modelling
<listitem>

Oferece detalhes sobre instruções de instalação de um ambiente desktop de
renderização e modelamento usando o RedHat Linux.



<varlistentry>
<term>FDU
<listitem>

Como corrigir fontes feias e ilegíveis no X.



<varlistentry>
<term>LBX
<listitem>

O LBX (Low Bandwidth X) é uma extensão do servidor X que realiza compressão no
protocolo X.  Isto significa que pode ser usado em conjunto com aplicativos X e
um servidor X que estão separados através de uma conexão de rede de baixa
velocidade, para aumentar o tempo de resposta.



<varlistentry>
<term>Nvidia-OpenGL-Configuration
<listitem>

Ensina como instalar os drivers OpenGL para a placa de vídeo Nvidia.



<varlistentry>
<term>Remote-X-Apps
<listitem>

Descreve como executar aplicativos X remotos.



<varlistentry>
<term>TT-XFree86
<listitem>

Ensina como usar fontes true type com o XFree 4.0.x



<varlistentry>
<term>XDM-Xterm
<listitem>

Ensina como utilizar o XDM para gerenciar terminais X.  Uma referência completa
do assunto pode ser encontrada no Thin-client HOWTO.



<varlistentry>
<term>XFree86-Second-Mouse
<listitem>

Instruções de como usar um segundo mouse no X.



<varlistentry>
<term>X-Big-Cursor
<listitem>

Descreve como usar cursores grandes no X.



<varlistentry>
<term>XFree86-XInside
<listitem>

Como converte um modeline XFree86 em um XInside/XiGraphics.



<varlistentry>
<term>Xterm-Title
<listitem>

Explica como usar seqüências de escape para alterar dinamicamente os títulos e
ícones de janelas de um xterm.



</variablelist>


 userlevel='inter' s43.8.2.10">###Migração/Convivência com outras plataformas
<variablelist>
<varlistentry>
<term>Linux+DOS+Win95+OS2
<listitem>

Este documento oferece um procedimento para fazer 4 sistemas operacionais
coexistirem no mesmo disco rígido.



<varlistentry>
<term>Linux+FreeBSD
<listitem>

Descreve como usar o Linux e FreeBSD no mesmo sistema.



<varlistentry>
<term>Linux+NT-Loader
<listitem>

Descreve como usar o gerenciador de inicialização do Windows NT para iniciar o
<command>GNU/Linux.  Este processo foi testado com o Windows NT 4.0
WorkStation.



<varlistentry>
<term>Linux+Solaris
<listitem>

Descreve como usar o Linux (X86) e Solaris (x86) no mesmo computador.



<varlistentry>
<term>Linux+Win95
<listitem>

Descreve como usar o Linux e Windows 95-98 na mesma máquina.



<varlistentry>
<term>Loadlin+Win95-98-ME
<listitem>

Descreve como usar o Loadlin com o Windows 95/98/ME para inicializar no Linux.



<varlistentry>
<term>Multiboot-with-GRUB
<listitem>

Descreve como instalar o Windows 98, 2000, DOS e Linux usando o GRUB.



<varlistentry>
<term>Multiboot-with-LILO
<listitem>

Descreve como usar múltipla inicialização entre o Windows 95, Windows NT e
Linux.



</variablelist>


 userlevel='inter' s43.8.2.11">###Tarefas Específicas
<variablelist>
<varlistentry>
<term>Backup-With-MSDOS
<listitem>

Descreve como usar uma unidade de tape compatível com o
<command>GNU/Linux instalado em uma máquina DOS para fazer o backup
do sistema de arquivos de uma máquina <command>GNU/Linux.



<varlistentry>
<term>Battery-Powered
<listitem>

Descreve como reduzir o consumo de energia do sistema
<command>GNU/Linux através de alguns ajustes de configuração.  Isto
será útil para qualquer um quer executar o <command>GNU/Linux em um
sistema de computador portátil.  Também contém dicas de uso da bateria.  Se
estiver usando o <command>GNU/Linux em um sistema desktop, você
provavelmente não precisará ler todo este documento.



<varlistentry>
<term>Clock
<listitem>

Como manter o relógio de seu computador na hora.



<varlistentry>
<term>Coffee
<listitem>

Uma dos mais extremos dos documentos.  Eu já pensei se era possível usar o
<command>GNU/Linux para fazer café...  e descobri que o
<command>GNU/Linux faz café!


Por um longo tempo a humanidade estava se perguntando se um computador podia
fazer café...  As pessoas precisam de café para não dormirem na frente do
computador.  Todo mundo sabe que é melhor programar de noite...



<varlistentry>
<term>Divert-Sockets-mini-HOWTO
<listitem>

Descreve como obter, compilar e usar os soquetes divert FreeBSD sob o
<command>GNU/Linux 2.2.12.



<varlistentry>
<term>Home-Electrical-Control
<listitem>

Contém referências para fazer o Linux controlar praticamente qualquer
dispositivo elétrico.



<varlistentry>
<term>Leased-Line
<listitem>

Configurando seu modem e pppd para usar 2 pares de cabos leased line.



<varlistentry>
<term>Linux-Modem-Sharing
<listitem>

Descreve como configurar o sistema <command>GNU/Linux para
compartilhar um modem conectado a este sistema com outros através de uma rede
TCP/IP.



<varlistentry>
<term>Mail2News
<listitem>

Descreve como enviar mensagens de uma lista de discussão para um servidor news.



<varlistentry>
<term>MP3-CD-Burning
<listitem>

Uma referência completa para a criação de CDs de audio e dados de arquivos MP3.



<varlistentry>
<term>MSSQL6-Openlink-PHP-ODBC
<listitem>

Ensina como conectar o servidor de banco de dados MS SQL 6.x ou superior via
ODBC do PHP3 (e superior) compilado com os drivers Openlink sob o Linux.



<varlistentry>
<term>NCD-X-Terminal
<listitem>

Descreve como conectar um terminal NCD X a um computador UNIX.



<varlistentry>
<term>NFS-Root
<listitem>

Este documento tenta explicar como configurar uma estação de trabalho "sem
disco" no <command>GNU/Linux, que monta seu sistema de arquivos raíz
via NFS.



<varlistentry>
<term>NFS-Root-Client-mini-HOWTO
<listitem>

O propósito deste documento é explicar como criar um cliente dos diretórios
raíz em um servidor que está usando clientes com NFS root montados.



<varlistentry>
<term>Netscape+Proxy
<listitem>

Este documento descreve o processo de configurar uma REDE (INTRANET) em casa.
Então configura o NETSCAPE das máquinas dos clientes para acessarem a internet.



<varlistentry>
<term>News-Leafsite
<listitem>

Este documento ajudará a configuração de um pequeno leafsite para a Usenet News
usando o Leadnode do pacote free software.



<varlistentry>
<term>Offline-Mailing
<listitem>

Explica como usar o sistema de mensagens do <command>GNU/Linux
off-line, receber emails para múltiplos usuários somente com uma conta de
e-mail, e sem estar 24-24 horas on-line na Internet.  Se você não pode pagar
uma linha para estar conectado por 24-24 horas e ainda deseja que seus usuários
recebem emails em sua máquina Linux; também não pague por uma conta multi-drop
em seu provedor, você pode usar este sistema usando somente um endereço de
e-mail para dividir seus endereços de e-mails dos usuários.



<varlistentry>
<term>Outlook-to-Unix-Mailbox
<listitem>

Mostra formas de converter mensagens de email do Microsoft Outlook (exceto do
Outlook Express) para formatos de arquivos típicos do Unix.



<varlistentry>
<term>Pager
<listitem>

Ensina como compilar, instalar e configurar um Gateway de emails para Pager.



<varlistentry>
<term>Partition
<listitem>

Descreve como criar partições em discos rígidos IDE e SCSI.  Também é coberta a
recuperação de tabelas de partição perdidas.



<varlistentry>
<term>Partition-Rescue
<listitem>

Descreve formas para recuperar uma partição de disco apagada.



<varlistentry>
<term>Process-Accounting
<listitem>

Descreve como ativar a conta de processos em uma máquina
<command>GNU/Linux, o uso de vários comandos de contabilização de
processos.



<varlistentry>
<term>RCS
<listitem>

Este documento cobre a instalação e uso básicos do RCS, o GNU Revision Control
System sob o <command>GNU/Linux.



<varlistentry>
<term>Saving-Space
<listitem>

Este documento mostra maneiras de diminuir sua instalação
<command>GNU/Linux consumindo o mínimo possível de espaço.



<varlistentry>
<term>Secure-POP+SSH
<listitem>

Este documento explica como usar conexões POP seguras via ssh.



<varlistentry>
<term>Small-Memory
<listitem>

O propósito deste documento é descrever como executar o
<command>GNU/Linux em um sistema com pequena quantidade de memória.
Assumindo que a compra de memória esta fora de questão aqui.



<varlistentry>
<term>Soundblaster-AWE
<listitem>

Descreve como instalar e configurar a placa de som Sound Blaster 32 (SB AWE 32,
SB AWE 64) da Creative Labs em um Sistema Linux usando a extensão do driver de
som AWE escrito por Takashi Iwai.



<varlistentry>
<term>StarOffice
<listitem>

Instalando o StarOffice 3.1 da StarDivision no <command>GNU/Linux.



<varlistentry>
<term>TT-Debian
<listitem>

Descreve como configurar o suporte das fontes True Type na
<command>Debian.



<varlistentry>
<term>TkRat
<listitem>

Este documento foi escrito para qualquer um que tem interesse em usar seu
computador <command>GNU/Linux para enviar e receber E-mails pela
Internet.



<varlistentry>
<term>Visual-Bell
<listitem>

Explica como usar o termcap para configurar um aviso visual no sistema ao invés
do beep e como desativar o sinal de audio.



<varlistentry>
<term>Wacom-USB-mini-HOWTO
<listitem>

Descreve como configurar um Wacom Graphire USB tablet para uso no
<command>GNU/Linux (console e X), iniciando com a configuração do
kernel para o nível da aplicação.



<varlistentry>
<term>WordPerfect
<listitem>

Discute a execução do WordPerfect no <command>GNU/Linux incluindo uma
breve discussão sobre o WordPerfect 7.0.



<varlistentry>
<term>ZIP-Install
<listitem>

Este documento somente é útil para aqueles que possuem a versão em porta
paralela de um ZIP drive e que deseja fazer o backup do sistema
<command>GNU/Linux em um disco ZIP.



<varlistentry>
<term>call-back-mini-HOWTO
<listitem>

Descreve como configurar um call-back usando um sistema
<command>GNU/Linux e um modem.



</variablelist>


 userlevel='inter' s43.8.2.12">###Rede / Administração / Firewall / Segurança
<variablelist>
<varlistentry>
<term>ADSL
<listitem>

Configurando o <command>GNU/Linux para funcionar com Asymmetric
Digital Subscriber Loop (ADSL), uma nova tecnologia de acesso digital de alta
velocidade através de linhas disponível através da Telcos.  O ADSL é uma das
tecnologias disponíveis da família da digital subscriber line (DSL) disponíveis
para usuários residenciais e comerciais usando copper loops, oferecendo
velocidades que variam de 384kbps a 1.5Mbps.  Este documento contém uma
introdução ao ADSL e informações de como instalar, configurar e colocar o ADSL
para funcionar.



<varlistentry>
<term>Apache+SSL+PHP+fp
<listitem>

Este documento explica como construir um servidor web que suportará conteúdo
web dinâmico via a linguagem de scripting PHP/FI, transmissão de dados segura
baseado no SSL do Netscape, execução segura de CGI's e extensões do M$
Frontpage Server.



<varlistentry>
<term>Apache-mods
<listitem>

Detalhes sobre a instalação do servidor web baseado no Apache configurado para
manipular DSO e vários módulos úteis incluindo perl, ssl, e php.



<varlistentry>
<term>Bridge
<listitem>

Este documento descreve como ajustar uma ponte ethernet (bridge).  O que é uma
ponte ethernet?  É um dispositivo que controla os pacotes de dados dentro de
uma subrede na tentativa de cortar o excesso de tráfego.  Uma ponte é colocada
normalmente entre dois grupos separados de computadores que falam entre eles,
mas não muito com computadores no outro grupo.  Um bom exemplo disto é
considerar um grupo de Macintoshes e um grupo de máquinas Unix.  Ambos destes
grupos de máquinas tendem falar uma com as outras, e o tráfego que produzem na
rede causam colisões para as outras máquinas que estão tentando falar uma com a
outra.  Uma ponte pode ser colocada entre estes dois grupos de computadores.  A
tarefa da ponte é então examinar o destino dos pacotes de dados um por vez e
decidir o que passar ou não para o outro lado do segmento ethernet.  O
resultado é uma rede rápida com menos colisões.



<varlistentry>
<term>Bridge+Firewall
<listitem>

Como configurar uma ponte com um firewall.



<varlistentry>
<term>Bridge+Firewall+DSL
<listitem>

Configurando um sistema <command>GNU/Linux para funcionar como um
firewall e ponte com uma conexão de rede DSL.



<varlistentry>
<term>Cipe+Masq
<listitem>

Como configurar uma VPN usando o Cipe em um firewall
<command>GNU/Linux masquerading.



<varlistentry>
<term>Compressed-TCP
<listitem>

Seções TCP/IP compactadas usando ferramentas como SSH.



<varlistentry>
<term>DHCP
<listitem>

Este documento tenta responder questões básicas de como configurar seu
computador <command>GNU/Linux para servir de cliente ou servidor
DHCP.



<varlistentry>
<term>DPT-Hardware-RAID
<listitem>

Como ajustar o hardware RAID sob o <command>GNU/Linux.



<varlistentry>
<term>Domain
<listitem>

Este documento explica as coisas que você provavelmente deve fazer quando
desejar construir uma rede de computadores sob seu próprio domínio.  Ele cobre
a configuração dos parâmetros de rede, serviços de rede e segurança.



<varlistentry>
<term>FTP
<listitem>

Como usar clientes e servidores FTP.



<varlistentry>
<term>Fax-Server
<listitem>

Descreve os métodos mais simples de configurar um servidor de fax em seu
sistema <command>GNU/Linux.  O fax está disponível aos usuários do
seu sistema local e rede de usuários.



<varlistentry>
<term>Firewall-Piercing
<listitem>

Métodos de usar PPP através de telnet para tornar os materiais da rede
transparentes através de um firewall Internet.



<varlistentry>
<term>Home-Network-mini-HOWTO
<listitem>

Um tutorial simples de configuração do sistema Red Hat 6 e variantes para
operar como um gateway na internet para uma pequena rede doméstica ou de
escritório.  Entre os tópicos cobertos estão incluídos masquerading, DNS, DHCP
e segurança básica.



<varlistentry>
<term>IP-Alias
<listitem>

Descreve como utilizar vários IPs em uma única interface de rede.  Em adição,
estão incluídas instruções de como ajustar a máquina para receber e-mais em IPs
alises.



<varlistentry>
<term>IP-Subnetworking
<listitem>

Descreve porque e como subdividir uma rede IP - que está usando uma simples
classe de rede A, B ou C para funcionar corretamente em diversas redes
interconectadas.



<varlistentry>
<term>IPMasquerading+Napster
<listitem>

Descreve como permitir usuários através de um sistema IPMasquerade usar o
Napster.



<varlistentry>
<term>ISP-Connectivity
<listitem>

Descreve como configurar o PPP, conectar-se ao seu Provedor, configurar o
E-mail e news, obter um IP permanente (se disponível), obter um nome de
domínio.



<varlistentry>
<term>Mail-Queue
<listitem>

Queue E-mails remotos + Entregar e-mails locais as configurações necessárias
para fazer o Sendmail enviar mensagens locais ***Agora*** e entregar mensagens
remotas "quando quiser".



<varlistentry>
<term>Netrom-Node
<listitem>

Este documento descreve como configurar o pacote de utilitários ax25 para Rádio
Amadores.



<varlistentry>
<term>PLIP
<listitem>

Este documento lhe ajudará a usar sua porta Paralela para conexão entre
computadores.



<varlistentry>
<term>ppp-ssh
<listitem>

Descreve como configurar uma rede VPN usando ssh sobre ppp.



<varlistentry>
<term>PortSlave
<listitem>

Configurando e usando um roteador Linux para conexão remota, radius, console
serial.



<varlistentry>
<term>Proxy-ARP-Subnet
<listitem>

Este documento discute o uso do Proxy Address Resolution Protocol (ARP) com
subrede em ordem para fazer uma pequena rede de computadores visível a outra
sub rede IP (eu chamo isto de sub-subrede).  isto faz todas as máquinas na rede
local (rede 0 onde estamos agora) aparecer como se estivessem conectadas a rede
principal (rede 1).



<varlistentry>
<term>Public-Web-Browser
<listitem>

A idéia básica é dar acesso web a pessoas que desejam, limitando suas
habilidades de causar problemas.



<varlistentry>
<term>Qmail+MH
<listitem>

Ensina como usar o Qmail em conjunto com o MH.



<varlistentry>
<term>Remote-Boot
<listitem>

Este documento descreve como configurar um servidor de inicialização robusto e
seguro para um grupo de PCS, permitindo cada cliente escolher em tempo de
inicialização qual sistema operacional executar.



<varlistentry>
<term>SLIP-PPP-Emulator
<listitem>

Descreve como obter seu computador Linux conectado a um site genérico via
emulador SLIP/PPP, tal como SLiRP ou TIA.



<varlistentry>
<term>Sendmail+UUCP
<listitem>

Como utilizar o Sendmail em conjunto com o UUCP.



<varlistentry>
<term>Sendmail-Address-Rewrite
<listitem>

Breve descrição de como ajustar o arquivo de configuração do sendmail para o
usuário doméstico que utiliza o acesso dial-up a



<varlistentry>
<term>Sybase-PHP-Apache
<listitem>

Explica como usar o PHP + Apache para acesso a uma base de dados Sybase-ASE.



<varlistentry>
<term>Term-Firewall
<listitem>

Métodos de usar o "term" para tornar os materiais de rede transparentes através
de um firewall TCP que parece não ser capaz.



<varlistentry>
<term>Token-Ring
<listitem>

Fazendo o Token Ring funcionar no <command>GNU/Linux.



<varlistentry>
<term>TransparentProxy
<listitem>

Como configurar um servidor proxy transparente de cache HTTP usando somente o
<command>GNU/Linux e o Squid.



<varlistentry>
<term>VPN
<listitem>

Ensina como configurar uma Virtual Protected Network no
<command>GNU/Linux.



</variablelist>


 userlevel='inter' s43.8.2.13">###Outros
<variablelist>
<varlistentry>
<term>Advocacy
<listitem>

Este documento oferece sugestões de como a comunidade Linux pode defender
efetivamente o uso do Linux.



<varlistentry>
<term>BogoMips
<listitem>

Detalhes sobre BogoMips.  Este texto foi criado a partir de vários arquivos
<command>GNU/Linux no arquivo
<filename>HOWTO/mini/BogoMips</filename>.



<varlistentry>
<term>Commercial-Port-Advocacy
<listitem>

Este documento discute métodos que podem ser usados como aproximação de
empresas comerciais para convence-las a portar seus programas para o
<command>GNU/Linux.



</variablelist>






    

 ajuda-docs">###Documentação de Programas

São documentos instalados junto com os programas.  
<!-- [ %DESCRICAOD [ --> Alguns programas também
trazem o **aviso de copyright, changelogs, modelos, scripts, exemplos e
FAQs (perguntas freqüêntes)** junto com a documentação normal.
 <!-- ]]> -->


Seu princípio é o mesmo do How-to; documentar o programa.  Estes arquivos estão
localizados em:


<!-- [ %DEBIAN [ --> <filename>/usr/share/doc/</filename>[**programa**]. <!-- ]]> -->


**Programa** é o nome do programa ou comando procurado.



 ajuda-faq">###FAQ

**FAQ** é um arquivo de perguntas e respostas mais freqüêntes
sobre o programa.  Normalmente os arquivos de FAQ estão localizados junto com a
documentação principal do programa em
<!-- [ %DEBIAN [ --> <filename>/usr/share/doc/</filename>[**programa**]. <!-- ]]> -->




 userlevel='inter;avanc' ajuda-rfcs">###RFC's

São textos que contém normas para a padronização dos serviços e protocolos da
Internet (como a porta padrão de operação, comandos que devem ser utilizados,
respostas) e outros detalhes usados para padronizar o uso de serviços Internet
entre as mais diversas plataformas de computadores, com o objetivo de garantir
a perfeita comunicação entre ambos.  As RFC's podem ser obtidas de ("http://www.w3.org/1999/xlink) [](http://rfc.net">http://rfc.net.

<!-- [ %DESCRICAOD [ -->

O arquivo de uma RFC segue o formato <filename>RFC+Número</filename>, onde
<literal>RFC descreve que o documento é uma RFC e
<literal>Número é o seu número de identificação, como o documento
<filename>RFC1939</filename> que documenta o funcionamento e comandos do
protocolo POP3.  Os arquivos de RFC's podem ser encontrados no pacote
<!-- [ %DEBIAN [ --> <systemitem role="package">doc-rfc</systemitem> da distribuição
<command>Debian e baseadas. <!-- ]]> --> 
<!-- ]]> -->


Segue abaixo o índice principal do diretório de RFC's que poderá ser usado para
localizar RFC's específicas de um determinado serviço/assunto:

<variablelist>
<varlistentry>
<term>0001
<listitem>

PADRÕES OFICIAIS DO PROTOCOLO INTERNET.  J.  Reynolds, R.  Braden.  Março 2000.
(Formato: TXT=86139 bytes) (Deixa obsoleto RFC2500, RFC2400, RFC2300, RFC2200,
RFC2000, RFC1920, RFC1880, RFC1800, RFC1780, RFC1720, RFC1610, RFC1600,
RFC1540, RFC1500, RFC1410, RFC1360, RFC1280, RFC1250, RFC1200, RFC1140,
RFC1130, RFC1100, RFC1083) (Também RFC2600)



<varlistentry>
<term>0002
<listitem>

Números designados.  J.  Reynolds, J.  Postel.  Outubro 1994.  (Formato:
TXT=458860 bytes) (Também RFC1700)



<varlistentry>
<term>0003
<listitem>

Requerimentos do sistema.  R.  Braden.  Outubro 1989.  (Formato: TXT=528939
bytes) (Também RFC1122, RFC1123)



<varlistentry>
<term>0004
<listitem>

Requerimentos do Gateway.  R.  Braden, J.  Postel.  Junho 1987.  (Formato:
TXT=125039 bytes) (Também RFC1009)



<varlistentry>
<term>0005
<listitem>

Protocolo Internet.  J.  Postel.  Setembro 1981.  (Formato: TXT=241903 bytes)
(Também RFC0791, RFC0950, RFC0919, RFC0922, RFC792, RFC1112)



<varlistentry>
<term>0006
<listitem>

User Datagram Protocol.  J.  Postel.  Agosto 1980.  (Formato: TXT=5896 bytes)
(Também RFC0768)



<varlistentry>
<term>0007
<listitem>

Transmission Control Protocol.  J.  Postel.  September 1981.  (Formato:
TXT=172710 bytes) (Também RFC0793)



<varlistentry>
<term>0008
<listitem>

Protocolo Telnet.  J.  Postel, J.  Reynolds.  Maio 1983.  (Formato: TXT=44639
bytes) (Também RFC0854, RFC0855)



<varlistentry>
<term>0009
<listitem>

File Transfer Protocol.  J.  Postel, J.  Reynolds.  Outubro 1985.  (Formato:
TXT=148316 bytes) (Também RFC0959)



<varlistentry>
<term>0010
<listitem>

SMTP Service Extensions.  J.  Klensin, N.  Freed, M.  Rose, E.  Stefferud &amp; D.
Crocker.  Novembro 1995.  (Formato: TXT=23299 bytes) (Deixa obsoleto RFC1651)
(Também RFC821, RFC1869)



<varlistentry>
<term>0011
<listitem>

Standard for the format of ARPA Internet text messages.  D.  Crocker.
13-Ago-1982.  (Formato: TXT=109200 bytes) (Deixa obsoleto RFC1653) (Também
RFC0822)



<varlistentry>
<term>0012
<listitem>

Network Time Protocol.  D.  Mills.  Setembro 1989.  (Formato: TXT=193 bytes)
(Também RFC1119)



<varlistentry>
<term>0013
<listitem>

Domain Name System.  P.  Mockapetris.  Novembro 1987.  (Formato: TXT=248726
bytes) (Também RFC1034, RFC1035)



<varlistentry>
<term>0014
<listitem>

Mail Routing and the Domain System.  C.  Partridge.  Janeiro 1986.  (Formato:
TXT=18182 bytes) (Também RFC0974)



<varlistentry>
<term>0015
<listitem>

Simple Network Management Protocol.  J.  Case, M.  Fedor, M.  Schoffstall, J.
Davin.  Maio 1990.  (Formato: TXT=72876 bytes) (Também RFC1157)



<varlistentry>
<term>0016
<listitem>

Structure of Management Information.  M.  Rose, K.  McCloghrie.  Maio 1990.
(Formato: TXT=82279 bytes) (Deixa obsoleto RFC1065) (Também RFC1155)



<varlistentry>
<term>0017
<listitem>

Management Information Base.  K.  McCloghrie, M.  Rose.  March 1991.  (Formato:
TXT=142158 bytes) (Deixa obsoleto RFC1158) (Também RFC1213)



<varlistentry>
<term>0018
<listitem>

Exterior Gateway Protocol.  D.  Mills.  Abril 1984.  (Formato: TXT=63836 bytes)
(Também RFC0904)



<varlistentry>
<term>0019
<listitem>

NetBIOS Service Protocols.  NetBIOS Working Group.  Março 1987.  (Formato:
TXT=319750 bytes) (Também RFC1001, RFC1002)



<varlistentry>
<term>0020
<listitem>

Echo Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=1237 bytes) (Também
RFC0862)



<varlistentry>
<term>0021
<listitem>

Discard Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=1239 bytes) (Também
RFC0863)



<varlistentry>
<term>0022
<listitem>

Character Generator Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=6842
bytes) (Também RFC0864)



<varlistentry>
<term>0023
<listitem>

Quote of the Day Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=1676 bytes)
(Também RFC0865)



<varlistentry>
<term>0024
<listitem>

Active Users Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=2029 bytes)
(Também RFC0866)



<varlistentry>
<term>0025
<listitem>

Daytime Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=2289 bytes) (Também
RFC0867)



<varlistentry>
<term>0026
<listitem>

Time Server Protocol.  J.  Postel.  Maio 1983.  (Formato: TXT=3024 bytes)
(Também RFC0868)



<varlistentry>
<term>0027
<listitem>

Binary Transmission Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.
(Formato: TXT=8965 bytes) (Também RFC0856)



<varlistentry>
<term>0028
<listitem>

Echo Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.  (Formato: TXT=10859
bytes) (Também RFC0857)



<varlistentry>
<term>0029
<listitem>

Suppress Go Ahead Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.
(Formato: TXT=3712 bytes) (Também RFC0858)



<varlistentry>
<term>0030
<listitem>

Status Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.  (Formato:
TXT=4273 bytes) (Também RFC0859)



<varlistentry>
<term>0031
<listitem>

Timing Mark Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.  (Formato:
TXT=7881 bytes) (Também RFC0860)



<varlistentry>
<term>0032
<listitem>

Extended Options List Telnet Option.  J.  Postel, J.  Reynolds.  Maio 1983.
(Formato: TXT=3068 bytes) (Também RFC0861)



<varlistentry>
<term>0033
<listitem>

Trivial File Transfer Protocol.  K.  Sollins.  Julho 1992.  (Formato: TXT=24599
bytes) (Também RFC1350)



<varlistentry>
<term>0034
<listitem>

Routing Information Protocol.  C.  Hedrick.  Junho 1988.  (Formato: TXT=91435
bytes) (Também RFC1058)



<varlistentry>
<term>0035
<listitem>

ISO Transport Service on top of the TCP (Version: 3).  M.  Rose, D.  Cass.
Maio 1978.  (Formato: TXT=30662 bytes) (Também RFC1006)



<varlistentry>
<term>0036
<listitem>

Transmission of IP and ARP over FDDI Networks.  D.  Katz.  Janeiro 1993.
(Formato: TXT=22077 bytes) (Também RFC1390)



<varlistentry>
<term>0037
<listitem>

An Ethernet Address Resolution Protocol.  David C.  Plummer.  Novembro 1982.
(Formato: TXT=21556 bytes) (Também RFC0826)



<varlistentry>
<term>0038
<listitem>

A Reverse Address Resolution Protocol.  Ross Finlayson, Timothy Mann, Jeffrey
Mogul, Marvin Theimer.  Junho 1984.  (Formato: TXT=9345 bytes) (Também RFC0903)



<varlistentry>
<term>0039
<listitem>

Interface Message Processor: Especificações para a Interconexão de um
computador e um IMP (Revisado).  BBN.  Dezembro 1981.  (fora de linha)



<varlistentry>
<term>0040
<listitem>

Host Access Protocol specification.  Bolt Beranek and Newman.  Agosto 1993.
(Formato: TXT=152740 bytes) (Deixa obsoleto RFC0907) (Também RFC1221)



<varlistentry>
<term>0041
<listitem>

Standard for the transmission of IP datagrams over Ethernet networks.  C.
Hornig.  Abril 1984.  (Formato: TXT=5697 bytes) (Também RFC0894)



<varlistentry>
<term>0042
<listitem>

Standard for the transmission of IP datagrams over experimental
Ethernetnetworks.  J.  Postel.  Abril 1984.  (Formato: TXT=4985 bytes) (Também
RFC0895)



<varlistentry>
<term>0043
<listitem>

Standard for the transmission of IP datagrams over IEEE 802 networks.  J.
Postel, J.K.  Reynolds.  Agosto 1993.  (Formato: TXT=34359 bytes) (Deixa
obsoleto RFC0948) (Também RFC1042)



<varlistentry>
<term>0044
<listitem>

DCN Local-Network Protocols.  D.L.  Mills.  Agosto 1993.  (Formato: TXT=65340
bytes) (Também RFC0891)



<varlistentry>
<term>0045
<listitem>

Internet Protocol on Network System's HYPERchannel: Protocol Specification.  K.
Hardwick, J.  Lekashman.  Augosto 1993.  (Formato: TXT=100836 bytes) (Também
RFC1044)



<varlistentry>
<term>0046
<listitem>

Transmitting IP traffic over ARCNET networks.  D.  Provan.  Agosto 1993.
(Formato: TXT=16565 bytes) (Deixa obsoleto RFC1051) (Também RFC1201)



<varlistentry>
<term>0047
<listitem>

Nonstandard for transmission of IP datagrams over serial lines: SLIP.  J.L.
Romkey.  Agosto 1993.  (Formato: TXT=12578 bytes) (Também RFC1055)



<varlistentry>
<term>0048
<listitem>

Standard for the transmission of IP datagrams over NetBIOS networks.  L.J.
McLaughlin.  Agosto 1993.  (Formato: TXT=5579 bytes) (Também RFC1088)



<varlistentry>
<term>0049
<listitem>

Standard for the transmission of 802.2 packets over IPX networks.  L.J.
McLaughlin.  Agosto 1993.  (Formato: TXT=7902 bytes) (Também RFC1132)



<varlistentry>
<term>0050
<listitem>

Definitions of Managed Objects for the Ethernet-like Interface Types.  F.
Kastenholz.  Julho 1994.  (Formato: TXT=39008, bytes) (Deixa obsoleto RFC1623,
RFC1398) (Também RFC1643)



<varlistentry>
<term>0051
<listitem>

The Point-to-Point Protocol (PPP).  W.  Simpson, Editor.  Julho 1994.
(Formato: TXT=151158 bytes) (Deixa obsoleto: RFC1549) (Também RFC1661, RFC1662)



<varlistentry>
<term>0052
<listitem>

The Transmission of IP Datagrams over the SMDS Service.  D.  Piscitello, J.
Lawrence.  Março 1991.  (Formato: TXT=24662 bytes) (Também RFC1209)



<varlistentry>
<term>0053
<listitem>

Post Office Protocol - Version 3.  J.  Myers &amp; M.  Rose.  Maio 1996.  (Formato:
TXT=47018 bytes) (Deixa Obsoleto: RFC1725) (Também RFC1939)



<varlistentry>
<term>0054
<listitem>

OSPF Version 2.  J.  Moy.  Abril 1998.  (Formato: TXT=447367 bytes) (Também
RFC2328)



<varlistentry>
<term>0055
<listitem>

Multiprotocol Interconnect over Frame Relay.  C.  Brown, A.  Malis.  Setembro
1998.  (Formato: TXT=74671 bytes) (Deixa Obsoleto: RFC1490, RFC1294) (Também
RFC2427)



<varlistentry>
<term>0056
<listitem>

RIP Version 2.  G.  Malkin.  Novembro 1998.  (Formato: TXT=98462 bytes)
(Atualiza RFC1723, RFC1388) (Também RFC2453)



<varlistentry>
<term>0057
<listitem>

RIP Version 2 Protocol Applicability Statement.  G.  Malkin.  Novembro 1994.
(Formato: TXT=10236 bytes) (Também RFC1722)



<varlistentry>
<term>0058
<listitem>

Structure of Management Information Version 2 (SMIv2.  K.  McCloghrie, D.
Perkins, J.  Schoenwaelder.  Abril 1999.  (Formato: TXT=89712 bytes) (Deixa
Obsoleto RFC1902) (Também RFC2578, RFC2579)



<varlistentry>
<term>0059
<listitem>

Remote Network Monitoring Management Information Base.  S.  Waldbusser.  Maio
2000.  (Formato: TXT=198676 bytes) (Deixa Obsoleto RFC1757) (Também RFC2819)



</variablelist>



 ajuda-internet">###Internet

Certamente o melhor suporte ao <command>GNU/Linux é via Internet,
veja abaixo alguns locais úteis de onde pode obter ajuda ou se atualizar.


 ajuda-paginas">###Páginas Internet de Referência

Existem boas páginas Internet Nacionais e Internacionais sobre o
<command>GNU/Linux e assuntos relacionados com este sistema.  A
maioria trazem documentos e explicações sobre configuração, instalação,
manutenção, documentação, suporte, etc.


Estas páginas podem ser encontradas através de ferramentas de busca.  Entre
outras páginas, posso citar as seguintes:

<itemizedlist>
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.debianbrasil.org)http://www.debianbrasil.org/
Projeto Debian-Br.  A <command>Debian é uma distribuição de
<command>Linux conhecida por sua qualidade, grande número de pacotes,
estabilidade, facilidade de atualização, desenvolvimento aberto, segurança,
ferramentas de gerenciamento de servidores e comprometimento com o software
livre.


A Debian é feita originalmente em inglês e traduzida por grupos em vários
lugares do mundo.  O projeto **Debian-br**
destina-se a colaborar na tradução da <command>Debian para o
Português (nossa língua-mãe).  Através desse projeto, todos poderão, da forma
colaborativa como na <command>Debian, trazer essa excelente
distribuição em nosso idioma!


Participe:

<itemizedlist>
<listitem>

Você pode pegar um documento pra traduzir


<listitem>

Reformular a página do projeto


<listitem>

Programando para o projeto


<listitem>

Sendo um desenvolvedor da Debian


<listitem>

A pagina do projeto é a ("http://www.w3.org/1999/xlink) [](http://www.debianbrasil.org)http://www.debianbrasil.org/


<listitem>

Revisar documentação


<listitem>

Ou participar de outras tarefas do seu interesse!




Entre em contato com o responsável pelo projeto pelo email
<email>debian-br@listas.cipsga.org.br para saber como entrar no projeto
ou visite a página ("http://www.w3.org/1999/xlink) [](http://www.debianbrasil.org)http://www.debianbrasil.org/.  Todos
os interessados estão convidados a participar do projeto!


<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.tldp.org)http://www.tldp.org/ - Projeto de
documentação do <command>GNU/Linux no Brasil.  Toda a documentação
traduzida para o Português do Brasil pode ser encontrada lá.


Responsável pela página: <email>ricardo@conectiva.com.br endereço:
("http://www.w3.org/1999/xlink) [](http://www.tldp.org)http://www.tldp.org/.


<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.linux.org)http://www.linux.org/ - Página
oficial do <command>GNU/Linux mantida pela
**Transmeta** (a empresa que Linus Torvalds vem trabalhando
atualmente).  Muita referência sobre <command>GNU/Linux,
distribuições, hardwares, softwares, downloads, etc.


Responsável pela página: <email>webmaster@linux.org endereço: ("http://www.w3.org/1999/xlink) [](http://www.linux.org)http://www.linux.org/.


<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.oreill.com/safari)http://www.oreill.com/safari/
- Neste site você encontra os livros publicados sobre a licença OpenBook da
Orreil.  Na maioria livros que não atende mais propósitos atualmente e livros
em que os autores concordaram em licenciar sob os termos OpenBook.


Endereço: ("http://www.w3.org/1999/xlink) [](http://www.oreill.com/safari)http://www.oreill.com/safari/.




Caso conhecer uma página de Internet que contenha materiais úteis a comunidade
<command>GNU/Linux ou desejar incluir a sua, entre em contato para
sua inclusão na próxima versão do guia junto com uma descrição da página.




 ajuda-listas">###Listas de discussão

São grupos de usuários que trocam mensagens entre si, resolvem dúvidas, ajudam
na configuração de programas, instalação, etc.  É considerado o melhor suporte
ao <command>GNU/Linux pois qualquer participante pode ser beneficiar
das soluções discutidas.  Existem milhares de listas de discussões sobre o
<command>GNU/Linux espalhadas pelo mundo, em Português existem
algumas dezenas.


Algumas listas são específicas a um determinado assunto do sistema, algumas são
feitas para usuários iniciantes ou avançados, outras falam praticamente de
tudo.  Existem desde usuários iniciantes, hackers, consultores, administradores
de redes experientes e gurus participando de listas e oferecendo suporte de
graça a quem se aventurar em instalar e usar o sistema
<command>GNU/Linux.

<!-- [ %DESCRICAOD [ -->

A lista de discussão funciona da seguinte forma: você se inscreve na lista
enviando uma mensagem ao endereço de inscrição, será enviada um pedido de
confirmação por e-mail, simplesmente dê um reply na mensagem para ser
cadastrado.  Pronto!  agora você estará participando do grupo de usuários e
receberá todas as mensagens dos participantes do grupo.  Assim você poderá
enviar sua mensagem e ela será vista por todos os participantes da lista.


Da mesma forma, você pode responder uma dúvida de outro usuário da lista ou
discutir algum assunto, tirar alguma dúvida sobre a dúvida de outra pessoa,
etc.

<!-- ]]> -->

Não tenha vergonha de enviar sua pergunta, participar de listas de discussão é
uma experiência quase obrigatório de um <literal>Linuxer.  Abaixo
segue uma relação de listas de discussão em Português com a descrição, endereço
de inscrição, e o que você deve fazer para ser cadastrado:

<variablelist>
<varlistentry>
<term><email>debian-user-portuguese@lists.debian.org
<listitem>

Lista de discussão para usuários Portugueses da <command>Debian.
Também são discutidos assuntos relacionados ao Linux em geral.  A inscrição é
aberta a todos os interessados.


Para se inscrever, envie uma mensagem para
<email>debian-user-portuguese-request@lists.debian.org contendo a
palavra <literal>subscribe no assunto da mensagem.  Será enviada uma
mensagem a você pedindo a confirmação da inscrição na lista de discussão,
simplesmente dê um reply na mensagem (responder) e você estará cadastrado e
poderá enviar e receber mensagens dos participantes.



<varlistentry>
<term><email>debian-news-portuguese@lists.debian.org
<listitem>

A <command>Debian é extremamente bem estruturada quanto a divulgações
e notícias, várias listas de email e várias páginas compõe essa base.  A
**Debian Weekly News** é especialmente importante pois dá uma
visão geral do que se passou na <command>Debian durante a semana.  E
não traz apenas traduções mas também adições dos acontecimentos atuais da
<command>Debian no Brasil, ou projetos concluídos ou lançados pela
equipe **Debian-br** http://www.w3.org/1999/xlink) [](http://www.debianbrasil.org)http://www.debianbrasil.org/).


Essa lista <literal>NÃO é usada para resolução de dúvidas e
problemas, apenas para o RECEBIMENTO de notícias relacionadas a Debian.  Não
poste mensagens nela!


Para se inscrever, envie uma mensagem para
<email>debian-news-portuguese-request@lists.debian.org contendo a
palavra <literal>subscribe no assunto da mensagem.  Será enviada uma
mensagem a você pedindo a confirmação da inscrição na lista de discussão,
simplesmente dê um reply na mensagem (responder) e você passará a receber as
notícias sobre a Debian em Português.



<varlistentry>
<term><email>linux-br@unicamp.br
<listitem>

Lista de discussão que cobre assuntos diversos.  Esta lista é voltada para
usuários com bons conhecimentos no <command>GNU/Linux, são abordados
assuntos como redes, configurações, etc.  Esta é uma lista moderada, o que
significa que a mensagem que envia passam por uma pessoa que verifica (modera)
e a libera caso estejam dentro das normas adotada na lista.  É uma lista de
alto nível e recomendada para quem deseja fugir de mensagens como <literal>não
consigo instalar o Linux, <literal>não sei compilar o
kernel, <literal>o que eu faço quando vejo uma tela com o nome
login:?, etc.


Para se inscrever nesta lista, envie uma mensagem para:
<email>linux-br-request@unicamp.br contendo a palavra
<literal>subscribe no assunto da mensagem e aguarde o recebimento da
confirmação da inscrição.  Apenas responda a mensagem de confirmação para se
inscrever.  Para se descadastrar envie uma mensagem para o mesmo endereço mas
use a palavra <literal>unsubscribe.



<varlistentry>
<term><email>dicas-l@unicamp.br
<listitem>

Esta lista envia diariamente uma dica de <command>Unix, sistemas da
Microsoft ou novidades da Internet.


Para se inscreve nesta lista de discussão, envie uma mensagem para:
<email>dicas-l-request@unicamp.br contendo a palavra
<literal>subscribe no corpo da mensagem e aguarde o recebimento da
confirmação da inscrição.  Apenas responda a mensagem de confirmação para
confirmar sua inscrição na lista.  Para se descadastrar envie uma mensagem para
o mesmo endereço mas use a palavra <literal>unsubscribe.



</variablelist>

Esta listagem deveria estar mais completa, mas eu não lembro de todas as
listas!.  Também recomendo dar uma olhada em <xref linkend="ajuda-netiqueta-listas"que descreve recomendações de comportamento
em listas de discussão.






 ajuda-netiqueta">###Netiqueta

São recomendações que tem como objetivo facilitar a comunicação através
dos recursos de uma rede.  O nome **Netiqueta** vem de
"Etiqueta de Rede" (**Net Etiquete**).  O material desta seção
foi escrito com base nos anos de observação que tive via internet e também com
referência a rfc 1855.


 ajuda-netiqueta-geral">###Recomendações Gerais sobre a Comunicação Eletrônica
<itemizedlist>
<listitem>

Como recomendação geral, lembre-se que a conversa via internet é feita sempre
de uma para outra pessoa ou de uma para várias pessoas, e que a forma de
comunicação é a mesma que utilizaria se estivesse de frente a frente com a
pessoa.  Nunca diga algo que não diria se estivesse diante da outra pessoa.
Existem pessoas que por estar atrás de um monitor, se sentem "maiores" se
esquecendo disso e causando prejuízos de comunicação (e sem imaginar que a
pessoa do outro lado da linha existe).


Apesar do modo que as frases são escritas expressarem o jeito que a outra
pessoa está do outro lado da linha e seu tom de comunicação no decorrer da
conversa, existem algumas coisas que não podem ser totalmente expressadas
através da Internet, como por exemplo a expressão da "face" das pessoas.  Para
isto foram criados símbolos chamados **smileys** que expressam
a face da outra pessoa em determinado momento, e dependendo do sentido da
conversa, um smiley pode expressar corretamente a intenção de sua frase.  Os
mais usados são os seguintes:

<screen>
:-)   --&gt; Sorriso

:-(   --&gt; Triste

;-)   --&gt; Piscadinha

:-O   --&gt; De boca aberta

:-|   --&gt; Sem graça

8-)   --&gt; De óculos 

|-)   --&gt; Com sono e feliz

&amp;:-)  --&gt; Bobo


Para entender o sentido do smiley, veja ele de lado (45 graus).  Use os smileys
em suas conversas, mas com cautela.  Não espere que a inclusão de um smiley
sorridente ":-)" deixe o destinatário da mensagem contente com um comentário
rude ou insulto.


<listitem>

ESCREVER EM MAIÚSCULAS significa gritar quando escrever mensagens eletrônicas.


<listitem>

Use *asteriscos* para destacar uma palavra ou frase.  _Isso_ indica uma
palavra/frase sublinhada.


<listitem>

Se você troca mensagens com pessoas do mundo todo, não espere que um japonês
responda logo seu e-mail que enviou as 15:00 da tarde.  A essa hora no país
dele, ele está roncando forte na cama e sonhando com a placa 3D que vai ganhar
para melhorar o desempenho de seus jogos de <command>Linux.


<listitem>

Durante a comunicação com pessoas de diferentes regiões (ou países), evite a
utilização de gírias, ou expressões regionais.  Uma interpretação em uma
determinada região não garante que ela tenha o mesmo significado para seu
destinatário, as vezes pode ser até ofensiva.


<listitem>

Assuma que sua mensagem está trafegando sobre uma via não segura, desta forma
não envie informações pessoais que não enviaria em uma carta comum.  O uso de
criptografia pode garantir melhor segurança na transmissão de dados.






 ajuda-netiqueta-email">###Email
<itemizedlist>
<listitem>

Tenha o hábito de colocar sempre um assunto na mensagem que envia para
identificar seu conteúdo.


<listitem>

Respeite os direitos autorais das mensagens de e-mail.  Se precisar encaminhar
mensagens, preserve seu conteúdo original.


<listitem>

Procure limitar o tamanho da linha a 70 caracteres.  Muitos usuários utilizam
cliente de e-mail em modo texto, e nem todo mundo usa a mesma resolução que
você.


<listitem>

Caso o e-mail que responda tenha mais que 100 linhas, é recomendável colocar a
palavra "LONGA" no assunto da mensagem.  Se possível corte as partes não
necessárias da mensagens de respostas tendo o cuidado de não "cortar" de forma
mal educada a mensagem de outra pessoa.


<listitem>

Caso utiliza um editor programa de e-mails com suporte a HTML, envie o e-mail
utilizando ambos os formatos TEXTO e HTML, muitos administradores Linux
utilizam sistemas que não suportam HTML.


<listitem>

Não espere que o espaçamento ou desenhos ASCII usados em uma mensagem sejam
mostrados corretamente em todos os sistemas.


<listitem>

Utilize sempre uma assinatura no final da mensagem para identificar você e
principalmente seu endereço de e-mail.  Em alguns clientes de e-mail, o campo
<literal>Reply-to é bagunçado, e em e-mails redirecionados o endereço
de resposta é excluído.  A assinatura facilita encontrar o remetente da
mensagem.  Tente manter a assinatura em um tamanho de no máximo 4 linhas.


<listitem>

Não repasse mensagens de corrente por e-mail.  Elas tem somente o objetivo de
espalhar boatos na Internet e se espalhar.  Normalmente elas vem com uma
história bonita e no final diz se não repassar acontecerá tudo ao contrário com
você ou algo do tipo.  **Não vai acontecer nada!  ignore isso e não
entre na corrente!**


Pelas políticas da Internet, você pode ter sua conta de e-mail perdida se fizer
mal uso dele.





 ajuda-netiqueta-rtmsg">###Telegram/Whatsapp/Messenger/Gtalk/Skype

Ferramentas de mensagens instantâneas são eficientes, alertando a presença
on-line do usuário, auxiliando na redução de custos, etc.  Este documento
inclui algumas recomendações etiqueta para os usuários aproveitarem
melhor as ferramentas de comunicação que seguem o padrão IM:

<itemizedlist>
<listitem>

De atenção ao status da outra pessoa.  Se ela estiver "on-line" ou "free for
chat" significa que ela está desocupada e que pode conversar naquele instante.
Se estiver como não perturbe, envie somente mensagens se for mesmo preciso.


<listitem>

EVITE colocar nicks chamativos e caracteres exóticos.  Nem todos os usuários
vêem o nick da mesma forma que a pessoa que os colocou.


<listitem>

Seja também sensato ao usar ferramentas de mensagem instantanea.  Não entre
nele caso não possa conversar, ou avise isso mudando seu status para o mais
adequado para a situação, assim os outros poderão entender que está longe do
computador, não disponível ou ocupado.


<listitem>

É recomendável ser prudente quanto ao envio de mensagens, não envie mais do que
4 mensagens seguidas, pois a outra pessoa terá dificuldades para responder a
todas elas mais outra que talvez possa estar recebendo de outras (ou nem tenha
recebido, caso exista algum problema temporário no servidor).


<listitem>

Guarde seu login e senha em lugar seguro.  Caso ela seja perdida, você terá
trabalho para avisar a todos de sua lista de contato.


<listitem>

Sempre que enviar uma URL, procure do que se trata na mensagem.


<listitem>

No modo de chat, use as recomendações descritas sobre o talk (em <xref linkend="ajuda-netiqueta-talk"/>).


<listitem>

Como em toda comunicação on-line, seja cauteloso quando a pessoa que conversa.
Nem sempre quem conversamos do outro lado é a pessoa que esperamos encontrar.
Lembre-se que um registro falso e uma identidade pode ser criada sem
dificuldades por qualquer pessoa.






 ajuda-netiqueta-talk">###Talk
<itemizedlist>
<listitem>

Use sempre quebra de linhas ao escrever suas mensagens, use pelo menos 70
caracteres para escrever suas mensagens de talk.  Evita escrever continuamente
até a borda para fazer quebra de linha automática, alguns clientes de talk não
aceitam isso corretamente.


<listitem>

Sempre que termina uma frase, deixe uma linha em branco (tecle enter 2 vezes)
para indicar que a outra pessoa pode iniciar a digitação.


<listitem>

Sempre se despeça da outra pessoa e espere ela responder antes de fechar uma
seção de conversação.  O respeito mútuo durante um diálogo é essencial :-)


<listitem>

Lembre-se que o talk normalmente interrompe as pessoas que trabalham
nativamente no console.  Evite dar talk para estranhos, pois podem fazer uma má
impressão de você.  Tente antes estabelecer outros meios de comunicação.


<listitem>

Se a outra pessoa não responder, não assuma de cara que ela está ignorando você
ou não levando sua conversa muito bem.  Ela pode simplesmente estar ocupada,
trabalhando, ou com problemas no cliente de talk.  Alguns cliente de talk dão
problemas durante a comunicação remota, lembre-se também que sua comunicação é
via UDP :-)


<listitem>

Se a pessoa não responder seus talks durante certo tempo, não deixe ele
infinitamente beepando a pessoa.  Tente mais tarde :-)


<listitem>

Seja atencioso caso utilize mais de uma seção de talk ao mesmo tempo.


<listitem>

O talk também leva em consideração sua habilidade de digitação.  Muitos erros e
correções contínuas fazem a outra pessoa ter uma noção de você, suas
experiências, etc ;-)






 ajuda-netiqueta-listas">###Listas de Discussão via Email
<itemizedlist>
<listitem>

Tente se manter dentro do assunto quando responder mensagens de listas.  Seja
claro e explicativo ao mesmo tempo :-)


<listitem>

Sempre coloque um assunto (subject) na mensagem.  O assunto serve como um
resumo do problema ou dúvida que tem.  Alguns usuários, principalmente os que
participam de várias listas de discussão, verificam o assunto da mensagem e
podem simplesmente descartar a mensagem sem lê-la porque as vezes ele não
conhece sobre aquele assunto.


<listitem>

Nunca use "Socorro!", "Help!"  ou coisa do gênero como assunto, seja objetivo
sobre o problema/dúvida que tem: **"Falha ao carregar módulo no do
kernel"**, **"SMAIL retorna a mensagem Access
denied"**, **"Novidades: Nova versão do guia Foca
Linux"** ;-).


<listitem>

Procure enviar mensagens em formato <literal>texto ao invés de
<literal>HTML para as listas de discussão pois isto faz com que a
mensagem seja vista por todos os participantes (muitos dos usuários
<command>GNU/Linux usam leitores de e-mail que não suportam formato
html) e diminui drásticamente o tamanho da mensagem porque o formato texto não
usa tags e outros elementos que a linguagem HTML contém (muitos dos usuários
costumam participar de várias listas de discussão, e mensagens em HTML levam a
um excesso de tráfego e tempo de conexão).


<listitem>

Tenha cautela e bom censo em suas mensagens para listas e grupos de discussão,
considere que cada mensagem que posta é são arquivadas para futura referência.


<listitem>

Quando o conteúdo das mensagem tomar outro rumo, é ético modificar o assunto do
e-mail para se adequar ao novo conteúdo da mensagem.  Por exemplo,
<literal>Correção nas regras de Netiqueta para <literal>Conversa de
pessoa para pessoa (Era: Correção das regras de Netiqueta).


<listitem>

Quando a conversa em grupo sair do assunto e envolver apenas duas pessoas, é
conveniente retirar os endereços das pessoas/listas do CC.


<listitem>

Não mande arquivos grandes para as listas, principalmente se eles tiverem mais
que 40Kb de tamanho.  Se precisar enviar arquivos maiores que isso, envie
diretamente para os e-mails dos interessados depois de perguntar.


<listitem>

Quando enviar mensagens para listas de discussão, seja educado e cordial quanto
ao conteúdo de sua mensagem.  Envie CC's para as pessoas que dizem respeito ao
assunto, assim com a lista.


<listitem>

Tente ignorar ou não responda mensagens de "Guerras" em listas (**Flame
Wars**), caso queira reponde-la por algum tipo de agressão de quem
mandou a mensagem, esperar para responde-la a noite (nunca é garantida uma boa
resposta no momento que está de cabeça quente).  Lembre-se de quando responde
uma mensagem de "Flame War" a "altura" de quem mandou seus ataques, está sendo
igualmente tão baixo quando o "nível" dessa pessoa.


<listitem>

Caso se desentenda com alguma pessoa em uma lista de discussão, não envie
mensagens agressivas para a listas, se precisar, faça isso diretamente para a
pessoa!  Você pode se arrepender disso mais tarde.


<listitem>

Não culpe o administrador da lista pelos usuários que participam dela.
Notifique somente usuários que não estejam colaborando com a lista e outras
coisas que prejudiquem seu funcionamento.  Administradores preservam o
funcionamento das listas, e não o comportamento dos usuários.


<listitem>

Não use auto respostas para listas de discussão.  Pelos inconvenientes
causados, você pode ser descadastrado ou banido de se inscrever na
lista/newsgroup.


<listitem>

Salve as mensagens de inscrição que recebe da lista.  Ela contém detalhes sobre
seus recursos, e a senha usada muitas vezes para se descadastrar dela ou
modificar suas permissões de usuário.  O administrador pode te ajudar nessa
tarefa, mas não espere que ele esteja sempre disponível para realizar tarefas
que podem ser feitas pelo próprio usuário.


<listitem>

Muitas pessoas reclamam do excesso de mensagens recebidas das listas de
discussão.  Se você recebe muitas mensagens, procure usar os **filtros
de mensagens** para organiza-las.  O que eles fazem é procurar por
campos na mensagem, como o remetente, e enviar para um local separado.  No
final da filtragem, todas as mensagens de listas de discussão estarão em locais
separados e as mensagens enviadas diretamente a você entrarão na caixa de
correio principal, por exemplo.


Um filtro de mensagens muito usado no <command>GNU/Linux é o
<command>procmail, para maiores detalhes consulte a documentação
deste programa.


O Netscape também tem recursos de filtros de mensagem que podem ser criadas
facilmente através da opção "Arquivo/Nova SubPasta" ("File/New Subfolder") do
programa de E-mail.  Então defina as regras através do menu "Editar/Filtros de
Mensagens" ("Edit/Message filters") clicando no botão "Novo"("New").







