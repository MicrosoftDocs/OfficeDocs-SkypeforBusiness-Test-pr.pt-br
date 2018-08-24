---
title: 'Lync Server 2013: Implantando repositório unificado de contatos'
TOCTitle: Implantando repositório unificado de contatos
ms:assetid: 68959d58-ac8a-45de-afcd-b9de2c36799c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204963(v=OCS.15)
ms:contentKeyID: 49306984
ms.date: 06/06/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando repositório unificado de contatos no Lync Server 2013

 

_**Tópico modificado em:** 2016-06-06_

A habilitação do repositório unificado de contatos no Lync Server 2013 não exige configurações de topologia. A habilitação do repositório unificado de contatos para os usuários exige o seguinte:

  - Que a política do repositório unificado de contatos esteja habilitada (ela é habilitada por padrão).

  - Que os usuários façam logon com o Lync 2013 pelo menos uma vez.

Depois que os contatos de um usuário tiverem sido migrados, o que acontece automaticamente quando um usuário faz logon com o Lync 2013, o usuário pode acessar e gerenciar seus contatos do Lync a partir do Lync 2013, do Outlook 2013 ou do Outlook Web Access. O usuário não precisa estar conectado ao Lync para gerenciar seus contatos do Outlook ou do Outlook Web Access.

> [!IMPORTANT]  
> Se um usuário fizer logon a partir do Lync 2010 após a migração, os contatos e grupos estarão disponíveis e atualizados, mas ele não poderá gerenciar (ou seja, adicionar, excluir, transferir, marcar, desmarcar ou modificar) esses contatos.

## Nesta seção

  - [Habilitar usuários para repositório unificado de contatos no Lync Server 2013](lync-server-2013-enable-users-for-unified-contact-store.md)

  - [Migrar usuários para o repositório unificado de contatos no Lync Server 2013](lync-server-2013-migrate-users-to-unified-contact-store.md)

  - [Reverter usuários migrados no Lync Server 2013](lync-server-2013-roll-back-migrated-users.md)

