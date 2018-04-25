---
title: Migrando federação de XMPP
TOCTitle: Migrando federação de XMPP
ms:assetid: 7368ee8f-a201-4d3a-b4e8-68396b156d4d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688093(v=OCS.15)
ms:contentKeyID: 49886263
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando federação de XMPP

 

_**Tópico modificado em:** 2012-10-16_

As versões anteriores do Office Communications Server forneciam uma gateway XMPP que podia ser implantado como uma função de servidor separada para permitir a federação com implantações XMPP. No Lync Server 2013, a funcionalidade XMPP pode ser implantada como um recurso. A funcionalidade XMPP é instalada em duas partes: como um proxy XMPP executado no servidor de borda do Lync Server 2013 e o gateway XMPP executado no servidor front-end do Lync Server 2013.

Pela perspectiva de migração, uma conta de usuário do Office Communications Server 2007 R2 pode ser movida para um pool do Lync Server 2013 e continuar a usar o gateway XMPP do Office Communications Server 2007 R2. Isso é possível somente quando o parceiro federado XMPP não está configurado no Lync Server 2013.

Em resumo, se o Office Communications Server foi implantado com o Gateway XMPP do Office Communications Server 2007 R2 e a federação XMPP foi ativada para usuários herdados do Office Communications Server 2007 R2, para migrar a federação XMPP para o Lync Server 2013:

1.  Implante um pool do Lync Server 2013.

2.  Implante um servidor de borda do Lync Server 2013.

3.  Mova todos os usuários para o pool do Lync Server 2013.

4.  Crie políticas de acesso XMPP e certificados para o Servidor de borda.

5.  Ative a federação XMPP no Lync Server 2013. 

6.  Atualize as entradas DNS para que apontem para o Gateway XMPP do Lync Server 2013.

