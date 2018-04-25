---
title: Tabela UserStatistics no Lync Server 2013
TOCTitle: Tabela UserStatistics no Lync Server 2013
ms:assetid: cfaf803b-1679-4169-92d3-533fad3e56ed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721893(v=OCS.15)
ms:contentKeyID: 49886423
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela UserStatistics no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela UserStatistics é uma tabela de suporte. Cada registro na tabela armazena informações sobre o uso individual do usuário no sistema. Esta tabela foi introduzida no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Chave/índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica este usuário.</p></td>
</tr>
<tr class="even">
<td><p><strong>LastLogInTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Última vez que o usuário fez o login.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastConfOrganizedTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Última vez que o usuário organizou uma conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>LastCallOrganizerCallFailureTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Última vez que o usuário enfrentou uma falha de ligação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastConfOrganizerCallFailureTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Última vez que o usuário enfrentou uma falha de ligação como um organização da conferência.</p></td>
</tr>
</tbody>
</table>

