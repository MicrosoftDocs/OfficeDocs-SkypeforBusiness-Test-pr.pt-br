---
title: 'Lync Server 2013: Tabela SessionCorrelation'
TOCTitle: Tabela SessionCorrelation
ms:assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398091(v=OCS.15)
ms:contentKeyID: 49305711
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela SessionCorrelation no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

SessionCorrelation é uma tabela de suporte. Cada registro representa uma CorrelationID usada para correlacionar várias sessões.


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
<td><p><strong>Checksum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>CorrelationKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo identificando este Servidor de Conferência A/V.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CorrelationID</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Sessões que são correlacionadas terão o mesmo ID de correlação.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

