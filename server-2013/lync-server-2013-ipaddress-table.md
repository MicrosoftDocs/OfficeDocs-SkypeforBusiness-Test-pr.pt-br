---
title: Tabela IPAddress no Lync Server 2013
TOCTitle: Tabela IPAddress no Lync Server 2013
ms:assetid: 8ec018b9-158e-4bbe-ad46-869e60315555
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205077(v=OCS.15)
ms:contentKeyID: 49307422
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela IPAddress no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela IPAddress mapeia endereços IP a identificadores de endereço IP exclusivos usados em outras partes do banco de dados de Qualidade de Experiência. Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<td><p><strong>IPAddressKey</strong>,</p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo do endereço de IP especificado.</p></td>
</tr>
<tr class="even">
<td><p><strong>IPAddress</strong></p></td>
<td><p>varchar(50)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Endereço de IP exclusivo (por exemplo, 189.168.1.1) que mapeia para IpAddressKey. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
</tbody>
</table>

