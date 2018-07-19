---
title: New-CsClientPolicy para Gerenciamento do catálogo de endereços
TOCTitle: New-CsClientPolicy para Gerenciamento do catálogo de endereços
ms:assetid: ef4415fc-82c4-4dc8-97d1-37a084553343
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429726(v=OCS.15)
ms:contentKeyID: 49308547
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientPolicy para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet New-CsClientPolicy: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsClientPolicy"}

O cmdlet New-CsClientPolicy define muitas configurações para provisionamento de clientes para recursos disponíveis no Lync Server 2013. Para o Serviço Catálogo de Endereços, o parâmetro AddressBookAvailability é de interesse. Esse parâmetro, que afeta diretamente as opções disponíveis aos clientes, tem três opções possíveis:

  - WebSearchAndFileDownload

  - WebSearchOnly

  - FileDownloadOnly

Quando definido, ele determina como o Catálogo de Endereços será acessado pelos clientes. Se você definir esse parâmetro, deverá definir uma das opções. Se você não modificar essa configuração, o padrão WebSearchAndFileDownload permanecerá em vigor.

Por exemplo:

    New-CsClientPolicy -Identity RedmondClientPolicy -DisableCalendarPresence $True -DisablePhonePresence $True -DisplayPhoto "PhotosFromADOnly" -AddressBookAvailability "WebSearchOnly"

## Consulte Também

#### Outros Recursos

[New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy)

