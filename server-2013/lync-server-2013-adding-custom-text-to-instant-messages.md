---
title: 'Lync Server 2013: Adicionando texto personalizado a mensagens instantâneas'
TOCTitle: Adicionando texto personalizado a mensagens instantâneas
ms:assetid: cabcc3ec-9d35-42ac-a403-e21b7d538c2c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398847(v=OCS.15)
ms:contentKeyID: 52057724
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionando texto personalizado a mensagens instantâneas no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-20_

Adicione um aviso ou aviso de isenção de responsabilidade ao início de cada conversa de mensagem instantânea do Lync 2013 usando o cmdlet **New-CSClientPolicy** ou **Set-CSClientPolicy**Shell de Gerenciamento do Lync Server com o parâmetro IMWarning.

O comando no exemplo a seguir adiciona um lembrete de segurança na parte superior da janela Conversa sempre que uma nova conversa de mensagem instantânea é iniciada:

    New-CsClientPolicy -Identity IMSecurityNotice -IMWarning 
    "Remember, security is everyone's responsibility. Keep it confidential."

Use o **Grant-CSClientPolicy** para atribuir essa nova política aos usuários. Para obter detalhes, consulte **New-CSClientPolicy** e **Grant-CSClientPolicy** na documentação do Shell de Gerenciamento do Lync Server.

