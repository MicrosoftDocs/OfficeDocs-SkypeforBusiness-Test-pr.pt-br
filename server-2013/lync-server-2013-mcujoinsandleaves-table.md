---
title: 'Lync Server 2013: Tabela McuJoinsAndLeaves'
TOCTitle: Tabela McuJoinsAndLeaves
ms:assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398316(v=OCS.15)
ms:contentKeyID: 49306666
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela McuJoinsAndLeaves no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro nessa tabela inclui os detalhes da chamada sobre uma combinação da entrada ou saída de um usuário e o servidor de conferência. Por exemplo, se um usuário ingressar em uma conferência que inclua Webconferência e elementos de áudio/vídeo, será criado um registro para o ingresso desse usuário na Webconferência, e será criado outro para o ingresso do usuário na conferência de áudio/vídeo.


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
<td><p>Primária, estrangeira</p></td>
<td><p>Número exclusivo que identifica este usuário. Consulte a <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Se um usuário fizer logon em vários computadores ou dispositivos de uma vez, o McuUserInstance identifica exclusivamente a combinação do dispositivo do usuário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsFromPstn</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Independentemente do usuário estar ingressando a partir de uma PSTN.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuId</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número exclusivo que identifica este servidor de conferência. Consulte a <a href="lync-server-2013-mcus-table.md">Tabela Mcus no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>A hora na qual este usuário ingressa neste servidor de conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>A hora na qual este usuário deixa este servidor de conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Identificador que especifica o número da versão do software do cliente usado na conferência. Consulte <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

