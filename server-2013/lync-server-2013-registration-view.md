---
title: Exibir Registro
TOCTitle: Exibir Registro
ms:assetid: 8a42bc7d-3d4f-43c1-9e15-89b2ee419ade
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688120(v=OCS.15)
ms:contentKeyID: 49886299
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Registro

 

_**Tópico modificado em:** 2015-03-09_

A visualização "Registro" armazena informações sobre o registro do usuário. Esse é um novo recurso do Lync Server 2013.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora da solicitação da sessão. Usada com o parâmetro SessionIdSeq para identificar a sessão com atributos exclusivos. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Número de identificação para identificar a sessão. Usado com o parâmetro SessionIdTime para identificar a sessão com atributos exclusivos. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RegisterTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora do registro.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>URI do usuário registrado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Tipo de URI do usuário registrado. Consulte <a href="lync-server-2013-uritypes-table.md">Tabela UriTypes no Lync Server 2013</a>para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Locatário do usuário registrado. Consulte <a href="lync-server-2013-tenants-table.md">Tabela Tenants no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Identificador exclusivo do ponto de extremidade em que o usuário se registrou.</p></td>
</tr>
<tr class="even">
<td><p><strong>EndpointEra</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Identificador exclusivo usado para diferenciar registros que envolvam o mesmo usuário e o mesmo ponto de extremidade.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeRegisterType</strong></p></td>
<td><p>datetime</p></td>
<td><p>Hora do cancelamento do registro.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeRegisterReason</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Motivo para o cancelamento do registro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Versão do cliente usada no registro.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientType</strong></p></td>
<td><p>int</p></td>
<td><p>Cliente usado pelo usuário no registro. Consulte <a href="lync-server-2013-useragentdef-table.md">Tabela UserAgentDef no Lync Server 2013</a> para obter mais detalhes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>Categoria do cliente do usuário no registro.</p></td>
</tr>
<tr class="even">
<td><p><strong>IpAddress</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Endereço IP com o qual o usuário se registrou. Pode ser um endereço IPv4 ou IPv6.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogId</strong></p></td>
<td><p>varstring(775)</p></td>
<td><p>ID do diálogo de SIP. O formato é:</p>
<p>diálogo;tag-de;tag-para</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p>Código de resposta SIP para o convite da sessão. Esse campo geralmente é preenchido com os dados gerados pela mensagem inicial &quot;INVITE&quot; da sessão. Se não houver uma mengem &quot;INVITE&quot;, o campo será preenchido com a data e a hora da primeira mensagem de SIP útil (&quot;BYE&quot;, &quot;CANCEL&quot;, &quot;MESSAGE&quot; ou &quot;INFO&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><strong>DiagnosticId</strong></p></td>
<td><p>int</p></td>
<td><p>ID de diagnóstico registrado do cabeçalho do SIP.</p></td>
</tr>
<tr class="even">
<td><p><strong>Registrar</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>FQDN do registrador.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>FQDN do pool que registrou os dados da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>EdgeServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>FQDN do servidor de borda usado pelo usuário que se registrou.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsInternal</strong></p></td>
<td><p>bit</p></td>
<td><p>Indica se o usuário fez logon a partir da rede interna.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsUserServiceAvailable</strong></p></td>
<td><p>bit</p></td>
<td><p>Indica se o UserService estava disponível no momento do registro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsPrimaryRegistrar</strong></p></td>
<td><p>bit</p></td>
<td><p>Indica se o registro foi feito com o registrador principal.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceMacAddress</strong></p></td>
<td><p>bigint</p></td>
<td><p>Endereço MAC do dispositivo registrado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceManufacturer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Fabricante do dispositivo registrado. Consulte <a href="lync-server-2013-manufacturers-table.md">Tabela Manufacturers no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHardwareVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Versão do hardware do dispositivo registrado. Consulte <a href="lync-server-2013-hardwareversions-table.md">Tabela HardwareVersions no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
</tbody>
</table>

