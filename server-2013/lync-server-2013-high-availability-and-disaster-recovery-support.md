---
title: 'Lync Server 2013: Suporte à alta disponibilidade e recuperação de desastre'
TOCTitle: Suporte à alta disponibilidade e recuperação de desastre
ms:assetid: 47e77e85-c7c3-4ade-8db7-a34c71aeafd7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204866(v=OCS.15)
ms:contentKeyID: 49306592
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte à alta disponibilidade e recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-25_

O Lync Server 2013 fornece alta disponibilidade para redundância de servidor via pool. Se um servidor executando certa função de servidor falha, os outros servidores no pool que executam a mesma função recebem a carga de tal servidor. Isso se aplica a Servidores de Front End, Servidores de Borda, Servidores de Mediação e Diretores. Para detalhes sobre funções de servidor, consulte [Funções do servidor no Lync Server 2013](lync-server-2013-server-roles.md).

O Lync Server 2013 também fornece medições de recuperação de desastre ao ativar o pareamento de pool. Sr você implantar tal topologia, pode designar pares para pools de Front End, com cada pool em um par localizado em um datacenter separado, e em uma área geográfica separada. Se um pool ou site sair do ar, você pode redirecionar os usuários deste pool para outro pool no par, com o mínimo de interrupção de serviço.

O Lync Server 2013 também suporta alta disponibilidade do Servidor de Back End. Isso é uma topologia opcional o qual você implanta dois Servidores de Back End para um pool de Front End e define espelhamento SQL Server sincronizado para todos os bancos de dados Lync em execução nos Servidores de Back End.

Para detalhes sobre o pareamento de pool e espelhamento de Servidor de Back End, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

## Consulte Também

#### Conceitos

[Funções do servidor no Lync Server 2013](lync-server-2013-server-roles.md)  
[Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)

