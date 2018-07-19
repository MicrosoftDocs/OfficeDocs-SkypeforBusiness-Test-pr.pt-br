---
title: Set-CsWebServiceConfiguration para Gerenciamento do catálogo de endereços
TOCTitle: Set-CsWebServiceConfiguration para Gerenciamento do catálogo de endereços
ms:assetid: 79d0edf5-23f3-4845-a7b7-e11b5a928bab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429709(v=OCS.15)
ms:contentKeyID: 49307196
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsWebServiceConfiguration para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Set-CsWebServiceConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsWebServiceConfiguration"}

O cmdlet Set-CsWebServiceConfiguration permite ao administrador redefinir um atributo existente na configuração dos serviços da Web.

Por exemplo:

    Set-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $True

Para obter uma descrição detalhada do comando completo, consulte o seguinte na referência principal RTCCmdlets do PowerShell do Lync Server Windows.

## Consulte Também

#### Outros Recursos

[Set-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsWebServiceConfiguration)

