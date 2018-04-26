---
title: 'Lync Server 2013: Chamadas de entrada'
TOCTitle: Chamadas de entrada
ms:assetid: 65b9c1b4-6af7-4527-8c33-22c4442bd209
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994038(v=OCS.15)
ms:contentKeyID: 52057649
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Chamadas de entrada no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O roteamento de chamadas recebidas para usuários habilitados para o Roteamento com Base no Local depende da localização do ponto de extremidade do usuário. Veja a seguir como o roteamento de chamadas recebidas é afetado. Se um usuário tem uma chamada recebida em um ponto de extremidade em um local de rede habilitado para o Roteamento com Base no Local, e se o ponto de extremidade estiver no mesmo local de rede de um gateway PSTN, a chamada será roteada. Se um usuário tem uma chamada recebida em um ponto de extremidade em um local de rede habilitado para o Roteamento com Base no Local, e se o ponto de extremidade estiver em um local de rede diferente de um gateway PSTN, a chamada não será roteada. Quando o usuário não tem pontos de extremidade localizados no mesmo local de rede de um gateway PSTN do qual a chamada recebida é originada, a chamada recebido será roteada diretamente para o correio de voz do usuário e uma mensagem de chamada perdida será enviada para o destinatário da chamada.

As configurações de encaminhamento de chamada de um usuário habilitado para Roteamento com Base no Local continuarão válidas. No entanto, as chamadas encaminhadas estarão sujeitas às restrições de Roteamento Baseado em Locais do usuário.

A tabela a seguir ilustra como o Roteamento com Base no Local afeta o roteamento de chamadas recebidas, dependendo do local do ponto de extremidade do destinatário da chamada. O local da rede do gateway PSTN é habilitado para Roteamento com Base no Local, e este só permite o roteamento de chamadas PSTN para pontos de extremidade dentro do mesmo local de rede.

### Destinatário recebe uma chamada do PSTN

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>O ponto de extremidade do destinatário da chamada fica no mesmo local da rede que o gateway PSTN</th>
<th>O ponto de extremidade do destinatário da chamada não fica no mesmo local da rede que o gateway PSTN</th>
<th>O ponto de extremidade do destinatário da chamada fica em um local de rede desconhecido ou não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Roteamento da chamada PSTN recebida</p></td>
<td><p>Chamada recebida é roteada para os pontos de extremidade do destinatário</p></td>
<td><p>Chamada recebida não é roteada para os pontos de extremidade do destinatário</p></td>
<td><p>Chamada recebida não é roteada para os pontos de extremidade do destinatário</p></td>
</tr>
</tbody>
</table>

  

## Consulte Também

#### Outros Recursos

[Cenários para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)

