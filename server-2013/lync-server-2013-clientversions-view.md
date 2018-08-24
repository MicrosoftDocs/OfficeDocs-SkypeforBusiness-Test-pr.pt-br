---
title: Exibir ClientVersions
TOCTitle: Exibir ClientVersions
ms:assetid: caf7678f-83a0-46c8-83cc-fee4c3991f52
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721891(v=OCS.15)
ms:contentKeyID: 49886410
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir ClientVersions

 

_**Tópico modificado em:** 2015-03-09_

A exibição ClientVersions armazena informações sobre os vários tipos de cliente e versões que participaram de sessões gravadas no banco de dados. Cada registro na exibição representa uma versão do cliente. Esta exibição foi introduzida no Microsoft Lync Server 2013.

> [!NOTE]  
> Pode haver vários registros para determinadas colunas.


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
<td><p><strong>VersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Número exclusivo que identifica esse tipo de cliente e a versão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Version</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Representa o agente do usuário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientType</strong></p></td>
<td><p>int</p></td>
<td><p>Tipo de cliente.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>Categoria na qual o cliente pertence. Por exemplo, o cliente Conferencing_Attendant_1.pertence ao CAA ClientCategory.</p></td>
</tr>
</tbody>
</table>

