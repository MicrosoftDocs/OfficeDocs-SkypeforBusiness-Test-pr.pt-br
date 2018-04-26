---
title: Migrando federação XMPP
TOCTitle: Migrando federação XMPP
ms:assetid: b8d2b4b9-d0ed-4b48-820a-2c257fbdd2fb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721861(v=OCS.15)
ms:contentKeyID: 49886377
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando federação XMPP

 

_**Tópico modificado em:** 2012-10-19_

As versões anteriores do Lync Server e do Office Communications Server forneceram um gateway de protocolo XMPP que poderia ser implantada como uma função de servidor separada e permitir a federação com implantações de XMPP. No Lync Server 2013, a funcionalidade XMPP pode ser implantada como um recurso. A funcionalidade XMPP é instalada em duas partes: como um proxy XMPP que funciona no Servidor de borda do Lync Server 2013 e o Gateway XMPP que funciona no Servidor front-end do Lync Server 2013.

Da perspectiva de migração, uma conta de usuário do Lync Server pode ser movida para um pool do Lync Server 2013 e continuar a usar o gateway XMPP herdado. Isso é possível somente quando o parceiro federado XMPP não está configurado no Lync Server 2013.

Em resumo, se o Lync Server 2010 foi implantado com o Gateway XMPP do Office Communications Server 2007 R2 e a federação XMPP foi ativada para usuários herdados do Lync Server 2010, para migrar a federação XMPP para o Lync Server 2013:

1.  Implante um pool do Lync Server 2013.

2.  Implante um servidor de borda do Lync Server 2013.

3.  Mova todos os usuários para o pool do Lync Server 2013

4.  Crie políticas de acesso XMPP e certificados para o Servidor de borda.

5.  Ative a federação XMPP no Lync Server 2013. 

6.  Atualize as entradas DNS para que apontem para o Gateway XMPP do Lync Server 2013.

