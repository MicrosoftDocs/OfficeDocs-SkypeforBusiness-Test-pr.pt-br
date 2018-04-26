---
title: Retornar informações sobre os provedores de audioconferência atribuídos a um usuário
TOCTitle: Retornar informações sobre os provedores de audioconferência atribuídos a um usuário
ms:assetid: 7fae822f-9f6c-4381-95c5-879661027925
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362814(v=OCS.15)
ms:contentKeyID: 56270437
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retornar informações sobre os provedores de audioconferência atribuídos a um usuário

 

_**Tópico modificado em:** 2015-06-22_

Para retornar informações sobre os provedores de audioconferência que foram atribuídos a um usuário, use o cmdlet [Get-CsUserAcp](get-csuseracp.md) e a seguinte sintaxe:

    Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

