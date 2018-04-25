---
title: 'Lync Server 2013: Movendo uma sala de chat de uma categoria a outra'
TOCTitle: Movendo uma sala de chat de uma categoria a outra
ms:assetid: 7e93b8f6-5a18-4476-a432-3918e01bcfa6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215877(v=OCS.15)
ms:contentKeyID: 49307253
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Movendo uma sala de chat de uma categoria a outra no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Recomendamos que você não modifique a categoria de um Chat Persistente depois que a sala de chat é criada. Contudo, se a o gerente da sala tiver privilégios de **Criador** em outra categoria, ele pode mover a sala de uma categoria a outra. A sala não é excluída e recriada. É uma mudança de associação no banco de dados.

Muda a categoria de uma sala de chat deve ser feito raramente. Uma categoria determina o membro permitido para a sala de chat, por isso, quando uma sala de chat muda de categoria, todas as listas de controle de acesso ao sistema (SACLs) não mais suportados pela nova categoria são purgadas. Por exemplo, se um usuário for membro da sala e não mais um **AllowedMember** na nova categoria, a filiação da sala será modificada e o usuário será removido da sala.

Para obter detalhes sobre como mover uma sala de chat usando Interface da linha de comando do Windows PowerShell, consulte "Gerenciamento de sala" em [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

Para obter detalhes sobre como configurar salas de chat, consulte [Configurar salas no Lync Server 2013](lync-server-2013-configure-rooms.md), na documentação de Implantação.

