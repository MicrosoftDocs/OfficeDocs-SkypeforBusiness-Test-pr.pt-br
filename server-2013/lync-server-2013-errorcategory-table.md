---
title: Tabela ErrorCategory no Lync Server 2013
TOCTitle: Tabela ErrorCategory no Lync Server 2013
ms:assetid: 0fde3b73-9a2f-44dd-b8dc-6df512303ff1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204675(v=OCS.15)
ms:contentKeyID: 49305903
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ErrorCategory no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ErrorCategory contém o nome amigável para cada classificação de diagnóstico do Microsoft Lync Server 2013. Por padrão, o Lync Server 2013 usa as seguintes classificações:

  - 0 -- Sucesso

  - 1 -- Falha esperada

  - 2 – Falha inesperada

Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<th>Chave/índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>CategoryId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primária</p></td>
<td><p>Identificador único para a classificação.</p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>nvarchar (256)</p></td>
<td><p></p></td>
<td><p>Valor e nome amigável atribuídos à classificação. Os valores permitidos são:</p>
<ul>
<li><p>0 -- Sucesso</p></li>
<li><p>1 -- Falha esperada</p></li>
<li><p>2 – Falha inesperada</p></li>
</ul></td>
</tr>
</tbody>
</table>

