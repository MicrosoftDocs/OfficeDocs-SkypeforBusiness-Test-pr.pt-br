---
title: Considerações da interoperabilidade de videoconferência
TOCTitle: Considerações da interoperabilidade de videoconferência
ms:assetid: 31ead3b5-ed95-42d4-96e2-7d9403d5c026
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204790(v=OCS.15)
ms:contentKeyID: 49306306
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Considerações da interoperabilidade de videoconferência

 

_**Tópico modificado em:** 2012-10-02_

Esta seção descreve a experiência do usuário durante a fase de coexistência da migração na qual há interoperabilidade entre os clientes herdados e um pool do Lync Server 2013 ou entre clientes do Lync Server 2013 e um pool herdado.

## Pools do Lync Server 2013

Os usuários observarão o seguinte comportamento quando um cliente herdado for usado em um pool do Lync Server 2013:

  - Para chamadas de duas partes, a resolução de vídeo é a mesma da resolução do pool herdado.

  - Para conferências com vários participantes, os recursos de resolução de vídeo e videoconferência são os mesmos dos presentes no pool herdado. O modo de exibição de galeria e a alta resolução não estão disponíveis.

## Pools herdados

Os usuários observarão o seguinte comportamento quando um cliente do Lync Server 2013 for usado em um pool herdado:

  - Para chamadas de duas partes, os clientes do Lync Server 2013 podem usar novos recursos com os seguintes:
    
      - H.264 está disponível quando os dois participantes usam clientes do Lync Server 2013.
    
      - O cliente do Lync Server 2013 usa o valor padrão TotalReceiveVideoBitRateKb, visto que o servidor herdado não envia essas informações com provisionamento em banda.

  - Para conferências com vários participantes, os recursos de resolução de vídeo e videoconferência são os mesmos observados por um cliente herdado no pool herdado.

> [!NOTE]  
> Quando um servidor herdado hospeda um cliente do Lync Server 2013, é possível configurar a largura de banda da videoconferência para que todos os usuários no pool recebam apenas baixa resolução de vídeo, mas enviem alta resolução de vídeo. Um exemplo disso é quando MaxVideoRateAllowed é definido como CIF-250K na configuração de mídia e VideoBitRateKb é definido como 2.000 kbps na política de conferências. O efeito líquido dessa situação é que uma alta resolução não é possível para os usuários no pool.<br />Visto que MaxVideoRateAllowed não é mais usado para clientes do Lync Server 2013, ele não pode impedir que clientes do Lync Server 2013 solicitem vídeo de alta resolução. Em vez disso, defina VideoBitRateKb na política de conferências para todos os usuários do pool como o mesmo valor de MaxVideoRateAllowed (isto é, CIF é definido como 250 kbps, VGA é definido como 600 kbps ou HD é definido como 1.500 kbps).
