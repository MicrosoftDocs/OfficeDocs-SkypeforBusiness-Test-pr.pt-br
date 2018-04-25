---
title: 'Lync Server 2013: Tabela EndpointSubnet'
TOCTitle: Tabela EndpointSubnet
ms:assetid: d62e51d6-2117-4c41-adce-08f8d9d75ce0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398933(v=OCS.15)
ms:contentKeyID: 49308246
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela EndpointSubnet no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela EndpointSubnet é uma tabela de suporte. Cada registro representa uma subrede capturada de pontos de extremidade.


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
<td><p>Representação de inteiro para a sub-rede.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

