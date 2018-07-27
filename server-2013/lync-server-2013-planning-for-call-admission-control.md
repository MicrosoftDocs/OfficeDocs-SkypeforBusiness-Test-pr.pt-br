---
title: 'Lync Server 2013: Planejamento para controle de admissão de chamada'
TOCTitle: Planejamento para controle de admissão de chamada (CAC)
ms:assetid: ca367138-adf5-4119-bc40-5ddf335ed22f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398842(v=OCS.15)
ms:contentKeyID: 49308098
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para controle de admissão de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Para aplicativos de UC (comunicações unificadas) baseados em IP, como telefonia, vídeo e compartilhamento de aplicativos, a largura de banda disponível de redes empresariais geralmente não é considerada como um fator limitante em ambientes de LAN; no entanto, em links WAN que interconectam locais, a largura de banda de rede pode ser limitada. Quando um influxo de tráfego de rede sobrecarrega um link WAN, mecanismos atuais como enfileiramento, armazenamento em buffer e descarte de pacotes são usados para resolver o congestionamento. O tráfego extra é normalmente atrasado até que o congestionamento de rede melhore ou, se necessário, o tráfego é descartado. No caso de tráfego de dados convencional em tais situações, o cliente receptor pode se recuperar. Para tráfego em tempo real como comunicações unificadas, o congestionamento da rede não pode ser resolvido dessa maneira, uma vez que o tráfego de comunicações unificadas é sensível à latência e à perda de pacotes. O congestionamento na WAN pode resultar em uma QoE (Qualidade da Experiência) ruim para os usuários finais. Para o tráfego em tempo real em condições congestionadas, é melhor negar chamadas em vez de permitir conexões com qualidade ruim.

O CAC determinar se há largura de banda suficiente para estabelecer uma sessão em tempo real de qualidade aceitável. No Lync Server 2013, o CAC controla o tráfego em tempo real apenas para áudio e vídeo, mas não afeta o tráfego de dados. Se o caminho WAN padrão não possui a largura de banda necessária, o CAC tenta rotear a chamada através de um caminho Internet ou PSTN. O CAC está disponível apenas no Lync Server.

Esta seção descreve a funcionalidade de controle de admissão de chamada e explica como planejar CAC.

> [!NOTE]  
> O Lync Server possui três recursos Enterprise Voice avançados: controle de admissão de chamadas (CAC), serviços de emergência (E9-1-1) e bypass de mídia. Para obter uma visão geral da informação de planejamento que é comum a todos os três recursos, consulte <a href="lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md">Configurações de rede para recursos avançados do Enterprise Voice no Lync Server 2013</a>.

## Nesta seção

  - [Visão geral do controle de admissão de chamada no Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md)

  - [Definindo seus requisitos de controle de admissão de chamadas no Lync Server 2013](lync-server-2013-defining-your-requirements-for-call-admission-control.md)

  - [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md)

  - [Componentes e topologias para CAC no Lync Server 2013](lync-server-2013-components-and-topologies-for-cac.md)

  - [Práticas recomendadas para controle de admissão de chamada no Lync Server 2013](lync-server-2013-best-practices-for-call-admission-control.md)

  - [Lista de verificação de implantação para controle de admissão de chamada no Lync Server 2013](lync-server-2013-deployment-checklist-for-call-admission-control.md)

