---
title: "Lync Server 2013: planj. p/ alta dispon. e recup. de desastre"
TOCTitle: Planejamento para alta disponibilidade e recuperação de desastre
ms:assetid: 15a72073-0336-45dd-b2a0-35e7522c6000
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204703(v=OCS.15)
ms:contentKeyID: 49305983
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-31_

Como no Lync Server 2010, o principal esquema de alta disponibilidade para a maioria das funções de servidor no Lync Server 2013 é baseado na redundância de servidor via pools. Se um servidor executando uma certa função de servidor falha, os ouros servidores no pool executando a mesma função assumem a carga daquele servidor. Isso se aplica a servidores Front-End, Servidores de Borda, Servidores de Mediação e Diretores.

O Lync Server 2013 adiciona novas medidas de recuperação de desastre para os pools Front-End, introduzindo a dispersão geográfica de seus servidores em dois data centers para fornecer a continuação do serviço caso um pool ou site caiam por inteiro.

O Lync Server 2013 também aprimora a alta disponibilidade do Servidor Back-End, oferecendo suportado ao espelhamento de SQL síncrono para seus bancos de dados de Back-End.

Essa seção explica como estes principais recursos de alta disponibilidade e de recuperação de disastres, e também cobre quais passos você pode tomar para ter alta disponibilidade e recuperação de disastres também para suas outras funções de servidor.

## Nesta seção

  - [Recuperação de desastre do pool Front-End no Lync Server 2013](lync-server-2013-front-end-pool-disaster-recovery.md)

  - [Recuperação de desastres do servidor de borda no Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)

  - [Planejamento para resiliência do Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md)

  - [Recursos de gerenciamento de chamada para recuperação de desastre no Lync Server 2013](lync-server-2013-call-management-features-for-disaster-recovery.md)

  - [Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Resiliência de site metropolitano no Lync Server 2010](lync-server-2013-compatibility-with-lync-server-2010-metropolitan-site-resiliency.md)

