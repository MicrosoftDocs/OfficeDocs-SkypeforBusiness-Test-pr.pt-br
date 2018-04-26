---
title: 'Lync Server 2013: Visão geral do Roteamento Baseado em Local'
TOCTitle: Visão geral do Roteamento Baseado em Local
ms:assetid: 4aa494bd-0d66-4335-b9e8-f758d44a7202
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994032(v=OCS.15)
ms:contentKeyID: 52057600
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

O roteamento baseado na localização introduz um novo conjunto de regras que modifica o roteamento de chamadas PSTN nacionais e internacionais para evitar desvio de tarifas. O roteamento baseado na localização oferece a flexibilidade para abranger essas regras em regiões específicas, gateways específicos ou somente conjunto de usuários específico.

Os cenários a seguir ilustram os principais tipos de restrições que o roteamento baseado na localização pode impor:

  - Chamadas de egresso – O roteamento baseado na localização pode impor chamadas de saída para egressar de um gateway PSTN localizado na mesma região do chamador para evitar desvio de tarifas PSTN, que evita o egresso de chamadas de um gateway PSTN localizado em uma região diferente do chamador.

  - Chamadas de ingresso – O roteamento com base na localização pode evitar que chamadas PSTN de entrada liguem para pontos de extremidade do Lync se o gateway PSTN que roteia a chamada de entrada não estiver localizado na mesma região que o usuário do Lync chamado.

  - Regiões desconhecidas – O roteamento baseado na localização restringe chamadas PSTN de entrada e saída para e de usuários localizados em locais indeterminados (por exemplo, usuários remotos conectados a partir da Internet ou localizados em regiões desconhecidas).

  - Regiões internacionais – O roteamento baseado na localização impõe o roteamento de chamadas de saída por meio de gateways PSTN internacionais se não for possível localizar um gateway local para o local do usuário.

## Consulte Também

#### Outros Recursos

[Planejamento de Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)

