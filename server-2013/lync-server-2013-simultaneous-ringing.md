---
title: 'Lync Server 2013: Toque simultâneo '
TOCTitle: Toque simultâneo
ms:assetid: df02f919-4d50-4832-9300-6c51f8b4fc56
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994079(v=OCS.15)
ms:contentKeyID: 52057745
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Toque simultâneo no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Quando a parte que recebe a chamada tiver habilitado o toque simultâneo, o Roteamento com Base no Local analisa o local da parte que faz a chamada e os pontos de extremidade das partes chamadas para determinar se a chamada deve ser roteada.

A tabela a seguir ilustra um usuário configurado com o toque simultâneo e o alvo de toque simultâneo é um usuário no mesmo local da rede, em um local diferente da rede ou em um local da rede desconhecido.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Chamadas de entrada do PSTN para</th>
<th>Localizado no mesmo local de rede do chamador</th>
<th>Localizado em um local de rede diferente do chamador</th>
<th>Localizado em um local de rede desconhecido ou não habilitado para o Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuário do Lync</p></td>
<td><p>Toque simultâneo permitido</p></td>
<td><p>Toque simultâneo não permitido</p></td>
<td><p>Toque simultâneo não permitido</p></td>
</tr>
</tbody>
</table>

  
A tabela a seguir ilustra uma chamada de um usuário do Lync (ou seja, chamador do Lync) no mesmo local de rede, em um local de rede diferente ou em um local de rede desconhecido. O chamador tem um ponto de extremidade do PSTN (ou seja, telefone celular) configurado como um destino de toque simultâneo. Nesse cenário, o Roteamento com Base no Local determinará se a chamada deverá ser roteada para o destino de toque simultâneo (ou seja, telefone celular) do chamador ou não.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Destino de toque simultâneo</th>
<th>Localizado no mesmo local de rede do chamador</th>
<th>Localizado em um local de rede diferente do chamador</th>
<th>Localizado em um local de rede desconhecido ou não habilitado para o Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ponto de extremidade do PSTN</p></td>
<td><p>Toque simultâneo permitido por meio da política de roteamento de voz do local do chamador</p></td>
<td><p>Toque simultâneo permitido por meio da política de roteamento de voz do local do chamador</p></td>
<td><p>Toque simultâneo permitido por meio da política de roteamento de voz do local do chamador para troncos não habilitados para o Roteamento com Base no Local</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Outros Recursos

[Cenários para Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)

