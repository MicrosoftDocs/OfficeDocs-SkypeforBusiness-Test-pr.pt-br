---
title: Set-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços
TOCTitle: Set-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços
ms:assetid: 3a64ceb1-9f79-4f3b-bf33-eaf346dbd60d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429700(v=OCS.15)
ms:contentKeyID: 49306425
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Set-CsAddressBookConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsAddressBookConfiguration"}

Set-CsAddressBookConfiguration é semelhante ao cmdlet New-CsAddressBookConfiguration, com a exceção de que é usado para modificar uma configuração existente.

Por exemplo:

    Set-CsAddressBookConfiguration -identity site:Redmond -RunTimeOfDay 23:00

Para obter uma descrição detalhada do comando completo, consulte o seguinte na principal referência de RTCCmdlets do Lync Server Windows PowerShell.

## Consulte Também

#### Outros Recursos

[Set-CsAddressBookConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsAddressBookConfiguration)

