---
title: 'Lync Server 2013: Excluindo uma mensagem ou limpando mensagens obsoletas'
TOCTitle: Excluindo uma mensagem ou limpando mensagens obsoletas
ms:assetid: 3f0c612d-6dfd-41a4-a5fe-5ff3448eb0ce
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215874(v=OCS.15)
ms:contentKeyID: 49306485
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo uma mensagem ou limpando mensagens obsoletas no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Um administrador Chat Persistente pode excluir uma mensagem de uma sala Chat Persistente (e, se quiser, poderá substituí-la por outra mensagem). Os administradores também podem limpar mensagens obsoletas como parte da manutenção contínua, para minimizar o crescimento do banco de dados. Por exemplo, esse comando Windows PowerShell remove todas as mensagens da sala de chat ITChatRoom que foram postadas pelo usuário kenmyer@litwareinc.com:

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com"

E este exemplo substitui as mensagens removidas pela observação de que a mensagem não está mais disponível:

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com" -ReplaceMessage "This message is no longer available."

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Remove-CsPersistentChatMessage](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsPersistentChatMessage).

