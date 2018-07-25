---
title: 'Lync Server 2013: Lista de tabelas CDR'
TOCTitle: Lista de tabelas CDR
ms:assetid: 031843fd-c7ff-4534-9b02-8847aad70807
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398084(v=OCS.15)
ms:contentKeyID: 49305695
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de tabelas do CDR no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O esquema de banco de dados de registro de detalhes das chamadas (CDR) consiste nas seguintes tabelas.

## Tabelas Estáticas


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-callpriorities-table.md">Tabela CallPriorities no Lync Server 2013</a></p></td>
<td><p>Armazena a lista de prioridade de chamadas possíveis, tais como emergência, urgente, normal, não urgente e outras.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencejointimethresholds-table.md">Tabela ConferenceJoinTimeThresholds no Lync Server 2013</a></p></td>
<td><p>Armazena os limites de classificação utilizados pelo Relatório de resumo de tempo de participação na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-deregistertype-table.md">Tabela DeRegisterType no Lync Server 2013</a></p></td>
<td><p>Armazena a lista de possíveis razões de cancelamento de registro de usuário, como &quot;iniciado por cliente&quot;, &quot;registro expirou&quot;, &quot;falha de cliente&quot; dentre outros.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-medialist-table.md">Tabela MediaList no Lync Server 2013</a></p></td>
<td><p>Armazena a lista de tipos de mídia que podem gerar as entradas no banco de dados (por exemplo IM, áudio, vídeo e transferência de arquivos).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-purgesettings-table.md">Tabela PurgeSettings no Lync Server 2013</a></p></td>
<td><p>Armazena informação que especifica se (e quando) registros de detalhes de chamada desatualizada serão excluídas automaticamente do banco de dados CDR.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-roles-table.md">Tabela Roles no Lync Server 2013</a></p></td>
<td><p>Armazena a lista de funções de conferência possíveis (por exemplo, participantes e apresentadores).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-sipresponsemetadata-table.md">Tabela SIPResponseMetaData no Lync Server 2013</a></p></td>
<td><p>Stores a list of SIP response codes and the classification and definition of each of those codes.</p></td>
</tr>
</tbody>
</table>


## Tabelas de Suporte


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a></p></td>
<td><p>Armazena os clientes (tanto o tipo de cliente quanto o número de versão) de cada cliente envolvido em uma chamada com informações capturadas neste banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferenceuris-table.md">Tabela ConferenceUris no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de ConferenceURIs que são utilizadas em chamadas relacionadas a conferências.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-contenttypes-table.md">Tabela ContentTypes no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de tipos de conteúdo SIP (Session Initiation Protocol) que são usadas tanto em chamadas ponto-a-ponto quanto em chamadas de conferência.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-devices-table.md">Tabela Devices no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de dispositivos, incluindo a versão de hardware, fabricante e endereço MAC.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre o ID de Diálogo para cada sessão no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-edgeservers-table.md">Tabela EdgeServers no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de Servidores de Borda usados para chamadas externas.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-gateways-table.md">Tabela Gateways no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de Gateways usados para chamadas VoIP (Voice over Internet Protocol).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-hardwareversions-table.md">Tabela HardwareVersions no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de versões de hardware de dispositivos (telefone de mesa).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-manufacturers-table.md">Tabela Manufacturers no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de fabricantes de dispositivos (telefone de mesa).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-mcus-table.md">Tabela Mcus no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre os vários Servidores de Conferência A/V e seus URIs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-mediationservers-table.md">Tabela MediationServers no Lync Server 2013</a></p></td>
<td><p>Armazena uma lista de Servidores de Mediação usados para chamadas VoIP.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-phones-table.md">Tabela Phones no Lync Server 2013</a></p></td>
<td><p>Armazena todos os números de telefone usados em chamadas VoIP que foram arquivadas ou que tiveram os detalhes da chamadas gravados.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-pools-table.md">Tabela Pools no Lync Server 2013</a></p></td>
<td><p>Armazena os nomes do pool no qual as mensagens de IM são capturadas.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a></p></td>
<td><p>Armazena o nome de servidores envolvidos em chamadas.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a></p></td>
<td><p>Armazena os locatários suportados pela implantação atual. Existem alguns locatários integrados para os usuários Enterprise, Federado, de conectividade de IM público e Anônimos.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-useragentdef-table.md">Tabela UserAgentDef no Lync Server 2013</a></p></td>
<td><p>Mapeia os identificadores de agente do usuário aos nomes descritivos dos agentes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a></p></td>
<td><p>Armazena o os URIs de usuários que tenham participado em sessões gravadas ou arquivadas neste banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-userstatistics-table.md">Tabela UserStatistics no Lync Server 2013</a></p></td>
<td><p>Armazena as informações de uso do sistema do usuário.</p></td>
</tr>
</tbody>
</table>


