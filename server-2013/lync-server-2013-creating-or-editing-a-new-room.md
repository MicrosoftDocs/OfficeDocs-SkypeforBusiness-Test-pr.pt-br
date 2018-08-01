---
title: 'Lync Server 2013: Criando ou editando uma nova sala'
TOCTitle: Criando ou editando uma nova sala
ms:assetid: aa8f4349-cfd9-4036-9c4d-de8fb2c4c8a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215880(v=OCS.15)
ms:contentKeyID: 49307751
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criando ou editando uma nova sala no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-19_

A configuração das salas do Chat Persistente é geralmente feita pelos usuários; um administrador do Chat Persistente geralmente não configura ou gerencia salas de chat. Os cmdlets do Windows PowerShell para gerenciamento de salas estão disponíveis somente para Administradores **CsPersistentChatAdministrator**.

Usuários que são **Criadores** em uma dada categoria podem usar o cliente do Lync para criar e gerenciar salas. Os usuários que foram designados como gerentes de uma sala de chat específica também podem realizar gerenciamento contínuo da sala, como edição das propriedades ou associação das salas.


> [!TIP]  
> Os administradores do Chat Persistente podem ser também Criadores, e eles não estão sujeitos às restrições colocadas nos Criadores.



Como opção, se você for um administrador do Chat Persistente, é possível empregar uma interface de usuário para criar e gerenciar salas, em vez de usar cmdlets do Windows PowerShell. Para isso, habilite um administrador do Servidor de Chat Persistente para SIP, e depois use o cliente do Lync para criar e gerenciar salas de chat.

Se quiser criar um fluxo de trabalho de gerenciamento de sala personalizado, você pode definir a propriedade **RoomManagementUrl** em sua configuração do Servidor de Chat Persistente para redirecionar os usuários para sua solução personalizada do cliente Lync.

Para obter detalhes sobre como configurar salas de chat usando o Interface da linha de comando do Windows PowerShell, consulte "Gerenciamento de salas" em [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

Para obter detalhes sobre como configurar salas de chat, consulte [Configurar salas no Lync Server 2013](lync-server-2013-configure-rooms.md), na documentação de Implantação.

