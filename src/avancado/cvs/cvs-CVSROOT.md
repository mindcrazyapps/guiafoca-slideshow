<?xml version="1.0" encoding="UTF-8"?>

 s-cvs-cvsroot">###Arquivos administrativos em CVSROOT

Esta seção descreve a função de cada um dos arquivos administrativos, isto pode
ser útil na configuração e personalização do CVS e de seu repositório.


Para não alongar muito o capítulo, procurei colocar uma breve descrição da
função de cada um deles, o comentários e exemplos existentes nos arquivos
oferecem uma boa compreensão do seu conteúdo.

 s-cvs-cvsroot-config">###<filename>config</filename>

Este arquivo é segue os padrões do arquivos de configuração e possui alguns
parâmetros que controlam o comportamento do CVS.  Segue uma lista deles:

<variablelist>
<varlistentry>
<term><replaceable>SystemAuth</replaceable>
<listitem>

Define se será utilizado a autenticação via <filename>/etc/passwd</filename>
quando o método **pserver** for utilizado.  Note que se o
arquivo <filename>passwd</filename> for criado no <filename>CVSROOT</filename>,
o <replaceable>SystemAuth</replaceable> será definido automaticamente para
<literal>no.


Exemplo: <literal>SystemAuth=yes.



<varlistentry>
<term><replaceable>LockDir</replaceable>
<listitem>

Especifica o diretório onde serão gravados os arquivos de lock.  Caso não seja
especificado, será usado o diretório do CVS.


Exemplo: <literal>LockDir=/var/lock/cvs



<varlistentry>
<term><replaceable>TopLevelAdmin</replaceable>
<listitem>

Permite criar ou não um diretório chamado <filename>CVS</filename> no root do
diretório de trabalho durante o <literal>cvs checkout.



<varlistentry>
<term><replaceable>LogHistory</replaceable>
<listitem>

Utiliza opções para especificar o que será registrado nos arquivos de log do
<literal>CVS.

<itemizedlist>
<listitem>

<literal>TOFEWGCMAR ou <literal>all


Registra todas as operações nos logs do <command>cvs.


<listitem>

<literal>TMAR


Registra todas as operações que modificam os arquivos <filename>",v"</filename>





</variablelist>


 s-cvs-cvsroot-modules">###<filename>modules</filename>

Especifica opções e programas externos que serão usados durante a execução de
comandos no repositório CVS.



 s-cvs-cvsroot-cvswrappers">###<filename>cvswrappers</filename>

Este arquivo define ações de controle de características de arquivos, de acordo
com seu nome.


Pode ser também definidas ações através de arquivos
<filename>.cvswrappers</filename>.



 s-cvs-cvsroot-commitinfo">###<filename>commitinfo</filename>

Define programas para fazer uma checagem baseada no diretório e dizer se o
commit é permitido.



 s-cvs-cvsroot-verifymsg">###<filename>verifymsg</filename>

Especifica o programa usado para verificar as mensagens de log.



 s-cvs-cvsroot-loginfo">###<filename>loginfo</filename>

Programa que é executado após o commit.  Ele pode ser usado para tratar a
mensagem de log e definir onde ela será gravada/enviada, etc.



 s-cvs-cvsroot-cvsignore">###<filename>cvsignore</filename>

Tudo que constar neste arquivo não será gravado (commit) no cvs.  Referências
globais podem ser usadas para especificar estes arquivos.  Veja a info page do
cvs para detalhes sober seu formato.


Pode também ser especificado através de arquivos
<filename>.cvsignore</filename>.



 s-cvs-cvsroot-checkoutlist">###<filename>checkoutlist</filename>

Especifica os arquivos que deseja manter sobre o controle do CVS que se
encontram em <filename>CVSROOT</filename>.  Se adicionar um script adicional,
ou qualquer outro arquivo no diretório <filename>CVSROOT</filename> ele deverá
constar neste arquivo.



 s-cvs-cvsroot-history">###<filename>history</filename>

É usado para registrar detalhes do comando **history** do CVS.





