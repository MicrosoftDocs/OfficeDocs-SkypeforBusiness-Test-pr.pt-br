---
title: Set-CsNetworkRegionLink
TOCTitle: Set-CsNetworkRegionLink
ms:assetid: b3d5d203-2aa7-4a54-93d4-30bcda391d68
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412867(v=OCS.15)
ms:contentKeyID: 49307859
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkRegionLink

 

_**Tópico modificado em:** 2015-03-09_

Modifica um link entre duas regiões de rede configuradas para o controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkRegionLink [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo altera o perfil da política de largura de banda do link da região de rede denominado NA\_EMEA para o perfil HighBWLimits. O nome do link da região de rede que queremos modificar é especificado como o valor do parâmetro Identity. Depois, atribuímos o valor HighBWLimits ao parâmetro BWPolicyProfile. Isto atribuirá as limitações de largura de banda definidas neste perfil de política de largura de banda (HighBWLimits) a conexões entre estas regiões.

    Set-CsNetworkRegionLink -Identity NA_EMEA -BWPolicyProfileID HighBWLimits

## Descrição detalhada

As regiões dentro de uma rede são vinculadas por meio da conectividade Wan. Este cmdlet modifica um link entre duas regiões, permitindo a alteração das regiões que estiverem vinculadas, assim como as limitações de largura de banda em conexões de áudio e vídeo entre essas regiões.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkRegionLink** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkRegionLink"}

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
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>A Identidade do perfil da política de largura de banda que definirá as limitações a este link. É possível recuperar uma lista de perfis disponíveis, chamando o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do link da região de rede que se deseja modificar. Como os links de região de rede são criados apenas no escopo global, esse identificador não precisa especificar um escopo. Em vez disto, ele contém uma cadeia de caracteres, que é um nome exclusivo que identifica este link.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>NetworkRegionLinkType</p></td>
<td><p>Uma referência de objeto a um link de região de rede. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType, que pode ser recuperado chamando o cmdlet <strong>Get-CsNetworkRegionLink</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>A Identidade (NetworkRegionID) da região que é vinculada à região identificada pela propriedade NetworkRegionID2.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>A Identidade (NetworkRegionID) da região que é vinculada à região identificada pela propriedade NetworkRegionID1.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType. Aceita entradas direcionadas dos objetos de link de região de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

