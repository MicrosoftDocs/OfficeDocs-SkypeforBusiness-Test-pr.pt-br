---
title: Restaurando dados do chat persistente
TOCTitle: Restaurando dados do chat persistente
ms:assetid: c251a7fa-50da-434b-b39a-17f5978ce736
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945649(v=OCS.15)
ms:contentKeyID: 52057719
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando dados do chat persistente

 

_**Tópico modificado em:** 2013-02-18_

O conteúdo da sala do Chat Persistente está armazenado no banco de dados do Chat Persistente (Mgc.mdf). Deve-se gravar com frequência uma cópia de segurança desses dados que são corporativamente essenciais. Além do conteúdo da sala de chat, diretores (como usuários e grupos) e as funções e acesso que eles têm em relação às salas de chat e conteúdo de salas de chat também são armazenados no banco de dados do Chat Persistente.

Como você deve restaurar os seus dados de Chat Persistente depende do método que você utilizou para realizar o backup.

  - Se você utilizou procedimentos de backup de SQL Server, você precisa utilizar procedimentos de restauração desse mesmo tipo.

  - Se você utilizou o cmdlet **Export-CsPersistentChatData** para realizar backup de dados de Chat Persistente, então você precisa utilizar o cmdlet **Import-CsPersistentChatData** para restaurá-los.

