<!-- Converted by db4-upgrade version 1.0 -->
chapter  userlevel='inic;inter'<!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" run">###Execução de programas

Este capítulo explica como executar programas no <command>GNU/Linux e
o uso das ferramentas de controle de execução dos programas.


 run-prgn">###Executando um comando/programa

Para executar um comando, é necessário que ele tenha permissões de execução
(veja <xref linkend="perm-tipos"e <xref linkend="comando-ls"/>) e que esteja
no caminho de procura de arquivos (veja <xref linkend="run-path"/>).


No aviso de comando **#**(root) ou
**$**(usuário), digite o nome do comando e tecle Enter.  O
programa/comando é executado e receberá um número de identificação (chamado de
PID - Process Identification), este número é útil para identificar o processo
no sistema e assim ter um controle sobre sua execução (será visto mais adiante
neste capítulo).

<para userlevel='inter'>
Todo o programa recebe uma identificação de usuário (UID) quando é executado o
que determina quais serão suas permissões de acesso durante sua execução.  O
programa normalmente usa o UID do usuário que o executou ou o usuário
configurado pelo bit de permissão de acesso SUID caso estiver definido.
Existem também programas que são executados como root e modificam sua
identificação de usuário para algum que tenha menos privilégios no sistema
(como o <command>Apache, por exemplo).  Para maiores detalhes veja
<xref linkend="perm"/>.


Todo o programa executado no <command>Linux roda sob o controle
das permissões de acesso.  Recomendo ver mais tarde o <xref linkend="perm"/>.

<!-- [ %EXEMPLO [ -->

Exemplos de comandos: <literal>ls, <literal>df,
<literal>pwd.

<!-- ]]> -->



 run-path">###path

Path é o caminho de procura dos arquivos/comandos executáveis.  O path
(caminho) é armazenado na variável de ambiente <filename>PATH</filename>.  Você
pode ver o conteúdo desta variável com o comando <literal>echo $PATH.

<!-- [ %EXEMPLO [ -->

Por exemplo, o caminho
<literal>/usr/local/bin:/usr/bin:/bin:/usr/bin/X11 significa que se
você digitar o comando <literal>ls, o interpretador de comandos
iniciará a procura do programa <command>ls no diretório
<filename>/usr/local/bin</filename>, caso não encontre o arquivo no diretório
<filename>/usr/local/bin</filename> ele inicia a procura em
<filename>/usr/bin</filename>, até que encontre o arquivo procurado.

<!-- ]]> -->

Caso o interpretador de comandos chegue até o último diretório do path e não
encontre o arquivo/comando digitado, é mostrada a seguinte mensagem:


<literal>bash: ls: command not found (comando não encontrado).


O caminho de diretórios vem configurado na instalação do Linux, mas pode ser
alterado no arquivo <filename>/etc/profile</filename>.  Caso deseje alterar o
caminho para todos os usuários, este arquivo é o melhor lugar, pois ele é lido
por todos os usuários no momento do login.


Caso um arquivo/comando não esteja localizado em nenhum dos diretórios do path,
você deve executa-lo usando um <literal>./ na frente do comando.


Se deseja alterar o <literal>path para um único usuário, modifique o
arquivo <filename>.bash_profile</filename> em seu diretório de usuário (home).

<!-- [ %OBS [ -->

**OBSERVAÇÃO:** Por motivos de segurança, não
inclua o diretório atual <command>$PWD no <literal>path.

<!-- ]]> -->

	<!-- ]]> -->

 run-tipos">###Tipos de Execução de comandos/programas

Um programa pode ser executado de duas formas:

<orderedlist numeration="arabic">
<listitem>

<literal>Primeiro Plano - Também chamado de
**foreground**.  Quando você deve esperar o término da
execução de um programa para executar um novo comando.  Somente é mostrado o
aviso de comando após o término de execução do comando/programa.


<listitem>

<literal>Segundo Plano - Também chamado de
**background**.  Quando você não precisa esperar o término da
execução de um programa para executar um novo comando.  Após iniciar um
programa em **background**, é mostrado um número PID
(identificação do Processo) e o aviso de comando é novamente mostrado,
permitindo o uso normal do sistema.


