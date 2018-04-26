---
title: Tabela ConferenceJoinTimeThresholds no Lync Server 2013
TOCTitle: Tabela ConferenceJoinTimeThresholds no Lync Server 2013
ms:assetid: 3944d724-bdd8-4d1c-a2af-933ee8141529
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204809(v=OCS.15)
ms:contentKeyID: 49306432
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ConferenceJoinTimeThresholds no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ConferenceJoinTimeThresholds contém os limites de classificação usados pelo Relatório de Resumo de Tempo de Participação em Conferência. Este relatório resume o período necessário para que os usuários participem com êxito de uma conferência; esses valores de tempo são reportados como média e em uma das seguintes categorias:

  - Menos de 2 segundos.

  - Entre 2 e 5 segundos.

  - Entre 5 e 10 segundos.

  - Mais de 10 segundos

A tabela ConferenceJoinTimeThresholds contém os valores de classificação de 2 segundos, 5 segundos e 10 segundos.

Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<td><p><strong>Limite</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo da classificação.</p></td>
</tr>
<tr class="even">
<td><p><strong>ThresholdValue</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Limite superior da classificação. Os valores permitidos são:</p>
<ol>
<li><p>2</p></li>
<li><p>5</p></li>
<li><p>10</p></li>
</ol></td>
</tr>
</tbody>
</table>

