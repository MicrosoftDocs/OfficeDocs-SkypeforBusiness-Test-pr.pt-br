---
title: 'Lync Server 2013: Práticas recomendadas para controle de admissão de chamada'
TOCTitle: Práticas recomendadas para controle de admissão de chamada
ms:assetid: 97173cca-8175-4ae2-a247-eb7ef809da93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398770(v=OCS.15)
ms:contentKeyID: 49307528
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Práticas recomendadas para controle de admissão de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

Para aprimorar o desempenho e facilitar a implantação, aplique as práticas recomendadas a seguir quando implantar o controle de admissão de chamadas:

  - Garanta que as WANs estejam adequadamente provisionadas para o tráfego de mídia atual e antecipado.
    
    > [!NOTE]  
    > É recomendável que você leve em consideração um buffer para seus limites de largura de banda. Existem cenários como condições de corrida que afetam a largura de banda total usada e podem resultar em situações em que o limite da largura de banda é excedido. Por exemplo, se duas chamadas tentarem iniciar enquanto o tráfego de mídia está alcançando um limite da largura de banda, uma delas pode ser recusada porque a outra conseguiu iniciar primeiro.

  - Monitore o uso da rede e registros de detalhes de chamadas para que possa escolher configurações de CAC ótimas e atualizá-las conforme o uso da rede muda.

  - Use políticas de largura de banda de CAC para complementar as configurações de QoS.

  - Se você desejar rerotear chamadas bloqueadas para o PSTN, verifique a funcionalidade e a capacidade do PSTN. Para detalhes, consulte [Planejando roteamento de voz de saída no Lync Server 2013](lync-server-2013-planning-outbound-voice-routing.md).
    
    > [!NOTE]  
    > A capacidade refere-se ao número de portas que precisam ser abertas para oferecer suporte a um possível reroteamento do PSTN.
