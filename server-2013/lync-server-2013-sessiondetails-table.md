---
title: 'Lync Server 2013: Tabela SessionDetails'
TOCTitle: Tabela SessionDetails
ms:assetid: 783d2508-e31f-4b54-be0c-63aa5ec21c04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398589(v=OCS.15)
ms:contentKeyID: 49307172
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela SessionDetails no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma sessão ponto a ponto, que poderia ser uma chamada telefônica VoIP-VoIP, uma sessão de IM de duas partes ou outro tipo de sessão. Você pode executar uma junção de tabela com a [Tabela Media no Lync Server 2013](lync-server-2013-media-table.md) para encontrar os detalhes de cada mídia envolvida nessa sessão.

Observe que os campos IsUser1IntegratedWithDeskPhone e IsUser2IntegratedWithDeskPhone foram retirados da tabela SessionDetails usada no Microsoft Lync Server 2013.


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
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>O número de ID para identificar a sessão.* Usado em conjunto com <strong>SessionIdTime</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CorrelationId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p></p></td>
<td><p>Um GUID para correlacionar várias sessões.</p></td>
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
<td><p><strong>User1Id</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A ID de um usuário na sessão. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User2Id</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A ID de outro usuário na sessão. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>User1EndpointId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>GUID que identifica o ponto de extremidade usado pelo primeiro usuário na sessão.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User2EndpointId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>GUID que identifica o ponto de extremidade usado pelo segundo usuário na sessão.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>TargetUserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A solicitação original Para o URI do usuário no SIP. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionStartedById</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A ID do usuário que iniciou a sessão. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
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
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do servidor front-end usado para esta sessão. Consulte <a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do pool em que a sessão foi capturada. Consulte <a href="lync-server-2013-pools-table.md">Tabela Pools no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentTypeID</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipo de conteúdo usado na sessão. Consulte a <a href="lync-server-2013-contenttypes-table.md">Tabela ContentTypes no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User1ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A versão do cliente usada pelo Usuário1. Consulte a <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>User2ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A versão do cliente usada pelo Usuário2. Consulte a <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User1EdgeServerid</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Borda usado pelo Usuário1. Consulte a <a href="lync-server-2013-edgeservers-table.md">Tabela EdgeServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>User2EdgeServerid</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O Servidor de Borda usado pelo Usuário2. Consulte a <a href="lync-server-2013-edgeservers-table.md">Tabela EdgeServers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsUser1Internal</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Se o Usuário1 está conectado internamente ou não.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsUser2Internal</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Se o Usuário2 está conectado internamente ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InviteTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>O horário da primeira solicitação INVITE. Este campo é tipicamente preenchido pelos dados gerados pela mensagem INVITE inicial na sessão. Se não houver mensagem INVITE, o campo será preenchido com a data e hora da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE ou INFO).</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>O tempo de resposta da primeira mensagem INVITE. Este campo é tipicamente preenchido pelos dados gerados pela mensagem INVITE inicial na sessão. Se não houver mensagem INVITE, o campo será preenchido com a data e hora da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE ou INFO).</p></td>
</tr>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>O código de resposta SIP para o convite de sessão. Este campo é normalmente preenchido pelos dados gerados a partir da mensagem INVITE inicial na sessão. Caso não exista uma mensagem INVITE então o campo é preenchido com a data e horário da primeira mensagem SIP relevante (BYE, CANCEL, MESSAGE, ou INFO).</p></td>
</tr>
<tr class="even">
<td><p><strong>DiagnosticId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>ID de diagnóstico capturado do cabeçalho do SIP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallPriority</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Prioridade de chamada. Consulte a <a href="lync-server-2013-callpriorities-table.md">Tabela CallPriorities no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>User1MessageCount</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>O número de mensagens enviadas pelo Usuário1 durante a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User2MessageCount</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>O número de mensagens enviadas pelo Usuário2 durante a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Hora ao final da sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaTypes</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica o tipo de mídia esta sessão. As definições dos tipos estão listadas:</p>
<h3 id="section-1"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>IM</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>FILE_TRANSFER</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>REMOTE_ASSISTANCE</p></td>
<td><p>4</p></td>
</tr>
<tr class="even">
<td><p>APP_SHARING</p></td>
<td><p>8</p></td>
</tr>
<tr class="odd">
<td><p>AUDIO</p></td>
<td><p>16</p></td>
</tr>
<tr class="even">
<td><p>VIDEO</p></td>
<td><p>32</p></td>
</tr>
<tr class="odd">
<td><p>APP_INVITE</p></td>
<td><p>64</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>User1Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica os atributos do Usuário1. As seguintes definições de atributo são listadas:</p>
<ul>
<li><p>0x01 - Integrado com telefone de mesa</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>User2Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica os atributos do Usuário2. As seguintes definições de atributo são listadas:</p>
<ul>
<li><p>0x01 - Integrado com telefone de mesa</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>CallFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Um conjunto de bits que indica os atributos da chamada. As definições de atributo a seguir são listadas:</p>
<ul>
<li><p>0x01 - Sessão repetida</p></li>
<li><p>0x02 - Uma chamada feita pelo operador em nome de um grupo de resposta</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Processado</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Para uso interno pelo serviço de Monitoramento.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


\* Para a maioria das sessões, SessionIdSeq terá o valor 1. Se várias sessões começarem exatamente ao mesmo tempo, o SessionIdSeq para uma será 1, para outra será 2 e assim por diante.

