<?xml version="1.0" encoding="UTF-8"?>

 s-cvs-intro">###Introdução ao CVS

O CVS (**Concurrent Version Software**) permite que se
organizem grupos de trabalho para desenvolvimento de projetos colaborativos.
Um projeto pode ser desde um programa em C, documentação em equipe, etc.  O uso
do CVS é recomendado para qualquer desenvolvimento de projeto que tenha vários
envolvidos trabalhando ao mesmo tempo.


Para cada mudança feita no programa, é pedido uma descrição dos trabalhos
realizados e o sistema registra todas as modificações realizadas ao longo do
desenvolvimento, permitindo voltar a uma versão anterior ou ver as mudanças
entre elas facilmente.


Imagine uma situação onde você está desenvolvendo um programa de computador e
após a última modificação ele para de funcionar.  Com o CVS é possível ver o
que foi modificado e voltar até a versão que estava funcionando para consertar
o problema.  No desenvolvimento de documentação e tradução o CVS também
desempenha um papel importante, pois com ele o tradutor pode ver o que foi
modificado entre a versão do documento original que ele usou para tradução e
uma versão recente, traduzindo apenas as diferenças.


Uma seção de <command>cvs é feita de modo interativo através do
comando <command>cvs.  Por exemplo:

<itemizedlist>
<listitem>

<literal>logar no sistema - cvs login


<listitem>

<literal>baixar um projeto - cvs checkout projeto




Cada comando do <command>cvs será explicado em detalhes no decorrer
deste capítulo.

 s-cvs-versao">###Versão

A versão do <command>CVS documentada no guia é a
**1.11.1**.  As explicações aqui certamente serão compatíveis
com versões posteriores deste programa.



 s-cvs-historia">###História

O <command>CVS é uma substituição do sistema RCS (Revision Control
System) ele possui mais recursos e foi criado sendo compatível com o RCS.


A história do CVS (extraída de sua info page) é que ele foi iniciado a partir
de um conjunto de scripts shell escritos por **Dick Grune**
que foram postados ao grupo de notícias <literal>comp.sources.unix no
volume 6 de Dezembro de 1986.  Na versão atual não estão mais presentes shell
scripts porque muitos dos conflitos de resolução de algorítmos vem deles.


Em Abril de 1989, **Brian Berliner** fez o design e programou
o CVS.  Mais tarde, Jeff Polk ajudou Brian com o design do módulo CVS.



 s-cvs-contribuindo">###Contribuindo com o CVS

Através da lista de discussão <literal>info-cvs.  Para se inscrever
envie uma mensagem com o subject "subscribe" para
<literal>info-cvs-request@gnu.org.  Outra alternativa é através do
grupo de noticias (newsgroup) da Usenet
<literal>comp.software.config-mgm.



 s-cvs-caracteristicas">###Características

Abaixo uma lista de características que tornam o CVS útil no gerenciamento de
trabalhos em grupo:

<itemizedlist>
<listitem>

Gerenciamento de projeto em equipe


<listitem>

Log de todas as alterações realizadas


<listitem>

Lock de arquivos, permitindo que somente uma determinada pessoa modifique o
arquivo durante o desenvolvimento do projeto.


<listitem>

Histórico de todas as mudanças feitas, isto permite voltar a uma versão
anterior em caso de problemas, e ver o que houve de errado com o código.


<listitem>

Os projetos podem ser hospedados em repositórios.


<listitem>

Podem ser criados diversas equipes de trabalho para cada repositórios, e
definidos quem terá ou não acesso ao repositório individualmente.  O
desenvolvedor <literal>gleydson, por exemplo, podem ter acesso ao
projeto <literal>x_beta e não ter acesso a projeto
<literal>secret_y.


<listitem>

Permissões de acesso individuais de leitura/gravação.


<listitem>

É possível criar um usuário com acesso anônimo sem dar uma conta no sistema.


<listitem>

Pode tanto utilizar o banco de dados de contas/senhas do sistema como um banco
de dados de autenticação do próprio CVS.


<listitem>

Permite utilizar diversos "métodos" de acesso ao servidor:
**local**, **pserver**,
**ext**, etc.  Cada um destes métodos será descrito a seguir.


<listitem>

Permite o acesso via ssh para usuários que já possuam conta na máquina
servidora.  Este método garante segurança no envio da senha criptografada (veja
<xref linkend="d-cripto-sniffer"para detalhes).


<listitem>

Permite visualizar facilmente o que foi modificado entre duas versões de um
arquivo.




**OBS**: O CVS possui algumas limitações e
falhas, uma delas que mais me faz falta é um suporte a protocolo pserver via
ssh que resolveria o problema de tráfego em texto plano e gerenciamento de
grupos com permissões diferenciadas.



 s-cvs-ficha">###Ficha técnica

Pacote: <systemitem role="package">cvs</systemitem>


Utilitários:

<itemizedlist>
<listitem>

<literal>cvs - Servidor/ferramenta cliente.


<listitem>

<literal>cvsbug - Envia um bug sobre o CVS para a equipe de suporte.


<listitem>

<literal>rcs2log - Converte arquivos de log do formato usado pelo
<command>RCS para o <command>CVS.  Utilizado na migração
desta ferramenta para o <command>CVS.


<listitem>

