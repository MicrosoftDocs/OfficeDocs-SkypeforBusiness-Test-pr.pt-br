---
title: Práticas recomendadas do Servidor de Chat Persistente
TOCTitle: Práticas recomendadas do Servidor de Chat Persistente
ms:assetid: dc18e7f7-599b-4d32-abf7-cd9e691426a2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398970(v=OCS.15)
ms:contentKeyID: 49308314
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Práticas recomendadas do Servidor de Chat Persistente

 

_**Tópico modificado em:** 2012-10-06_

Conforme você cria suas categorias e salas do Chat Persistente e projeta seu escopo e associação, as seguintes dicas podem ajudar você a planejar:

  - Se sua empresa não exigir uma parede ética, não restrinja o escopo em sua árvore de categorias. Coloque todos os seus usuários no escopo da categoria raiz e permita que esse escopo seja herdado em toda a árvore. Em seguida, use somente as listas de associação para conceder ou restringir acesso a cada sala de chat.

  - Na maioria dos casos, você deve habilitar os usuários criarem novas salas de chat, a fim de que as discussões sobre novos tópicos possam ser iniciadas a qualquer momento. Faça isso tornando a lista de **Criadores** o mesmo que a lista **AllowedMembers**. No entanto, se você deseja permitir que apenas uma equipe de suporte central ou usuários designados criem salas, torne a lista de **Criadores** o subconjunto adequado.

  - Proporcione a cada sala de chat um nome completo e um resumo por tópicos que descreve onde ela se encaixa em sua organização. Como os usuários não podem ver o nome da categoria quando usam a sala de chat, não é possível depender do nome de categoria para ajudar os usuários a determinar o fórum de discussão pretendido para a sala de chat.

  - Você pode desejar ter um fluxo de trabalho de criação de sala personalizado se tiver determinadas convenções de nomeação ou outros controles de acesso ou validações para implementar. A configuração do Chat Persistente permite personalizar o **RoomManagementUrl** para algo que você hospeda. Por exemplo, quando os usuários clicam em **Criar uma sala** em seu cliente Lync, eles podem ser redirecionados para sua solução personalizada.

  - Criar uma variedade de complementos que ajudam a melhorar a experiência de salas de chat trazendo outros dados comerciais para salas de chat. Os administradores devem registrar os complementos que desejam permitir no sistema. Os gerentes da sala de chat e criadores podem escolher da lista de complementos permitidos aqueles mais relevantes para suas respectivas salas.

## Consulte Também

#### Outros Recursos

[Gerenciando categotias, salas e suplementos no Lync Server 2013](lync-server-2013-managing-categories-rooms-and-add-ins.md)

