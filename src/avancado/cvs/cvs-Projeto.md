<?xml version="1.0" encoding="UTF-8"?>

 s-cvs-p">###Criando projetos para serem usados no CVS

Esta seção descreve todos os passos necessários para colocação de um projeto
para ser desenvolvido através do CVS, os comandos do cvs, considerações a
respeito dos comandos e sua utilização através de exemplos didáticos.

 s-cvs-p-repos">###Repositório

Um repositório CVS é o local que armazena módulos e também os arquivos
administrativos (que contém permissões, etc) são armazenados em um subdiretório
chamado <filename>CVSROOT</filename>.


O acesso a um repositório é feito através de parâmetros especificados na
variável <replaceable>CVSROOT</replaceable> ou pela opção **-d
repositório** do cvs.  Veja <xref linkend="s-cvs-d"para ver
exemplos de métodos de acesso.


O Repositório pode conter um ou mais módulos, cada módulo representa um projeto
no servidor, criado após o uso do comando <literal>import.  Segue um
exemplo da estrutura de um repositório CVS:

<screen>
var/lib
     |
     +- cvs
         |- CVSROOT
         |- projeto1
         +- projeto2


O subdiretório <filename>cvs</filename> é o repositório (veja o subdiretório
<filename>CVSROOT</filename> dentro dele) e os diretórios dentro dele
<filename>projeto1</filename> e <filename>projeto2</filename> são os módulos
criados através do comando <literal>cvs import ...(veja <xref linkend="s-cvs-p-import"/>).


Para acessar o projeto do CVS, então é definido o repositório que tem
permissões de acesso na variável <literal>CVSROOT e então é executado
um comando (checkout, update, commit, etc) no módulo que desejamos utilizar:

<screen>
export CVSROOT=:ext:anonymous@servidor.org.br:/var/lib/cvs (&lt;- Repositório "cvs")
cvs checkout projeto1 (&lt;- módulo que desejamos pegar do servidor)


Nas seções seguintes serão explicados cada um dos comandos usados para
trabalhar com um projeto no <command>cvs.



 s-cvs-p-mkrepos">###Criando um repositório

Para adicionar um novo repositório no sistema, edite o arquivo
<filename>/etc/cvs-pserver.conf</filename> e defina o nome de cada repositório
na variável <replaceable>CVS_PSERV_REPOS</replaceable> separados por ":"
(exemplo: <literal>CVS_PSERV_REPOS="/var/lib/cvs:/var/lib/cvs2").


Feito isso execute o comando <command>cvs-makerepos para que os
diretórios especificados no arquivo <filename>/etc/cvs-pserver.conf</filename>
sejam criados com as devidas permissões.


Para adicionar manualmente um repositório (/var/lib/cvs), execute os seguintes
passos:

<orderedlist numeration="arabic">
<listitem>

