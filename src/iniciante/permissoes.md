<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" perm">###Permissões de acesso a arquivos e diretórios

As permissões de acesso protegem o sistema de arquivos Linux do acesso indevido
de pessoas ou programas não autorizados.


A permissão de acesso do <command>GNU/Linux também impede que um
programa mal intencionado, por exemplo, apague um arquivo que não deve, envie
arquivos especiais para outra pessoa ou forneça acesso da rede para que outros
usuários invadam o sistema.  O sistema <command>GNU/Linux é muito
seguro e como qualquer outro sistema seguro e confiável impede que usuários mal
intencionados (ou iniciantes que foram enganados) instalem programas enviados
por terceiros sem saber para que eles realmente servem e causem danos
irreversíveis em seus arquivos, seu micro ou sua empresa.


Esta seção do guia, de inicio, pode ser um pouco dificil de se entender, então
recomendo ler e ao mesmo tempo prática-la para uma ótima compreensão.  Não se
preocupe, também coloquei exemplos para ajuda-lo a entender o sistema de
permissões de acesso do ambiente <command>GNU/Linux.



 perm-user-group">###Donos, Grupos e outros usuários

A idéia básica da segurança no sistema <command>GNU/Linux é definir o
acesso aos arquivos por donos, grupos e outros usuários:

<variablelist>
<varlistentry>
<term>**dono**
<listitem>

É a pessoa que criou o arquivo ou o diretório.  O nome do dono do
arquivo/diretório é o mesmo do usuário usado para entrar no sistema
<command>GNU/Linux.  Somente o dono pode modificar as permissões de
acesso do arquivo.


As permissões de acesso do dono de um arquivo somente se aplicam ao dono do
arquivo/diretório.  A identificação do dono também é chamada de <literal>user
id (UID).


A identificação de usuário ao qual o arquivo pertence é armazenada no arquivo
<filename>/etc/passwd</filename> e do grupo no arquivo
<filename>/etc/group</filename>.  Estes são arquivos textos comuns e podem ser
editados em qualquer editor de texto, mas utilize preferencialmente os comandos
<command>vipw e <command>vigr que executa procedimentos
adicionais de checagem de uids e grupos após a alteração.  Tenha cuidado para
não modificar o campo que contém a senha do usuário encriptada (que pode estar
armazenada no arquivo <filename>/etc/passwd</filename> caso não estiver usando
senhas ocultas).



<varlistentry>
<term>**grupo**
<listitem>

Permite que vários usuários diferentes tenham acesso a um mesmo arquivo (já que
somente o dono poderia ter acesso ao arquivo).  Cada usuário pode fazer parte
de um ou mais grupos e então acessar arquivos que pertençam ao mesmo grupo que
o seu (mesmo que estes arquivos tenham outro **dono**).


Por padrão, quando um novo usuário é criado e não especificar nenhum grupo, ele
pertencerá ao grupo de mesmo nome do seu grupo primário (este comportamento é
controlado pelo parametro <literal>USERGROUPS=yes do arquivo
<filename>/etc/adduser.conf</filename>, veja <xref linkend="cmdc-id"/>).  A
identificação do grupo é chamada de <literal>GID (**group
id**).


Um usuário pode pertencer a um ou mais grupos.  Para detalhes de como incluir o
usuário em mais grupos veja <xref linkend="cmdc-incluirgrupo"/>.



<varlistentry>
<term>**outros**
<listitem>

É a categoria de usuários que não são donos ou não pertencem ao grupo do
arquivo.



</variablelist>

Cada um dos tipos acima possuem três tipos básicos de permissões de acesso que
serão vistas na próxima seção.




 perm-tipos">###Tipos de Permissões de Acesso

Quanto aos tipos de permissões que se aplicam ao **dono**,
**grupo** e **outros usuários**, temos 3
permissões básicas:

<itemizedlist>
<listitem>

<literal>r - Permissão de leitura para arquivos.  Caso for um
diretório, permite listar seu conteúdo (através do comando
<command>ls, por exemplo).


<listitem>

<literal>w - Permissão de gravação para arquivos.  Caso for um
diretório, permite a gravação de arquivos ou outros diretórios dentro dele.


Para que um arquivo/diretório possa ser apagado, é necessário o acesso a
gravação.


<listitem>

