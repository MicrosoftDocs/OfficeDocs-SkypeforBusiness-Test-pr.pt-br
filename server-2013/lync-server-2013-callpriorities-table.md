---
title: 'Lync Server 2013: Tabela CallPriorities'
TOCTitle: Tabela CallPriorities
ms:assetid: 043b63ae-2d64-4f38-a0df-18aa08d6caf5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398093(v=OCS.15)
ms:contentKeyID: 49305714
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela CallPriorities no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

CallPriorities é uma tabela estática que armazena a lista de prioridades de chamada possíveis, como "emergência", "urgente" ou "normal".


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
<th>Chave/Índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PriorityId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Prioridade</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p>
<ul>
<li><p>0 - Desconhecido</p></li>
<li><p>1 - Não urgente</p></li>
<li><p>2 - Normal</p></li>
<li><p>3 - Urgente</p></li>
<li><p>4 - Emergência</p></li>
</ul></td>
</tr>
</tbody>
</table>

