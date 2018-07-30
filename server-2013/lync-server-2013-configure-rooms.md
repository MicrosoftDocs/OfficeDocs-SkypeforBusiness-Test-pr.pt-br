---
title: 'Lync Server 2013: Configurar salas'
TOCTitle: Configurar salas
ms:assetid: 8956bd2c-c863-4704-bc65-5c0d83556258
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205067(v=OCS.15)
ms:contentKeyID: 49307384
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar salas no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

A configuração das salas do Chat Persistente geralmente é feita por usuários ou outras equipes centrais por meio do Interface da linha de comando do Windows PowerShell; em geral, as salas de chat não são gerenciadas por administradores. No entanto, se for necessário criar e gerenciar salas de chat, use ou Interface da linha de comando do Windows PowerShell ou adicione a sim mesmo como participante da sala de chat e use o cliente Lync 2013.

Para obter detalhes sobre como configurar salas de chat usando o Interface da linha de comando do Windows PowerShell, consulte "Gerenciamento de salas" em [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

## Gerenciando dados em salas de chat

O Servidor de Chat Persistente permite que os usuários colaborem pr meio da postagem de mensagem nas salas do Chat Persistente. Os dados persistem no servidor e os membros da sala podem ter acesso a eles, inclusive ao histório de dados. No entanto, os usuários que têm funções diferentes têm acesso diferente aos dados persistentes conforme descrito na lista a seguir.

  - Os administradores podem excluir qualquer conteúdo (por exemplo, conteúdo postado antes de determinada data) de qualquer sala de char para impedir que o banco de dados assuma proporções muito grandesm. Eles também podem remover ou substituir mensagens consideradas impróprias para uma sala de chat específica.

  - Os usuários finais, incluisive os autores das mensagens, não podem excluir conteúdo de nenhuma sala de chat.

  - Os gerentes das salas de chat podem desabilitar salas, mas não excluí-las. Somente os administradores podem excluir salas de chat após a criação.

Quando a mensagem é excluída, não é possível desfazer a ação. No entanto, as mensagens excluídas podem ser restauradas caso exista um backup. Se houver um servidor de conformidade do Chat Persistente ativo, as mensgem antiga persistirão no banco de dados de conformidade.

> [!NOTE]  
> Esses dados das salas de chat aplicam-se ao Lync Server 2013 e ao aplicativo de API do Servidor de Chat Persistente, exceto quando a função de administrador estiver envolvida. A API do Servidor de Chat Persistente não pode ser usada em operações do administrador. Execute essas operações no Shell de Gerenciamento do Lync Server.
