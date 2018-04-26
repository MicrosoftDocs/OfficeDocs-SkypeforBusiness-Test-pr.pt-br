---
title: O Número Máximo de Shells Atuais para este Usuário Foi Excedido
TOCTitle: O Número Máximo de Shells Atuais para este Usuário Foi Excedido
ms:assetid: b309efe8-a214-41ea-a345-93e6a36e0cb1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362837(v=OCS.15)
ms:contentKeyID: 56270462
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# O Número Máximo de Shells Atuais para este Usuário Foi Excedido

 

_**Tópico modificado em:** 2015-06-22_

Cada administrador pode efetuar um máximo de três conexões remotas simultaneamente a Skype for Business Online. Se três conexões remotas Windows PowerShell estiverem sendo executadas, qualquer tentativa de fazer uma quarta conexão simultânea falhará, e a seguinte mensagem de erro aparecerá:

    New-PSSession : [admin.vdomain.com] Falha na conexão ao servidor remoto admin.vdomain.com com a seguinte mensagem de erro : O serviço WS-Management não pode processar a solicitação. O número máximo de shells simultâneos para este usuário foi excedido. Feche os shells existentes ou aumente a cota de shells do usuário. Para mais informações, consulte o tópico Ajuda about_Remote_Troubleshooting.

A única forma de resolver esse problema é fechando uma ou mais conexões anteriores. Quando uma sessão Skype for Business Online for encerrada, recomendamos que o cmdlet **Remove-PSSession** seja usado para terminar a sessão. Isso ajudará a evitar esse problema.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

