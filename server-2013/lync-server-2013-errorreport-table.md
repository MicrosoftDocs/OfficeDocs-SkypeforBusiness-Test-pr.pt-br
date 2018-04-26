---
title: 'Lync Server 2013: Tabela ErrorReport'
TOCTitle: Tabela ErrorReport
ms:assetid: ae0287b4-e8ca-4f8c-84ef-502897dcaa2a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412826(v=OCS.15)
ms:contentKeyID: 49307808
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ErrorReport no Lync Server 2013

 

_**Tópico modificado em:** 2015-06-22_

A tabela ErrorReport armazena informações sobre erros ocorridos. Cada registro é uma ocorrência de erro. Os erros são capturados pelo agente CDR executado no servidor front-end ou enviados pelo cliente.


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
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Data e horário em que o erro aconteceu.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>ID numérico para identificar o relatório do erros. Usado em conjunto com <strong>ErrorTime</strong> para identificar de forma exclusiva um relatório de erros.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID única do tipo de erro. Consulte a <a href="lync-server-2013-errordef-table.md">Tabela ErrorDef no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromUserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O usuário que originou a solicitação que causou o erro. Consulte a <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToUserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O usuário de destino para a solicitação que causou o erro. Consulte a <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI de conferência relacionada ao erro. Consulte a <a href="lync-server-2013-conferenceuris-table.md">Tabela ConferenceUris no Lync Server 2013</a> para obter mais informações. Normalmente, se ConferenceUriId não for nulo, então FromUserId ou ToUserId será nulo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Usado em conjunto com <strong>SessionIdSeq</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O servidor que enviou o relatório de erro (se o relatório estiver sendo enviado de um componente do servidor). Consulte <a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a> para obter mais informações.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O servidor que enviou o relatório de erro (se o relatório estiver sendo enviado de um componente do servidor). Consulte <a href="lync-server-2013-application-table.md">Tabela de aplicativos no Lync Server 2013</a> para obter mais informações.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagHeader</strong></p></td>
<td><p>imagem</p></td>
<td><p> </p></td>
<td><p>Mais informações sobre o erro.</p>
<p>Este dado pode ser convertido para o formato de texto usando esta sintaxe:</p>
<p><code>cast(cast(Detail as varbinary(max)) as varchar(max)) </code></p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A versão do cliente do ponto de extremidade que envia o relatório de erros. Consulte a <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsCapturedByServer</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>É o relatório de erros capturado pelo agente de CDR em execução no servidor front-end, ou enviado pelo cliente.</p></td>
</tr>
<tr class="even">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Reservado para uso futuro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>Identificador exclusivo relacionando a informação do tempo de participação para diferentes componentes envolvidos em uma conferência.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Tempo (em milissegundos) exigido para um componente específico participar de uma conferência.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Representa o nome de domínio totalmente qualificado do servidor que gerou o relatório de erro.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Representa o nome de domínio totalmente qualificado do pool onde o relatório de erro foi gerado.</p></td>
</tr>
</tbody>
</table>

