---
title: 'Lync Server 2013: Tabela Mcus'
TOCTitle: Tabela Mcus
ms:assetid: 271b7963-8fd8-4d92-a701-1a62aaf895ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425742(v=OCS.15)
ms:contentKeyID: 49306177
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Mcus no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Mcus é uma tabela de suporte. Cada registro armazena informações sobre um serviço de conferência, que pode ser o serviço de Conferência de IM e o serviço de Conferência com Telefonia (executados como processos em servidores front-end), bem como o serviço de Webconferência e o serviço de Conferências A/V.


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
<td><p><strong>McuId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica este servidor de conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p><strong>McuTypeId</strong></p></td>
<td><p>inyint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipo do servidor de conferência, como conf:chat (para IMs) ou conf:audio-video. Consulte <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
</tbody>
</table>

