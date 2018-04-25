---
title: 'Lync Server 2013: Tabela Server'
TOCTitle: Tabela Server
ms:assetid: 9af89d08-d35a-48e8-b56d-6df292f973cc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398801(v=OCS.15)
ms:contentKeyID: 49307575
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Server no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Server é uma tabela de suporte. Cada registro representa um servidor.


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
<td><p><strong>ServerKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica o servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>FQDNOrIP</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>index</p></td>
<td><p>Cadeia de caracteres do endereço MAC.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerType</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>1: Servidor de Mediação</p>
<p>2: Servidor de Conferências de A/V16394: Serviço de Borda de A/V32769: Gateway</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolName</strong></p></td>
<td><p>nvarchar(512)</p></td>
<td><p></p></td>
<td><p>Pool ao qual o servidor pertence. Aplicável somente para o Servidor de Conferências de A/V.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

