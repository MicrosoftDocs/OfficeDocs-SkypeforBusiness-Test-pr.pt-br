---
title: Get-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
TOCTitle: Get-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
ms:assetid: 0b223733-5224-47d1-9b47-2109e6f135c9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429692(v=OCS.15)
ms:contentKeyID: 49305846
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros dos seguintes grupos estão autorizados a executar o cmdlet Get-CsWebServiceConfiguration localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsWebServiceConfiguration"}

O Get-CsWebServiceConfiguration retorna as informações das configurações dos Serviços da Web sendo usadas em sua organização. De interesse do Serviço de Catálogo de Endereços está o status da função de Expansão da Lista de Distribuição. Se o atributo do EnableGroupExpansion for Verdadeiro, sua organização atualmente permite a expansão de grupo.

Por exemplo:

    Get-CsWebServiceConfiguration -Identity site:Redmond

Para uma descrição detalhada do comando completo, consulte o seguinte na referência principal do Lync Server Windows PowerShell RTCCmdlets reference.

## Consulte Também

#### Outros Recursos

[Get-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsWebServiceConfiguration)

