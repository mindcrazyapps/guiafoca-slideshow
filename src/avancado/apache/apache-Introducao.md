<?xml version="1.0" encoding="UTF-8"?>
 
 s-apache-intro">###Introdução

O servidor web é um programa responsável por disponibilizar páginas, fotos, ou
qualquer outro tipo de objeto ao navegador do cliente.  Ele também pode operar
recebendo dados do cliente, processando e enviando o resultado para que o
cliente possa tomar a ação desejada (como em aplicações CGI's, banco de dados
web, preenchimento de formulários, etc).


O <command>Apache é um servidor Web extremamente configurável,
robusto e de alta performance desenvolvido por uma equipe de voluntários
(conhecida como <literal>Apache Group) buscando criar um servidor web
com muitas características e com código fonte disponível gratuitamente via
Internet.  Segundo a Netcraft http://www.w3.org/1999/xlink) [](http://www.netcraft.com)http://www.netcraft.com/), o
<command>Apache é mais usado que todos os outros servidores web do
mundo juntos.


Este capítulo não tenta ser um guia completo ao <command>Apache, mas
tentará mostrar como sua estrutura é organizada, as diretivas principais de
configuração, diretivas de segurança, virtual hosting, proxy, o uso de
utilitários de gerenciamento do servidor, como personalizar algumas partes do
servidor e programas úteis de terceiros para análise e diagnóstico do servidor
web.  Não deixe também de ver <xref linkend="s-apache-exemplo"pois contém
diretivas básicas de configuração comentadas e explicações interessante e faz
parte do aprendizado.


 s-apache-versao">###Versão

É assumido que esteja usando a versão 1.3.22 do <command>apache.  As
explicações contidas aqui podem funcionar para versões posteriores, mas é
recomendável que leia a documentação sobre modificações no programa (changelog)
em busca de mudanças que alterem o sentido das explicações fornecidas aqui.



 s-apache-historia">###Um resumo da História do Apache

O <command>Apache tem como base o servidor web <command>NCSA
1.3 (**National Center of Supercomputing
Applications**), que foi desenvolvido por Rob McCool.  Quando Rob
deixou o NCSA, o desenvolvimento foi interrompido, assim muitos desenvolvedores
buscaram personalizar sua própria versão do NCSA ou adicionar mais
características para atender as suas necessidades.  Neste momento começa a
história do <command>Apache com **Brian Behlendorf**
e **Cliff Skolnick** abrindo uma lista de discussão para
interessados no desenvolvimento, conseguindo espaço em um servidor doado pela
**HotWired** e trocando patches corrigindo problemas,
adicionando recursos e discutindo idéias com outros desenvolvedores e hackers
interessados neste projeto.


A primeira versão oficial do <command>Apache foi a 0.6.2, lançada em
Abril de 1995 (neste período a NCSA retomava o desenvolvimento de seu servidor
web, tendo como desenvolvedores **Brandon Long** e
**Beth Frank** que também se tornaram membros especiais do
grupo <command>Apache, compartilhando idéias sobre seus projetos).


Nas versões 2.x do Apache, a escalabilidade do servidor foi ampliada suportando
as plataformas <command>Win32 (não obtendo o mesmo desempenho que em
plataformas UNIX mas sendo melhorado gradativamente).



 s-apache-contribuindo">###Enviando Correções/Contribuindo com o projeto

