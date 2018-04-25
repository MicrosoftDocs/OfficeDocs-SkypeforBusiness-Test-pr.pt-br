---
title: 'Lync Server 2013: Tabela de regiões'
TOCTitle: Tabela de regiões
ms:assetid: 1751a6aa-a6e8-4f16-8eb7-ae731c2e3ee3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398235(v=OCS.15)
ms:contentKeyID: 49306011
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela de regiões no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Regions é uma tabela de suporte. Cada registro representa um país ou uma região definida na configuração de rede.


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
<td><p><strong>RegionKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo de identificação de país/região.</p></td>
</tr>
<tr class="even">
<td><p><strong>RegionName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Exclusivo</p></td>
<td><p>O nome do país/região.</p></td>
</tr>
</tbody>
</table>

