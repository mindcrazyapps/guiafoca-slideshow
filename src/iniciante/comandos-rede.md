<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" cmdn">###Comandos de rede

Este capítulo traz alguns comandos úteis para uso em rede e ambientes
multiusuário.



 cmdn-who">###who

Mostra quem está atualmente conectado no computador.  
<!-- [ %DESCRICAOD [ --> Este comando lista os nomes de usuários que estão 
conectados em seu computador, o terminal e data da conexão. <!-- ]]> -->


<command>who [**opções**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-H, --heading
<listitem>

Mostra o cabeçalho das colunas.



<varlistentry>
<term>-b, --boot
<listitem>

Mostra o horário do último boot do sistema.



<varlistentry>
<term>-d, --dead
<listitem>

Mostra processos mortos no sistema.



<varlistentry>
<term>-i, -u, --idle
<listitem>

Mostra o tempo que o usuário está parado em Horas:Minutos.



<varlistentry>
<term>-m, i am
<listitem>

Mostra o nome do computador e usuário associado ao nome.  É equivalente a
digitar <literal>who i am ou <literal>who am i.



<varlistentry>
<term>-q, --count
<listitem>

Mostra o total de usuários conectados aos terminais.



<varlistentry>
<term>-r, --runlevel
<listitem>

Mostra o nível de execução atual do sistema e desde quando ele está ativo.



<varlistentry>
<term>-T, -w, --mesg
<listitem>

Mostra se o usuário pode receber mensagens via <command>talk
(conversação).

<itemizedlist>
<listitem>

+ O usuário recebe mensagens via talk


<listitem>

- O usuário não recebe mensagens via talk.


<listitem>

?  Não foi possível determinar o dispositivo de terminal onde o usuário está
conectado.





</variablelist>
<!-- ]]> -->



 cmdn-telnet">###telnet

Permite acesso a um computador remoto.  
<!-- [ %DESCRICAOD [ --> É mostrada uma tela de acesso
correspondente ao computador local onde deve ser feita a autenticação do
usuário para entrar no sistema.  Muito útil, mas deve ser tomado cuidados ao
disponibilizar este serviço para evitar riscos de segurança e usado o
<command>ssh sempre que possível por ser um protocolo criptografado e
com recursos avançados de segurança. <!-- ]]> -->


<command>telnet [**opções**] [**ip/dns**]
[**porta**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**ip/dns**
<listitem>

Endereço IP do computador de destino ou nome DNS.



<varlistentry>
<term>**porta**
<listitem>

Porta onde será feita a conexão.  Por padrão, a conexão é feita na porta
**23**.



<varlistentry>
<term>**opções**
<listitem>
<variablelist>
<varlistentry>
<term>-8
<listitem>

Requisita uma operação binária de 8 bits.  Isto força a operação em modo
binário para envio e recebimento.  Por padrão, <command>telnet não
usa 8 bits.



<varlistentry>
<term>-a
<listitem>

Tenta um login automático, enviando o nome do usuário lido da variável de
ambiente <filename>USER</filename>.



<varlistentry>
<term>-d
<listitem>

Ativa o modo de debug.



<varlistentry>
<term>-r
<listitem>

Ativa a emulação de rlogin.



<varlistentry>
<term>-l [usuário]
<listitem>

Faz a conexão usando [usuário] como nome de usuário.



</variablelist>


</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>telnet 192.168.1.1, <literal>telnet 192.168.1.1
23.

<!-- ]]> -->



 cmdn-finger">###finger

Mostra detalhes sobre os usuários de um sistema.  
<!-- [ %DESCRICAOD [ --> Algumas versões do <command>finger possuem 
bugs e podem significar um risco para a segurança do sistema.  É 
recomendado desativar este serviço na máquina local. <!-- ]]> -->


