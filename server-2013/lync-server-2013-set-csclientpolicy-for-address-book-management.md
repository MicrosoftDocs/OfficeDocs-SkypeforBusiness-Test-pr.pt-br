---
title: Set-CsClientPolicy para Gerenciamento do catálogo de endereços
TOCTitle: Set-CsClientPolicy para Gerenciamento do catálogo de endereços
ms:assetid: e7788bea-606f-481a-a3a4-1855ac028493
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429723(v=OCS.15)
ms:contentKeyID: 49308440
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientPolicy para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Set-CsClientPolicy localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClientPolicy"}

Parecido com o New-CsClientPolicy, o cmdlet Set-CsClientPolicy permite que você modifique as configurações cliente que já estão aplicadas.

Por exemplo:

    Set-CsClientPolicy -Identity RedmondClientPolicy -WebServicePollInterval "00:15:00" -AddressBookAvailability "WebSearchAndFileDownload"

Para obter uma descrição detalhada do comando completo, consulte o seguinte na principal referência do Lync Server Windows PowerShell RTCCmdlets.

## Consulte Também

#### Outros Recursos

[Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy)

