---
title: 'Lync Server 2013: tblPrincipalAffiliations'
TOCTitle: tblPrincipalAffiliations
ms:assetid: 45fd8484-5837-44d2-85bb-45c83546607c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558642(v=OCS.15)
ms:contentKeyID: 49306566
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalAffiliations no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O tblPrincipalAffiliations inclui as principais afiliações que descrevem as associações em locais, incluindo grupos de segurança do Serviços de Domínio Active Directory, contêineres do Active Directory e domínios.

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
<td><p>principalID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade de segurança afiliada.</p></td>
</tr>
<tr class="even">
<td><p>affiliationID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade de segurança que representa a afiliação. Cada entidade (exceto system-user-types) tem também uma autoafiliação.</p></td>
</tr>
<tr class="odd">
<td><p>index</p></td>
<td><p>int, não nulo</p></td>
<td><p>Índice. O valor para autoafiliações é -1 e para as outras afiliações ele aumenta sequencialmente em 1 em cada classificação de &lt;principalID, affiliationId&gt;.</p></td>
</tr>
<tr class="even">
<td><p>updatedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>Entidade de segurança que fez a atualização mais recente. Isso geralmente é 1, o que significa Sincronização do Active Directory.</p></td>
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
<th>Colunas</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;principalID, index, affiliationID&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>principalID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
<tr class="odd">
<td><p>affiliationID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>

