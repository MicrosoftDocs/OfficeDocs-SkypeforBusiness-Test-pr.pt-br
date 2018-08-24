---
title: Remove-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços
TOCTitle: Remove-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços
ms:assetid: 5d173ebe-ec4d-4640-8432-a25071ea9cc5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429705(v=OCS.15)
ms:contentKeyID: 49306845
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Remove-CsAddressBookConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAddressBookConfiguration"}

Como o nome implica, Remove-CsAddressBookConfiguration removerá a configuração com base na Identidade do Site definida.

Por exemplo:

    Remove-CsAddressBookConfiguration -Identity site:Redmond

Para obter uma descrição detalhada do comando completo, consulte o seguinte na referência principal a RTCCmdlets do Lync Server Windows PowerShell.

## Consulte Também

#### Outros Recursos

[Remove-CsAddressBookConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAddressBookConfiguration)