O programa executado em background continua sendo executado internamente.  Após
ser concluído, o sistema retorna uma mensagem de pronto acompanhado do número
PID do processo que terminou.


</orderedlist>

Para iniciar um programa em <literal>primeiro plano, basta digitar
seu nome normalmente.  Para iniciar um programa em <literal>segundo
plano, acrescente o caracter <literal>"&amp;" após o final do
comando.

<!-- [ %OBS [ -->

OBS: Mesmo que um usuário execute um programa em segundo plano e saia do
sistema, o programa continuará sendo executado até que seja concluído ou
finalizado pelo usuário que iniciou a execução (ou pelo usuário root).

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>find / -name boot.b &amp;


O comando será executado em segundo plano e deixará o sistema livre para outras
tarefas.  Após o comando <command>find terminar, será mostrada uma
mensagem.

<!-- ]]> -->



 run-seq">###Executando programas em seqüência

Os comandos podem ser executados em seqüência (um após o término do outro) se
os separarmos com ";".  Por exemplo: <literal>echo primeiro;echo segundo;echo
terceiro




 run-ps">###ps

Algumas vezes é útil ver quais processos estão sendo executados no computador.
O comando <command>ps faz isto, e também nos mostra qual usuário
executou o programa, hora que o processo foi iniciado, etc.


<command>ps [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>a
<listitem>

Mostra os processos criados por você e de outros usuários do sistema.



<varlistentry>
<term>x
<listitem>

Mostra processos que não são controlados pelo terminal.



<varlistentry>
<term>u
<listitem>

Mostra o nome de usuário que iniciou o processo e hora em que o processo foi
iniciado.



<varlistentry>
<term>m
<listitem>

Mostra a memória ocupada por cada processo em execução.



<varlistentry>
<term>f
<listitem>

Mostra a árvore de execução de comandos (comandos que são chamados por outros
comandos).



<varlistentry>
<term>e
<listitem>

Mostra variáveis de ambiente no momento da inicialização do processo.



<varlistentry>
<term>w
<listitem>

Mostra a continuação da linha atual na próxima linha ao invés de cortar o
restante que não couber na tela.



<!-- [ %INTERMEDIARIO [ -->
<varlistentry>
<term>--sort:**[coluna]**
<listitem>

Organiza a saída do comando <command>ps de acordo com a coluna
escolhida.  Você pode usar as colunas <literal>pid, utime, ppid, rss, size,
user, priority.


Pode ser especificada uma listagem em ordem inversa especificando
<literal>--sort:[-coluna].  Para mais detalhes e outras opções, veja
a página de manual.



<!-- ]]> -->
</variablelist>
<!-- ]]> -->

As opções acima podem ser combinadas para resultar em uma listagem mais
completa.  Você também pode usar pipes "|" para <literal>filtrar a
saída do comando <command>ps.  
<!-- [ %INIC-INTER [ --> Para detalhes, veja <xref linkend="redir-pipe"/>. <!-- ]]> -->


Ao contrário de outros comandos, o comando <command>ps não precisa do
hífen "-" para especificar os comandos.  Isto porque ele não utiliza opções
longas e não usa parâmetros.

<!-- [ %EXEMPLO [ -->

Exemplos: <literal>ps, <literal>ps ax|grep inetd,
<literal>ps auxf, <literal>ps auxw.

<!-- ]]> -->



 run-top">###top

Mostra os programas em execução ativos, parados, tempo usado na CPU, detalhes
sobre o uso da memória RAM, Swap, disponibilidade para execução de programas no
sistema, etc.

<!-- [ %DESCRICAOD [ -->

<command>top é um programa que continua em execução mostrando
continuamente os processos que estão rodando em seu computador e os recursos
utilizados por eles.  Para sair do <command>top, pressione a tecla
<literal>q. <!-- ]]> -->


