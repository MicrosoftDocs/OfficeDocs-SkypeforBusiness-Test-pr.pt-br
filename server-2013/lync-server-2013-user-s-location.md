---
title: 'Lync Server 2013: Local do usuário'
TOCTitle: Local do usuário
ms:assetid: ce57941d-086b-448e-8ada-c7d636a2a1c9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994073(v=OCS.15)
ms:contentKeyID: 52057725
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Local do usuário no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-09_

O Roteamento com Base no Local influencia as mesmas sub-redes, regiões e locais de rede conforme definido no Lync Server usado pelos serviços E9-1-1, CAC (controle de admissão de chamadas) e Media Bypass para aplicar restrições de roteamento de chamadas a fim de impedir desvios de tarifas de PSTN. A localização de um usuário é determinada pela sub-rede IP em que o(s) ponto(s) de extremidade do usuário estão conectados. Cada sub-rede IP está associada a um local de rede que, por sua vez, está agrupado a regiões de rede definidas pelo administrador. O Roteamento com Base no Local é forçado com base no local da rede do usuário.

As regras do Roteamento com Base no Local são aplicadas por local de rede, ou seja, um determinado conjunto de regras será aplicado a todos os pontos de extremidade habilitados para o Roteamento com Base no Local que estão no mesmo local de rede. Os administradores podem aplicar o Roteamento com Base no Local aos locais de rede que forem necessários.

As políticas de roteamento de voz podem ser definidas por locais de rede a fim de determinar um gateway PSTN específico que deve ser usado por todos os usuários do local da rede para chamar telefones PSTN. Essas políticas de roteamento de voz prevalecem sobre o roteamento definido pela política de voz do usuário quando ele está em um local de rede habilitado para o Roteamento com Base no Local, impedindo o roteamento de chamadas por outros gateways PSTN habilitados para o Roteamento com Base no Local. Quando um usuário Lync faz uma chamada PSTN, sua política de voz determina se ele pode ser autorizado a fazer a chamada. Caso seja permitido, o Roteamento com Base no Local determina de qual gateway PSTN a chamada deve partir. O Roteamento com Base no Local faz essa determinação com base na localização do usuário.

A localização de um usuário pode ser categorizada das seguintes formas:

  - O usuário está em um local de rede conhecido e habilitado para o Roteamento com Base no Local e seu número de DDR (Discagem Direta a Ramal) termina em um gateway PSTN que está no mesmo local de rede (por exemplo, no escritório). O roteamento de chamadas efetuadas será feito pela política de roteamento de voz do local de rede em que o usuário está. As chamadas PSTN recebidas do usuário são roteadas para pontos de extremidade que estão no mesmo local de rede do gateway PSTN.

  - O usuário está em um local de rede conhecido que fica em um local de rede diferente do gateway PSTN. (isto é, o usuário viajou para outro escritório da empresa). O roteamento de chamadas efetuadas será feito pela política de roteamento de voz do local de rede em que o usuário está. As chamadas PSTN recebidas pelo usuário não serão roteadas para pontos de extremidade que estão localizados em locais diferentes do gateway PSTN a fim de impedir desvios de tarifas de PSTN.

  - Quando um usuário está em um local de rede desconhecido para a implantação do Lync Server, o roteamento de chamadas efetuadas se baseará na política de voz atribuída ao usuário para gateways PSTN sem estar vinculadas às restrições do Roteamento com Base no Local. As chamadas PSTN recebidas não serão roteadas para pontos de extremidade localizados em locais de rede desconhecidos a fim de impedir desvios de tarifas de PSTN.

## Consulte Também

#### Outros Recursos

[Orientação para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-guidance-for-location-based-routing.md)

