---
title: 'Lync Server 2013: Visão geral de Arquivamento'
TOCTitle: Visão geral de Arquivamento
ms:assetid: 1e3c2ef1-f561-4f57-8b6a-7d78addc1ed1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204729(v=OCS.15)
ms:contentKeyID: 49306072
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2013-09-30_

Arquivamento no Lync Server 2013 oferece uma forma de arquivar comunicações enviadas através do Lync Server 2013.

É possível implementar o Arquivamento como parte da sua implantação inicial do Lync Server 2013 ou é possível adicioná-lo a uma implantação existente. Para usar os bancos de dados de Arquivamento do Lync Server 2013 (banco de dados do SQL Server) para armazenamento de dados de arquivamento, use o Construtor de Topologias para adicionar bancos de dados a sua topologia e publique a topologia novamente. Se todos seus usuários estão hospedados no Exchange 2013 e possuem suas caixas de correio em Retenção Local, você não precisa atualizar sua topologia, mas precisa apenas habilitar a integração do Microsoft Exchange para armazenar os dados arquivados no Exchange 2013.

Ao implementar o Arquivamento, você o configura para especificar o que é arquivado. Por padrão, nada é arquivado. Você configura e gerencia o Arquivamento usando o Painel de Controle do Lync Server 2013. É possível implementar o Arquivamento para comunicações internas, comunicações externas ou ambos. É possível definir as configurações de arquivamento de toda sua organização e, opcionalmente, para sites específicos, pools de sites e usuários e grupos de usuários específicos. Para obter detalhes sobre a determinação das opções adequadas para sua organização, consulte [Definindo seus requisitos para Arquivamento no Lync Server 2013](lync-server-2013-defining-your-requirements-for-archiving.md) na documentação de Planejamento. Para obter detalhes sobre como as políticas de Arquivamento e configurações são implementadas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações.