Um formulário está disponível na Web para o envio de correções/sugestões em
<literal>("http://www.w3.org/1999/xlink) [](http://www.apache.org/bug_report.html)http://www.apache.org/bug_report.html/.
Uma lista de anuncio sobre o <command>Apache está disponível em
<email>apache-announce@apache.org que divulgam correções, novas versões
e realização de eventos.


Mais detalhes sobre o desenvolvimento do Apache podem ser visualizadas na URL
<literal>("http://www.w3.org/1999/xlink) [](http://dev.apache.org)http://dev.apache.org/.



 s-apache-caracteristicas">###Características do Apache

Abaixo estão algumas características que fazem esse servidor web o preferido
entre os administradores de sistemas:

<itemizedlist>
<listitem>

Possui suporte a scripts cgi usando linguagens como **Perl, PHP, Shell
Script, ASP, etc**.


<listitem>

Suporte a autorização de acesso podendo ser especificadas restrições de acesso
separadamente para cada endereço/arquivo/diretório acessado no servidor.


<listitem>

Autenticação requerendo um nome de usuário e senha válidos para acesso a alguma
página/sub-diretório/arquivo (suportando criptografia via Crypto e MD5).


<listitem>

Negociação de conteúdo, permitindo a exibição da página Web no idioma
requisitado pelo Cliente Navegador.


<listitem>

Suporte a tipos mime.


<listitem>

Personalização de logs.


<listitem>

Mensagens de erro.


<listitem>

Suporte a virtual hosting (é possível servir 2 ou mais páginas com endereços/
portas diferentes através do mesmo processo ou usar mais de um processo para
controlar mais de um endereço).


<listitem>

Suporte a IP virtual hosting.


<listitem>

Suporte a name virtual hosting.


<listitem>

Suporte a servidor Proxy ftp e http, com limite de acesso, caching (todas
flexivelmente configuráveis).


<listitem>

Suporte a proxy e redirecionamentos baseados em URLs para endereços Internos.


<listitem>

Suporte a criptografia via SSL,Certificados digitais


<listitem>

Módulos DSO (Dynamic Shared Objects) permitem adicionar/remover funcionalidades
e recursos sem necessidade de recompilação do programa.





 s-apache-ficha">###Ficha técnica

Pacote: <systemitem role="package">apache</systemitem>


Utilitários:

<itemizedlist>
<listitem>

<literal>apache - Servidor Web Principal


<listitem>

<literal>apachectl - Shell script que faz interface com o
<command>apache de forma mais amigável


<listitem>

<literal>apacheconfig - Script em Perl para configuração interativa
básica do <command>Apache


<listitem>

<literal>htpasswd - Cria/Gerencia senhas criptografadas Crypto/MD5


<listitem>

<literal>htdigest - Cria/Gerencia senhas criptografadas Crypto/MD5


<listitem>

<literal>dbmmanage - Cria/Gerencia senhas em formato DBM (Perl)


<listitem>

<literal>logresolve - Faz um DNS reverso dos arquivos de log do
<command>Apache para obter o endereço de hosts com base nos endereços
IP's.


<listitem>

<literal>ab - Apache Benchmarcking - Ferramenta de medida de
desempenho do servidor Web Apache.




Por padrão, os arquivos de configuração do <command>Apache residem no
diretório <filename>/etc/apache</filename>:

<variablelist>
<varlistentry>
<term>httpd.conf
<listitem>

Arquivo de configuração principal do <command>Apache, possui
diretivas que controlam a operação do daemon servidor.  Um arquivo de
configuração alternativo pode ser especificado através da opção "-f" da linha
de comando.



<varlistentry>
<term>srm.conf
<listitem>

Contém diretivas que controlam a especificação de documentos que o servidor
oferece aos clientes.  O nome desse arquivo pode ser substituído através da
diretiva ResourceConfig no arquivo principal de configuração.



<varlistentry>
<term>access.conf
<listitem>

Contém diretivas que controlam o acesso aos documentos.  O nome desse arquivo
pode ser substituído através da diretiva **AccessConfig** no
arquivo principal de configuração.



</variablelist>

O servidor Web lê os arquivos acima na ordem que estão especificados
(<filename>httpd.conf</filename>, <filename>srm.conf</filename> e
<filename>access.conf</filename>).  As configurações também podem ser
especificadas diretamente no arquivo <filename>httpd.conf</filename>.  Note que
não é obrigatório usar os arquivos <filename>srm.conf</filename> e
<filename>access.conf</filename>, mas isto proporciona uma melhor organização
das diretivas do servidor, principalmente quando se tem um grande conjunto de
diretivas.  Um exemplo comentado destes três arquivos de configuração é
encontrado em <xref linkend="s-apache-exemplo"/>.



 s-apache-hwreq">###Requerimentos

A máquina mínima para se rodar um servidor <command>Apache para
atender a uma rede padrão 10MB/s é um Pentium 90, 24MB de RAM, um HD com um bom
desempenho e espaço em disco considerável de acordo com o tamanho projetado de
seu servidor web (considerando seu crescimento).


Uma configuração mais rápida para redes 100MB/s teria como processador um Cyrix
MX ou Intel Pentium MMX como plataforma mínima (Cyrix é o recomendado pelo alto
desempenho no processamento de strings), barramento de HD SCSI com uma boa
placa controladora (Adaptec 19160 ou superior) com 64MB de RAM no mínimo.



 s-apache-logs">###Arquivos de log criados pelo Apache

O servidor <command>httpd grava seus arquivos de log geralmente em
<filename>/var/log/apache</filename>, não é possível descrever os arquivos de
logs usados porque tanto seus nomes como conteúdo podem ser personalizados no
arquivo <filename>httpd.conf</filename>.  Mesmo assim, os arquivos de logs
encontrados na instalação padrão do <command>Apache são os seguintes:

<itemizedlist>
<listitem>

<filename>access.log</filename> - Registra detalhes sobre o acesso as páginas
do servidor <command>httpd.


<listitem>

<filename>error.log</filename> - Registra detalhes saber erros de acesso as
páginas ou erros internos do servidor.


<listitem>

<filename>agent.log</filename> - Registra o nome do navegador do cliente (campo
<replaceable>UserAgent</replaceable> do cabeçalho http).




Mais referências podem ser encontradas em <xref linkend="s-apache-log"/>.  Um
bom programa para geração de estatísticas de acesso com gráficos é o <xref linkend="s-apache-log-webalizer"/>.



 s-apache-install">###Instalação

<literal>apt-get install apache apache-doc


(o pacote <systemitem role="package">apache-doc</systemitem> contém a
documentação de referencia do <command>Apache, é recomendável
instala-lo se estiver curioso e deseja entender melhor seu funcionamento ou
consultar diretivas).



 s-apache-rodando">###Iniciando o servidor/reiniciando/recarregando a configuração

O <command>Apache pode ser executado tanto como um servidor
**Inetd** ou como um **Daemon**.  A
inicialização de programas pelo **Inetd** é uma boa estratégia
quando você precisa de um controle de acesso básico (o fornecido pelo
<command>tcpd), e o serviço é pouco usado na máquina.


A segurança de um serviço iniciado pelo <command>inetd pode ser
substituída e melhorada por um firewall bem configurado, garantindo facilidades
extras como um relatório de tráfego para a porta do servidor web, por exemplo.
Mesmo assim se o servidor <command>Apache estiver rodando como daemon
e estiver ocioso, ele será movido para swap liberando a memória RAM para a
execução de outros programas.


Neste capítulo será assumido seu funcionamento do <command>Apache
como Daemon, que é o método de funcionamento recomendado para sites de grande
tráfego onde ele é freqüentemente requisitado e considerado um serviço crítico.


O método padrão para iniciar programas como daemons na
<command>Debian é através dos diretórios
<filename>/etc/rc?.d</filename>.  Cada diretório deste contém os programas que
serão executados/interrompidos no nível de execução "?"
(<filename>rc1.d/</filename>, <filename>rc2.d/</filename> ...).  O conteúdo
destes diretórios são links para os scripts originais em
<filename>/etc/init.d/programa</filename>, o nosso programa alvo é
<filename>/etc/init.d/apache</filename>.  O
<filename>/etc/init.d/apache</filename> aceita os seguintes parâmetros:

<itemizedlist>
<listitem>

<literal>start - Inicia o <command>Apache


<listitem>

<literal>stop - Finaliza o <command>Apache


<listitem>

<literal>restart - Reinicia o <command>Apache, efetuando
uma pausa de 5 segundos entre a interrupção do seu funcionamento e reinicio.


<listitem>

<literal>reload - Recarrega os arquivos de configuração do
<literal>Apache, as alterações entram em funcionamento imediatamente.


<listitem>

<literal>reload-modules - Recarrega os módulos.  Basicamente é feito
um restart no servidor.


<listitem>

<literal>force-reload - Faz a mesma função que o reload




Para reiniciar o <command>Apache usando o
<filename>/etc/init.d/apache</filename>, digite:


./etc/init.d/apache restart


ou


<literal>cd /etc/init.d;./apache restart


Na realidade, o que o <filename>/etc/init.d/apache</filename> faz é interagir
diretamente com o shell script <command>apachectl.


O <command>apachectl recebe os parâmetros enviados pelo usuário e
converte para sinais que serão enviados para o binário
<command>apache.  Da mesma forma ele verifica os códigos de saída do
<command>apache e os transforma em mensagens de erro legíveis para o
usuário comum.  Os seguintes comandos são aceitos pelo
<command>apachectl:

<itemizedlist>
<listitem>

<literal>httpd-server/start - Inicia o <command>Apache


<listitem>

<literal>stop - Finaliza o <command>Apache (enviando um
sinal TERM)


<listitem>

<literal>restart - Reinicia o <command>Apache (enviando um
sinal HUP)


<listitem>

<literal>graceful - Recarrega os arquivos de configuração do
<command>Apache (enviando um sinal USR1)


<listitem>

<literal>fullstatus - Mostra o status completo do servidor
<command>Apache (requer o <command>lynx e o módulo
**mod_status** carregado).


<listitem>

<literal>status - Mostra o status do processo do servidor
<command>Apache (requer o <command>lynx e o módulo
**mod_status** carregado).


<listitem>

<literal>configtest - Verifica se a sintaxe dos arquivos de
configuração está OK (executa um <literal>apache -t).





 s-apache-opcoescmd">###Opções de linha de comando
<itemizedlist>
<listitem>

<literal>-D nome - define um nome que será usado na diretiva
&lt;IfDefine nome&gt;.


<listitem>

<literal>-d diretório - especifica o diretório
**ServerRoot** (substitui o do arquivo de configuração).


<listitem>

<literal>-f arquivo - especifica um arquivo
**ServerConfigFile** alternativo.


<listitem>

<literal>-C "diretiva" - processa a diretiva antes de ler os arquivo
de configuração.


<listitem>

<literal>-c "diretiva" - processa a diretiva depois de ler os
arquivos de configuração.


<listitem>

<literal>-v - mostra a versão do programa.


<listitem>

<literal>-V - mostra opções usadas na compilação do
<command>Apache.


<listitem>

<literal>-h - Mostra o help on-line do programa


<listitem>

<literal>-l - lista módulos compilados junto com o Apache (embutidos)


<listitem>

<literal>-L - lista diretivas de configurações disponíveis


<listitem>

<literal>-S - Mostra configurações de Virtual Hosting


<listitem>

<literal>-t - executa a checagem de sintaxe nos arquivos de
configuração do Apache (incluindo a checagem da diretiva
**DocRoot**).


<listitem>

<literal>-T - executa a checagem de sintaxe nos arquivos de
configuração do <command>Apache (menos da diretiva
**DocRoot**).








