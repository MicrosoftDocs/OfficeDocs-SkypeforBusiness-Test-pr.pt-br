---
title: 'Lync Server 2013: Preparando Serviços de Domínio Active Directory bloqueado'
TOCTitle: Preparando Serviços de Domínio Active Directory bloqueado
ms:assetid: 68bde963-3fa3-4102-88d6-ac931c1dd2d7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398492(v=OCS.15)
ms:contentKeyID: 49306986
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando Serviços de Domínio Active Directory bloqueado no Lync Server 2013

 

_**Tópico modificado em:** 2012-05-14_

As organizações frequentemente bloqueiam os Serviços de Domínio Active Directory para ajudar a reduzir os riscos de segurança. Entretanto, um ambiente do Active Directory bloqueado pode limitar as permissões exigidas pelo Lync Server 2013. A preparação adequada de um ambiente do Active Directory bloqueado para o Lync Server 2013 envolve algumas considerações e etapas adicionais.

As permissões estão limitadas em um ambiente de Active Directory bloqueado de duas maneiras:

  - As ACEs (entradas de controle de acesso) de usuários autenticados são removidas dos contêineres.

  - A herança de permissões está desabilitada nos contêineres de objetos de Usuário, Contato, InetOrgPerson ou Computador.

## Nesta seção

  - [Permissões de usuário autenticado são removidas no Lync Server 2013](lync-server-2013-authenticated-user-permissions-are-removed.md)

  - [Herança de permissões está desabilitado em computadores, usuários ou contêiners InetOrgPerson no Lync Server 2013](lync-server-2013-permissions-inheritance-is-disabled-on-computers-users-or-inetorgperson-containers.md)

