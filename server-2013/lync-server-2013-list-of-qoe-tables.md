---
title: 'Lync Server 2013: Lista de tabelas QoE'
TOCTitle: Lista de tabelas QoE
ms:assetid: 176194d7-d184-4e23-94bb-cb62b4db47f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398236(v=OCS.15)
ms:contentKeyID: 49306004
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de tabelas QoE no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O esquema de banco de dados consiste nas tabelas a seguir.

**Tabelas de suporte**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tabela</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-appsharingmetricsthreshold-table.md">Tabela AppSharingMetricsThreshold no Lync Server 2013</a></p></td>
<td><p>Armazena valores ótimos e aceitáveis para as métricas de Qualidade da Experiência usadas com compartilhamento de aplicativo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-codecdescription-table.md">Tabela CodecDescription no Lync Server 2013</a></p></td>
<td><p>Mapeia identificadores exclusivos de codec ao codec correspondente.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a></p></td>
<td><p>Mapeia endereços IP aos identificadores de endereços IP exclusivos usados em outros locais no banco de dados de Qualidade da Experiência.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-networkconnectiondetail-table.md">Tabela NetworkConnectionDetail no Lync Server 2013</a></p></td>
<td><p>Mapeia os tipos de conexão de rede aos identificadores de conexão de rede usados em outros locais no banco de dados de Qualidade da Experiência.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-purgesettings-table-qoe.md">Tabela PurgeSettings (QoE) no Lync Server 2013</a></p></td>
<td><p>Armazena informações que especificam se (e quando) registros de Qualidade da Experiência antigos serão automaticamente deletados do banco de dados de QoE (Qualidade da Experiência).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-traceroute-table.md">Tabela TraceRoute no Lync Server 2013</a></p></td>
<td><p>Armazena informações de roteamento para chamadas.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragentdef-table-qoe.md">Tabela UserAgentDef (QoE) no Lync Server 2013</a></p></td>
<td><p>Mapeia os identificadores de agente do usuário aos nomes descritivos dos agentes.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videometricsthreshold-table.md">Tabela VideoMetricsThreshold no Lync Server 2013</a></p></td>
<td><p>Armazena valores ótimos e aceitáveis para as métricas de Qualidade da Experiência usadas com chamadas de vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a></p></td>
<td><p>Armazena as cadeias de Agente de Usuário (UA) do Protocolo de Iniciação de Sessão (SIP) e tipos de UA usados em sessões de áudio e vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-user-table.md">Tabela User no Lync Server 2013</a></p></td>
<td><p>Armazena URIs de usuário, de conferência, e de telefone usados em sessões de áudio e vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-endpoint-table.md">Tabela Endpoint no Lync Server 2013</a></p></td>
<td><p>Armazena nomes de computador FQDN de pontos de extremidade que participam de sessões de áudio e vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-pool-table.md">Tabela Pool no Lync Server 2013</a></p></td>
<td><p>Armazena os nomes de pools às quais os dados de métrica pertencem.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-device-table.md">Tabela Device no Lync Server 2013</a></p></td>
<td><p>Armazena os dispositivos de captura e de renderização que são usados em chamadas de áudio/vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-devicedriver-table.md">Tabela DeviceDriver no Lync Server 2013</a></p></td>
<td><p>Armazena o driver do dispositivo de captura e de renderização que são usados em chamadas de áudio/vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-conference-table.md">Tabela Conference no Lync Server 2013</a></p></td>
<td><p>Armazena os URIs da conferência para cenários de conferência ou DialogID para outros cenários.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-sessioncorrelation-table.md">Tabela SessionCorrelation no Lync Server 2013</a></p></td>
<td><p>Armazena CorrelationID para chamadas PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-payloaddescription-table.md">Tabela PayloadDescription no Lync Server 2013</a></p></td>
<td><p>Armazena o Codec usado em chamadas de áudio/vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-appliedbandwidthsource-table.md">Tabela AppliedBandwidthSource no Lync Server 2013</a></p></td>
<td><p>Armazena a origem da largura de banda usada em chamadas de áudio/vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-macaddress-table.md">Tabela MacAddress no Lync Server 2013</a></p></td>
<td><p>Armazena o endereço MAC dos pontos de extremidade participantes de sessões de áudio e vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-dialog-table.md">Tabela Dialog no Lync Server 2013</a></p></td>
<td><p>Armazena a ID de Diálogo de sessões de áudio e vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-region-table.md">Tabela de regiões no Lync Server 2013</a></p></td>
<td><p>Armazena a região de rede definida na configuração NCS.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-usersite-table.md">Tabela UserSite no Lync Server 2013</a></p></td>
<td><p>Armazena o site de rede definido na configuração NCS.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-subnet-table.md">Tabela Subnet no Lync Server 2013</a></p></td>
<td><p>Armazena a sub-rede definida na configuração NCS.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-monitoredregionlink-table.md">Tabela MonitoredRegionLink no Lync Server 2013</a></p></td>
<td><p>Armazena o link de região definido na configuração NCS.</p></td>
</tr>
<tr class="odd">
<td><p><a href="monitoredusersitelink-table.md">Tabela MonitoredUserSiteLink</a></p></td>
<td><p>Armazena os links de site de rede definidos na configuração NCS.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-endpointsubnet-table.md">Tabela EndpointSubnet no Lync Server 2013</a></p></td>
<td><p>Armazena a sub-rede do ponto de extremidade participando em uma sessão de áudio e vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-server-table.md">Tabela Server no Lync Server 2013</a></p></td>
<td><p>Armazena o FQDN ou endereço IP do servidor pelo qual a mídia passa.</p></td>
</tr>
</tbody>
</table>


