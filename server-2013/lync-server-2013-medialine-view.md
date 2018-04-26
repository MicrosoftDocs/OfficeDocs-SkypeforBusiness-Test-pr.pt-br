---
title: Exibir MediaLine
TOCTitle: Exibir MediaLine
ms:assetid: 132eca13-8913-4218-9eff-4960ced8c3dc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687972(v=OCS.15)
ms:contentKeyID: 49886106
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir MediaLine

 

_**Tópico modificado em:** 2015-03-09_

O MediaLine View armazena informações sobre cada linha de mídia no banco de dados. Uma sessão de áudio normalmente contém uma linha de mídia de áudio. Uma sessão de áudio e vídeo (A/V) normalmente contém uma linha de mídia de áudio e uma linha de mídia de vídeo; no entanto, a sessão pode conter duas linhas de mídia de vídeo se um dispositivo de conferência ou o modo de exibição de galeria for usado. Este modo de exibição foi introduzido no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dado</th>
<th>detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ConferenceDateTime</p></td>
<td><p>datetime</p></td>
<td><p>Referenciado de <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>SessionSeq</p></td>
<td><p>int</p></td>
<td><p>Referenciado de <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MediaLineLabel</p></td>
<td><p>tinyint</p></td>
<td><p>Referenciado de <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>CallerIceWarningFlags</p></td>
<td><p>int</p></td>
<td><p>Informações sobre o processo do ICE (Estabelecimento de Conectividade Interativa) descrito em sinalizadores de bits para o chamador. Para detalhes, consulte a Especificação do Protocolo de Servidor do Monitoramento da Qualidade da Experiência.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeIceWarningFlags</p></td>
<td><p>int</p></td>
<td><p>Informações sobre o processo do ICE (Estabelecimento de Conectividade Interativa) descrito em sinalizadores de bits para o chamador. Para detalhes, consulte a Especificação do Protocolo de Servidor do Monitoramento da Qualidade da Experiência.</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>tinyint</p></td>
<td><p>Perfil de segurança em uso. 0 é NONE (nenhum), 1 é SRTP, 2 é V1.</p></td>
</tr>
<tr class="odd">
<td><p>Transport</p></td>
<td><p>tinyint</p></td>
<td><p>Tipo de transporte. 0 é UDP, 1 é TCP.</p></td>
</tr>
<tr class="even">
<td><p>CallerIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do chamador. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
<tr class="odd">
<td><p>CallerPort</p></td>
<td><p>int</p></td>
<td><p>Porta usada pelo chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerInside</p></td>
<td><p>bit</p></td>
<td><p>Indica se o chamador está ou não dentro da rede da organização. 1 significa que o chamador está dentro da rede corporativa, 0 significa que está fora.</p></td>
</tr>
<tr class="odd">
<td><p>CallerMacAddress</p></td>
<td><p>varchar(256)</p></td>
<td><p>Endereço MAC da interface de rede usada pelo chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerRelayIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do serviço de Borda de A/V usado pelo chamador. Consulte a <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRelayPort</p></td>
<td><p>int</p></td>
<td><p>Porta usada no serviço de Borda de A/V usado pelo chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerReflexiveIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do chamador conforme reportado pelo serviço de Borda de A/V. Este endereço pode ser diferente do endereço na coluna CallerIPAddr se o cliente estiver localizado atrás de uma NAT, por exemplo.</p></td>
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
<td><p>Nome da unidade do dispositivo de captura do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerRenderDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome da unidade do dispositivo de renderização do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerWifiDriverDeviceDesc</p></td>
<td><p>varchar(256</p></td>
<td><p>Descrição da unidade wifi do chamador.</p></td>
</tr>
<tr class="even">
<td><p>CallerWifiDriverVersion</p></td>
<td><p>varchar(256)</p></td>
<td><p>Versão da unidade wifi do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeNetworkConnectionDetail</p></td>
<td><p>varchar(256)</p></td>
<td><p>Detalhes da conexão de rede do chamador. Consulte a <a href="lync-server-2013-networkconnectiondetail-table.md">Tabela NetworkConnectionDetail no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CallerBssid</p></td>
<td><p>varchar(256)</p></td>
<td><p>Identificador SSID usado pela conexão WiFi do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>CallerVPN</p></td>
<td><p>bit</p></td>
<td><p>Indica se o chamador se conectou por uma rede virtual privada. 1 é rede virtual privada (VPN), 0 é não-VPN.</p></td>
</tr>
<tr class="even">
<td><p>CalleeIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do receptor da chamada. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
<tr class="odd">
<td><p>CalleePort</p></td>
<td><p>int</p></td>
<td><p>Porta usada pelo receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeInside</p></td>
<td><p>bit</p></td>
<td><p>Indica se o receptor da chamada está dentro da rede corporativa. 1 significa que o receptor está dentro da rede corporativa, 0 significa que está fora.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeMacAddress</p></td>
<td><p>varchar(256)</p></td>
<td><p>Endereço MAC da interface de rede usada pelo receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRelayIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do serviço de Borda de A/V usado pelo receptor da chamada. Consulte a <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeRelayPort</p></td>
<td><p>int</p></td>
<td><p>Porta usada no serviço de Borda de A/V usado pelo receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeReflexiveIPAddr</p></td>
<td><p>var(50)</p></td>
<td><p>Endereço IP do receptor da chamada conforme reportado pelo serviço de Borda de A/V. Este endereço pode ser diferente do endereço na coluna CalleeIPAddr se o cliente estiver localizado atrás de uma NAT, por exemplo.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCaptureDev</p></td>
<td><p>var(50)</p></td>
<td><p>Nome do dispositivo de captura do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRenderDev</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome do dispositivo de renderização do receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeCaptureDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome da unidade do dispositivo de captura do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeRenderDevDriver</p></td>
<td><p>varchar(256)</p></td>
<td><p>Nome da unidade do dispositivo de renderização do receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeWifiDriverDeviceDesc</p></td>
<td><p>varchar(256)</p></td>
<td><p>Descrição da unidade wifi do receptor da chamada.</p></td>
</tr>
<tr class="even">
<td><p>CalleeWifiDriverVersion</p></td>
<td><p>varchar(256</p></td>
<td><p>Versão da unidade wifi do receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeNetworkConnectionDetail</p></td>
<td><p>varchar(256)</p></td>
<td><p>Detalhes da conexão de rede do receptor da chamada. Consulte a <a href="lync-server-2013-networkconnectiondetail-table.md">Tabela NetworkConnectionDetail no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p>CalleeBssid</p></td>
<td><p>varchar(256)</p></td>
<td><p>Identificador SSID usado pela conexão WiFi do receptor da chamada.</p></td>
</tr>
<tr class="odd">
<td><p>CalleeVPN</p></td>
<td><p>bit</p></td>
<td><p>Indica se o receptor da chamada se conectou por uma rede virtual privada. 1 é rede virtual privada (VPN), 0 é não-VPN.</p></td>
</tr>
<tr class="even">
<td><p>ConversationalMOS</p></td>
<td><p>decimal(3,2)</p></td>
<td><p>MOS da conversa de banda estreita das sessões de áudio (com base em ambos os fluxos de áudio).</p></td>
</tr>
<tr class="odd">
<td><p>AppliedBandwidthLimit</p></td>
<td><p>int</p></td>
<td><p>Esta é a largura de banda real aplicada a um dado fluxo de envio, considerando várias configurações de política (TURN, API, SDP, Servidor de Políticas, etc.). Não deve ser confundida com a largura de banda real porque pode haver uma largura de banda real menor com base na estimativa da largura de banda. Esta é basicamente a largura de banda máxima que o fluxo de envio pode usar, salvo limites impostos pela estimativa da largura de banda.</p></td>
</tr>
<tr class="even">
<td><p>AppliedBandwidthSource</p></td>
<td><p>varchar(256)</p></td>
<td><p>Origem da capacidade da largura de banda imposta. Descreve de onde o limite da largura de banda está vindo (por exemplo, “Servidor de Políticas”, “Servidor TURN” ou “Modalidade”).</p></td>
</tr>
<tr class="odd">
<td><p>Caller</p></td>
<td><p>bit</p></td>
<td><p>Indica se as métricas do chamador foram recebidas; 1 é sim, 0 é não.</p></td>
</tr>
<tr class="even">
<td><p>Callee</p></td>
<td><p>bit</p></td>
<td><p>Indica se as métricas do receptor da chamada foram recebidas; 1 é sim, 0 é não.</p></td>
</tr>
<tr class="odd">
<td><p>MidCallReport</p></td>
<td><p>bit</p></td>
<td><p>Indica se o relatório refere-se a uma parte da chamada ou à chamada completa.</p></td>
</tr>
<tr class="even">
<td><p>ClassifiedPoorCall</p></td>
<td><p>bit</p></td>
<td><p>Indica se uma chamada foi classificada como ruim (1) ou boa (0).</p></td>
</tr>
<tr class="odd">
<td><p>CallerConnectivityICE</p></td>
<td><p>tinyint</p></td>
<td><p>Indica se o chamador se conectou à rede usando o protocolo ICE (Internet Connectivity Establishment).</p></td>
</tr>
<tr class="even">
<td><p>CalleeConnectivityICE</p></td>
<td><p>tinyint</p></td>
<td><p>Indica se o usuário receptor da chamada se conectou à rede usando o protocolo ICE (Internet Connectivity Establishment).</p></td>
</tr>
</tbody>
</table>

