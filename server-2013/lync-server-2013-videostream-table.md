---
title: 'Lync Server 2013: Tabela VideoStream'
TOCTitle: Tabela VideoStream
ms:assetid: 4275ede7-5467-4a97-b8c8-a4b00917bf32
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425928(v=OCS.15)
ms:contentKeyID: 49306530
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela VideoStream no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa um fluxo de vídeo. Uma linha de mídia de vídeo geralmente contém dois fluxos de vídeo.


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
<td><p><strong>VideoPayloadDescription</strong></p></td>
<td><p>smallint</p></td>
<td><p>Externo, Primário</p></td>
<td><p>Descrição de carga. Consulte <a href="lync-server-2013-payloaddescription-table.md">Tabela PayloadDescription no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrival</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Média de tremulação de rede a partir da estatística do protocolo RTCP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrivalMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Tremulação máxima da rede durante a sessão de vídeo.</p></td>
</tr>
<tr class="even">
<td><p><strong>RoundTrip</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Tempo de ida e volta de estatísticas RTCP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RoundTripMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Tempo máximo de ida e volta para o fluxo de vídeo.</p></td>
</tr>
<tr class="even">
<td><p><strong>PacketLossRate</strong></p></td>
<td><p>decimal(5,4)</p></td>
<td><p> </p></td>
<td><p>Taxa média de perda de pacotes durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketLossRateMax</strong></p></td>
<td><p>decimal(5,4)</p></td>
<td><p> </p></td>
<td><p>Perda máxima de pacotes observada durante a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>PacketUtilization</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Contagem de pacotes para o fluxo de vídeo (protocolo RTP)</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEst</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Estimativas de largura de banda para o fluxo de vídeo.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoResolution</strong></p></td>
<td><p>char(9)</p></td>
<td><p> </p></td>
<td><p>Resolução do vídeo em pixels de largura multiplicados por pixels de altura. Relatado como uma seqüência de caracteres.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoBitRateAvg</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Taxa média de bits do fluxo de vídeo.</p></td>
</tr>
<tr class="even">
<td><p><strong>InboundVideoFrameRateAvg</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p> </p></td>
<td><p>A taxa de quadro de vídeo recebida.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutboundVideoFrameRateAvg</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p> </p></td>
<td><p>A taxa de quadro de vídeo enviada.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoBitRateMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>A taxa máxima de bits de vídeo durante a sessão de vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoFrameLossRate</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p> </p></td>
<td><p>A porcentagem do total de quadros de vídeo que são perdidos.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoFEC</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Não disponível.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoLocalFrameLossPercentageAvg</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p></p></td>
<td><p>A porcentagem do total de quadros de vídeo que são perdidos.</p></td>
</tr>
<tr class="even">
<td><p><strong>CIFQualityRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>A porcentagem da chamada que estava na resolução CIF (Common Interchange Format).</p></td>
</tr>
<tr class="odd">
<td><p><strong>VGAQualityRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>A porcentagem da chamada que estava na resolução VGA.</p></td>
</tr>
<tr class="even">
<td><p><strong>HD720QualityRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>A porcentagem da chamada que estava na resolução HD720.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NoneDropRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Porcentagem de duração da chamada sem remoção de quadro.</p></td>
</tr>
<tr class="even">
<td><p><strong>BDropRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Porcentagem de duração da chamada com remoção de quadro B.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BPDropRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Porcentagem de duração da chamada com remoção de quadro BP.</p></td>
</tr>
<tr class="even">
<td><p><strong>BPSPDropRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Porcentagem de duração da chamada com remoção de quadro SP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BPSPIDropRatio</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Porcentagem de duração da chamada com remoção de quadro BPSP.</p></td>
</tr>
<tr class="even">
<td><p><strong>Inbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Dados de fluxo no lado do receptor são recebidos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Outbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Dados de fluxo no lado do remetente são recebidos.</p></td>
</tr>
<tr class="even">
<td><p><strong>SenderIsCallerPAI</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 significa que a direção do fluxo é do chamador para o receptor.</p>
<p>0 significa que a direção do fluxo é do receptor para o chamador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LossCongestionPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de tempo quando uma chamada foi perdida em um estado de congestionamento de perda.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>DelayCongestionPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de chamadas durante um congestionamento causado pelo atraso na chegada de pacotes de rede.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ContentionDetectedPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Indica a porcentagem de tempo quando uma chamada estava competindo por recursos de rede.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstMin</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade mínima de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade máxima de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstStdDev</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Desvio padrão da estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstAvge</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade média de estimativa de largura de banda medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>LowBandwidthForMultiview</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada onde a extremidade determinou que a conexão de rede não pode suportar vídeos multiview.</p>
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
<td><p>int</p></td>
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
<td><p><strong>VideoPacketLossRate</strong></p></td>
<td><p>decimal(9,4)</p></td>
<td><p></p></td>
<td><p>Taxa a qual os pacotes de vídeo foram perdidos.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoAllocateBWAvg</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade média de largura de banda alocada para vídeo.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendCodecTypes</strong></p></td>
<td><p>smallint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipos de codecs de vídeo utilizados pelo remetente. Consulte <a href="lync-server-2013-codecdescription-table.md">Tabela CodecDescription no Lync Server 2013</a> para mais informações.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendResolutionWidth</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Largura da resolução utilizada pelo remetente.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendResolutionHeight</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Altura de resolução utilizada pelo remetente.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendFrameRateAverage</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Média de transmissão da taxa de quadros de vídeo utilizada pelo remetente.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendBitRateMaximum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Taxa de bit máxima para o remetente.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendBitRateAverage</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Média de taxa de bit para o remetente.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendVideoStreamsMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Número máximo de fluxos de vídeo utilizado pelo remetente.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvCodecTypes</strong></p></td>
<td><p>smallint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Códigos de vídeo utilizados pelo receptor. Consulte <a href="lync-server-2013-codecdescription-table.md">Tabela CodecDescription no Lync Server 2013</a> para mais informações.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvResolutionWidth</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Largura de resolução utilizada pelo receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvResolutionHeight</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Altura de resolução utilizada pelo receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvFrameRateAverage</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Média de taxa de quadro de vídeo usado pelo receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvBitRateMaximum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Taxa de bit máximo para o receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvBitRateAverage</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Taxa de bit média para o receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvVideoStreamsMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Fluxos de vídeo máximos para o receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvVideoStreamsMin</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Mínimo de fluxos de vídeo para o receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvVideoStreamsMode</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Modo de vídeo (por exemplo, galeria ou fluxo único) para o receptor.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoPostFECPLR</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Taxa de perda de pacotes após o encaminhamento de uma correção de erro ter sido aplicado.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DynamicCapabilityPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem de tempo em que uma marcação de capacidade dinâmica esteve ativa.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ResolutionMin</strong></p></td>
<td><p>char(9)</p></td>
<td><p></p></td>
<td><p>Resolução mínima medida durante a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowBitRateCallPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada abaixo do limiar da menor taxa de bit (70 kilobits por segundo).</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>LowFrameRateCallPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada abaixo do limiar da menor taxa de quadro (7.5 quadros por segundo, entrada).</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowResolutionCallPercent</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Porcentagem da chamada na resolução mais baixa.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>DurationSeconds</strong></p></td>
<td><p>flutuar</p></td>
<td><p></p></td>
<td><p>Comprimento da chamada em segundos.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsAggregatedData</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se os dados foram agregados a várias chamadas.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

