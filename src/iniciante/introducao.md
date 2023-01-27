chapter <!---  [docbook](http://docbook.org/ns/docbook)" ---> version="5.0" intro">###Introdução

Bem vindo ao Guia **Foca Linux**.  O nome
**FOCA** significa **FO**nte de
**C**onsulta e **A**prendizado.  Este guia
está dividido em 3 níveis de aprendizado e versão que está lendo agora contém
os níveis:

<itemizedlist>
<listitem userlevel='inic' >Iniciante
<listitem userlevel='inter' >Intermediário
<listitem userlevel='avanc' >Avançado


<!-- [ %CAPJUNTOS [ -->

Entre o conteúdo do guia, você encontrará:

<itemizedlist>

<listitem userlevel='inic' >

Textos explicativos falando sobre o sistema <command>Linux, seus
comandos, como manusear arquivos, diretórios, etc.


<listitem userlevel='inic' >

Explicações iniciais sobre as partes básicas do computador e periféricos


<listitem userlevel='inic' >

Comandos e Programas equivalentes entre o
<command>DOS/<command>Windows e o
<command>GNU/Linux


<listitem userlevel='inic' >

Todos os materiais contidos na versão iniciante são ideais para quem está tendo
o primeiro contato com computadores e/ou com o <command>Linux.  A
linguagem usada é simples com o objetivo de explicar claramente o funcionamento
de cada comando e evitando, sempre que possível, termos técnicos




<listitem userlevel='inter' >

Explicações necessárias para conhecer, operar, configurar, desenvolver,
personalizar seu sistema Linux.


<listitem userlevel='inter'>

Uma lista de aplicativos para serem usados em seu sistema
<command>GNU/Linux, com suas características, equipamento mínimo
requerido e espaço em disco recomendado para instalação.


<listitem userlevel='inter'>

Aprender como particionar discos


<listitem userlevel='inter'>

Criação de partições e arquivos contendo o sistema de arquivos
**ext2**, **ext3**,
**reiserfs** ou **xfs** (para gravação de
arquivos e diretórios) e swap (memória virtual) e as vantagens/desvantagens de
se utilizar um arquivo ou partição para armazenamento de dados.


<listitem userlevel='inter'>

Compilação de programas/kernel, com explicações sobre cada uma das opções
ajudando-o a decidir sobre a inclusão ou não.


<listitem userlevel='inter'>

Manipulação de módulos do kernel


<listitem userlevel='inter'>

Explicações sobre hardwares (dispositivo, Interrupções, DMA) e como configura-los no Linux, 
valores padrões e resolução de conflitos entre hardwares.


<listitem userlevel='inter'>

Dicas de como avaliar e comprar bons hardwares para que seu computador tenha o
melhor desempenho (também válido para outras plataformas como <command>Windows 
e <command>MacOS).  Você também entenderá
porque alguns dispositivos de boa qualidade, como placas de rede, custam até 3
vezes mais caro que outras e o que a placa traz de especial para ter este
diferencial.


<listitem userlevel='inter'>

Como modificar facilmente o idioma usado em seu sistema (localização) para o
modo texto e modo gráfico.


<listitem userlevel='inter'>

Utilização de compactadores de arquivos


<listitem userlevel='inter'>

Mais opções para os comandos existentes na versão
**Iniciante** do guia e novos comandos.


<listitem userlevel='inter'>

Conhecer os arquivos de configuração e arquivos básicos de segurança,
entendendo para que eles servem e como usa-los.


<listitem userlevel='inter'>

Dicas de como saber escolher bons periféricos para uso no
<command>GNU/Linux e outros sistemas operacionais


<listitem userlevel='inter'>

Manutenção básica do computador (verificação do disco, desfragmentação) e
manutenção automática feita através dos programas de e scripts configurados.


<listitem userlevel='inter'>

Introdução a rede no Linux (com a configuração de dispositivos de rede, etc.).


<listitem userlevel='inter'>

Configurações básicas de segurança de Rede


<listitem userlevel='inter'>

Gerenciadores de inicialização (boot), o que são e como funcionam e como criar
um arquivo de inicialização para inicializar o <command>GNU/Linux
pelo disco rígido ou mais de um Sistema Operacional.


<listitem userlevel='inter'>

Criação de Memória virtual no disco rígido e em arquivo.


<listitem userlevel='inter'>

Os materiais contidos na versão intermediário são ideais para quem já tem um
conhecimento básico do sistema <command>GNU/Linux mas que deseja se
aprofundar neste sistema conhecendo os arquivos necessários para o
funcionamento do <command>GNU/Linux, como modifica-los e como estas
modificações afetam o funcionamento do sistema.



<listitem userlevel='avanc'>

Análise de logs do sistema GNU/Linux e aplicação para a solução de problemas
(<xref linkend="log"/>).


<listitem userlevel='avanc'>

Gerenciamento de contas de usuários, definição de período automático para troca
de senha periódica, políticas de segurança, etc (<xref linkend="d-contas"/>).


<listitem userlevel='avanc'>

Principais tipos de ataques para descoberta de senhas e alguns métodos de como
evita-las (<xref linkend="d-contas-cms-senhas"/>).


<listitem userlevel='avanc'>

Integrar máquinas <command>Windows e <command>Linux em uma
mesma rede compartilhando dados entre si e impressão (<xref linkend="samba"/>).


<listitem userlevel='avanc'>

Sistemas de proteção de senhas do sistema (<xref linkend="d-contas-segsenhas"/>).


<listitem userlevel='avanc'>

Criptografia e segurança na transmissão de dados, usando exemplos práticos do
uso de sniffers para entender o porque da uso de criptografia para transmissão
segura de dados (<xref linkend="d-cripto"/>).


<listitem userlevel='avanc'>

Uso de serviços alternativos criptográficos (<xref linkend="d-cripto-alt"/>).


<listitem userlevel='avanc'>

Criptografia usando <command>gnupgp (<xref linkend="d-cripto-gpg"/>).


<listitem userlevel='avanc'>

Uso de sistema de arquivos criptográficos para armazenamento de dados (<xref linkend="d-cripto-criptofs"/>).


<listitem userlevel='avanc'>

Otimização de performance na transferência de dados do disco rígido através de
particionamento e <command>hdparm, uso de spindles para criação de
swap (<xref linkend="hard-perf"/>).


<listitem userlevel='avanc'>

O que são descargas estáticas e a importância do aterramento da instalação
elétrica do computador (dirigido a usuários domésticos e de pequenas
instalações) (<xref linkend="hard-descestat"/>).


<listitem userlevel='avanc'>

Maiores considerações a segurança de sistema e a problemas de segurança
relativos a falhas de configuração (distribuída entre os capítulos de daemons e
servidores).


<listitem userlevel='avanc'>

Montagem de um servidor de publicação Web usando o <command>Apache
(<xref linkend="apache"/>).


<listitem userlevel='avanc'>

Montagem de um firewall avançado para proteção do sistema (filtragem de
pacotes) usando o <command>iptables, redirecionamento de pacotes,
nat, bloqueio de tráfego P2P, masquerading, balanceamento de carga, marcação de
pacotes, log, proteção contra port scans (<xref linkend="fw-iptables"/>).


<listitem userlevel='avanc'>

Servidor de acesso para permitir o acesso a distância ao seu computador usando
o <command>telnetd (<xref linkend="telnet"/>).


<listitem userlevel='avanc'>

Servidor de acesso para permitir o acesso a distância a seu computador com
criptografia usando o <command>ssh (<xref linkend="ssh"/>).


<listitem userlevel='avanc'>

Servidor de identificação usando o <command>oidentd (<xref linkend="ident"/>).


<listitem userlevel='avanc'>

Montagem de um servidor pop3 para que suas estações de rede possam acessar o
email na máquina servidor <command>Linux usando programas como
<command>Outlook, <command>Communicator,
<command>Mutt, <command>sylpheed e outros que utilizem o
protocolo <command>pop3 (<xref linkend="pop3"/>).


<listitem userlevel='avanc'>

Restrições de acesso a instalação do computador, acesso a grupos do sistema,
restrições de login usando **PAM** (<xref linkend="d-restr"/>).


<listitem userlevel='avanc'>

Restrições de espaço usado em disco por usuários/grupos usando o sistema de
quotas (<xref linkend="d-restr-quotas"/>).


<listitem userlevel='avanc'>

Uso de grupos dos sistema para restrições de acesso (<xref linkend="d-restr-grupos"/>).


<listitem userlevel='avanc'>

Restrições de acesso via hardware: BIOS, disquete, placa com boot via rede,
LILO, disco rígido (<xref linkend="d-restr-hardware"/>).


<listitem userlevel='avanc'>

Manipulações de variáveis no bash (<replaceable>TMOUT</replaceable>,
<replaceable>PS1</replaceable>, <replaceable>PS2</replaceable>,
<replaceable>PS3</replaceable>, <replaceable>PS4</replaceable>,
<replaceable>HISTORY</replaceable>, etc).


<listitem userlevel='avanc'>

Montagem de shell básico restrito (<xref linkend="d-restr-bash-restricted"/>).


<listitem userlevel='avanc'>

Uso do <command>sudo para dar privilégio de execução de programas
como root a determinados usuários (<xref linkend="d-restr-sudo"/>).



<!-- ]]> -->

Para melhor organização, dividi o guia em 3 versões:
**Iniciante**, **Intermediário** e
**Avançado**.  Sendo que a versão
**Iniciante** é voltada para o usuário que não tem
<literal>nenhuma experiência no <command>GNU/Linux.  A
última versão deste guia pode ser encontrada em: ("http://www.w3.org/1999/xlink) []( [guiafoca](http://www.guiafoca.org)  Página Oficial do guia Foca GNU/Linux.


Caso tiver alguma sugestão, correção, crítica para a melhoria deste guia,
preencha o formuário de sugestões disponíveis na página oficial do guia ou
envie um e-mail para <email>gleydson@guiafoca.org.


O **Foca GNU/Linux** é atualizado freqüentemente, por este
motivo recomendo que preencha a ficha do aviso de atualizações na página web em
("http://www.w3.org/1999/xlink) []( [guiafoca](http://www.guiafoca.org)  Página Oficial do guia Foca
GNU/Linux no fim da página principal.  Após preencher a ficha do aviso
de atualizações, você receberá um e-mail sobre o lançamento de novas versões do
guia e o que foi modificado, desta forma você poderá decidir em copia-la caso a
nova versão contenha modificações que considera importantes.


Tenho recebido elegios de pessoas do Brasil (e também de outros países)
elogiando o trabalho e a qualidade da documentação.  Agradeço a todos pelo
apoio, tenham certeza que este trabalho é desenvolvido pensando em repassar um
pouco do conhecimento que adquiri ao começar o uso do Linux.


Também recebo e-mails de pessoas comemorando a aprovação na prova LPI
nível 1, 2 e 3 após estudar usando o guia Foca GNU/Linux.  Fico bastante feliz por
saber disso, pois nunca tive a intenção de tornar o guia uma referência livre
para estudo da LPI e hoje é usado para estudo desta difícil certificação que
aborda comandos, serviços, configurações, segurança, empacotamento,
criptografia, etc.



	
  userlevel='avanc' introducao-avisoADV">###Considerações sobre o nível Avançado

Este guia foi compilado incluindo o nível **Avançado** do guia
FOCA GNU/Linux, ele não tem a intenção de ser a única referencia na
configuração de serviços, servidores, aplicativos, nem garantia que ele
atenderá a determinada finalidade específica do usuário (principalmente de uma
rede, que depende de uma perfeita compreensão para adaptação de acordo com os
requisitos de uma instalação local).  Seu foco principal é a instalação do
serviço, abordando considerações voltadas a segurança, e exemplos de
configuração e seu funcionamento.


Com relação a capítulos sobre servidores, é importante observar qual versão é
documentada no guia e se confere com a instalada em seu sistema, a fim de que
tudo funcione corretamente.  Entretanto, na maioria dos casos, as explicações
relacionadas a uma versão de um programa são válidas em uma nova versão.



  userlevel='inic;inter' introducao-palavras">###Antes de começar

Os capítulos **Introdução** e **básico**
contém explicações teóricas sobre o computador, <command>GNU/Linux,
etc., você pode pular este capítulos caso já conheça estas explicações ou se
desejar partir para a prática e quiser vê-los mais tarde, se lhe interessar.


Se você já é um usuário do <command>DOS e <command>Windows,
recomendo ler <xref linkend="d-l"/>.  Lá você vai encontrar comparações de
comandos e programas <command>DOS/Windows e
<command>GNU/Linux.


Para quem está começando, muita teoria pode atrapalhar o aprendizado, é mais
produtivo ver na prática o que o computador faz e depois porque ele faz isto.
Mesmo assim, recomendo ler estes capítulos pois seu conteúdo pode ser útil.


Coloquei abaixo algumas dicas para um bom começo:

<itemizedlist>
<listitem>

Recomendo que faça a leitura deste guia e pratique imediatamente o que
aprendeu.  Isto facilita o entendimento do programa/comando/configuração.


<listitem>

É preciso ter interesse em aprender, se você tiver vontade em aprender algo,
você terá menos dificuldade do que em algo que não gosta e está se obrigando a
aprender.


<listitem>

Decorar não adianta, pelo contrário, só atrapalha no aprendizado.  Você precisa
entender o que o comando faz, deste modo você estará estimulando e
desenvolvendo sua interpretação, e entenderá melhor o assunto (talvez até me de
uma força para melhorar o guia ;-)


<listitem>

Curiosidade também é importante.  Você talvez possa estar procurando um comando
que mostre os arquivos que contém um certo texto, e isto fará você chegar até o
comando <command>grep, depois você conhecerá suas opções, etc.


<listitem>

Não desanime vendo outras pessoas que sabem mais que você, lembre-se que
ninguém nasce sabendo :-).  Uma pessoa pode ter mais experiência em um assunto
no sistema como compilação de programas, configuração, etc., e você pode ter
mais interesse em redes.


<listitem>

Ninguém pode saber tudo da noite para o dia, não procure saber TUDO sobre o
sistema de uma só vez, senão não entenderá NADA.  Caso tenha dúvidas sobre o
sistema, procure ler novamente a seção do guia, e caso ainda não tenha
entendido procure ajuda nas página de manual (veja <xref linkend="ajuda-man"/>), ou nas listas de discussão (veja <xref linkend="ajuda-listas"/>) ou me envie uma mensagem
<email>gleydson@guiafoca.org.


<listitem>

Certamente você buscará documentos na Internet que falem sobre algum assunto
que este guia ainda não explica.  Muito cuidado!  O
<command>GNU/Linux é um sistema que cresce muito rapidamente, a cada
semana uma nova versão é lançada, novos recursos são adicionados, seria
maravilhoso se a documentação fosse atualizada com a mesma freqüência.


Infelizmente a atualização da documentação não segue o mesmo ritmo
(principalmente aqui no Brasil).  É comum você encontrar na Internet documentos
da época quando o kernel estava na versão 2.2.30, 2.4.8, 2.6.28, etc.  Estes
documentos são úteis para pessoas que por algum motivo necessitam operar com
versões antigas do Kernel Linux, mas pode trazer problemas ou causar má
impressão do <command>GNU/Linux em outras pessoas.


Por exemplo, você pode esbarrar pela Internet com um documento que diz que o
Kernel não tem suporte aos "nomes extensos" da VFAT (Windows 95), isto é
verdade para kernels anteriores ao 2.0.31, mas as versões mais novas que a
2.0.31 reconhecem sem problemas os nomes extensos da partição Windows VFAT.


Uma pessoa desavisada pode ter receio de instalar o
<command>GNU/Linux em uma mesma máquina com Windows por causa de um
documento como este.  Para evitar problemas deste tipo, verifique a data de
atualização do documento, se verificar que o documento está obsoleto, contacte
o autor original e peça para que ele retire aquela seção na próxima versão que
será lançada.


<listitem>

O <command>GNU/Linux é considerado um sistema mais difícil do que os
outros, mas isto é porque ele requer que a pessoa realmente aprenda e conheça
computadores e seus periféricos antes de fazer qualquer coisa (principalmente
se você é um técnico em manutenção, redes, instalações, etc., e deseja oferecer
suporte profissional a este sistema).


Você conhecerá mais sobre computadores, redes, hardware, software, discos,
saberá avaliar os problemas e a buscar a melhor solução, enfim as
possibilidades de crescimento neste sistema operacional depende do
conhecimento, interesse e capacidade de cada um.


<listitem>

A interface gráfica existe, mas os melhores recursos e flexibilidade estão na
linha de comando.  Você pode ter certeza que o aprendizado no
<command>GNU/Linux ajudará a ter sucesso e menos dificuldade em usar
qualquer outro sistema operacional.


<listitem>

Peça ajuda a outros usuários do <command>GNU/Linux quando estiver em
dúvida ou não souber fazer alguma coisa no sistema.  Você pode entrar em
contato diretamente com outros usuários ou através de listas de discussão (veja
<xref linkend="ajuda-listas"/>).




Boa Sorte e bem vindo ao <command>GNU/Linux!


Gleydson (<email>gleydson@guiafoca.org).


	<!-- ]]> -->


 introducao-requisitos">###Pré-requisitos para a utilização deste guia
