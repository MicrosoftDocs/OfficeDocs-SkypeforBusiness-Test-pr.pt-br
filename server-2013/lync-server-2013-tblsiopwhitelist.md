---
title: 'Lync Server 2013: tblSiopWhiteList'
TOCTitle: tblSiopWhiteList
ms:assetid: 05fc1df4-32eb-4d46-9d1c-e0b607091142
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558607(v=OCS.15)
ms:contentKeyID: 49305744
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblSiopWhiteList no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela SiopWhiteList é a lista de suplementos registrados que podem ser associados aos nós.

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
<td><p>siopID</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUID do suplemento.</p></td>
</tr>
<tr class="even">
<td><p>siopName</p></td>
<td><p>nvarchar (50), não nulo</p></td>
<td><p>Nome de exibição do suplemento.</p></td>
</tr>
<tr class="odd">
<td><p>siopUrl</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>URL do suplemento.</p></td>
</tr>
</tbody>
</table>


### Chave

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>siopID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

