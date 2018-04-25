---
title: 'Lync Server 2013: Tabela Roles'
TOCTitle: Tabela Roles
ms:assetid: e8eb8a10-26b5-488b-bc8c-f9ef93f98bdb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399043(v=OCS.15)
ms:contentKeyID: 49308463
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Roles no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Roles é uma tabela estática que armazena a lista de possíveis funções de conferência, como participante e apresentador.


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
<td><p><strong>RoleId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Função</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p>
<ul>
<li><p>0 - Desconhecido</p></li>
<li><p>1 - Apresentador</p></li>
<li><p>2 - Participante</p></li>
</ul></td>
</tr>
</tbody>
</table>

