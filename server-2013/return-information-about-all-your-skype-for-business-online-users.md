---
title: Retornar informações sobre todos os seus usuários do Lync Online
TOCTitle: Retornar informações sobre todos os seus usuários do Lync Online
ms:assetid: 0b59fadf-67e6-48ea-86f1-2efef500ebdf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362769(v=OCS.15)
ms:contentKeyID: 56270369
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retornar informações sobre todos os seus usuários do Lync Online

 

_**Tópico modificado em:** 2015-06-22_

Para retornar informações sobre todos os usuários que foram habilitados para o Skype for Business Online, chame o cmdlet [Get-CsOnlineUser](get-csonlineuser.md) sem qualquer parâmetro adicional:

    Get-CsOnlineUser

Para retornar informações para um único usuário selecionado aleatoriamente (por exemplo, para usar esta conta para fins de teste), chame o cmdlet **Get-CsOnlineUser** e defina o parâmetro ResultSize como 1:

    Get-CsOnlineUser -ResultSize 1

Isso faz com que o cmdlet **Get-CsOnlineUser** retorne informações para somente um usuário, independentemente do número de usuários em sua organização. Para retornar informações para cinco usuários, defina o valor do parâmetro ResultSize como 5:

    Get-CsOnlineUser -ResultSize 5

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