## Tabelas Específicas para Registros de CDR de Conferências


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-conferences-table.md">Tabela Conferences no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre todas as conferências que foram arquivadas ou que tiveram seus detalhes gravados, incluindo ConferenceUI e hora de início e término.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencesessiondetails-table.md">Tabela ConferenceSessionDetails no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre todas as sessões de conferência baseada em SIP, incluindo hora de início e término, ID de usuário, código de resposta e ID de diagnóstico para cada sessão.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-focusjoinsandleaves-table.md">Tabela FocusJoinsAndLeaves no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre entradas e saídas de conferências, incluindo as funções e versões de cliente dos usuários.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-mcujoinsandleaves-table.md">Tabela McuJoinsAndLeaves no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre os Servidores de Conferência A/V que estão envolvidos em uma conferência e os horários de ingresso e saída de usuário.</p></td>
</tr>
</tbody>
</table>


## Tabelas para Mensagens em Conferências IM


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-conferencemessagecount-table.md">Tabela ConferenceMessageCount no Lync Server 2013</a></p></td>
<td><p>Armazena, para cada conferência IM, o número de mensagem que foram enviadas por cada usuário.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-imreportsummary-table.md">Tabela IMReportSummary no Lync Server 2013</a></p></td>
<td><p>Provides an overall report on the instant messaging sessions held in an organization.</p></td>
</tr>
</tbody>
</table>


## Tabelas para Sessões Ponto-a-Ponto


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-sessiondetails-table.md">Tabela SessionDetails no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre cada sessão ponto-a-ponto, incluindo horário de início e término, ID de usuário, código de resposta e a contagem de mensagem para cada usuário.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-filetransfers-table.md">Tabela FileTransfers no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre sessões de transferência de arquivo, incluindo nome de arquivo e resultado (aceita, rejeitada ou cancelada).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-media-table.md">Tabela Media no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre os diferentes tipos de mídia envolvidos em sessões ponto-a-ponto.</p></td>
</tr>
</tbody>
</table>


## Tabela para Detalhes de Chamadas VoIP


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-voipdetails-table.md">Tabela VoipDetails no Lync Server 2013</a></p></td>
<td><p>Armazena, para cada chamada VoIP/PSTN de duas partes, informações sobre a chamada, tais como ID de telefone do telefone VoIP, gateway usado e qual parte desconectou. Consulte <a href="lync-server-2013-sessiondetails-table.md">Tabela SessionDetails no Lync Server 2013</a> para horários de início/término de chamadas e código de resposta.</p>

> [!NOTE]  
> Se uma parte em uma chamada é um usuário VoIP ou se um Servidor de Mediação esteve envolvido na chamada, um registro será criado nesta tabela. Informações sobre chamadas VoIP/VoIP não envolvendo um telefone PSTN (rede de telefonia pública comutada) são capturadas no <a href="lync-server-2013-sessiondetails-table.md">Tabela SessionDetails no Lync Server 2013</a>.

</td>
</tr>
</tbody>
</table>


## Tabela para Auditoria de Chamada E9-1-1


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-locations-table.md">Tabela Locations no Lync Server 2013</a></p></td>
<td><p>Armazena, para cada chamada de emergência, tal como uma chamada Enhanced 9-1-1 (E9-1-1), informações locais sobre a chamada. Consulte <a href="lync-server-2013-sessiondetails-table.md">Tabela SessionDetails no Lync Server 2013</a> para horários de início/término de chamadas e código de resposta.</p>

> [!NOTE]  
> Esta tabela contém apenas o blob de local para a chamada E9-1-1. Consulte a tabela SessionDetails para outras informações detalhadas sobre a chamada.

</td>
</tr>
</tbody>
</table>


## Tabelas para Resolução de Problemas


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-application-table.md">Tabela de aplicativos no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre vários processos dentro de Lync Server 2013 que estão envolvidos em roteamento e conexões.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-calltype-table.md">Tabela CallType no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre tipos de chamada, tais como &quot;áudio&quot;, &quot;IM&quot;, &quot;áudio e vídeo&quot; e &quot;compartilhamento de aplicativos&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-errorcategory-table.md">Tabela ErrorCategory no Lync Server 2013</a></p></td>
<td><p>Stores the friendly name for each Microsoft Lync Server 2013 diagnostic classification.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-errordef-table.md">Tabela ErrorDef no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre tipos de erros e suas definições.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-errorreport-table.md">Tabela ErrorReport no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre erros que ocorreram.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-progressreport-table.md">Tabela ProgressReport no Lync Server 2013</a></p></td>
<td><p>Armazena informações sobre os relatórios de progresso das várias etapas envolvidas nos processos Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


As tabelas na lista a seguir são usadas internamente por Lync Server. Seus detalhes não são descritos neste documento.

## Tabelas para Uso Interno do Lync Server


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
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
<td><p><strong>DbErrorMessage</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>FrontEnd Table</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MSMQProcessing Table</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>SummaryTableConfiguration</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Syndicators Table</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>SyndicatorsTenantMap Table</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Task Table</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserStatistics</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UsageSummary_UQ</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>UsageSummary</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DaylightSavingYears</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimeZoneConfiguration</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TimeZones</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>FailureSummary_UQ</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FailureSummary</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="even">
<td><p><strong>ServerSummary</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagMetaData</strong></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

