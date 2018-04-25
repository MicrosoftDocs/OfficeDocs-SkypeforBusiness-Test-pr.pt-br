---
title: 'Lync Server 2013: Tabela Session'
TOCTitle: Tabela Session
ms:assetid: 7f05529c-794d-41ed-bca4-2e85b87b2dec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398635(v=OCS.15)
ms:contentKeyID: 49307255
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Session no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma sessão que envolve áudio ou áudio e vídeo. Ele contém informações gerais sobre a sessão. Uma sessão é definida como um diálogo de protocolo SIP de áudio ou vídeo entre dois pontos de extremidade.


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
<td><p>Referência na <a href="lync-server-2013-dialog-table.md">Tabela Dialog no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Referência na <a href="lync-server-2013-dialog-table.md">Tabela Dialog no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Chave de conferência. Referência da <a href="lync-server-2013-conference-table.md">Tabela Conference no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CorrelationKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Chave de correlação. Referência da <a href="lync-server-2013-sessioncorrelation-table.md">Tabela SessionCorrelation no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogCategory</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Categoria da caixa de diálogo; 0 é o Lync Server para o trecho Servidor de Mediação; 1 é o Servidor de Mediação para o trecho gateway PSTN.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediationServerBypassFlag</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Sinalizador que indica se a chamada foi ignorada ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaBypassWarningFlag</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Este campo, se presente, indica por que uma chamada não foi ignorada, mesmo se as IDs o desvio correspondem. Para o Lync Server, apenas um valor é definido.</p>
<p>0x0001 - ID de desvio desconhecida ao adaptador de rede padrão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora de início</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Hora de início da chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Hora de término da chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPool</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O pool do chamador. Referência da <a href="lync-server-2013-pool-table.md">Tabela Pool no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleePool</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O pool do receptor. Referência da <a href="lync-server-2013-pool-table.md">Tabela Pool no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleePAI</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI de SIP na identidade declarada (PAI) do SIP do ponto de extremidade de recebimento. Referência da <a href="lync-server-2013-user-table.md">Tabela User no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerURI</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI do chamador. Referência da <a href="lync-server-2013-user-table.md">Tabela User no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerEndpoint</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Ponto de extremidade do chamador. Referência da <a href="lync-server-2013-endpoint-table.md">Tabela Endpoint no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerUserAgent</strong></p></td>
<td><p>bit</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Agente de usuário do chamador. Referência da <a href="lync-server-2013-useragent-table.md">Tabela UserAgent no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallPriority</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>A prioridade desta chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClassifiedPoorCall</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Essa coluna foi deprecada e não é usada em Microsoft Lync Server 2013. Em vez disso, essas informações são relatadas em bases de linha por mídia. Consulte <a href="lync-server-2013-medialine-table.md">Tabela MediaLine no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPAI</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O P-Asserted-Identity do usuário que fez a chamada. O P-Asserted-Identity (PAI) é usado para transmitir a identidade verdadeira do usuário que fez a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeEndpoint</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Ponto de extremidade que recebeu a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeUserAgent</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Agente de usuário empregado pelo usuário que recebeu a chamada. Os agentes representam o dispositivo de ponto de extremidade do cliente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeUri</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI SIP do usuário que recebeu a chamada.</p></td>
</tr>
</tbody>
</table>