**Tabelas para dados de métrica**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tabela</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-appsharingstream-table.md">Tabela AppSharingStream no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de Qualidade da Experiência para as transmissões de rede usadas para compartilhamento de aplicativo. Métricas de Qualidade da Experiência para as transmissões de rede usadas para compartilhamento de aplicativo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-session-table.md">Tabela Session no Lync Server 2013</a></p></td>
<td><p>Armazena informações gerais sobre sessões de áudio ou de áudio/vídeo. Uma sessão é definida como um diálogo SIP de áudio ou vídeo entre dois pontos de extremidade.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre cada linha de mídia de uma sessão. Uma linha de mídia é uma coleção de um ou mais fluxos de áudio e vídeo. Geralmente, uma linha única de mídia terá dois fluxos, áudio ou vídeo.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-audiostream-table.md">Tabela AudioStream no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de qualidade de mídia de áudio para cada fluxo de áudio na linha de mídia.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-audiosignal-table.md">Tabela AudioSignal no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de qualidade de mídia de áudio na linha de mídia. Inclui cancelamento do eco acústico (AEC) e métricas de controle automático de ganho (AGC).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videostream-table.md">Tabela VideoStream no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de qualidade de mídia de vídeo para cada fluxo de áudio na linha de mídia.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-audioclientevent-table.md">Tabela AudioClientEvent no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de qualidade de mídia de áudio coletadas do evento do cliente.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videoclientevent-table.md">Tabela VideoClientEvent no Lync Server 2013</a></p></td>
<td><p>Armazena métricas de qualidade de mídia de vídeo coletadas do evento do cliente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tabela DiagnosticData</strong></p></td>
<td><p>Armazena dados de diagnóstico apenas para uso interno.</p></td>
</tr>
</tbody>
</table>


**Tabelas para dados de resumo**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tabela</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Tabela ServerSummary</strong></p></td>
<td><p>Armazena dados de resumo para os servidores, esses dados são usados apenas para relatório de Qualidade de Experiência (QoE).</p></td>
</tr>
<tr class="even">
<td><p><strong>Tabela UserSummary</strong></p></td>
<td><p>Armazena dados de resumo para os usuários, esses dados são usados apenas para relatório de QoE.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tabela CallTypeSummary</strong></p></td>
<td><p>Armazena dados de resumo para tipos de chamadas, esses dados são usados apenas para relatório de QoE.</p></td>
</tr>
</tbody>
</table>


**Tabelas para uso interno de Monitoring Server**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tabela</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DbConfigDateTime</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>DbConfigInt</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tabela FrontEnd</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tabela Tarefa</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SummaryTableConfiguration</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>DbErrorMessage</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MetricsThreshold</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>DaylightSavingYears</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TimeZoneConfiguration</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimeZones</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tabela CallSummary</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tabela DeviceCallSumary</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tabela Inquilino</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoCallSummaryTable</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ASCallSummaryTable</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

