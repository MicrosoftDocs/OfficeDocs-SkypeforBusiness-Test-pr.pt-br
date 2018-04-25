---
title: 'Lync Server 2013: Tabela ConferenceUris'
TOCTitle: Tabela ConferenceUris
ms:assetid: b1721d52-3c65-45ea-8997-06af8fef93fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412854(v=OCS.15)
ms:contentKeyID: 49307822
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ConferenceUris no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ConferenceUris é uma tabela de suporte que armazena uma lista de diversos URIs de conferência que participaram de sessões de conferência gravadas no banco de dados. Cada registro da tabela representa um pool.


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
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Carimbo de hora, Interno usado.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica o URI desta conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p></p></td>
<td><p>URI da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Checksum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Soma de verificação do ConferenceUri. Usado para aumentar a velocidade de pesquisas no banco de dados.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UriTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipo de URI, por exemplo, conf:chat para conferência IM ou conf:audio-video para conferência de áudio/vídeo. Consulte a tabela <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
</tbody>
</table>

