---
title: Tabela AppSharingStream no Lync Server 2013
TOCTitle: Tabela AppSharingStream no Lync Server 2013
ms:assetid: 391490cb-d7b8-44ca-b4d1-429600da909c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204808(v=OCS.15)
ms:contentKeyID: 49306407
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AppSharingStream no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela AppSharingStream contém medidas de qualidade da experiência dos fluxos de rede usados no compartilhamento de aplicativos. Esta tabela foi introduzida no Microsoft Lync Server 2013.


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
<th><strong>Tipos de dados</strong></th>
<th><strong>Chave/índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>dateTime</p></td>
<td><p>Primário, externo</p></td>
<td><p>Data e hora de início da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário, externo</p></td>
<td><p>Identificador sequencial usado para distinguir entre sessões que foram iniciadas na mesma data e na mesma hora.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário, externo</p></td>
<td><p>Representa o tipo de linha de vídeo usada na chamada. Os valores permitidos são:</p>
<ul>
<li><p>0 – Áudio</p></li>
<li><p>1 – Vídeo</p></li>
<li><p>2 – Vídeo panorâmico</p></li>
<li><p>3 – Compartilhamento de aplicativos/área de trabalho</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>StreamID</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo do fluxo de compartilhamento de aplicativos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrival</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores altos de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Tremulação máxima detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores altos de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RoundTrip</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade média (em milissegundos) exigida para que um pacote de protocolo de transporte em tempo real viaje até outro ponto de extremidade e retorne. Tempos de viagem de ida e volta de 200 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Altos valores de tempo de resposta podem ser causados por roteamento de chamadas internacionais, configuração incorreta de um roteamento ou um servidor de mídia sobrecarregado. Tempos de resposta altos resultam em dificuldades para conversas de áudio bidirecionais e em tempo real.</p></td>
</tr>
<tr class="even">
<td><p><strong>RoundTripMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Quantidade máxima (em milissegundos) exigida para que um pacote de protocolo de transporte em tempo real viaje até outro ponto de extremidade e retorne. Tempos de viagem de ida e volta de 200 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Altos valores de tempo de resposta podem ser causados por roteamento de chamadas internacionais, configuração incorreta de um roteamento ou um servidor de mídia sobrecarregado. Tempos de resposta altos resultam em dificuldades para conversas de áudio bidirecionais e em tempo real.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketLossRate</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa média de perda de pacotes de RTP (protocolo de transporte em tempo real). (A perda de pacotes ocorre quando pacotes de RTP, um protocolo usado para transmitir áudio e vídeo pela Internet, falha ao tentar alcançar seu destino). Altas taxas de perda geralmente são causadas por congestionamento, insuficiência da largura de banda, congestionamento ou interferência na rede sem fio ou um servidor de mídia sobrecarregado. A perda de pacotes normalmente resulta em distorção ou perda de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>PacketLossRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa máxima de perda de pacotes de RTP (protocolo de transporte em tempo real). (A perda de pacotes ocorre quando pacotes de RTP, um protocolo usado para transmitir áudio e vídeo pela Internet, falha ao tentar alcançar seu destino). Altas taxas de perda geralmente são causadas por congestionamento, insuficiência da largura de banda, congestionamento ou interferência na rede sem fio ou um servidor de mídia sobrecarregado. A perda de pacotes normalmente resulta em distorção ou perda de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketUtilization</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Número de pacotes enviados.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEst</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Largura de banda unidirecional estimada disponível no final da sessão. Reportada em bits por segundo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppSharingPayloadDescription</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Descrição da carga do compartilhamento de aplicativos.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Quantidade total de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Quantidade média de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Quantidade máxima de latência unidirecional. A latência relativa unidirecional mede o atraso entre o cliente e o servidor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Total de ocorrências de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade total de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração total de intermitências unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Total de ocorrências de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade total de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração total de intervalos unidirecionais. Uma transmissão &quot;intermitente&quot; ocorre quando os fluxos de dados sofrem intermitências imprevisíveis, em oposição a um fluxo contínuo: os intervalos indicam os atrasos entre essas intermitências. Esta medida avalia o fluxo de dados entre o cliente e o servidor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ApplicationSharingType</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p></p></td>
<td><p>Função do aplicativo (participante do compartilhamento ou visualizador) e tipo de conteúdo.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>O tempo total de processamento de blocos de protocolo RDP (RDP). Um total mais alto significa uma demora mais longa na experiência de exibição.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Tempo médio de processamento de blocos de protocolo RDP (RDP). Um total mais alto significa uma demora mais longa na experiência de exibição.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Tempo máximo de processamento de blocos de protocolo RDP (RDP). Um total mais alto significa uma demora mais longa na experiência de exibição.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência no tempo de processamento de blocos de protocolo RDP (RDP). Uma transmissão &quot;intermitente&quot; é uma transmissão em que os fluxos de dados são imprevisivelmente intermitentes, em oposição a um fluxo contínuo.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência no tempo de processamento de blocos de protocolo RDP (RDP). Uma transmissão &quot;intermitente&quot; é uma transmissão em que os fluxos de dados são imprevisivelmente intermitentes, em oposição a um fluxo contínuo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência no tempo de processamento de blocos de protocolo RDP (RDP). Uma transmissão &quot;intermitente&quot; é uma transmissão em que os fluxos de dados são imprevisivelmente intermitentes, em oposição a um fluxo contínuo.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalos no tempo de processamento de blocos de protocolo RDP (RDP).</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo no tempo de processamento de blocos de protocolo RDP (RDP). Uma baixa densidade do intervalo significa uma melhor experiência de exibição.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo no tempo de processamento de blocos de protocolo RDP (RDP). Uma baixa densidade de intervalo significa uma melhor experiência de exibição.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CaptureTileRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa total de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureTileRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa média de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="odd">
<td><p><strong>CaptureTileRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa máxima de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureTileRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="odd">
<td><p><strong>CaptureTileRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureTileRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="odd">
<td><p><strong>CaptureTileRateGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureTileRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="odd">
<td><p><strong>CaptureTileRateGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo na taxa de blocos capturados (em blocos por segundo)</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Porcentagem total do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Porcentagem média do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Porcentagem máxima do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo do conteúdo que não chegou ao visualizador, mas que foi descartado e substituído por conteúdo recente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ScrapingFrameRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Número total de quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ScrapingFrameRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Número médio de quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ScrapingFrameRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Número máximo de quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ScrapingFrameRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ScrapingFrameRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ScrapingFrameRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ScrapingFrameRateGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ScrapingFrameRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ScrapingFrameRateGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo nos quadros retirados da origem de gráficos.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingTileRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros total de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingTileRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingTileRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de blocos máxima de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingTileRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingTileRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingTileRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingTileRateGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingTileRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingTileRateGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo na taxa de blocos de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingFrameRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros total de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingFrameRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingFrameRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingFrameRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingFrameRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingFrameRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingFrameRateGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>IncomingFrameRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IncomingFrameRateDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo na taxa de quadros de entrada como recebida pelo visualizador.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingTileRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de blocos total de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingTileRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de blocos média de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingTileRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de blocos máxima de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingTileRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência na taxa de blocos de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingTileRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de blocos de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingTileRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência na taxa de blocos de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingTileRateGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingTileRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo na taxa de blocos de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingTileRateGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo na taxa de blocos de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingFrameRateTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros total de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingFrameRateAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingFrameRateMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Taxa de quadros máxima de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingFrameRateBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intermitência na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingFrameRateBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade da intermitência na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingFrameRateBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração da intermitência na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>a</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Ocorrências de intervalo na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>OutgoingFrameRateGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Densidade do intervalo na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OutgoingFrameRateGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>Duração do intervalo na taxa de quadros de saída para o emissor.</p></td>
</tr>
<tr class="even">
<td><p><strong>AverageRectangleHeight</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Altura média da resolução de vídeo em pixels.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AverageRectangleWidth</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Largura média da resolução de vídeo em pixels.</p></td>
</tr>
<tr class="even">
<td><p><strong>Inbound</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média (em quadros por segundo) para transmissões de entrada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Outbound</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Taxa de quadros média (em quadros por segundo) para transmissões de saída.</p></td>
</tr>
<tr class="even">
<td><p><strong>SenderIsCallerPAI</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>1 significa que a direção do fluxo é do chamador para o receptor.</p>
<p>0 significa que a direção do fluxo é do receptor para o chamador.</p></td>
</tr>
</tbody>
</table>

