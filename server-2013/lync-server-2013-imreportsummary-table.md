---
title: Tabela IMReportSummary no Lync Server 2013
TOCTitle: Tabela IMReportSummary no Lync Server 2013
ms:assetid: 27ff9453-53f2-4fae-b637-70a086c9df96
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204753(v=OCS.15)
ms:contentKeyID: 49306207
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela IMReportSummary no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O IMReportSummaryTable oferece um relatório geral sobre as sessões de mensagem instantânea mantidas em uma organização. Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<th>Chave/índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>StartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Data e hora que a sessão de mensagem instantânea começou.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimePeriod</strong></p></td>
<td><p>char(1)</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolFQDN</strong></p></td>
<td><p>nvarchar(257)</p></td>
<td><p>Primário</p></td>
<td><p>Nome de domínio totalmente qualificado do pool hospedando a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>AuthType</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Prioridade (por exemplo, urgente ou não urgente) da chamada. A informação de prioridade é armazenada no <a href="lync-server-2013-callpriorities-table.md">Tabela CallPriorities no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionCount</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>MsgCount</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p>Número total de mensagens instantâneas trocadas durante a sessão.</p></td>
</tr>
</tbody>
</table>

