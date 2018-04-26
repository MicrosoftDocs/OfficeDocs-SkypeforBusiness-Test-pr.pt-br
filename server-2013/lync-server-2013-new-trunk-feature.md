---
title: 'Lync Server 2013: Novo recurso de tronco'
TOCTitle: Novo recurso de tronco
ms:assetid: 9b398bc8-2760-4218-b1a4-89b9694b1171
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688152(v=OCS.15)
ms:contentKeyID: 49886330
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novo recurso de tronco no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

No Microsoft Lync Server 2013, podem ser definidos vários troncos entre um Servidor de Mediação e um gateway. O Microsoft Lync Server 2010 permitia apenas um tronco entre um Servidor de Mediação e um gateway PSTN. Este recurso fornece a flexibilidade para definir troncos adicionais. Um tronco é uma associação lógica entre um FQDN e porta de escuta do Servidor de Mediação e um FQDN e porta de escuta do gateway PSTN. Este novo recurso possibilita definir facilmente o tronco para resiliência (onde vários Servidores de mediação podem ser usados para rotear chamadas para o mesmo Gateway PSTN), para interoperabilidade de PBX, onde vários troncos com diferentes políticas associadas podem ser usados entre o IP-PBX e um Servidor de Mediação, e para configurações de tronco SIP onde os Servidor de Mediação em diferentes locais têm troncos SIP para a portadora referenciados pelo menos FQDN da portadora.

## Consulte Também

#### Conceitos

[Novos recursos do Enterprise Voice no Lync Server 2013](lync-server-2013-new-enterprise-voice-features.md)

