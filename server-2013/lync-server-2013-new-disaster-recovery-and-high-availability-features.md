---
title: "Lync Server 2013: Novos recursos de recuperação de desastre e alta dispon."
TOCTitle: Novos recursos de recuperação de desastre e alta disponibilidade
ms:assetid: 4fa7cd0f-784b-4d3f-b839-432c2ecaf7c1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204892(v=OCS.15)
ms:contentKeyID: 49306691
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novos recursos de recuperação de desastre e alta disponibilidade no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-20_

Com no Lync Server 2010, o principal esquema de alta disponibilidade (HA) para o Lync Server 2013 é baseado na redundância do servidor por meio de pool. Se um servidor executando uma determinada função do servidor falhar, os outros servidores no pool executando a mesma função assumirão a carga desse servidor. Isso se aplica aos Servidores Front-End, Servidores de Borda, Servidores de Mediação e Diretores.

O Lync Server 2013 adiciona novas medidas de recuperação de desastres permitindo que você emparelhe pools Front-End localizados em dois datacenters. Se um dos pools emparelhados parar de funcionar, um administrador pode transferir os usuários do pool para outro pool no emparelhamento, para fornecer a continuação do serviço. Essa função não requer soluções de rede ou de hardware dispendiosas, como redes de armazenamentos ou discos compartilhados.

O Lync Server 2013 também adiciona alta disponibilidade ao Servidor Back-End. Essa é uma topologia opcional na qual você implanta dos Servidores Back-End para um pool Front-End e configura espelhamento SQL síncrono para todos os bancos de dados do Lync sendo executados nos Servidores Back-End. Você também pode escolher implantar uma testemunha para o espelhamento.

## Consulte Também

#### Conceitos

[Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)

