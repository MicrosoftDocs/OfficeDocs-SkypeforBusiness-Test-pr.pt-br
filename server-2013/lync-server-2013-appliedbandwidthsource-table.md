---
title: 'Lync Server 2013: Tabela AppliedBandwidthSource'
TOCTitle: Tabela AppliedBandwidthSource
ms:assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425725(v=OCS.15)
ms:contentKeyID: 49306151
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AppliedBandwidthSource no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela AppliedBandwidthSource é uma tabela de suporte. Cada registro representa uma origem.


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
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica a origem.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthSource</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Essa é a origem do cap de largura de banda que está sendo imposto. Descreve de onde o limite de largura de banda está vindo (por exemplo, &quot;Política de servidor&quot;, &quot;Servidor TURN&quot; ou &quot;Modalidade&quot;).</p></td>
</tr>
</tbody>
</table>

