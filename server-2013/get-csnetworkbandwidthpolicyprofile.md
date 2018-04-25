---
title: Get-CsNetworkBandwidthPolicyProfile
TOCTitle: Get-CsNetworkBandwidthPolicyProfile
ms:assetid: 31784852-0cf4-4114-bf92-5eef6f346c47
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425815(v=OCS.15)
ms:contentKeyID: 49306308
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkBandwidthPolicyProfile

 

_**Tópico modificado em:** 2015-03-09_

Recupera um ou mais perfis de política de largura de banda de rede. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkBandwidthPolicyProfile [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

A chamada do cmdlet **Get-CsNetworkBandwidthPolicyProfile** sem parâmetros irá recuperar todos os perfis de política de largura de banda definidos na implantação do Lync Server.

    Get-CsNetworkBandwidthPolicyProfile

## EXEMPLO 2

Esse exemplo recupera o perfil de política de largura de banda com a Identidade LowBWProfile. Pelo fato de as identidades serem exclusivas, isso retornará, no máximo, um perfil.

    Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## EXEMPLO 3

Nesse exemplo, usamos o parâmetro Filter para especificar um ou vários perfis a serem recuperados, com base em uma cadeia de caracteres curinga. Usamos a cadeia de caracteres \*50MB\*, que indica que queremos recuperar todos os perfis de política de largura de banda com valores de Identidade que contenham a cadeia de caracteres 50MB em qualquer posição do valor. Por exemplo, isso recupera perfis com identidades como “BW profile for 50MB links”, “50MB audio limit”, e “video limits of 50MB”.

    Get-CsNetworkBandwidthPolicyProfile -Filter *50MB*

## Descrição detalhada

As políticas de largura de banda, que integram o controle de admissão de chamadas (CAC), são usadas para definir as limitações de largura de banda para determinadas modalidades. (no Lync Server, as limitações de largura de banda podem ser atribuídas apenas às modalidades de áudio e vídeo). Esse cmdlet recupera um ou vários perfis de contêiner correspondentes a essas políticas.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsNetworkBandwidthPolicyProfile** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkBandwidthPolicyProfile"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma cadeia de caracteres que contém curingas, usada para recuperar perfis de política de largura de banda que possuem valores de Identidade correspondentes ao padrão de curinga.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Um valor de cadeia de caracteres que identifica exclusivamente o perfil de política de largura de banda a ser recuperado. A especificação de uma Identidade irá recuperar, no máximo, um perfil.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera o perfil da política de largura de banda da rede na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

