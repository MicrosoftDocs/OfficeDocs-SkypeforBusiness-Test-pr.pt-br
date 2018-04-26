---
title: 'Lync Server 2013: Local do gateway PSTN'
TOCTitle: Local do gateway PSTN
ms:assetid: 49693a35-fad3-49ee-a71e-c7e4537b79aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994031(v=OCS.15)
ms:contentKeyID: 52057599
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Local do gateway PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-09_

Chamadas roteadas por meio de gateways PSTN e PBXs podem exigir restrições de Roteamento com Base no Local dependendo da localização desses sistemas. O Roteamento com Base no Local pode ser habilitado na granularidade por tronco.

O Roteamento com Base no Local introduz o seguinte conjunto de regras quando habilitado em um tronco:

  - Quando o Roteamento com Base no Local é habilitado por tronco, as regras definidas naquele tronco serão aplicadas apenas a chamadas roteadas através dele.

  - Para impedir que ferramentas PSTN sejam ignoradas quando chamadas originadas de um local de rede diferente daquele em que está o gateway PSTN, o Roteamento com Base no Local associa um local de rede àquele determinado tronco. Isso define que o local de rede permite que chamadas sejam roteadas para um determinado tronco.

Há duas formas de habilitar os troncos para o Roteamento com Base no Local:

  - O tronco é definido para um gateway PSTN que faz chamadas para o PSTN. As chamadas recebidas roteadas por um tronco deste tipo serão roteadas apenas para os pontos de extremidade localizados dentro do mesmo local de rede que o tronco.

  - O tronco é definido para um ponto Servidor de Mediação que não faz chamadas para o PSTN e para os usuários de serviços com telefones legados em locais estáticos (isto é, telefones PBX). Para esta configuração em particular, todas as chamadas recebidas roteadas por um tronco deste tipo serão consideradas como se fossem originadas do mesmo local de rede do tronco. Chamadas de usuários de PBX terão a mesma imposição do Roteamento com Base no Local que os usuários do Lync que estão no mesmo local de rede do tronco. Se dois sistemas PBX em locais de rede separados estiverem conectados através do Lync Server, o Roteamento com Base no Local permitirá o roteamento a partir de um ponto de extremidade PBX em um dos locais de rede para o outro ponto de extremidade PBX no outro local de rede. Este cenário não será bloqueado pelo Roteamento com Base no Local. Além deste cenário, e de modo semelhante a como um usuário do Lync no mesmo local de rede, os pontos de extremidade conectados a um ponto Servidor de Mediação com esta configuração poderão fazer ou receber chamadas com outro outro pronto Servidor de Mediação que não roteia chamadas para PSTN (isto é, um ponto de extremidade conectado.a um PBX diferente), não importando a qual local de rede o ponto Servidor de Mediação está associado. Todas as chamadas recebidas, efetuadas, transferidas e encaminhadas envolvendo pontos de extremidade PSTN estarão sujeitas ao Roteamento com Base no Local para usar apenas gateways PSTN definidos como local para tal ponto Servidor de Mediação.

## Consulte Também

#### Outros Recursos

[Orientação para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-guidance-for-location-based-routing.md)

