<!-- Converted by db4-upgrade version 1.0 -->

 s-apache-log">###Sistema de Log do Apache

O <command>Apache é bem flexível na especificação do que será
registrado em seus arquivos de log, possibilitando utilizar um arquivo de log
único, diversos arquivos de logs registrando cada evento ocorrido no sistema
(conexão, navegador, bloqueio de acesso, erros, etc) incluindo os campos que
deseja em cada arquivo e a ordem dos campos em cada um deles.


Enfim qualquer coisa pode ser especificada de forma que atenda as suas
necessidades particulares de logging.

 s-apache-log-agentlog">###AgentLog

<literal>AgentLog arquivo/pipe: Indica o nome do arquivo que
registrará o nome do navegador que está acessando a página (conteúdo do
cabeçalho <literal>User-Agent).  É possível usar o pipe "|" para
direcionar os erros para um programa de formatação ou processamento.  **ATENÇÃO**: Se um programa for usado como pipe, ele será
executado sob o usuário que iniciou o <command>apache.  Revise o
código fonte do programa para ter certeza que não contém falhas que possam
comprometer a segurança de seu sistema.


Exemplo: <literal>AgentLog /var/log/apache/agent.log



 s-apache-log-errorlog">###ErrorLog

<literal>ErrorLog arquivo/pipe - Especifica o arquivo que registrará
as mensagens de erro do servidor <command>Apache.  É possível usar o
pipe "|" para direcionar os erros para um programa de formatação ou
processamento.


Exemplo: <literal>ErrorLog /var/log/apache/errors.log



 s-apache-log-customlog">###CustomLog

Permite especificar onde os logs serão gravados para os arquivos de logs
personalizados.  Esta diretiva também aceita apelidos definidos pela diretiva
**LogFormat**.


<literal>CustomLog [arquivo/pipe] [formato/nome]


Onde:

<variablelist>
<varlistentry>
<term>**arquivo/pipe**
<listitem>

Arquivo de log personalizado ou pipe.



<varlistentry>
<term>**formato/nome**
<listitem>

Especifica o formato do arquivo de log (da mesma forma que o especificado na
opção **LogFormat**).  Deverá ser especificado entre "aspas"
caso tiver espaços.  Veja <xref linkend="s-apache-log-logformat"para
detalhes.



</variablelist>

Ao invés de especificar o formato, também é possível usar um apelido definido
pela opção **LogFormat** (<xref linkend="s-apache-log-logformat"/>), neste caso os parâmetros definidos pelo
**LogFormat** para "nome" serão atribuídos a diretiva
**CustomLog**.


Exemplos:

<itemizedlist>
<listitem>

<literal>CustomLog /var/log/apache/common.log "%h %l %u %t \"%r\" %&gt;s
%b"


<listitem>

<literal>CustomLog /var/log/apache/common.log common





 s-apache-log-refererlog">###RefererLog

<literal>RefererLog [arquivo/pipe]: Indica que arquivo/pipe
registrará os campos Referer do cabeçalho HTTP.  Esta diretiva é mantida por
compatibilidade com o servidor web NCSA 1.4.


A configuração padrão do <command>Apache usa uma diretiva alternativa
para a especificação do **referer** que é a seguinte:

<screen>
LogFormat "%{Referer}i -&gt; %U" referer
CustomLog /var/log/apache/referer.log referer


Exemplo: <literal>RefererLog /var/log/apache/referer.log



 s-apache-log-rewritelog">###RewriteLog

<literal>RewriteLog: [arquivo/pipe]: Indica o arquivo/pipe que
registrará qualquer regravação de URL feita pelo <command>Apache.


**OBS**: Não é recomendável direcionar o nome de
arquivo para <filename>/dev/null</filename> como forma de desativar este log,
porque o módulo de regravação não cria a saída para um arquivo de log, ele cria
a saída de log internamente.  Isto somente deixará o servidor lento.  Para
desativar este registro, simplesmente remova/comente a diretiva RewriteLog ou
use a opção RewriteLogLevel 0.


Exemplo: <literal>RewriteLog "/usr/local/var/apache/logs/rewrite.log



 s-apache-log-rewriteloglevel">###RewriteLogLevel

