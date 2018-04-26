---
title: Returne uma lista de usuários filtrada
TOCTitle: Returne uma lista de usuários filtrada
ms:assetid: f2c4d13b-8601-4192-8b94-e9a57969da11
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362858(v=OCS.15)
ms:contentKeyID: 56270486
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Returne uma lista de usuários filtrada

 

_**Tópico modificado em:** 2015-06-22_

Usando o cmdlet [Get-CsOnlineUser](get-csonlineuser.md) e o parâmetro LdapFilter ou Filter, você pode retornar facilmente informações sobre um conjunto de usuários de destino. Por exemplo, este comando retorna todos os usuários que trabalham no departamento Financeiro:

    Get-CsOnlineUser -LdapFilter "department=Finance"

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

