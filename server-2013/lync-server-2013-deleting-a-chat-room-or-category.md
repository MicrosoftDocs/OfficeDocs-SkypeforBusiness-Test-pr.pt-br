---
title: 'Lync Server 2013: Excluindo sala de chat ou categoria'
TOCTitle: Excluindo sala de chat ou categoria
ms:assetid: adccb869-0015-4eba-ac73-718bac7843b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215881(v=OCS.15)
ms:contentKeyID: 49307805
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo sala de chat ou categoria no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

As salas do Chat Persistente podem ser excluídas. Se tiver uma sala de chat que não está mais sendo usada, você pode desativá-la. Para obter mais detalhes, consulte [Habilitar ou desabilitar uma sala de chat no Lync Server 2013](lync-server-2013-disabling-or-enabling-a-chat-room.md).

Um administrador do Chat Persistente pode consultar se há salas de chat desativadas e limpá-las de forma periódica e permanente usando o cmdlet Windows PowerShell, **Remove-CsPersistentChatRoom**.

É possível excluir categorias. No entanto, para excluir uma categoria, você deve excluir todas as salas de chat sob ela ou movê-las para uma nova categoria, deixando uma categoria vazia para exclusão. O Servidor de Chat Persistente não permite que você exclua uma categoria que contém salas de chat. Para obter detalhes, consulte [Movendo uma sala de chat de uma categoria a outra no Lync Server 2013](lync-server-2013-moving-a-chat-room-from-one-category-to-another.md).

Para obter detalhes sobre como excluir categorias vazias usando o Interface da linha de comando do Windows PowerShell, consulte "Gerenciamento de sala" em [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

Para obter detalhes sobre salas de chat e categorias, consulte [Configurar salas no Lync Server 2013](lync-server-2013-configure-rooms.md) e [Configurar categorias no Lync Server 2013](lync-server-2013-configure-categories.md) na documentação de Implantação.

