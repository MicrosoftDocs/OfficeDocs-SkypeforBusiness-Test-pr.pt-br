---
title: Impedir que usuários anônimos sejam admitidos automaticamente em uma reunião
TOCTitle: Impedir que usuários anônimos sejam admitidos automaticamente em uma reunião
ms:assetid: 23f120d2-4c39-4509-aa1f-4d186a525075
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362775(v=OCS.15)
ms:contentKeyID: 56270377
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Impedir que usuários anônimos sejam admitidos automaticamente em uma reunião

 

_**Tópico modificado em:** 2015-06-22_

Para impedir que usuários anônimos sejam automaticamente admitidos em uma reunião online, use o cmdlet [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) e defina a propriedade AdmitAnonymousUsersByDefault como Falsa ($False):

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

Para habilitar a admissão automática, defina a propriedade AdmitAnonymousUsersByDefault novamente como Verdadeira ($True):

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

