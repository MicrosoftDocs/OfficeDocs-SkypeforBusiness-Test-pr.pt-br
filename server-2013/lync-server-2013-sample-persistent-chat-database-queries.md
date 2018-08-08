---
title: "Lync Server 2013: Amostragem de consultas de banco de dados de Chat Persistente"
TOCTitle: Amostragem de consultas de banco de dados de Chat Persistente
ms:assetid: 545b1a93-9758-4344-98cc-aa0e559d494f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558649(v=OCS.15)
ms:contentKeyID: 49306732
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Amostragem de consultas de banco de dados de Chat Persistente para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Esta seção contém exemplos de consultas do banco de dados do Chat Persistente.

Use o exemplo a seguir para obter uma lista de suas salas de chat mais ativas do Chat Persistente após uma determinada data.

    SELECT nodeName as ChatRoom, COUNT(*) as ChatMessages
      FROM tblChat, tblNode
      WHERE channelId = nodeID AND dbo.fnTicksToDate(chatDate) > '1/1/2011'
      GROUP BY nodeName
      ORDER BY ChatMessages DESC

Use o exemplo a seguir para obter uma lista de seus usuários mais ativos após uma determinada data.

    SELECT prinName as Name, count(*) as ChatMessages
      FROM tblChat, tblPrincipal
      WHERE prinID = userId AND dbo.fnTicksToDate(chatDate) > '1/1/2011'
      GROUP BY prinName
      ORDER BY ChatMessages DESC

Use o seguinte exemplo para obter uma lista de todos que já enviaram uma mensagem com a frase "Olá Mundo".

    SELECT nodeName as ChatRoom, prinName as Name, content as Message
      FROM tblChat, tblNode, tblPrincipal
      WHERE channelId = nodeID AND userId = prinID AND content like '%Hello World%'

Use o exemplo a seguir para obter uma lista de membros do grupo de uma determinada entidade.

    SELECT prinName as Name    
      FROM tblPrincipalAffiliations as pa, tblPrincipal
      where principalID = 7 and affiliationID = prinID

Use o exemplo a seguir para obter uma lista de todas as salas de chat das quais um usuário, Maria da Silva, é um membro direto.

    SELECT DISTINCT nodeName as ChatRoom, prinName as Name          
      FROM tblPrincipalRole, tblPrincipal, tblNode
      WHERE  prinRoleNodeID = nodeID AND prinRolePrinID = prinID AND prinName = 'Jane Dow'

Use o exemplo a seguir para obter uma lista dos convites recebidos por um usuário.

    SELECT prinName
          ,nodeName
          ,invID   
          ,createdOn
      FROM tblPrincipalInvites as inv, tblPrincipal as p, tblNode as n
      where inv.prinID = 5 AND inv.prinID = p.prinID and inv.nodeID = n.nodeID
      ORDER BY invID DESC

