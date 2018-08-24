---
title: 'Lync Server 2013: Planejamento para acesso de usuário externo'
TOCTitle: Planejamento para acesso de usuário externo
ms:assetid: ea098933-eff5-461e-aba3-e7f128784dc2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399048(v=OCS.15)
ms:contentKeyID: 49308485
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2013-01-19_

Muitas das comunicações na sua organização provavelmente envolvem pessoas fora do firewall: funcionários que estão temporariamente ou permanentemente fora do escritório, funcionários de clientes ou de organizações parceiras, pessoas que usam IMs (serviços de mensagens instantâneas) e clientes em potencial que você convida para reuniões e apresentações. Nesta documentação, essas pessoas são coletivamente chamadas de *usuários externos* .

Com o Microsoft Lync Server 2013, os usuários em sua organização podem usar IM e presença para se comunicar com usuários externos, e podem participar de conferência de áudio/vídeo (A/V) e webconferência com seus funcionários remotos e outros tipos de funcionários externos. Também é possível suportar acesso externo de dispositivos móveis e sobre o Enterprise Voice. Usuários externos que não são membros de sua organização podem participar de reuniões do Lync Server 2013 sem fazer logon em sua intranet, permitindo assim participantes anônimos.

Para suportar as comunicações por seu firewall organizacional, implante o Servidor de Borda Lync Server 2013, em sua rede de perímetro (também conhecida como sub-rede filtrada). O Servidor de Borda controla como os usuários fora do firewall podem se conectar à sua implantação do Lync Server 2013 interna. Também controla as comunicações com os usuários externos originários dentro do firewall.

Dependendo de seus requisitos, é possível implantar um ou mais Servidores de Borda em um ou mais locais. Esta seção descreve o acesso de usuário externo no Lync Server 2013 e explica como planejar sua topologia de borda e proxy reverso.

> [!NOTE]  
> Embora você precise de um Servidor de Borda para suportar o Enterprise Voice e o acesso de usuário externo, esta seção se concentra no suporte para IM, presença, conferência A/V, federação, webconferência e Lync Mobile. Para obter detalhes sobre o suporte ao Enterprise Voice, consulte <a href="lync-server-2013-planning-for-enterprise-voice.md">Planejamento para Enterprise Voice no Lync Server 2013</a> na documentação de Planejamento.

## Nesta seção

  - [Alterações no Lync Server 2013 que afetam o planejamento do Servidor de Borda](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md)

  - [Requisitos do sistema para componentes de acesso de usuário externo para Lync Server 2013](lync-server-2013-system-requirements-for-external-user-access-components.md)

  - [Visão geral de acesso de usuário externo no Lync Server 2013](lync-server-2013-overview-of-external-user-access.md)

  - [Noções básicas sobre a descoberta automática no Lync Server 2013](lync-server-2013-understanding-autodiscover.md)

  - [Escolhendo uma topologia no Lync Server 2013](lync-server-2013-choosing-a-topology.md)

  - [Coleta de dados no Lync Server 2013](lync-server-2013-data-collection.md)

  - [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

  - [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

  - [Planejar certificados do Servidor de Borda no Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)

  - [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)

