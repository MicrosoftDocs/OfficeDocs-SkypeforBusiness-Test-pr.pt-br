---
title: Ver Session
TOCTitle: Ver Session
ms:assetid: 49e33f5b-45d0-4146-a5a4-76954d895a98
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688048(v=OCS.15)
ms:contentKeyID: 49886209
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ver Session

 

_**Tópico modificado em:** 2015-03-09_

O Modo de exibição do servidor armazena informações sobre sessões que foram registradas no banco de dados. Esta visualização foi introduzida no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dado</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ConferenceDateTime</p></td>
<td><p>datetime</p></td>
<td><p>Referenciado da tabela MediaLine.</p></td>
</tr>
<tr class="even">
<td><p>ConferenceURI</p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI de Conferência é uma conferência, ou DialogID se é uma sessão peer-to-peer.</p></td>
</tr>
<tr class="odd">
<td><p>Correlação</p></td>
<td><p>varchar(max)</p></td>
<td><p>ID de correlação da sessão.</p></td>
</tr>
<tr class="even">
<td><p>DialogCategory</p></td>
<td><p>bit</p></td>
<td><p>Categoria do diálogo; 0 é Lync Server para a perna do Servidor de Mediação; 1 para o Servidor de Mediação para a perna do gateway PSTN.</p></td>
</tr>
<tr class="odd">
<td><p>MediationServerBypassFlag</p></td>
<td><p>bit</p></td>
<td><p>Indica se uma ligação foi ou não ignorada.</p></td>
</tr>
<tr class="even">
<td><p>MediaBypassWarningFlag</p></td>
<td><p>int</p></td>
<td><p>Caso presente, este campo indica o motivo de uma chamada não ter sido ignorada, mesmo se as IDs de bypass correspondessem. Para Lync Server, apenas um valor é definido:</p>
<p>0x0001 – ID de bypass desconhecido para o adaptador de rede padrão</p></td>
</tr>
<tr class="odd">
<td><p>StartTime</p></td>
<td><p>datetime</p></td>
<td><p>Hora do início da chamada.</p></td>
</tr>
<tr class="even">
<td><p>EndTime</p></td>
<td><p>datetime</p></td>
<td><p>Hora da finalização da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CallerPool</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Pool FQDN do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CalleePool</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Pool FQDN do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallerPAI</p></td>
<td><p>nvarchar(450)</p></td>
<td><p>Identidade URI declarada p do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CalleePAI</p></td>
<td><p>nvarchar(450)</p></td>
<td><p>Identidade URI declarada p do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallerEndpoint</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome de ponto de extremidade do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CalleeEndpoint</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome de ponto de extremidade do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerUserAgent</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>String do agente de usuário do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerUserAgentType</p></td>
<td><p>smallint</p></td>
<td><p>Tipo de agente de usuário do chamador. Consulte <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a> para detalhes.</p></td>
</tr>
<tr class="odd">
<td><p>CallerUserAgentCategory</p></td>
<td><p>nvarchar (64)</p></td>
<td><p>Categoria do agente de usuário do chamador. Consulte o <a href="lync-server-2013-useragentdef-table-qoe.md">Tabela UserAgentDef (QoE) no Lync Server 2013</a> para detalhes.</p></td>
</tr>
<tr class="even">
<td><p>CalleeUserAgent</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>String de agente de usuário do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeUserAgentType</p></td>
<td><p>smallint</p></td>
<td><p>Tipo de agente de usuário para o receptor. Consulte <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a> para detalhes.</p></td>
</tr>
<tr class="even">
<td><p>CalleeUserAgentCategory</p></td>
<td><p>nvarchar (64)</p></td>
<td><p>Categoria do agente de usuário para o receptor. Consulte <a href="lync-server-2013-useragentdef-table-qoe.md">Tabela UserAgentDef (QoE) no Lync Server 2013</a> para detalhes.</p></td>
</tr>
<tr class="odd">
<td><p>CallerURI</p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CalleeURI</p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallPrioirty</p></td>
<td><p>int</p></td>
<td><p>Prioridade da chamada.</p></td>
</tr>
</tbody>
</table>

