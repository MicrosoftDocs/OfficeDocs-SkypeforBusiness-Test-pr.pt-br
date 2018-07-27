---
title: 'Lync Server 2013: Configurando seu ambiente do Lync Server 2013 para Porta da Web Administrativo do Sistema de Sala do Lync'
TOCTitle: Configurando seu ambiente do Lync Server 2013 para Porta da Web Administrativo do Sistema de Sala do Lync
ms:assetid: 1bf3cc55-cfa8-46ee-a8bc-6dab3bff76b2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn436325(v=OCS.15)
ms:contentKeyID: 59602787
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando seu ambiente do Lync Server 2013 para Porta da Web Administrativo do Sistema de Sala do Lync

 

_**Tópico modificado em:** 2016-12-08_

Para usar o Portal da Web Administrativo do Lync Room System (LRS), será necessário instalar ou configurar pré-requisitos a seguir.

> [!IMPORTANT]  
> Se o servidor estiver configurado com a autenticação Kerberos e NTLM, e o LRS estiver em execução em um computador que não esteja ingressado no domínio, haverá falha na autenticação Kerberos, e o usuário não verá o status do LRS no portal administrativo. Para resolver este problema, configure o servidor com a autenticação NTLM ou a autenticação NTLM e TLS-DSK (sem Kerberos), ou ingresse o computador LRS no domínio.

1.  Instale as Atualizações Cumulativas do Lync Server 2013: julho de 2013 na topologia do Lync Server.
    
    Para obter a atualização ou para ver o que foi incluída nela, consulte [Atualizações para o Lync Server 2013](http://support.microsoft.com/kb/2809243).

2.  Crie um usuário do Active Directory habilitado para SIP.
    
    O Portal da Web Administrativo do LRS usa estas credenciais para consultar essas credenciais para consultar informações do Lync Server. O nome de usuário recomendado é LRSApp.

3.  Crie um grupo de segurança do Active Directory com o nome LRSSupportAdminGroup.
    
    Crie o grupo com Escopo do Grupo como Global e Tipo de Grupo como Segurança. Os usuários habilitados para SIP que forem adicionados a este grupo serão autorizados a ver a lista de salas e a executar determinados comandos, como coletar logs.

4.  Crie um grupo de segurança do Active Directory com o nome LRSFullAccessAdminGroup.
    
    Crie o grupo com Escopo do Grupo como Global e Tipo de Grupo como Segurança. Os usuários habilitados que forem adicionados a este grupo serão autorizados a usar toda a funcionalidade de administrador do portal.
    
     
    
    ![Lista de grupos administrativos com a função de grupo de segurança](images/Dn436325.5d432819-a2e2-452c-bc2a-5d4ee79d8c33(OCS.15).png "Lista de grupos administrativos com a função de grupo de segurança")  
    
     

5.  Adicione LRSFullAccessAdminGroup como membro de LRSSupportAdminGroup.
    
    ![Página Membros de Propriedades LRSSupportAdminGroup](images/Dn436325.91a4a28a-cacf-4ef6-aac1-915ec41c9648(OCS.15).png "Página Membros de Propriedades LRSSupportAdminGroup")  
    
     

6.  Crie um usuário do Active Directory habilitado para SIP com o nome LRSSupport. Adicione-o a LRSSupportAdminGroup.
    
    ![Página Membros de Propriedades LRSSupportAdminGroup](images/Dn436325.7638055d-22ac-4909-914d-1966f5623909(OCS.15).png "Página Membros de Propriedades LRSSupportAdminGroup")  
    
     

7.  Instale o ASP.NET MVC 4 para Visual Studio 2010 SP1 e Visual Web Developer 2010 SP1, disponível no Centro de Download da Microsoft em [http://www.microsoft.com/pt-br/download/details.aspx?id=30683](http://go.microsoft.com/fwlink/p/?linkid=323967).

