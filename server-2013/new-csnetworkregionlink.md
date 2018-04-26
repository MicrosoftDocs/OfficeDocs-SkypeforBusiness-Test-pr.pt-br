---
title: New-CsNetworkRegionLink
TOCTitle: New-CsNetworkRegionLink
ms:assetid: 61a6a7be-8078-4d59-a78a-2f241f6bf800
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398437(v=OCS.15)
ms:contentKeyID: 49306888
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkRegionLink

 

_**Tópico modificado em:** 2015-03-09_

Cria um link entre duas regiões configuradas para o CAC (controle de admissão de chamadas). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsNetworkRegionLink -NetworkRegionLinkID <String> <COMMON PARAMETERS>

    New-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID1 <String> -NetworkRegionID2 <String> [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo cria um novo link de região de rede chamado NA\_EMEA para vincular as regiões NorthAmerica e EMEA. O link de região é especificado como o valor do parâmetro Identity. (Ele será atribuído automaticamente como valor de NetworkRegionLinkID.) As duas regiões de rede que estão sendo vinculadas são parâmetros exigidos para a criação do link. Neste caso, as regiões se chamam NorthAmerica e EMEA. No exemplo, também atribuímos um valor ao parâmetro BWPolicyProfile. Isso irá atribuir as limitações de largura de banda definidas no perfil de diretiva de largura de banda (LowBWLimits) para conexões entre essas regiões. Se nenhum BWPolicyProfileID for fornecido, não haverá limitações nas conexões entre essas duas regiões. (ainda podem haver limitações entre sites. para detalhes, consulte o tópico de Ajuda do cmdlet **New-CsNetworkSite**).

    New-CsNetworkRegionLink -Identity NA_EMEA -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID LowBWLimits

## Descrição detalhada

Regiões dentro de uma rede são vinculadas por conectividade WAN física. Este cmdlet define um link entre duas regiões e define as limitações de largura de banda em conexões de áudio e vídeo entre essas regiões.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **New-CsNetworkRegionLink** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkRegionLink"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Um identificador exclusivo para o link de região de rede recém-criado. Links de regiões de rede são criadas apenas em escopo global, então o identificador não precisa especificar um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome único para identificação do link.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>A identidade (NetworkRegionID) da região que está vinculada à região identificada pelo parâmetro NetworkRegionID2.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>A identidade (NetworkRegionID) da região que está vinculada à região identificada pelo parâmetro NetworkRegionID1.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinkID</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>O valor é o mesmo da Identity. Você não pode especificar tanto uma Identity quanto um NetworkRegionLinkID; o valor digitado para um será usado automaticamente para ambos.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>A identidade do perfil de diretiva de largura de banda que definirá as limitações de largura de banda do link. Para recuperar uma lista de perfis disponíveis, chame o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime todos os avisos de confirmação que seriam exibidos antes que as alterações sejam feitas.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Este cmdlet cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

## Consulte Também

#### Outros Recursos

[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkSite](new-csnetworksite.md)