<para userlevel='inic'>
É assumido que você já tenha seu <command>GNU/Linux instalado e
funcionando. 

<para userlevel='inter'>
É assumido que você tenha entendido a função de boa parte dos
comandos que consta na versão iniciante do Foca Linux, arquivos e permissões de
acesso.  Em resumo, que saiba decidir quando e qual(is) comando(s) deve usar em
cada situação.

<para userlevel='inter'>
Caso não entenda as explicações da versão INTERMEDIÁRIO, recomendo que faça a
leitura da versão INICIANTE do Foca Linux que pode ser encontrada em ("http://www.w3.org/1999/xlink) []( [guiafoca](http://www.guiafoca.org)   [guiafoca](http://www.guiafoca.org) ).

<para userlevel='avanc'>
É assumido que você ja tenha experiência na configuração de sistemas <command>Linux,
conheça boa parte dos comandos e sua utilização, tenha noções de rede e saiba
como procurar documentação para complementar o que vem aprendendo.  Enfim,
requer que se tiver interesse em se aprofundar em determinada área, que utilize
os métodos de busca de documentação sugeridos no guia para complementação do
aprendizado.  O guia não contém todos os materiais para que a pessoa se torne
um <literal>expert no assunto, mas contém as referências para
documentações mais específicas sobre determinadas áreas do sistema. 


Este guia não cobre a instalação do sistema.  Para detalhes sobre instalação,
consulte a documentação que acompanha sua distribuição
<command>GNU/Linux.




 userlevel='inic' introducao-so">###Sistema Operacional

O **Sistema Operacional** é o conjunto de programas que fazem
a interface do usuário e seus programas com o computador.  Ele é responsável
pelo gerenciamento de recursos e periféricos (como memória, discos, arquivos,
impressoras, CD-ROMs, etc.), interpretação de mensagens e a execução de
programas.


No <command>Linux o Kernel mais o conjunto de ferramentas GNU compõem
o Sistema Operacional.  O kernel (que é a base principal de um sistema
operacional), poderá ser construído de acordo com a configuração do seu
computador e dos periféricos que possui.




 introducao-linux">###O Linux

O <command>Linux é um sistema operacional criado em 1991 por
**Linus Torvalds** na universidade de Helsinki na Finlândia.
É um sistema Operacional de código aberto distribuído gratuitamente pela
Internet.  Seu código fonte é liberado como **Free Software**
(software livre), sob licença GPL, o aviso de copyright do kernel feito por
Linus descreve detalhadamente isto e mesmo ele não pode fechar o sistema para
que seja usado apenas comercialmente.


Isto quer dizer que você não precisa pagar nada para usar o Linux, e não é
crime fazer cópias para instalar em outros computadores, nós inclusive
incentivamos você a fazer isto.  Ser um sistema de código aberto pode explicar
a performance, estabilidade e velocidade em que novos recursos são adicionados
ao sistema.


O requisito mínimo para rodar o <command>Linux depende do kernel que
será usado:

<itemizedlist>
<listitem>

<literal>2.2.x - Computador 386 SX com 2 MB de memória


<listitem>

<literal>2.4.x - Computador 386 SX com 4MB de memória


<listitem>

<literal>2.6.x - Computador 486 DX com no mínimo 8MB


<listitem>

<literal>3.x.x - Computador 586 com no mínimo 16MB


<listitem>

<literal>4.x.x - Computador 586 com no mínimo 32MB


<listitem>

<literal>5.x.x - Computador 686 com no mínimo 32MB


			


Para espaço em disco é requerido 900MB para uma instalação básica usando modo
texto com suporte a rede.  Claro que não é considerada a execução de ambiente
gráfico ou serviços de rede em produção, que neste caso é exigido mais memória
RAM e espaço em disco para armazenamento de dados de programas e usuários.


O sistema segue o padrão **POSIX** que é o mesmo usado por
sistemas **UNIX** e suas variantes.  Assim, aprendendo o
<command>Linux você não encontrará muita dificuldade em operar um
sistema do tipo <command>UNIX, FreeBSD, HPUX, SunOS, etc., bastando
apenas aprender alguns detalhes encontrados em cada sistema.


O código fonte aberto permite que qualquer pessoa veja como o sistema funciona
(útil para aprendizado), corrigir algum problema ou fazer alguma sugestão sobre
sua melhoria, esse é um dos motivos de seu rápido crescimento, do aumento da
compatibilidade de periféricos (como novas placas sendo suportadas logo após
seu lançamento) e de sua estabilidade.


Outro ponto em que ele se destaca é o suporte que oferece a placas, CD/DVD-RWs,
BluRay e outros tipos de dispositivos de última geração e mais antigos (a
maioria deles já ultrapassados e sendo completamente suportados pelo sistema
operacional).  Este é um ponto forte para empresas que desejam manter seus
micros em funcionamento e pretendem investir em avanços tecnológicos com as
máquinas que possui.


O <command>Linux é desenvolvido por milhares de pessoas espalhadas
pelo mundo, cada uma fazendo sua contribuição ou mantendo alguma parte do
kernel gratuitamente.  **Linus Torvalds** ainda trabalha em
seu desenvolvimento e na coordenação dos grupos de trabalho do kernel.


O suporte ao sistema também se destaca como sendo o mais eficiente e rápido do
que qualquer programa comercial disponível no mercado.  Existem milhares de
consultores e empresas especializadas no suporte e treinamento espalhados ao
redor do mundo.  Outra opção de suporte é através da comunidade Linux; você
pode se inscrever em uma lista de discussão e relatar sua dúvida ou alguma
falha, e sua mensagem será vista por centenas de usuários na Internet e algum
irá te ajudar ou avisará as pessoas responsáveis sobre a falha encontrada para
devida correção.

<para userlevel='inic;inter' >
Para detalhes, veja <xref linkend="ajuda-listas"/>.


 introducao-linux-carac">###Algumas Características do Linux
<itemizedlist>
<listitem>

É livre e desenvolvido voluntariamente por programadores experientes, hackers,
e contribuidores espalhados ao redor do mundo que tem como objetivo a
contribuição para a melhoria e crescimento deste sistema operacional.


Muitos deles estavam cansados do excesso de propaganda (Marketing) e baixa
qualidade de sistemas comerciais existentes


<listitem>

Também recebe apoio de grandes empresas como IBM, Sun, RedHat, Intel, HP, etc.  para seu
desenvolvimento


<listitem>

Convivem sem nenhum tipo de conflito com outros sistemas operacionais (com o
<command>Windows, <command>OS/2) no mesmo computador.


<listitem>

Multitarefa real


<listitem>

Multiusuário


<listitem>

Suporte a nomes extensos de arquivos e diretórios (255 caracteres)


<listitem>

Conectividade com outros tipos de plataformas como **Apple, Sun,
Macintosh, Sparc, Alpha, PowerPc, ARM, Unix, Windows, DOS, etc**.


<listitem>

Utiliza permissões de acesso a arquivos, diretórios e programas em execução na
memória RAM.


<listitem>

Proteção entre processos executados na memória RAM


<listitem>

Suporte a mais de 256 terminais virtuais (consoles)


<listitem>

Modularização - O <command>Linux somente carrega para a memória o que
é usado durante o processamento, liberando totalmente a memória assim que o
programa/dispositivo é finalizado


<listitem>

Devido a modularização, os drivers dos periféricos e recursos do sistema podem
ser carregados e removidos completamente da memória RAM a qualquer momento.  Os
drivers (módulos) ocupam pouco espaço quando carregados na memória RAM (cerca
de 6Kb para a Placa de rede NE 2000, por exemplo)


<listitem>

Suporte nativo a rede e tecnologias avançadas como: balanceamento de carga, ips
alias, failover, vlans, bridge, trunking, OSPF, BGP, MPLS.


<listitem>

Não há a necessidade de se reiniciar o sistema após a modificar a configuração
de qualquer periférico ou parâmetros de rede.  Somente é necessário reiniciar o
sistema no caso de uma instalação interna de um novo periférico, falha em algum
hardware (queima do processador, placa mãe, etc.).


<listitem>

Excepcional em escalabilidade desde computadores extreamemente simples,dispositivos móveis
(sistema Android utiliza kernel Linux), Raspberry PI, sistemas embarcados, geladeiras 
inteligentes, carros com centrais inteligentes, etc.  até sistemas de clusters
em núvem gigantescos (como Amazon, Digital Ocean, entre maiores datacenters
utilizados em núvens no mundo).


<listitem>

Suporte nativo a múltiplas CPUs e multi threads, assim processadores como Dual Core, Core Duo,
Athlon Duo, Quad Core, XEON, i3-i9 tem seu poder de processamento integralmente aproveitado,
tanto em 32 ou 64 bits.


<listitem>

Suporte nativo a dispositivos SSD, SATA, PATA, Fiber Channel


<listitem>

Suporte nativo a virtualização, onde o <command>Linux se destaca como
plataforma preferida para execução de múltiplos sistemas operacionais com
performance e segurança. Nuvens como Amazon, Digital Ocean utilizam nativamente
KVM para execucução de plataformas, assim como o sistema CGROUPs para execução 
de containers.


<listitem>

O crescimento e novas versões do sistema não provocam lentidão, pelo contrário,
a cada nova versão os desenvolvedores procuram buscar maior compatibilidade,
acrescentar recursos úteis e melhor desempenho do sistema (como o que aconteceu
na passagem do kernel 2.0.x para 2.2.x, da 2.2.x para a 2.4.x, da 3 para a 4.x.x,
da 4.x.x para a 5.x.x)


<listitem>

O <command>GNU/Linux é distribuido livremente e licenciado de acordo
com os termos da GPLv2.


<listitem>

Acessa corretamente discos formatados pelo <command>DOS, Windows, Novell, OS/2,
NTFS, SunOS, Amiga, Atari, Mac, etc.


<listitem>

O LINUX POSSUI MECANISMOS DE HARDENING AVANÇADOS CONTRA VÍRUS E MALWARES!  Devido 
a separação de privilégios entre processos e respeitadas as recomendações padrão 
de política de segurança e uso de contas privilegiadas (como a de root, como 
veremos adiante), programas como vírus tornam-se inúteis pois tem sua ação 
limitada pelas restrições de acesso do sistema de arquivos e execução.


Qualquer programa (nocivo ou não) poderá alterar partes do sistema que possui
permissões (será abordado como alterar permissões e tornar seu sistema mais
restrito no decorrer do guia).  Frequentemente são criados exploits que tentam
se aproveitar de falhas existentes em sistemas desatualizados e usa-las para
causar danos.  **Erroneamente** este tipo de ataque é
classificado como vírus por pessoas mal informadas e são resolvidas com
sistemas bem mantidos.  Em geral, usando uma boa distribuição que tenha um
eficiente sistema de atualização e bem configurado, você terá 99.9% de sua
tranquilidade.


<listitem>

Rede TCP/IP mais rápida que no Windows e tem sua pilha constantemente
melhorada.  O <command>GNU/Linux tem suporte nativo a redes TCP/IP e
não depende de uma camada intermediária como o WinSock.  Em acessos via modem a
Internet, a velocidade de transmissão é 10% maior.


<listitem>

Executa outros sistemas operacionais como **Windows**,
**MacOS**, **DOS** ou outro sistema
<command>Linux através de consagrados sistemas de virtualização como
<command>KVM, <command>Xen, <command>vmware
<command>VirtualBox, ou emulação como o <command>DOSEMU, 
<command>QEMU, <command>WINE.


<listitem>

Suporte completo e nativo a diversos dispositivos de comunicação via
infravermelho, Bluetooth, Firewire, USB.  Basta conectar e o seu dispositivo é
automaticamente reconhecido.  Raramente são necessários drivers externos,
exceto no caso de dispositivos muito novos que não tenham o suporte ainda
adicionado no sistema.


<listitem>
	
	Suporte a fiber channel.
	


<listitem>

Suporte a rede via rádio amador.


<listitem>

Suporte a dispositivos Plug-and-Play.


<listitem>

Suporte nativo a pen drivers, dispositivos de armazenamento e cartões de
memória.


<listitem>

Suporte nativo a dispositivos I2C


<listitem>

Integração com gerenciamento de energia ACPI e APM


<listitem>

Dispositivos de rede Wireless.  Tanto com criptografia WEB e WPA2/3 PSK


<listitem>

Vários tipos de firewalls avançados de alta qualidade na detecção de tráfego
indesejável, dando ao administrador uma excelente ferramenta de proteção e
controle de sua rede.


<listitem>

Roteamento estático e dinâmico de pacotes.


<listitem>

Ponte entre Redes, proxy arp


<listitem>

Proxy Tradicional e Transparente.


<listitem>

Possui recursos para atender a mais de um endereço IP na mesma placa de rede,
sendo muito útil para situações de manutenção em servidores de redes ou para a
emulação de "múltiplos computadores".


O servidor WEB e FTP podem estar localizados no mesmo computador, mas o usuário
que se conecta tem a impressão que a rede possui servidores diferentes.


<listitem>

Os sistemas de arquivos usados pelo <command>GNU/Linux
(<literal>Ext2, <literal>Ext3, <literal>reiserfs,
<literal>xfs, <literal>jfs) organiza os arquivos de forma
inteligente evitando a fragmentação e fazendo-o um poderoso sistema para
aplicações multi-usuárias exigentes e gravações intensivas.


<listitem>

Permite a montagem de um servidor de publicação Web, E-mail, News, etc.  com um
baixo custo e alta performance.  O melhor servidor Web do mercado, o
<command>Apache, é distribuído gratuitamente junto com a maioria das
distribuições Linux.  O mesmo acontece com o <command>Sendmail.


<listitem>

Por ser um sistema operacional de código aberto, você pode ver o que o código
fonte (instruções digitadadas pelo programador) faz e adapta-lo as suas
necessidades ou de sua empresa.  Esta característica é uma segurança a mais
para empresas sérias e outros que não querem ter seus dados roubados (você não
sabe o que um sistema sem código fonte faz na realidade enquanto esta
processando o programa).


<listitem>

Suporte a diversos dispositivos e periféricos disponíveis no mercado, tanto os
novos como obsoletos.


<listitem>

Pode ser executado em 16 arquiteturas diferentes (Intel, Macintosh, Alpha, Arm,
etc.) e diversas outras sub-arquiteturas.


<listitem>

Empresas especializadas e consultores especializados no suporte ao sistema
espalhados por todo o mundo.


<listitem>

Entre muitas outras características que você descobrirá durante o uso do
sistema (além de poder criar outras, caso seja um administrador avançado ou
desenvolvedor).




TODOS OS ÍTENS DESCRITOS ACIMA SÃO VERDADEIROS E TESTADOS PARA QUE TIVESSE
PLENA CERTEZA DE SEU FUNCIONAMENTO.





 userlevel="inic" introducao-distrib">###Distribuições do Linux

Só o kernel <command>GNU/Linux não é suficiente para se ter uma
sistema funcional, mas é o principal.


Existem grupos de pessoas, empresas e organizações que decidem "distribuir" o
Linux junto com outros aplicativos (como por exemplo <command>editores
gráficos, planilhas, bancos de dados, ambientes de programação, formatação de
documentos, firewalls, etc).


Este é o significado essencial de **distribuição**.  Cada
distribuição tem sua característica própria, como o sistema de instalação, o
objetivo, a localização de programas, nomes de arquivos de configuração, etc.
A escolha de uma distribuição é pessoal e depende das necessidades de cada um.


Algumas distribuições bastante conhecidas são: **Ubuntu, Debian,
Slackware, Red Hat, Gentoo, Suse** todas usando o SO Linux como kernel
principal (a <command>Debian é uma distribuição independente de
kernel e pode ser executada sob outros kernels, como o GNU hurd ou o kernel
BSD).


A escolha de sua distribuição deve ser feita com muita atenção, não adianta
muita coisa perguntar em canais de IRC sobre qual é a melhor distribuição, ser
levado pelas propagandas, pelo vizinho, etc.  O melhor caminho para a escolha
da distribuição, acredito eu, seria perguntar as características de cada uma e
porque essa pessoa gosta dela ao invés de perguntar qual é a melhor, porque
quem lhe responder isto estará usando uma distribuição que se encaixa de acordo
com suas necessidade e esta mesma distribuição pode não ser a melhor para lhe
atender.


Segue abaixo as características de algumas distribuições seguidas do site
principal e endereço para download:

<variablelist>

<varlistentry>
<term>**Debian**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.debian.org)http://www.debian.org/ -
Distribuição desenvolvida e atualizada através do esforço de voluntários
espalhados ao redor do mundo, seguindo o estilo de desenvolvimento
<command>GNU/Linux.  Por este motivo, foi adotada como a distribuição
oficial do projeto **GNU**.  Possui suporte a língua
Portuguesa, é a única que tem suporte a 9 arquiteturas diferentes (AMD64, i386, ARMEL,
ARMHF, MIPS,MIPSEL,MIPS64el, etc.) e aproximadamente 15
arquitetura não suportadas oficialmente.  A instalação da distribuição pode ser feita tanto através de
flash disks, CD-ROM, Tftp, Ftp, NFS, imagem Docker ou através da combinação de 
vários destes em cada etapa de instalação.


