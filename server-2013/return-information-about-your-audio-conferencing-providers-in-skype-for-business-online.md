---
title: Retorne informações sobre seus provedores de audioconferência
TOCTitle: Retorne informações sobre seus provedores de audioconferência
ms:assetid: df9c8fc0-8bb6-4416-a5cc-aa9b1601a688
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362848(v=OCS.15)
ms:contentKeyID: 56270479
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retorne informações sobre seus provedores de audioconferência

 

_**Tópico modificado em:** 2015-06-22_

Para retornar informações sobre os provedores de audioconferência atribuídos a um usuário, use o cmdlet [Get-CsUserAcp](get-csuseracp.md) e a sintaxe a seguir:

    Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

