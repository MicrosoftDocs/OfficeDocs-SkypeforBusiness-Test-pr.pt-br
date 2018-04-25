---
title: 'Lync Server 2013: Tabela ProgressReport'
TOCTitle: Tabela ProgressReport
ms:assetid: 38e5f060-5e9b-4185-87b2-7ef61c4bb75f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425864(v=OCS.15)
ms:contentKeyID: 49306420
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ProgressReport no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Relatórios de andamento são baseados nos dados carregados pelo cliente no banco de dados após a conclusão de uma chamada ou sessão. Os relatórios de andamento serão gravados apenas para chamadas e sessões que o Lync Server 2013 determinar úteis para fins de diagnóstico.

Os campos ErrorTime, ErrorReportSeq e ProgressReportSeq não se referem necessariamente aos erros, mas a mensagens que indicam o status das chamadas ou mensagens.


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
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Data e hora do relatório de erros de andamento. Consulte a <a href="lync-server-2013-errorreport-table.md">Tabela ErrorReport no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número de ID usado junto com o ErrorTime, ProgressReportSeq para identificar exclusivamente um relatório de andamento. Consulte a <a href="lync-server-2013-errorreport-table.md">Tabela ErrorReport no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número de ID que identifica o relatório de erros. O ErrorReporSeq é usado em conjunto com o ErrorTime para identificar exclusivamente um relatório de erros. Consulte o <a href="lync-server-2013-errorreport-table.md">Tabela ErrorReport no Lync Server 2013</a> para obter mais informações</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgressReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número de ID para identificar o relatório de andamento. Usado junto com ErrorTime e ErrorReportSeq para identificar exclusivamente um relatório de andamento.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>ID do diagnóstico do relatório de andamento.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Servidor que enviou o relatório de erros (se o relatório foi enviado de um componente do servidor), Consulte a <a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a> para obter mais informações. Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>O processo do Lync Server do qual o relatório trata. Consulte a Application Table para obter mais informações</p></td>
</tr>
<tr class="even">
<td><p><strong>Detalhe</strong></p></td>
<td><p>imagem</p></td>
<td><p></p></td>
<td><p>Detalhes do relatório de andamento armazenados em formato binário para economizar espaço. Esses dados podem ser convertidos em formato de texto usando essa sintaxe:</p>
<p>cast(cast(Detail as varbinary(max)) as varchar(max))</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>Identificador exclusivo que correlaciona as informações da hora de ingresso com os diferentes componentes envolvidos em uma conferência.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Tempo (em milissegundos) para que um componente específico ingresse em uma conferência.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

