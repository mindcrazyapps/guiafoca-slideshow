<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cmdc">###Comandos para manipulação de contas

Este capítulo traz comandos usados para manipulação de conta de usuários e
grupos em sistemas <command>GNU/Linux.  Entre os assuntos descritos
aqui estão adicionar usuários ao sistema, adicionar grupos, incluir usuários em
grupos existentes, etc.



 cmdc-adduser">###adduser

Adiciona um usuário ou grupo no sistema.  Por padrão, quando um novo usuário é
adicionado, é criado um grupo com o mesmo nome do usuário.  Opcionalmente o
<command>adduser também pode ser usado para adicionar um usuário a um
grupo (veja <xref linkend="cmdc-incluirgrupo"/>).  
<!-- [ %DESCRICAOD [ --> Será criado um diretório
home com o nome do usuário (a não ser que o novo usuário criado seja um usuário
do sistema) e este receberá uma identificação.  A identificação do usuário
(UID) escolhida será a primeira disponível no sistema especificada de acordo
com a faixa de UIDS de usuários permitidas no arquivo de configuração
<filename>/etc/adduser.conf</filename>.  Este é o arquivo que contém os padrões
para a criação de novos usuários no sistema. <!-- ]]> -->


<command>adduser [**opções**]
[**usuário/grupo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**usuário/grupo**
<listitem>

Nome do novo usuário que será adicionado ao sistema.



<varlistentry>
<term>**opções**
<term>-disable-passwd
<listitem>

Não executa o programa <command>passwd para escolher a senha e
somente permite o uso da conta após o usuário escolher uma senha.



<varlistentry>
<term>--force-badname
<listitem>

Desativa a checagem de senhas ruins durante a adição do novo usuário.  Por
padrão o <command>adduser checa se a senha pode ser facilmente
adivinhada.



<varlistentry>
<term>--group
<listitem>

Cria um novo grupo ao invés de um novo usuário.  A criação de grupos também
pode ser feita pelo comando <command>addgroup.



<varlistentry>
<term>-uid [num]
<listitem>

Cria um novo usuário com a identificação [num] ao invés de procurar o próximo
UID disponível.



<varlistentry>
<term>-gid [num]
<listitem>

Faz com que o usuário seja parte do grupo [gid] ao invés de pertencer a um novo
grupo que será criado com seu nome.  Isto é útil caso deseje permitir que
grupos de usuários possam ter acesso a arquivos comuns.


Caso estiver criando um novo grupo com <command>adduser, a
identificação do novo grupo será [num].



<varlistentry>
<term>--home [dir]
<listitem>

Usa o diretório [dir] para a criação do diretório home do usuário ao invés de
usar o especificado no arquivo de configuração
<filename>/etc/adduser.conf</filename>.



<varlistentry>
<term>--ingroup [nome]
<listitem>

Quando adicionar um novo usuário no sistema, coloca o usuário no grupo [nome]
ao invés de criar um novo grupo.



<varlistentry>
<term>--quiet
<listitem>

Não mostra mensagens durante a operação.



<varlistentry>
<term>--system
<listitem>

Cria um usuário de sistema ao invés de um usuário normal.



</variablelist>
<!-- ]]> -->

Os dados do usuário são colocados no arquivo <filename>/etc/passwd</filename>
após sua criação e os dados do grupo são colocados no arquivo
<filename>/etc/group</filename>.

<!-- [ %OBS [ -->

OBSERVAÇÃO: Caso esteja usando senhas ocultas (shadow passwords), as senhas dos
usuários serão colocadas no arquivo <filename>/etc/shadow</filename> e as
senhas dos grupos no arquivo <filename>/etc/gshadow</filename>.  Isto aumenta
mais a segurança do sistema porque somente o usuário <literal>root
pode ter acesso a estes arquivos, ao contrário do arquivo
<filename>/etc/passwd</filename> que possui os dados de usuários e devem ser
lidos por todos.

<!-- ]]> -->



 cmdc-addgroup">###addgroup

Adiciona um novo grupo de usuários no sistema.  As opções usadas são as mesmas
do <xref linkend="cmdc-adduser"/>.