Acompanha mais de 59000 programas distribuídos em forma de pacotes cada um
destes programas são mantidos e testados pela pessoa ou grupo responsável por
seu empacotamento.  Os pacotes são divididos em diretórios de acordo com sua
categoria e gerenciados através de um avançado sistema de gerenciamento de
pacotes (o apt e o dpkg) facilitando a instalação e atualização de pacotes.
Possui tanto ferramentas para administração de redes e servidores quanto para
desktops, estações multimídia, jogos, desenvolvimento, web, etc.


A atualização da distribuição ou de pacotes individuais pode ser feita
facilmente através de 2 comandos, não requerendo adquirir um novo CD para usar
a última versão da distribuição.  É a única distribuição não comercial onde
todos podem contribuir usando seu conhecimento para o desenvolvimento.  Para
gerenciar os voluntários, conta com centenas de listas de discussão envolvendo
determinados desenvolvedores das mais diversas partes do mundo.


São feitos extensivos testes antes do lançamento de cada versão para atingir um
alto grau de confiabilidade.  As falhas encontradas nos pacotes podem ser
relatados através de um **sistema de tratamento de falhas**
que encaminha a falha encontrada diretamente ao responsável para avaliação e
correção.  Qualquer um pode receber a lista de falhas ou sugestões sobre a
distribuição cadastrando-se em uma das lista de discussão que tratam
especificamente da solução de falhas encontradas na distribuição (disponível na
página principal da distribuição).


