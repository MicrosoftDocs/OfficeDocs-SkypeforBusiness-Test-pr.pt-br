---
title: 'Lync Server 2013: Tabela MonitoredRegionLink'
TOCTitle: Tabela MonitoredRegionLink
ms:assetid: cebda194-7be3-42d6-b6f0-c86f8b0f200a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398874(v=OCS.15)
ms:contentKeyID: 49308169
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MonitoredRegionLink no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela MonitoredRegionLink é uma tabela de suporte. Cada registro representa um link entre dois países/regiões.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Coluna</strong></th>
<th><strong>Tipo de dados</strong></th>
<th><strong>Chave/Índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Region1Key</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Referência na <a href="lync-server-2013-region-table.md">Tabela de regiões no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Region2Key</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Referência na <a href="lync-server-2013-region-table.md">Tabela de regiões no Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>

