---
title: 'Lync Server 2013: Tabela Media'
TOCTitle: Tabela Media
ms:assetid: 1e1b427f-59b5-4564-bde5-1002a80439ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398268(v=OCS.15)
ms:contentKeyID: 49306076
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Media no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa um tipo de mídia usado em uma sessão ponto a ponto. Uma sessão será representada por vários registros na tabela se mais de um tipo de mídia for usado.

> [!NOTE]  
> A tabela de Mídia não deve ser usada para calcular a duração da mídia de uma sessão. Esta tabela contém os detalhes de sinalização da troca de mídia em uma sessão. A troca de mídia é realizada pela solicitação INVITE e StartTime indica a hora que INVITE foi enviado. O horário do convite não necessariamente significa a hora inicial da mídia, porque a mídia começa apenas após o participante aceitar a sessão. O EndTime geralmente significa a hora final desta sessão.


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
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número exclusivo identificando este tipo de mídia. Consulte <a href="lync-server-2013-medialist-table.md">Tabela MediaList no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora de início</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Este é o horário em que a solicitação de mídia foi enviada, não o horário de início de mídia real. O <strong>StartTime</strong> inclui a hora de configuração da sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Este é o horário de término da sessão.</p></td>
</tr>
</tbody>
</table>

