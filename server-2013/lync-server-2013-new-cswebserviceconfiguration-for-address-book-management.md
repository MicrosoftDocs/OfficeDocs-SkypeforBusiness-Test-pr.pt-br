---
title: New-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
TOCTitle: New-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços
ms:assetid: 49e4ecc5-aa3e-4dd4-a32c-b0dea3758fab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429703(v=OCS.15)
ms:contentKeyID: 49306614
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWebServiceConfiguration para Gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros dos seguintes grupos estão autorizados a executar o cmdlet New-CsWebServiceConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsWebServiceConfiguration"}

O cmdlet New-CsWebServiceConfiguration define uma nova configuração para Serviços Web em sua organização. O escopo da configuração dos Serviços Web só pode estar no nível do site ou de serviço. Ele não pode criar uma nova configuração de Serviços Web no nível global. Especificamente de interesse para o Catálogo de Endereços é o atributo EnableGroupExansion. Se definidos como True, os Serviços Web podem responder às solicitações para expansão de grupo.

Por exemplo:

    New-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $False -UseCertificateAuth $True

Para obter uma descrição detalhada do comando completo, consulte o seguinte na referência principal Lync Server Windows PowerShell RTCCmdlets.

## Consulte Também

#### Outros Recursos

[New-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsWebServiceConfiguration)

