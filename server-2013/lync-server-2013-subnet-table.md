---
title: 'Lync Server 2013: Tabela Subnet'
TOCTitle: Tabela Subnet
ms:assetid: 76f5c995-96c8-4aa3-bc30-1d74991d7c42
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398582(v=OCS.15)
ms:contentKeyID: 49307157
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Subnet no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Subnet é uma tabela de suporte. Cada registro representa uma subrede definida em uma configuração de rede.


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
<td><p><strong>SubnetIP</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Representação de inteiro para o IP da sub-rede.</p></td>
</tr>
<tr class="even">
<td><p><strong>SubnetMask</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Máscara de sub-rede.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserSiteKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Referência na <a href="lync-server-2013-usersite-table.md">Tabela UserSite no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SubnetDescription</strong></p></td>
<td><p>nvarchar(512)</p></td>
<td><p></p></td>
<td><p>A descrição para a sub-rede.</p></td>
</tr>
</tbody>
</table>