Os pacotes podem ser instalados através de <literal>Tarefas contendo
seleções de pacotes de acordo com a utilização do computador (servidor Web,
desenvolvimento, TeX, jogos, desktop, etc.), **Perfis**
contendo seleções de pacotes de acordo com o tipo de usuário (programador,
operador, etc.), ou através de uma seleção individual de pacotes, garantindo
que somente os pacotes selecionados serão instalados fazendo uma instalação
enxuta.


Existe um time de desenvolvedores com a tarefa específica de monitorar
atualizações de segurança em serviços (apache, sendmail, e todos os outros
59000 pacotes) que possam comprometer o servidor, deixando-o vulnerável a
ataques.  Assim que uma falha é descoberta, é enviado uma alerta (DSA - Debian
Security Alert) e disponibilizada uma atualização para correção das diversas
versões da <command>Debian.  Isto é geralmente feito em menos de 48
horas desde a descoberta da falha até a divulgação da correção.  Como quase
todas as falhas são descobertas nos programas, este método também pode ser
usado por administradores de outras distribuições para manterem seu sistema
seguro e atualizado.


O suporte ao usuário e desenvolvimento da distribuição são feitos através de
listas de discussões e canais IRC.  Existem uma lista de consultores
habilitados a dar suporte e assistência a sistemas Debian ao redor do mundo na
área consultores do site principal da distribuição.


