---
title: Atribuir um Provedor de Audioconferência a um Usuário
TOCTitle: Atribuir um Provedor de Audioconferência a um Usuário
ms:assetid: 60db6896-9c5c-4d64-ab7e-10d91748587c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362791(v=OCS.15)
ms:contentKeyID: 56270399
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir um Provedor de Audioconferência a um Usuário

 

_**Tópico modificado em:** 2015-06-22_

O [Set-CsUserAcp](set-csuseracp.md) cmdlet fornece um caminho para você atribuir um provedor de audioconferência a um usuário:

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "12065551219" -TollFreeNumbers "18005550712" -ParticipantPasscode "p@ssw0rd" -Domain "sip.contoso.com" -Name "Contoso ACP"

Essa atribuição será inútil, a meno que você já tenha contratado um provedor específico.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

