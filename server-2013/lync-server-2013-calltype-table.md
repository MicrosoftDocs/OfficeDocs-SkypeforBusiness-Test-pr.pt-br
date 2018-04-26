---
title: 'Lync Server 2013: Tabela CallType'
TOCTitle: Tabela CallType
ms:assetid: a1d7187c-f851-4967-88ea-73922911ee7a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412752(v=OCS.15)
ms:contentKeyID: 49307656
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela CallType no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela CallType é uma tabela estática que armazena a lista de possíveis tipos de chamada.


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
<td><p><strong>CallTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>CallType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p>
<ul>
<li><p>0 - Desconhecido</p></li>
<li><p>1 - Mensagens instantâneas</p></li>
<li><p>2 - Compartilhamento de Aplicativos</p></li>
<li><p>3 – Áudio</p></li>
<li><p>4 - Áudio e Vídeo</p></li>
<li><p>5 - Transferência de arquivos</p></li>
</ul></td>
</tr>
</tbody>
</table>

