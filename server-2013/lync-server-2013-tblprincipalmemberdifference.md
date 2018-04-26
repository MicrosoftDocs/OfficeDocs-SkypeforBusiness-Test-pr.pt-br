---
title: 'Lync Server 2013: tblPrincipalMemberDifference'
TOCTitle: tblPrincipalMemberDifference
ms:assetid: 0b94f555-6888-4fe0-a048-4660a2513276
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558612(v=OCS.15)
ms:contentKeyID: 49305845
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalMemberDifference no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela PrincipalMemberDifference inclui as alterações de associação a um grupo (tanto para membros adicionados como para os removidos) que ainda não foram processadas pelas etapas posteriores de Sincronização dos Serviços de Domínio Active Directory.

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
<td><p>GUID principal do grupo que mudou.</p></td>
</tr>
<tr class="even">
<td><p>memberADPath</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome distinto do membro.</p></td>
</tr>
<tr class="odd">
<td><p>memberRemoved</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Falso se o membro tiver sido adicionado. Verdadeiro se o membro tiver sido removido.</p></td>
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
<td><p>&lt;prinGuid, memberADPath&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

