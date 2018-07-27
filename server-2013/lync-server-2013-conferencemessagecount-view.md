---
title: Exibir ConferenceMessageCount
TOCTitle: Exibir ConferenceMessageCount
ms:assetid: 8ee3ee95-fb78-4d4e-bcdd-6ce5a0a23b44
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688129(v=OCS.15)
ms:contentKeyID: 49886307
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir ConferenceMessageCount

 

_**Tópico modificado em:** 2015-03-09_

A exibição ConferenceMessageCount armazena informações sobre quantas mensagens foram enviadas por um usuário para uma conferência. Esta exibição foi introduzida no Microsoft Lync Server 2013.

> [!NOTE]  
> A exibição ConferenceMessageCount contém todas as colunas na <a href="lync-server-2013-conferencesessiondetails-view.md">Exibir ConferenceSessionDetails</a>, além das colunas listadas abaixo.


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
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do usuário que enviou a mensagem.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo do URI do usuário que enviou as mensagens. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Locatário do usuário que enviou as mensagens. Consulte a <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserMessageCount</strong></p></td>
<td><p>smallint</p></td>
<td><p>Número de mensagens enviadas pelo usuário durante a sessão de conferência.</p></td>
</tr>
</tbody>
</table>

