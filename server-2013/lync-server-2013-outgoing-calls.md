---
title: 'Lync Server 2013: Chamadas de saída'
TOCTitle: Chamadas de saída
ms:assetid: 885ffe6f-cd51-4f21-8d4f-a1ff8d818858
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994049(v=OCS.15)
ms:contentKeyID: 52057646
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Chamadas de saída no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O roteamento de chamadas de saída para usuários habilitados para o Roteamento com Base no Local é afetado pelo local da rede do ponto de extremidade do usuário. A tabela a seguir ilustra como o Roteamento com Base no Local afeta o roteamento de chamada de saída, dependendo do local do ponto de extremidade de quem faz a chamada.

### Pessoa fazendo uma chamada de saída para o PSTN

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Ponto de extremidade do usuário localizado em um local de rede habilitado para o Roteamento com Base no Local</th>
<th>Ponto de extremidade do usuário localizado em um local de rede desconhecido ou não habilitado para o Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Autorização de chamadas de saída</p></td>
<td><p>A chamada é autorizada com base na política de voz do usuário</p></td>
<td><p>A chamada é autorizada com base na política de voz do usuário</p></td>
</tr>
<tr class="even">
<td><p>Roteamento de chamada de saída</p></td>
<td><p>A chamada é roteada de acordo com a política de roteamento de voz do local da rede</p></td>
<td><p>A chamada é roteada de acordo com a política de voz do usuário e somente por meio de troncos não habilitados para o Roteamento com Base no Local (se disponível)</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Outros Recursos

[Cenários para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)