<literal>x - Permite executar um arquivo (caso seja um programa
executável).  Caso seja um diretório, permite que seja acessado através do
comando <command>cd 
(veja <xref linkend="comando-cd"para detalhes).




As permissões de acesso a um arquivo/diretório podem ser visualizadas com o uso
do comando <literal>ls -la.  
Para maiores detalhes veja <xref linkend="comando-ls"/>.
As 3 letras (rwx) são agrupadas da seguinte forma:

<screen>
-rwxr-xr--   gleydson   users  teste


Virou uma bagunça não?  Vou explicar cada parte para entender o que quer dizer
as 10 letras acima (da esquerda para a direita):

<itemizedlist>
<listitem>

A primeira letra diz qual é o tipo do arquivo.  Caso tiver um "d" é um
diretório, um "l" um link a um arquivo no sistema 
<!-- [ %INIC-INTER [ --> (veja <xref linkend="cmdv-ln"para detalhes) <!-- ]]> -->, 
um "-" quer dizer que é um arquivo comum,
etc.


<listitem>

Da segunda a quarta letra (rwx) dizem qual é a permissão de acesso ao
**dono** do arquivo.  Neste caso **gleydson**
ele tem a permissão de ler (r - read), gravar (w - write) e executar (x -
execute) o arquivo <filename>teste</filename>.


<listitem>

Da quinta a sétima letra (r-x) diz qual é a permissão de acesso ao
**grupo** do arquivo.  Neste caso todos os usuários que
pertencem ao grupo **users** tem a permissão de ler (r), e
também executar (x) o arquivo <filename>teste</filename>.


<listitem>

Da oitava a décima letra (r--) diz qual é a permissão de acesso para os
**outros usuários**.  Neste caso todos os usuários que não são
donos do arquivo <filename>teste</filename> tem a permissão somente para ler o
programa.




Veja o comando <xref linkend="perm-chmod"para detalhes sobre a mudança das
permissões de acesso de arquivos/diretórios.




 perm-acessando">###Etapas para acesso a um arquivo/diretório

O acesso a um arquivo/diretório é feito verificando primeiro se o usuário que
acessará o arquivo é o seu **dono**, caso seja, as permissões
de dono do arquivo são aplicadas.  Caso não seja o **dono** do
arquivo/diretório, é verificado se ele pertence ao grupo correspondente, caso
pertença, as permissões do **grupo** são aplicadas.  Caso não
pertença ao **grupo**, são verificadas as permissões de acesso
para os outros usuários que não são **donos** e não pertencem
ao **grupo** correspondente ao arquivo/diretório.


Após verificar aonde o usuário se encaixa nas permissões de acesso do arquivo
(se ele é o **dono**, pertence ao **grupo**,
ou **outros usuários**), é verificado se ele terá permissão
acesso para o que deseja fazer (ler, gravar ou executar o arquivo), caso não
tenha, o acesso é negado, mostrando uma mensagem do tipo: "Permission denied"
(permissão negada).


O que isto que dizer é que mesmo que você seja o dono do arquivo e definir o
acesso do **dono** (através do comando
<command>chmod) como somente leitura (r) mas o acesso dos
**outros usuários** como leitura e gravação, você somente
poderá ler este arquivo mas os outros usuários poderão ler/grava-lo.


As permissões de acesso (leitura, gravação, execução) para donos, grupos e
outros usuários são independentes, permitindo assim um nível de acesso
diferenciado.  Para maiores detalhes veja <xref linkend="perm-tipos"/>.

<!-- [ %OBS [ -->

Lembre-se: Somente o dono pode modificar as permissões de um arquivo/diretório!

<!-- ]]> -->

Para mais detalhes veja os comandos <xref linkend="perm-chown"e <xref linkend="perm-chgrp"/>.




 perm-exemplo">###Exemplos práticos de permissões de acesso

Abaixo dois exemplos práticos de permissão de acesso: <xref linkend="perm-exemplo-a"e a <xref linkend="perm-exemplo-d"/>.  Os dois
exemplos são explicados passo a passo para uma perfeita compreensão do assunto.
Vamos a prática!



 perm-exemplo-a">###Exemplo de acesso a um arquivo

