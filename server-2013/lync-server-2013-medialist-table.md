---
title: 'Lync Server 2013: Tabela MediaList'
TOCTitle: Tabela MediaList
ms:assetid: 1f440590-c1bc-483e-b7bc-6cc763847768
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398279(v=OCS.15)
ms:contentKeyID: 49306086
ms.date: 07/13/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MediaList no Lync Server 2013

 

_**Tópico modificado em:** 2016-07-12_

MediaList é uma tabela estática que armazena a lista de vários tipos de mídia.


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
<td><p><strong>MediaId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Media</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p>
<ul>
<li><p>1 – IM</p></li>
<li><p>2 – Transferência de arquivos</p></li>
<li><p>3 – Assistência Remota</p></li>
<li><p>4 – Compartilhamento de Aplicativos</p></li>
<li><p>5 – Áudio</p></li>
<li><p>6 – Vídeo</p></li>
<li><p>7 – Convite do Aplicativo</p></li>
</ul></td>
</tr>
</tbody>
</table>

