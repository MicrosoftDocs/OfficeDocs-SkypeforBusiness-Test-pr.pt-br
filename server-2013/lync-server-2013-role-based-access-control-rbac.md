---
title: Função de controle de acesso baseado em função (RBAC) do Lync Server 2013
TOCTitle: Função de controle de acesso baseado em função (RBAC) do Lync Server 2013
ms:assetid: d01fba36-eb7e-4de9-9bba-5102ae157820
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481134(v=OCS.15)
ms:contentKeyID: 59679349
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Função de controle de acesso baseado em função (RBAC) do Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

O Microsoft Lync Server 2013 inclui grupos de Função de controle de acesso baseado em função (RBAC) para permitir que você delegue tarefas administrativas, enquanto mantém altos padrões de segurança. Esses grupos são criados durante a preparação da floresta. Para obter mais detalhes sobre a preparação da floresta, consulte [Active Directory Domain Services para Lync Server 2013](lync-server-2013-active-directory-domain-services-for-lync-server.md). Para obter mais detalhes sobre os grupos específicos criados pela preparação da floresta, consulte [Alterações feitas pela preparação da floresta no Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) na Documentação de implantação.

Com a RBAC, o privilégio administrativo é concedido através da atribuição de funções administrativas pré-definidas aos usuários, incluindo 11 funções pré-definidas que abrangem várias tarefas administrativas comuns. Cada função está associada a uma lista específica de cmdlets do Shell de Gerenciamento do Lync Server que os usuários dessa função podem executar. Você pode utilizar a RBAC para seguir o princípio do "menor privilégio", no qual os usuários somente recebem as habilidades administrativas que seus trabalhos exigem. Para obter mais detalhes, consulte [Planejamento de controle de acesso baseado em função no Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md) na Documentação de planejamento.