<literal>RewriteLogLevel [num]: Especifica os detalhes que serão
incluídos no registro da opção RewriteLog, os valores permitidos estão entre 0
e 9.  Se for usado 0, o registro do RewriteLog é totalmente desativado (esta é
a padrão).  **OBS**: Qualquer valor acima de 2
deixa o servidor Web cada vez mais lento devido ao processamento e a quantidade
de detalhes registrados no arquivo especificado por
**RewriteLog**.



 s-apache-log-scriptlog">###ScriptLog

<literal>ScriptLog [arquivo]: Especifica o nome do arquivo de log que
receberá as mensagens de erros gerados por scripts CGI executados no servidor.
Esta opção é controlada pelo módulos **mod_cgi**.


Os arquivos de log serão abertos por um sub-processo rodando com as permissões
do usuário especificado na diretiva "user".


**OBS**: Esta opção somente é recomendada como
depuradora de scripts CGI, não para uso contínuo em servidores ativos.


Exemplo: <literal>ScriptLog /var/log/apache/cgiscripts.log



 s-apache-log-scriptlogbuffer">###ScriptLogBuffer

<literal>ScriptLogBuffer: Especifica o tamanho do cabeçalho PUT ou
POST gravado no arquivo especificado por **ScriptLog**.  O
valor padrão é 1024 bytes.  Esta opção é controlada pelo módulos
**mod_cgi**


Exemplo: <literal>ScriptLogBuffer 512



 s-apache-log-scriptloglength">###ScriptLogLength

<literal>ScriptLogLength: [tamanho]: Especifica o tamanho máximo do
arquivo de log gerado pela opção ScriptLog.  O valor padrão é 10385760 bytes
(10.3MB).  Esta opção é controlada pelo módulos **mod_cgi**


Exemplo: <literal>ScriptLogLength 1024480



 s-apache-log-logformat">###LogFormat

<literal>LogFormat: Define os campos padrões do arquivo gerado pela
opção **TransferLog**.  O seu formato é o seguinte:


<literal>LogFormat [formato] [nome]


Quando o formato não é especificado, assume o valor padrão <literal>%h %l %u %t
\"%r\" %s %b.  A especificação do [**nome**] permite
que você utilize o formato especificado em uma opção
**CustomLog** ou outra diretiva
**LogFormat**, facilitando a especificação do formato do log.


Os seguintes formatos são válidos:

<itemizedlist>
<listitem>

<literal>%b - Bytes enviados, excluindo cabeçalhos HTTP.


<listitem>

<literal>%f - Nome do arquivo.


<listitem>

<literal>%{FOOBAR}e - O conteúdo da variável de ambiente FOOBAR.


<listitem>

<literal>%h - Máquina cliente.


<listitem>

<literal>%a - Endereço IP da máquina cliente.


<listitem>

<literal>%A - Endereço IP local.  Muito útil em virtual hostings.


<listitem>

<literal>%{Foobar}i - O conteúdo de Foobar: linhas de cabeçalho na
requisição enviada ao servidor.


<listitem>

<literal>%l - O nome de login remoto enviado pelo identd (se
fornecido).


<listitem>

<literal>%{Foobar}n - O conteúdo de "FooBar" de outro módulo.


<listitem>

<literal>%{Foobar}o: - O conteúdo de Foobar: linhas de cabeçalho na
resposta.


<listitem>

<literal>%p - A porta do servidor servindo a requisição.


<listitem>

<literal>%P - A identificação do processo filho que serviu a
requisição.


<listitem>

<literal>%r - A primeira linha da requisição.


<listitem>

<literal>%s - Status.  Para requisições que foram redirecionadas.
internamente.  Este é o status de uma requisição *original*.  Use %s para a
última.


<listitem>

<literal>%t - Hora, no formato do arquivo de log (formato inglês
padrão).


<listitem>

<literal>%{format}t - Hora, no formato definido por strftime.


<listitem>

<literal>%T - O tempo necessário para servir a requisição, em
segundos.


<listitem>

<literal>%u - Usuário remoto (através do auth, pode ser falso se o
status de retorno (%s) for 401).


<listitem>

<literal>%U - O caminho da URL requisitada.


<listitem>

<literal>%v - O nome canônico definido por
**ServerName** que serviu a requisição.


<listitem>

