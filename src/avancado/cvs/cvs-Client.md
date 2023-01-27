<?xml version="1.0" encoding="UTF-8"?>

 s-cvs-c">###Clientes de CVS

Esta seção traz alguns programas cliente em modo texto/gráfico e visualizadores
de repositórios via web.  Eles facilitam o trabalho de controle de revisão por
parte de iniciantes e flexibilidade para pessoas mais experientes, além de ter
uma interface de navegação disponível para todos os interessados em fazer
pesquisas no repositório.

 s-cvs-c-cvs">###cvs

Este é o cliente <command>Unix padrão, bastante poderoso e que opera
em modo texto.  As explicações neste capítulo do guia assumem este cliente de
<command>cvs, então as explicações sobre sua utilização se encontra
em <xref linkend="s-cvs-p"e os parâmetros de linha de comando em <xref linkend="s-cvs-opcoescmd"/>


É **altamente** recomendável a leitura caso
deseje utilizar um cliente de <command>cvs gráfico, pois os conceitos
são os mesmos.



 s-cvs-c-gcvs">###gcvs - Linux

Este é um cliente CVS em GTK+Python para <command>Linux que interage
externamente com o cliente <command>cvs externo, todas as opções do
cvs estão disponíveis através de checkboxes nas telas de comando, incluindo
suporte a compactação, visualizador gráfico da árvore de releases, histórico,
diffs, etc.


Sua instalação é bastante fácil, instale o programa com <literal>apt-get
install gcvs e execute o programa através do menu do sistema ou do
terminal.  Utilize os seguintes procedimentos para configurar e utilizar o
programa:

<orderedlist numeration="arabic">
<listitem>

Defina o repositório <replaceable>CVSROOT</replaceable> através do menu
**Admin**/**Preferences**.  Selecione o
método de acesso, entre com o login, servidor e repositório.

<screen>
Exemplo: :pserver:anonymous@servidor:/var/lib/cvs


O formato deve ser **EXATAMENTE** como o usado na variável
CVSROOT no shell, incluindo os ":".  Caso tenha erros de login, verifique o
valor de <replaceable>CVSROOT</replaceable> cuidadosamente antes de contactar o
administrador de sistemas!


<listitem>

Agora faça o login no sistema em: **Admin**,
**Login**.  Note que o status de todas as operações do
<command>cvs são mostradas na janela de status que fica na parte
inferior da tela.


<listitem>

Crie um diretório que será usado para armazenar os fontes baixados do CVS, por
exemplo: <literal>mkdir ~/projetos


<listitem>

Acesse o menu **Create**, **Checkout Module**
para baixar o projeto do CVS para sua máquina local.  Ele irá te pedir o nome
de diretório para onde o código fonte do servidor CVS será baixado.  Digite
<filename>~/projetos</filename> ou outro diretório que foi criado no passo
anterior.


**OBS:** Não utilize o nome
<filename>"cvs"</filename> para o diretório local, pois o
<command>gcvs oculta automaticamente pois os arquivos administrativos
de controle ficam neste local.


<listitem>

Altere o diretório padrão do <command>gcvs para o diretório onde
baixou o projeto (<filename>~/projetos</filename>)clicando no botão "set" no
topo da coluna esquerda do <command>gcvs.


<listitem>

Para enviar um arquivo modificado de volta ao servidor, selecione os arquivos,
clique em **Modify**, **Commit Selection**,
entre com a mensagem descrevendo as alterações e clique em "OK".


Note que os arquivos modificados serão identificados por um ícone vermelho e
seu status será "Mod.  File" (arquivo modificado).


<listitem>

Se desejar adicionar um novo projeto no CVS, entre em
**Create**, **Import Module**, entre no
diretório que deseja adicionar como um projeto no servidor de CVS.  Após isto
será feita uma checagem e mostrada uma tela de possíveis problemas que podem
ocorrer durante a importação do novo projeto.


Na próxima tela, digite o nome do módulo e caminho no servidor remoto no
primeiro campo, no segundo campo a mensagem de log para adicionar o projeto ao
servidor.  Em "Vendor tag" especifique o nome do projeto e sua versão logo
abaixo.  Clique em "OK" e aguarde a transferência dos arquivos para o servidor.


Para maiores detalhes sobre a criação de novos projetos no servidor de CVS,
veja <xref linkend="s-cvs-p-import"/>.


**OBS:** Você deverá ter permissão de gravação
para criar um novo projeto no servidor CVS.


<listitem>

A partir de agora você poderá explorar as funções do programa e fazer uso das
funções habituais do CVS.  Todas as funções de operação e opções extras do CVS
estão disponíveis na interface gráfica, basta se acostumar com sua utilização.


</orderedlist>

Após isto, explore bastante as opções do programa.  Todas as funcionalidades do
CVS estão organizadas entre os menus do programa.  Caso não entenda bem as
funções do programa, leia atentamente <xref linkend="s-cvs-p"e também não
deixe de consultar detalhes na info page do cvs.



 s-cvs-c-wincvs">###WinCVS - Windows

Este é um cliente CVS em Python para <command>Windows equivalente ao
<command>gcvs para <command>Linux.  Suas funcionalidades e
recomendações são idênticas aos do <command>gcvs.  Este cliente pode
ser baixado de: ("http://www.w3.org/1999/xlink) [](http://telia.dl.sourceforge.net/sourceforge/cvsgui/WinCvs13b13.zip">http://telia.dl.sourceforge.net/sourceforge/cvsgui/WinCvs13b13.zip
e o Python para Windows de ("http://www.w3.org/1999/xlink) [](http://starship.python.net/crew/mhammond/downloads/win32all-153.exe">http://starship.python.net/crew/mhammond/downloads/win32all-153.exe.


Para sua utilização, as explicações em <xref linkend="s-cvs-c-gcvs"são
totalmente válidas.



 s-cvs-c-maccvs">###MacCVS - Macintosh (PPC)

Idêntico ao <command>gcvs, pode ser baixado de ("http://www.w3.org/1999/xlink) [](http://telia.dl.sourceforge.net/sourceforge/cvsgui/MacCvsX-3.3a1-1.dmg">http://telia.dl.sourceforge.net/sourceforge/cvsgui/MacCvsX-3.3a1-1.dmg.



 s-cvs-c-viewcvs">###viewcvs

Este é um visualizador de repositórios CVS via web, ele precisa apenas de um
servidor web instalado com suporte a CGI.  Para instalar, execute o comando
<literal>apt-get install <systemitem role="package">viewcvs</systemitem> e siga os passos para configurar
programa.  Para adequar melhor o <command>viewcvs ao seu sistema,
edite o arquivo <filename>/etc/viewcvs/viewcvs.conf</filename>.


O <command>viewcvs possui uma interface que se parece com a navegação
de um diretório de ftp, recursos como a extração de diffs coloridos entre
versões de um arquivo selecionado, visualização de commits (com data, log do
commit, usuário, etc.), classificação da listagem exibida.


**OBS:**Leve em consideração as implicações de
segurança impostas por aplicativos cgi sendo executados em seu sistema.  Veja
<xref linkend="apache"para entender melhor o assunto.





