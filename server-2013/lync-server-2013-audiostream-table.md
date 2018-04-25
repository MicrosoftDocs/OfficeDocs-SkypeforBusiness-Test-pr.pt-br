---
title: 'Lync Server 2013: Tabela AudioStream'
TOCTitle: Tabela AudioStream
ms:assetid: 49ccbbc3-2f73-45fc-80a6-e612535cbc10
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425961(v=OCS.15)
ms:contentKeyID: 49306617
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AudioStream no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa um fluxo de áudio. Uma linha de mídia de áudio geralmente contém dois fluxos de áudio.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Referência na <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Referência na <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p>Referência na <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>StreamID</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Identificação exclusiva em uma linha de mídia.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrival</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Média de tremulação de rede a partir da estatística do protocolo RTCP.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Instabilidade máxima da rede durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketLossRate</strong></p></td>
<td><p>decimal(5,4)</p></td>
<td><p> </p></td>
<td><p>Taxa média de perda de pacotes durante a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>PacketLossRateMax</strong></p></td>
<td><p>decimal(5,4)</p></td>
<td><p> </p></td>
<td><p>Perda máxima de pacotes observada durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BurstDensity</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p> </p></td>
<td><p>Densidade média de perda de pacote durante picos de perdas durante a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>BurstDuration</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Duração média de perda de pacote durante picos de perdas durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BurstGapDensity</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p> </p></td>
<td><p>Densidade média de perda de pacote durante intervalos entre picos de perda de pacotes.</p></td>
</tr>
<tr class="even">
<td><p><strong>BurstGapDuration</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Duração média de intervalos entre picos de perda de pacotes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketUtilization</strong></p></td>
<td><p>Int</p></td>
<td><p> </p></td>
<td><p>Contagem de pacotes para o fluxo de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEst</strong></p></td>
<td><p>Int</p></td>
<td><p> </p></td>
<td><p>Estimativas de largura de banda do stream de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DegradationAvg</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Degradação de MOS de rede para a chamada completa. O intervalo vai de 0,0 a 5,0. Essa métrica mostra o quanto o MOS de rede foi reduzido por causa de tremulação e perda de pacote. Para obter a qualidade aceitável, o MOS da rede deve ser menor que 0,5.</p></td>
</tr>
<tr class="even">
<td><p><strong>DegradationMax</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Degradação máxima de MOS de rede durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DegradationJitterAvg</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Degradação de MOS de rede causada por tremulação.</p></td>
</tr>
<tr class="even">
<td><p><strong>DegradationPacketLossAvg</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Degradação de MOS de rede causada por perda de pacote.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioPayloadDescription</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Codec de áudio usado para a chamada, referenciado na Tabela PayloadDescription.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioSampleRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Taxa de amostragem para o fluxo de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RoundTrip</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Tempo de ida e volta de estatísticas RTCP. Para obter qualidade aceitável, esse tempo deve ser menor que 100 ms.</p></td>
</tr>
<tr class="even">
<td><p><strong>RoundTripMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Tempo máximo de viagem de ida e volta do stream de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OverallAvgNetworkMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Média de MOS de rede de banda ampla para a chamada. Essa métrica depende da perda de pacote, da tremulação e do codec usado. O intervalo é [1,0 a 5,0].</p></td>
</tr>
<tr class="even">
<td><p><strong>OverallMinNetworkMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>O MOS mínimo de rede de banda ampla para a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendListenMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>A média prevista de pontuação do MOS de Escuta de banda ampla para áudio enviado, incluindo nível de fala, nível de ruído e características do dispositivo de captura.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendListenMOSMin</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>SendListenMOS mínimo para a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvListenMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>A média prevista de pontuação do MOS de Escuta de banda ampla para áudio recebido da rede, incluindo nível de fala, nível de ruído, codec, condições de rede e características do dispositivo de captura.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvListenMOSMin</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>O RecvListenMOS mínimo para a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioFECUsed</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Sinalizador que indica se o FEC de áudio foi usado para a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>RatioConcealedSamplesAvg</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Taxa média de amostras escondidas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RatioStretchedSamplesAvg</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Taxa média de amostras corrigidas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="even">
<td><p><strong>RatioCompressedSamplesAvg</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Taxa média de amostras compactadas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Inbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Dados de fluxo no lado do receptor são recebidos.</p></td>
</tr>
<tr class="even">
<td><p><strong>Outbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Dados de fluxo no lado do remetente são recebidos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SenderIsCallerPAI</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 significa que a direção do fluxo é do chamador para o receptor.</p>
<p>0 significa que a direção do fluxo é do receptor para o chamador.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalSD</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Desvio padrão para tempos de chegada de tremulação.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConcealRatioMax</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Índice máximo para pacotes de correção oculta.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConcealRatioSD</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Desvio padrão para o índice de pacotes de correção oculta.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HealerPacketDropRatio</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Índice de pacotes deixados pela correção comparados com o número total de pacotes recebidos.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>HealerFECPacketUsedRatio</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Índice de pacotes de correção de erro encaminhados comparado com o número total de pacotes recebidos.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxCompressedSamples</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Número máximo de pacotes de áudio comprimidos pela correção.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>LossCongestionPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de tempo quando uma chamada foi perdida em um estado de congestionamento de perda.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DelayCongestionPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de chamadas durante um congestionamento causado pelo atraso na chegada de pacotes de rede.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentionDetectedPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de tempo quando uma chamada estava competindo por recursos de rede.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstMin</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade mínima de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade máxima de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstStdDev</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Desvio padrão da estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstAvge</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade média de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayTotal</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Quantidade total de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayAverage</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Quantidade média de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayMax</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Quantidade máxima de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Total de ocorrências de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDensity</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Densidade total de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDuration</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Duração total de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Total de ocorrências de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayGapDensity</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Densidade total de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayGapDuration</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Duração total de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>DecodeStereoPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada decodificada como estéreo.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AecRenderStereoPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem de chamada renderizada como estéreo pelo Acoustic Echo Canceller.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioPostFECPLR</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Taxa de perda de pacotes após o encaminhamento de uma correção de erro ter sido aplicado.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EncodeStereoPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem de chamadas codificadas como estéreo.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>AecCaptureStereoPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada capturada como estéreo pelo Acoustic Echo Canceller.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