<command>finger [**usuário**]
[**usuário@host**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome do usuário que deseja obter detalhes do sistema.  Se não for digitado o
nome de usuário, o sistema mostra detalhes de todos os usuários conectados no
momento.



<varlistentry>
<term>**usuário@host**
<listitem>

Nome do usuário e endereço do computador que deseja obter detalhes.



<varlistentry>
<term>-l
<listitem>

Mostra os detalhes de todos os usuários conectados no momento.  Entre os
detalhes, estão incluídos o **nome do interpretador de
comandos** (shell) do usuário, **diretório home**,
**nome do usuário**, **endereço**, etc.
Estes dados são lidos de <filename>/etc/passwd</filename>.



<varlistentry>
<term>-p
<listitem>

Não exibe o conteúdo dos arquivos <filename>.plan</filename> e
<filename>.project</filename>



</variablelist>
<!-- ]]> -->

Se for usado sem parâmetros, mostra os dados de todos os usuários conectados
atualmente ao seu sistema.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>finger, <literal>finger root.

<!-- ]]> -->



 cmdn-ftp">###ftp

Permite a transferência de arquivos do computador remoto/local e vice versa.  
<!-- [ %DESCRICAOD [ --> O file transfer protocol é o sistema de transmissão de arquivos 
mais usado na Internet.  É requerida a autenticação do usuário para que seja permitida 
a conexão.  Muitos servidores ftp disponibilizam acesso anônimo aos usuários, com
acesso restrito. <!-- ]]> -->


Uma vez conectado a um servidor <command>ftp, você pode usar a
maioria dos comandos do <command>GNU/Linux para operá-lo.


<command>ftp [**ip/dns**]


Abaixo alguns dos comandos mais usados no FTP:

<variablelist>
<varlistentry>
<term>ls
<listitem>

Lista arquivos do diretório atual.



<varlistentry>
<term>cd [diretório]
<listitem>

Entra em um diretório.



<varlistentry>
<term>get [arquivo]
<listitem>

Copia um arquivo do servidor ftp para o computador local.  O arquivo é gravado,
por padrão, no diretório onde o programa ftp foi executado.



<varlistentry>
<term>hash [on/off]
<listitem>

Por padrão esta opção está desligada.  Quando ligada, faz com que o caracter
"#" seja impresso na tela indicando o progresso do download.



<varlistentry>
<term>mget [arquivos]
<listitem>

Semelhante ao get, mas pode copiar diversos arquivos e permite o uso de
coringas.



<varlistentry>
<term>send [arquivo]
<listitem>

Envia um arquivo para o diretório atual do servidor FTP (você precisa de uma
conta com acesso a gravação para fazer isto).



<varlistentry>
<term>prompt [on/off]
<listitem>

Ativa ou desativa a pergunta para a cópia de arquivo.  Se estiver como
<literal>off assume sim para qualquer pergunta.



</variablelist>
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>ftp ftp.debian.org.

<!-- ]]> -->



 cmdn-whoami">###whoami

Mostra o nome que usou para se conectar ao sistema.  É útil quando você usa
várias contas e não sabe com qual nome entrou no sistema :-)


<literal>whoami




 cmdn-dnsdomainname">###dnsdomainname

Mostra o nome do domínio de seu sistema.




 cmdn-hostname">###hostname

Mostra ou muda o nome de seu computador na rede.




 cmdn-talk">###talk

Inicia conversa com outro usuário de sistema em uma rede local ou Internet.
<!-- [ %DESCRICAOD [ --> Talk é um programa de conversação em tempo real, caracter por
caracter. <!-- ]]> -->


<command>talk [**usuário**]
[**tty**]


ou


<command>talk [**usuário@host**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome de login do usuário que deseja iniciar a conversação.  Este nome pode ser
obtido com o comando <command>who (veja <xref linkend="cmdn-who"/>).



<varlistentry>
<term>**tty**
<listitem>

O nome de terminal onde o usuário está conectado, para iniciar uma conexão
local.



<varlistentry>
<term>**usuário@host**
<listitem>

Se o usuário que deseja conversar estiver conectado em um computador remoto,
você deve usar o nome do usuário@hosname do computador.



</variablelist>
<!-- ]]> -->

Após o <command>talk ser iniciado, ele verificará se o usuário pode
receber mensagens, em caso positivo, ele enviará uma mensagem ao usuário
dizendo como responder ao seu pedido de conversa.  Veja <xref linkend="cmdn-who"/>.


