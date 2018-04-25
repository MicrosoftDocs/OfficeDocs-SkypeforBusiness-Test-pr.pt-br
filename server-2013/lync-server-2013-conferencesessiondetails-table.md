---
title: 'Lync Server 2013: Tabela ConferenceSessionDetails'
TOCTitle: Tabela ConferenceSessionDetails
ms:assetid: 9eae6a54-69fd-4966-aa17-7ecee1297ad8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412741(v=OCS.15)
ms:contentKeyID: 49307631
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ConferenceSessionDetails no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma sessão de conferência, que poderia ser a sessão com Foco ou a sessão com um servidor de conferência específico.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Chave/Índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>Datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Tempo da solicitação da sessão; usado em conjunto com <strong>SessionIdSeq</strong> para identificar de forma única uma sessão de conferência. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar de forma única uma sessão de conferência. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI da conferência com foco relacionada a esta sessão. Consulte <a href="lync-server-2013-conferenceuris-table.md">Tabela ConferenceUris no Lync Server 2013</a> para obter mais informações. Esta é uma URI de conferência baseada em Foco.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConfInstance</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>Identificador que diferencia entre instâncias de conferências recorrentes. Cada conferência recorrente tem o mesmo ConferenceURI, mas um valor de ConfInstance diferente.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>McuConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI da conferência do servidor de conferências relacionada a esta sessão. Consulte <a href="lync-server-2013-conferenceuris-table.md">Tabela ConferenceUris no Lync Server 2013</a> para obter mais informações. Esta é a URI de conferência baseada em servidor. Para sessões de conferência com foco, esta coluna estará nula.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID de um usuário na sessão de conferência. Consulte a <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserEndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p></p></td>
<td><p>Um GUID para identificar a instância do ponto de extremidade. Por exemplo, se um usuário faz logon em máquinas diferentes com a mesma conta, cada máquina terá um ID de ponto de extremidade diferente.</p></td>
</tr>
<tr class="even">
<td><p><strong>OnBehalfOfId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O chamador está em nome do usuário identificado por este ID. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReferredById</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A chamada é referenciada para o usuário identificado por este ID. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Versão do cliente usado pelo usuário da conferência. Consulte a <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConfClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Versão do cliente usado pelo servidor de conferências. Consulte a <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReplaceDialogIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número para identificar a caixa de diálogo substituída pela sessão atual. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReplaceDialogIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>ReplacesDialogIdTime</strong> para identificar de forma única uma sessão substituída por esta sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsStartedByConfServer</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se a sessão é iniciada pelo Servidor de conferências.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsEndedByConfServer</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se a sessão é encerrada pelo Servidor de conferências.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsUserInternal</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Se o usuário está conectado de um local interno ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Código de resposta do Protocolo de Iniciação de Sessão (SIP) para o convite da sessão. Este campo é geralmente preenchido por dados gerados da mensagem INVITE inicial em uma sessão. Se não houver mensagem INVITE, então o campo será preenchido com a data e hora da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE ou INFO).</p></td>
</tr>
<tr class="even">
<td><p><strong>DiagnosticId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>ID de diagnóstico capturado do cabeçalho do SIP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do servidor front-end usado para esta sessão. Consulte <a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do pool em que a sessão foi capturada. Consulte <a href="lync-server-2013-pools-table.md">Tabela Pools no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediationServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Mediação que está sendo usado pela chamada, Consulte a <a href="lync-server-2013-mediationservers-table.md">Tabela MediationServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>GatewayId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O gateway que a chamada está usando. Consulte a <a href="lync-server-2013-gateways-table.md">Tabela Gateways no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EdgeServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Borda que a chamada está usando. Consulte a <a href="lync-server-2013-edgeservers-table.md">Tabela EdgeServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipo de conteúdo usado na sessão. Consulte a <a href="lync-server-2013-contenttypes-table.md">Tabela ContentTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InviteTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>A hora da primeira solicitação INVITE. Este campo é geralmente preenchido por dados gerados da mensagem INVITE inicial em uma sessão. Se não houver mensagem INVITE, então o campo será preenchido com a data e hora da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE ou INFO).</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>A hora da primeira SIP RESPONSE. Este campo é geralmente preenchido por dados gerados da mensagem INVITE inicial em uma sessão. Se não houver mensagem INVITE, então o campo será preenchido com a data e hora da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE ou INFO).</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>O horário em que a sessão terminou.</p></td>
</tr>
<tr class="even">
<td><p><strong>UriTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Contém o valor do tipo do MCU URI do <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a>. Esse campo é usado para melhorar o desempenho da consulta.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica os atributos do usuário. As definições de atributo a seguir são listadas:</p>
<ul>
<li><p>Integrado com telefone de mesa - 1</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>CallFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica os atributos da chamada. As definições de atributo a seguir são listadas:</p>
<ul>
<li><p>Sessão Repetida - 1</p></li>
</ul></td>
</tr>
</tbody>
</table>


\* Para a maioria das sessões, SessionIdSeq terá o valor 1. Se várias sessões começarem exatamente ao mesmo tempo, o SessionIdSeq para uma será 1, para outra será 2 e assim por diante.