<literal>("http://www.w3.org/1999/xlink) [](ftp://ftp.debian.org)ftp://ftp.debian.org/ - Endereço
para download.




<varlistentry>
<term>**Ubuntu**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.ubuntu.com)http://www.ubuntu.com/ -
Variante da distribuição Debian voltada a interação mais amigável com o usuário
final e facilidade de instalação.  Atualmente é a melhor para usuários que tem
o primeiro contato com o Linux.  Conta tanto com a instalação do sistema em HD
e execução através de Live CD.


<literal>("http://www.w3.org/1999/xlink) [](http://www.ubuntu.com/getubuntu/download)http://www.ubuntu.com/getubuntu/download/
- Endereço para download do Ubuntu.




<varlistentry>
<term>**Slackware**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.slackware.com)http://www.slackware.com/ -
Distribuição desenvolvida por <literal>Patrick Volkerding,
desenvolvida para alcançar facilidade de uso e estabilidade como prioridades
principais.  Foi a primeira distribuição a ser lançada no mundo e costuma
trazer o que há de mais novo enquanto mantém uma certa tradição, provendo
simplicidade, facilidade de uso e com isso flexibilidade e poder.


Desde a primeira versão lançada em Abril de 1993, o Projeto <command>Slackware
Linux tem buscado produzir a distribuição <command>Linux
mais <literal>UNIX-like, ou seja, mais parecida com UNIX.  O
Slackware segue os padrões Linux como o Linux File System Standard, que é um
padrão de organização de diretórios e arquivos para as distribuições.


Enquanto as pessoas diziam que a Red Hat era a melhor distribuição para o
usuário iniciante, o <command>Slackware é o melhor para o usuário
mais "velho", ou seja programadores, administradores, etc.


<literal>("http://www.w3.org/1999/xlink) [](ftp://ftp.slackwarebrasil.org/linux/slackware)ftp://ftp.slackwarebrasil.org/linux/slackware/
- Ftp da distribuição Slackware.




<varlistentry>
<term>**SuSE**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.suse.com)http://www.suse.com/ -
Distribuição comercial Alemã com a coordenação sendo feita através dos
processos administrativos dos desenvolvedores e de seu braço norte-americano.
O foco da Suse é o usuário com conhecimento técnico no Linux (programador,
administrador de rede, etc.) e não o usuário iniciante no Linux.
Preferencialmente a administração deve ser feita usando o
<command>Yast, mas também pode ser feita manualmente através de
alteração dos arquivos de configuração.


Possui suporte as arquiteturas Intel x86 e Alpha.  Sua instalação pode ser
feita via CD-ROM ou CD-DVD (é a primeira distribuição com instalação através de
DVD).


Uma média de 2000 programas acompanham a versão 10 distribuídos em 6 DVDs.
O sistema de gerenciamento de pacotes é o RPM padronizado.  A seleção de
pacotes durante a instalação pode ser feita através da seleção do perfil de
máquina (developer, estação kde, gráficos, estação gnome, servidor de rede,
etc.) ou através da seleção individual de pacotes.


