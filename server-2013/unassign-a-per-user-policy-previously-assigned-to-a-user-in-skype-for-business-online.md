---
title: Remover uma Política de Usuário Previamente Atribuída a Usuário
TOCTitle: Remover uma Política de Usuário Previamente Atribuída a Usuário
ms:assetid: bdba1d22-28e4-4203-a109-a3fb408783d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362840(v=OCS.15)
ms:contentKeyID: 56270467
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover uma Política de Usuário Previamente Atribuída a Usuário

 

_**Tópico modificado em:** 2015-06-22_

Se quiser remover uma política de usuário previamente atribuída a usuário execute novamente o cmdlet adequado **Grant-Cs** (por exemplo, cmdlet [Grant-CsVoicePolicy](grant-csvoicepolicy.md) para remover uma política de voz), e defina o parâmetro PolicyName como um valor nulo ($Null):

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

Para remover políticas de voz para todos os usuários, use este comando:

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName $Null

Quando uma politica deixa de ser atribuída a um usuário, este passa a ser gerenciado pela política global.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

