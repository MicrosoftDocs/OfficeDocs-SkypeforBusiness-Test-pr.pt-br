---
title: 'Lync Server 2013: tblLastChatId'
TOCTitle: tblLastChatId
ms:assetid: 17a4ffbe-cca9-4ec5-ae46-38a15274889a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558616(v=OCS.15)
ms:contentKeyID: 49306007
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblLastChatId no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblLastChatId inclui a última ID de chat que foi gerada (e usada na tabela tblChat) para cada usuário.

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
<td><p>nodeID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID de nó (apenas para tipo de sala de chat).</p></td>
</tr>
<tr class="even">
<td><p>lastChatID</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Último ID de chat usado.</p></td>
</tr>
</tbody>
</table>


### Chaves

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
<td><p>&lt;nodeID, lastChatID&gt;</p></td>
<td><p>Chave primária (apenas o nodeID é suficiente para o processamento).</p></td>
</tr>
<tr class="even">
<td><p>nodeID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblNode.nodeID.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[tblChat no Lync Server 2013](lync-server-2013-tblchat.md)