<command>top [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>-d [tempo]
<listitem>

Atualiza a tela após o [tempo] (em segundos).



<varlistentry>
<term>-s
<listitem>

Diz ao <command>top para ser executado em modo seguro.



<varlistentry>
<term>-i
<listitem>

Inicia o <command>top ignorando o tempo de processos zumbis.



<varlistentry>
<term>-c
<listitem>

Mostra a linha de comando ao invés do nome do programa.



</variablelist>
<!-- ]]> -->

A ajuda sobre o <command>top pode ser obtida dentro do programa
pressionando a tecla <literal>h ou pela página de manual
(<literal>man top).


Abaixo algumas teclas úteis:

<itemizedlist>
<listitem>

<literal>espaço - Atualiza imediatamente a tela.


<listitem>

<literal>CTRL+<literal>L - Apaga e atualiza a tela.


<listitem>

<literal>h - Mostra a tela de ajuda do programa.  É mostrado todas as
teclas que podem ser usadas com o <command>top.


<listitem>

<literal>i - Ignora o tempo ocioso de processos zumbis.


<listitem>

<literal>q - Sai do programa.


<listitem>

<literal>k - Finaliza um processo - semelhante ao comando
<command>kill.  Você será perguntado pelo número de identificação do
processo (PID).  Este comando não estará disponível caso esteja usando o
<command>top com a opção <literal>-s.


<listitem>

<literal>n - Muda o número de linhas mostradas na tela.  Se 0 for
especificado, será usada toda a tela para listagem de processos.






 run-controle">###Controle de execução de processos

Abaixo algumas comandos e métodos úteis para o controle da execução de
processos no <command>Linux.



 run-break">###Interrompendo a execução de um processo

Para cancelar a execução de algum processo <literal>rodando em primeiro
plano, basta pressionar as teclas
<literal>CTRL+<literal>C.  A execução do programa será
cancelada e será mostrado o aviso de comando.  Você também pode usar o comando
<xref linkend="run-kill"para interromper um processo sendo executado.




 run-pausa">###Parando momentaneamente a execução de um processo

Para parar a execução de um processo rodando em primeiro plano, basta
pressionar as teclas <literal>CTRL+<literal>Z.  O programa
em execução será pausado e será mostrado o número de seu job e o aviso de
comando.


Para retornar a execução de um comando pausado, use <xref linkend="run-fg"ou
<xref linkend="run-bg"/>.


O programa permanece na memória no ponto de processamento em que parou quando
ele é interrompido.  Você pode usar outros comandos ou rodar outros programas
enquanto o programa atual está interrompido.




 run-ver-backgrounds">###jobs

O comando <command>jobs mostra os processos que estão parados ou
rodando em **segundo plano**.  Processos em segundo plano são
iniciados usando o símbolo <literal>"&amp;" no final da linha de comando
<!-- [ %INIC-INTER [ --> (veja <xref linkend="run-tipos"/>) <!-- ]]> --> ou através do comando <command>bg.


<literal>jobs


O número de identificação de cada processo parado ou em segundo plano (job), é
usado com os comandos <xref linkend="run-fg"e <xref linkend="run-bg"/>.  Um
processo interrompido pode ser finalizado usando-se o comando <literal>kill
%[num], onde <literal>[num] é o número do processo obtido
pelo comando <command>jobs.




 run-fg">###fg

Permite fazer um programa rodando em segundo plano ou parado, rodar em primeiro
plano.  Você deve usar o comando <command>jobs para pegar o número do
processo rodando em segundo plano ou interrompido, este número será passado ao
comando <command>fg para ativa-lo em primeiro plano.


<command>fg [**número**]


Onde **número** é o número obtido através do comando
<command>jobs.


Caso seja usado sem parâmetros, o <command>fg utilizará o último
programa interrompido (o maior número obtido com o comando
<command>jobs).

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>fg 1.

<!-- ]]> -->



 run-bg">###bg

