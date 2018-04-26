---
title: 'Lync Server 2013: tblLastInviteId'
TOCTitle: tblLastInviteId
ms:assetid: 222b3508-5963-4ddc-b4f3-e8412767e61b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558625(v=OCS.15)
ms:contentKeyID: 49306123
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblLastInviteId no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblLastInviteId contém a última ID de convite gerada (e usada na tabela tblPrincipalInvites) para cada usuário.

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
<td><p>prinID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade.</p></td>
</tr>
<tr class="even">
<td><p>lastInviteID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do último convite usado.</p></td>
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
<td><p>prinID</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[tblPrincipalInvites no Lync Server 2013](lync-server-2013-tblprincipalinvites.md)

