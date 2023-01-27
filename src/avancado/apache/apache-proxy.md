<!-- Converted by db4-upgrade version 1.0 -->

 s-apache-proxy">###Configurando o Apache como servidor proxy

O <command>Apache pode ser configurado para funcionar como servidor
proxy transparente para sua rede interna, possibilitando inclusive o uso de
cache de disco.  É possível se fazer conexões HTTP (incluindo SSL) e FTP.
Através desta característica também é possível usar uma das características
mais interessante desse servidor web: o redirecionamento de conexões para uma
determinada URL para uma outra máquina, que pode ser um outro host remoto ou
uma máquina da rede interna (não acessível diretamente via Internet).


O primeiro passo é ativar o módulo de proxy no arquivo
<filename>httpd.conf</filename>, basta descomentar a linha:

<screen>
# LoadModule proxy_module /usr/lib/apache/1.3/libproxy.so


O seguinte bloco pode ser colocado no final do arquivo
<filename>httpd.conf</filename> para configurar um servidor proxy para realizar
conexões diretas (sem o uso de cache) e permitir o uso de servidores proxy em
sua rede:

<screen>
# Suporte a Proxy
#
&lt;IfModule mod_proxy.c&gt;
  ProxyRequests off
  ProxyRemote * http://debian:3128
  ProxyBlock microsoft.com microsoft.com.br
  NoProxy 192.168.1.0/24
  ProxyDomain .gms.com.br

# Ativa/Desativa a manipulação de cabeçalhos HTTP/1.1 "Via:".
# 
# ("Full" adiciona a versão do servidor Apache; "Block" remove todos os cabeçalhos 
# de saída "Via:")
# Escolha uma das opções: Off | On | Full | Block
#
#ProxyVia On
#&lt;/IfModule&gt;


Segue a explicação de cada uma das diretivas acima:

<variablelist>
<varlistentry>
<term>ProxyRequests [**on/off**]
<listitem>

Ativa (on) ou Desativa (off) o serviço de proxy do servidor Apache.  Note que o
módulo <filename>libproxy.so</filename> deve estar carregado para que o bloco
&lt;IfModule libproxy.c&gt; seja processado.  A desativação desta diretiva não
afeta a diretiva **ProxyPass**.



<varlistentry>
<term>ProxyRemote [**origem**] [**URL**]
<listitem>