Para poder fazer a rolagem para cima e para baixo no <command>talk,
pressione <literal>CTRL+P(Previous - Tela anterior) e
<literal>CTRL+N (Next - Próxima tela).  

<!-- [ %INTER-AVANC [ --> Você deve ter o daemon do
<command>talk instalado (<literal>talkd) para receber
requisições de conversa. <!-- ]]> -->


Você deve autorizar o recebimento de talks de outros usuários para que eles
possam se comunicar com você. 
<!-- [ %INIC-INTER [ --> Para detalhes veja o comando <xref linkend="cmdv-mesg"/>. <!-- ]]> -->




 userlevel='inter' cmdn-ping">###ping

Verifica se um computador está disponível na rede.  
<!-- [ %DESCRICAOD [ --> Este comando é muito
utilizado por alguns programas de conexão e administradores para verificar se
uma determinada máquina está conectada na rede e também para verificar o tempo
de resposta de cada máquina da rede.  O <command>ping envia pacotes
ICMS ECHO_REQUEST para um computador, este quando recebe o pacote envia uma
resposta ao endereço de origem avisando que está disponível na rede. <!-- ]]> -->


<command>ping [**opções**] [**IP/DNS**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**IP/dns**
<listitem>

Endereço IP ou nome DNS do endereço.



<varlistentry>
<term>**opções**
<term>-c [num]
<listitem>

Envia **num** pacotes ao computador de destino.



<varlistentry>
<term>-f
<listitem>

**Flood ping**.  Envia novos pacotes antes de receber a
resposta do pacote anterior.  Para cada requisição enviada, um "."  é mostrado
na tela e para cada resposta recebida, um backspace é mostrado.  Somente o
usuário root pode utilizar esta opção e pode te auxiliar muito na detecção de
erros de transmissão de pacotes em interfaces das máquinas em sua rede.



<varlistentry>
<term>-i [seg]
<listitem>

Aguarda [seg] segundos antes de enviar cada pacote.



<varlistentry>
<term>-q
<listitem>

Não mostra as requisições enquanto são enviadas, somente mostra as linhas de
sumário no inicio e término do programa.



<varlistentry>
<term>-s [tamanho]
<listitem>

Especifica o tamanho do pacote que será enviado.



<varlistentry>
<term>-v, --verbose
<listitem>

Saída detalhada, tanto os pacotes enviados como recebidos são listados.



</variablelist>
<!-- ]]> -->

Exemplo: <literal>ping 192.168.1.1, <literal>ping
www.debian.org.




 userlevel='inter' cmdn-rlogin">###rlogin

Executa um login em uma máquina local ou remota.


<command>rlogin [**opções**]
[**IP/DNS**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**IP/DNS**
<listitem>

Endereço IP ou DNS do computador que será acessado.



<varlistentry>
<term>opções
<term>-l [nome]
<listitem>

Entra com o user id [nome] no sistema.



</variablelist>
<!-- ]]> -->

<command>rlogin é usado para executar comandos interativamente no
computador de destino (como se você estivesse sentado diante dele, muito
semelhante ao telnet).  Para executar comandos não interativamente veja <xref linkend="cmdn-rsh"/>.




 userlevel='inter' cmdn-rsh">###rsh

Executa um comando em um computador local ou remoto.


<command>rsh [**opções**] [**IP/DNS**]
[**comando**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**IP/DNS**
<listitem>

Endereço IP ou nome DNS do computador.



<varlistentry>
<term>**comando**
<listitem>

Comando que será executado no computador local/remoto.



<varlistentry>
<term>**opções**
<term>-l [nome]
<listitem>

Entra no sistema usando o login [nome].



</variablelist>
<!-- ]]> -->

<command>rsh é usado somente para executar comandos.  Para usar um
shell interativo veja <xref linkend="cmdn-telnet"e <xref linkend="cmdn-rlogin"/>.




 userlevel='inter' cmdn-w">###w

Mostra quem está conectado no sistema e o que cada um está fazendo.


<command>w [**opções**][**usuário**]

