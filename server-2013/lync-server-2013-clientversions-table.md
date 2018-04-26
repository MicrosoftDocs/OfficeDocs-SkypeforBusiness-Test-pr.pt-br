---
title: 'Lync Server 2013: Tabela ClientVersions'
TOCTitle: Tabela ClientVersions
ms:assetid: 542316cf-a6db-4d52-ab28-8bf6d27a3b48
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398356(v=OCS.15)
ms:contentKeyID: 49306731
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ClientVersions no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

ClientVersions é uma tabela de suporte que armazena uma lista dos vários tipos de cliente e as versões que participaram de sessões gravadas no banco de dados. Cada registro da tabela representa uma versão de cliente.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Chave/Índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>VersionId</strong></p></td>
<td><p><strong>int</strong></p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica esse tipo de cliente e a versão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Version</strong></p></td>
<td><p><strong>nvarchar(256)</strong></p></td>
<td><p></p></td>
<td><p>Nome da versão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientType</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Especifique o tipo de cliente utilizado na sessão. Consulte o <a href="lync-server-2013-useragentdef-table.md">Tabela UserAgentDef no Lync Server 2013</a> para obter mais informações.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

