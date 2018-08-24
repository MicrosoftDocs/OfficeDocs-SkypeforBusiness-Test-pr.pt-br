---
title: Exibir Media
TOCTitle: Exibir Media
ms:assetid: 1a7b2e59-082e-4188-98ae-48ae9bd3494a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687981(v=OCS.15)
ms:contentKeyID: 49886119
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Media

 

_**Tópico modificado em:** 2015-03-09_

A exibição de mídia armazena informações sobre um tipo de mídia usado em uma sessão ponto a ponto. Uma sessão será representada por vários registros na tabela caso mais de um tipo de mídia seja usado. Essa exibição foi introduzida no Microsoft Lync Server 2013.

> [!NOTE]  
> A exibição de mídia não deve ser usada para calcular a duração de mídia para uma sessão. Essa exibição contém os detalhes de sinalização da troca de mídia em uma sessão. A troca de mídia é feita pela solicitação INVITE, e o StartTime indica o horário em que o INVITE foi enviado. O horário de convite não significa, necessariamente, o horário de início da mídia, pois a mídia só começa depois que a sessão tenha sido aceita.

A exibição de mídia contém todas as colunas do [Exibir SessionDetails](lync-server-2013-sessiondetails-view.md) além das listadas abaixo.


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
<td><p><strong>Mídia</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Tipo de mídia. Consulte <a href="lync-server-2013-medialist-table.md">Tabela MediaList no Lync Server 2013</a> para obter maiores informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediaStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Horário em que a solicitação de mídia foi enviada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Horário de término da sessão.</p></td>
</tr>
</tbody>
</table>

