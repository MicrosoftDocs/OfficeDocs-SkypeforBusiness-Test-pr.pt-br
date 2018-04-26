---
title: Set-CsNetworkConfiguration
TOCTitle: Set-CsNetworkConfiguration
ms:assetid: d54dc154-c092-4be9-8656-f7fec3fbd835
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398927(v=OCS.15)
ms:contentKeyID: 49308225
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica as definições de uma configuração de rede. Na maioria das vezes, esse cmdlet será usado para habilitar ou desabilitar o controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfiles <PSListModifier>] [-Confirm [<SwitchParameter>]] [-EnableBandwidthPolicyCheck <$true | $false>] [-Force <SwitchParameter>] [-InterNetworkRegionRoutes <PSListModifier>] [-InterNetworkSitePolicies <PSListModifier>] [-MediaBypassSettings <MediaBypassSettingsType>] [-NetworkRegionLinks <PSListModifier>] [-NetworkRegions <PSListModifier>] [-NetworkSites <PSListModifier>] [-Subnets <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando desse exemplo executará uma verificação de validação em toda a configuração do CAC e, em seguida (dependendo de suas respostas a todos os prompts de aviso que forem retornados), habilitará o CAC. Se o CAC já estiver habilitado (em outras palavras, se a propriedade EnableBandwidthPolicyCheck for True) e você executar esse comando, ele simplesmente executará a verificação de validação.

    Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck $True

## Descrição detalhada

O objeto de configuração de rede contém todas as definições de uma configuração de CAC completa da implantação de um Lync Server, além das definições de desvio de mídia. É possível usar esse cmdlet para modificar qualquer parte da configuração de CAC e é necessário usá-lo se precisar alterar as definições de desvio de mídia. No entanto, ao se modificar a maioria das definições de configuração de CAC, é recomendável utilizar os cmdlets específicos ao tipo de objeto. Por exemplo, para trabalhar com regiões de rede, utilize os cmdlets que terminam com CsNetworkRegion, em vez de manipular o parâmetro NetworkRegions desse cmdlet.

O uso principal desse cmdlet é habilitar (e desabilitar) o CAC e aplicar as definições de desvio de mídia. Depois de definir os diversos componentes necessários à configuração (regiões, sites e sub-redes), será necessário habilitar a configuração, para que ela funcione. Para fazê-lo, simplesmente defina o parâmetro EnableBandwidthPolicyCheck como sendo True. Observe que a execução desse cmdlet com EnableBandwidthPolicyCheck definido como True não habilitará imediatamente o CAC. Antes que ele possa ser habilitado, é feita uma série de verificações de validação, para garantir que a instalação tenha sido configurada adequadamente. Qualquer erro ou discrepância na instalação exibirá avisos e perguntará se você deseja continuar a habilitar o CAC, mesmo que haja um problema. Se você preferir continuar (pressionando Enter ou Y), a validação continuará e perguntará novamente caso seja relatado outro problema.

Se você executar toda a validação, optando por continuar após cada aviso, EnableBandwidthPolicyCheck será definido como True e o CAC será habilitado, mas enquanto os problemas não forem solucionados, ele provavelmente não funcionará como esperado. Se, em algum momento da validação, você optar por interrompê-la (digitando N no prompt de aviso), ela será encerrada e EnableBandwidthPolicyCheck permanecerá definido como False (o padrão).

Se EnableBandwidthPolicyCheck já estiver definido como Verdadeiro, você poderá chamar o cmdlet **Set-CsNetworkConfiguration** e passar o valor Verdadeiro para o parâmetro EnableBandwidthPolicyCheck a fim de executar a validação sem modificar nenhuma configuração. Além disso, quando EnableBandwidthPolicyCheck for Verdadeiro, todas as alterações que você tentar realizar chamando o cmdlet **Set-CsNetworkConfiguration** farão com que a verificação de validação seja executada novamente.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkConfiguration"}

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
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>BWPolicyProfiles</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de todos os perfis de política de largura de banda que podem ser atribuídas a sites, políticas entre sites e links de região de rede. Cada perfil de política de largura de banda contém limitações de largura de banda (limitações gerais e de sessão) às conexões de áudio e/ou vídeo. É possível recuperar uma lista completa de perfis de política de largura de banda, chamando-se o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBandwidthPolicyCheck</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>A definição desse parâmetro como True executará uma verificação de validação em toda a configuração do CAC. Se as verificações de validação forem aprovadas ou se você optar por ignorar todos os avisos, o CAC será habilitado. Se uma verificação de validação não for aprovada, você poderá optar por interromper a validação e o valor de EnableBandwidthPolicyCheck não será alterado. Você precisa ter rotas de região definidas entre cada par de regiões de rede antes de executar a verificação de validação.</p>
<p>A definição desse valor como False desabilitará o CAC.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Este parâmetro não aceita qualquer valor. Se você incluir esse parâmetro, todas as alterações feitas na configuração, inclusive a sua habilitação, entrarão em vigor sem avisos ou verificações de validação.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Esse valor sempre será Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>NetworkConfigurationSettings</p></td>
<td><p>Uma referência a um objeto de configuração de rede. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings, que pode ser recuperado chamando-se o cmdlet <strong>Get-CsNetworkConfiguration</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>InterNetworkRegionRoutes</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de todas as rotas de região de rede definidas na configuração do CAC. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkInterRegionRoute</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkSitePolicies</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de políticas entre sites de rede, definidas na configuração do CAC. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkInterSitePolicy</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaBypassSettings</em></p></td>
<td><p>Opcional</p></td>
<td><p>MediaBypassSettingsType</p></td>
<td><p>Uma referência a um objeto que estabelece as definições globais de desvio de mídia da configuração do CAC. A definição desse valor substituirá todas as definições de desvio de mídia existentes. Essa referência de objeto é obtida chamando-se o cmdlet <strong>New-CsNetworkMediaBypassConfiguration</strong> e atribuindo-se as novas definições de configuração a uma variável. Passe essa variável para o parâmetro MediaBypassSettings, para alterar as definições globais de desvio de mídia.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de todos os links de região de rede, definidos na configuração do CAC. Cada link de região de rede define uma conexão existente entre duas regiões e qualquer limitação de largura de banda que deva ser aplicada a conexões entre essas regiões. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkRegionLink</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegions</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de regiões de rede (cada uma representando um hub ou backbone dentro da rede), definidas na configuração do CAC. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkRegion</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSites</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de locais de rede (cada um representando um escritório ou local de uma região), definidos na configuração do CAC. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkSite</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnets</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de sub-redes da rede (cada qual associa um ponto de extremidade a um site) definidas na configuração do CAC. É possível recuperar todos os membros dessa coleção, chamando-se o cmdlet <strong>Get-CsNetworkSubnet</strong>.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings. Aceita entrada canalizada de um objeto de configuração de rede.

## Tipos de retorno

O cmdlet **Set-CsNetworkConfiguration** não retorna nenhum valor ou objeto. Em vez disso, ele modifica as instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings.

## Consulte Também

#### Outros Recursos

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)

