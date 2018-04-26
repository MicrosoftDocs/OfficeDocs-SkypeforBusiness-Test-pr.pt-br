---
title: Tabela VideoMetricsThreshold no Lync Server 2013
TOCTitle: Tabela VideoMetricsThreshold no Lync Server 2013
ms:assetid: 2e2f4711-35ba-48c6-b15b-5aba61c4eb75
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204778(v=OCS.15)
ms:contentKeyID: 49306254
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela VideoMetricsThreshold no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela VideoMetricsThreshold contém os melhores valores e aceitáveis para as métricas de Qualidade da Experiência usada com chamadas de vídeo.


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
<th><strong>Chave/índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>CallType</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Tipo de chamada realizada.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoPostFECPLROptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 0.05.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoPostFECPLRAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 0.10.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoLocalFrameLostPercentageAverageOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 5.0.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoLocalFrameLostPercentageAverageAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 10.0.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvFrameRateAverageOptimal</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 12.0000.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvFramerateAverageAcceptable</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 7.0000.</p></td>
</tr>
<tr class="even">
<td><p><strong>LowFrameRateCallPercentOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 5.0.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowFrameRateCallPercentAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 10.0/</p></td>
</tr>
<tr class="even">
<td><p><strong>LowResolutionCallPercentOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 5.0.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowResolutionCallPercentAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 10.0.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoPacketLossRateOptimal</strong></p></td>
<td><p>foat</p></td>
<td><p></p></td>
<td><p>O valor padrão é 0.05.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoPacketLossRateAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>O valor padrão é 0.10.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoFrameRateAvgOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>O valor padrão é 12.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoFrameRateAvgAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>O valor padrão é 7.</p></td>
</tr>
<tr class="even">
<td><p><strong>DynamicCapabilityPercentOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 5.00.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DynamicCapabilityPercentAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>O valor padrão é 10.00.</p></td>
</tr>
</tbody>
</table>

