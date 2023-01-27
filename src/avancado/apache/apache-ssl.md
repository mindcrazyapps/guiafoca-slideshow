<!-- Converted by db4-upgrade version 1.0 -->

 s-apache-ssl">###Uso de criptografia SSL

Esta seção é uma referência rápida para configuração e uso do módulo
<filename>apache-ssl</filename> com o servidor <command>Apache.  Este
módulo realiza a comunicação segura de dados (criptografada) via porta 443 (que
é usada como padrão quando especificamos uma url iniciando com
**https://**).  A transmissão criptografada de dados é
importante quanto temos dados confidenciais que precisamos transmitir como
movimentação bancária, senhas, número de cartões de crédito, fazer a
administração remota do servidor, etc.  SSL significa **Secure Sockets
Layer** (camada segura de transferência) e TLS **Transport
Layer Security** (camada segura de Transporte).


A intenção aqui é fornecer explicações práticas para colocar um servidor
<command>Apache com suporte a SSL funcionando no menor tempo
possível.  Detalhes sobre funcionamento de certificados, métodos de
criptografia, assinatura, etc.  deverão ser buscados na documentação deste
módulo ou em sites especializados (é um assunto muito longo).

 s-apache-ssl-s">###Servidor apache com suporte a ssl

Ao invés de utilizar o módulo <filename>mod_ssl</filename>, você poderá usar o
pacote <systemitem role="package">apache-ssl</systemitem>, ele nada mais é que
um servidor <command>Apache com o suporte SSL já incluso e não
interfere no servidor <command>Apache padrão, porque é executado
somente na porta 443.


Se você tem um grande site com configurações de acesso personalizadas, ele
trará mais trabalho de administração, pois as configurações e diretivas de
restrições de acesso deverão ser copiadas para este servidor web.  No entanto,
ele é indicado para máquinas que serão servidores SSL dedicados ou quando não
possui configurações especiais em seu servidor web principal.


Esta seção tem por objetivo a instalação do suporte ao módulo SSL
(<filename>mod_ssl</filename>) no servidor <command>Apache padrão.



 s-apache-ssl-instal">###Instalando o suporte a módulo SSL no Apache

Instale o pacote <systemitem role="package">libapache-mod-ssl</systemitem>.
Após instala-lo, edite o arquivo <filename>/etc/apache/httpd.conf</filename>
adicionando a linha:

<screen>
LoadModule ssl_module /usr/lib/apache/1.3/mod_ssl.so


Depois, gere um certificado digital ssl com o programa
<command>mod-ssl-makecert.  Ele será armazenado por padrão nos
diretórios em <filename>/etc/apache/ssl.???</filename> e seu uso explicado no
resto desta seção.



 s-apache-ssl-mkcert">###Gerando um certificado digital

O certificado digital é a peça que garante a transferência segura de dados.
Ele contém detalhes sobre a empresa que fará seu uso e quem o emitiu.  Para
gerar ou modificar um certificado digital, execute o comando
<literal>mod-ssl-makecert e siga as instruções.  O método de
criptografia usado pelo certificado digital é baseado no conceito de chave
pública/privada, a descrição sobre o funcionamento deste sistema de
criptografia é feito em <xref linkend="d-cripto-gpg"/>.


**OBS** Não utilize acentos nos dados de seu
certificado.



 s-apache-ssl-exemplo">###Exemplo de configuração do módulo mod-ssl

Abaixo uma configuração rápida para quem deseja ter um servidor com suporte a
SSL funcionando em menor tempo possível (ela é feita para operar em todas as
instalações e não leva em consideração o projeto de segurança de sua
configuração atual do <command>Apache).  Note que todas as diretivas
relacionadas com o módulo <filename>mod_ssl</filename> começam com o nome
"SSL":

<screen>
# Somente processa as diretivas relacionadas a SSL caso o módulo mod_ssl estiver
# carregado pela diretiva LoadModule
&lt;IfModule mod_ssl.c&gt;
# É necessário especificar as portas que o servidor Web aguardará conexões (normais e 
# ssl). 
Listen 80
Listen 443

# Ativa o tratamento de conexões com o destino na porta 443 pela diretiva
# VirtualHost abaixo
&lt;VirtualHost _default_:443&gt;

# Ativa ou desativa o módulo SSL para este host virtual
SSLEngine on

# Certificado do servidor
SSLCertificateFile    /etc/apache/ssl.crt/server.crt

# Chave privada de certificado do servidor. 
SSLCertificateKeyFile /etc/apache/ssl.key/server.key

# A linha abaixo força o fechamento de conexões quando a 
# conexão com o navegador Internet Explorer é interrompida. Isto
# viola o padrão SSL/TLS mas é necessário para este tipo de 
# navegador. Alguns problemas de conexões de navegadores também
# são causados por não saberem lidar com pacotes keepalive.
SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown

&lt;/VirtualHost&gt;

&lt;/IfModule&gt;

#################################################################################
# Adicionalmente poderão ser especificadas as seguintes opções para modificar   #
# o comportamento da seção SSL (veja mais detalhes na documentação do mod-ssl)  #
#################################################################################

# Formato e localização do cache paralelo de processos da seção. O cache de seção é 
# feito internamente pelo módulo mas esta diretiva acelera o processamento 
# de requisições paralelas feitas por modernos clientes navegadores. Por padrão 
# nenhum cache é usado ("none"). 
SSLSessionCache         dbm:/var/run/ssl-cache

# Localização do arquivo de lock que o módulo SSL utiliza para 
# sincronização entre processos. O padrão é nenhum. 
SSLMutex  file:/var/run/ssl-mutex

# Especifica o método de embaralhamento de dados que será utilizado
# durante o inicio de uma seção SSL (startup) ou durante o processo 
# de conexão (connect). Podem ser especificados "builtin" (é muito rápido 
# pois consome poucos ciclos da CPU mas não gera tanta combinação aleatória), um 
# programa que gera números aleatórios (com "exec") ou os dispositivos aleatórios 
# /dev/random e /dev/urandom (com "file"). Por padrão nenhuma fonte 
# adicional de números aleatórios é usada. 
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
#SSLRandomSeed startup file:/dev/urandom 512
#SSLRandomSeed connect file:/dev/urandom 512
#SSLRandomSeed connect exec:/pub/bin/NumAleat

# Tipos MIME para download de certificados
AddType application/x-x509-ca-cert .crt
AddType application/x-pkcs7-crl    .crl

# Tempo máximo de permanência dos objetos do cache acima. O valor padrão é 
# 300 segundos (5 minutos).
SSLSessionCacheTimeout  300

# Versão do protocolo SSL que será usada. Podem ser especificadas 
# SSLv2, SSLv3 TLSv1 ou all. O mais compatível com os navegadores atuais 
# é o "SSLv2". Por padrão "all" é usado.
#SSLProtocol all
#SSLProtocol -all +SSLv3

# Registra detalhes sobre o tráfego neste arquivo. Mensagens de erro 
# também são armazenadas no arquivo de registro padrão do Apache
SSLLog      /var/log/apache/ssl-mod.log

# Nível das mensagens de log registradas por SSLLog
SSLLogLevel info


Algumas diretivas deste módulo podem fazer parte tanto da configuração global
do servidor como diretivas de acesso (<literal>Directory,
<literal>Location, <literal>.htaccess, veja a opção
"Context" na documentação do <filename>mod_ssl</filename>).



 s-apache-ssl-sslreq">###Autorizando acesso somente a conexões SSL

Existem casos que precisa restringir o uso de conexões normais e permitir
somente conexões via SSL (como por exemplo, dentro da diretiva de acesso que
controla seu acesso a uma página com listagem de clientes).  A opção
**SSLRequereSSL** é usada para tal e deve ser usada dentro das
diretivas de controle acesso:

<screen>
&lt;Directory /var/www/secure/clientes&gt;
 Options Indexes 
 Order deny,allow
 Deny from evil.cracker.com
 SSLRequireSSL
&lt;/Directory&gt;


A diretiva acima **requer** que sejam feitas conexões SSL
(porta 443 - https://) para acesso ao diretório
<filename>/var/www/secure/clientes</filename>, qualquer conexão padrão não
criptografada (feita na porta 80) será rejeitada com o erro 403.


**OBS:** A diretiva
**SSLRequireSSL** podia ser colocada entre as condicionais
"IfModule mod_ssl.c" mas o servidor web permitiria conexões não criptografadas
se por algum motivo esse módulo não estivesse carregado.  Na configuração
acima, ocorrerá um erro e impedirá o funcionamento do servidor web caso ocorra
algum problema com o <filename>mod_ssl</filename>.



 s-apache-ssl-inic">###Iniciando o servidor Web com suporte a SSL

Verifique se a configuração do <command>Apache está ok com
<literal>apache -t.  Caso positivo, reinicie o servidor usando um dos
métodos descritos em <xref linkend="s-apache-rodando"/>.  O servidor web lhe
pedirá a FraseSenha para descriptografar a chave privada SSL (esta senha foi
escolhida durante o processo de criação do certificado).


Esta senha garante uma segurança adicional caso a chave privada do servidor
seja copiada de alguma forma.  Somente quem tem conhecimento da FraseSenha
poderá iniciar o servidor com suporte a transferência segura de dados.
Verifique se o virtual host está servindo as requisições na porta 443 com
<literal>apache -S.


O único método para fazer o servidor web evitar de pedir a senha para
descriptografar a chave privada é colocando uma senha em branco.  Isto só é
recomendado em ambientes seguros e o diretório que contém a chave privada
deverá ter somente permissões para o dono/grupo que executa o servidor Web.
Qualquer outra permissão poderá por em risco a segurança da instalação caso a
chave privada seja roubada.  Depois disso, execute o comando:

<screen>
# entre no diretório que contém a chave privada
cd /etc/apache/ssl.key
# renomeie a chave privada para outro nome
ren server.key server.key-Csenha
openssl rsa -in server.key-Csenha -out server.key


Digite a senha quando pedido.  A chave original (com senha) estará gravada no
arquivo <filename>server.key-Csenha</filename> e poderá ser restaurada se
necessário.  Reinicie o servidor <command>Apache, desta vez ele não
pedirá a senha.


**OBS1:** Tire uma cópia de segurança da chave
privada original antes de executar esta operação.


**OBS2:** Não se esqueça de ajustar as
permissões de acesso no diretório <filename>/etc/apache/ssl.key</filename> caso
não utilize senha para proteger seu certificado digital.





