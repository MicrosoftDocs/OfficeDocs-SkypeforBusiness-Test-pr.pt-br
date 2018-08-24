---
title: Test-CsAddressBookWebQuery para Gerenciamento do catálogo de endereços
TOCTitle: Test-CsAddressBookWebQuery para Gerenciamento do catálogo de endereços
ms:assetid: 977a9c1f-5f4e-4539-9a26-8748b61a57d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429716(v=OCS.15)
ms:contentKeyID: 49307535
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAddressBookWebQuery para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Test-CsAddressBookWebQuery localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAddressBookService"}

Similar à transação sintética Test-CsAddressBookService, Test-CsAddressBookWebQuery executa uma consulta no Address Book Web Query para garantir que esteja funcionando corretamente. O cmdlet se conectará à autenticação Web Ticket e apresentará as credenciais especificadas em –UserCredential. Se autenticado, o cmdlet então apresenta a informação –TargetSipAddress. O cmdlet deve reportar sucesso se conseguir recuperar as informações sobre o contato.

Por exemplo:

    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.contoso.com -UserCredential contoso\bob -UserSipAddress "sip:bob@contoso.com" -TargetSipAddress "sip:bob@contoso.com"

Para uma descrição detalhada do comando completo, consulte o seguinte na principal referência de RTCCmdlets do Windows PowerShell do Lync Server.

## Consulte Também

#### Outros Recursos

[Test-CsAddressBookWebQuery](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsAddressBookWebQuery)

