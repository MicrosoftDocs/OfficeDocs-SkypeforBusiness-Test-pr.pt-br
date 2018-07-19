---
title: Get-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços
TOCTitle: Get-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços
ms:assetid: bd62f916-caf3-4e10-ada4-631bbb331ef1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429721(v=OCS.15)
ms:contentKeyID: 49307946
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAddressBookConfiguration para Gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Get-CsAddressBookConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAddressBookConfiguration"}

O cmdlet Get-CsAddressBookConfiguration retorna informações sobre uma configuração que já existe.

Por exemplo:

    Get-CsAddressBookConfiguration -Identity site:Redmond

Combinando a funcionalidade do CsAddressBookConfiguration Get e do Set CsAddressBookConfiguration, permite ao administrador definir quais configurações serão modificadas e aplicar as modificações. Por exemplo, isto combinado:

    Get-CsAddressBookConfiguration -Filter site:* | Set-CsAddressBookConfiguration -RunTimeOfDay 23:00

Retorna todas as configurações em todos os sites e aplica RunTimeOfDay de 23h às configurações.

Para obter uma descrição detalhada do comando completo, consulte o seguinte na principal referência do Lync Server Windows PowerShell RTCCmdlets.

## Consulte Também

#### Outros Recursos

[Get-CsAddressBookConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAddressBookConfiguration)

