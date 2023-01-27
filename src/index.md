<?xml version="1.0" standalone="no"?>
<!DOCTYPE book [

<!--
Guia Foca GNU/Linux

Estilo de tagas de marcação usada no Guia Foca XML:
- Nome de Programa, nome de comando      - <command>
- Nome de pacote                         - <package>
- Texto sem formatação, saida de comando - <screen>
- Saída de comando, entrada no 
  teclado, parâmetros e comandos    - <literal>
- Nome de arquivo, diretório, modulo- <filename>
- Parte em destaque no texto        - **
- Aviso de observação, atenção, etc - **
- Nome de variável                  - <replaceable>


Copyleft 1999-2021, Gleydson Mazioli da Silva <gleydson@guiafoca.org>
-->

<!-- Definições de entities dinâmicas usadas no Foca Linux -->
<!--- <!ENTITY --->% dinamic    SYSTEM "dinamicas.md" > %dinamic;
<!--- <!ENTITY --->% definicoes SYSTEM "padroes.md"   > %definicoes;
<!--- <!ENTITY --->% urldata    SYSTEM "urls.md"      > %urldata;
<!--- <!ENTITY --->% versao     SYSTEM "versao.md"    > %versao;

<!-- Arquivos separados contendo o texto do Documento -->
<!--                Versão Iniciante                       -->
<!--- <!ENTITY --->introducao         SYSTEM "Iniciante/introducao.md"         >
<!--- <!ENTITY --->basico             SYSTEM "Iniciante/basico.md"             >
<!--- <!ENTITY --->discos             SYSTEM "Iniciante/discos.md"             >
<!--- <!ENTITY --->ajuda              SYSTEM "Iniciante/ajuda.md"              >
<!--- <!ENTITY --->migrando           SYSTEM "Iniciante/migrando.md"           >
<!--- <!ENTITY --->comandos-arquivo   SYSTEM "Iniciante/comandos-arquivo.md"   >
<!--- <!ENTITY --->comandos-contas    SYSTEM "Iniciante/comandos-contas.md"    >
<!--- <!ENTITY --->comandos-diretorio SYSTEM "Iniciante/comandos-diretorio.md" >
<!--- <!ENTITY --->comandos-diversos  SYSTEM "Iniciante/comandos-diversos.md"  >
<!--- <!ENTITY --->comandos-rede      SYSTEM "Iniciante/comandos-rede.md"      >
<!--- <!ENTITY --->configurando       SYSTEM "Iniciante/configurando.md"       >
<!--- <!ENTITY --->redir              SYSTEM "Iniciante/redir.md"              >
<!--- <!ENTITY --->run                SYSTEM "Iniciante/run.md"                >
<!--- <!ENTITY --->impressao          SYSTEM "Iniciante/impressao.md"          >
<!--- <!ENTITY --->x11                SYSTEM "Iniciante/x11.md"                >
<!--- <!ENTITY --->permissoes         SYSTEM "Iniciante/permissoes.md"         >
<!--- <!ENTITY --->apendice           SYSTEM "Iniciante/apendice.md"           >

<!--                  Versão Intermediário                     -->
<!--- <!ENTITY --->aplicativos        SYSTEM "Intermediario/aplicativos.md"    >
<!--- <!ENTITY --->bootloaders        SYSTEM "Intermediario/bootloaders.md"    >
<!--- <!ENTITY --->compactadores      SYSTEM "Intermediario/compactadores.md"  >
<!--- <!ENTITY --->compilacao         SYSTEM "Intermediario/compilacao.md"     >
<!--- <!ENTITY --->debian             SYSTEM "Intermediario/debian.md"         >
<!--- <!ENTITY --->dpkg               SYSTEM "Intermediario/dpkg.md"           >
<!--- <!ENTITY --->hardware           SYSTEM "Intermediario/hardware.md"       >
<!--- <!ENTITY --->kernel             SYSTEM "Intermediario/kernel.md"         >
<!--- <!ENTITY --->log                SYSTEM "Intermediario/log.md"            >
<!--- <!ENTITY --->manutencao         SYSTEM "Intermediario/manutencao.md"     >
<!--- <!ENTITY --->internet           SYSTEM "Intermediario/internet.md"       >
<!--- <!ENTITY --->personalizacao     SYSTEM "Intermediario/personalizacao.md" >
<!--- <!ENTITY --->tasks              SYSTEM "Intermediario/tasks.md"          >
<!--- <!ENTITY --->etc                SYSTEM "Intermediario/etc.md"            >
<!--- <!ENTITY --->rede               SYSTEM "Intermediario/rede.md"           >

<!--                  Versão Avançado                         -->
<!-- % apache         SYSTEM "Avancado/apache/Apache-INDEX.md"> %apache; -->
<!-- % cfgrede      SYSTEM "Avancado/conf-rede/CFGRede-INDEX.md"> %cfgrede; -->
<!-- ENTITY % iptables     SYSTEM "Avancado/iptables-firewall/iptables-INDEX.md"> %iptables; -->
<!-- ENTITY % contas       SYSTEM "Avancado/gerenc-contas/contas-INDEX.md"> %contas; -->
<!-- ENTITY % restricoes   SYSTEM "Avancado/restr-seguranca/restricoes-INDEX.md"> %restricoes; -->
<!-- ENTITY % criptografia SYSTEM "Avancado/criptografia/Cripto-INDEX.md"> %criptografia; -->
<!-- ENTITY % ident        SYSTEM "Avancado/identd/Ident-INDEX.md"> %ident; -->
<!-- ENTITY % telnet       SYSTEM "Avancado/telnet/telnet-INDEX.md"> %telnet; -->
<!--  % ssh          SYSTEM "Avancado/ssh/ssh-INDEX.md"> %ssh; -->
<!-- % pop3         SYSTEM "Avancado/pop3/pop3-INDEX.md"> %pop3; -->
<!--  % cvs          SYSTEM "Avancado/cvs/CVS-INDEX.md"> %cvs; -->
<!-- % samba        SYSTEM "Avancado/samba/SAMBA-INDEX.md"> %samba; -->

]>

