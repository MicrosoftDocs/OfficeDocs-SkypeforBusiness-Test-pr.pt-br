---
title: 'Lync Server 2013: Tabela de registro'
TOCTitle: Tabela de registro
ms:assetid: 05ff9dd3-1aaa-4af0-bd69-8789fb8eaeb3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398114(v=OCS.15)
ms:contentKeyID: 49305771
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela de registro no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa um evento de registro de usuário.


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
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>A ID do usuário. Consulte <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a>para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>EndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p></p></td>
<td><p>Um GUID para identificar um ponto de extremidade de registro. Geralmente, o evento de registro do mesmo computador do mesmo usuário terá a mesma ID de ponto de extremidade. Máquinas diferentes possuem uma ID de ponto de extremidade diferente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EndpointEra</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>ID usado para diferenciar registros que envolvem o mesmo usuário e o mesmo ponto de extremidade.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Versão do cliente do usuário atual. Consulte <a href="lync-server-2013-clientversions-table.md">Tabela ClientVersions no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RegistrarId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do Servidor Registrador usado para registro. Consulte <a href="lync-server-2013-servers-table.md">Tabela de servidores no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>ID do pool em que a sessão foi capturada. Consulte <a href="lync-server-2013-pools-table.md">Tabela Pools no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EdgeServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Servidor de Borda pelo qual o registro está passando. Consulte <a href="lync-server-2013-edgeservers-table.md">Tabela EdgeServers no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsInternal</strong></p></td>
<td><p>Bit</p></td>
<td><p></p></td>
<td><p>Quer o usuário esteja conectado internamente ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsUserServiceAvailable</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Quer o UserService esteja disponível ou não.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsPrimaryRegistrar</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Quer registre-se no primeiro Registrador ou não.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsPrimaryRegistrarCentral</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Indica se o usuário é registrado com um Aparelho de Filial Persistente.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RegisterTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Período de registro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeRegisterTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Período de cancelamento de registro.</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Código de resposta da solicitação de registro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DiagnosticId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>ID do diagnóstico da solicitação de registro, que indica o tipo de informação de diagnóstico.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O dispositivo do qual a solicitação de registro está vindo. Consulte <a href="lync-server-2013-devices-table.md">Tabela Devices no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeRegisterTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Estrangeiro</p></td>
<td><p>O motivo do cancelamento do registro, como &quot;iniciado pelo usuário&quot;, &quot;registro expirado&quot;, &quot;falha do cliente&quot; e mais. Consulte <a href="lync-server-2013-deregistertype-table.md">Tabela DeRegisterType no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>IPAddress</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Endereço IP do ponto da extremidade com o qual o usuário é registrado. Pode ser um endereço IPv4 ou IPv6.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

