---
title: 'Lync Server 2013: Tabela DeviceDriver'
TOCTitle: Tabela DeviceDriver
ms:assetid: ca91a0b4-98c0-49f6-af9d-7d0f8ac75f1a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398844(v=OCS.15)
ms:contentKeyID: 49308107
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela DeviceDriver no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela DeviceDriver é uma tabela de suporte. Cada registro representa um driver usado por um dispositivo de captura ou um dispositivo de renderização.


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
<td><p><strong>DeviceDriverKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica este registro de driver de dispositivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceDriver</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>exclusivo</p></td>
<td><p>Nome do driver de dispositivo.</p></td>
</tr>
</tbody>
</table>

