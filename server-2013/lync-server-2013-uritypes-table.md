---
title: 'Lync Server 2013: Tabela UriTypes'
TOCTitle: Tabela UriTypes
ms:assetid: 77c4dfae-1b29-4e81-ba05-609e61643998
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398587(v=OCS.15)
ms:contentKeyID: 49307170
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela UriTypes no Lync Server 2013

 

_**Tópico modificado em:** 2015-06-16_

A tabela UriTypes Table contém os tipos diferentes de URI (Uniform Resource Identifier) monitorados no Microsoft Lync Server 2013.


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
<td><p><strong>UriTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo atribuído a um tipo de URI.</p></td>
</tr>
<tr class="even">
<td><p><strong>UriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Descrições de tipos de URI diferentes. Os valores permitidos são:</p>
<ul>
<li><p>0 – Phone Uri</p></li>
<li><p>1 – User Uri</p></li>
</ul></td>
</tr>
</tbody>
</table>

