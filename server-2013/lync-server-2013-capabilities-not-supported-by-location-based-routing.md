---
title: 'Lync Server 2013: Recursos não suportados pelo Roteamento Baseado em Local'
TOCTitle: Recursos não suportados pelo Roteamento Baseado em Local
ms:assetid: c3d54953-a7d6-4465-a6c3-ae411b2d8ea9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994071(v=OCS.15)
ms:contentKeyID: 52057722
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos não suportados pelo Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-12_

O roteamento baseado em local não se aplica aos tipos de interações a seguir. Esse roteamento não é imposto quando os pontos de extremidade do Lync interagem com pontos de extremidade PSTN usando esses recursos.

  - Discagem PSTN para conferências

  - Chamadas PSTN de entrada e saída por meio do grupo de resposta

  - Estacionamento de chamada ou recuperação de chamadas PSTN por meio do estacionamento de chamada

  - Chamadas PSTN de entrada para o serviço de anúncio

  - Chamadas PSTN de entrada recuperadas por meio do recebimento de chamada de grupo

Para impor regras de roteamento baseado em local aos tipos de interações na seguinte lista, você deve habilitar o roteamento baseado em local para conferência:

  - Discagem de saída PSTN de conferências

  - Escalonamentos de conversas de áudio ponto a ponto para conferências envolvendo pontos de extremidade PSTN

  - Transferências consultivas envolvendo pontos de extremidade PSTN

Para habilitar o roteamento baseado em local para conferência, consulte [Roteamento com base no local para conferência no Lync Server 2013](lync-server-2013-location-based-routing-for-conferencing.md).

## Consulte Também

#### Outros Recursos

[Planejamento de Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)

