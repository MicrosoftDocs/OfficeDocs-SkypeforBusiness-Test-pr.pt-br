---
title: "Lync Server 2013: Lista de tabelas de conform. do Servidor de Chat Persist."
TOCTitle: Lista de tabelas de conformidade do Servidor de Chat Persistente
ms:assetid: 8563446e-90cc-47cc-8a8e-4883decfe195
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215878(v=OCS.15)
ms:contentKeyID: 49307341
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de tabelas de conformidade do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O esquema de conformidade do banco de dados do Chat Persistente é composto pelas tabelas mencionadas a seguir.

## Lista de tabelas de conformidade do Servidor de Chat Persistente


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblcompliancedata.md">tblComplianceData no Lync Server 2013</a></p></td>
<td><p>Contém eventos de conformidade que ainda não foram processados pelo adaptador configurado.</p>
<p>Esta tabela inclui eventos relacionados ao Chat Persistente, como mensagens de chat e downloads de arquivos (os eventos participantes são acompanhados por meio da tabela tblComplianceParticipant).</p>
<p>Os servidores que processaram os eventos dessa tabela estão listados na tabela tblComplianceFanout.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblcompliancefanout.md">tblComplianceFanout no Lync Server 2013</a></p></td>
<td><p>Contém os servidores que processaram um evento de conformidade. Esta tabela está diretamente relacionada à tabela tblComplianceData.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblcomplianceparticipant.md">tblComplianceParticipant no Lync Server 2013</a></p></td>
<td><p>Contém os participantes atuais por serviço de chat e por servidor. Ela é mantida com base nos eventos de conformidade de ingresso e participação do serviço Chat Persistente.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblcompliancestate.md">tblComplianceState no Lync Server 2013</a></p></td>
<td><p>Contém informações sobre o estado de conformidade de todo o pool.</p></td>
</tr>
</tbody>
</table>

