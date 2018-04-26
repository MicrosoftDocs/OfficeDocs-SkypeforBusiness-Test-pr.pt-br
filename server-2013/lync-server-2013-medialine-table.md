---
title: 'Lync Server 2013: Tabela MediaLine'
TOCTitle: Tabela MediaLine
ms:assetid: 414b1d63-ae97-4c27-bac0-c9ad0f808ff0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425920(v=OCS.15)
ms:contentKeyID: 49306510
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MediaLine no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma linha de mídia. Uma sessão de áudio normalmente contém uma linha de mídia de áudio. Uma sessão A/V (audiovisual) normalmente contém uma linha de mídia de áudio e uma linha de mídia de vídeo, apesar de a sessão poder conter duas linhas de mídia de vídeo se um dispositivo de conferência estiver sendo usado ou se o Modo de exibição de galeria for utilizado.


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
<td><p>Referência na <a href="lync-server-2013-session-table.md">Tabela Session no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Referência na <a href="lync-server-2013-session-table.md">Tabela Session no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p>0 é áudio principal, 1 é vídeo principal, 2 é vídeo panorâmico e 3 é Compartilhamento de Aplicativos/Área de Trabalho. Esse rótulo deve ser exclusivo dentro de uma única sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConnectivityIce</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>Essa coluna está presente, mas não é utilizada no Microsoft Lync Server 2013. Informações sobre conectividade utilizada para linha de mídia é capturada nas colunas CallerConnectivityICE e CalleeConnectivityICE.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Informações sobre o processo de ICE (Estabelecimento de Conectividade Interativa) descrito em sinalizadores de bits. Para obter detalhes, consulte <em>Especificação do Protocolo QoE Monitoring Server</em> , disponível para download.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Mesmo que CallerIceWarningFlags, mas no lado do receptor. Para obter detalhes, consulte a <em>Especificação do Protocolo QoE Monitoring Server</em> , disponível para download.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Security</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>O perfil de segurança em uso. 0 é NENHUM, 1 é SRTP, 2 é V1.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transport</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>0 é UDP, 1 é TCP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP do chamador. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Porta usada pelo chamador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerSubnet</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A sub-rede do chamador. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 significa que o chamador está dentro da rede corporativa, 0 significa que o chamador está fora da rede.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço mac do chamador, com referência na <a href="lync-server-2013-macaddress-table.md">Tabela MacAddress no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP do serviço de Borda A/V Lync Server usado pelo receptor. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Porta usada no serviço de Borda A/V pelo chamador.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Dispositivo de captura usado pelo chamador. Referência na <a href="lync-server-2013-device-table.md">Tabela Device no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Dispositivo de renderização usado pelo chamador. Referência na <a href="lync-server-2013-device-table.md">Tabela Device no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Driver do dispositivo de captura do chamador, referenciado na <a href="lync-server-2013-devicedriver-table.md">Tabela DeviceDriver no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Driver do dispositivo de renderização do chamador, referenciado na <a href="lync-server-2013-devicedriver-table.md">Tabela DeviceDriver no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Indica como o chamador se conectou à rede. Os valores são obtidos do <a href="lync-server-2013-networkconnectiondetail-table.md">Tabela NetworkConnectionDetail no Lync Server 2013</a>. Os valores típicos são 0 para uma conexão com cabo, 1 para uma conexão Wi-Fi e 3 para uma conexão Ethernet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerBssid</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>BSSID do chamador, se for usada conexão sem fio BSSID. Referência na <a href="lync-server-2013-macaddress-table.md">Tabela MacAddress no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerVPN</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>O link do chamador. 1 é VPN (rede virtual privada), 0 é não VPN.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerLinkSpeed</strong></p></td>
<td><p>decimal(18,0)</p></td>
<td><p></p></td>
<td><p>A velocidade de link de rede, em bps, para o ponto de extremidade do chamador.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP do receptor de chamada. Consulte <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleePort</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Porta usada pelo receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeSubnet</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Sub-rede do receptor. Consulte o <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 significa que o receptor da chamada está dentro da rede corporativa, 0 significa que o receptor da chamada está dentro da rede.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço Mac do receptor. Referência da <a href="lync-server-2013-macaddress-table.md">Tabela MacAddress no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP do serviço de Borda A/V usado pelo receptor da chamada. Consulte o <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Porta usada no Serviço de Borda A/V pelo receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>estrangeira</p></td>
<td><p>Dispositivo de captura usado pelo receptor da chamada. Referência na <a href="lync-server-2013-device-table.md">Tabela Device no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Dispositivo de renderização usado pelo receptor da chamada. Referência na <a href="lync-server-2013-device-table.md">Tabela Device no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Driver do dispositivo de captura do receptor da chamada. Referência na <a href="lync-server-2013-devicedriver-table.md">Tabela DeviceDriver no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDevDriver</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Driver do dispositivo de renderização do receptor da chamada. Referência na <a href="lync-server-2013-devicedriver-table.md">Tabela DeviceDriver no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Indica como o receptor se conectou à rede. Os valores são obtidos do <a href="lync-server-2013-networkconnectiondetail-table.md">Tabela NetworkConnectionDetail no Lync Server 2013</a>. Os valores típicos são 0 para uma conexão com cabo, 1 para uma conexão Wi-Fi e 3 para uma conexão Ethernet.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeBssid</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>BSSID do receptor, se for usada conexão sem fio BSSID. Referência da <a href="lync-server-2013-macaddress-table.md">Tabela MacAddress no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeVPN</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>O link do receptor da chamada. 1 é VPN (rede virtual privada), 0 é não VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeLinkSpeed</strong></p></td>
<td><p>decimal(18,0)</p></td>
<td><p> </p></td>
<td><p>A velocidade de link de rede, em bps, para o ponto de extremidade do receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConversationalMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>MOS da Conversa de Banda Estreita das sessões de áudio (com base nos dois fluxos de áudio).</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimit</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Esta é a largura de banda real aplicada às várias configurações de política fornecidas do fluxo do lado de envio (TURN, API, SDP, Servidor de Política, e assim por diante). Isso não deve ser confundido com a largura de banda efetiva porque pode haver uma menor largura de banda efetiva com base na estimativa de largura de banda. Essa é basicamente a largura de banda máxima que o fluxo de envio pode demorar bloqueando os limites impostos pela estimativa da largura de banda.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Essa é a origem da ponta da largura de banda que está sendo imposta. Ela descreve de onde está vindo o limite de largura de banda (“Servidor de Política”, “Servidor TURN”, “Modalidade&quot;, e assim por diante). Referência na <a href="lync-server-2013-appliedbandwidthsource-table.md">Tabela AppliedBandwidthSource no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Indica se foram recebidas métricas do chamador; 1 é sim, um valor nulo é não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Indica se foram recebidas métricas do receptor da chamada; 1 é sim, um valor nulo é não.</p></td>
</tr>
<tr class="even">
<td><p><strong>MidCallReport</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se o relatório é para uma parte da sessão ou da sessão inteira.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClassifiedPoorCall</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se uma chamada foi classificada como pobre (valor de 1) ou boa (0).</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerConnectivityICE</strong></p></td>
<td><p>tinyInt</p></td>
<td><p></p></td>
<td><p>Indica se o chamador conectou-se à rede utilizando o protocolo ICE (Internet Connectivity Establishment).</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeConnectivityICE</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>Indica se o chamador conectou-se à rede utilizando o protocolo ICE (Internet Connectivity Establishment).</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP reflexivo do usuário que iniciou a ligação. Em organizações que utilizam NAT (conversão de endereços de rede), o endereço IP reflexivo é o endereço IP do servidor de proxy.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Descrição do dispositivo para o driver WiFi empregado pelo usuário que fez a ligação.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número de versão para o driver WiFi empregado pelo usuário que fez a ligação.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Endereço IP reflexivo do usuário que recebeu a chamada. Em organizações que utilizam NAT (conversão de endereços de rede), o endereço IP reflexivo é o endereço IP do servidor de proxy.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Descrição do dispositivo para o driver WiFi empregado pelo usuário que recebeu a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número de versão para o driver WiFi empregado pelo usuário que recebeu a chamada.</p>
<p>Esta coluna foi introduzida no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

