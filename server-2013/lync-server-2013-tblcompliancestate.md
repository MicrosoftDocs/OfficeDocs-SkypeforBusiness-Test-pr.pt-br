---
title: 'Lync Server 2013: tblComplianceState'
TOCTitle: tblComplianceState
ms:assetid: ea82e56c-3cca-4d89-b4e6-6bcaeb1f2830
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615045(v=OCS.15)
ms:contentKeyID: 49308486
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblComplianceState no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblComplianceState contém informações sobre o estado de conformidade de todo o pool.

### Colunas

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>lastProcessedEntryID</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>ID do último evento de conformidade processado.</p></td>
</tr>
<tr class="even">
<td><p>activeServerID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do servidor de conformidade que possui o bloqueio exclusivo no banco de dados, ou -1 se nenhum.</p></td>
</tr>
<tr class="odd">
<td><p>lockExpirationTime</p></td>
<td><p>datetime2, não nulo</p></td>
<td><p>Hora de expiração do bloqueio (se activeServerID não for igual a -1).</p></td>
</tr>
</tbody>
</table>

