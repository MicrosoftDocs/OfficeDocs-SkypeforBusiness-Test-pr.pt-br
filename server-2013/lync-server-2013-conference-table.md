---
title: 'Lync Server 2013: Tabela Conference'
TOCTitle: Tabela Conference
ms:assetid: 2a2c327c-4719-42dc-a3bb-6dbc0864d9af
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425762(v=OCS.15)
ms:contentKeyID: 49306205
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Conference no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela de Conferência é uma tabela de suporte. Cada registro representa uma conferência ou sessão ponto a ponto.


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
<td><p><strong>ConferenceKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica o registro desta conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConfURI</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>exclusivo</p></td>
<td><p>URI de Conferência é uma conferência, ou DialogID se é uma sessão peer-to-peer.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Checksum</strong></p></td>
<td><p>int</p></td>
<td><p>index</p></td>
<td><p>Soma de verificação do URI de conferência. Isso é usado internamente.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

