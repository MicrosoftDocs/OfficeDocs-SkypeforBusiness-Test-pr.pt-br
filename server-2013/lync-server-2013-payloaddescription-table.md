---
title: 'Lync Server 2013: Tabela PayloadDescription'
TOCTitle: Tabela PayloadDescription
ms:assetid: c49d61c0-305a-4770-a5d2-5d9f05decc6d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412971(v=OCS.15)
ms:contentKeyID: 49308040
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela PayloadDescription no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela PayloadDescription é uma tabela de suporte. Cada registro representa um Codec, que é usado em uma sessão de áudio ou de vídeo.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Coluna</strong></th>
<th><strong>Tipo de dados</strong></th>
<th><strong>Chave/Índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PayloadDescriptionKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica o Codec.</p></td>
</tr>
<tr class="even">
<td><p><strong>PayloadDescription</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Nome do codec.</p></td>
</tr>
</tbody>
</table>

