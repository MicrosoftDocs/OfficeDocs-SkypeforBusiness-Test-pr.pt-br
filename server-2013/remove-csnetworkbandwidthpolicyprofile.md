---
title: Remove-CsNetworkBandwidthPolicyProfile
TOCTitle: Remove-CsNetworkBandwidthPolicyProfile
ms:assetid: 7b1f3c8d-486c-4a7e-aa40-57893f249f66
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398609(v=OCS.15)
ms:contentKeyID: 49307209
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkBandwidthPolicyProfile

 

_**Tópico modificado em:** 2015-03-09_

Remove um perfil de diretiva de largura de banda de rede. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo remove o perfil de diretiva de largura de banda com identidade igual a LowBWProfile. Uma vez que as identidades precisam ser exclusivas, isso removerá no máximo um único perfil.

    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## EXEMPLO 2

O Exemplo 2 remove todas as referências ao perfil de diretiva de largura de banda com Identidade igual a LowBWProfile de todos os sites aos quais ele tenha sido atribuído e, em seguida, remove o perfil. A primeira linha deste exemplo começa com uma chamada para o cmdlet **Get-CsNetworkSite** para recuperar todos os sites configurados para o CAC (controle de admissão de chamadas). Essa coleção de sites é então canalizada para o cmdlet **Where-Object**, que procura apenas os sites nos quais BWPolicyProfileID seja igual a (-eq) LowBWProfile. Essa coleção refinada, contendo apenas os sites com valor de BWPolicyProfileID igual a LowBWProfile, é canalizada para **Set-CSNetworkSite**, que modifica cada um desses sites para alterar o BWPolicyProfileID para Null ($null). O que acabamos de fazer é encontrar todos os sites com BWPolicyProfileID igual a LowBWProfile e definir esse valor com Null. Nesse momento, não há mais sites usando o perfil LowBWProfile. Agora chamamos o cmdlet **Remove-CsNetworkBandwidthPolicyProfile** no perfil LowBWProfile para removê-lo, sabendo que ele não está sendo usado em nenhum site.

Para garantir que o perfil não esteja em uso em nenhum outro lugar da configuração de rede, realize as mesmas etapas da Linha 1 nas diretivas entre sites e nos links de região de rede.

    Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Set-CsNetworkSite -BWPolicyProfileID $null
    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## Descrição detalhada

Como parte de um controle de admissão de chamadas (CAC), uma diretiva de largura de banda é utilizada para definir limites para certas modalidades. (no Lync Server, somente as modalidades de áudio e vídeo podem receber a atribuição de limites de largura de banda). Este cmdlet remove um perfil que atua como contêiner para essas diretivas.

IMPORTANTE: Se um perfil tiver sido atribuído a um site (usando o cmdlet **New-CsNetworkSite** ou o cmdlet **Set-CsNetworkSite**), a uma diretiva entre sites (usando o cmdlet **New-CsNetworkInterSitePolicy** ou o cmdlet **Set-CsNetworkInterSitePolicy**) ou a um link de região de rede (usando o cmdlet **New-CsNetworkRegionLink** ou o cmdlet **Set-CsNetworkRegionLink**), ele não poderá ser removido. Você receberá um erro se tentar remover o perfil chamando o cmdlet **Remove-CsNetworkBandwidthPolicyProfile**. É preciso primeiro remover o perfil de todos os sites, diretivas entre sites e links de região de rede, para depois removê-lo.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Remove-CsNetworkBandwidthPolicyProfile** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkBandwidthPolicyProfile"}

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
<td><p>Um valor do tipo cadeia de caracteres que identifica exclusivamente o perfil de diretiva de largura de banda que você deseja remover. Quando você especifica uma Identity, vai remover no máximo um único perfil.</p></td>
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
<td><p>Suprime a exibição de qualquer prompt de confirmação que de outra forma seria exibido antes de se efetuar alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType. Aceita entrada em pipeline de objetos de perfil de diretiva de largura de banda.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