Abaixo um exemplo e explicação das permissões de acesso a um arquivo no
<command>GNU/Linux (obtido com o comando <literal>ls -la,
explicarei passo a passo cada parte:


-rwxr-xr-- 1 gleydson user 8192 nov 4 16:00 teste

<variablelist>
<varlistentry>
<term><literal>-rwxr-xr--
<listitem>

Estas são as permissões de acesso ao arquivo <filename>teste</filename>.  Um
conjunto de 10 letras que especificam o tipo do arquivo, permissão do dono do
arquivo, grupo do arquivo e outros usuários.  Veja a explicação detalhada sobre
cada uma abaixo:

<variablelist>
<varlistentry>
<term>**-**rwxr-xr--
<listitem>

A primeira letra (do conjunto das 10 letras) determina o tipo do arquivos.  Se
a letra for um **d** é um diretório, e você
poderá acessa-lo usando o comando <command>cd.  Caso for um **l** é um link simbólico para algum arquivo ou diretório
no sistema 
<!-- [ %INIC-INTER [ --> (para detalhes veja o comando <xref linkend="cmdv-ln"<!-- ]]> -->.  
Um **-** significa que é um arquivo normal.



<varlistentry>
<term>-**rwx**r-xr--
<listitem>

Estas 3 letras (da segunda a quarta do conjunto das 10 letras) são as
permissões de acesso do **dono** do arquivo
<filename>teste</filename>.  O dono (neste caso **gleydson**)
tem a permissão para ler (r), gravar (w) e executar (x) o arquivo
<filename>teste</filename>.



<varlistentry>
<term>-rwx**r-x**r--
<listitem>

Estes 3 simbolos (do quinto ao sétimo do conjunto de 10) são as permissões de
acesso dos usuários que pertencem ao **grupo user** do arquivo
<filename>teste</filename>.  Os usuários que pertencem ao grupo
**user** tem a permissão somente para ler (r) e executar (x) o
arquivo <filename>teste</filename> não podendo modifica-lo ou apaga-lo.



<varlistentry>
<term>-rwxr-x**r--**
<listitem>

Estes 3 simbolos (do oitavo ao décimo) são as permissões de acesso para
usuários que **não** são
**donos** do arquivo <filename>teste</filename> e que
**não** pertencem ao grupo
**user**.  Neste caso, estas pessoas somente terão a permissão
para ver o conteúdo do arquivo <filename>teste</filename>.



</variablelist>


<varlistentry>
<term>**gleydson**
<listitem>

Nome do dono do arquivo <filename>teste</filename>.



<varlistentry>
<term>**user**
<listitem>

Nome do grupo que o arquivo <filename>teste</filename> pertence.



<varlistentry>
<term><filename>teste</filename>
<listitem>

Nome do arquivo.



</variablelist>



 perm-exemplo-d">###Exemplo de acesso a um diretório

Abaixo um exemplo com explicações das permissões de acesso a um diretório no
<command>GNU/Linux:


drwxr-x--- 2 gleydson user 1024 nov 4 17:55 exemplo

<variablelist>
<varlistentry>
<term><literal>drwxr-x---
<listitem>

Permissões de acesso ao diretório <filename>exemplo</filename>.  É um conjunto
de 10 letras que especificam o tipo de arquivo, permissão do dono do diretório,
grupo que o diretório pertence e permissão de acesso a outros usuários.  Veja
as explicações abaixo:

<variablelist>
<varlistentry>
<term>**d**rwxr-x---
<listitem>

A primeira letra (do conjunto das 10) determina o tipo do arquivo.  Neste caso
é um diretório porque tem a letra **d**.



<varlistentry>
<term>d**rwx**r-x---
<listitem>

Estas 3 letras (da segunda a quarta) são as permissões de acesso do
**dono** do diretório <filename>exemplo</filename>.  O dono do
diretório (neste caso **gleydson**) tem a permissão para
listar arquivos do diretório (r), gravar arquivos no diretório (w) e entrar no
diretório (x).



<varlistentry>
<term>drwx**r-x**---
<listitem>

Estas 3 letras (da quinta a sétima) são as permissões de acesso dos usuários
que pertencem ao **grupo user**.  Os usuários que pertencem ao
grupo **user** tem a permissão somente para listar arquivos do
diretório (r) e entrar no diretório (x) <filename>exemplo</filename>.



<varlistentry>
<term>drwxr-x**---**
<listitem>

Estes 3 simbolos (do oitavo ao décimo) são as permissões de acesso para
usuários que **não** são
**donos** do diretório <filename>exemplo</filename> e que
**não** pertencem ao grupo
**user**.  Com as permissões acima, nenhum usuário que se
encaixe nas condições de **dono** e **grupo**
do diretório tem a permissão de acessa-lo.



</variablelist>


<varlistentry>
<term>**gleydson**
<listitem>

Nome do dono do diretório <filename>exemplo</filename>.



<varlistentry>
<term>**user**
<listitem>

Nome do grupo que diretório <filename>exemplo</filename> pertence.



<varlistentry>
<term><filename>exemplo</filename>
<listitem>

Nome do diretório.



</variablelist>

Para detalhes de como alterar o dono/grupo de um arquivo/diretório, veja os
comandos <xref linkend="perm-chmod"/>, <xref linkend="perm-chgrp"e <xref linkend="perm-chown"/>.

<!-- [ %OBS [ -->

**OBSERVAÇÕES**:

<itemizedlist>
<listitem>

O usuário <literal>root não tem nenhuma restrição de acesso ao
sistema.


<listitem>

Se você tem permissões de gravação no diretório e tentar apagar um arquivo que
você não tem permissão de gravação, o sistema perguntará se você confirma a
exclusão do arquivo apesar do modo leitura.  Caso você tenha permissões de
gravação no arquivo, o arquivo será apagado por padrão sem mostrar nenhuma
mensagem de erro (a não ser que seja especificada a opção -i com o comando
<command>rm).


<listitem>

Por outro lado, mesmo que você tenha permissões de gravação em um arquivo mas
não tenha permissões de gravação em um diretório, a exclusão do arquivo será
negada.



<!-- ]]> -->

Isto mostra que é levado mais em consideração a permissão de acesso do
diretório do que as permissões dos arquivos e sub-diretórios que ele contém.
Este ponto é muitas vezes ignorado por muitas pessoas e expõem seu sistema a
riscos de segurança.  Imagine o problema que algum usuário que não tenha
permissão de gravação em um arquivo mas que a tenha no diretório pode causar em
um sistema mal administrado.






 perm-especiais">###Permissões de Acesso Especiais

Em adição as três permissões básicas (rwx), existem permissões de acesso
especiais (stX) que afetam os arquivos e diretórios:

<itemizedlist>
<listitem>

<literal>s - Quando é usado na permissão de acesso do
**Dono**, ajusta a identificação efetiva do usuário do
processo durante a execução de um programa, também chamado de **bit
setuid**.  Não tem efeito em diretórios.


Quando <literal>s é usado na permissão de acesso do
**Grupo**, ajusta a identificação efetiva do grupo do processo
durante a execução de um programa, chamado de **bit setgid**.
É identificado pela letra <literal>s no lugar da permissão de
execução do grupo do arquivo/diretório.  Em diretórios, força que os arquivos
criados dentro dele pertençam ao mesmo grupo do diretório, ao invés do grupo
primário que o usuário pertence.


Ambos **setgid** e **setuid** podem aparecer
ao mesmo tempo no mesmo arquivo/diretório.  A permissão de acesso especial
<literal>s somente pode aparecer no campo **Dono** e
**Grupo**.


<listitem>

<literal>S - Idêntico a "s".  Significa que não existe a permissão
"x" (execução ou entrar no diretório) naquela posição.  Um exemplo é o chmod
2760 em um diretório.


<listitem>

<literal>t - Salva a imagem do texto do programa no dispositivo swap,
assim ele será carregado mais rapidamente quando executado, também chamado de
**stick bit**.


Em diretórios, impede que outros usuários removam arquivos dos quais não são
donos.  Isto é chamado de colocar o diretório em modo
<literal>append-only.  Um exemplo de diretório que se encaixa
perfeitamente nesta condição é o <filename>/tmp</filename>, todos os usuários
devem ter acesso para que seus programas possam criar os arquivos temporários
lá, mas nenhum pode apagar arquivos dos outros.  A permissão especial
<literal>t, pode ser especificada somente no campo outros usuários
das permissões de acesso.


<listitem>

<literal>T - Idêntico a "t".  Significa que não existe a permissão
"x" naquela posição (por exemplo, em um chmod 1776 em um diretório).


<listitem>

<literal>X - Se você usar <literal>X ao invés de
<literal>x, a permissão de execução somente é aplicada se o arquivo
já tiver permissões de execução.  Em diretórios ela tem o mesmo efeito que a
permissão de execução <literal>x.




<!-- [ %EXEMPLO [ -->
<itemizedlist>
<listitem>

Exemplo da permissão de acesso especial <literal>X:

<orderedlist numeration="arabic">
<listitem>

Crie um arquivo <filename>teste</filename> (digitando <literal>touch
teste) e defina sua permissão para <literal>rw-rw-r--
(<literal>chmod ug=rw,o=r teste ou <literal>chmod 664
teste).


<listitem>

Agora use o comando <literal>chmod a+X teste


<listitem>

digite <literal>ls -l


<listitem>

Veja que as permissões do arquivo não foram afetadas.


<listitem>

agora digite <literal>chmod o+x teste


<listitem>

digite <literal>ls -l, você colocou a permissão de execução para os
outros usuários.


<listitem>

Agora use novamente o comando <literal>chmod a+X teste


<listitem>

digite <literal>ls -l


<listitem>

Veja que agora a permissão de execução foi concedida a todos os usuários, pois
foi verificado que o arquivo era executável (tinha permissão de execução para
outros usuários).


<listitem>

Agora use o comando <literal>chmod a-X teste


<listitem>

Ele também funcionará e removerá as permissões de execução de todos os
usuários, porque o arquivo <filename>teste</filename> tem permissão de execução
(confira digitando <literal>ls -l).


<listitem>

Agora tente novamente o <literal>chmod a+X teste


<listitem>

Você deve ter reparado que a permissão de acesso especial <literal>X
é semelhante a <literal>x, mas somente faz efeito quanto o arquivo já
tem permissão de execução para o dono, grupo ou outros usuários.


</orderedlist>

Em diretórios, a permissão de acesso especial <literal>X funciona da
mesma forma que <literal>x, até mesmo se o diretório não tiver
nenhuma permissão de acesso (<literal>x).



<!-- ]]> -->




 perm-root">###A conta root

**Esta seção foi baseada no Manual de Instalação da Debian**.


A conta root é também chamada de **super usuário**, este é um
login que não possui restrições de segurança.  A conta root somente deve ser
usada para fazer a administração do sistema, e usada o menor tempo possível.


Qualquer senha que criar deverá conter no mínimo 10 caracteres (pois tamanho
menor do que 10 é facilmente quebrado usando brute force com o puder computacional
existente atulamente, sendo que o ideal é utilizar frases senhas, contendo letras
maísculas e minúsculas, caracteres especiais, números e pontuação.  Tenha um cuidado 
especial quando escolher sua senha root, porque ela é a conta mais poderosa.  Evite 
palavras de dicionário ou o uso de qualquer outros dados pessoais que podem ser adivinhados.


Em distribuições <command>Linux mais modernas, o acesso via usuário root é 
automaticamente negado em sessões iniciadas via acesso remoto <command>ssh.


Se qualquer um lhe pedir senha root, seja extremamente cuidadoso.  Você
normalmente nunca deve distribuir sua conta root, a não ser que esteja
administrando um computador com mais de um administrador do sistema.


Utilize uma conta de usuário normal ao invés da conta root para operar seu
sistema.  Porque não usar a conta root?  Bem, uma razão para evitar usar
privilégios root é por causa da facilidade de se cometer danos irreparáveis
como root.  Outra razão é que você pode ser enganado e rodar um programa
**Cavalo de Tróia** -- que é um programa que obtém poderes do
**super usuário** para comprometer a segurança do seu sistema
sem que você saiba.




 perm-chmod">###chmod

Muda a permissão de acesso a um arquivo ou diretório.  Com este comando você
pode escolher se usuário ou grupo terá permissões para ler, gravar, executar um
arquivo ou arquivos.  
<!-- [ %DESCRICAOD [ --> Sempre que um arquivo é criado, seu dono é o usuário que
o criou e seu grupo é o grupo do usuário (exceto para diretórios configurados
com a permissão de grupo <literal>"s", será visto adiante). <!-- ]]> -->


<command>chmod [**opções**] [**permissões**]
[**diretório/arquivo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**diretório/arquivo**
<listitem>

Diretório ou arquivo que terá sua permissão mudada.



<varlistentry>
<term>**opções**
<term>-v, --verbose
<listitem>

Mostra todos os arquivos que estão sendo processados.



<varlistentry>
<term>-f, --silent
<listitem>

Não mostra a maior parte das mensagens de erro.



<varlistentry>
<term>-c, --change
<listitem>

Semelhante a opção -v, mas só mostra os arquivos que tiveram as permissões
alteradas.



<varlistentry>
<term>-R, --recursive
<listitem>

Muda permissões de acesso do **diretório/arquivo** no
diretório atual e sub-diretórios.



<varlistentry>
<term>ugoa+-=rwxXst
<listitem>
<itemizedlist>
<listitem>

**ugoa** - Controla que nível de acesso será mudado.
Especificam, em ordem, usuário (u), grupo (g), outros (o), todos (a).


<listitem>

**+-=** - **+** coloca a permissão,
**-** retira a permissão do arquivo e **=**
define a permissão exatamente como especificado.


<listitem>

rwx - **r** permissão de leitura do arquivo.
**w** permissão de gravação.  **x** permissão
de execução (ou acesso a diretórios).





</variablelist>
<!-- ]]> -->

<command>chmod não muda permissões de links simbólicos, as permissões
devem ser mudadas no arquivo alvo do link.  Também podem ser usados códigos
numéricos octais para a mudança das permissões de acesso a arquivos/diretórios.
Para detalhes veja <xref linkend="perm-octal"/>.

<!-- [ %OBS [ -->

DICA: É possível copiar permissões de acesso do arquivo/diretório, por exemplo,
se o arquivo <filename>teste.txt</filename> tiver a permissão de acesso
<literal>r-xr----- e você digitar <literal>chmod o=u, as
permissões de acesso dos outros usuários (o) serão idênticas ao do dono (u).
Então a nova permissão de acesso do arquivo <filename>teste.txt</filename> será
<literal>r-xr--r-x 

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos de permissões de acesso:

<variablelist>
<varlistentry>
<term><literal>chmod g+r *
<listitem>

Permite que todos os usuários que pertençam ao grupo dos arquivos (g) tenham
(+) permissões de leitura (r) em todos os arquivos do diretório atual.



<varlistentry>
<term><literal>chmod o-r teste.txt
<listitem>

Retira (-) a permissão de leitura (r) do arquivo <filename>teste.txt</filename>
para os outros usuários (usuários que não são donos e não pertencem ao grupo do
arquivo <filename>teste.txt</filename>).



<varlistentry>
<term><literal>chmod uo+x teste.txt
<listitem>

Inclui (+) a permissão de execução do arquivo <filename>teste.txt</filename>
para o dono e outros usuários do arquivo.



<varlistentry>
<term><literal>chmod a+x teste.txt
<listitem>

Inclui (+) a permissão de execução do arquivo <filename>teste.txt</filename>
para o dono, grupo e outros usuários.



<varlistentry>
<term><literal>chmod a=rw teste.txt
<listitem>

Define a permissão de todos os usuários exatamente (=) para leitura e gravação
do arquivo <filename>teste.txt</filename>.



</variablelist>
<!-- ]]> -->



 perm-chgrp">###chgrp

Muda o grupo de um arquivo/diretório.


<command>chgrp [**opções**] [grupo] [arquivo/diretório]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**grupo**
<listitem>

Novo grupo do **arquivo/diretório**.



<varlistentry>
<term>**arquivo/diretório**
<listitem>

Arquivo/diretório que terá o grupo alterado.



<varlistentry>
<term>**opções**
<term>-c, --changes
<listitem>

Somente mostra os arquivos/grupos que forem alterados.



<varlistentry>
<term>-f, --silent
<listitem>

Não mostra mensagens de erro para arquivos/diretórios que não puderam ser
alterados.



<varlistentry>
<term>-v, --verbose
<listitem>

Mostra todas as mensagens e arquivos sendo modificados.



<varlistentry>
<term>-R, --recursive
<listitem>

Altera os grupos de arquivos/sub-diretórios do diretório atual.



</variablelist>
<!-- ]]> -->



 perm-chown">###chown

