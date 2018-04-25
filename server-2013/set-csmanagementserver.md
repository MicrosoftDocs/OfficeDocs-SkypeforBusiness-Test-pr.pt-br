---
title: Set-CsManagementServer
TOCTitle: Set-CsManagementServer
ms:assetid: 6607580d-f111-4dff-961a-71525bf2e482
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398465(v=OCS.15)
ms:contentKeyID: 49306938
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsManagementServer

 

_**Tópico modificado em:** 2015-03-09_

Modifies the replication port used by the Lync Server Serviço de Gerenciamento Central. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsManagementServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplicationServicePort <UInt16>] [-WhatIf [<SwitchParameter>]]

## Examples

## EXAMPLE 1

The command shown in Example 1 connects to the Serviço de Gerenciamento Central with the Identity ManagementServer:atl-cs-001.litwareinc.com and sets the replication service port to port 5076.

    Set-CsManagementServer -Identity "ManagementServer:atl-cs-001.litwareinc.com" -ReplicationServicePort 5076

## Detailed Description

The Serviço de Gerenciamento Central is responsible for replicating data between the Repositório de Gerenciamento Central and computers running Lync Server services or server roles. The Serviço de Gerenciamento Central runs on a single Pool de Front-Ends (or a single Servidor Standard Edition) and facilitates replication throughout the Lync Server infrastructure.

The **Set-CsManagementServer** cmdlet enables you to specify the port that the Serviço de Gerenciamento Central uses for replication.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsManagementServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsManagementServer"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique identifier for the Serviço de Gerenciamento Central. For example: -Identity &quot;ManagementServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;ManagementServer:&quot; when specifying a Servidor de Gerenciamento Central. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicationServicePort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port number for the replication port used by the Serviço de Gerenciamento Central.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Input Types

None. The **Set-CsManagementServer** cmdlet does not accept pipelined input.

## Return Types

The **Set-CsManagementServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayManagementServer object.

## Consulte Também

#### Outros Recursos

[Get-CsService](get-csservice.md)  
[Move-CsManagementServer](move-csmanagementserver.md)

