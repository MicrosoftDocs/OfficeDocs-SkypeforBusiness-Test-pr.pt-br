---
title: 'Lync Server 2013: Tabela de servidores'
TOCTitle: Tabela de servidores
ms:assetid: 1535e676-a647-4606-bc56-e8bfde5ca823
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398223(v=OCS.15)
ms:contentKeyID: 49305999
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela de servidores no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Servers é uma tabela de suporte que armazena informações sobre os vários servidores. Cada registro na tabela representa um servidor.


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
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo de identificação desse servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>ServerFQDN</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>FQDN do servidor.</p></td>
</tr>
</tbody>
</table>

