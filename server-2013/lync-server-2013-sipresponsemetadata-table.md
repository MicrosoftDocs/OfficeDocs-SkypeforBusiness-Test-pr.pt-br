---
title: Tabela SIPResponseMetaData no Lync Server 2013
TOCTitle: Tabela SIPResponseMetaData no Lync Server 2013
ms:assetid: cf723737-4a75-4352-829b-f4954aa59716
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205294(v=OCS.15)
ms:contentKeyID: 49308154
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela SIPResponseMetaData no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O SIPResponseMetaDataTable contém uma lista de códigos de resposta SIP e a classificação e definição de cada um destes códigos. Estes códigos são gerados em resposta aos eventos que afetam dispositivos SIP e sessões de comunicação SIP. Por exemplo, o código de resposta 403 é gerado quando um dispositivo SIP faz uma solicitação, mas o servidor declina esta solicitação.

Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<th>Chave/índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Valor numérico que representa o código de resposta SIP.</p></td>
</tr>
<tr class="even">
<td><p><strong>Class</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Classificação geral do código de resposta. As classificações incluem:</p>
<ul>
<li><p>1 – Respostas informacionais</p></li>
<li><p>2 – Respostas de sucesso</p></li>
<li><p>3 – Respostas de redirecionamento</p></li>
<li><p>4 – Respostas de falha do cliente</p></li>
<li><p>5 -- Respostas de falha do servidor</p></li>
<li><p>6 – Resposta de falha global</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Description</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Descrição do código de resposta SIP. Por exemplo, o código de resposta 181 possui a seguinte descrição:</p>
<p>A chamada está sendo encaminhada</p></td>
</tr>
</tbody>
</table>