<!-- [ %OPCOES [ -->

onde:

<variablelist>
<varlistentry>
<term>**usuário**
<listitem>

Nome do usuário que deseja ver os detalhes.  Se o usuário não for digitado, o
comando <command>w mostra detalhes de todos os usuários conectados no
sistema.



<varlistentry>
<term>**opções**
<term>-h
<listitem>

Não mostra o cabeçalho



<varlistentry>
<term>-u
<listitem>

Ignora os nomes de usuários enquanto verifica os processo atuais e tempos de
CPU.



<varlistentry>
<term>-f
<listitem>

Mostra ou oculta o campo **FROM** na listagem.



</variablelist>
<!-- ]]> -->



 userlevel='inter' cmdn-traceroute">###traceroute

Mostra o caminho percorrido por um pacote para chegar ao seu destino.  
<!-- [ %DESCRICAOD [ --> Este comando mostra na tela o caminho percorrido entre 
os Gateways da rede e o tempo gasto de retransmissão.  Este comando é útil 
para encontrar computadores defeituosos na rede caso o pacote não esteja chegando 
ao seu destino. <!-- ]]> -->


<command>traceroute [**opções**] [**host/IP de
destino**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**host/IP destino**
<listitem>

É o endereço para onde o pacote será enviado (por exemplo, www.debian.org).
Caso o tamanho do pacote não seja especificado, é enviado um pacote de 38
bytes.



<varlistentry>
<term>**opções**
<term>-l
<listitem>

Mostra o tempo de vida do pacote (ttl)



<varlistentry>
<term>-m [num]
<listitem>

Ajusta a quantidade máximas de ttl dos pacotes.  O padrão é 30.



<varlistentry>
<term>-n
<listitem>

Mostra os endereços numericamente ao invés de usar resolução DNS.



<varlistentry>
<term>-p [porta]
<listitem>

Ajusta a porta que será usada para o teste.  A porta padrão é 33434.



<varlistentry>
<term>-r
<listitem>

Pula as tabelas de roteamento e envia o pacote diretamente ao computador
conectado a rede.



<varlistentry>
<term>-s [end]
<listitem>

Usa o endereço IP/DNS [end] como endereço de origem para computadores com
múltiplos endereços IPs ou nomes.



<varlistentry>
<term>-v
<listitem>

Mostra mais detalhes sobre o resultado do <command>traceroute.



<varlistentry>
<term>-w [num]
<listitem>

Configura o tempo máximo que aguardará por uma resposta.  O padrão é 3
segundos.



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplos: <literal>traceroute www.debian.org, <literal>traceroute
www.guiafoca.org.

<!-- ]]> -->



 userlevel='inter' cmdn-netstat">###netstat

Mostra conexões de rede, tabela de roteamento, estatísticas de interfaces,
conexões masquerade, e mensagens.


<command>netstat [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-i [interface]
<listitem>

Mostra estatísticas da interface [interface].



<varlistentry>
<term>-M, --masquerade
<listitem>

Se especificado, também lista conexões masquerade.



<varlistentry>
<term>-n, --numeric
<listitem>

Usa endereços numéricos ao invés de tentar resolver nomes de hosts, usuários e
portas.



<varlistentry>
<term>-c, --continuous
<listitem>

Mostra a listagem a cada segundo até que a
<literal>CTRL+<literal>C seja pressionado.



<varlistentry>
<term>-l
<listitem>

Lista sockets aguardando por conexão.



<varlistentry>
<term>-t, --tcp
<listitem>

Lista conexões TCP.



<varlistentry>
<term>-u, --udp
<listitem>

Lista conexões UDP.



</variablelist>
<!-- ]]> -->

Se não for especificada nenhuma opção, os detalhes das conexões atuais serão
mostrados.

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>netstat -n, <literal>netstat -lt,
<literal>netstat -M.

<!-- ]]> -->



 userlevel='inter' cmdv-wall">###wall

Envia uma mensagem a todos os usuários do sistema.  
<!-- [ %DESCRICAOD [ --> Este comando faz a leitura de um arquivo ou entrada 
padrão e escreve o resultado em todos os terminais onde existem usuários 
conectados.  Somente o usuário root pode utilizar este comando. <!-- ]]> -->


<command>wall [**arquivo**]

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>wall /tmp/mensagem.txt, <literal>echo Teste de
mensagem enviada a todos os usuários conectados ao sistema|wall.



