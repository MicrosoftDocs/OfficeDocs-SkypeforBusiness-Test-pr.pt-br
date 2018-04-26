---
title: 'Lync Server 2013: Tabela ConferenceMessageCount'
TOCTitle: Tabela ConferenceMessageCount
ms:assetid: 78569dbf-5217-42fa-ba1a-4380f56e2a3d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398590(v=OCS.15)
ms:contentKeyID: 49307175
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ConferenceMessageCount no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro dessa tabela representa um usuário em uma conferência de IM e inclui o número de mensagens enviadas por esse usuário. Cada conferência é representada por vários registros dessa tabela; um registro para cada usuário.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Hora da instância da conferência. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma instância de conferência. Consulte <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número de ID para identificar a instância da conferência. Usado em conjunto com <strong>SessionIdTime</strong> para identificar exclusivamente uma instância de conferência. Consulte <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número exclusivo que identifica esse usuário, referenciado de <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>MessageCount</strong></p></td>
<td><p>smallint</p></td>
<td><p> </p></td>
<td><p>O número de mensagens enviadas por esse usuário durante esta conferência.</p></td>
</tr>
</tbody>
</table>

