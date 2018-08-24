---
title: Habilitar integração do Exchange 2013 Outlook Web App com IM
TOCTitle: Habilitar integração do Exchange 2013 Outlook Web App com IM
ms:assetid: 44d08cf0-b17d-46e1-a4f0-fcc2fe96a958
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204857(v=OCS.15)
ms:contentKeyID: 49306549
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar integração do Exchange 2013 Outlook Web App com IM

 

_**Tópico modificado em:** 2012-10-19_

Para ativar o Exchange 2013 do Outlook Web Access (OWA) e a integração de mensagem instantânea (IM) com Lync Server 2013, você deve adicionar o servidor Exchange 2013 Servidor de Acesso para Cliente (CAS) para a topologia Lync Server 2013 como servidor de aplicativo confiável.

## Para criar um pool de aplicativo confiável

1.  Inicie o Shell de Gerenciamento do Lync Server 2013.

2.  Execute o seguinte cmdlet:
    
        Get-CsSite
    
    Isso retorna o siteID para o siteName o qual você está criando o pool. Para detalhes, consulte [Get-CsSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsSite) na documentação Shell de Gerenciamento do Lync Server 2013.

3.  Execute o seguinte cmdlet:
    
        New-CsTrustedApplicationPool -Identity <E14 CAS FQDN> -ThrottleAsServer $true -TreatAsAuthenticated $true -ComputerFQDN <E14 CAS FQDN> -Site <Site> -Registrar <Pool FQDN in the site> -RequiresReplication $false
    
    Para obter detalhes, consulte [New-CsTrustedApplicationPool](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTrustedApplicationPool) na documentação do Shell de Gerenciamento do Lync Server 2013.
    
    O Exchange Server FQDN deve ser configurado como o certificado Exchange OWA do Nome da Entidade (SN) ou Nome Alternativo de Entidade (SAN).
    
    No Exchange OWA, verifique se o pool do FQDN também é confiável.
    
    > [!IMPORTANT]  
    > Se o seu servidor CAS <em>não</em> estiver alocado no mesmo servidor executando o Exchange 2013 Unified Messaging (UM), pule as etapas restantes neste procedimento e efetue o procedimento “Criar um aplicativo confiável para o servidor CAS Exchange 2013” mais adiante neste tópico. Se o servidor CAS estiver alocado no mesmo servidor que está executando o Exchange 2013 Unified Messaging (UM), complete as etapas deste procedimento e não efetue o procedimento “Criar um aplicativo confiável para o servidor CAS Exchange 2013” mais adiante neste tópico.

4.  Execute **Enable-CsTopology**.

5.  Abra o Construtor de Topologia e baixe a topologia existente.

6.  No painel à esquerda, expanda a árvore até chegar em **Servidores de aplicativos confiáveis**.

7.  Expanda o nó **Servidor de aplicativos confiáveis**.

8.  Você deverá ver agora o servidor CAS Exchange 2013 listado como um servidor de aplicativos confiável.

## Para criar um aplicativo confiável para o servidor CAS Exchange 2013

1.  Inicie o Shell de Gerenciamento do Lync Server 2013.

2.  Se o seu servidor CAS *não* estiver alocado no mesmo servidor executando Exchange 2013 Unified Messaging (UM), execute o cmdlet a seguir:
    
        New-CsTrustedApplication -ApplicationId <AppID String> -TrustedApplicationPoolFqdn <E14 CAS FQDN> -Port <available port number>
    
    Para detalhes, consulte o tópico [New-CsTrustedApplication](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTrustedApplication) na documentação Shell de Gerenciamento do Lync Server 2013.

3.  Execute **Enable-CsTopology**.

4.  Do Construtor de Topologia, no painel à esquerda, expanda a árvore até chegar em **Servidores de aplicativos confiáveis**.

5.  Expanda o nó **Servidor de aplicativos confiáveis**.

6.  Você deverá ver agora o servidor CAS Exchange 2013 listado como um servidor de aplicativos confiável.

