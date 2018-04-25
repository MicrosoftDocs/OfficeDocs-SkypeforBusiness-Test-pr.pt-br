---
title: 'Lync Server 2013: Tabela AudioSignal'
TOCTitle: Tabela AudioSignal
ms:assetid: 0013c8c6-cdf9-4d70-bc2a-cddd1560f66b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398064(v=OCS.15)
ms:contentKeyID: 49305659
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela AudioSignal no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa métricas de sinal de áudio para um ponto de extremidade. Geralmente, cada chamada tem dois registros, um para quem chama, outro para quem é chamado.


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
<td><p><strong>SendSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Representa o nível de sinal de áudio de Controle de Ganho Pós-Analógico. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser ao menos 30 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Veja SendSignalLevel.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Representa o nível de ruído de áudio de Controle de Ganho Pós-Analógico. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser menor que 35 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Veja SendNoiseLevel.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoReturn</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Medida de Realce de Perda de Eco de Retorno. A unidade desta medida é o dB. Valores mais baixos representam menos eco. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioSpeakerGlitchRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Média de estalos por cada cinco minutos para reconstrução de alto-falante. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioMicGlitchRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Média de estalos por cada cinco minutos para captura de microfone. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioTimestampDriftRateMic</strong></p></td>
<td><p>decimal(9,2)</p></td>
<td><p> </p></td>
<td><p>Taxa de deriva do clock do dispositivo de microfone, relativo ao clock de CPU.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioTimestampDriftRateSpk</strong></p></td>
<td><p>decimal(9,2)</p></td>
<td><p> </p></td>
<td><p>Taxa de deriva do clock do dispositivo de alto-falante, relativo ao clock de CPU.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioTimestampErrorMicMs</strong></p></td>
<td><p>decimal(9,2)</p></td>
<td><p> </p></td>
<td><p>Taxa de deriva do clock do dispositivo de alto-falante, relativo ao clock de CPU.</p>
<p>Média de erro de registro de hora de fluxo de captura de microfone, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioTimestampErrorSpkMs</strong></p></td>
<td><p>decimal(9,2)</p></td>
<td><p> </p></td>
<td><p>Média de erro de registro de hora de fluxo de reconstrução de alto-falante, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>VsEntryCauses</strong></p></td>
<td><p>smallint</p></td>
<td><p> </p></td>
<td><p>Opção de voz é um modo meio-duplex com capacidade de interrupção reduzida. Causas de entrada de opção de voz:</p>
<p>ENTER_VS_BADTS 0x01</p>
<p>ENTER_VS_ECHO 0x02</p>
<p>ENTER_VS_FORCEORCONVERGENCE 0x04</p>
<p>ENTER_VS_DNLP 0x08</p>
<p>A causa pode ser uma combinação destas causas individuais. ENTER_VS_FORCEORCONVERGENCE pode apenas ser habilitado por regkey para testes.</p>
<p>O tipo de dados para esta coluna foi alterado no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoEventCauses</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>Causas de um evento de eco:</p>
<p>ECHO_EVENT_BAD_TIMESTAMP 0x01</p>
<p>ECHO_EVENT_POSTAEC_ECHO 0x02</p>
<p>ECHO_EVENT_ANLP 0x04</p>
<p>ECHO_EVENT_DNLP 0x08</p>
<p>ECHO_EVENT_MIC_CLIPPING 0x10</p>
<p>ECHO_EVENT_BAD_STATE 0x20</p>
<p>A causa pode ser uma combinação destas causas individuais.</p></td>
</tr>
<tr class="even">
<td><p><strong>EchoPercentMicIn</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Porcentagem de tempo em que o eco foi detectado no fluxo de captura do microfone. Normalmente, os valores são baixos para fones de ouvido ou celulares e mais altos para viva voz e auto falante. Para dispositivos que suportam cancelamento de eco acústico na placa, os altos níveis indicam vazamento de eco. Para outros dispositivos, essa métrica não deve ser utilizada para avaliar a qualidade do dispositivo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoPercentSend</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>Porcentagem do tempo quando eco é detectado no fluxo enviado. Uma alta porcentagem de eco em fluxos enviados indica um vazamento de eco.</p></td>
</tr>
<tr class="even">
<td><p><strong>RxAGCSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Nível de sinal recebido no Servidor de Mediação do Gateway; se aplica apenas ao Servidor de Mediação. A unidade desta medida é o dBoV. Para uma boa qualidade, a faixa aceitável deve ser de [-30 a -18] dBoV.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RxAGCNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Nível de sinal recebido no Servidor de Mediação do Gateway. Se aplica apenas ao Servidor de Mediação. A unidade desta medida é o dBoV. Para uma boa qualidade, a faixa aceitável deve ser menor do que -50 dBoV.</p></td>
</tr>
<tr class="even">
<td><p><strong>RxAvgAGCGain</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Controle de ganho automático (AGC) na ponta do Servidor de Mediação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InitialSignalLevelRMS</strong></p></td>
<td><p>flutuar</p></td>
<td><p> </p></td>
<td><p>A Raiz Quadrada Média RMS do sinal de entrada até dos primeiros 30 segundos da chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvSignalLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de sinal como recebido no canal 1.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvSignalLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de sinal como recebido no canal 2.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvNoiseLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de ruído como recebido no canal 1.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvNoiseLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de ruído como recebido no canal 2.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendSignalLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de sinal como enviado no canal 1.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendSignalLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de sinal como enviado no canal 2.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendNoiseLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de ruído como enviado no canal 1.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendNoiseLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Nível de ruído como enviado no canal 2.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

