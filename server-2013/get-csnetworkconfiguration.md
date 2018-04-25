---
title: Get-CsNetworkConfiguration
TOCTitle: Get-CsNetworkConfiguration
ms:assetid: 08bc8eca-b244-4d5e-b089-1cc95605ba14
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398140(v=OCS.15)
ms:contentKeyID: 49305807
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Recupera configurações globais do CAC (controle de admissão de chamadas), do E9-1-1 (Enhanced 9-1-1) e da passagem livre de mídia. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Este exemplo recupera as configurações de rede. Essas configurações são definidas apenas em escopo global, então apenas um item será retornado.

    Get-CsNetworkConfiguration

## EXEMPLO 2

Há apenas um conjunto de configurações de passagem livre de mídia que se aplicam globalmente. Essas configurações são armazenadas como parte da configuração geral de rede. O comando primeiro recupera essa configuração chamando o cmdlet **Get-CsNetworkConfiguration** e recupera a propriedade MediaBypassSettings da configuração.

    (Get-CsNetworkConfiguration).MediaBypassSettings

## Descrição detalhada

O objeto de configuração de rede contém todas as definições globais de passagem livre de mídia e de uma configuração completa do CAC em uma implementação do Lync Server, incluindo o fato de essa configuração ter sido habilitada ou não. Este cmdlet pode ser usado para recuperar essas configurações e definições. Entretanto, além de EnableBandwidthPolicyCheck e MediaBypassSettings, recomenda-se o uso de cmdlets específicos do tipo do objeto para a recuperação das configurações do CAC. Por exemplo, para recuperar as regiões da rede, geralmente será mais fácil chamar o cmdlet **Get-CsNetworkRegion** do que o **Get-CsNetworkConfiguration** para então recuperar a propriedade NetworkRegions dessa configuração.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsNetworkConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Como sempre haverá apenas uma configuração de rede, você não precisará desse parâmetro nesse cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Este sempre será Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera a configuração de rede a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Get-CsNetworkConfiguration** retorna uma instância do objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings.

## Consulte Também

#### Outros Recursos

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

