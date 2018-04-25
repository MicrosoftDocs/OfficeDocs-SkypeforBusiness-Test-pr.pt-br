---
title: 'Lync Server 2013: tblADUpdates'
TOCTitle: tblADUpdates
ms:assetid: ba19fa16-4d2d-4635-ac32-f93e09469546
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615033(v=OCS.15)
ms:contentKeyID: 49307912
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblADUpdates no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela tblADUpdates contém alterações de Serviços de Domínio Active Directory que ainda não foram processadas pelas etapas posteriores de Sincronização do Active Directory.

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
<td><p>prinGuid</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUID da entidade do objeto que mudou.</p></td>
</tr>
<tr class="even">
<td><p>prinADPath</p></td>
<td><p>nvarchar (384), não nulo</p></td>
<td><p>Nome distinto do objeto.</p></td>
</tr>
<tr class="odd">
<td><p>prinAttributesChanged</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se pelo menos um atributo do objeto tiver mudado.</p></td>
</tr>
<tr class="even">
<td><p>prinMembersChanged</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se a associação tiver sido alterada.</p></td>
</tr>
<tr class="odd">
<td><p>prinAffiliationsChanged</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Não usado.</p></td>
</tr>
<tr class="even">
<td><p>prinDeleted</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se o objeto tiver sido excluído.</p></td>
</tr>
<tr class="odd">
<td><p>lastUpdated</p></td>
<td><p>datetime, não nulo</p></td>
<td><p>Carimbo de hora de quando a linha foi inserida.</p></td>
</tr>
</tbody>
</table>

