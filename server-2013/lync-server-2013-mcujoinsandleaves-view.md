---
title: Exibir McuJoinsAndLeaves
TOCTitle: Exibir McuJoinsAndLeaves
ms:assetid: 6f00b8e7-b8b6-4657-ac5e-d8a571806ae2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688088(v=OCS.15)
ms:contentKeyID: 49886258
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir McuJoinsAndLeaves

 

_**Tópico modificado em:** 2015-03-09_

A exibição McuJoinsAndLeaves armazena informações sobre ingresso e saída de usuários de um servidor de conferências. Cada registro nessa exibição inclui os detalhes da chamada sobre uma combinação da entrada ou saída de um usuário e o servidor de conferência. Essa exibição foi introduzida no Microsoft Lync Server 2013.


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
<td><p>Hora da instância da conferência. Usada em conjunto com SessionIdSeq para identificar uma instância da conferência de maneira exclusiva. Consulte a <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Número de ID para identificar a instância da conferência. Usada em conjunto com SessionIdTime para identificar uma instância da conferência de maneira exclusiva. Consulte a <a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>McuUri</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URI do servidor de conferências ao qual o usuário está conectado.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URI do servidor de conferências ao qual o usuário está conectado. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo de URI do usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Locatário do usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas. Consulte a <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Versão do cliente usado pelo usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientType</strong></p></td>
<td><p>int</p></td>
<td><p>Cliente usado pelo usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas. Consulte a <a href="lync-server-2013-useragentdef-table.md">Tabela UserAgentDef no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>Nome da categoria do cliente usado pelo usuário cujas informações de ingresso/saída do servidor de conferências foram capturadas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>McuUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p>Identificador exclusivo da combinação de usuário/dispositivo para usuários que fizeram logon simultâneo em vários dispositivos.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsUserFromPstn</strong></p></td>
<td><p>bit</p></td>
<td><p>Bit que representa se o usuário é interno ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora da solicitação de sessão. Usada em conjunto com SessionIdSeq para identificar uma sessão de maneira exclusiva. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Número de ID para identificar a sessão. Usada em conjunto com SessionIdTime para identificar uma sessão de maneira exclusiva. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>ID de diálogo SIP da sessão. O formato é: diálogo;de-marca;para-marca.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora em que o usuário ingressou no servidor de conferências.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora em que o usuário saiu do servidor de conferências.</p></td>
</tr>
</tbody>
</table>