Muda dono de um arquivo/diretório.  Opcionalmente pode também ser usado para
mudar o grupo.


<command>chown [**opções**] [dono.grupo] [diretório/arquivo]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**dono.grupo**
<listitem>

Nome do **dono.grupo** que será atribuído ao
**diretório/arquivo**.  O grupo é opcional.



<varlistentry>
<term>**diretório/arquivo**
<listitem>

Diretório/arquivo que o dono.grupo será modificado.



<varlistentry>
<term>**opções**
<term>-v, --verbose
<listitem>

Mostra os arquivos enquanto são alterados.



<varlistentry>
<term>-f, --supress
<listitem>

Não mostra mensagens de erro durante a execução do programa.



<varlistentry>
<term>-c, --changes
<listitem>

Mostra somente arquivos que forem alterados.



<varlistentry>
<term>-R, --recursive
<listitem>

Altera dono e grupo de arquivos no diretório atual e sub-diretórios.



</variablelist>
<!-- ]]> -->

O **dono.grupo** pode ser especificado usando o nome de grupo
ou o código numérico correspondente ao grupo (GID).

<!-- [ %OBS [ -->

Você deve ter permissões de gravação no diretório/arquivo para alterar seu
dono/grupo.

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->
<itemizedlist>
<listitem>

<literal>chown gleydson teste.txt - Muda o dono do arquivo
<filename>teste.txt</filename> para <literal>gleydson.


<listitem>

<literal>chown gleydson.foca teste.txt - Muda o dono do arquivo
<filename>teste.txt</filename> para <literal>gleydson e seu grupo
para <literal>foca.


<listitem>

<literal>chown -R gleydson.focalinux * - Muda o dono/grupo dos
arquivos do diretório atual e sub-diretórios para
<literal>gleydson/focalinux (desde que você tenha permissões de
gravação no diretórios e sub-diretórios).



<!-- ]]> -->



 perm-octal">###Modo de permissão octal

