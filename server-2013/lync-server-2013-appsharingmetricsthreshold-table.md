---
title: Tabela AppSharingMetricsThreshold no Lync Server 2013
TOCTitle: Tabela AppSharingMetricsThreshold
ms:assetid: 782cfab9-01a6-4843-aea1-28f47b0b51f7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205018(v=OCS.15)
ms:contentKeyID: 49307171
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AppSharingMetricsThreshold no Lync Server 2013

 

_**Tópico modificado em:** 2015-12-08_

A tabela AppSharingMetricsThreshold contém valores ideais e aceitáveis de métricas de Qualidade de Experiência usadas no compartilhamento de aplicativos. Esses limites são usado para determinar se a experiência de compartilhamento de aplicativos deve ser classificada como inadequada.

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
<td><p>Tipo de chamada feita.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimitOptimal</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Limitação de largura de banda ideal para compartilhamento de aplicativos. O valor padrão é 1000000.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthLimitAcceptable</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Limitação de largura de banda aceitável para compartilhamento de aplicativos. O valor padrão é 500000.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentTotalOptimal</strong></p></td>
<td><p>decimal (5,2)</p></td>
<td><p></p></td>
<td><p>Percentual ideal de blocos &quot;danificados&quot; para classificação de qualidade de compartilhamento de aplicativos. Esse valor é o percentual de conteúdo do compartilhador que não alcançou o visualizador. O conteúdo pode ser descartado (ou danificado) quando o compartilhador descarta blocos da origem gráfica ou os blocos ASMCU descartam blocos do compartilhador, respectivamente. O valor padrão é 11%.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentTotalAcceptable</strong></p></td>
<td><p>decimal (5,2)</p></td>
<td><p></p></td>
<td><p>Percentual aceitável de blocos &quot;danificados&quot; para classificação de qualidade de compartilhamento de aplicativos. Esse valor é o percentual de conteúdo do compartilhador que não alcançou o visualizador. O conteúdo pode ser descartado (ou danificado) quando o compartilhador descarta blocos da origem gráfica ou os blocos ASMCU descartam blocos do compartilhador, respectivamente. O valor padrão é 36%.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalOptimal</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrivalAcceptable</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Esta coluna não é usada no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Valor ideal do atraso unidirecional relativo entre dois pontos de extremidade de mídia envolvidos no compartilhamento de aplicativos. Esta é uma medida de latência de salto único. O valor padrão é 1,0 segundo.</p>
<p>A coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Valor ideal do atraso unidirecional relativo entre dois pontos de extremidade de mídia envolvidos no compartilhamento de aplicativos. Esta é uma medida de latência de salto único. O valor padrão é 1,75 segundo.</p>
<p>A coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Valor ideal da latência média de processamento de blocos RDP no Servidor de Conferência AS pelo tempo da sessão de visualização. Esta métrica não abrange latência de rede.</p>
<p>Uma média alta reflete um atraso maior na experiência de visualização. Um servidor de conferência sobrecarregado pode ter atrasos médios maiores. O valor padrão é 200 ms.</p>
<p>A coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Valor aceitável da latência média de processamento de blocos RDP no Servidor de Conferência AS pelo tempo da sessão de visualização. Esta métrica não abrange latência de rede.</p>
<p>Uma média alta reflete um atraso maior na experiência de visualização. Um servidor de conferência sobrecarregado pode ter atrasos médios maiores. O valor padrão é 200 ms.</p>
<p>A coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

