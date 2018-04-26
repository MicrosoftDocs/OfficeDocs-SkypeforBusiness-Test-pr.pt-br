---
title: Set-CsNetworkInterSitePolicy
TOCTitle: Set-CsNetworkInterSitePolicy
ms:assetid: 973979bc-db2c-47a6-909e-5949a927f51c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398772(v=OCS.15)
ms:contentKeyID: 49307529
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkInterSitePolicy

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma política entre sites de rede existente que define as limitações de largura de banda entre sites que estiverem diretamente ligados em uma configuração de controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkInterSitePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkSiteID1 <String>] [-NetworkSiteID2 <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo modifica a política de site de rede com a identidade Reno\_Portland. O parâmetro BWPolicyProfileID é utilizado para alterar para HighBWLimits o perfil da política de largura de banda associado a essa política de site de rede.

    Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits

## Descrição detalhada

Quando os sites de uma rede compartilham um link direto, é possível definir limitações de largura de banda às conexões de áudio e vídeo entre esses dois sites. Este cmdlet modifica uma política entre sites de rede, que associa uma política de limitação de largura de banda a dois sites conectados diretamente.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkInterSitePolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkInterSitePolicy"}

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
<td><p>A identidade do perfil de política de largura de banda que definirá as limitações a esta política de site. É possível recuperar uma lista de perfis disponíveis, chamando o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>.SwitchParameter</p></td>
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
<td><p>O identificador exclusivo da política do site de rede que se deseja modificar. As políticas de site de rede são criadas apenas no escopo global, de forma que não é necessário que esse identificador especifique um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome exclusivo que identifica a política do site.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>InterNetworkSitePolicyType</p></td>
<td><p>Uma referência de objeto a uma política de site que tenha sido modificada na memória. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType e pode ser obtido chamando o cmdlet <strong>Get-CsNetworkInterSitePolicy</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSiteID1</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>A Identidade (NetworkSiteID) de um dos dois sites associados a essa política. A combinação de NetworkSiteID1 e NetworkSiteID2 deve ser exclusiva (por exemplo, não é possível que haja duas políticas de site definidas que conectem Reno e Portland).</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID2</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>A Identidade (NetworkSiteID) de um dos dois sites associados a essa política. A combinação de NetworkSiteID1 e NetworkSiteID2 deve ser exclusiva (por exemplo, não é possível que haja duas políticas de site definidas que conectem Reno e Portland).</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType. Aceita entrada direcionada dos objetos da política entre sites de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