<command>addgroup [**usuário/grupo**]
[**opções**]




 cmdc-passwd">###passwd

Modifica a parametros e senha de usuário.  
<!-- [ %DESCRICAOD [ --> Um usuário somente pode alterar a
senha de sua conta, mas o superusuário (<literal>root) pode alterar a
senha de qualquer conta de usuário, inclusive a data de validade da conta, etc.
Os donos de grupos também podem alterar a senha do grupo com este comando.


Os dados da conta do usuário como nome, endereço, telefone, também podem ser
alterados com este comando.

<!-- ]]> -->

<command>passwd [**usuário**]
[**opções**]

<!-- [ %OPCOES [ --> 

Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome do usuário que terá sua senha alterada.



<varlistentry>
<term>**opções**
<term>-e
<listitem>

Força a expiração de senha para a conta especificada.



<varlistentry>
<term>-k
<listitem>

Somente altera a senha se a conta estiver expirada.



<!-- [ %INTER-AVANC [ --> 
<varlistentry>
<term>-x [dias]
<listitem>

Especifica o número máximo de dias que a senha poderá ser usada.  Após terminar
o prazo, a senha deverá ser modificada.



<varlistentry>
<term>-i
<listitem>

Desativa a conta caso o usuário não tenha alterado sua senha após o tempo
especificado por -x.



<varlistentry>
<term>-n [dias]
<listitem>

Especifica o número mínimo de dias para a senha ser alterada.  O usuário não
poderá mudar sua senha até que [dias] sejam atingidos desde a última alteração
de senha.



<varlistentry>
<term>-w [num]
<listitem>

Número de dias antecedentes que o usuário receberá o alerta para mudar sua
senha.  O alerta ocorre [num] dias antes do limite da opção -x, avisando ao
usuários quantos dias restam para a troca de sua senha.



<varlistentry>
<term>-l [nome]
<listitem>

Bloqueia a conta do usuário [nome].  Deve ser usada pelo root.  O bloqueio da
conta é feito acrescentando um caracter a senha para que não confira com a
senha original.



<varlistentry>
<term>-u [nome]
<listitem>

Desbloqueia a conta de um usuário bloqueada com a opção -l.



<varlistentry>
<term>-S [nome]
<listitem>

Mostra o status da conta do usuário [nome].  A primeira parte é o nome do
usuário seguido de L(conta bloqueada), NP(sem senha), ou P (com senha), a
terceira parte é a data da última modificação da senha, a quarta parte é a
período mínimo, máximo, alerta e o período de inatividade para a senha.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

Procure sempre combinar letras maiúsculas, minúsculas, e números ao escolher
suas senhas.  Não é recomendado escolher palavras normais como sua senha pois
podem ser vulneráveis a ataques de dicionários cracker.  Outra recomendação é
utilizar **senhas ocultas** em seu sistema (**shadow
password**).

<!-- [ %OBS [ --> 

Você deve ser o dono da conta para poder modificar a senhas.  O usuário root
pode modificar/apagar a senha de qualquer usuário.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>passwd root.

<!-- ]]> -->



 cmdc-gpasswd">###gpasswd

Modifica parametros e senha de grupo.  
<!-- [ %DESCRICAOD [ --> Um usuário somente pode alterar a senha
de seu grupo, mas o superusuário (<literal>root) pode alterar a senha
de qualquer grupo de usuário, inclusive definir o administrador do grupo. <!-- ]]> -->


<command>gpasswd [**opções**] [**usuario**]
[**grupo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome do usuário/grupo que terá sua senha alterada.



<varlistentry>
<term>**opções**
<term>-r **usuario** **grupo**
<listitem>

Remove a senha de grupo.



<varlistentry>
<term>-R **usuario** **grupo**
<listitem>

Desativa o acesso do grupo usando o comando <command>newgrp.



<varlistentry>
<term>-a **usuario** **grupo**
<listitem>

Adiciona o usuário no grupo especificado.



<varlistentry>
<term>-d **usuario** **grupo**
<listitem>

Apaga o usuário do gurpo especificado.



<!-- [ %INTER-AVANC [ -->
<varlistentry>
<term>-A [usuario] [grupo]
<listitem>

Define que o **[usuario]** será o administrador do
**[grupo]**.



<varlistentry>
<term>-M [usuario] [grupo]
<listitem>

Define os usuários que fazem parte do **grupo** e suas
permissões.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

Quando o grupo não possui senha, somente quem faz parte do grupo pode utilizar
o comando new-grp.

<!-- [ %OBS [ -->

Você deve ser o dono da conta para poder modificar a senhas.  O usuário root
pode modificar/apagar a senha de qualquer usuário.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>gpasswd grupo, <literal>gpasswd -a gleydson
grupo.

<!-- ]]> -->



 cmdc-newgrp">###newgrp

Altera a identificação de grupo do usuário.  
<!-- [ %DESCRICAOD [ --> Para retornar a identificação
anterior, digite <literal>exit e tecle <literal>Enter.
Para executar um comando com outra identificação de grupo de usuário, use o
comando <xref linkend="cmdc-sg"/>. <!-- ]]> -->


<command>newgrp **-** [**grupo**]


Onde:

<variablelist>
<varlistentry>
<term>**-**
<listitem>

Se usado, inicia um novo ambiente após o uso do comando
<command>newgrp (semelhante a um novo login no sistema), caso
contrário, o ambiente atual do usuário é mantido.



<varlistentry>
<term>**grupo**
<listitem>

Nome do grupo ou número do grupo que será incluído.



</variablelist>

Quando este comando é usado, é pedida a senha do grupo que deseja acessar.
Caso a senha do grupo esteja incorreta ou não exista senha definida, a execução
do comando é negada.  A listagem dos grupos que pertence atualmente pode ser
feita usando o comando <xref linkend="cmdc-id"/>.




 cmdc-userdel">###userdel

Apaga um usuário do sistema.  
<!-- [ %DESCRICAOD [ --> Quando é usado, este comando apaga todos os dados
da conta especificado dos arquivos de contas do sistema. <!-- ]]> -->


<command>userdel [**-r**] [**usuário**]

<!-- [ %OPCOES [ --> 

Onde:

<variablelist>
<varlistentry>
<term>-r
<listitem>

Apaga também o diretório HOME do usuário.



</variablelist>
<!-- ]]> -->
<!-- [ %OBS [ --> 

OBS: Note que uma conta de usuário não poderá ser removida caso ele estiver no
sistema, pois os programas podem precisar ter acesso aos dados dele (como UID,
GID) no <filename>/etc/passwd</filename>.

<!-- ]]> -->



 cmdc-groupdel">###groupdel

Apaga um grupo do sistema.  
<!-- [ %DESCRICAOD [ --> Quando é usado, este comando apaga todos os dados
do grupo especificado dos arquivos de contas do sistema. <!-- ]]> -->


<command>groupdel [**grupo**]


Tenha certeza que não existem arquivos/diretórios criados com o grupo apagado
através do comando <command>find.

<!-- [ %OBS [ -->

OBS: Você não pode remover o grupo primário de um usuário.  Remova o usuário
primeiro.

<!-- ]]> -->


    <!-- [ %INTER-AVANC [ -->
 cmdc-lastlog">###lastlog

Mostra o último login dos usuários cadastrados no sistema.  
<!-- [ %DESCRICAOD [ --> É mostrado o nome usado no login, o terminal onde 
ocorreu a conexão e a hora da última conexão.
Estes dados são obtidos através da pesquisa e formatação do arquivo
<filename>/var/log/lastlog</filename>.  Caso o usuário não tenha feito login, é
mostrada a mensagem <literal>** Never logged in **. <!-- ]]> -->


<command>lastlog [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-t [dias]
<listitem>

Mostra somente os usuários que se conectaram ao sistema nos últimos [dias].



<varlistentry>
<term>-b [dias]
<listitem>

Mostra somente os usuários que se conectaram antes de [dias].



<varlistentry>
<term>-u [nome]
<listitem>

Mostra somente detalhes sobre o usuário [nome].



</variablelist>
<!-- ]]> -->

A opção -t substitui a opção -u caso sejam usadas.




 cmdc-last">###last

Mostra uma listagem de entrada e saída de usuários no sistema.  
<!-- [ %DESCRICAOD [ --> São mostrados os seguintes campos na listagem:

<itemizedlist>
<listitem>

Nome do usuário


<listitem>

Terminal onde ocorreu a conexão/desconexão


<listitem>

O hostname (caso a conexão tenha ocorrido remotamente) ou console (caso tenha
ocorrido localmente).


<listitem>

A data do login/logout, a hora do login/down se estiver fora do sistema/ still
logged in se ainda estiver usando o sistema


<listitem>

Tempo (em Horas:Minutos) que esteve conectado ao sistema.



<!-- ]]> -->

A listagem é mostrada em ordem inversa, ou seja, da data mais atual para a mais
antiga.  A listagem feita pelo <command>last é obtida de
<filename>/var/log/wtmp</filename>.


<command>last [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-n [num]
<listitem>

Mostra [num] linhas.  Caso não seja usada, todas as linhas são mostradas.



<varlistentry>
<term>-R
<listitem>

Não mostra o campo HostName.



<varlistentry>
<term>-a
<listitem>

Mostra o hostname na última coluna.  Será muito útil se combinada com a opção
-d.



<varlistentry>
<term>-d
<listitem>

Usa o DNS para resolver o IP de sistemas remotos para nomes DNS.



<varlistentry>
<term>-x
<listitem>

Mostra as entradas de desligamento do sistema e alterações do nível de execução
do sistema.



</variablelist>
<!-- ]]> -->

O comando <command>last pode ser seguido de um argumento que será
pesquisado como uma expressão regular durante a listagem.

<!-- [ %OBS [ -->

O comando <command>last usa o arquivo
<filename>/var/log/wtmp</filename> para gerar sua listagem, mas alguns sistemas
podem não possuir este arquivo.  O arquivo <filename>/var/log/wtmp</filename>
somente é usado caso existir.  Você pode cria-lo com o comando <literal>"echo
-n &gt;/var/log/wtmp" ou <literal>touch /var/log/wtmp. 

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->
<itemizedlist>
<listitem>

<literal>last - Mostra a listagem geral


<listitem>

<literal>last -a - Mostra a listagem geral incluindo o nome da
máquina


<listitem>

<literal>last gleydson - Mostra somente atividades do usuário
gleydson


<listitem>

<literal>last reboot - Mostra as reinicializações do sistema


<listitem>

<literal>last tty1 - Mostra todas as atividades no tty1



<!-- ]]> -->

    <!-- ]]> -->


 cmdc-sg">###sg

Executa um comando com outra identificação de grupo.  
<!-- [ %DESCRICAOD [ --> A identificação do grupo
de usuário é modificada somente durante a execução do comando.  Para alterar a
identificação de grupo durante sua seção shell, use o comando <xref linkend="cmdc-newgrp"/>. <!-- ]]> -->


<command>sg [**-**] [**grupo**] [**comando**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term><literal>-
<listitem>

Se usado, inicia um novo ambiente durante o uso do comando (semelhante a um
novo login e execução do comando), caso contrário, o ambiente atual do usuário
é mantido.



<varlistentry>
<term><literal>grupo
<listitem>

Nome do grupo que o comando será executado.



<varlistentry>
<term><literal>comando
<listitem>

Comando que será executado.  O comando será executado pelo bash.



</variablelist>
<!-- ]]> -->

Quando este comando é usado, é pedida a senha do grupo que deseja acessar.
Caso a senha do grupo esteja incorreta ou não exista senha definida, a execução
do comando é negada.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>sg root ls /root

<!-- ]]> -->



 cmdc-incluirgrupo">###Adicionando o usuário a um grupo extra

Para adicionar um usuário em um novo grupo e assim permitir que ele acesse os
arquivos/diretórios que pertencem àquele grupo, você deve estar como root e
editar o arquivo <filename>/etc/group</filename> com o comando
<command>vigr.  Este arquivo possui o seguinte formato:


NomedoGrupo:senha:GID:usuários


Onde:

<variablelist>
<varlistentry>
<term>NomedoGrupo
<listitem>

É o nome daquele grupo de usuários.



<varlistentry>
<term>senha
<listitem>

Senha para ter acesso ao grupo.  Caso esteja utilizando senhas ocultas para
grupos, as senhas estarão em <filename>/etc/gshadow</filename>.



<varlistentry>
<term>GID
<listitem>

Identificação numérica do grupo de usuário.



<varlistentry>
<term>usuarios
<listitem>

Lista de usuários que também fazem parte daquele grupo.  Caso exista mais de um
nome de usuário, eles devem estar separados por vírgula.



</variablelist>

Deste modo para acrescentar o usuário "joao" ao grupo <literal>audio
para ter acesso aos dispositivos de som do Linux, acrescente o nome no final da
linha: "audio:x:100:joao".  Pronto, basta digitar <literal>logout e
entrar novamente com seu nome e senha, você estará fazendo parte do grupo
<literal>audio (confira digitando <literal>groups ou
<literal>id).


Outros nomes de usuários podem ser acrescentados ao grupo
<literal>audio bastando separar os nomes com vírgula.  Você também
pode usar o comando <command>adduser da seguinte forma para adicionar
automaticamente um usuário a um grupo:

<screen>
adduser joao audio


Isto adicionaria o usuário "joao" ao grupo <literal>audio da mesma
forma que fazendo-se a edição manualmente.




 cmdc-chfn">###chfn

Muda os dados usados pelo comando <xref linkend="cmdn-finger"/>.


<command>chfn [**usuário**]
[**opções**]


Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome do usuário.



<varlistentry>
<term>**opções**
<term>-f [nome]
<listitem>

Adiciona/altera o nome completo do usuário.



<varlistentry>
<term>-r [nome]
<listitem>

Adiciona/altera o número da sala do usuário.



<varlistentry>
<term>-w [tel]
<listitem>

Adiciona/altera o telefone de trabalho do usuário.



<varlistentry>
<term>-h [tel]
<listitem>

Adiciona/altera o telefone residencial do usuário.



<varlistentry>
<term>-o [outros]
<listitem>

Adiciona/altera outros dados do usuário.



</variablelist>

Caso o nome que acompanha as opções (como o nome completo) contenha espaços,
use "" para identifica-lo.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>chfn -f "Nome do Usuário root" root

<!-- ]]> -->



 cmdc-id">###id

