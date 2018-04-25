---
title: 'Lync Server 2013: Delegação'
TOCTitle: Delegação
ms:assetid: 89e76e5c-3cfb-4504-8d0d-7509c8ba9815
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994045(v=OCS.15)
ms:contentKeyID: 52057673
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Delegação no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-09_

As funcionalidades de delegação no Lync são afetadas pelo Roteamento com Base no Local da seguinte forma:

  - quando um delegado habilitado para o Roteamento com Base no Local realiza uma chamada em nome de um gerente, a política de voz do delegado é utilizada para autorizar a chamada e a política de roteamento de voz do local do delegado será usada para rotear a chamada

  - Para chamadas de entrada do PSTN para um gerente, as mesmas regras que se aplicam ao encaminhamento de chamadas ou toque simultâneo se aplicarão conforme descrito nos tópicos de Transferência e encaminhamento de chamada e Toque Simultâneo.

  - Quando um delegado configura um ponto de extremidade do PSTN como um destino de toque simultâneo, para uma chamada de entrada para o gerente, a política de roteamento de voz do local associado ao tronco de entrada será utilizada para rotear a chamada para o ponto de extremidade do PSTN do delegado.

  - Para delegação, recomenda-se que o gerente e seus delegados associados estejam, em geral, localizados no mesmo local da rede.

## Consulte Também

#### Outros Recursos

[Cenários para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)