Permite fazer um programa rodando em primeiro plano ou parado, rodar em segundo
plano.  Para fazer um programa em primeiro plano rodar em segundo, é necessário
primeiro interromper a execução do comando com <literal>CTRL+
<literal>Z, será mostrado o número da tarefa interrompida, use este
número com o comando <command>bg para iniciar a execução do comando
em segundo plano.


<command>bg [**número**]


Onde: **número** número do programa obtido com o
pressionamento das teclas <literal>CTRL+<literal>Z ou
através do comando <command>jobs.




 run-kill">###kill

Permite enviar um sinal a um comando/programa. 
<!-- [ %DESCRICAOD [ --> Caso seja usado sem parâmetros,
o <command>kill enviará um sinal de término ao processo sendo
executado. <!-- ]]> -->


<command>kill **opções**] [**sinal**]
[**número**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**número**
<listitem>

É o número de identificação do processo obtido com o comando <xref linkend="run-ps"/>.  Também pode ser o número após o sinal de
<literal>% obtido pelo comando <command>jobs para matar uma
tarefa interrompida.  Veja <xref linkend="run-ver-backgrounds"/>.



<varlistentry>
<term>**sinal**
<listitem>

Sinal que será enviado ao processo.  Se omitido usa <literal>-15 como
padrão.



<varlistentry>
<term>**opções**
<term>-9
<listitem>

Envia um sinal de destruição ao processo ou programa.  Ele é terminado
imediatamente sem chances de salvar os dados ou apagar os arquivos temporários
criados por ele.



</variablelist>
<!-- ]]> -->

Você precisa ser o dono do processo ou o usuário root para termina-lo ou
destruí-lo.  Você pode verificar se o processo foi finalizado através do
comando <command>ps.  Os tipos de sinais aceitos pelo
<command>GNU/Linux são explicados em detalhes em <xref linkend="run-sinais"/>.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>kill 500, <literal>kill -9 500,
<literal>kill %1.

<!-- ]]> -->



 run-killall">###killall

Permite finalizar processos através do nome.


<command>killall [**opções**] [**sinal**]
[**processo**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**processo**
<listitem>

Nome do processo que deseja finalizar



<varlistentry>
<term>**sinal**
<listitem>

Sinal que será enviado ao processo (pode ser obtido usando a opção
<literal>-i).



<varlistentry>
<term>**opções**
<term>-i
<listitem>

Pede confirmação sobre a finalização do processo.



<varlistentry>
<term>-l
<listitem>

Lista o nome de todos os sinais conhecidos.



<varlistentry>
<term>-q
<listitem>

Ignora a existência do processo.



<varlistentry>
<term>-v
<listitem>

Retorna se o sinal foi enviado com sucesso ao processo.



<varlistentry>
<term>-w
<listitem>

Finaliza a execução do <command>killall somente após finalizar todos
os processos.



</variablelist>
<!-- ]]> -->

Os tipos de sinais aceitos pelo <command>GNU/Linux são explicados em
detalhes na <xref linkend="run-sinais"/>.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>killall -HUP inetd

<!-- ]]> -->



 run-killall5">###killall5

Envia um sinal de finalização para todos os processos sendo executados.


<command>killall5 [**sinal**]




 run-sinais">###Sinais do Sistema

Retirado da página de manual <literal>signal.  O
<command>GNU/Linux suporta os sinais listados abaixo.  Alguns números
de sinais são dependentes de arquitetura.


Primeiro, os sinais descritos no **POSIX 1**:

<screen>
Sinal   Valor     Ação    Comentário
---------------------------------------------------------------------------
HUP        1        A      Travamento detectado no terminal de controle ou 
                           finalização do processo controlado
