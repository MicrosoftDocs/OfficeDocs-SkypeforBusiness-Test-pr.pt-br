---
title: "Lync Server 2013: Adic. domínios de usuários e grupos de usuários à categoria da sala"
TOCTitle: Adicionando domínios de usuários e grupos de usuários à categoria da sala
ms:assetid: ee03f2cf-1c84-41c4-b524-d0729be33b8c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215884(v=OCS.15)
ms:contentKeyID: 49308536
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionando domínios de usuários e grupos de usuários à categoria da sala no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-07_

Para adicionar grupos maiores de usuários a uma sala de chat, consulte [Configurar categorias no Lync Server 2013](lync-server-2013-configure-categories.md) e [Gerenciar categorias](manage-categories.md) na documentação de implantação. Por exemplo, esse comando adiciona todos os usuários da UO NorthAmericaUsers no Active Directory à sala de chat NorthAmerica:

    Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="OU=NorthAmericaUsers,DC=litwareinc,DC=com"}

Esse comando adiciona todos os membros do grupo de distribuição Finanças à mesma sala de chat:

    Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="CN=Finance,OU=ExternalUsers,DC=litwareinc,DC=com"}

