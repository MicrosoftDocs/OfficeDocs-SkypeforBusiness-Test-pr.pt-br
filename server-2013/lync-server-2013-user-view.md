---
title: Exibição do Usuário
TOCTitle: Exibição do Usuário
ms:assetid: 796f77e6-1da6-4969-b18b-3537209a1fe4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688100(v=OCS.15)
ms:contentKeyID: 49886272
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibição do Usuário

 

_**Tópico modificado em:** 2015-03-09_

A exibição de Usuário armazena informações sobre usuários envolvidos em chamadas ou sessões com registros no banco de dados. Essa exibição foi introduzida no Microsoft Lync Server 2013


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
<td><p>UserId</p></td>
<td><p>int</p></td>
<td><p>Número exclusivo que identifica este usuário.</p></td>
</tr>
<tr class="even">
<td><p>UserUri</p></td>
<td><p>nvarchar (450)</p></td>
<td><p>Uri do usuário.</p></td>
</tr>
<tr class="odd">
<td><p>TenantKey</p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Locatário do usuário. Consulte a <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>UriType</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Tipo de URI do usuário. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
</tbody>
</table>