INT        2        A      Interrupção através do teclado
QUIT       3        C      Sair através do teclado
ILL        4        C      Instrução Ilegal
ABRT       6        C      Sinal de abortar enviado pela função abort
FPE        8        C      Exceção de ponto Flutuante
KILL       9       AEF     Sinal de destruição do processo
SEGV      11        C      Referência Inválida de memória
PIPE      13        A      Pipe Quebrado: escreveu para o pipe sem leitores
ALRM      14        A      Sinal do Temporizador da chamada do sistema alarm
TERM      15        A      Sinal de Término
USR1   30,10,16     A      Sinal definido pelo usuário 1
USR2   31,12,17     A      Sinal definido pelo usuário 2
CHLD   20,17,18     B      Processo filho parado ou terminado
CONT   19,18,25            Continuar a execução, se interrompido
STOP   17,19,23    DEF     Interromper processo
TSTP   18,20,24     D      Interromper digitação no terminal
TTIN   21,21,26     D      Entrada do terminal para o processo em segundo plano
TTOU   22,22,27     D      Saída do terminal para o processo em segundo plano


As letras da coluna <literal>Ação tem o seguinte significado:

<itemizedlist>
<listitem><literal>A - A ação padrão é terminar o processo.
<listitem><literal>B - A ação padrão é ignorar o sinal.
<listitem><literal>C - A ação padrão é terminar o processo e mostrar o core.
<listitem><literal>D - A ação padrão é parar o processo.
<listitem><literal>E - O sinal não pode ser pego.
<listitem><literal>F - O sinal não pode ser ignorado.


Sinais não descritos no **POSIX 1** mas descritos na
**SUSv2**:

<screen>
Sinal     Valor     Ação     Comentário
-------------------------------------------------------------------------
BUS      10,7,10      C      Erro no Barramento (acesso incorreto da memória)
POLL                  A      Evento executado em Pool (Sys V). Sinônimo de IO
PROF     27,27,29     A      Tempo expirado do Profiling
SYS      12,-,12      C      Argumento inválido para a rotina (SVID)
TRAP        5         C      Captura do traço/ponto de interrupção
URG      16,23,21     B      Condição Urgente no soquete (4.2 BSD)
VTALRM   26,26,28     A      Alarme virtual do relógio (4.2 BSD)
XCPU     24,24,30     C      Tempo limite da CPU excedido (4.2 BSD)
XFSZ     25,25,31     C      Limite do tamanho de arquivo excedido (4.2 BSD)


(Para os casos SIGSYS, SIGXCPU, SIGXFSZ, e em algumas arquiteturas também o
SIGGUS, a ação padrão do Linux para kernels 2.3.27 e superiores é A (terminar),
enquanto SYSv2 descreve C (terminar e mostrar dump core).) Seguem vários outros
sinais:

<screen>
Sinal     Valor     Ação     Comentário
--------------------------------------------------------------------
IOT         6         C      Traço IOT. Um sinônimo para ABRT
EMT       7,-,7
STKFLT    -,16,-      A      Falha na pilha do processador
IO       23,29,22     A      I/O agora possível (4.2 BSD)
CLD       -,-,18             Um sinônimo para CHLD
PWR      29,30,19     A      Falha de força (System V)
INFO      29,-,-             Um sinônimo para SIGPWR
LOST      -,-,-       A      Perda do bloqueio do arquivo
WINCH    28,28,20     B      Sinal de redimensionamento da Janela (4.3 BSD, Sun)
UNUSED    -,31,-      A      Sinal não usado (será SYS)


O "-" significa que o sinal não está presente.  Onde três valores são listados,
o primeiro é normalmente válido para o Alpha e Sparc, o do meio para i386,
PowerPc e sh, o último para o Mips.  O sinal 29 é SIGINFO/SIGPWR em um Alpha
mas SIGLOST em um Sparc.






 userlevel='inter' run-nohup">###nohup

Executa um comando ignorando os sinais de interrupção.  
<!-- [ %DESCRICAOD [ --> O comando poderá ser executado até mesmo em segundo plano 
caso seja feito o logout do sistema. <!-- ]]> -->


<command>nohup [**comando que será executado**]


As mensagens de saída do <command>nohup são direcionadas para o
arquivo <filename>$HOME/nohup.out</filename>.

<!-- [ %EXEMPLO [ -->

Exemplo: <literal>nohup find / -uid 0 &gt;/tmp/rootfiles.txt &amp;.

<!-- ]]> -->



 userlevel='inter' run-nice">###nice

Configura a prioridade da execução de um comando/programa.


