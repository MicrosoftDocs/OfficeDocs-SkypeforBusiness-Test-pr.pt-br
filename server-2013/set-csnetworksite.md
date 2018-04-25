---
title: Set-CsNetworkSite
TOCTitle: Set-CsNetworkSite
ms:assetid: 221a099c-72c4-4eb0-8812-6b2b7639a9ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398295(v=OCS.15)
ms:contentKeyID: 49306120
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkSite

 

_**Tópico modificado em:** 2015-03-09_

Modifica um site de rede existente que tenha sido definido para controle de admissão de chamadas (CAC) ou Enhanced 9-1-1 (E9-1-1). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkSite [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-BypassID <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-LocationPolicy <String>] [-NetworkRegionID <String>] [-VoiceRoutingPolicy <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Neste exemplo, o site de rede denominado Vancouver é modificado. O nome do site sendo modificado é especificado como o valor do parâmetro Identity. O site de Vancouver está sendo transferido para uma nova região, que requer que o parâmetro NetworkRegionID seja alterado, neste caso, para a região denominada Canadá. Como um NetworkRegionID foi fornecido, mas nenhum valor foi especificado para BypassID, será gerado automaticamente um valor de BypassID. Qualquer ID de desvio previamente existente será sobrescrito.

    Set-CsNetworkSite -Identity Vancouver -NetworkRegionID Canada

## EXEMPLO 2

O Exemplo 2 simplesmente modifica o perfil da política de largura de banda associado ao site de Vancouver. O nome do site é especificado como o valor do parâmetro Identity. Em seguida, especifica-se um valor para o parâmetro BWPolicyProfileID: LowBWLimits. As políticas associadas a esse perfil serão utilizadas neste site.

    Set-CsNetworkSite -Identity Vancouver - BWPolicyProfileID LowBWLimits

## Descrição detalhada

Os sites de rede são os escritórios ou locais configurados em cada região de uma implantação do CAC ou E9-1-1. Esse cmdlet modifica as definições de um site existente. Isto pode incluir aspectos como a região associada ao site, a descrição do site e o perfil de política de largura de banda associado.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsNetworkSite** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkSite"}

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
<td><p>Cadeia</p></td>
<td><p>A Identidade do perfil da política de largura de banda que definirá as limitações a este site. É possível recuperar uma lista de perfis disponíveis, chamando-se o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p>
<p>Se for especificado um valor para esse parâmetro, será necessário especificar também o valor do parâmetro NetworkRegionID.</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Um identificador global exclusivo (GUID). Este GUID é usado para mapear sites de rede para definições de desvio de mediação em uma configuração de rede CAC ou E9-1-1. (utilize este valor de BypassID ao chamar o cmdlet <strong>New-CsNetworkMediaBypassConfiguration</strong>).</p>
<p>Se for especificado um valor para esse parâmetro, será necessário especificar também o valor do parâmetro NetworkRegionID. Se não for especificado um valor para este parâmetro, mas NetworkRegionID for especificado, BypassID será gerado automaticamente.</p>
<p>Se for explicitamente especificado um valor, ele deverá estar no formato de um GUID (por exemplo: 3b24a047-dce6-48b2-9f20-9fbff17ed62a). Recomendamos que você forneça um valor para NetworkRegionID e permita que o valor BypassID seja gerado automaticamente. Se você digitar um valor, receberá uma solicitação, indagando se não deseja gerar esse valor automaticamente.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Uma cadeia de caracteres que descreve o site. Este parâmetro pode ser utilizado para fornecer uma explicação mais descritiva sobre a função ou localização do site, superando o que pode ser expresso apenas pela identidade.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Quando definido como True, o roteamento de voz será gerenciado levando em conta a localização de ambos os usuários, o que faz a chamada e o que a recebe. O valor padrão é False.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do site de rede que se deseja modificar. Como os sites são criados apenas no escopo global, não é necessário especificar o escopo. Em vez disso, é necessário especificar apenas o ID do site de rede.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>DisplayNetworkSiteType</p></td>
<td><p>Uma referência a um objeto de site de rede (um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType). Este objeto pode ser recuperado chamando-se o cmdlet <strong>Get-CsNetworkSite</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocationPolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>O nome da política de local associada a este site. A política de local atribui ao site definições do E9-1-1 específicas. Para recuperar uma lista de políticas de local, chame o cmdlet <strong>Get-CsLocationPolicy</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A identidade da região de rede à qual este site está associado. Este parâmetro deve conter um valor, se se desejar fornecer um BypassID (mediante a geração automática ou manual) ou se a propriedade EnableBandwidthPolicyCheck da configuração de rede for True. É possível recuperar as definições de configuração de rede chamando-se o cmdlet <strong>Get-CsNetworkConfiguration</strong>.</p>
<p>Se este site já tiver um BypassID e não se especificar um valor para o parâmetro BypassID, o BypassID existente será sobrescrito por um BypassID gerado automaticamente.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceRoutingPolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A política de roteamento de voz por usuário pode ser atribuída ao site. Por exemplo:</p>
<p>-VoiceRoutingPolicy &quot;RedmondVoiceRouting”</p>
<p>Observe que você deve especificar uma política por usuário. Políticas globais e/ou de site não podem ser atribuídas a um site usando o parâmetro VoiceRoutingPolicy.</p>
<p>Esse parâmetro foi introduzido na versão de fevereiro de 2013 do Lync Server 2013.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType. Aceita entradas canalizadas dos objetos de site de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkSite](new-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)