Ao invés de utilizar os modos de permissão <literal>+r,
<literal>-r, etc, pode ser usado o modo octal para se alterar a
permissão de acesso a um arquivo.  O modo octal é um conjunto de oito números
onde cada número define um tipo de acesso diferente.


É mais flexível gerenciar permissões de acesso usando o modo octal ao invés do
comum, pois você especifica diretamente a permissão do dono, grupo, outros ao
invés de gerenciar as permissões de cada um separadamente.  Abaixo a lista de
permissões de acesso octal:

<itemizedlist>
<listitem>

<literal>0 - Nenhuma permissão de acesso.  Equivalente a -rwx.


<listitem>

<literal>1 - Permissão de execução (x).


<listitem>

<literal>2 - Permissão de gravação (w).


<listitem>

<literal>3 - Permissão de gravação e execução (wx).  Equivalente a
permissão 2+1


<listitem>

<literal>4 - Permissão de leitura (r).


<listitem>

<literal>5 - Permissão de leitura e execução (rx).  Equivalente a
permissão 4+1


<listitem>

<literal>6 - Permissão de leitura e gravação (rw).  Equivalente a
permissão 4+2


<listitem>

<literal>7 - Permissão de leitura, gravação e execução.  Equivalente
a +rwx (4+2+1).




