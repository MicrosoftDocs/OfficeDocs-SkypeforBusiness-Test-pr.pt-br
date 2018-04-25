---
title: 'Lync Server 2013: Tabela Phones'
TOCTitle: Tabela Phones
ms:assetid: 41cb356d-9cc8-42b6-ac23-98a61b25aadc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425923(v=OCS.15)
ms:contentKeyID: 49306517
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Phones no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Phones é uma tabela de suporte. Cada registro dessa tabela armazena informações sobre um número de telefone envolvido em chamadas VoIP que possuem registros em um banco de dados.


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
<td><p><strong>PhoneId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica esse telefone.</p></td>
</tr>
<tr class="even">
<td><p><strong>PhoneUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p> </p></td>
<td><p>Número do telefone.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>dateTime</p></td>
<td><p></p></td>
<td><p>Carimbo de data/hora (somente para uso interno).</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

