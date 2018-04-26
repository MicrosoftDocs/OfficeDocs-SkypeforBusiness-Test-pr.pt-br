---
title: 'Lync Server 2013: Tabela Pool'
TOCTitle: Tabela Pool
ms:assetid: 92ded8fd-d0ad-4f8a-9e6f-2e8a690fda3a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398746(v=OCS.15)
ms:contentKeyID: 49307484
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Pool no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Pool é uma tabela de suporte que armazena informações sobre os diversos pools de Front-Ends. Cada registro da tabela representa um pool.


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
<td><p><strong>PoolKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica este pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Exclusivo </p></td>
<td><p>FQDN do pool.</p></td>
</tr>
</tbody>
</table>

