---
title: 'Lync Server 2013: Transferência e encaminhamento de chamadas'
TOCTitle: Transferência e encaminhamento de chamadas
ms:assetid: 978610ec-63c7-4cf6-ad7a-9ef91559bf12
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994051(v=OCS.15)
ms:contentKeyID: 52057655
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Transferência e encaminhamento de chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Quando um ponto de extremidade PSTN estiver envolvido, o Roteamento com Base no Local analisará a localização do ponto de extremidade do destinatário da chamada e o ponto de extremidade para o qual a chamada será transferida ou encaminhada (isto é, destino da transferência/encaminhamento). O Roteamento com Base no Local determina se a chamada deve ser transferida ou encaminhada dependendo da localização de ambos os pontos de extremidade.

A tabela a seguir ilustra o cenário de um usuário do Lync em uma chamada com um ponto de extremidade PSTN que transfere a chamada para outro usuário do Lync. Dependendo do local da rede do ponto de extremidade do destinatário da transferência, o Roteamento com Base no Local afeta o roteamento da transferência ou encaminhamento de chamada.

### Iniciando uma transferência ou encaminhamento de chamada

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Usuário que inicia a transferência/encaminhamento da chamada</th>
<th>O ponto de extremidade de destino está no mesmo local de rede do usuário que inicia a transferência ou o encaminhamento da chamada</th>
<th>O ponto de extremidade de destino está em um local de rede diferente do que o do usuário que inicia a transferência ou o encaminhamento da chamada</th>
<th>O ponto de extremidade de destino está em um local de rede desconhecido ou em um local de rede não habilitado para o Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuário do Lync</p></td>
<td><p>Encaminhamento ou transferência de chamada permitido</p></td>
<td><p>Encaminhamento ou transferência de chamada não permitido</p></td>
<td><p>Encaminhamento ou transferência de chamada não permitido</p></td>
</tr>
</tbody>
</table>

  

Por exemplo: um usuário do Lync em uma chamada com um ponto de extremidade PSTN transfere a chamada para outro usuário do Lync que está no mesmo local de rede. Neste caso, a transferência de chamada é permitida.

A tabela a seguir ilustra o cenário de um usuário do Lync em uma chamada com um outro usuário do Lync, e um deles transfere a chamada para um ponto de extremidade PSTN. Dependendo do local onde está o usuário para o qual a chamada está sendo transferida, a tabela detalha como o Roteamento com Base no Local afeta a chamada.

### Transferência ou encaminhamento da chamada para um ponto de extremidade PSTN

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Destino do ponto de extremidade da transferência/encaminhamento de chamada</th>
<th>Usuários do Lync no mesmo local de rede</th>
<th>Usuários do Lync em locais de rede diferentes</th>
<th>Um ou ambos os usuários do Lync estão em um local de rede desconhecido ou em um local de rede não habilitado para o Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ponto de extremidade do PSTN</p></td>
<td><p>Encaminhamento ou transferência da chamada é permitido pela política de roteamento de voz do local do destinatário da transferência</p></td>
<td><p>Encaminhamento ou transferência da chamada é permitido pela política de roteamento de voz do local do destinatário da transferência</p></td>
<td><p>O encaminhamento ou a transferência da chamada é permitida pela política de voz do destinatário da transferência somente pelos troncos não habilitados para o Roteamento com Base no Local</p></td>
</tr>
</tbody>
</table>

  
Por exemplo: um usuário do Lync em uma chamada com outro usuário do Lync que está na mesma rede transfere a chamada para um ponto de extremidade PSTN e a transferência de chamada é permitida.

## Consulte Também

#### Outros Recursos

[Cenários para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)

