---
title: Exibir ProgressReport
TOCTitle: Exibir ProgressReport
ms:assetid: b49f3fc7-0e2f-498f-8505-aaaf54e435f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721857(v=OCS.15)
ms:contentKeyID: 49886371
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir ProgressReport

 

_**Tópico modificado em:** 2015-03-09_

A exibição ProgressReport armazena informações sobre sessões concluídas. Os relatórios de progresso será gravados somente para chamadas e sessões que o Lync Server 2013 determina como úteis para diagnósticos. Esta exibição foi apresentada no Microsoft Lync Server 2013.

> [!NOTE]  
> Os campos ErrorTime, ErrorReportSeq e ProgressReportSeq não se referem necessariamente aos erros, mas a mensagens que indicam o status das chamadas ou mensagens.


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
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora do erro. Usada com o ErrorReportSeq para identificar um erro.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Um número de ID para identificar o erro. Usado com ErrorTime para identificar um erro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgressReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>ID para identificar o relatórios de progresso. Usado para distinguir relatórios de progresso do mesmo relatório de erro.</p></td>
</tr>
<tr class="even">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p>ID de diagnóstico do relatório de erro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Source</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Nome do servidor que originou o erro (se o relatório foi enviado de um componente do servidor).</p></td>
</tr>
<tr class="even">
<td><p><strong>Aplicativo</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Nome de um aplicativo que originou o erro (se o relatório foi enviado de um componente do servidor).</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Identificador exclusivo correlacionando as informações da hora de ingresso dos diferentes componentes envolvidos em uma conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p>Tempo (em milissegundos) necessário para que um componentes específico ingresse em uma conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagHeader</strong></p></td>
<td><p>varchar(máx)</p></td>
<td><p>Informações de erro adicionais.</p></td>
</tr>
</tbody>
</table>

