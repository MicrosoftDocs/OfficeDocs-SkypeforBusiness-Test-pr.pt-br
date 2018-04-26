---
title: Fazendo backup e restaurando o Lync Server 2013
TOCTitle: Fazendo backup e restaurando o Lync Server 2013
ms:assetid: 07dc1f5e-af66-4e18-bf39-881dceff8bc3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202160(v=OCS.15)
ms:contentKeyID: 52057549
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fazendo backup e restaurando o Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Nesta seção, você encontrará as melhores práticas para efetuar backup dos dados do Lync Server 2013 e restaurá-lo em caso de falha. Estas melhores práticas se aplicam às seguintes situações:

  - Todo um pool Lync Server de qualquer tipo (Servidor Front-End, Servidor de Borda, Servidor de Mediação, Servidor de Chat Persistente ou Diretor) ou um servidor individual em um desses pools.

  - O Servidor de Gerenciamento Central

  - Um servidor Standard Edition

  - Um Enterprise EditionServidor Back-End

  - Um Repositório de Arquivos

  - Um Banco de dados de arquivamento, Banco de dados de monitoramento ou um banco de dados de Chat Persistente

Essa seção não inclui informações sobre restauração de um site inteiro ou para o desenvolvimento um site em espera. Para obter detalhes sobre o desenvolvimento de uma solução de recuperação de desastres com pools de Front-End pareados, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md). Este é o método recomendado para planejamento de recuperação de desastres.

Se você implantou pools de Front-End pareados, se um desses pools pode falhar e se tornar irrecuperável, você pode restaurá-lo com um nome de domínio qualificado totalmente novo (FQDN) a partir deste pool pareado. Para detalhes sobre as etapas para efetuar tal recuperação, consulte [Fazendo failover de um pool no Lync Server 2013](lync-server-2013-failing-over-a-pool.md). Adicionalmente, se você quiser recriar um pool que falhou e é irrecuperável e fazia parte de um par de Front-End, use as etapas em [Realizando um failover ABC do pool de front-ends](lync-server-2013-performing-an-abc-front-end-pool-failover.md).

A metodologia descrita neste documento envolve considerações especiais durante a fase de planejamento. Para obter detalhes, consulte [Estabelecendo um plano de restauração e backup](lync-server-2013-establishing-a-backup-and-restoration-plan.md).

## Nesta seção

  - [Preparando para restauração e backup do Lync Server](lync-server-2013-preparing-for-lync-server-backup-and-restoration.md)

  - [Fazendo backup de dados e configurações](lync-server-2013-backing-up-data-and-settings.md)

  - [Restaurando configurações e dados](lync-server-2013-restoring-data-and-settings.md)

  - [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md)

