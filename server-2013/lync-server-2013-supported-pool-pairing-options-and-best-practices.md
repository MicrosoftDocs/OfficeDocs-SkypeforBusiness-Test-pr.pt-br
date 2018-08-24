---
title: "Lync Server 2013: Opções e práticas recomend. de empar. de pool com suporte"
TOCTitle: Opções e práticas recomendadas de emparelhamento de pool com suporte
ms:assetid: 142caf34-0f20-47f3-9d32-ce25ab622fad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204697(v=OCS.15)
ms:contentKeyID: 49305978
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Opções e práticas recomendadas de emparelhamento de pool com suporte para o Lync Server 2013

 

_**Tópico modificado em:** 2017-03-09_

Não há restrições de distância entre dois data centers que incluirão pools de Front End emparelhados entre si. É recomendável usar dois data centers na mesma região geográfica com links de alta velocidade entre eles. É melhor se os dois data centers estiverem suficientemente distantes para evitar que um único desastre atinja ambos ao mesmo tempo.

Ter dois data centers em regiões geográficas distintas é possível, mas poderia incorrer em maior perda de dados devido à latência na replicação dos dados.

Ao planejar quais pools emparelhar, você deve ter em mente que somente os emparelhamentos a seguir são suportados:

  - Pools do Enterprise Edition só podem ser emparelhados com outros pools do Enterprise Edition. Da mesma forma, pools do Standard Edition podem ser emparelhados somente com outros pools do Standard Edition.

  - Pools físicos só podem ser emparelhados com outros pools físicos. Da mesma forma, pools virtuais só podem ser emparelhados com outros pools virtuais.

Nem o Construtor de Topologias nem a validação da topologia proibirão o emparelhamento de dois pools de uma forma que estas recomendações não sejam seguidas. Por exemplo, o Construtor de Topologias permite o emparelhamento de um pool do Enterprise Edition com um pool do Standard Edition. No entanto, estes tipos de emparelhamento não são suportados.

Cada pool em um emparelhamento deve ter a capacidade de atender todos os usuários de ambos os pools em caso de desastre.

Se você emparelhar pools do Enterprise Edition, também poderá implementar alta disponibilidade nos servidores de Back End, mas para pares de pools do Standard Edition somente as medidas da recuperação de desastres estão disponíveis.