Esta opção é útil para fazer o Apache redirecionar suas requisições para outro
servidor proxy (como o <command>squid ou o gateway da rede, caso o
Apache estiver sendo executado em uma máquina interna).  A
**origem** pode ser uma URL completa (como
http://www.debian.org), uma URL parcial (como ftp, http) ou "*" para que o
redirecionamento seja sempre usado.



<varlistentry>
<term>ProxyBlock [**padrão**]
<listitem>

Permite bloquear o acesso a endereços que contenham o
**padrão** especificado.  Podem ser especificadas palavras,
máquinas, domínios, URLs separados por espaços.  O <command>Apache
fará a resolução DNS no caso de endereços IP e fará o cache para requisições
futuras.



<varlistentry>
<term>NoProxy [**endereços**]
<listitem>

Permite especificar endereços Internos que não serão redirecionados para o
servidor proxy especificado por **ProxyRemote**.  Podem ser
usados nomes de máquinas, endereços IP, subredes ou domínios separados por
espaços.



<varlistentry>
<term>ProxyDomain [**endereço**]
<listitem>

Especifica o endereço que será adicionado a URL caso seja recebida uma
requisição que contenha somente um nome de máquina.  É útil em redes Internas.



</variablelist>

Note que quando o suporte a proxy não está ativado no
<command>Apache, qualquer endereço de URL externa levará a página
definida pela diretiva **DocumentRoot**.  Isto deixará de
funcionar após configurar o serviço de proxy.


O uso do cache é interessante para acelerar as requisições http da rede interna
para a rede externa, desta forma, se uma requisição foi feita anteriormente,
será descarregado o arquivo do disco rígido e assim evitar uma nova conexão
externa (isto libera a rede para outras coisas).  Para configurar um cache no
serviço proxy, adicione as seguintes linhas no final do bloco anterior de
proxy:

<screen>
  # As linhas abaixo ativam o cache do apache, o cache não funcionará ao menos que
  # CacheRoot seja especificado
  CacheRoot /var/spool/apache
  CacheForceCompletion 70
  CacheSize 5
  CacheGcInterval 3
  CacheDefaultExpire 5
  CacheMaxExpire 300
  NoCache 192.168.1.0/24 a_domain.com outrodomínio.com.br outro.dominio.net


Cada diretiva acima possui o seguinte significado:

<variablelist>
<varlistentry>
<term>CacheRoot
<listitem>

Diretório base onde serão criados os outros diretórios de cache.  O cache só
será ativado se esta diretiva for definida.



<varlistentry>
<term>CacheForceCompletion [**num**]
<listitem>

Se uma transferência for cancelada e passar de **num**%, o
<command>Apache continuará a transferência e armazenará o arquivo no
cache.  O valor padrão é 90.



<varlistentry>
<term>CacheSize [**num**]
<listitem>

Define o tamanho máximo do diretório de cache do <command>Apache, em
KB.  Não especifique um valor que tome mais de 70% do espaço em disco.  O valor
padrão é 5.



<varlistentry>
<term>CacheGcInterval [**num**]
<listitem>

Define o tempo que o cache será checado em busca de arquivos maiores que o
total do cache.  Arquivos que ultrapassem o tamanho do cache são
automaticamente eliminados.



<varlistentry>
<term>CacheDefaultExpire [**num**]
<listitem>

Define o tempo que os documentos ficarão no cache, se foram transferidos
através de protocolos que não suportam horas de expiração.  O valor padrão é 1
hora.



<varlistentry>
<term>CacheMaxExpire [**num**]
<listitem>

Define o tempo que os documentos permanecerão armazenados no cache (em horas).
Esta opção ignora a hora de expiração do documento (caso fornecida).  O valor
padrão é 24 horas.



<varlistentry>
<term>NoCache [**endereços**]
<listitem>

Permite especificar lista de palavras, máquinas, domínios, IP's que não serão
armazenados no cache do <command>Apache.  Caso seja usado
<literal>NoCache * o cache será desativado completamente.  Note que o
cache também pode ser desativado comentando a diretiva
**CacheRoot**.



</variablelist>

Se você desejar um servidor cache mais flexível, rápido, dinâmico, configurável
(com possibilidade de uso de restrições baseadas em URL, tempo de acesso,
autenticação), instale o <command>squid e configure o
<command>apache para fazer forward de conexões para ele (<xref linkend="s-apache-proxy-redir"/>).

 s-apache-proxy-access">###Controlando o acesso ao servidor proxy

Incluir o bloco abaixo no arquivo <filename>access.conf</filename> para definir
o acesso dos serviços de proxy nas redes desejadas (se a sua configuração for
aberta como padrão isto pode ser opcional):

<screen>
# Acesso aos serviços proxy do apache
&lt;Directory proxy:*&gt;
    Order deny,allow
    Deny from all
    Allow from .seudominio.com.br
&lt;/Directory&gt;


Para explicações sobre o processo de bloqueio acima, veja <xref linkend="""-autor"/>.



 s-apache-proxy-redir">###Redirecionamento de conexões no Apache

Este recurso do <command>Apache é interessante para criar clusters de
servidores em sua rede interna.  O que ele faz é pegar uma requisição a um
determinado endereço e redireciona-lo a outra máquina e as respostas são
repassadas ao servidor web (para o cliente a mesma máquina esta atendendo a
requisição, para você o processamento das requisições esta sendo distribuído
internamente na rede).


As seguintes diretivas são usadas para realizar o redirecionamento de conexões:
**ProxyPass** e **ProxyPassReverse**

<variablelist>
<varlistentry>
<term>ProxyPass [**diretório_da_url** [**outro_servidor:/diretório**]
<listitem>

A **ProxyPass** permite que a URL seja redirecionada para o
servidor local e diretório especificado.  Por exemplo, assumindo que o endereço
principal de nosso servidor é <filename> [guiafoca](http://www.guiafoca.org) )</filename> e
desejamos que a URL <filename> [guiafoca](http://www.guiafoca.org) )/download</filename> seja
atendida por uma máquina localizada na nossa rede privada com o endereço
<filename>http://192.168.1.54</filename>.  Basta incluir a linha:

<screen>
ProxyPass /download http://192.168.1.54


Qualquer requisição externa a
<filename> [guiafoca](http://www.guiafoca.org) )/download/iniciante</filename> será atendida
por <filename>http://192.168.1.54/iniciante</filename>.



<varlistentry>
<term>ProxyPassRemote [**diretório_da_url** [**outro_servidor:/diretório**]
<listitem>

Esta diretiva permite modificar o cabeçalho <literal>Location nas
mensagens de respostas de redirecionamento enviadas pelo
<command>Apache.  Isto permite que o endereço retornado seja o do
servidor (que faz a interface externa com o cliente) e não da máquina do
redirecionamento.

<screen>
ProxyPass        /download http://192.168.1.54
ProxyPassReverse /download http://192.168.1.54


Se a máquina <filename>192.168.1.54</filename> redirecionar a URL para
<filename>http://192.168.1.54/download/iniciante</filename>, a resposta será
modificada para <filename> [guiafoca](http://www.guiafoca.org) )/download/iniciante</filename>
antes de ser retornada ao cliente.



</variablelist>