<literal>%V - O nome do servidor de acordo com a configuração de
**UseCanonicalName**.




Exemplos:

<screen>
 LogFormat "%h %l %u %t \"%r\" %&gt;s %b \"%{Referer}i\" \"%{User-Agent}i\" %T %v" full
 LogFormat "%h %l %u %t \"%r\" %&gt;s %b \"%{Referer}i\" \"%{User-Agent}i\" %P %T" debug
 LogFormat "%h %l %u %t \"%r\" %&gt;s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
 LogFormat "%h %l %u %t \"%r\" %&gt;s %b" common
 LogFormat "%{Referer}i -&gt; %U" referer
 LogFormat "%{User-agent}i" agent



 s-apache-log-transferlog">###TransferLog

<literal>TransferLog [arquivo/pipe]: Indica o arquivo que armazenará
as transferências entre o servidor http e o cliente.  Ela cria o arquivo de log
com o formato definido pela opção **LogFormat** mais recente
(sem a especificação do nome associado a diretiva) ou o formato padrão CLF do
log do <command>Apache.


Se omitido, o arquivo não será gerado


Exemplo: <literal>TransferLog /var/log/apache/transferências.log


**OBS:** Se esta não é uma opção muito utilizada
na administração de seus sistemas, é recomendável o uso da diretiva
**CustomLog** (veja <xref linkend="s-apache-log-customlog"/>)
para evitar confusões futuras.



 s-apache-log-loglevel">###LogLevel

Define o nível de alerta das mensagens que serão gravadas no arquivo
especificado pela diretiva **ErrorLog**.  Quando não é
especificado, assume o nível "error" como padrão.  Abaixo os parâmetros aceitos
em sua respectiva ordem de importância:

<itemizedlist>
<listitem>

<literal>emerg - O sistema está inutilizável.


<listitem>

<literal>alert - A ação deve ser tomada imediatamente.


<listitem>

<literal>crit - Condições críticas.


<listitem>

<literal>error - Condições de erro.


<listitem>

<literal>warn - Condições de alerta.


<listitem>

<literal>notice - Condição normal mas significante.


<listitem>

<literal>info - Mensagens informativas.


<listitem>

<literal>debug - Mensagens do nível de depuração.




Note que os níveis são os mesmos usados pelo <command>syslog.  Quando
um nível particular é especificado, as mensagens de todos os níveis de maior
importância também serão registrados.  Por exemplo, se o nível "info" for
especificado, as mensagens com os níveis de "notice" e "warn" também serão
registradas.  É recomendado o uso de um nível de no mínimo
**crit**.



 s-apache-log-anonylogmail">###Anonymous_LogEmail

Se estiver como "on" a senha digitada será registrada no arquivo especificado
por **ErrorLog**.  Esta diretiva é
**ativada** por padrão.


Exemplo: <literal>Anonymous_LogEmail off



 s-apache-log-cookielog">###CookieLog

Especifica o arquivo que será usado para registrar os cookies


**OBS1**: Caso o caminho do arquivo não for
especificado nas diretivas, será assumido **DocumentRoot**
como diretório padrão.


**OBS2**: Caso esteja usando o pipe, o dono do
processo será o mesmo que iniciou o servidor WEB Apache.  Tenha certeza do
funcionamento do programa para não comprometer o seu sistema, e cuide para que
ele não possa ser modificado indevidamente por outros usuários.


Exemplo: <literal>CookieLog /var/log/apache/cookies.log



 s-apache-log-webalizer">###Relatório gráfico de acesso ao sistema

O programa <command>webalizer poderá ser instalado para gerar um
relatório gráfico com a estatísticas de visitas por ano/mes/dia/hora usando os
dados do <filename>access.log</filename>.  Outra interessante característica
são as estatísticas de códigos http (veja <xref linkend="s-apache-httpcodes"/>), onde é possível saber a quantidade de links
quebrados existentes em nosso servidor (estes poderão ser detectados usando o
pacote de análise de sites <systemitem role="package">linbot</systemitem>).  O
<command>webalizer também é compatível com os formatos de log do
<command>squid e <command>proftpd.  Na distribuição
<command>Debian ele pode ser instalado a partir do pacote <systemitem role="package">webalizer</systemitem> e gera um relatório geral quando é
executado sem opções.





