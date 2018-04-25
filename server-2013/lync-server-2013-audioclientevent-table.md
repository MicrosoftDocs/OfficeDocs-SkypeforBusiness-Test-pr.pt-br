---
title: 'Lync Server 2013: Tabela AudioClientEvent'
TOCTitle: Tabela AudioClientEvent
ms:assetid: fef73d8f-7261-4e5b-9769-82435b007979
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413086(v=OCS.15)
ms:contentKeyID: 49308720
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AudioClientEvent no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro contém um evento do cliente para um ponto de extremidade em uma chamada de áudio. Normalmente, uma chamada possui dois registros, um para o chamador e um para o receptor.


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
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>Primário</p></td>
<td><p>0: Dados do Receptor</p>
<p>1: Dados do Chamador</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkSendQualityEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem da sessão que o evento NetworkSendQuality foi acionado para um estado &quot;Ruim&quot;.</p>
<p>Qualidade da rede em termos de perda de pacote ou jitter é grave e afeta a qualidade do áudio que está sendo enviado.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkReceiveQualityEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem da sessão que o evento ReceiveSendQuality foi acionado para o estado &quot;Ruim&quot;.</p>
<p>Qualidade da rede em termos de perda de pacote ou jitter é grave e afeta a qualidade do áudio que está sendo recebido.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkDelayEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem da sessão que o evento Delay foi acionado para o estado &quot;Ruim&quot;. A latência de rede é grave e afeta a experiência, impedindo a comunicação interativa</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkBandwidthLowEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento LowBandwidth foi acionado para o estado &quot;Ruim&quot;. A largura de banda disponível é insuficiente para uma experiência de voz aceitável.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPUInsufficientEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento de CPU insuficiente foi acionado para &quot;Ruim&quot;. Não há ciclos de CPU suficientes para processamento com modalidades atuais e aplicativos em uso. Isso causa distorções no canal de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHalfDuplexAECEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceHalfDuplexAEC foi acionado para &quot;Ruim&quot;. Para evitar o eco, o sistema precisa inserir o half duplex.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceRenderNotFunctioning foi acionado para &quot;Ruim&quot;. O dispositivo de renderização usado atualmente para a sessão não está funcionando corretamente. Isso pode causar problemas de áudio unidirecionais.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceCaptureNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceCaptureNotFunctioning foi acionado para &quot;Ruim&quot;. O dispositivo de captura usado atualmente para a sessão não está funcionando corretamente. Isso pode causar problemas de áudio unidirecionais.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceGlitchesEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceGlitches foi acionado para &quot;Ruim&quot;. Há falhas graves na renderização de áudio que está causando distorções. Esses problemas podem ser causados por problemas de driver, tempestade de chamadas de procedimento deferidas (DAC) (drives) e alta utilização da CPU.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceLowSNREventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceLowSNR foi acionado para &quot;Ruim&quot;. A qualidade de captura é muito baixa ou muito barulhento ou o usuário está falando muito longe do microfone. Isso pode causar distorções.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceLowSpeechLevelEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceLowSpeechLevel foi acionado para &quot;Ruim&quot;. O nível de fala do usuário é muito baixo e o sistema não pode aumentá-lo ainda mais. Isso pode causar distorções ou ser percebido como áudio unidirecional.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceClippingEventRatio</strong></p></td>
<td><p>Decimal (5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceClipping foi acionado para &quot;Ruim&quot;.</p>
<p>Quando a fala próximo ao final corta o microfone, é ouvido uma distorção devido ao corte. É importante evitar o corte de microfone perto do final.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceEchoEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceEchoEvent foi acionado para &quot;Ruim&quot;. A instalação ou o dispositivo está causando eco além da capacidade do sistema para compensar.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceNearEndToEchoRatioEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de sessões que o evento DeviceNearEndToEchoRatio foi acionado para &quot;Ruim&quot;. A fala do usuário está muito baixa em comparação com o eco sendo capturado que afeta a experiência de usuários porque limita o quão fácil é interromper um usuário. Reduza o volume do alto-falante, mova o microfone mais perto do falante.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceMultipleEndpointsEventCount</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Número de vezes durante a sessão que o evento DeviceMultipleEndpoints foi acionado para o estado &quot;Ruim&quot;. Vários pontos de extremidade de áudio na mesma sessão detectados e o sistema tem compensado reduzindo o volume de renderização.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHowlingEventCount</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Número de vezes durante a sessão que o evento DeviceHowlingEvent foi acionado para o estado &quot;Ruim&quot;. Loop de feedback de áudio detectado (causado por vários pontos de extremidade compartilhando caminho de áudio).</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderZeroVolumeEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Porcentagem de sessões em que o evento DeviceRenderZeroVolume foi acionado pelo estado “Ruim’. O dispositivo de renderização foi definido como volume zero.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceRenderMuteEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Porcentagem de sessões em que o evento DeviceRenderMute foi acionado pelo estado “Ruim’. O dispositivo de renderização foi definido como mudo.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