O uso de um deste números define a permissão de acesso do
**dono**, **grupo** ou **outros
usuários**.  Um modo fácil de entender como as permissões de acesso
octais funcionam, é através da seguinte tabela:

<screen>
1 = Executar
2 = Gravar
4 = Ler

* Para Dono e Grupo, multiplique as permissões acima por x100 e x10.

<!-- [ %INTER-AVANC [ -->

e para as permissões de acesso especiais:

<screen>
1000 = Salva imagem do texto no dispositivo de troca
2000 = Ajusta o bit setgid na execução
4000 = Ajusta o bit setuid na execução

<!-- ]]> -->

Basta agora fazer o seguinte:

<itemizedlist>
<listitem>

Somente permissão de execução, use 1.


<listitem>

Somente a permissão de leitura, use 4.


<listitem>

Somente permissão de gravação, use 2.


<listitem>

Permissão de leitura/gravação, use 6 (equivale a 2+4 / Gravar+Ler).


<listitem>

Permissão de leitura/execução, use 5 (equivale a 1+4 / Executar+Ler).


<listitem>

Permissão de execução/gravação, use 3 (equivale a 1+2 / Executar+Gravar).


<listitem>

Permissão de leitura/gravação/execução, use 7 (equivale a 1+2+4 /
Executar+Gravar+Ler).



