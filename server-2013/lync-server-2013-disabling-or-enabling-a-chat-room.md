---
title: 'Lync Server 2013: Habilitar ou desabilitar uma sala de chat'
TOCTitle: Habilitar ou desabilitar uma sala de chat
ms:assetid: db0908fc-aae3-46e8-bc0b-245e9adfa1e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215883(v=OCS.15)
ms:contentKeyID: 49308303
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar uma sala de chat no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Se o tópico de uma sala do Chat Persistente não for mais relevante, você poderá tornar a sala de chat indisponível para os usuários desabilitando-a. Quando uma sala de chat está desabilitada, todos os membros são desconectados imediatamente da sala. Após uma sala de chat é desabilitada, os usuários não podem participar novamente ou encontrar nas pesquisas de sala de chat.

Uma sala de chat desabilitada pode ser habilitada posteriormente por um administrador do Chat Persistente. Se uma sala de chat é desabilitada, sua lista de associação e outras configurações são preservadas. Se você habilitar a sala novamente, não é necessário recriar manualmente as configurações.

Se o histórico da sala de chat persistir (persistência da histórico da sala de chat é a melhor configuração em uma categoria aplicável a todas as salas dentro da categoria; o padrão é que é persistente, mas pode ser desativado configurando **Habilitar histórico de chat** da categoria para falso), o conteúdo é preservado quando a sala de chat é desabilitada. No entanto, este conteúdo não será exibido nas pesquisas durante o momento que a sala de chat permanece em um estado desabilitado. Se você posteriormente habilitar a sala de chat, os usuários podem pesquisar por mensagens publicadas antes da sala de chat ser desabilitada.

Para obter detalhes sobre como habilitar e desabilitar salas de chat usando o Interface da linha de comando do Windows PowerShell, consulte "Gerenciamento da sala" em [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md). Para desabilitar uma sala de chat, use um comando semelhante a este:

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True

Para habilitar uma sala de chat, defina a propriedade Disabled como False:

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $False

Observe que as salas de chat não podem ser habilitadas ou desabilitadas com o uso do Painel de Controle do Lync Server.

Para obter detalhes sobre como configurar salas de chat, consulte [Configurar salas no Lync Server 2013](lync-server-2013-configure-rooms.md), na documentação de Implantação.