A atualização da distribuição pode ser feita através do CD-ROM de uma nova
versão ou baixando pacotes de ("http://www.w3.org/1999/xlink) [](ftp://ftp.suse.com)ftp://ftp.suse.com/.  Usuários registrados
ganham direito a suporte de instalação via e-mail.  A base de dados de suporte
também é excelente e está disponível na web para qualquer usuário independente
de registro.


<literal>("http://www.w3.org/1999/xlink) [](ftp://ftp.suse.com)ftp://ftp.suse.com/
- Ftp da distribuição SuSE.




<varlistentry>
<term>**Red Hat Enterprise Linux**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://www.redhat.com)http://www.redhat.com/ -
Distribuição comercial suportada pela Red Hat e voltada a servidores de grandes
e medias empresas.  Também conta com uma certificação chamada RHCE específica
desta distro.


Ela não está disponível para download, apenas vendida a custos a partir de 179
dólares (a versão workstation) até 1499 dólares (advanced server).




<varlistentry>
<term>**Fedora**
<listitem>

<literal>("http://www.w3.org/1999/xlink) [](http://fedora.redhat.com)http://fedora.redhat.com/ - O
Fedora Linux é a distribuição de desenvolvimento aberto patrocinada pela RedHat
e pela comunidade, originada em 2002 e baseada em versão da antiga linha de
produtos RedHat Linux.  Esta distribuição não é suportada pela Red Hat como
distribuição oficial (ela suporta apenas a linha Red Hat Enterprise Linux),
devendo obter suporte através da comunidade ou outros meios.


A distribuição <literal>Fedora dá prioridade ao uso do computador
como estação de trabalho.  Além de contar com uma ampla gama de ferramentas de
escritório possui funções de servidor e aplicativos para produtividade e
desenvolvimento de softwares.  Considerado um dos sistemas mais fáceis de
instalar e utilizar, inclui tradução para portugês do Brasil e suporte às
plataformas Intel e 64 bits.


Por basear-se no RedHat.  o Fedora conta com um o <command>up2date,
um software para manter o sistema atualizado e utiliza pacotes de programas no
formato RPM, um dos mais comuns.


O Fedora não é distribuido oficialmente através de mídias ou CDs, se você
quiser obte-lo terá de procurar distribuidores independentes ou fazer o
download dos 4 CDs através do site oficial.


<literal>("http://www.w3.org/1999/xlink) [](http://download.fedora.redhat.com/pub/fedora/linux/core/2/i386/iso)http://download.fedora.redhat.com/pub/fedora/linux/core/2/i386/iso/
- Download da distribuição Fedora.




</variablelist>

Para contato com os grupos de usuários que utilizam estas distribuições, veja
<xref linkend="ajuda-listas"/>.



	
 userlevel="inic;inter" introducao-software-livre">###Software Livre

(tradução do texto <literal>Linux e o Sistema GNU de <literal>Richard
Stallman obtido no site do CIPSGA: ("http://www.w3.org/1999/xlink) [](http://www.cipsga.org.br)http://www.cipsga.org.br/).  O projeto
**GNU** começou em 1983 com o objetivo de desenvolver um
sistema operacional Unix-like totalmente livre.  <literal>Livre se
refere à liberdade, e não ao preço; significa que você está livre para
executar, distribuir, estudar, mudar e melhorar o software.


Um sistema Unix-like consiste de muitos programas diferentes.  Nós achamos
alguns componentes já disponíveis como softwares livres -- por exemplo,
<command>X Window e <command>TeX.  Obtemos outros
componentes ajudando a convencer seus desenvolvedores a tornarem eles livres --
por exemplo, o Berkeley network utilities.  Outros componentes nós escrevemos
especificamente para o GNU -- por exemplo, <command>GNU Emacs, o
compilador <command>GNU C, o <command>GNU C library,
<command>Bash e <command>Ghostscript.  Os componentes desta
última categoria são "software GNU".  O sistema GNU consiste de todas as três
categorias reunidas.


O projeto GNU não é somente desenvolvimento e distribuição de alguns softwares
livres úteis.  O coração do projeto GNU é uma idéia: que software deve ser
**livre**, e que a liberdade do usuário vale a pena ser
defendida.  Se as pessoas têm liberdade mas não a apreciam conscientemente, não
irão mantê-la por muito tempo.  Se queremos que a liberdade dure, precisamos
chamar a atenção das pessoas para a liberdade que elas têm em programas livres.


O método do projeto GNU é que programas livres e a idéia da liberdade dos
usuários ajudam-se mutuamente.  Nós desenvolvemos software GNU, e conforme as
pessoas encontrem programas GNU ou o sistema GNU e comecem a usá-los, elas
também pensam sobre a filosofia GNU.  O software mostra que a idéia funciona na
prática.  Algumas destas pessoas acabam concordando com a idéia, e então
escrevem mais programas livres.  Então, o software carrega a idéia, dissemina a
idéia e cresce da idéia.


Em 1992, nós encontramos ou criamos todos os componentes principais do sistema
exceto o kernel, que nós estávamos escrevendo.  (Este kernel consiste do
microkernel Mach mais o GNU HURD.  Atualmente ele está funcionando, mas não
está preparado para os usuários.  Uma versão alfa deverá estar pronta em
breve.)


Então o kernel do Linux tornou-se disponível.  Linux é um kernel livre escrito
por Linus Torvalds compatível com o Unix.  Ele não foi escrito para o projeto
GNU, mas o Linux e o quase completo sistema GNU fizeram uma combinação útil.
Esta combinação disponibilizou todos os principais componentes de um sistema
operacional compatível com o Unix, e, com algum trabalho, as pessoas o tornaram
um sistema funcional.  Foi um sistema GNU variante, baseado no kernel do
<command>Linux.


Ironicamente, a popularidade destes sistemas desmerece nosso método de
comunicar a idéia GNU para as pessoas que usam GNU.  Estes sistemas são
praticamente iguais ao sistema GNU -- a principal diferença é a escolha do
kernel.  Porém as pessoas normalmente os chamam de "sistemas Linux (Linux
systems)".  A primeira impressão que se tem é a de que um "sistema Linux" soa
como algo completamente diferente de "sistema GNU", e é isto que a maioria dos
usuários pensam que acontece.


A maioria das introduções para o "sistema Linux" reconhece o papel desempenhado
pelos componentes de software GNU.  Mas elas não dizem que o sistema como um
todo é uma variante do sistema GNU que o projeto GNU vem compondo por uma
década.  Elas não dizem que o objetivo de um sistema Unix-like livre como este
veio do projeto GNU.  Daí a maioria dos usuários não saber estas coisas.


Como os seres humanos tendem a corrigir as suas primeiras impressões menos do
que as informações subseqüentes tentam dizer-lhes, estes usuários que depois
aprendem sobre a relação entre estes sistemas e o projeto GNU ainda geralmente
o subestima.


Isto faz com que muitos usuários se identifiquem como uma comunidade separada
de "usuários de Linux", distinta da comunidade de usuários GNU.  Eles usam
todos os softwares GNU; de fato, eles usam quase todo o sistema GNU; mas eles
não pensam neles como usuários GNU, e freqüentemente não pensam que a filosofia
GNU está relacionada a eles.


Isto leva a outros problemas também -- mesmo dificultando cooperação com a
manutenção de programas.  Normalmente quando usuários mudam um programa GNU
para fazer ele funcionar melhor em um sistema específico, eles mandam a mudança
para o mantenedor do programa; então eles trabalham com o mantenedor explicando
a mudança, perguntando por ela, e às vezes reescrevendo-a para manter a
coerência e mantenebilidade do pacote, para ter o patch instalado.


Mas as pessoas que pensam nelas como "usuários Linux" tendem a lançar uma
versão "Linux-only" do programa GNU, e consideram o trabalho terminado.  Nós
queremos cada e todos os programas GNU que funcionem "out of the box" em
sistemas baseados em Linux; mas se os usuários não ajudarem, este objetivo se
torna muito mais difícil de atingir.


Como deve o projeto GNU lidar com este problema?  O que nós devemos fazer agora
para disseminar a idéia de que a liberdade para os usuários de computador é
importante?


Nós devemos continuar a falar sobre a liberdade de compartilhar e modificar
software -- e ensinar outros usuários o valor destas liberdades.  Se nós nos
beneficiamos por ter um sistema operacional livre, faz sentido para nós pensar
em preservar estas liberdades por um longo tempo.  Se nós nos beneficiamos por
ter uma variedade de software livres, faz sentido pensar sobre encorajar outras
pessoas a escrever mais software livre, em vez de software proprietário.


Nós não devemos aceitar a idéia de duas comunidades separadas para GNU e Linux.
Ao contrário, devemos disseminar o entendimento de que "sistemas Linux" são
variantes do sistema GNU, e que os usuários destes sistemas são tanto usuários
GNU como usuários Linux (usuários do kernel do Linux).  Usuários que têm
conhecimento disto irão naturalmente dar uma olhada na filosofia GNU que fez
estes sistemas existirem.


Eu escrevi este artigo como um meio de fazer isto.  Outra maneira é usar os
termos "sistema GNU baseado em Linux (Linux-based GNU system)" ou "sistema
GNU/Linux (GNU/Linux system)", em vez de "sistema Linux", quando você escreve
sobre ou menciona este sistema.



 userlevel="inic" introducao-processamento">###Processamento de Dados

**Processamento de Dados** é o envio de dados ao computador
que serão processados e terão um resultado de saída útil.


Veja também <xref linkend="introducao-disp-e-s"/>.



 userlevel="inic" introducao-computador">###O Computador

É uma máquina eletrônica que processa e armazena os dados e pode executar
diversos programas para realizar uma série de tarefas e assim atender a
necessidade do seu utilizador.  O computador não é uma máquina inteligente, ele
apenas executa as instruções dos programas que foram escritos pelo programador.



 userlevel="inic" introducao-conhecendo">###Conhecendo o Computador

Esta explica para que serve cada botão do painel do computador e monitor de
vídeo.  Se você já sabe para que cada um serve, recomendo pular esta parte, é o
BE-A-BA.  :-)


Todo computador possuem funções que são usados em outros tipos e modelos.  Você
pode ter um modelo de computador e um amigo seu outro tipo e mesmo tendo
aparência diferente, terão as mesmas funções.


 userlevel="inic" introducao-conhecendo-tipo">###Tipos de Gabinete

Quanto ao tipo, o gabinete pode ser **Desktop**,
**Mini-torre** e **Torre**.

<variablelist>
<varlistentry>
<term>**Desktop**
<listitem>

É usado na posição **Horizontal** (como o vídeo cassete).  Sua
característica é que ocupa pouco espaço em uma mesa, pois pode ser colocado sob
o monitor.  A desvantagem é que normalmente possui pouco espaço para a
colocação de novas placas e periféricos.  Outra desvantagem é a dificuldade na
manutenção deste tipo de equipamento (hardware).



<varlistentry>
<term>**Mini-Torre**
<listitem>

É usado na posição **Vertical** (torre).  É o modelo mais
usado.  Sua característica é o espaço interno para expansão e manipulação de
periféricos.  A desvantagem é o espaço ocupado em sua mesa :-).



<varlistentry>
<term>**Torre**
<listitem>

Possui as mesmas características do **Mini-torre**, mas tem
uma altura maior e mais espaço para colocação de novos periféricos.  Muito
usado em servidores de rede e placas que requerem uma melhor refrigeração.



</variablelist>



 userlevel="inic" introducao-conhecendo-painel">###Painel Frontal

O painel frontal do computador tem os botões que usamos para ligar, desligar, e
acompanhar o funcionamento do computador.  Abaixo o significado de cada um:

<variablelist>
<varlistentry>
<term>**Botão POWER**
<listitem>

Liga/Desliga o computador.



<varlistentry>
<term>**Botão TURBO**
<listitem>

Se ligado, coloca a placa mãe em operação na velocidade máxima (o padrão).
Desligado, faz o computador funcionar mais lentamente (depende de cada placa
mãe).  Deixe sempre o **TURBO** ligado para seu computador
trabalhar na velocidade máxima de processamento.



<varlistentry>
<term>Botão RESET
<listitem>

Reinicia o computador.  Quando o computador é reiniciado, uma nova partida é
feita (é como se nós ligássemos novamente o computador).  Este botão é um dos
mais usados por usuários <command>Windows dentre os botões
localizados no painel do microcomputador.  No <command>GNU/Linux é
raramente usado (com menos freqüência que a tecla <literal>SCROLL
LOCK).


É recomendado se pressionar as teclas &lt;CTRL&gt; &lt;ALT&gt; &lt;DEL&gt; para
reiniciar o computador e o botão **RESET** somente em último
caso, pois o &lt;CTRL&gt; &lt;ALT&gt; &lt;DEL&gt; avisa ao Linux que o usuário
pediu para o sistema ser reiniciado assim ele poderá salvar os arquivos, fechar
programas e tomar outras providências antes de resetar o computador.



<varlistentry>
<term>KEYLOCK
<listitem>

Permite <literal>ligar/desligar o teclado.  É acionado por uma chave
e somente na posição "Cadeado Aberto" permite a pessoa usar o teclado (usar o
computador).  Alguns computadores não possuem KEYLOCK.



<varlistentry>
<term>LED POWER
<listitem>

Led (normalmente verde) no painel do computador que quando aceso, indica que o
computador está ligado.  O led é um diodo emissor de luz (light emission diode)
que emite luz fria.



<varlistentry>
<term>LED TURBO
<listitem>

Led (normalmente amarelo) no painel do computador.  Quando esta aceso, indica
que a chave turbo está ligada e o computador funcionando a toda velocidade.


Raramente as placas mãe Pentium e acima usam a chave turbo.  Mesmo que exista
no gabinete do micro, encontra-se desligada.



<varlistentry>
<term>LED HDD
<listitem>

Led (normalmente vermelho) no painel do computador.  Acende quando o disco
rígido (ou discos) do computador esta sendo usado.


Também acende quando uma unidade de CD-ROM está conectada na placa mãe e for
usado.



</variablelist>



 userlevel="inic" introducao-conhecendo-monitor">###Monitor de Vídeo

O monitor de vídeo se divide em dois tipos:

<itemizedlist>
<listitem>

**Monocromático** - Mostra tons de cinza


<listitem>

**Policromático** - A conhecida tela colorida




Quanto ao padrão do monitor, existem diversos:

<variablelist>
<varlistentry>
<term>**CGA** - Color Graphics Adapter
<listitem>

Capacidade de mostrar 4 cores simultâneas em modo gráfico.  Uma das primeiras
usadas em computadores PCs, com baixa qualidade de imagem, poucos programas
funcionavam em telas CGA, quase todos em modo texto.  Ficou muito conhecida
como "tela verde" embora existem modelos CGA preto e branco.



<varlistentry>
<term>**Hércules**
<listitem>

Semelhante ao CGA.  Pode mostrar 2 cores simultâneas em modo gráfico.  A
diferença é que apresenta uma melhor qualidade para a exibição de gráficos mas
por outro lado, uma grande variedade de programas para monitores CGA não
funcionam com monitores Hércules por causa de seu modo de vídeo.  Também é
conhecido por sua imagem <literal>amarela.


Dependendo da placa de vídeo, você pode configurar um monitor Hércules
monocromático para trabalhar como **CGA**.



<varlistentry>
<term>**EGA** - Enhanced Graphics Adapter
<listitem>

Capacidade de mostrar 16 cores simultâneas em modo gráfico.  Razoável melhora
da qualidade gráfica, mais programas rodavam neste tipo de tela.  Ficou mais
conhecida após o lançamento dos computadores 286, mas no Brasil ficou pouco
conhecida pois logo em seguida foi lançada o padrão VGA.



<varlistentry>
<term>**VGA** - Video Graphics Array
<listitem>

Capacidade de mostrar 256 cores simultâneas.  Boa qualidade gráfica, este
modelo se mostrava capaz de rodar tanto programas texto como gráficos com ótima
qualidade de imagem.  Se tornou o padrão mínimo para rodar programas em modo
gráfico.



<varlistentry>
<term>**SVGA** - Super Video Graphics Array
<listitem>

Atual padrão de mercado, capaz de mostrar até 16 milhões de cores simultâneas.
Excelente qualidade gráfica, também capaz de operar corretamente em modo texto.



</variablelist>





 userlevel="inic" introducao-placamae">###Placa Mãe

É a placa principal do sistema onde estão localizados o Processador, Memória
RAM, Memória Cache, BIOS, CMOS, RTC, etc.  A placa mãe possui encaixes onde são
inseridas placas de extensão (para aumentar as funções do computador).  Estes
encaixes são chamados de "<literal>SLOTS".


 userlevel="inic" introducao-placamae-outros">###Alguns componentes da placa mãe

Abaixo a descrição de alguns tipos de componentes eletrônicos que estão
presentes na placa mãe.  Não se preocupe se não entender o que eles significam
agora:

<itemizedlist>
<listitem>

<literal>RAM - Memória de Acesso Aleatório (Randomic Access Memory).
É uma memória de armazenamento temporário dos programas e depende de uma fonte
de energia para o armazenamento dos programas.  É uma memória eletrônica muito
rápida assim os programas de computador são executados nesta memória.  Seu
tamanho é medido em Kilobytes, Megabytes ou Gigabytes.


Os chips de memória **RAM** podem ser independentes (usando
circuitos integrados encaixados em soquetes na placa mãe) ou agrupados placas
de 30 pinos, 72 pinos e 168 pinos.


Quanto maior o tamanho da memória, mais espaço o programa terá ao ser
executado.  O tamanho de memória RAM pedido por cada programa varia, o
<command>GNU/Linux precisa de no mínimo 8 MB de memória RAM para ser
executado pelo processador.


<listitem>

<literal>PROCESSADOR - É a parte do computador responsável pelo
processamentos das instruções matemáticas/lógicas e programas carregados na
memória **RAM**.


<listitem>

<literal>CO-PROCESSADOR - Ajuda o Processador principal a processar
as instruções matemáticas.  É normalmente embutido no Processador principal em
computadores a partir do **486 DX2-66**.  Em processadores
Pentium e superiores, o co-processador é sempre embutido no processador.


<listitem>

<literal>CACHE - Memória de Armazenamento Auxiliar do Processador.
Possui alta velocidade de funcionamento, normalmente a mesma que o processador.
Serve para aumentar o desempenho de processamento.  A memória Cache pode ser
embutida na placa mãe ou encaixada externamente através de módulos L2.


<listitem>

<literal>BIOS - É a memória **ROM** que contém as
instruções básicas para a inicialização do computador, reconhecimento e
ativação dos periféricos conectados a placa mãe.  As **BIOS**
mais modernas (a partir do 286) também trazem um programa que é usado para
configurar o computador modificando os valores localizados na
**CMOS**.


As placas controladoras SCSI possuem sua própria **BIOS** que
identificam automaticamente os periféricos conectados a ela.  Os seguintes
tipos de chips podem ser usados para gravar a **BIOS**:

<itemizedlist>
<listitem>

<literal>ROM - Memória Somente para Leitura (Read Only Memory).
Somente pode ser lida.  É programada de fábrica através de programação elétrica
ou química.


<listitem>

<literal>PROM - Memória Somente para Leitura Programável (Programable
Read Only Memory) idêntica a **ROM** mas que pode ser
programada apenas uma vez por máquinas "Programadoras PROM".  É também chamada
de <literal>MASK ROM.


<listitem>

<literal>EPROM - Memória semelhante a **PROM**, mas
seu conteúdo pode ser apagado através raios ultra-violeta.


<listitem>

<literal>EEPROM - Memória semelhante a **PROM**, mas
seu conteúdo pode ser apagado e regravado.  Também é chamada de
**Flash**.




<listitem>

<literal>CMOS - É uma memória temporária alimentada por uma Bateria
onde são lidas/armazenadas as configurações do computador feitas pelo programa
residente na BIOS.








 userlevel="inic" introducao-memoria">###Memória do Computador

A memória é a parte do computador que permitem o armazenamento de dados.  A
memória é dividida em dois tipos: Principal e Auxiliar.  Normalmente quando
alguém fala em "memória de computador" está se referindo a memória "Principal".
Veja abaixo as descrições de **Memória Principal** e
**Auxiliar**.



 userlevel="inic" introducao-memoria-principal">###Memória Principal

É um tipo de memória eletrônica que depende de uma fonte de energia para manter
os dados armazenados e perde os dados quando a fonte de energia é desligada.  A
memória **RAM** do computador (Randomic Access Memory -
Memória de Acesso aleatório) é o principal exemplo de memória de armazenamento
Principal.


Os dados são armazenados em circuitos integrados ("chips") e enquanto você está
usando seu computador, a **RAM** armazena e executa seus
programas.  Os programas são executados na memória **RAM**
porque a memória eletrônica é muito rápida.  As memórias EDO, DIMM, DDR, DDR2,
DDR3 são exemplos de memória **RAM**.


Se desligarmos o computador ou ocorrer uma queda de energia, você perderá os
programas que estiverem em execução ou o trabalho que estiver fazendo.  Por
esse motivo é necessário o uso de uma memória auxiliar (veja <xref linkend="introducao-memoria-auxiliar"/>).




 userlevel="inic" introducao-memoria-auxiliar">###Memória Auxiliar

São dispositivos que NÃO dependem de uma fonte de energia para manter os dados
armazenados, os dados não são perdidos quando a fonte de energia é desligada.
As **Memórias Auxiliares** são muito mais lentas que as
**Memórias Principais** porque utilizam mecanismos mecânicos e
elétricos (motores e eletroímãs) para funcionar e fazer a leitura/gravação dos
dados.  Existem também modelos chamados disco de estado sólido (SSD), os dados
são armazenados em chips eletrônicos ao invés de mecanismos mecânicos.


Um exemplo de dispositivos de armazenamento auxiliar são os pen drives,
disquetes, cartões SD, discos rígidos, unidades de fita, Zip Drives,
DVD/CD/BluRay, etc.


A **Memória Auxiliar** resolve o problema da perda de dados
causado pela **Memória Principal** quando o computador é
desligado, desta forma podemos ler nossos arquivos e programas da
**memória Auxiliar** e copia-los para a **Memória
Principal** (memória RAM) para que possam ser novamente usados.


Um exemplo simples é de quando estiver editando um texto e precisar salva-lo, o
que você faz é simplesmente salvar os dados da memória **RAM**
que estão sendo editados para o disco rígido, desta forma você estará guardando
seu documento na **Memória Auxiliar**.


Este tipo de memória é mais lento que a memória principal, é por este motivo
que os programas somente são carregados e executados na **Memória
Principal**.






 userlevel="inic" introducao-discos">###Discos

Os discos são memórias de armazenamento Auxiliares.  Entre os vários tipos de
discos existentes, posso citar os Flexíveis, Rígidos, Pen-drives, SSD e CDs.
Veja as explicações sobre cada um deles abaixo.



 userlevel="inic" introducao-discos-flexiveis">###Discos Flexíveis

São discos usados para armazenar e transportar pequenas quantidades de dados.
Este tipo de disco é normalmente encontrado no tamanho 3 1/2 (1.44MB) polegadas
e 5 1/4 polegadas (360Kb ou 1.2MB).  Hoje os discos de 3 1/2 são os mais
utilizados por terem uma melhor proteção por causa de sua capa plástica rígida,
maior capacidade e o menor tamanho o que facilita seu transporte.


Os disquetes são inseridos em um compartimento chamado de "<literal>Unidade de
Disquetes" ou "<literal>Drive" que faz a leitura/gravação
do disquete.


Sua característica é a baixa capacidade de armazenamento e baixa velocidade no
acesso aos dados mas podem ser usados para transportar os dados de um
computador a outro com grande facilidade.  Os disquetes de computador comuns
são discos flexíveis.




 userlevel="inic" introducao-discos-rigidos">###Disco Rígido

É um disco localizado dentro do computador.  É fabricado com discos de metal
recompostos por material magnético onde os dados são gravados através de
cabeças e revestido externamente por uma proteção metálica que é preso ao
gabinete do computador por parafusos.  Também é chamado de HD (Hard Disk) ou
Winchester.  É nele que normalmente gravamos e executamos nossos programas mais
usados.


Existe também um tipo de disco rígido chamado **SSD** (disco
de estado sólido).  A diferença deste disco para o disco rígido comum, é que no
SSD os dados são armazenados em chips ao invés de disco magnético.


A característica deste tipo de disco é a alta capacidade de armazenamento de
dados e alta velocidade no acesso aos dados.




 userlevel="inic" introducao-discos-cd">###CD/DVD/BluRay

É um tipo de disco que permite o armazenamento de dados através de um
**compact disc** e os dados são lidos através de uma lente
ótica.  A Unidade de CD é localizada no gabinete do computador e pode ler CDs
de músicas, arquivos, interativos, etc.  Existem diversos tipos de CDs no
mercado, entre eles:

<itemizedlist>
<listitem>

<literal>CD-R - CD gravável, pode ser gravado apenas uma vez.  Possui
sua capacidade de armazenamento entre <literal>600MB e
<literal>740MB dependendo do formato de gravação usado.  Usa um
formato lido por todas as unidades de CD-ROM disponíveis no mercado.


<listitem>

<literal>CD-RW - CD regravável, pode ser gravado várias vezes, ter
seus arquivos apagados, etc.  Seu uso é semelhante ao de um disquete de alta
capacidade.  Possui capacidade de armazenamento de normalmente
<literal>640MB mas isto depende do fabricante.  Usa um formato que é
lido apenas por unidades leitoras e gravadoras multiseção.


<listitem>

<literal>DVD-ROM - Alta capacidade de armazenamento.  Pode armazenar
até 8GB de arquivos ou programas quando usado em dual layer.
<literal>BluRay - Alta capacidade de armazenamento.  Pode armazenar
mais de 50GB de arquivos ou programas quando usado em dual layer.  É um tipo de
CD muito novo no mercado e ainda em desenvolvimento.  É lido somente por
unidades próprias para este tipo de disco.








 userlevel="inic" introducao-cuidados">###Cuidados Básicos com o Computador

Abaixo uma lista de cuidados básicos para garantir uma melhor conservação e
funcionamento de seu computador.

<itemizedlist>
<listitem>

Não deixe seu computador em locais expostos a umidade ou sol.  O mesmo se
aplica a mídias como pen-drives, gavetas de HD, cartões de memória etc.


<listitem>

Limpe o Gabinete e o Monitor com um pano levemente umedecido em água com sabão
neutro ou solução de limpeza apropriada para micros.  Não use Álcool,
querosene, acetona ou qualquer outro tipo de produto abrasivo.  O uso de um
destes podem estragar o gabinete de seu computador e se um destes produtos
atingir a parte interna pode causar problemas nas placas ou até um incêndio!


<listitem>

Não retire o Pino central da tomada do computador, ele não veio sobrando e tem
utilidade!  Este pino é ligado a carcaça do computador (chassis) e deve ser
ligado ao terra de sua rede elétrica.  As descargas elétricas vindas da fonte e
componentes do micro são feitas no chassis e se este pino for retirado você
poderá tomar choques ao tocar em alguma parte metálica do micro e queimar
componentes sensíveis como o disco rígido, placa mãe, etc.


Se estiver em dúvida consulte um eletricista de confiança.


<listitem>

Não instale seu computador muito próximo de campos magnéticos com televisores,
aparelhos de som, motores, etc.  Estes aparelhos geram ruídos elétricos e/ou
magnéticos que podem prejudicar o bom funcionamento de seu micro.
<!-- [ %OBS [ -->
OBS: As
caixas de som de kits multimídia possuem os ímãs revestidos de metais em seus
auto-falantes para não causar nenhuma interferência ao computador. <!-- ]]> -->


<listitem>

Não use a bandeja da unidade de CD/DVD como porta copos!


<listitem>

Não coloque objetos dentro da unidade de disquetes.


<listitem>

Antes de desligar seu computador, utilize o comando <literal>"shutdown -h
now" (ou seus sinonimos, como <literal>"halt",
<literal>poweroff) para desligar corretamente o computador.  Este
comando finaliza adequadamente os programas, salva os dados, desmontar os
sistemas de arquivos <command>GNU/Linux.  Para detalhes veja <xref linkend="introducao-desligando"/>.






 userlevel="inic" introducao-disp-e-s">###Dispositivos de Entrada e Saída
<itemizedlist>
<listitem>

<literal>Entrada - Permite a comunicação do usuário com o computador.
São dispositivos que <literal>enviam dados ao computador para
processamento.  Exemplos: Teclado, mouse, touch screen, caneta ótica, scanner.


O dispositivo de entrada padrão (stdin) em sistemas
<command>GNU/Linux é o teclado.


<listitem>

<literal>Saída - Permite a comunicação do computador com o usuário.
São dispositivos que permitem o usuário visualizar o resultado do processamento
enviado ao computador.  Exemplos: Monitor, Impressora, Plotter, som.


O dispositivo de saída padrão (stdout) em sistemas <command>GNU/Linux
é o Monitor.






 userlevel="inic" introducao-ligando">###Ligando o computador

Para ligar o computador pressione o botão **POWER** ou
**I/O** localizado em seu painel frontal do micro.


Imediatamente entrará em funcionamento um programa residente na memória
**ROM** (Read Only Memory - memória somente para leitura) da
placa mãe que fará os testes iniciais para verificar se os principais
dispositivos estão funcionando em seu computador (memória RAM, discos,
processador, portas de impressora, memória cache, etc).


Quando o ROM termina os testes básicos, ele inicia a procura do setor de boot
nos discos do computador que será carregado na memória RAM do computador.  Após
carregar o setor de boot, o sistema operacional será iniciado (veja <xref linkend="introducao-so"/>).  O setor de boot contém a porção principal usada
para iniciar o sistema operacional.


No <command>GNU/Linux, o setor de boot normalmente é criado por um
gerenciador de inicialização (um programa que permite escolher qual sistema
operacional será iniciado).  Deste modo podemos usar mais de um sistema
operacional no mesmo computador (como o DOS e Linux).  Os gerenciadores de
inicialização mais usados em sistemas <command>GNU/Linux na
plataforma Intel X86 são o <command>GRUB e o <command>LILO.


Caso o ROM não encontre o sistema operacional em nenhum dos discos, ele pedirá
que seja inserido um disquete contendo o Sistema Operacional para partida.




 userlevel="inic" introducao-desligando">###Desligando o computador

Para desligar o computador primeiro digite (como root): <literal>"shutdown -h
now", <literal>"halt" ou <literal>"poweroff", o
<command>GNU/Linux finalizará os programas e gravará os dados em seu
disco rígido, quando for mostrada a mensagem <literal>"power down",
pressione o botão **POWER** em seu gabinete para desligar a
alimentação de energia do computador.

<!-- [ %OBS [ -->

**NUNCA** desligue diretamente o computador sem
usar o comando <command>shutdown, <command>halt ou
<command>poweroff, pois podem ocorrer perda de dados ou falhas no
sistema de arquivos de seu disco rígido devido a programas abertos e dados
ainda não gravados no disco.


Salve seus trabalhos para não correr o risco de perde-los durante o
desligamento do computador.

<!-- ]]> -->



 userlevel="inic" introducao-reiniciando">###Reiniciando o computador

Reiniciar quer dizer iniciar novamente o sistema.  Não é recomendável desligar
e ligar constantemente o computador pelo botão <literal>ON/OFF, por
este motivo existe recursos para reiniciar o sistema sem desligar o computador.
No <command>GNU/Linux você pode usar o comando
<literal>reboot, <literal>shutdown -r now e também
pressionar simultaneamente as teclas &lt;CTRL&gt; &lt;ALT&gt; &lt;DEL&gt; para
reiniciar de uma forma segura.

<!-- [ %OBS [ -->

Observações:

<itemizedlist>
<listitem>

Salve seus trabalhos para não correr o risco de perde-los durante a
reinicialização do sistema.


<listitem>

O botão reset do painel frontal do computador também reinicia o computador, mas
de uma maneira mais forte pois está ligado diretamente aos circuitos da placa
mãe e o sistema será reiniciado imediatamente, não tendo nenhuma chance de
finalizar corretamente os programas, gravar os dados da memória no disco e
desmontar os sistemas de arquivos.  O uso indevido da tecla reset pode causar
corrompimentos em seus arquivos e perdas.


Prefira o método de reinicialização explicado acima e use o botão reset somente
em último caso.



<!-- ]]> -->