<!-- [ %INTER-AVANC [ -->
<listitem>

Salvar texto no dispositivo de troca, use 1000.


<listitem>

Ajustar bit setgid, use 2000.


<listitem>

Ajustar bip setuid, use 4000.


<listitem>

Salvar texto e ajustar bit setuid, use 5000 (equivale a 1000+4000 / Salvar
texto + bit setuid).


<listitem>

Ajustar bit setuid e setgid, use 6000 (equivale a 4000+2000 / setuid + setgid).


<!-- ]]> -->



Vamos a prática com alguns exemplos:

<screen>
"chmod 764 teste"


Os números são interpretados da **direita para a
esquerda** como permissão de acesso aos **outros
usuários** (4), **grupo** (6), e
**dono** (7).  O exemplo acima faz os **outros
usuários** (4) terem acesso somente leitura (r) ao arquivo
<filename>teste</filename>, o **grupo** (6) ter a permissão de
leitura e gravação (w), e o **dono** (7) ter permissão de
leitura, gravação e execução (rwx) ao arquivo <filename>teste</filename>.


Outro exemplo:

<screen>
"chmod 40 teste"


O exemplo acima define a permissão de acesso dos **outros
usuários** (0) como nenhuma, e define a permissão de acesso do
**grupo** (4) como somente leitura (r).  Note usei somente
dois números e então a permissão de acesso do **dono** do
arquivo <literal>não é modificada (leia as permissões de acesso da
direita para a esquerda!).  Para detalhes veja a lista de permissões de acesso
em modo octal no inicio desta seção.