<book<!---  [docbook](http://docbook.org/ns/docbook)" ---> http://www.w3.org/2001/XInclude" version="5.0" xml:lang="pt">

###Guia Foca Linux
<titleabbrev>focalinux</titleabbrev>
<subtitle>
<img src="images/src/png/foca-highres.png" format="PNG"/>


<bookinfo>

    <legalnotice>
    
Permission is granted to copy, distribute and/or modify this document under the
terms of the GNU Free Documentation License, Version 1.2 published by the Free
Software Foundation; A copy of the license is included in the section entitled
"GNU Free Documentation License".
    
    

<author><firstname>Gleydson <surname>Mazioli da Silva</surname><email>gleydson@guiafoca.org
<releaseinfo>Versão - VERSAO; - - DATADOC;
<copyright><year>1999-- ULTIMOANO; -</year><holder>Gleydson Mazioli da Silva

<pubdate>- DATADOC;

<abstract>

Este guia tem por objetivo ser uma referência ao aprendizado do usuário e um
manual de consulta, operação e configuração de sistemas Linux (e outros tipos
de *ix).  A última versão oficial deste guia pode ser encontrada na <ulink
 [guiafoca](http://www.guiafoca.org)  Página Oficial do Foca Linux.  Novas
versões são lançadas com uma frequência mensal e você pode receber avisos de
novos lançamentos deste guia preenchendo um formulário na página Web ou
assinando o twitter <ulink
[@guiafoca](http://twitter.com/guiafoca .

- introducao;
- basico;
- hardware; 
- migrando;
- discos;
- bootloaders;
- run;
- comandos-diretorio;
- comandos-arquivo; 
- comandos-diversos; 
- comandos-rede; 
- comandos-contas; 
- permissoes; 
- redir; 
- rede;
 http://www.w3.org/2001/XInclude"  href="Avancado/conf-rede/CFGRede-INDEX.md"
- kernel;
- log;
- compactadores;
- debian;
- dpkg;
- personalizacao;
- impressao;
- configurando;
- tasks;
- compilacao;
- manutencao;
- etc;
- internet;
- x11;

<!-- Inicio de capitulos apenas do Avancado -->
 http://www.w3.org/2001/XInclude"  href="Avancado/iptables-firewall/iptables-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/gerenc-contas/contas-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/apache/apache-INDEX.md"
<!-- 
  - s-bind1; 
  - s-dhcp1; 
 -->
 http://www.w3.org/2001/XInclude"  href="Avancado/ident/ident-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/telnet/telnet-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/ssh/ssh-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/pop3/pop3-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/cvs/cvs-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/samba/samba-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/restr-seguranca/restricoes-INDEX.md"
 http://www.w3.org/2001/XInclude"  href="Avancado/criptografia/cripto-INDEX.md" 
 <!-- Fim de capitulos apenas do Avancado -->

- aplicativos;
- ajuda;
- apendice;


