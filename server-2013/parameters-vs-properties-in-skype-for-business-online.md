---
title: Parâmetros vs. Propriedades
TOCTitle: Parâmetros vs. Propriedades
ms:assetid: 65348f95-f4d4-40cd-8869-f9d72643792d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362796(v=OCS.15)
ms:contentKeyID: 56270400
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Parâmetros vs. Propriedades

 

_**Tópico modificado em:** 2015-06-22_

Quando revisar os tópicos de ajuda para os cmdlets Skype for Business Online, você verá, às vezes, os parâmetros de *termos* e *propriedade* intercambiável usada. Não se confunda com esta terminologia: embora as duas sejam tecnicamente diferentes, em Skype for Business Online, essencialemnte, os termos se referem à mesma coisa.

Tecnicamente falando, os parâmetros são usados quando você executa um cmdlet. Por exemplo, no seguinte comando Windows PowerShell, EnableMicrosoftPushNotificationService e EnableApplePushNotificationService são parâmetros de cmdlet [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md):

    Set-CsPushNotificationConfiguration -EnableMicrosoftPushNotificationService -EnableApplePushNotificationService $True

Uma propriedade é um atributo de um objeto Skype for Business Online (por exemplo, uma coleção de configurações de notificações por push). Vamos dizer que você executa este comando:

    Set-CsPushNotificationConfiguration

Quando você faz isso, você volta para a coleção de propriedades e seus valores associados, que incluirão os seguintes ítens:

    EnableMicrosoftPushNotificationService : True
    EnableApplePushNotificationService     : True

Como você pode ver, as propriedades e parâmetros compartilham o mesmo nome: você usa o parâmetro EnableMicrosoftPushNotificationService para configurar o valor da propriedade EnableMicrosoftPushNotificationService.

## Consulte Também

#### Conceitos

[Uma introdução ao Windows PowerShell e ao Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

