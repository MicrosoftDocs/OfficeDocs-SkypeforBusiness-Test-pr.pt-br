---
title: 'Lync Server 2013: Tabela MacAddress'
TOCTitle: Tabela MacAddress
ms:assetid: a32e68c5-3f95-4217-aff4-cb3d1cc70505
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412761(v=OCS.15)
ms:contentKeyID: 49307676
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MacAddress no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela MacAddress é uma tabela de suporte. Cada registro representa uma origem.


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
<td><p><strong>MacAddressKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica o endereço Mac.</p></td>
</tr>
<tr class="even">
<td><p><strong>MacAddress</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Cadeia de caracteres do endereço Mac.</p></td>
</tr>
</tbody>
</table>

