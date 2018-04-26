---
title: Ativar/desativar a gravação da conferência
TOCTitle: Ativar/desativar a gravação da conferência
ms:assetid: f6c5afab-081c-495c-97f7-135dcc2f6085
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362857(v=OCS.15)
ms:contentKeyID: 56270491
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ativar/desativar a gravação da conferência

 

_**Tópico modificado em:** 2015-06-22_

Se você não quiser que os usuários tenham a capacidade de gravar as conferências on-line, use o cmdlet [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) e defina o valor do parâmetro AllowConferenceRecording para False ($False):

    Set-CsMeetingConfiguration -AllowConferenceRecording $False

Para restaurar a capacidade de gravar conferências on-line, defina o valor do parâmetro AllowConferenceRecording para True ($True):

    Set-CsMeetingConfiguration -AllowConferenceRecording $True

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

