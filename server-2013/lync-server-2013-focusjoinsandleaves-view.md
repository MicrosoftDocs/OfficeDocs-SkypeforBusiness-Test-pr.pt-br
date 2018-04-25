---
title: Exibir FocusJoinsAndLeaves
TOCTitle: Exibir FocusJoinsAndLeaves
ms:assetid: 226460ef-766f-4d61-80cb-f332b65a210d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687992(v=OCS.15)
ms:contentKeyID: 49886133
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir FocusJoinsAndLeaves

 

_**Tópico modificado em:** 2015-03-09_

O FocusJoinsAndLeaves exibe informações de repositórios sobre a informação de participação e saída de uma conferência. Cada conferência é representada nesta exibição por um registro gravado cada vez que um usuário participar ou deixar a conferência. Esta exibição foi introduzida no Microsoft Lync Server 2013.


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
<td><p>Tempo da instância da conferência. Usado em conjunto com SessionIdSeq para identificar exclusivamente uma instância da conferência. Consulte a <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Número de ID para identificar a instância da conferência. Usado em conjunto com SessionIdTime para identificar exclusivamente uma instância de conferência. Consulte a <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do usuário cuja informação de participação/saída da conferência foi capturada.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo de URI do usuário cuja informação de participação/saída da conferência foi capturada. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Inquilino do usuário cuja informação de participação/saída da conferência foi capturada. Consulte a <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserEndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Identificador exclusivo do usuário cuja informação de participação/saída da conferência foi capturada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Versão do cliente usado pelo usuário cuja informação de participação/saída da conferência foi capturada.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientType</strong></p></td>
<td><p>int</p></td>
<td><p>Cliente usado pelo usuário cuja informação de participação/saída da conferência foi capturada. Consulte a <a href="lync-server-2013-useragentdef-table.md">Tabela UserAgentDef no Lync Server 2013</a> para obter mais detalhes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>Nome da categoria do cliente utilizado pelo usuário cuja informação de participação/saída da conferência foi capturada.</p></td>
</tr>
<tr class="even">
<td><p><strong>FocusUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>IsuserInternal</strong></p></td>
<td><p>bit</p></td>
<td><p>Bit que representa se o usuário é interno ou não.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Tempo da solicitação da sessão. Usado em conjunto com SessionIdSeq para identificar exclusivamente uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Se um usuário está conectado em vários computadores ou dispositivos ao mesmo tempo, UserInstance é utilizado para identificar exclusivamente a combinação de usuário/dispositivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>ID de diálogo SIP da sessão. O formato é: diálogo;da-tag;para-tag.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora que o usuário entrou na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora que o usuário saiu da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserRole</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Função do usuário na conferência, como Apresentador ou Participante.</p></td>
</tr>
</tbody>
</table>

