---
title: Roteamento com Base no Local e Transferências de Chamada Consultiva
TOCTitle: Roteamento com Base no Local e Transferências de Chamada Consultiva
ms:assetid: b12460c2-36c8-481f-b867-fe10dc1c0bdf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362836(v=OCS.15)
ms:contentKeyID: 56270463
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento com Base no Local e Transferências de Chamada Consultiva

 

_**Tópico modificado em:** 2015-03-09_

Além de aplicar o Roteamento com Base no Local às reuniões do Lync, o aplicativo de Roteamento com Base no Local da Conferência impõe restrições de Roteamento com Base no Local em transferências de chamada consultiva provenientes dos pontos de extremidade PSTN. Uma transferência de chamada consultiva é estabelecida entre duas partes, na qual uma das partes transfere a chamada a um novo usuário. Por exemplo, uma extremidade PSTN liga para o usuário A (destinatário do Lync). O usuário A determina que o usuário PSTN deve ser encaminhado para o usuário B (usuário Lync). O usuário A coloca a chamada com o usuário PSTN em espera e liga para o usuário B. O usuário B concorda em falar com o usuário PSTN. O usuário A transfere a ligação eM espera para o usuário B.

**Fluxo da Transferência de Chamada Consultiva**

![Diagrama de roteamento baseado em local para conferência](images/Dn362836.e4d43d6f-23d2-49c9-b12b-15248a743f92(OCS.15).jpg "Diagrama de roteamento baseado em local para conferência")

Quando um usuário habilita o Roteamento com Base no Local ele inicia uma transferência de chamada consultiva de um ponto de extremidade PSTN (como mostrado na figura anterior), isso cria duas chamadas ativas, uma entre o usuário PSTN e o usuário Lync A, e outra entre o usuário Lync A e o usuário Lync B. O comportamento seguinte é imposto pelo aplicativo de Roteamento com Base no Local da Conferência:

  - Se o tronco SIP roteando a chamada PSTN for autorizado a reencaminhar essa chamada para um site da rede onde o usuário Lync B esteja localizado (i.e. destino da transferência), a transferência de chamada será permitida; do contrário, a transferência consultiva de chamada será bloqueada. Essa autorização é realizada quando a pessoa transferida está no mesmo local de rede que o tronco SIP roteando a chamada ativa do ponto de extremidade PSTN.

  - Se o tronco SIP roteando a chamada de entrada PSTN não for autorizado a rotear chamadas para o local de rede onde a pessoa transferida (usuário Lync B) está localizada, ou a pessoa transferida estiver localizada em um local de rede desconhecido, a transferência de chamada consultiva para o ponto de extremidade PSTN (i.e., destino de transferência de chamada) será bloqueada.

A tabela a seguir descreve como as restrições do Roteamento com Base no Local são aplicadas pelo aplicativo de Roteamento com Base no Local da Conferência para transferências de chamada consultiva. Embora pontos de extremidade PBX não sejam diretamente associados a um local de rede, o tronco SIP do PBX é conectado para poder ser atribuído a um local de rede. Portanto, o ponto de extremidade PBX pode ser indiretamente associado a um local de rede.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Site de rede da pessoa em chamada transferida</p></td>
<td><p>Site de rede de destino de chamada transferida</p></td>
<td><p>Comportamento</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade do PSTN</p></td>
<td><p>Usuário Lync no mesmo local de rede (i.e. site 1)</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Usuário Lync em diferentes locais de rede (i.e. site 2)</p></td>
<td><p>Transferência consultiva não permitida</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Usuário Lync em um local de rede desconhecido</p></td>
<td><p>Transferência consultiva não permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Usuário Lync Federado</p></td>
<td><p>Transferência consultiva não permitida</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Ponto de extremidade PBX no mesmo site (i.e. site 1)</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Ponto de extremidade PBX em sites diferentes (i.e. site 2)</p></td>
<td><p>Transferência consultiva não permitida</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade do PBX no mesmo site (i.e. site 1)</p></td>
<td><p>Ponto de extremidade do PSTN</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade do PBX em sites diferentes (i.e. site 2)</p></td>
<td><p>Ponto de extremidade PSTN</p></td>
<td><p>Transferência consultiva não permitida</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade PBX em qualquer site</p></td>
<td><p>Usuário Lync no mesmo local de rede (i.e. site 1)</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade PBX em qualquer site</p></td>
<td><p>Usuário Lync em diferentes locais de rede (i.e. site 2)</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="even">
<td><p>Ponto de extremidade PBX em qualquer site</p></td>
<td><p>Usuário Lync em um local de rede desconhecido</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
<tr class="odd">
<td><p>Ponto de extremidade PBX em qualquer site</p></td>
<td><p>Usuário Lync Federado</p></td>
<td><p>Transferência consultiva permitida</p></td>
</tr>
</tbody>
</table>

