---
title: 'Lync Server 2013: Anexo A: Usando cmdlets para implantar uma Aparelho de Filial Persistente'
TOCTitle: 'Anexo A: Usando cmdlets para implantar uma Aparelho de Filial Persistente'
ms:assetid: 796a26cf-7ec9-453b-8757-6153a6dd86c5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398598(v=OCS.15)
ms:contentKeyID: 49307186
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Anexo A: Usando cmdlets para implantar uma Aparelho de Filial Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-07_

Este tópico descreve como implantar um Aparelho de Filial Persistente usando o Shell de Gerenciamento do Lync Server. Execute este procedimento no local central.

## Para implantar um Aparelho de Filial Persistente remotamente

1.  Siga o procedimento em [Adicionar sites de filial a sua topologia no Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md) para adicionar um novo site de filial.

2.  Ingresse o site da filial no domínio.

3.  Adicione o grupo RTCUniversalSBATechnicians ao grupo de Administradores local.

4.  Reinicie o servidor e faça o logon nele como um membro do grupo RTCUniversalSBATechnicians.

5.  No Shell de Gerenciamento do Lync Server, digite os seguintes comandos, substituindo os espaços reservados pelas informações corretas de sua organização:
    
        Export-CsConfiguration -FileName C:\CSConfig.zip
        Import-CsConfiguration -LocalStore -FileName C:\CSConfig.zip -Verbose
        Enable-CSReplica -Verbose
        Enable-CsComputer -Verbose
        Request-CsCertificate -New -Type default -CA <YourCA> -Verbose
        Set-CsCertificate -Type Default -Thumbprint <YourCertThumbprint>
        Start-cswindowsservice -verbose

