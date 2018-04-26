---
title: 'Lync Server 2013: Tabela Devices'
TOCTitle: Tabela Devices
ms:assetid: 532e2280-4bbc-4a6c-93da-45d9f80a30a0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398351(v=OCS.15)
ms:contentKeyID: 49306717
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Devices no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela de Dispositivos é uma tabela de suporte. Cada registro armazena informações sobre um dispositivo (telefone de mesa).


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
<td><p><strong>DeviceId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica a versão de hardware.</p></td>
</tr>
<tr class="even">
<td><p><strong>ManufacturerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Fabricante do dispositivo. Consulte <a href="lync-server-2013-manufacturers-table.md">Tabela Manufacturers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HardwareVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Versão de hardware deste dispositivo. Consulte <a href="lync-server-2013-hardwareversions-table.md">Tabela HardwareVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>MacAddress</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p>Endereço MAC</p></td>
</tr>
</tbody>
</table>

