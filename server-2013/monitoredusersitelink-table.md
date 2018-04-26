---
title: Tabela MonitoredUserSiteLink
TOCTitle: Tabela MonitoredUserSiteLink
ms:assetid: 16edc24a-2718-4bb4-b05c-bc7aafa97963
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398233(v=OCS.15)
ms:contentKeyID: 49306006
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MonitoredUserSiteLink

 

_**Tópico modificado em:** 2015-03-09_

MonitoredUserSiteLink é uma tabela de suporte. Cada registro representa um link entre dois locais de usuários.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Coluna</strong></th>
<th><strong>Tipo de dados</strong></th>
<th><strong>Chave/Índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>UserSite1Key</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Referência na <a href="lync-server-2013-usersite-table.md">Tabela UserSite no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserSite2Key</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Referenciado de <a href="lync-server-2013-usersite-table.md">Tabela UserSite no Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>

