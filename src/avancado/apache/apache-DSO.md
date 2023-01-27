<!-- Converted by db4-upgrade version 1.0 -->

 s-apache-dso">###Módulos DSO

Os módulos **DSO** permitem adicionar/remover características
do <command>Apache sem necessidade de recompilar todo o servidor web,
assim interrompendo o serviço para a atualização dos arquivos.  Módulos de
programas terceiros também podem ser compilados e adicionado sem problemas
através deste recurso.


Os módulos são carregados para a memória no momento que o
<command>apache é iniciado através da diretiva
**LoadModule** no arquivo de configuração.  Dessa forma, toda
vez que um novo módulo for adicionado, removido ou alterado, será necessário
reiniciar o servidor <command>apache.  A sintaxe da linha para
carregar módulos <filename>.so</filename> é a seguinte:


<literal>LoadModule [**nome_do_modulo**]
[**caminho_do_arquivo_so**]

<variablelist>
<varlistentry>
<term>**nome_do_modulo**
<listitem>

Especifica o nome do módulo, não deve conter espaços.



<varlistentry>
<term>**caminho_do_arquivo_so**
<listitem>

Define a localização do arquivo que contém o módulo especificado.  Por padrão
os módulos estão localizados em <filename>/usr/lib/apache/[versão]</filename>



</variablelist>

A posição em que os módulos aparecem podem ter influência em seu funcionamento,
alguns requerem que sejam especificados antes de outros módulos para
funcionarem corretamente (como o módulo **php3_module**, que
deve ser carregado antes de qualquer módulo de controle de CGI's).  Leia a
documentação específica sobe o módulo em caso de dúvidas, os módulos que
acompanham o <command>Apache são documentados em detalhes no manual
do <command>Apache.


Para usar uma característica/diretiva/opção do <command>Apache que
dependa de um certo módulo, obviamente você deverá carregar o módulo
correspondente (em caso de dúvidas, leia a documentação sobre o módulo).  Veja
a <xref linkend="s-apache-exemplo-httpd"para exemplos do uso da diretiva
**LoadModule**.


Por exemplo, se você quiser utilizar as diretivas de autorização
(**allow, deny, order**) deverá ter o módulo
**mod_access** carregado, para usar as diretivas de
autorização (**authname, authuserfile, authtype, etc**) deverá
ter o módulo **mod_auth** carregado.  Mais detalhes podem ser
encontrados em <xref linkend="""-autor"/>.  **OBS1**: O suporte a **DSO** atualmente
só está disponível para plataforma <command>UNIX e seus derivados,
como o <command>Linux.


Também é possível ativar certas diretivas verificando se o módulo
correspondente estiver ou não carregado através da diretiva
**IfModule**:

<screen>
&lt;IfModule mod_userdir.c&gt;
 UserDir disabled root
 UserDir public_html
&lt;/IfModule&gt;


Nas linhas acima, as diretivas **UserDir** somente serão
executadas se o módulo **mod_userdir.c** estiver carregado
através da diretiva **LoadModule**.


Segue abaixo uma lista de módulos padrões que acompanham do
<command>Apache, os módulos marcados com "*" são ativados por padrão:

<variablelist>
<varlistentry>
<term>Criação de Ambiente
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_env - Ajusta variáveis de ambiente para scripts
CGI/SSI


<listitem>

<literal>* mod_setenvif - Ajusta variáveis de ambiente de acordo com
cabeçalhos http


<listitem>

<literal>mod_unique_id - Gera identificadores únicos para requisições





<varlistentry>
<term>Decisão de tipo de conteúdo de arquivos
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_mime - Determinação de tipo/encodificação do conteúdo
(configurado)


<listitem>

<literal>mod_mime_magic - Determinação de tipo/encodificação do
conteúdo (automático)


<listitem>

<literal>* mod_negotiation - Seleção de conteúdo baseado nos
cabeçalhos "HTTP Accept*"





<varlistentry>
<term>Mapeamento de URL
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_alias - Tradução e redirecionamento de URL simples


<listitem>

<literal>mod_rewrite - Tradução e redirecionamento de URL avançado


<listitem>

<literal>* mod_userdir - Seleção de diretórios de recursos por nome
de usuário


<listitem>

<literal>mod_speling - Correção de URLs digitadas incorretamente


<listitem>

<literal>mod_vhost_alias - Suporte para virtual hosts dinamicamente
configurados em massa.





<varlistentry>
<term>Manipulação de Diretórios
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_dir - Manipulação de Diretório e arquivo padrão de
diretório


<listitem>

<literal>* mod_autoindex - Geração de índice automático de diretório





<varlistentry>
<term>Controle de Acesso
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_access - Controle de acesso por autorização (usuário,
endereço, rede)


<listitem>

<literal>* mod_auth - Autenticação HTTP básica (usuário, senha)


<listitem>

<literal>mod_auth_dbm - Autenticação HTTP básica (através de arquivos
NDBM do Unix)


<listitem>

<literal>mod_auth_db - Autenticação HTTP básica (através de arquivos
Berkeley-DB)


<listitem>

<literal>mod_auth_anon - Autenticação HTTP básica para usuários no
estilo anônimo


<listitem>

<literal>mod_auth_digest - Autenticação MD5


<listitem>

<literal>mod_digest - Autenticação HTTP Digest





<varlistentry>
<term>Respostas HTTP
<listitem>
<itemizedlist>
<listitem>

<literal>mod_headers - Cabeçalhos de respostas HTTP (configurado)


<listitem>

<literal>mod_cern_meta - Cabeçalhos de respostas HTTP (arquivos no
estilo CERN)


<listitem>

<literal>mod_expires - Respostas de expiração HTTP


<listitem>

<literal>* mod_asis - Respostas HTTP em formato simples (raw)





<varlistentry>
<term>Scripts
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_include - Suporte a Includes no lado do servidor (SSI
- Server Sides Includes)


<listitem>

<literal>* mod_cgi - Suporte a CGI (Common Gateway Interface)


<listitem>

<literal>* mod_actions - Mapeia scripts CGI para funcionarem como
'handlers' internos.





<varlistentry>
<term>Manipuladores de conteúdo Interno
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_status - Visualiza status do servidor em tempo de
execução.


<listitem>

<literal>mod_info - Visualiza sumário de configuração do servidor.





<varlistentry>
<term>Registros de Requisições
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_log_config - Registro de requisições personalizáveis


<listitem>

<literal>mod_log_agent - Registro especializado do User-Agent HTTP
(depreciado)


<listitem>

<literal>mod_log_refer - Registro especializado do Referrer HTTP
(depreciado)


<listitem>

<literal>mod_usertrack - Registro de cliques de usuários através de
Cookies HTTP





<varlistentry>
<term>Outros
<listitem>
<itemizedlist>
<listitem>

<literal>* mod_imap - Suporte a Mapeamento de Imagem no lado do
servidor.


<listitem>

<literal>mod_proxy - Módulo de Cache do Proxy (HTTP, HTTPS, FTP).


<listitem>

<literal>mod_so - Inicialização do Dynamic Shared Object (DSO)





<varlistentry>
<term>Experimental
<listitem>
<itemizedlist>
<listitem>

<literal>mod_mmap_static - Cache de páginas freqüentemente servidas
via mmap()





<varlistentry>
<term>Desenvolvimento
<listitem>
<itemizedlist>
<listitem>

<literal>mod_example - Demonstração da API do Apache (somente
desenvolvedores)





</variablelist>