Mostra a identificação atual do usuário, grupo primário e outros grupos que
pertence.


<command>id [**opções**]
[**usuário**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

É o usuário que desejamos ver a identificação, grupos primários e
complementares.



<varlistentry>
<term>**opções**
<term>-g, --group
<listitem>

Mostra somente a identificação do grupo primário.



<varlistentry>
<term>-G, --groups
<listitem>

Mostra a identificação de outros grupos que pertence.



<varlistentry>
<term>-n, --name
<listitem>

Mostra o nome do usuário e grupo ao invés da identificação numérica.



<varlistentry>
<term>-u, --user
<listitem>

Mostra somente a identificação do usuário (user ID).



<varlistentry>
<term>-r, --real
<listitem>

Mostra a identificação real de usuário e grupo, ao invés da efetiva.  Esta
opção deve ser usada junto com uma das opções: -u, -g, ou -G.



</variablelist>
<!-- ]]> -->

Caso não sejam especificadas opções, <command>id mostrará todos os
dados do usuário.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>id, <literal>id --user, <literal>id -r
-u.

<!-- ]]> -->



 cmdc-logname">###logname

Mostra seu login (username).


<literal>logname



 cmdc-users">###users

Mostra os nomes de usuários usando atualmente o sistema.  
<!-- [ %DESCRICAOD [ --> Os nomes de usuários
são mostrados através de espaços sem detalhes adicionais, para ver maiores
detalhes sobre os usuários, veja os comandos <xref linkend="cmdc-id"e <xref linkend="cmdn-who"/>. <!-- ]]> -->


<literal>users


Os nomes de usuários atualmente conectados ao sistema são obtidos do arquivo
<filename>/var/log/wtmp</filename>.




 cmdc-groups">###groups

Mostra os grupos que o usuário pertence.


<command>groups [**usuário**]

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>groups, <literal>groups root

<!-- ]]> -->


