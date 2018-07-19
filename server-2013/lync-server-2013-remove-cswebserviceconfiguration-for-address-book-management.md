---
title: Remove-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
TOCTitle: Remove-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
ms:assetid: 91947cad-5cdd-41b9-83e1-650703c55879
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429713(v=OCS.15)
ms:contentKeyID: 49307456
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Remove-CsWebServiceConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsWebServiceConfiguration"}

O cmdlet Remove-CsWebServiceConfiguration permite que um administrador remova uma configuração dos Serviços Web previamente criada. O cmdlet não pode remover a configuração dos Serviços Web Globais.

Por exemplo:

    Remove-CsWebServiceConfiguration -Identity site:Redmond

Para uma descrição detalhada do comando completo, consulte o seguinte na principal referência de RTCCmdlets do Windows PowerShell do Lync Server.

## Consulte Também

#### Outros Recursos

[Remove-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsWebServiceConfiguration)

