<!-- Converted by db4-upgrade version 1.0 -->
 
 s-apache-vhosts">###Virtual Hosts

Virtual Hosts (sites virtuais) é um recurso que permite servir mais de um site
no mesmo servidor.  Podem ser usadas diretivas específicas para o controle do
site virtual, como nome do administrador, erros de acesso a página, controle de
acesso e outros dados úteis para personalizar e gerenciar o site.  Existem 2
métodos de virtual hosts:

<itemizedlist>
<listitem>

<literal>Virtual Hosts baseados em IP - Requer um endereço IP
diferente para cada site.  Este poderá ser um IP real (da interface de rede) ou
um apelido (veja <xref linkend="cfgrede-ipalias"/>), o que interessa é que deve
haver um endereço IP diferente para cada site.  O número de sites servidos
estará limitado a quantidade de endereços IP disponíveis em sua classe de rede.
Veja <xref linkend="s-apache-vhosts-ip"para detalhes de como construir um
virtual host deste tipo.


O <command>apache foi um dos primeiros servidores web a incluir
suporte a virtual hosts baseados em IP.


<listitem>

<literal>Virtual Hosts baseados em nome - Este utiliza nomes para
identificar os sites servidos e requerem somente um endereço IP.  Desta maneira
é possível servir um número ilimitado de sites virtuais.  O navegador do
cliente deve suportar os cabeçalhos necessários para garantir o funcionamento
deste recurso (praticamente todos os navegadores atuais possuem este suporte).
Veja <xref linkend="s-apache-vhosts-nome"para detalhes de como construir um
virtual host deste tipo.




As explicações desta seção são baseadas na documentação do
<command>Apache.


 s-apache-vhosts-ip">###Virtual hosts baseados em IP

Existem duas maneiras de rodar este tipo de host virtual: Através de daemons
<command>httpd separados ou em um único daemon
<command>httpd usando a diretiva &lt;VirtualHost&gt;.


As vantagens do uso de **daemons separados** para servir
requisições é a proteção sob **UID** e
**GID** diferente dos outros servidores, assim o administrador
do **site1** não terá acesso ao
<filename>httpd.conf</filename>, página do <filename>site2</filename> (porque
ele estará rodando sob uma **UID** e **GID**
diferentes e o acesso é restrito).  Para usar este método, especifique a opção
**-f [arquivo_cfg]** para utilizar um arquivo de configuração
personalizado e a diretiva **Listen endereço:porta** para
dizer onde o servidor aguardará as requisições.


As vantagens do uso de um **mesmo daemon** para servir as
requisições são: quando não há problema se os administradores de outros sites
tenham acesso ao mesmo arquivo de configuração ou quando há a necessidade de
servir muitas requisições de uma só vez (quanto menos servidores web estiverem
em execução, melhor o desempenho do sistema).  Abaixo um exemplo de
configuração de virtual hosts servindo os sites
<literal>www.site1.com.br e <literal>www.site2.com.br:

<screen>
ServerAdmin webmaster@site.com.br

&lt;VirtualHost www.site1.com.br&gt;
 ServerName www.site1.com.br
 ServerAdmin site1@site1.com.br
 DocumentRoot /var/www/www_site1_com_br
 TransferLog /var/log/apache/site1/access.log
 ErrorLog /var/log/apache/site1/error.log
 User www-data
 Group www-data
&lt;/VirtualHost&gt;

&lt;VirtualHost www.site2.com.br&gt;
 ServerName www.site2.com.br
 DocumentRoot /var/www/www_site2_com_br
 CustomLog /var/log/apache/site2/access.log combined
 ErrorLog /var/log/apache/site2/error.log
&lt;/VirtualHost&gt;


Qualquer diretiva dentro de &lt;VirtualHost&gt; controlarão terão efeito no
site virtual especificado.  Quando uma diretiva não for especificada dentro de
&lt;VirtualHost&gt;, serão usados os valores padrões especificados no arquivo
de configuração do <command>Apache (como a diretiva
**ServerAdmin webmaster@site.com.br** que será usado como
padrão na configuração de **www.site2.com.br**).


Digite <literal>apache -S para ver suas configurações de virtual
hosts atual.


**OBS1:** Desative a diretiva
<literal>UseCanonicalName off quando utilizar o recurso de máquinas
virtuais, esta diretiva faz que o nome do servidor retornado usando o valor em
<literal>ServerName quando o cliente digita um endereço qualquer.


