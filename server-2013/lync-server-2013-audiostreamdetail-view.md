---
title: Exibir AudioStreamDetail
TOCTitle: Exibir AudioStreamDetail
ms:assetid: b6a435b3-103c-41c4-96ed-33c3784534c0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721859(v=OCS.15)
ms:contentKeyID: 49886375
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir AudioStreamDetail

 

_**Tópico modificado em:** 2015-03-09_

A exibição AudioStreamDetail armazena informações sobre cada fluxo de áudio no banco de dados. Essa exibição foi apresentada no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SessionTime</p></td>
<td><p>datetime</p></td>
<td><p>Referenciado da <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>SessionSeq</p></td>
<td><p>int</p></td>
<td><p>Referenciado da <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>StreamId</p></td>
<td><p>int</p></td>
<td><p>Identificação exclusiva em uma linha de mídia.</p></td>
</tr>
<tr class="even">
<td><p>StartTime</p></td>
<td><p>datetime</p></td>
<td><p>Hora de início da sessão.</p></td>
</tr>
<tr class="odd">
<td><p>EndTime</p></td>
<td><p>datetime</p></td>
<td><p>Hora de término da sessão.</p></td>
</tr>
<tr class="even">
<td><p>DialogCategory</p></td>
<td><p>bit</p></td>
<td><p>Categoria do diálogo: 0 é o Lync Server para a perna do Servidor de mediação; 1 é o Servidor de mediação para a perna do gateway PSTN.</p></td>
</tr>
<tr class="odd">
<td><p>MediationServerBypassFlag</p></td>
<td><p>bit</p></td>
<td><p>Sinalizador que indica se a chamada foi ignorada ou não.</p></td>
</tr>
<tr class="even">
<td><p>MediaBypassWarningFlag</p></td>
<td><p>int</p></td>
<td><p>Se presente, indica porque uma chamada não foi ignorada, mesmo se as IDs de desvio correspondem. Apenas um valor é definido:</p>
<p>0x0001 - ID de desvio desconhecida ao adaptador de rede padrão.</p></td>
</tr>
<tr class="odd">
<td><p>CallPriority</p></td>
<td><p>int</p></td>
<td><p>Prioridade da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerPool</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>FQDN do pool de chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleePool</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>FQDN do pool do receptor de chamada.</p></td>
</tr>
<tr class="even">
<td><p>Autor da chamada</p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>Receptor da chamada</p></td>
<td><p>nvarchar (450)</p></td>
<td><p>URI do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerUserAgent</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Cadeia de caracteres do agente do usuário do receptor de chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CallerUserAgentType</p></td>
<td><p>smallint</p></td>
<td><p>Tipo de agente do usuário do receptor da chamada. Consulte a <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a> para obter mais detalhes.</p></td>
</tr>
<tr class="even">
<td><p>CallerUserAgentCategory</p></td>
<td><p>nvarchar (64)</p></td>
<td><p>Categoria o agente do usuário do autor da chamada. Consulte a tabela <a href="lync-server-2013-useragentdef-table-qoe.md">Tabela UserAgentDef (QoE) no Lync Server 2013</a> para obter mais detalhes.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeUserAgent</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Cadeia de caracteres do agente do usuário do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeUserAgentType</p></td>
<td><p>smallint</p></td>
<td><p>Tipo de agente do usuário do receptor. Consulte a <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeUserAgentCategory</p></td>
<td><p>nvarchar (64)</p></td>
<td><p>Categoria do agente do usuário do receptor. Consulte a <a href="lync-server-2013-useragentdef-table-qoe.md">Tabela UserAgentDef (QoE) no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CallerEndpoint</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Nome do ponto de extremidade do autor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeEndpoint</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Nome do ponto de extremidade do receptor.</p></td>
</tr>
<tr class="even">
<td><p>CallerOS</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Sistema operacional (OS) do ponto de extremidade do autor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeOS</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Sistema operacional (OS) do ponto de extremidade do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerCPUName</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome da CPU do ponto de extremidade do autor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCPUName</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome da CPU do ponto de extremidade do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerCPUNumberOfCores</p></td>
<td><p>smallint</p></td>
<td><p>Número de núcleos da CPU no ponto de extremidade do autor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCPUNumberOfCores</p></td>
<td><p>smallint</p></td>
<td><p>Número de núcleos da CPU no ponto de extremidade do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerCPUProcessorSpeed</p></td>
<td><p>int</p></td>
<td><p>Velocidade do processador da CPU do ponto de extremidade do autor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCPUProcessorSpeed</p></td>
<td><p>int</p></td>
<td><p>Velocidade do processador da CPU do ponto de extremidade do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerVirtualizationFlag</p></td>
<td><p>tinyint</p></td>
<td><p>Indica se o sistema do autor da chamada está funcionando em um ambiente virtualizado. Consulte <a href="lync-server-2013-endpoint-table.md">Tabela Endpoint no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeVirtualizationFlag</p></td>
<td><p>tinyint</p></td>
<td><p>Indica que o sistema do receptor da chamada está funcionando em um ambiente virtualizado. Consulte <a href="lync-server-2013-endpoint-table.md">Tabela Endpoint no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CorrelationKey</p></td>
<td><p></p></td>
<td><p>Chave de correlação. Referência da <a href="lync-server-2013-sessioncorrelation-table.md">Tabela SessionCorrelation no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>ConnectivityIce</p></td>
<td><p>tinyint</p></td>
<td><p>Informações sobre o caminho de mídia, como direto ou retransmitido. Consulte <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CallerIceWarningFlags</p></td>
<td><p>int</p></td>
<td><p>Informações sobre o processo de ICE (Estabelecimento de Conectividade Interativa) descrito em sinalizadores de bits do autor da chamada. Para obter detalhes, consulte a Especificação de protocolo do servidor de monitoramento de Qualidade da Experiência.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeIceWarningFlags</p></td>
<td><p>int</p></td>
<td><p>Informações sobre o processo de ICE (Estabelecimento de Conectividade Interativa) descrito em sinalizadores de bits do receptor da chamada. Para obter detalhes, consulte a Especificação de protocolo do servidor de monitoramento de Qualidade da Experiência.</p></td>
</tr>
<tr class="even">
<td><p>Transporte</p></td>
<td><p>tinyint</p></td>
<td><p>Tipo de transporte: 0 é UDP, 1 é TCP.</p></td>
</tr>
<tr class="odd">
<td><p>CallerIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do autor da chamada. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
<tr class="even">
<td><p>CallerPort</p></td>
<td><p>int</p></td>
<td><p>Porta usada pelo chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerInside</p></td>
<td><p>bit</p></td>
<td><p>Indica se o chamador está na rede de intervalo: 1 significa que o chamador está na rede empresarial, 0 significa que está fora da rede.</p></td>
</tr>
<tr class="even">
<td><p>CalleeIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do receptor. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
<tr class="odd">
<td><p>CalleePort</p></td>
<td><p>int</p></td>
<td><p>Porta usada pelo receptor.</p></td>
</tr>
<tr class="even">
<td><p>CalleeInside</p></td>
<td><p>bit</p></td>
<td><p>Indica se o receptor está na rede de intervalo: 1 significa que o receptor está na rede empresarial, 0 significa que está fora da rede.</p></td>
</tr>
<tr class="odd">
<td><p>CallerUserSite</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome do site do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerRegion</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome do país/região do site do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeUserSite</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome do site do receptor.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRegion</p></td>
<td><p>nvarchar (128)</p></td>
<td><p>Nome o país/região do site do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallerRelayIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do serviço de borda A/V usado pelo chamador. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CallerRelayPort</p></td>
<td><p>int</p></td>
<td><p>Port used on the A/V Edge service used by the caller.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRelayIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Chave de endereço IP do serviço de borda A/V usado pelo receptor. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRelayPort</p></td>
<td><p>int</p></td>
<td><p>Porta usada no serviço de borda A/V usado pelo receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallerCaptureDev</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do dispositivo de captura do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerRenderDev</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do dispositivo de renderização do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerCaptureDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do driver do dispositivo de captura do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerRenderDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do driver do dispositivo de renderização do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCaptureDev</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do dispositivo de captura do receptor.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRenderDev</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do dispositivo de renderização do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCaptureDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do driver do dispositivo de captura do receptor.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRenderDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do driver do dispositivo de renderização do receptor.</p></td>
</tr>
<tr class="odd">
<td><p>CallerNetworkConnectionType</p></td>
<td><p>tinyint</p></td>
<td><p>Tipo de conexão de rede do chamador: 0 é por fio, 1 é sem fio.</p></td>
</tr>
<tr class="even">
<td><p>CallerVPN</p></td>
<td><p>bit</p></td>
<td><p>Indica se o autor da chamada se conectou por uma rede privada virtual: 1 é a rede privada virtual (VPN), 0 é não VPN.</p></td>
</tr>
<tr class="odd">
<td><p>CallerLinkSpeed</p></td>
<td><p>decimal(18,0)</p></td>
<td><p>Velocidade da rede dos pontos de extremidade do chamador em bps.</p></td>
</tr>
<tr class="even">
<td><p>CalleeNetworkConnectionType</p></td>
<td><p>tinyint</p></td>
<td><p>Tipo de conexão de rede do receptor: 0 é por fio, 1 é sem fio.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeVPN</p></td>
<td><p>bit</p></td>
<td><p>Indica se o autor da chamada se conectou por uma rede privada virtual: 1 é a rede privada virtual (VPN), 0 é não VPN.</p></td>
</tr>
<tr class="even">
<td><p>CalleeLinkSpeed</p></td>
<td><p>decimal(18,0)</p></td>
<td><p>Velocidade de rede do ponto de extremidade do receptor em bps.</p></td>
</tr>
<tr class="odd">
<td><p>ConversationalMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>MOS da Conversa de Banda Estreita das sessões de áudio (com base nos dois fluxos de áudio).</p></td>
</tr>
<tr class="even">
<td><p>AppliedBandwidthLimit</p></td>
<td><p>int</p></td>
<td><p>Largura de banda aplicada a determinado fluxo de envio considerando várias configurações de política (TURN, API, SDP, Servidor de política etc.). Isso não deve ser confundido com a largura de banda efetiva porque pode haver uma menor largura de banda efetiva com base na estimativa de largura de banda. Isso é basicamente a largura de banda máxima a qual o fluxo de envio pode aceitar limites de bloqueio impostos pela estimativa de largura de banda</p></td>
</tr>
<tr class="odd">
<td><p>JitterInterArrival</p></td>
<td><p>int</p></td>
<td><p>Média de tremulação de rede a partir da estatística do protocolo RTCP.</p></td>
</tr>
<tr class="even">
<td><p>JitterInterArrivalMax</p></td>
<td><p>int</p></td>
<td><p>Tremulação máxima da rede durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p>PacketLossRate</p></td>
<td><p>decimal(5,4)</p></td>
<td><p>Taxa média de perda de pacotes durante a chamada.</p></td>
</tr>
<tr class="even">
<td><p>PacketLossRateMax</p></td>
<td><p>decimal(5,4)</p></td>
<td><p>Perda máxima de pacotes observada durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p>BurstDensity</p></td>
<td><p>decimal(9,4)</p></td>
<td><p>Densidade média de perda de pacote durante picos de perdas em uma chamada.</p></td>
</tr>
<tr class="even">
<td><p>BurstDuration</p></td>
<td><p>int</p></td>
<td><p>Duração média de perda de pacote durante picos de perdas durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p>BurstGapDensity</p></td>
<td><p>decimal(9,4)</p></td>
<td><p>Densidade média de perda de pacote durante intervalos entre picos de perda de pacotes.</p></td>
</tr>
<tr class="even">
<td><p>BurstGapDuration</p></td>
<td><p>int</p></td>
<td><p>Duração média de intervalos entre picos de perda de pacotes.</p></td>
</tr>
<tr class="odd">
<td><p>PacketUtilization</p></td>
<td><p>int</p></td>
<td><p>Contagem de pacotes para o fluxo de áudio.</p></td>
</tr>
<tr class="even">
<td><p>BandwidthEst</p></td>
<td><p>int</p></td>
<td><p>Estimativas de largura de banda para o fluxo de áudio.</p></td>
</tr>
<tr class="odd">
<td><p>DegradationAvg</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Degradação de MOS de rede para a chamada completa. O intervalo vai de 0,0 a 5,0. Essa métrica mostra o quanto o MOS de rede foi reduzido por causa de tremulação e perda de pacote. Para obter a qualidade aceitável, o MOS da rede deve ser menor que 0,5.</p></td>
</tr>
<tr class="even">
<td><p>DegradationMax</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Degradação máxima de MOS de rede durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p>DegradationJitterAvg</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Degradação de MOS de rede causada por tremulação.</p></td>
</tr>
<tr class="even">
<td><p>DegradationPacketLossAvg</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Degradação de MOS de rede causada por perda de pacote.</p></td>
</tr>
<tr class="odd">
<td><p>PayloadDescription</p></td>
<td><p>int</p></td>
<td><p>O codec de áudio usado para a chamada, referenciado de <a href="lync-server-2013-payloaddescription-table.md">Tabela PayloadDescription no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>AudioSampleRate</p></td>
<td><p>int</p></td>
<td><p>Taxa de amostragem para o fluxo de áudio.</p></td>
</tr>
<tr class="odd">
<td><p>CallerSendSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Nível do sinal de áudio de controle de ganho pós-analógico do áudio enviado pelo chamador. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser ao menos 30 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CallerRecvSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Nível do sinal de áudio do áudio recebido pelo chamador. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser ao menos 30 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CallerSendNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de ruído de áudio de controle de ganho pós-analógico do áudio enviado pelo chamador. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser menor que 35 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CallerRecvNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de ruído de áudio de controle de ganho pós-analógico do áudio recebido pelo chamado. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser menor que 35 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CallerEchoReturn</p></td>
<td><p>int</p></td>
<td><p>Aprimoramento de perda e retorno de eco do chamador. A unidade desta medida é o dB. Valores mais baixos representam menos eco. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CallerSpeakerGlitchRate</p></td>
<td><p>int</p></td>
<td><p>Média de falhar por cinco minutos da renderização de alto-falante do chamador. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CallerMicGlitchRate</p></td>
<td><p>int</p></td>
<td><p>Média de falhas por cinco minutos da captura de microfone do chamador. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CallerTimestampDriftRateMic</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Taxa de descompasso de relógio do dispositivo de microfone do chamador, relativo ao relógio da CPU.</p></td>
</tr>
<tr class="odd">
<td><p>CallerTimestampDriftRateSpk</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Taxa de descompasso de relógio de dispositivo do de alto-falante do chamador, relativo ao relógio da CPU.</p></td>
</tr>
<tr class="even">
<td><p>CallerTimestampErrorMicMs</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Média de erro de registro de hora de fluxo de captura de microfone, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CallerTimestampErrorSpkMs</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Média de erros de carimbo de data/hora do fluxo de renderização de alto-falante do chamador, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CallerVsEntryCauses</p></td>
<td><p>smallint</p></td>
<td><p>Opção de voz é um modo meio-duplex com capacidade de interrupção reduzida. Consulte a <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CallerEchoEventCauses</p></td>
<td><p>tinyint</p></td>
<td><p>Causas de um evento de eco para o chamador. Consulte a <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CallerEchoPercentMicIn</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Porcentagem de tempo quando ecos são detectados no fluxo de captura do microfone do chamador. Caso seja utilizado headset, o valor deve ser baixo.</p></td>
</tr>
<tr class="odd">
<td><p>CallerEchoPercentSend</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Porcentagem de tempo quando ecos são detectados no fluxo enviado pelo chamador. Uma alta porcentagem de eco em fluxos enviados indica um vazamento de eco.</p></td>
</tr>
<tr class="even">
<td><p>CallerRxAGCSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de sinal recebido no Servidor de mediação do Gateway para o áudio do chamador; isso se aplica apenas ao Servidor de mediação. A unidade desta medida é o dBoV. Para obter uma boa qualidade, o intervalo aceitável deve ser entre -30 a -18 dBoV.</p></td>
</tr>
<tr class="odd">
<td><p>CallerRxAGCNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de sinal recebido na Servidor de mediação do Gateway para o áudio do chamador. Se aplica apenas ao Servidor de Mediação. A unidade desta medida é o dBoV. Para uma boa qualidade, a faixa aceitável deve ser menor do que -50 dBoV.</p></td>
</tr>
<tr class="even">
<td><p>CallerRxAGCGain</p></td>
<td><p>int</p></td>
<td><p>Controle de ganho automático (AGC) no Servidor de mediação aplicado ao áudio do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerInitialSignalLevelRMS</p></td>
<td><p>float</p></td>
<td><p>Raiz quadrada média (RMS) o sinal de entrada para o chamador pelos 30 primeiros segundos da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeSendSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Representa o nível de sinal de áudio de controle de ganho pós-analógico do áudio enviado pelo receptor. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser ao menos 30 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRecvSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Nível do sinal de áudio do áudio recebido pelo receptor. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser ao menos 30 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CalleeSendNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de ruído de áudio de controle de ganho pós-analógico do áudio enviado pelo receptor. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser menor que 35 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRecvNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de ruído de áudio de controle de ganho pós-analógico do áudio recebido pelo receptor. A unidade desta medida é o dBmo. Para uma qualidade aceitável, deve ser menor que 35 dBmo. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CalleeEchoReturn</p></td>
<td><p>int</p></td>
<td><p>Aprimoramento de perda e retorno de eco do receptor. A unidade desta medida é o dB. Valores mais baixos representam menos eco. Essa medida não é relatada pelo Servidor de Conferência A/V ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeSpeakerGlitchRate</p></td>
<td><p>int</p></td>
<td><p>Média de falhas por cinco minutos da renderização de alto-falante do receptor. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="even">
<td><p>CalleeMicGlitchRate</p></td>
<td><p>int</p></td>
<td><p>Média de falhas por cinco minutos da captura de microfone do receptor. Para uma boa qualidade, deve ser menos de um a cada cinco minutos. Não relatado pelos Servidores de Conferência A/V, Servidores de Mediação ou telefones IP.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeTimestampDriftRateMic</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Taxa de descompasso do relógio do dispositivo de microfone do receptor, relativa ao relógio da CPU.</p></td>
</tr>
<tr class="even">
<td><p>CalleeTimestampDriftRateSpk</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Taxa de descompasso do relógio do dispositivo de alto-falante do receptor, relativa ao relógio da CPU.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeTimestampErrorMicMs</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Média de erro de registro de hora de fluxo de captura de microfone, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeTimestampErrorSpkMs</p></td>
<td><p>decimal(9,2)</p></td>
<td><p>Médio de erro de carimbo de data/hora do fluxo de renderização de alto-falante do receptor, em milissegundos, nos últimos 20 segundos da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeVsEntryCauses</p></td>
<td><p>smallint</p></td>
<td><p>Opção de voz é um modo meio-duplex com capacidade de interrupção reduzida. Consulte a <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CalleeEchoEventCauses</p></td>
<td><p>tinyint</p></td>
<td><p>Causa um evento de eco para o receptor. Consulte <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeEchoPercentMicIn</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Porcentagem de tempo quando ecos são detectados no fluxo de captura do microfone do receptor. Caso seja utilizado headset, o valor deve ser baixo.</p></td>
</tr>
<tr class="even">
<td><p>CalleeEchoPercentSend</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Porcentagem de tempo quando ecos são detectados no fluxo de envio do receptor. Uma alta porcentagem de eco em fluxos enviados indica um vazamento de eco.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRxAGCSignalLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de sinal recebido no Servidor de mediação do Gateway para o áudio do receptor; isso se aplica apenas ao Servidor de mediação. A unidade desta medida é o dBoV. Para uma boa qualidade, a faixa aceitável deve ser de [-30 a -18] dBoV.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRxAGCNoiseLevel</p></td>
<td><p>int</p></td>
<td><p>Nível de sinal recebido no Servidor de mediação do Gateway para o áudio do receptor. Se aplica apenas ao Servidor de Mediação. A unidade desta medida é o dBoV. Para uma boa qualidade, a faixa aceitável deve ser menor do que -50 dBoV.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRxAGCGain</p></td>
<td><p>int</p></td>
<td><p>Controle de ganho automático (AGC) no Servidor de mediação aplicado ao áudio do receptor.</p></td>
</tr>
<tr class="even">
<td><p>CalleeInitialSignalLevelRMS</p></td>
<td><p>float</p></td>
<td><p>Raiz quadrada média (RMS) do sinal de entrada para o receptor durante os 30 primeiros segundos da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>RatioConcealedSamplesAvg</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Taxa média de amostras escondidas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="even">
<td><p>RatioStretchedSamplesAvg</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Taxa média de amostras corrigidas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="odd">
<td><p>RatioCompressedSamplesAvg</p></td>
<td><p>decimal(5,2)</p></td>
<td><p>Taxa média de amostras compactadas geradas pelo reparo de áudio para exemplos típicos.</p></td>
</tr>
<tr class="even">
<td><p>RoundTrip</p></td>
<td><p>int</p></td>
<td><p>Tempo de ida e volta de estatísticas RTCP.</p></td>
</tr>
<tr class="odd">
<td><p>RoundTripMax</p></td>
<td><p>int</p></td>
<td><p>Tempo máximo de ida e volta para o fluxo de áudio.</p></td>
</tr>
<tr class="even">
<td><p>OverallAvgNetworkMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Média de MOS de rede de banda ampla para a chamada. Essa métrica depende da perda de pacote, da tremulação e do codec usado. O intervalo é de 1.0 a 5.0.</p></td>
</tr>
<tr class="odd">
<td><p>OverallMinNetworkMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Mínimo de MOS de rede de banda ampla para a chamada.</p></td>
</tr>
<tr class="even">
<td><p>SendListenMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Pontuação média prevista de MOS de escuta de banda larga do áudio enviado, incluindo nível de fala, nível de ruído e características de dispositivo de captura.</p></td>
</tr>
<tr class="odd">
<td><p>SendListenMOSMin</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>SendListenMOS mínimo da chamada.</p></td>
</tr>
<tr class="even">
<td><p>RecvListenMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>Pontuação média prevista de MOS de escuta de banda larga do áudio recebido da rede, incluindo nível de fala, nível de ruído, codec, condições da rede e características do dispositivo de captura.</p></td>
</tr>
<tr class="odd">
<td><p>RecvListenMOSMin</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>RecvListenMOS mínimo da chamada.</p></td>
</tr>
<tr class="even">
<td><p>AudioFECUsed</p></td>
<td><p>bit</p></td>
<td><p>Indica se o FEC de áudio foi usado para a chamada.</p></td>
</tr>
<tr class="odd">
<td><p>SenderIsCallerPAI</p></td>
<td><p>bit</p></td>
<td><p>Indica a direção das informações de identidade declarada; 1 significa que a direção do fluxo é do chamador para o receptor; 0 significa que a direção do fluxo é do receptor para o chamador.</p></td>
</tr>
</tbody>
</table>

