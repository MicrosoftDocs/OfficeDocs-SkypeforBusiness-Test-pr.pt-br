---
title: Exibir UserAgent
TOCTitle: Exibir UserAgent
ms:assetid: b986f76f-f16e-4e5e-96cb-6e8f7f9b42ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721862(v=OCS.15)
ms:contentKeyID: 49886378
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir UserAgent

 

_**Tópico modificado em:** 2015-03-09_

A Exibição UserAgent armazena informações sobre os agentes do usuário que foram envolvidos em sessões com registros no banco de dados. Essa exibição foi apresentada no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UserAgentKey</p></td>
<td><p>int</p></td>
<td><p>Número exclusivo que identifica esse agente do usuário.</p></td>
</tr>
<tr class="even">
<td><p>UserAgent</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Cadeia de caracteres de agente do usuário.</p></td>
</tr>
<tr class="odd">
<td><p>UAType</p></td>
<td><p>smallint</p></td>
<td><p>Tipo de agente do usuário. Consulte o <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a> para obter mais detalhes.</p></td>
</tr>
<tr class="even">
<td><p>UACategory</p></td>
<td><p>nvarchar (64)</p></td>
<td><p>Categoria a qual o agente do usuário pertence. Por exemplo, o agente do usuário Conferencing_Attendant_1.0 pertence ao CAA UACategory.</p></td>
</tr>
</tbody>
</table>

