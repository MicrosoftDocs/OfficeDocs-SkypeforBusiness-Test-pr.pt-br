---
title: 'Lync Server 2013: Tabela Device'
TOCTitle: Tabela Device
ms:assetid: d5a4f777-bc12-4ce8-bc0d-867d5e22b436
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398930(v=OCS.15)
ms:contentKeyID: 49308234
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Device no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Device é uma tabela de suporte que armazena informações sobre os vários dispositivos de captura ou renderização. Cada registro na tabela representa um dispositivo.


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
<td><p><strong>DeviceKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica este dispositivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>DeviceName + DeviceType é exclusivo</p></td>
<td><p>Nome do dispositivo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceType</strong></p></td>
<td><p>bit</p></td>
<td><p>DeviceName + DeviceType é exclusivo</p></td>
<td><p>Tipo de dispositivo. 1 é um dispositivo de captura, 0 é um dispositivo de processamento.</p></td>
</tr>
</tbody>
</table>

