---
title: 'Lync Server 2013: Controle de admissão de chamada e Servidor de Mediação'
TOCTitle: Controle de admissão de chamada e Servidor de Mediação
ms:assetid: 76faccdc-67d0-4c8b-8e47-1e23c93b02c6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398585(v=OCS.15)
ms:contentKeyID: 49307160
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Controle de admissão de chamada e Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

O CAC (Controle de Admissão de Chamadas), introduzido primeiramente no Lync Server 2010, gerencia o estabelecimento de sessão em tempo real com base na largura de banda disponível para ajudar a evitar uma QoE (Qualidade de Experiência) ruim para os usuários em redes congestionadas. Para oferecer suporte a esse recurso, o Servidor de Mediação, que oferece a sinalização e a conversão de mídia entre a infraestrutura do Enterprise Voice e um gateway ou provedor de tronco SIP, é responsável pelo gerenciamento da largura de banda para essas duas interações no lado do Lync Server e no lado do gateway. No controle de admissão de chamadas, a entidade de terminação de uma chamada lida com a reserva da largura de banda. Os pares de gateway (gateway de PSTU, IP-PBX, SBC) com que o Servidor de Mediação interage no lado do gateway não oferecem suporte ao controle de admissão de chamadas do Lync Server 2013. Dessa forma, o Servidor de Mediação precisa lidar com interações de largura de banda em nome do seu par de gateway. Sempre que possível, o Servidor de Mediação reservará largura de banda por antecipação. Se isso não for possível (por exemplo, a localidade do ponto de extremidade da mídia final no lado do gateway for desconhecido para uma chamada feita para o par de gateway), a largura de banda será reservada quando a chamada for feita. Esse comportamento pode resultar em uma inscrição em excesso da largura de banda, mas é a única maneira de impedir anéis falsos.

O bypass de mídia e o modo de reserva da largura de banda são mutuamente exclusivos. Se um bypass de mídia é empregado para uma chamada, o controle de admissão de chamada não é executado para essa chamada. O pressuposto é que não há links com largura de banda restrita envolvidos na chamada. Se o controle de admissão de chamada é usado para uma chamada específica que envolve o Servidor de Mediação, a chamada não pode empregar o bypass de mídia.

Para obter detalhes sobre o bypass de mídia ou controle de admissão de chamada, consulte [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) ou [Planejamento para controle de admissão de chamada no Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md) na documentação de Planejamento.

