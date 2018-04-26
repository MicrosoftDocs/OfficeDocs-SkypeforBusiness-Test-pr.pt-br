---
title: Atribuir uma política por usuário a um usuário
TOCTitle: Atribuir uma política por usuário a um usuário
ms:assetid: 37e07da7-6391-4d6d-a428-c70272897039
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362779(v=OCS.15)
ms:contentKeyID: 56270382
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política por usuário a um usuário

 

_**Tópico modificado em:** 2015-06-22_

Para atribuir uma política por usuário a um usuário, primeiro você deverá selecionar o cmdlet **Grant-Cs** apropriado (por exemplo, [Grant-CsVoicePolicy](grant-csvoicepolicy.md), se quiser atribuir uma política de voz por usuário). Execute o cmdlet, especificando a identidade do usuário que receberá a política e o nome da política sendo atribuída:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

Se quiser atribuir a mesma política a todos os seus usuários, use esta sintaxe:

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName "RedmondVoicePolicy"

Observe que, por causa de contratos de licenciamentos diferentes e de restrições de país/região diferentes, é possível que determinadas políticas de conferência, políticas de acesso externas ou políticas de mobilidade não possam ser atribuídas a um usuário em particular. Para verificar as políticas por usuário que realmente podem ser atribuídas a um determinado usuário (por exemplo, pauloneves@litwareinc.com) use um dos comandos a seguir (e o parâmetro ApplicableTo), como apropriado:

    Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"

A sintaxe precedida retorna somente as políticas por usuário que possam realmente ser atribuídas a Paulo Neves.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

