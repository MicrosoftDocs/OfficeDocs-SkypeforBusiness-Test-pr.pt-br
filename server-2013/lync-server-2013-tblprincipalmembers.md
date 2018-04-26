---
title: 'Lync Server 2013: tblPrincipalMembers'
TOCTitle: tblPrincipalMembers
ms:assetid: 9a3e24cf-6ef7-4b82-99fc-50ba41800b6f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615022(v=OCS.15)
ms:contentKeyID: 49307570
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalMembers no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblPrincipalMembers contém associações de entidade.

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
<td><p>memberADPath</p></td>
<td><p>nvarchar (384), não nulo</p></td>
<td><p>Nome diferenciado de um membro. Um membro não precisa ser uma entidade (na tabela tblPrincipal).</p></td>
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
<td><p>&lt;prinID, memberADPath&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Chave estrangeira com pesquisa em tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>

