---
title: 'Lync Server 2013: Tronco SIP'
TOCTitle: Tronco SIP
ms:assetid: 7c586401-d0e5-4017-b3e1-fe5e7f8fc6db
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398619(v=OCS.15)
ms:contentKeyID: 49307234
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-13_

O SIP é usado para iniciar e gerenciar sessões de comunicações de VoIP (voz sobre IP) para o serviço telefônico básico e para vários serviços de comunicação em tempo real adicionais, como serviços de mensagens instantâneas, conferência, detecção de presença e multimídia. Esta seção oferece informações de planejamento para a implementação de *troncos SIP* , um tipo de conexão SIP que se estende além do limite da rede local.

## O que é o tronco SIP?

Um tronco SIP é uma conexão do IP estabelece um vínculo de comunicações SIP entre sua organização e um provedor de serviços de telefonia de Internet (ITSP), além do firewall. Normalmente, um tronco SIP é usado para conectar o site central da organização a um ITSP. Em alguns casos, você também pode optar por usar um tronco SIP para conectar o site da filial a um ITSP.

## Troncos SIP vs. Conexões diretas do cabo SIP

O termo *tronco* deriva da tecnologia de comutação de circuitos. Refere-se a uma linha física dedicada que conecta o equipamento de comutação telefônica. Assim como seu predecessor, troncos TDM (multiplexação por divisão do tempo), os troncos SIP são conexões entre duas redes SIP, o Lync Server 2013 enterprise e o ITSP. Diferentemente dos troncos de comutação de circuitos, os troncos SIP são conexões virtuais que podem ser estabelecidas sobre qualquer tipo de conexão de troncos SIP compatíveis. Para obter detalhes sobre os tipos de conexões compatíveis, consulte [Como implementar tronco SIP no Lync Server 2013?](lync-server-2013-how-do-i-implement-sip-trunking.md).

As conexões SIP diretas, por outro lado, são conexões de SIP que não atravessam o limite de rede local (ou seja, elas se conectam a um gateway PSTN ou PBX dentro de sua rede interna). Para obter detalhes sobre como usar as conexões diretas de SIP com Lync Server 2013, consulte [Conexões SIP diretas no Lync Server 2013](lync-server-2013-direct-sip-connections.md).

## Nesta seção

  - [Visão geral do tronco SIP no Lync Server 2013](lync-server-2013-overview-of-sip-trunking.md)

  - [Como implementar tronco SIP no Lync Server 2013?](lync-server-2013-how-do-i-implement-sip-trunking.md)

  - [Componentes e topologias para tronco SIP no Lync Server 2013](lync-server-2013-components-and-topologies-for-sip-trunking.md)

  - [Tronco SIP do site da filial no Lync Server 2013](lync-server-2013-branch-site-sip-trunking.md)

  - [Lista de verificação de tronco SIP para Lync Server 2013](lync-server-2013-sip-trunk-deployment-checklist.md)