Execute o comando <literal>cvs -d /var/lib/cvs init (para criar o
repositório e os arquivos administrativos que ficam armazenados dentro de
<filename>CVSROOT</filename>.


<listitem>

Mude as permissões do diretório para sgid com: <literal>chmod 2775
/var/lib/cvs.


<listitem>

Mude o dono/grupo com o comando: <literal>chown root.src /var/lib/cvs


<listitem>

Opcional: caso utilize o método de acesso **pserver** será
necessário adicionar a opção <literal>--allow-root=/var/lib/cvs na
linha que inicia o servidor pserver.  Este parâmetro deve ser usada para cada
repositório adicionado no servidor.


</orderedlist>

A partir de agora, seu repositório já está pronto para ser utilizado.



 s-cvs-p-login">###Logando no servidor de CVS via pserver

Quando é usado o método de acesso pserver (<xref linkend="s-cvs-d-metodos-pserver"/>), é necessário fazer para ter acesso ao
repositório.  Por exemplo, para acessar o repositório
<filename>/var/lib/cvs</filename> no servidor
<filename>servidor.org.br</filename>:

<screen>
export CVSROOT=:pserver:anonymous@servidor.org.br:/var/lib/cvs
cvs login

ou 

cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs login


Então será solicitada a senha para ter acesso ao sistema.  Note que toda a
seção de <command>cvs ocorre por comandos interativos que logo após
concluídos retornam para o interpretador de comandos.  O restante desta seção
descreverá estes comandos e como utiliza-los de maneira eficiente.


**OBS:** O uso da variável
<replaceable>CVSROOT</replaceable> torna a utilização bastante prática, assim
não precisamos especificar o repositório, método de acesso, etc.  toda vez que
usar um comando do <command>cvs.



 s-cvs-p-logout">###Encerrando uma seção de CVS

Embora que não seja necessário, após o uso do cvs é recomendável executar o
logout do servidor para encerrar sua conexão com a máquina remota.

<screen>
# (assumindo que a variável CVSROOT está definida)
cvs logout

ou 

cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs logout


**OBS:** Para os paranóicos é importante
encerrar uma seção de CVS, pois ele possui alguns bugs e um spoofing pode
tornar possível o uso de uma seção deixada aberta.



 s-cvs-p-checkout">###Baixando arquivos

O comando <literal>checkout (ou "co") é usado para fazer isto.  Para
utilizá-lo seguindo os exemplos anteriores:

<screen>
mkdir /tmp/cvs
cd /tmp/cvs
cvs checkout modulo
cvs -d :pserver:anonymous@servidor.org.br:/var/lib/cvs


Será criado um subdiretório chamado <filename>modulo</filename> que contém
todos os arquivos do servidor de CVS remoto.  É necessário apenas que tenha
acesso de leitura ao servidor de CVS para executar este comando.  Você pode
usar a opção <literal>-z [num] para ativar a compactação na
transferência dos arquivos, isso acelera bastante a transferência em conexões
lentas: <literal>cvs -z 3 checkout modulo.


Também é possível especificar apenas subdiretórios de um módulo para baixa-lo
via CVS e a estrutura de diretórios criada localmente será idêntica ao do
servidor remoto.



 s-cvs-p-import">###Adicionando um novo projeto

Use o comando <literal>cvs import para adicionar um novo projeto ao
CVS.  As entradas nos arquivos administrativos serão criadas e o projeto estará
disponível para utilização dos usuários.  A sintaxe básica do comando
<literal>import é a seguinte:


<literal>cvs import [**opções**]
[**dir_modulo**] [**tag**] start


Para adicionar o projeto <literal>focalinux que reside em
<filename>/usr/src/focalinux</filename> ao cvs:

<screen>
# Primeiro exportamos o CVSROOT para dizer onde e qual repositório acessar
export CVSROOT=:ext:usuario@servidor.com.br:2401/var/lib/cvs

cd /usr/src/focalinux
cvs import documentos/focalinux tag_modulo start


Por padrão o <command>import sempre utiliza a máscara
***** para fazer a importação dos arquivos do diretório atual.
O projeto <literal>focalinux será acessado através de
$CVSROOT/documentos/focalinux (<literal>cvs checkout
documentos/focalinux), ou seja,
<filename>/var/lib/cvs/documentos/focalinux</filename> no servidor CVS terá a
cópia do focalinux.  <literal>tag_modulo define o nome que será usado
como identificador nas operações com os arquivos do CVS (pode ser usado
"focalinux" em nosso exemplo).  O parâmetro "start" diz para criar o módulo.


**OBS:** Por segurança, o diretório que contém
os arquivos deverá ser sempre um caminho relativo na estrutura de diretórios,
ou seja, você precisará entrar no diretório pai (como
<filename>/usr/src/projeto</filename>) para executar o <literal>cvs
import.  Não é permitido usar <literal>/ ou
<literal>.., isto proíbe a descida em diretórios de nível mais altos
e sérios incidentes de segurança em servidores CVS mal configurados pelo
Administrador.



 s-cvs-p-update">###Sincronizando a cópia remota com a cópia local

Este comando sincroniza a cópia remota do CVS (ou arquivo) com a cópia local
que está trabalhando em sua máquina.  Quando se trabalha nativamente no CVS em
equipe é recomendado a utilização deste comando pois alguém pode ter modificado
o arquivo antes de você, então uma incompatibilidade entre sua versão e a nova
poderia causar problemas.


Supondo que tenha acabado de modificar o arquivo <filename>main.c</filename> do
módulo <filename>cvsproj</filename>, então antes de fazer o commit (<xref linkend="s-cvs-p-commit"/>) use o update:

<screen>
cvs update main.c

ou 

cvs -d :ext:usuario@servidor.com.br:2401/var/lib/cvs update main.c


Após alguns segundos, sua cópia local ficará sincronizada com a cópia remota.
Caso ele mostre alguma mensagem de saída, verifique o arquivo para solucionar
qualquer conflito e então envie o arquivo para o servidor remoto (<xref linkend="s-cvs-p-commit"/>).


Você pode fazer o update de mais arquivos usando referências globais
(<literal>*, <literal>? ou <literal>[]).



 s-cvs-p-commit">###Enviando as mudanças para o servidor remoto

O comando "commit" (ou "ci"), envia as mudanças feitas nos arquivos locais para
o servidor remoto.  Um exemplo de commit no arquivo
<filename>main.c</filename>:

<screen>
cvs commit main.c

cvs commit main.?

cvs commit *


O editor padrão do sistema será aberto e pedirá uma descrição das modificações
para o commit.  Esta descrição será usada como referência sobre as atualizações
feitas em cada etapa do desenvolvimento.  A mensagem também pode ser
especificada usando a opção "-m mensagem", principalmente quando o texto
explicando as alterações é pequeno.


Para mudar o editor de texto padrão que será usado pelo <command>cvs,
altere a variável de ambiente <replaceable>EDITOR</replaceable> ou especifique
o editor que deseja usar na linha de comando com a opção "-e editor":

<screen>
cvs commit -e vi main.c



 s-cvs-p-add">###Adicionando um arquivo ao módulo CVS do servidor

Após criar/copiar o arquivo para seu diretório de trabalho, use o comando
<literal>add para fazer isto.  O arquivo será enviado ao servidor,
bastando apenas executa o <literal>commit para salvar o arquivo:

<screen>
cvs add main.h
cvs commit main.h



 s-cvs-p-add-dir">###Adicionando um diretório ao módulo CVS do servidor

O método para adicionar um diretório com arquivos é semelhante ao de adicionar
apenas arquivos ao cvs.  O único ponto que deve se seguido é que primeiro deve
ser adicionado o diretório (com o "cvs add") salvar no servidor remoto ("cvs
commit") e depois adicionar os arquivos existentes dentro dele (assim como
descrito em <xref linkend="s-cvs-p-add"/>).  Para adicionar o diretório
<filename>teste</filename> e seus arquivos no servidor <command>cvs
remoto:

<screen>
cvs add teste
cvs commit -m "Adicionado" teste
cvs add teste/*
cd teste
cvs commit -m "Adicionados" .


Os dois primeiros comandos agendam o diretório <filename>teste</filename> e
fazem o <literal>commit no diretório remoto.  Os dois últimos, enviam
os arquivos existentes dentro deste diretório para o servidor remoto.



 s-cvs-p-remove">###Removendo um arquivo do módulo CVS remoto

O comando para fazer isto é o "remove".  Primeiro use o <command>rm
para remover o arquivo/diretório de sua cópia local, depois execute o
<literal>remove seguido de commit para confirmar a remoção do
arquivo:

<screen>
cvs remove main.h
cvs commit main.h



 s-cvs-p-removed">###Removendo um diretório do módulo CVS remoto

Para remover um diretório, primeiro remova todos os arquivos existentes dentro
dele com o comando <command>rm e salve para o servidor (seguindo os
métodos descritos em <xref linkend="s-cvs-p-remove"/>).  O CVS não remove
diretamente diretórios vazios, uma maneira de contornar isto é usar o
<literal>update ou <literal>commit seguido da opção
<literal>-P para ignorar diretórios vazios.  Então a cópia remota do
diretório será removida do servidor:

<screen>
rm -f teste/*
cvs remove teste/.
cvs commit teste/.
cd ..
cvs checkout modulo


Depois do checkout, o subdiretório teste terá sido removido.



 s-cvs-p-release">###Dizendo que o módulo atual não está mais em uso

O comando "release" faz esta função.  Ele não é requerido, mas caso você tenha
feito modificações que ainda não foram salvas no servidor de cvs
(<literal>commit), ele alertará de arquivos modificados e perguntará
se deseja continuar.  Registrando também o abandono das modificações no
histórico do <command>cvs.  O comando pode ser acompanhado de "-d"
para remover o módulo anteriormente baixado com o "commit":

<screen>
cvs release modulo

cvs release -d modulo


O <literal>release retorna os seguintes códigos quando verifica que
as duas cópias (local e remota) não estão sincronizadas:

<variablelist>
<varlistentry>
<term>U ou P
<listitem>

Existe uma versão nova do arquivo no repositório.  Para corrigir isso, execute
o comando "update".



<varlistentry>
<term>A
<listitem>

O arquivo não foi adicionado ainda ao repositório remoto.  Se apagar o
repositório local, este arquivo não será adicionado.  Para corrigir isto,
executa o comando "add" do cvs.



<varlistentry>
<term>R
<listitem>

O arquivo foi removido localmente, mas não foi removido do servidor remoto.
Use os procedimentos em <xref linkend="s-cvs-p-remove"para corrigir a
situação.



<varlistentry>
<term>M
<listitem>

O arquivo está modificado localmente e não foi salvo ainda no servidor.  Use os
procedimentos em <xref linkend="s-cvs-p-update"e <xref linkend="s-cvs-p-commit"para salvar o arquivo.



<varlistentry>
<term>?
<listitem>

O arquivo está em seu diretório de trabalho mas não tem referências no
repositório remoto e também não está na lista de arquivos ignorados do CVS.



</variablelist>


 s-cvs-p-diff">###Visualizando diferenças entre versões de um arquivo

Com o comando "diff" é possível visualizar que diferenças o arquivo que está
sendo editado possui em relação ao arquivo do repositório remoto.  Outra
funcionalidade útil do "diff" é comparar 2 versões de arquivos do mesmo
repositório CVS.  Exemplos:

<variablelist>
<varlistentry>
<term>cvs diff main.c
<listitem>

Verifica as diferenças entre o arquivo <filename>main.c</filename> local e
remoto.



<varlistentry>
<term>cvs diff -u -r 1.1 -r 1.2 main.c
<listitem>

Mostra as diferenças em formato unificado para mostrar as diferenças entre as
versões 1.1 e 1.2 do arquivo <filename>main.c</filename>.



</variablelist>


 s-cvs-p-status">###Visualizando o status de versão de arquivos

O comando "status" permite verificar que versões do arquivo especificado está
disponível localmente, remotamente, qual a versão inicial do arquivo no
repositório, sticky tag.  Exemplos:

<variablelist>
<varlistentry>
<term>cvs status main.c
<listitem>

Verifica o status do arquivo <filename>main.c</filename>.



<varlistentry>
<term>cvs status -v main.c
<listitem>

Mostra o status do arquivo <filename>main.c</filename>, adicionalmente mostra
também as tags existentes no arquivo (versão inicial, versão do repositório).



</variablelist>


 s-cvs-p-utils">###Outros utilitários para trabalho no repositório

Além dos comandos do <command>cvs descritos aqui, existem comandos no
pacote <systemitem role="package">cvsutils</systemitem> que auxiliam desde quem
está aprendendo a utilizar o CVS (com o comando <command>cvsdo para
simular algumas operações de adição/remoção de arquivos) até profissionais que
usam o programa no dia a dia (<command>cvsu,
<command>cvsco, <command>cvschroot).