<command>nice [**opções**] [**comando/programa**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**comando/programa**
<listitem>

Comando/programa que terá sua prioridade ajustada.



<varlistentry>
<term>**opções**
<term>-n [numero]
<listitem>

Configura a prioridade que o programa será executado.  Se um programa for
executado com maior prioridade, ele usará mais recursos do sistema para seu
processamento, caso tenha uma prioridade baixa, ele permitirá que outros
programas tenham preferência.  A prioridade de execução de um
**programa/comando** pode ser ajustada de -20 (a mais alta)
até 19 (a mais baixa).



</variablelist>
<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>nice -n -19 find / -name apropos.

<!-- ]]> -->



 userlevel='inter' run-fuser">###fuser

Permite identificar e fechar os processos que estão utilizando arquivos e
soquetes no sistema.


<command>fuser [**opções**] [**nome**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**nome**
<listitem>

Especifica um nome de processo, diretório, arquivo, etc.



<varlistentry>
<term>**opções**
<term>-k
<listitem>

Finaliza os processos acessando o arquivo especificado.  O sinal desejado deve
ser especificado com a opção <literal>-signal [num], ou o sinal -9
será enviado como padrão.  Não é possível matar o próprio processo
<command>fuser.



<varlistentry>
<term>-i
<listitem>

Pergunta antes de destruir um processo.  Será ignorada caso a opção
<literal>-k não seja especificada.



<varlistentry>
<term>-l
<listitem>

Lista todos os nomes de sinais conhecidos.



<varlistentry>
<term>-m [nome]
<listitem>

Especifica um arquivo em um sistema de arquivos montado ou dispositivo de bloco
que está montado.  Todos os processos acessando aquele sistema de arquivos
serão listados.  Diretórios são mostrados seguidos de uma <literal>/



<varlistentry>
<term>-signal [número]
<listitem>

Usa o sinal especificado ao invés de -9 (SIGKILL) quando finalizar processos.



<varlistentry>
<term>-u
<listitem>

Acrescenta o nome do dono de cada processo ao PID.



<varlistentry>
<term>-v
<listitem>

Os processos são mostrados em um estilo idêntico ao <command>ps.



</variablelist>
<!-- ]]> -->



 userlevel='inter' run-tload">###tload

Representa de forma gráfica a carga do sistema.


<command>tload [**opções**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**opções**
<term>-s [número]
<listitem>

Mostra uma escala vertical com espaçamento especificado por [número].  É
recomendável o uso de números entre 1 e 10 para melhor visualização da escala.



<varlistentry>
<term>-d [número]
<listitem>

Especifica o intervalo entre atualizações, em segundos.



</variablelist>
<!-- ]]> -->



 userlevel='inter' run-vmstat">###vmstat

Mostra estatísticas sobre o uso da memória virtual do sistema.


<command>vmstat [**intervalo**] [**contagem**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**intervalo**
<listitem>

Número especificado em segundos entre atualizações.



<varlistentry>
<term>**contagem**
<listitem>

Número de vezes que será mostrado.



</variablelist>
<!-- ]]> -->

Se não for especificado nenhum parâmetro, o <command>vmstat mostra o
status da memória virtual e volta imediatamente para a linha de comando.  A
descrição dos campos do <command>vmstat são as seguintes:

<variablelist>
<varlistentry>
<term>**Processos**
<term>r
<listitem>

Número de processos aguardando execução.



<varlistentry>
<term>b
<listitem>

Número de processos em espera não interrompíveis.



<varlistentry>
<term>w
<listitem>

Número de processos extraídos do arquivo de troca ou caso contrário em
execução.



<varlistentry>
<term/>
<term>**Memória**
<term>swpd
<listitem>

A quantidade de memória virtual usada em Kb.



<varlistentry>
<term>free
<listitem>

Quantidade de memória livre em Kb.



<varlistentry>
<term>buff
<listitem>

Quantidade de memória usada como buffer em Kb.



<varlistentry>
<term/>
<term>**Memória Virtual**
<term>si
<listitem>

