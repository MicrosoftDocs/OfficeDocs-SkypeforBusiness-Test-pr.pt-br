---
title: 'Lync Server 2013: Tabela Locations'
TOCTitle: Tabela Locations
ms:assetid: 78dc1b14-5394-4f8e-89d3-4ba593272a04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398596(v=OCS.15)
ms:contentKeyID: 49307188
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Locations no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma referência de local em uma chamada de emergência, como uma chamada do tipo 9-1-1 Avançado.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Location</strong></p></td>
<td><p>nvarchar (máx)</p></td>
<td><p></p></td>
<td><p>Local da chamada de emergência.</p></td>
</tr>
</tbody>
</table>

