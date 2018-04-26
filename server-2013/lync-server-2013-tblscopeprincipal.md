---
title: 'Lync Server 2013: tblScopePrincipal'
TOCTitle: tblScopePrincipal
ms:assetid: 422d6c7f-7ba7-4dd4-bacc-95ace47959ff
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558639(v=OCS.15)
ms:contentKeyID: 49306531
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblScopePrincipal no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblScopePrincipal inclui os escopos atribuídos aos nós.

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
<td><p>scopeNodeID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Identificação do nó ao qual o escopo se aplica.</p></td>
</tr>
<tr class="even">
<td><p>scopePrinID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade.</p></td>
</tr>
<tr class="odd">
<td><p>scopeIsDenied</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se o tipo de escopo for Negar; falso se for Permitir.</p></td>
</tr>
<tr class="even">
<td><p>scopeUpdatedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade que atualizou pela última vez essa entrada.</p></td>
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
<td><p>&lt;scopeNodeID, scopePrinID&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>scopeNodeID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblNode.nodeID.</p></td>
</tr>
<tr class="odd">
<td><p>scopePrinID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>

