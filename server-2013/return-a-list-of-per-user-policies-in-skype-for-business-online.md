---
title: Retorne uma lista de políticas por usuário
TOCTitle: Retorne uma lista de políticas por usuário
ms:assetid: e95a2755-3501-40cc-a704-5ecd01839d76
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362856(v=OCS.15)
ms:contentKeyID: 56270484
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retorne uma lista de políticas por usuário

 

_**Tópico modificado em:** 2015-06-22_

Para retornar uma lista das políticas disponíveis por usuário, primeiro selecione o devido cmdlet **Get-Cs** (por exemplo, o cmdlet [Get-CsVoicePolicy](get-csvoicepolicy.md), se você quiser retornar as políticas de voz por usuário). então, use a seguinte sintaxe para retornar a identidade de cada política por usuário:

    Get-CsVoicePolicy -Filter "tag:*" | Select-Object Identity

Note que, por causa dos diferentes contratos de licença e das diferentes restrições de país/região, é possível que certas políticas de conferência, políticas de acesso externo ou políticas de mobilidade não possam ser atribuídas a determinado usuário. Para verificar as políticas por usuário que podem realmente ser atribuídas a certo usuário (por exemplo, kenmyer@litwareinc.com), use um dos seguintes comandos (e o parâmetro ApplicableTo), como apropriado:

    Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"

A sintaxe anterior retorna apenas as políticas por usuário que podem realmente ser atribuídas a Ken Myer.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

