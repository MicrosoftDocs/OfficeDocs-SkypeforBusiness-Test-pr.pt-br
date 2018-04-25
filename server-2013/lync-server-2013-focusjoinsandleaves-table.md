---
title: 'Lync Server 2013: Tabela FocusJoinsAndLeaves'
TOCTitle: Tabela FocusJoinsAndLeaves
ms:assetid: e6f0212c-67e9-4061-8720-d0296e855991
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399026(v=OCS.15)
ms:contentKeyID: 49308437
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela FocusJoinsAndLeaves no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro dessa tabela contém informações de CDR sobre uma entrada de usuário e informações de saída de uma conferência. Cada conferência é representada nessa tabela por um registro para cada vez que um usuário entra de uma conferência ou sai de uma conferência.


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
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número de ID para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número exclusivo que identifica esse usuário, referenciado de <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>FocusUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Se um usuário estiver conectado em vários computadores ou dispositivos ao mesmo tempo, <strong>UserInstance</strong> será usado para identificar exclusivamente a combinação de usuário/dispositivo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsUserInternal</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Se o usuário fez logon internamente ou não.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserRole</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Função do usuário na conferência, como Apresentador ou Atendedor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>A hora de ingresso do usuário na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>A hora de saída do usuário da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Versão do software cliente do usuário, referenciado para o <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserEndpointId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>GUID (Identificador Global Exclusivo) do ponto de extremidade usado na conferência.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

