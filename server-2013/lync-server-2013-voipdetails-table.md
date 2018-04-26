---
title: 'Lync Server 2013: Tabela VoipDetails'
TOCTitle: Tabela VoipDetails
ms:assetid: 74ffbb71-569b-4018-be1f-4db2bbafcf36
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398566(v=OCS.15)
ms:contentKeyID: 49307132
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela VoipDetails no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma chamada de dois participantes na qual pelo menos um usuário utiliza VoIP.


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
<td><p>Primário</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromNumberId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p><strong>PhoneId</strong> do chamador. Consulte a <a href="lync-server-2013-phones-table.md">Tabela Phones no Lync Server 2013</a> para obter mais informações. Se não é NULL e <strong>FromGatewayId</strong> não é nulo, o chamador era um usuário PSTN.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConnectedNumberId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p><strong>PhoneId</strong> do receptor de chamada. Consulte a <a href="lync-server-2013-phones-table.md">Tabela Phones no Lync Server 2013</a> para obter mais informações. Se não é NULL e <strong>ToGatewayId</strong> não é nulo, o receptor de chamada era um usuário PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromMediationServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Mediação de onde a chamada está vindo. Consulte a <a href="lync-server-2013-mediationservers-table.md">Tabela MediationServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToMediationServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Mediação para onde vai a chamada. Consulte a <a href="lync-server-2013-mediationservers-table.md">Tabela MediationServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromGatewayId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Gateway de onde a chamada é feita. Consulte a <a href="lync-server-2013-gateways-table.md">Tabela Gateways no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToGatewayId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Gateway para onde a chamada vai. Consulte a <a href="lync-server-2013-gateways-table.md">Tabela Gateways no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DisconnectedbyURIId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI do usuário que desconectou a chamada, se o usuário tem um URI. Consulte a <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>DisconnectedbyPhoneId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A ID do telefone que desconectou a chamada foi desconectada de um telefone. Consulte a <a href="lync-server-2013-phones-table.md">Tabela Phones no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
</tbody>
</table>

