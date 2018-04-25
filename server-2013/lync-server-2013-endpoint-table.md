---
title: 'Lync Server 2013: Tabela Endpoint'
TOCTitle: Tabela Endpoint
ms:assetid: 500f330d-4d7d-4e88-b1cc-fef9a9de6b5c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398327(v=OCS.15)
ms:contentKeyID: 49306687
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Endpoint no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela de Pontos de Extremidade é uma tabela de suporte que armazena informações sobre os pontos de extremidade que participaram de sessões registradas no banco de dados. Cada registro da tabela representa um ponto de extremidade.


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
<td><p><strong>EndpointKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica este ponto de extremidade.</p></td>
</tr>
<tr class="even">
<td><p><strong>Nome</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Nome do ponto de extremidade.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SO</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p> </p></td>
<td><p>Sistema operacional (SO) do ponto de extremidade.</p></td>
</tr>
<tr class="even">
<td><p><strong>CPUName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p></p></td>
<td><p>Nome da CPU do ponto de extremidade.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPUNumberOfCores</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Número de núcleos de CPU do ponto de extremidade.</p></td>
</tr>
<tr class="even">
<td><p><strong>CPUProcessorSpeed</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Velocidade do processador da CPU do ponto de extremidade.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VirtualizationFlag</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Sinalizador de bit que indica se o sistema está sendo executado em um ambiente virtualizado:</p>
<ul>
<li><p>0x0000 - Nenhum</p></li>
<li><p>0x0001 - HyperV</p></li>
<li><p>0x0002 - VMWare</p></li>
<li><p>0x0004 - Virtual PC</p></li>
<li><p>0x0008 - Xen PC</p></li>
</ul></td>
</tr>
</tbody>
</table>