**OBS2:** Utilize sempre que possível endereços
IP em configurações críticas, assim os serviços não serão tão vulneráveis a
possíveis falsificações ou erros.  Veja <xref linkend="rede-dns-a-hostconf"e
<xref linkend="fw-iptables-outras-ipspoof"/>.  Leia também a seção <xref linkend="s-apache-vhosts-dnssec"/>.


**OBS3:** Não permita que outros usuários a não
ser o root e o dono do processo <command>Apache (especificado pela
diretiva **User**) tenham acesso de gravação aos logs gerados
pelo servidor, pois os dados podem ser apagados ou criados links simbólicos
para binários do sistema que serão destruídos quando o
<command>Apache gravar dados.  Alguns binários e bibliotecas são
essenciais para o funcionamento do sistema.



 s-apache-vhosts-nome">###Virtual hosts baseados em nome

Este método é idêntico ao baseado em IP, em especial adicionamos a diretiva
**NameVirtualHost** para dizer qual é o endereço IP do
servidor que está servindo os virtual hosts baseados em nome.  Veja o exemplo
de configuração:

<screen>
NameVirtualHost 200.200.200.10:80

&lt;VirtualHost _default_:80 200.200.200.10:80&gt;
 ServerName www.site.com.br
 ServerAdmin admin@site.com.br
 DocumentRoot /var/www
 TransferLog /var/log/apache/access.log
 ErrorLog /var/log/apache/error.log
&lt;/VirtualHost&gt;

&lt;VirtualHost 200.200.200.10&gt;
 ServerName www.site1.com.br
 ServerAdmin admin1@site1.com.br
 DocumentRoot /var/www/www_site1_com_br
 TransferLog /var/log/apache/site1/access.log
 ErrorLog /var/log/apache/site1/error.log
&lt;/VirtualHost&gt;

&lt;VirtualHost 200.200.200.10&gt;
 ServerName www.site2.com.br
 ServerAdmin admin2@site2.com.br
 DocumentRoot /var/www/www_site2_com_br
 TransferLog /var/log/apache/site2/access.log
 ErrorLog /var/log/apache/site2/error.log
&lt;/VirtualHost&gt;


A diretiva **NameVirtualHost** diz que será usado virtual
hosts baseados em nome servidos pela máquina com IP
<literal>200.200.200.10.  Os parâmetros dentro do bloco das diretivas
&lt;VirtualHost &gt; são específicas somente no site virtual especificado, caso
contrário os valores padrões definidos no arquivo de configuração serão usados.
Caso nenhum virtual host confira com a configuração, o virtualhost
**_default_** será usado.


Digite <literal>apache -S para ver suas configurações de virtual
hosts atual.  Se sua intenção é criar um grande número de virtual hosts que
serão servidos pela mesma máquina, o uso da expansão <literal>%0 e
diretivas <literal>VirtualDocumentRoot e
<literal>VirtualScriptAlias são recomendados:

<screen>
NameVirtualHost 200.200.200.10:80

&lt;VirtualHost 200.200.200.10&gt;
 VirtualDocumentRoot /var/www/%0
 VirtualScriptAlias /var/www/%0/cgi-bin
 TransferLog log/apache/site1/access.log
 ErrorLog log/apache/site1/error.log
&lt;/VirtualHost&gt;


Agora crie os diretórios em <filename>/var/www</filename> correspondentes aos
nomes de domínios que serão servidos por sua máquina: <literal>mkdir
/var/www/www.site1.com.br, <literal>mkdir
/var/www/www.site2.com.br.  Note que sua máquina deverá estar com o
DNS configurado para responder por estes domínios .


**ATENÇÃO** É importante que os endereços
especificados nas diretivas **ServerName**
(<literal>www.site1.com.br) resolvam o endereço IP da diretiva
**VirtualHost** (<filename>200.200.200.10</filename>).  Isto
deve ser feito via DNS ou nos arquivos <filename>/etc/hosts</filename>.


**OBS1:** Utilize sempre que possível endereços
IP em configurações críticas, assim os serviços não serão tão vulneráveis a
possíveis falsificações ou erros.  Veja <xref linkend="rede-dns-a-hostconf"e
<xref linkend="fw-iptables-outras-ipspoof"/>.  Leia também a seção <xref linkend="s-apache-vhosts-dnssec"/>.