Quantidade de memória gravada para o disco Kb/s.



<varlistentry>
<term>so
<listitem>

Quantidade de memória retirada do disco em Kb/s.



<varlistentry>
<term/>
<term>**Entrada/Saída**
<term>bi
<listitem>

Blocos enviados para um dispositivo de bloco (medido em blocos por segundo).



<varlistentry>
<term>bo
<listitem>

Blocos recebidos de um dispositivo de bloco (em blocos por segundo).



<varlistentry>
<term/>
<term>**Sistema**
<term>in
<listitem>

Número de interrupções por segundo, incluindo o clock.



<varlistentry>
<term>cs
<listitem>

Número de mudanças de contexto por segundo.



<varlistentry>
<term/>
<term>**Porcentagem do total de tempo da CPU**
<term>us
<listitem>

Tempo do usuário



<varlistentry>
<term>sy
<listitem>

Tempo do sistema



<varlistentry>
<term>id
<listitem>

Tempo ocioso



</variablelist>



 userlevel='inter' run-pidof">###pidof

Retorna o PID do processo especificado


<command>pidof [**opções**] [**nome**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**nome**
<listitem>

Nome do processo que seja obter o número PID



<varlistentry>
<term>**opções**
<term>-s
<listitem>

Retorna somente o primeiro PID encontrado.



<varlistentry>
<term>-x
<listitem>

Retorna o PID do do shell que está executando o script



<varlistentry>
<term>-o [PID]
<listitem>

Ignora o processo com aquele PID.  O PID especial %PPID pode ser usado para
nomear o processo pai do programa <command>pidof, em outras palavras



</variablelist>
<!-- ]]> -->
<!-- [ %OBS [ -->

OBS: O programa <command>pidof é um link simbólico ao programa
<command>killall5.  Cuidado ao executar o <command>killall5
as funções e opções são completamente diferentes dependendo da forma como é
chamado na linha de comando!  (veja <xref linkend="run-killall5"para
detalhes.)

<!-- ]]> -->
<!-- [ %EXEMPLO [ -->

Exemplo: <literal>pidof -s init

<!-- ]]> -->



 userlevel='inter' run-pstree">###pstree

Mostra a estrutura de processos em execução no sistema em forma de árvore.


<command>pstree [**opções**] [**pid**]

<!-- [ %OPCOES [ -->

Onde:

<variablelist>
<varlistentry>
<term>**pid**
<listitem>

Número do processo que terá sua árvore listada.  Se omitido, lista todos os
processos.



<varlistentry>
<term>**opções**
<term>-a
<listitem>

Mostra opções passadas na linha de comando.



<varlistentry>
<term>-c
<listitem>

Mostra toda a estrutura (inclusive sub-processos do processo pai).



<varlistentry>
<term>-G
<listitem>

Usa caracteres gráficos no desenho da árvore de processos.



<varlistentry>
<term>-h
<listitem>

Destaca o processo atual e seus antecessores.



<varlistentry>
<term>-H [pid]
<listitem>

Destaca o processo especificado.



<varlistentry>
<term>-l
<listitem>

Não faz quebra de linha



<varlistentry>
<term>-n
<listitem>

Classifica pelo número PID ao invés do nome.



<varlistentry>
<term>-p
<listitem>

Mostra o número PID entre parênteses após o nome do processo.



<varlistentry>
<term>-u
<listitem>

Mostra também o dono do processo.



<varlistentry>
<term>-U
<listitem>

Usa o conjunto de caracteres Unicode para o desenho da árvore.



</variablelist>
<!-- ]]> -->


 run-fechando">###Fechando um programa quando não se sabe como sair

Muitas vezes quando se esta iniciando no <command>GNU/Linux você pode
executar um programa e talvez não saiba como fecha-lo.  Este capítulo do guia
pretende ajuda-lo a resolver este tipo de problema.


Isto pode também ocorrer com programadores que estão construindo seus programas
e por algum motivo não implementam uma opção de saída, ou ela não funciona!


