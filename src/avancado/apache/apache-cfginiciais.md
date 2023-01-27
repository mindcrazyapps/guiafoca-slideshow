<!--- <?xml version="1.0" encoding="utf-8" ?> --->
 
 s-apache-cfgini">###Configurações Básicas do Apache
    
        Esta seção traz algumas configurações obrigatórioas para quem 
        está iniciando a configuração do servidor web Apache.
    

 s-apache-port">###Configurando a porta padrao
    
    Use a diretiva **Port** para configurar a porta padrão que o
    <command>Apache receberá requisições por padrão.  A diretiva
    **Listen** também é usada para ajustar o endereço/portas
    alternativas (usadas também em <literal>Virtual Hosts) e substituirá
    as definições de **Port**(veja <xref linkend="s-apache-listen"para detalhes).
    
    
    **OBS:**: Somente uma diretiva
    **Port** e um argumento poderão ser especificados.  Para mais
    controle sobre as portas do sistema use a diretiva **Listen**.
    


 s-apache-adicpagina">###Adicionando uma página no Apache
    
    Existem dois tipos de páginas que podem ser adicionadas ao
    <command>Apache: a página raíz e sub-páginas.
    
    <variablelist>
    <varlistentry>
    <term>**Página Raíz**
    <listitem>
    
    A página raíz é especificada através da diretiva
    **DocumentRoot** e será mostrada quando se entrar no domínio
    principal, como <filename> [guiafoca](http://www.guiafoca.org) )</filename>.  Na configuração
    padrão do <command>Apache, **DocumentRoot** aponta
    para o diretório <filename>/var/www</filename>.  Este diretório será assumido
    como **raíz** caso os diretórios não sejam
    iniciados por uma <filename>/</filename>:
    
    <itemizedlist>
    <listitem>
    
    <filename>home/focalinux</filename> - Aponta para
    <filename>/var/www/home/focalinux</filename>
    
    
    <listitem>
    
    <filename>/home/focalinux</filename> - Aponta para
    <filename>/home/focalinux</filename>
    
    
    
    
    Este diretório deve conter um arquivo de índice válido (especificado pela
    diretiva **DocumentIndex** no <filename>srm.conf</filename>) e
    permissões de acesso válidas no arquivo <filename>access.conf</filename> para
    autorizar o acesso as páginas em <filename>/var/www</filename> (veja <xref linkend=""""para detalhes).
    
    
    
    <varlistentry>
    <term>Sub-páginas
    <listitem>
    
    Sub páginas são armazenadas abaixo do diretório da **Página
    raíz**, como <filename> [guiafoca](http://www.guiafoca.org) )/download</filename>.
    Elas podem ser um subdiretório da página principal em
    <filename>/var/www</filename> ou serem criadas através da diretiva
    **Alias** no arquivo <filename>srm.conf</filename>.  Caso seja
    um sub-diretório, as permissões de acesso de <filename>/var/www</filename>
    serão herdadas para este subdiretório, mas também poderão ser modificadas com a
    especificação de uma nova diretiva de acesso.
    
    
    Através da diretiva **Alias** a página pode estar localizada
    em outro diretório do disco (até mesmo outro sistema de arquivos) e as
    permissões de acesso deverão ser definidas para aquela página.  Para criar um
    endereço <filename> [guiafoca](http://www.guiafoca.org) )/iniciante</filename> que aponta para
    o diretório <filename>/home/focalinux/download/iniciante</filename> no disco
    local, basta usar a seguinte diretiva no <filename>srm.conf</filename>:
    
    <screen>
    Alias /iniciante /home/focalinux/download/iniciante
    
    
    Pode ser necessário permitir o acesso a nova página caso o servidor tenha uma
    configuração restritiva por padrão (veja <xref linkend=""""para detalhes).  Após isto, faça o servidor
    <command>httpd re-ler os arquivos de configuração ou reinicia-lo.
    Após isto, a página <filename>/home/focalinux/download/iniciante</filename>
    estará acessível via <filename> [guiafoca](http://www.guiafoca.org) )/iniciante</filename>.
    
    
    **OBS:** Caso inclua uma <filename>/</filename>
    no diretório que será acessível via URL, o endereço somente estará disponível
    caso você entre com <filename>/</filename> no final da URL:
    
    <screen>
    Alias /doc/ /usr/doc/
    
    
    O diretório <filename>/doc</filename> somente poderá ser acessado usando
    <filename> [guiafoca](http://www.guiafoca.org) )/doc/</filename>, o uso de
    <filename> [guiafoca](http://www.guiafoca.org) )/doc</filename> retornará uma mensagem de URL
    não encontrada.
    
    
    
    </variablelist>


 s-apache-bindaddress">###Configurando as interfaces que o Apache atenderá
    
    A diretiva **BindAddress** é usada para especificar endereços
    IP das interfaces ou endereços FQDN que o <command>Apache responderá
    requisições.  Mais de um endereço podem ser especificados separados por
    espaços.  Caso não seja definido, o <command>Apache assumirá o valor
    "*" (atenderá requisições vindas de qualquer interface).
    
    
    **OBS1:** - É permitido usar somente uma
    diretiva **BindAddress**.  A diretiva
    **Listen** deverá ser usada se desejar mais controle sobre as
    portas do servidor web.  Veja <xref linkend="s-apache-listen"para detalhes.
    
    
    **OBS2:** - As interfaces especificadas pela
    diretiva **Listen** substituirá as especificadas em
    **BindAddress**.
    
    
    Exemplo:
    
    <itemizedlist>
    <listitem>
    
    <literal>BindAddress 192.168.1.1 - Especifica que os usuários da
    faixa de rede <filename>192.168.1.*</filename> terão acesso ao servidor
    <command>httpd.  Isto assume que a máquina possui o endereço
    <filename>192.168.1.1</filename> em sua interface de rede interna.
    
    
    <listitem>
    
    <literal>BindAddress * - Atenderá requisições vindas de qualquer
    interface de rede.
    
    
    
    
    
     s-apache-listen">###Especificando endereços/portas adicionais (a diretiva **Listen**)
        
        A diretiva **Listen** é usada para se ter um controle maior
        sobre a especificação de endereços/portas alternativas que o servidor web
        esperará por requisições externas.  Esta diretiva é muito usada na construção
        de **Virtual Hosts**.  Esta diretiva pode substituir
        completamente as diretivas **Port** e
        **BindAddress**.  Podem ser usados o número da porta, ou o par
        <literal>endereço:porta:
        
        <screen>
        Listen 192.168.1.1:80
        Listen 192.168.7.1:81
        Listen 60000
        
        
        O endereço que deverá ser usado é o da interface de rede (assim como na
        diretiva **BindAddress**).  No exemplo acima, o servidor
        <command>httpd esperará por requisições vindas de
        <filename>192.168.1.*</filename> na porta 80 e também 60000, e requisições
        vindas de 192.168.7.1 na porta 81 e também 60000.
        
    
    