<screen>
"chmod 751 teste"


O exemplo acima define a permissão de acesso dos **outros
usuários** (1) para somente execução (x), o acesso do
**grupo** (5) como leitura e execução (rx) e o acesso do
**dono** (7) como leitura, gravação e execução (rwx).

<!-- [ %INTER-AVANC [ -->
<screen>
"chmod 4751 teste"


O exemplo acima define a permissão de acesso dos **outros
usuários** (1) para somente execução (x), acesso do
**grupo** (5) como leitura e execução (rx), o acesso do
**dono** (7) como leitura, gravação e execução (rwx) e ajusta
o bit setgid (4) para o arquivo <filename>teste</filename>.

<!-- ]]> -->



 perm-umask">###umask

A umask (**user mask**) são 3 números que definem as
permissões iniciais do <literal>dono, <literal>grupo e
<literal>outros usuários que o arquivo/diretório receberá quando for
criado ou copiado para um novo local.  Digite <literal>umask sem
parâmetros para retornar o valor de sua umask atual.


A umask tem efeitos diferentes caso o arquivo que estiver sendo criado for
**binário** (um programa executável) ou
**texto** 
<!-- [ %INICIANTE [ --> (<xref linkend="basico-arquivo-bintext"/>) <!-- ]]> -->.  Veja a
tabela a seguir para ver qual é a mais adequada a sua situação:

<screen>
---------------------------------------------
|       |        ARQUIVO       | DIRETÓRIO  |
| UMASK |----------------------|            |
|       |   Binário  |  Texto  |            |
|------------------------------|------------|
|   0   |    r-x     |   rw-   |    rwx     |
|   1   |    r--     |   rw-   |    rw-     |
|   2   |    r-x     |   r--   |    r-x     |
|   3   |    r--     |   r--   |    r--     |
|   4   |    --x     |   -w-   |    -wx     |
|   5   |    ---     |   -w-   |    -w-     |
|   6   |    --x     |   ---   |    --x     |
|   7   |    ---     |   ---   |    ---     |
---------------------------------------------


Um **arquivo texto** criado com o comando <literal>umask
012;touch texto.txt receberá as permissões
<literal>-rw-rw-r--, pois 0 (dono) terá permissões
<literal>rw-, 1 (grupo), terá permissões <literal>rw- e 2
(outros usuários) terão permissões <literal>r--.  Um
**arquivo binário** copiado com o comando <literal>umask
012;cp /bin/ls /tmp/ls receberá as permissões
<literal>-r-xr--r-x (confira com a tabela acima).


Por este motivo é preciso atenção antes de escolher a umask, um valor mal
escolhido poderia causar problemas de acesso a arquivos, diretórios ou
programas não sendo executados.  O valor padrão da umask na maioria das
distribuições atuais é 022.  
A umask padrão no sistema Debian é a  022.


A umask é de grande utilidade para programas que criam arquivos/diretórios
temporários, desta forma pode-se bloquear o acesso de outros usuários desde a
criação do arquivo, evitando recorrer ao <command>chmod.