Em nosso exemplo vou supor que executamos um programa em desenvolvimento com o
nome <command>contagem que conta o tempo em segundos a partir do
momento que é executado, mas que o programador esqueceu de colocar uma opção de
saída.  Siga estas dicas para finaliza-lo:

<orderedlist numeration="arabic">
<listitem>

Normalmente todos os programas <command>UNIX (o
<command>GNU/Linux também é um Sistema Operacional baseado no
<command>UNIX) podem ser interrompidos com o pressionamento das
teclas <literal>&lt;CTRL&gt; e <literal>&lt;C&gt;.  Tente
isto primeiro para finalizar um programa.  Isto provavelmente não vai funcionar
se estiver usando um Editor de Texto (ele vai entender como um comando de
menu).  Isto normalmente funciona para comandos que são executados e terminados
sem a intervenção do usuário.


Caso isto não der certo, vamos partir para a força!  ;-)


<listitem>

Mude para um novo console (pressionando <literal>&lt;ALT&gt; e
<literal>&lt;F2&gt;), e faça o **login** como
usuário **root**.


<listitem>

Localize o PID (número de identificação do processo) usando o comando:
<literal>ps ax, aparecerão várias linhas cada uma com o número do
processo na primeira coluna, e a linha de comando do programa na última coluna.
Caso aparecerem vários processos você pode usar <literal>ps ax|grep
contagem, neste caso o <command>grep fará uma filtragem da
saída do comando <literal>ps ax mostrando somente as linhas que tem a
palavra "contagem".  Para maiores detalhes, veja o comando <xref linkend="cmdv-grep"/>.


<listitem>

Feche o processo usando o comando <command>kill
**PID**, lembre-se de substituir PID pelo número
encontrado pelo comando <command>ps ax acima.


O comando acima envia um sinal de término de execução para o processo (neste
caso o programa <command>contagem).  O sinal de término mantém a
chance do programa salvar seus dados ou apagar os arquivos temporários que
criou e então ser finalizado, isto depende do programa.


<listitem>

Alterne para o console onde estava executando o programa
<command>contagem e verifique se ele ainda está em execução.  Se ele
estiver parado mas o aviso de comando não está disponível, pressione a tecla
&lt;ENTER&gt;.  Freqüentemente acontece isto com o comando
<command>kill, você finaliza um programa mas o aviso de comando não é
mostrado até que se pressione &lt;ENTER&gt;.


<listitem>

Caso o programa ainda não foi finalizado, repita o comando
<command>kill usando a opção -9: <literal>kill -9 PID.
Este comando envia um sinal de DESTRUIÇÃO do processo, fazendo ele terminar "na
marra"!


</orderedlist>

Uma última dica: todos os programas estáveis (todos que acompanham as boas
distribuições <command>GNU/Linux) tem sua opção de saída.  Lembre-se
que quando finaliza um processo todos os dados do programa em execução podem
ser perdidos (principalmente se estiver em um editor de textos), mesmo usando o
<command>kill sem o parâmetro <literal>-9.


Procure a opção de saída de um programa consultando o help on line, as páginas
de manual, a documentação que acompanha o programa, info pages.  Para detalhes
de como encontrar a ajuda dos programas, veja o <xref linkend="ajuda"/>




 run-reset">###Eliminando caracteres estranhos

As vezes quando um programa <literal>mal comportado é finalizado ou
quando você visualiza um arquivo binário através do comando
<literal>cat, é possível que o aviso de comando (prompt) volte com
caracteres estranhos.


Para fazer tudo voltar ao normal, basta digitar <literal>reset e
teclar <literal>ENTER.  Não se preocupe, o comando
<literal>reset não reiniciará seu computador (como o botão reset do
seu computador faz), ele apenas fará tudo voltar ao normal.

<!-- [ %OBS [ -->

Note que enquanto você digitar <literal>reset aparecerão caracteres
estranhos ao invés das letras.  Não se preocupe!  Basta digitar corretamente e
bater <literal>ENTER e o aviso de comando voltará ao normal.

<!-- ]]> -->


