---
title: Exibir Conferências
TOCTitle: Exibir Conferências
ms:assetid: c0e5c4db-c135-401f-9296-e9a49f6499a1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721871(v=OCS.15)
ms:contentKeyID: 49886389
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Conferências

 

_**Tópico modificado em:** 2015-03-09_

A Exibição de Conferências armazena informações sobre as conferências. Esta exibição foi introduzida no Microsoft Lync Server 2013.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com SessionIdSeq para identificar exclusivamente uma sessão. Consulte o <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Número da ID para identificar a sessão. Usado em conjunto com SessionIdTime para identificar exclusivamente uma sessão. Consulte o <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo da URI de conferência. Consulte o <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConfInstance</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Usado para conferências recorrentes. Cada instância de uma conferência recorrente possui o mesmo ConferenceUri, mas um ConfInstance diferente.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora inicial da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora final da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>OrganizerUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do usuário que organizou a conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OrganizerType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo de URI do usuário que organizou a conferência. Consulte o <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>OrganizerTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Inquilino do usuário que organizou a conferência. Consulte o <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome de domínio totalmente qualificado do pool que hospeda a conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p>Máscara de bits que contém os Atributos de Conferência. Os possíveis valores são:</p>
<p>0X01 – Transação Sintética</p></td>
</tr>
</tbody>
</table>

