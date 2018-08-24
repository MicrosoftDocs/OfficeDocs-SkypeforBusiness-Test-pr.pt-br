---
title: Exibir VoIPDetails
TOCTitle: Exibir VoIPDetails
ms:assetid: 14c44736-71ba-4fc5-82c7-1df65bf6261c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687973(v=OCS.15)
ms:contentKeyID: 49886109
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir VoIPDetails

 

_**Tópico modificado em:** 2015-03-09_

O modo de exibição VoIPDetails armazena informações sobre sessões ponto a ponto, onde no mínimo um usuário é um usuário VoIP. Este modo de exibição foi introduzido no Microsoft Lync Server 2013.

> [!NOTE]  
> O modo de exibição VoIPDetails contém todas as colunas do <a href="lync-server-2013-sessiondetails-view.md">Exibir SessionDetails</a> além das colunas listadas abaixo.


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
<td><p><strong>FromPhone</strong></p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do telefone do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToPhone</strong></p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do telefone do usuário que entrou na sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DisconnectedByUri</strong></p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do usuário que desconectou da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>DisconnectedByUriType</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Tipo da URI do usuário que desconectou da sessão. Consulte a <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DisconnectedByTenant</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Locatário do usuário que desconectou da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>DisconnectedByPhone</strong></p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do telefone do usuário que desconectou da sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromMediationServer</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Servidor de Mediação usado pelo usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToMediationServer</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Servidor de Mediação usado pelo usuário que entrou na sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromGateway</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Gateway usado pelo usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToGateway</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Gateway usado pelo usuário que entrou na sessão.</p></td>
</tr>
</tbody>
</table>

