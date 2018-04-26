---
title: Ativar/Desativar a Notificaão por Push em iPhones e Windows Phones
TOCTitle: Ativar/Desativar a Notificaão por Push em iPhones e Windows Phones
ms:assetid: 64482dcb-6354-4fb5-a2e4-1564b3d0e047
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362792(v=OCS.15)
ms:contentKeyID: 56270411
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ativar/Desativar a Notificaão por Push em iPhones e Windows Phones

 

_**Tópico modificado em:** 2015-06-22_

Para desativar as notificações por push nos iPhones ou Windows Phones, utilize o cmdlet [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) e defina os valores do EnableApplePushNotificationService e das propriedades do EnableMicrosoftPushNotificationService como Falsa ($False):

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False

Observe que iPhones e Windows phones podem ser definidos independentemente. Por exemplo, esse comando desativa as notificações por push em iPhones, mas habilita essas notificações nos Windows Phones:

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $True

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

