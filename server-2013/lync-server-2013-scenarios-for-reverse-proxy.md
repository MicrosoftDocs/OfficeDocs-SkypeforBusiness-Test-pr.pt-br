---
title: 'Lync Server 2013: Cenários de proxy reverso'
TOCTitle: Cenários de proxy reverso
ms:assetid: 13108f59-a660-4ff1-8404-079d1cb646f2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204691(v=OCS.15)
ms:contentKeyID: 49305948
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cenários de proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2013-01-21_

Proxies reversos são requeridos no Lync Server 2013 para fornecer acesso a serviços e recursos como reuniões e URLs Simples de discagem, catálogo de endereços, conteúdo de reunião, expansão da lista de distribuição, serviços de mobilidade e outros. O cenário de proxy reverso típico no Lync Server 2013 é permitir que clientes (por exemplo, o cliente de área de trabalho ou Lync Web App) acesse o Serviço Web externo Diretor ou Servidor Front-End.

**Proxy reverso e serviços da Web externos**

![Proxy Reverso e Serviços Web Externos](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "Proxy Reverso e Serviços Web Externos")

Durante a fase de planejamento, você define os requisitos para o proxy reverso em uma implantação Lync Server 2013. O proxy reverso permite o acesso a recursos para os seguintes clientes externos:

  - Microsoft Lync 2013 cliente de área de trabalho

  - Microsoft Lync Web App

  - Microsoft Lync Mobile

  - Aplicativo Lync Windows Store

Ao planejar a implantação do Lync Server 2013, você mapeia os requisitos reais para Lync Server 2013 para recursos de proxy reverso.

1.  Os clientes externos se conectarão com o proxy reverso na porta TCP 443 e usará o SSL ou o TLS. Clientes do Microsoft Lync Mobile podem se conectar na porta TCP 80, mas apenas quando efetuar a conexão inicial nos serviços de descoberta do Lync e o administrador tiver configurado registros no nome de domínio (DNS) CNAME adequado (ou alias), e aceitar que essa comunicação não será criptografada.

2.  Os serviços Web externos Lync Server 2013 (implantado no Servidor Front-End e/ou Diretor) esperam uma conexão de um proxy reverso na porta TCP 4443, e espera que tal conexão seja SSL/TLS.
    
    > [!IMPORTANT]  
    > As portas de escuta padrão sugeridas para os serviços Web externos são TCP 8080 par tráfego HTTP e TCP 4443 para tráfego HTTPS. O Construtor de Topologias oferece uma oportunidade de substituir os padrões e definir suas próprias portas para os serviços Web externos. É importante observar que o proxy reverso se comunica com os serviços Web externos, e os clientes externos se comunicam com o proxy reverso. O cliente externo se comunica com o proxy reverso na porta TCP 443, mas você pode redefinir qual porta o proxy reverso se comunica com os serviços Web externos ativos. As opções no Construtor de Topologias para substituir as portas de escuta padrão para os serviços Web permitem que você resolva conflitos de porta de escuta que podem surgir na sua infraestrutura.

3.  Os serviços Web externos Lync Server 2013 esperam um Host Header não modificado do cliente para identificar qual serviço e diretório de servidor da Web o cliente está tentando usar. Solicitações devem aparecer como se viessem do proxy reverso.

4.  O uso dos serviços Web externos define os diretórios virtuais de servidor da Web (vDir) que fornecem os serviços oferecidos aos clientes. Os serviços da Web identificáveis externamente são:
    
      - O vDir “Reunião” para reuniões de conferência pela Web
    
      - O vDir “Discando” para acesso telefônico e conferência por telefone
    
      - O vDir “Descoberta automática” para Aplicativo Lync Windows Store, Lync Mobile e o Lync 2013 cliente de área de trabalho. A Descoberta automática no Lync Server 2013 é conhecido pelo nome de DNS “lyncdiscover”
    
      - Os serviços não definidos são acessados pelo cliente externo por chamadas diretas aos serviços Web externos. Por exemplo, a expansão de grupo de distribuição (DLX) e o serviço de catálogo de endereço (ABS) são acessados por chamadas diretas para os serviços Web externos e vDirs associados. O cliente sabe o caminho atual do vDir e constroi um localizador de registro uniforme (URL) com base nessa informação. O cliente poderia acessar o serviço de catálogo de endereços usando uma URL similar a `https://externalweb.contoso.com/abs/handler`
    
      - O Servidor Office Web Apps, quando em conferência, é definido e configurado como parte da topologia Lync Server
        
        > [!NOTE]  
        > O Servidor Office Web Apps é um servidor de função separado e não está configurado como parte dos serviços Web externos. Esse servidor é publicado separadamente para acesso de cliente.

5.  Defina a ponte SSL para cada serviço. A porta externa TCP 443 é mapeada para a porta de serviços Web externos TCP 4443. Para HTTP não criptografado, a porta TCP 80 é mapeada para a porta TCP 8080 dos serviços Web externos

6.  Plano para escutas de proxy reverso para publicar recursos de servidor Web

7.  Solicite e configure o certificado para o proxy reverso com base nos serviços que serão oferecidos. Se configurado com os nomes alternativos de assunto corretos, esse certificado pode ser compartilhado por todas as escutas configuradas no servidor de proxy reverso

Recursos disponíveis para planejar a implantação do seu proxy reverso:

  - [Coleta de dados no Lync Server 2013](lync-server-2013-data-collection.md)

  - [Resumo de certificado - Proxy reverso no Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [Resumo de porta - Proxy reverso no Lync Server 2013](lync-server-2013-port-summary-reverse-proxy.md)

  - [Resumo de DNS - Proxy reverso no Lync Server 2013](lync-server-2013-dns-summary-reverse-proxy.md)

