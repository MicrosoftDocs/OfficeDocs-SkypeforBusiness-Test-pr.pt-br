---
title: 'Lync Server 2013: Tabela ContentTypes'
TOCTitle: Tabela ContentTypes
ms:assetid: e3e38035-457c-4173-bdb9-d53a7420eba2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399007(v=OCS.15)
ms:contentKeyID: 49308405
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ContentTypes no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ContentTypes é uma tabela de suporte que armazena uma lista de tipos de conteúdo nas sessões ponto a ponto e de conferência. Cada registro da tabela representa um tipo de conteúdo.


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
<td><p><strong>ContentTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica o tipo de conteúdo.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td> </td>
<td><p>Nome do tipo de conteúdo.</p></td>
</tr>
</tbody>
</table>

