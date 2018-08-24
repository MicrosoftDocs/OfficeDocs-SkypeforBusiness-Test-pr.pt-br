---
title: "Compat. do Lync Server 2013 com resiliência de site metrop. do Lync Server 2010"
TOCTitle: Resiliência de site metropolitano no Lync Server 2010
ms:assetid: 18673ff6-b664-4a57-a89b-cbda8b129e6a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204715(v=OCS.15)
ms:contentKeyID: 49306019
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resiliência de site metropolitano no Lync Server 2010

 

_**Tópico modificado em:** 2014-03-19_

A solução de resiliência de site metropolitano suportada para Lync Server 2010 não é suportada para Lync Server 2013. Essa solução envolvia a extensão de um único pool de Front-Ends por dois data centers na mesma área metropolitana.

A solução de resiliência de site metropolitano foi projetada para se recuperar da perda de um datacenter completo. Ao estender seu pool entre dois datacenters, normalmente se coloca metade dos front-ends em um datacenter e a outra metade em outro datacenter. Se você perder um datacenter completo, terá perdido metade de seus servidores de front-ends. Isso pode causar problemas com o novo modelo de sistema distribuído para pools de front-ends no Lync Server 2013. Para obter mais informações, consulte [Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

