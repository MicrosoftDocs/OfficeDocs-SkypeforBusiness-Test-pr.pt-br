---
title: 'Lync Server 2013: Concedendo permissões'
TOCTitle: Concedendo permissões
ms:assetid: d1c9ea66-bd07-480e-99a0-011108f97e42
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398901(v=OCS.15)
ms:contentKeyID: 49308201
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Concedendo permissões no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-15_

Para configuração, é possível conceder permissões para o grupo universal RTCUniversalServerAdmins para uma OU específica do Active Directory, permitindo os membros do grupo RTCUniversalServerAdmins nesta OU instalar o Lync Server 2013 no domínio especificado. Ao conceder permissões para um OU, as seguintes permissões são concedidas:

  - Ler

  - Gravar

  - ReadSPN

  - WriteSPN

Para administração, é possível adicionar permissões às UOs especificadas de modo que os membros dos grupos universais do RTC criados pela preparação da floresta possam acessar as UOs sem precisar ser membros do grupo Admins. do Domínio. As permissões adicionadas à UO especificada são as mesmas permissões que o cmdlet **Enable-CsAdDomain** adiciona aos recipientes de UO dos computadores e usuários.

## Nesta seção

  - [Concedendo permissões de configuração no Lync Server 2013](lync-server-2013-granting-setup-permissions.md)

  - [Concedendo permissões de unidade organizacional no Lync Server 2013](lync-server-2013-granting-organizational-unit-permissions.md)

