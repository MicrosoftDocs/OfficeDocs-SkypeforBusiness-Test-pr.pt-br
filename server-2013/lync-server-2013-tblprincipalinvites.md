---
title: 'Lync Server 2013: tblPrincipalInvites'
TOCTitle: tblPrincipalInvites
ms:assetid: 548ec156-4d1a-469d-a804-62cff226e5c2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558650(v=OCS.15)
ms:contentKeyID: 49306736
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalInvites no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O tblPrincipalInvites inclui convites para todos os usuários provisionados de todos os nós com a opção de convite automático ativada.

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
<td><p>invID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Número sequencial exclusivo (por ID de entidade) gerado a partir da tabela tblLastInviteId.</p></td>
</tr>
<tr class="odd">
<td><p>nodeID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID de nó (somente sala de chat).</p></td>
</tr>
<tr class="even">
<td><p>createdOn</p></td>
<td><p>datetime, não nulo</p></td>
<td><p>Hora da criação.</p></td>
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
<td><p>&lt;prinID, nodeID&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
<tr class="odd">
<td><p>nodeID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblNode.nodeID.</p></td>
</tr>
</tbody>
</table>