**OBS2:** Não permita que outros usuários a não
ser o root e o dono do processo <command>Apache (especificado pela
diretiva **User**) tenha acesso de gravação aos logs gerados
pelo servidor.  Pois os dados podem ser apagados ou criados links para binários
do sistema que serão destruídos quando o apache gravar dados para os logs.
Alguns binários e bibliotecas são essenciais para o funcionamento do sistema.



 s-apache-vhosts-dnssec">###Segurança no uso de IP's em Virtual Hosts

Quando você está colocando um nome na diretiva de configuração do seu virtual
hosts, está assumindo que ele resolverá o endereço IP corretamente (como
<literal>www.site1.com.br =&gt; <literal>200.200.200.10).
Se por algum motivo o servidor DNS for modificado (por outra pessoa que tem
acesso a isto), o endereço IP resolvido para o site
<literal>www.site1.com.br poderá ser modificado para
<literal>200.200.200.20, isto redirecionará as requisições para outra
máquina ao invés da máquina correta.  Este tipo de ataque é chamado "DNS
Spoofing" e o uso de endereço IP (ao invés de nomes) praticamente evita que
isto aconteça.  Esta situação pode acontecer com a diretiva abaixo:

<screen>
&lt;VirtualHost www.gms.com.br&gt;
 ServerName www.gms.com.br
 ServerAdmin gleydson@guiafoca.org
 DocumentRoot /var/www/www_gms_com_br
&lt;/VirtualHost&gt;


Outra situação, que impede o funcionamento do servidor Web, é quando o servidor
DNS está em manutenção ou por algum outro motivo não pode resolver o endereço
IP de um nome especificado (como <literal>www.site1.com.br).  O
<command>apache precisa saber qual é o seu endereço IP para ser
executado.  Veja a próxima modificação:

<screen>
&lt;VirtualHost 192.168.1.1&gt;
 ServerName www.gms.com.br
 ServerAdmin gleydson@guiafoca.org
 DocumentRoot /var/www/www_gms_com_br
&lt;/VirtualHost&gt;


Na configuração acima usamos o IP do servidor para especificar o virtual host.
O <command>apache tentará fazer o DNS reverso para determinar qual
nome é servido por aquele endereço IP (<literal>www.site1.com.br).
Se ele falhar, somente a seção &lt;VirtualHost&gt; correspondente será
desativada.  Isto já é uma melhoria sobre a primeira configuração.  O nome do
servidor na diretiva **ServerName** garante que o servidor
responda com o nome correto.


Para evitar ataques baseados em DNS siga os seguintes procedimentos de
segurança:

<orderedlist numeration="arabic">
<listitem>

Preferencialmente utilize o arquivo <filename>/etc/hosts</filename> para a
resolução de nomes em máquinas locais (principalmente quando existe somente um
administrador).  É um método que evita diversas consultas ao servidor DNS (que
pode deixar o acesso lento) e este arquivo é gerenciado pelo usuário
<literal>root, isto evita o acesso de qualquer usuário para a
falsificação de endereços.


Este arquivo também é útil caso a pesquisa DNS falhe (quando a ordem de
pesquisa for do servidor DNS para o arquivo <filename>hosts</filename> no
arquivo <filename>/etc/host.conf</filename>), pois de qualquer forma o nome
será resolvido e o servidor <command>Apache será executado.


<listitem>

Evite dar poderes a outros administradores manipularem seu próprio domínio DNS,
não há nada que possa impedi-lo de modificar o endereço "X" para ser servido
pelo IP "Y" desviando o tráfego para seu próprio servidor web.  Se isto não for
possível, siga as dicas abaixo para diminuir possíveis problemas.


<listitem>

Utilize endereços IP na diretiva &lt;VirtualHost&gt;.


<listitem>

Use endereços IP na diretiva **Listen**.


<listitem>

Use um endereço IP na diretiva **BindAddress**.


<listitem>

Sempre utilize o parâmetro **ServerName** em todas as
diretivas &lt;VirtualHost&gt;, isto evita o retorno incorreto de nomes (que
pode evitar/revelar fraudes).


<listitem>

Quando utilizar virtual hosts, crie uma diretiva &lt;VirtualHost
_default_L:*&gt; usando uma diretiva **DocumentRoot** que não
aponte para lugar algum.  Esta diretiva será acessada quando nenhuma diretiva
**VirtualHost** servir a requisição, conferindo com o
endereço/ip.


</orderedlist>




