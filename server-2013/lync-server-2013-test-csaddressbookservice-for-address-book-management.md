---
title: Test-CsAddressBookService para Gerenciamento do catálogo de endereços
TOCTitle: Test-CsAddressBookService para Gerenciamento do catálogo de endereços
ms:assetid: b88cea74-41fd-4c0e-9284-7135bff27a27
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429720(v=OCS.15)
ms:contentKeyID: 49307908
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAddressBookService para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet Test-CsAddressBookService localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAddressBookService"}

O Lync Server 2013 contém diversos cmdlets que iniciam comandos sintéticos para confirmar que uma função ou recurso específico está funcionando apropriadamente. Test-CsAddressBookService confirma que um usuário definido pode conectar e solicitar os arquivos locais a partir do serviço Web do catálogo de endereços.

Por exemplo:

    Test-CsAddressBookService -TargetFqdn atl-cs-001.contoso.com -UserCredential contoso\bob -UserSipAddress "sip:bob@contoso.com"

## Consulte Também

#### Outros Recursos

[Test-CsAddressBookService](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsAddressBookService)

