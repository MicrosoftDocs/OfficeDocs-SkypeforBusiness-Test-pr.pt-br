---
title: 'Lync Server 2013: tblComplianceParticipant'
TOCTitle: tblComplianceParticipant
ms:assetid: 5d7e0dea-74f7-46d1-badf-b94abc8f066d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558655(v=OCS.15)
ms:contentKeyID: 49306849
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblComplianceParticipant no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblComplianceParticipant contém os participantes atuais por canal e por servidor.

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
<td><p>channelUri</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>Identificador de Recurso Uniforme do Canal (URI).</p></td>
</tr>
<tr class="even">
<td><p>userId</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade do participante (correspondente à tabela tblPrincipal.prinID).</p></td>
</tr>
<tr class="odd">
<td><p>joinedAt</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data e hora de ingresso no evento.</p></td>
</tr>
<tr class="even">
<td><p>partedAt</p></td>
<td><p>bigint</p></td>
<td><p>Nulo se o participante ainda estiver ingressado. O carimbo de data e hora de quando o canal deixa o evento se não for nulo.</p>
<p>Essas entradas são eventualmente removidas quando todos os conversores processam o evento.</p></td>
</tr>
<tr class="odd">
<td><p>userUri</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>URI do usuário.</p></td>
</tr>
<tr class="even">
<td><p>serverID</p></td>
<td><p>int</p></td>
<td><p>Identidade do servidor (como na tabela tblServerIdentity.serverID).</p></td>
</tr>
<tr class="odd">
<td><p>sessionId</p></td>
<td><p>bigint</p></td>
<td><p>Sessão do servidor. Este é um número aleatório gerado sempre que um serviço de chat é iniciado. Ele é usado para diferenciar as sessões a fim de identificar os participantes órfãos.</p></td>
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
<td><p>&lt;channelUri, userId, joinedAt&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