<literal>cvsconfig - Usado pela <command>Debian para
ativar/desativar o servidor <literal>pserver.  Pode também ser usado
o <literal>dpkg-reconfigure cvs para desativar o servidor
<literal>pserver e suas características.


<listitem>

<literal>cvs-makerepos - Script da <command>Debian que lê a
lista de repositórios de <filename>/etc/cvs-pserver.conf</filename>, cria os
repositórios no local apropriado, corrige as permissões do diretório e adiciona
os repositórios no servidor <literal>pserver.


<listitem>

<literal>cvs-pserver - Script da <command>Debian
responsável por fazer uma inicialização mais inteligente do servidor de CVS via
<literal>pserver, leitura e processamento de repositórios, etc.
Normalmente ele é chamado a partir do arquivo
<filename>/etc/inetd.conf</filename>.





 s-cvs-hwreq">###Requerimentos de Hardware

Para executar o <command>CVS é requerido pelo menos 3 vezes mais
memória que o tamanho do maior arquivo usado pelo projeto (para realização de
diffs entre as atualizações) e uma boa quantidade de espaço em disco.


Na realidade os requerimentos sobre o CVS dependem muito da aplicação que será
desenvolvida.  É recomendável que a máquina tenha memória suficiente para
evitar o uso de swap, que degrada bastante a performance do sistema.



 s-cvs-logs">###Arquivos de log criados pelo CVS

Problemas na inicialização do <command>CVS são registrados no arquivo
<filename>/var/log/daemon.log</filename>.  Os logs de modificações feitas nos
arquivos de um projeto no CVS são armazenadas no formato
<filename>arquivo.extensão,v</filename> (é adicionado o ",v" ao final do
arquivo para indicar que é um arquivo de controle de modificações do CVS).



 s-cvs-install">###Instalação

O <command>CVS pode ser baixado de ("http://www.w3.org/1999/xlink) [](http://www.cvshome.org)http://www.cvshome.org/.


Para pacotes <command>Debian basta apenas executar o comando:
<literal>apt-get install cvs e seguir as telas de configuração para
ter o pacote <command>CVS instalado e (opcionalmente) com o servidor
sendo executado.  Você poderá a qualquer momento reconfigurar o
<command>CVS executando: <literal>dpkg-reconfigure cvs.


Uma boa documentação de referência é encontrada no pacote <systemitem role="package">cvs-doc</systemitem>.



 s-cvs-rodando">###Iniciando o servidor/reiniciando/recarregando a configuração

A única configuração requerida é quando o <command>CVS é executado
via <literal>pserver.  Para isto, é necessária a seguinte linha no
arquivo <filename>/etc/inetd.conf</filename>

<screen>
cvspserver      stream  tcp     nowait.200      root    /usr/sbin/tcpd /usr/sbin/cvs-pserver


Note que o parâmetro "200" indica quantas vezes o processo
<command>CVS poderá ser executado por minuto no sistema.  Caso esse
número seja excedido, o serviço será desabilitado e será necessário reiniciar o
servidor <command>inetd com o comando <literal>killall -HUP
inetd para reativar o servidor CVS pserver (veja <xref linkend="rede-servicos-inetd-c"capítulo do <command>inetd para
detalhes).  Ajuste este valor de forma adequada ao seu servidor!


Veja o script <filename>cvs-pserver</filename> sendo executado no final da
linha.  Ele foi desenvolvido para lidar de forma mais inteligente com a
configuração do servidor CVS pserver.



 s-cvs-opcoescmd">###Opções de linha de comando

As seguintes opções são aceitas pelo CVS.

<variablelist>
<varlistentry>
<term>-z [num]
<listitem>

Utiliza o gzip para fazer a transferência compactada dos arquivos.  O valor
especificado pode ser de 0 a 9, quanto maior o número maior o nível de
compactação e uso da CPU.


Exemplo: <literal>cvs -z 3 checkout teste



<varlistentry>
<term>-q
<listitem>

Oculta mensagens sobre recursão de diretório durante os comandos do CVS.



<varlistentry>
<term>-d [repositório]
<listitem>

Permite especificar o repositório através da linha de comando.



<varlistentry>
<term>-e [editor]
<listitem>

Define qual é o editor de textos usado para registrar o texto de commits.



<varlistentry>
<term>-n
<listitem>

Executa o cvs em modo "simulação" não modificando qualquer arquivo do
repositório.



<varlistentry>
<term>-t
<listitem>

Mostra mensagens mostrando o processo de execução de comandos do CVS.  É
bastante útil para aprendizado do cvs usado junto com a opção
**-n**.



<varlistentry>
<term>-r
<listitem>

Torna os novos arquivos criados somente para leitura.  É a mesma coisa que
especificar a variável <replaceable>CVSREAD</replaceable>.



<varlistentry>
<term>-w
<listitem>

Torna os novos arquivos criados leitura/gravação que é o padrão.



<varlistentry>
<term>-x
<listitem>

Utiliza criptografia para a transferência dos arquivos quando é utilizado em
conjunto com o <command>Kerberos.



</variablelist>

Você pode obter detalhes sobre opções sobre um comando em especial do CVS
(**commit**, **checkout**, etc) digitando:
<literal>cvs comando --help.  Veja <xref linkend="s-cvs-p"para
exemplos sobre cada uma delas.





