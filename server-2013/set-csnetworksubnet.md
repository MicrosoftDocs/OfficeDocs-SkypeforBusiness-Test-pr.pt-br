---
title: Set-CsNetworkSubnet
TOCTitle: Set-CsNetworkSubnet
ms:assetid: 9e85cdbb-b5fb-48d6-8f95-6e7cba9d9597
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412739(v=OCS.15)
ms:contentKeyID: 49307628
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkSubnet

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma sub-rede existente. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkSubnet [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-MaskBits <Int32>] [-NetworkSiteID <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo modifica a sub-rede com identidade (o ID de sub-rede) 172.11.15.0. A sub-rede é modificada com um novo valor de MaskBits (25) e um novo NetworkSiteID (Chicago).

    Set-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 25 -NetworkSiteID Chicago

## EXEMPLO 2

O Exemplo 2 move todas as sub-redes no site Vancouver para o site Chicago. Para isso, começamos chamando o cmdlet **Get-CsNetworkSubnet**, que recuperará um conjunto de todas as sub-redes definidas na implementação do Lync Server. Esse conjunto de sub-redes é então direcionado para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringe o conjunto apenas às sub-redes com NetworkSiteID igual a (-eq) Vancouver. Agora que o conjunto consiste apenas de sub-redes associadas ao site Vancouver, a coleção é direcionada para o cmdlet **Set-CsNetworkSubnet**. Fornecemos um parâmetro para o cmdlet **Set-CsNetworkSubnet**: NetworkSiteID. Passando para o parâmetro o valor Chicago, instruímos o cmdlet **Set-CsNetworkSubnet** a alterar o ID do site de rede de todos os integrantes da coleção para Chicago.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Set-CsNetworkSubnet -NetworkSiteID Chicago

## Descrição detalhada

Cada sub-rede deve ser associada a um site de rede para que seja determinada a localização geográfica do host que pertence a essa sub-rede. Use este cmdlet para modificar o site de rede associado, alterar a descrição da sub-rede ou modificar os bits de máscara da sub-rede.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkSubnet** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkSubnet"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Uma descrição da sub-rede que será modificada.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime eventuais avisos de confirmação que seriam exibidos antes da realização das alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O ID exclusivo da sub-rede que será modificada. Este valor será um endereço IP (como 174.11.12.0) ou uma URL começando com http: ou https:.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>SubnetType</p></td>
<td><p>Uma referência ao objeto de sub-rede da rede que será modificado. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType, que pode ser recuperado chamando o cmdlet <strong>Get-CsNetworkSubnet</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>MaskBits</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>A bitmask a ser aplicada à sub-rede.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>O ID do site de rede à qual a sub-rede será aplicada. É possível recuperar IDs de sites da sua implementação chamando o cmdlet <strong>Get-CsNetworkSite</strong>.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType. Aceita entrada por pipeline de objetos de sub-rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)

