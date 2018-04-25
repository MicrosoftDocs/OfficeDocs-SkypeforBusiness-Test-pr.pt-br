---
title: Remove-CsNetworkRegionLink
TOCTitle: Remove-CsNetworkRegionLink
ms:assetid: f26cde90-e789-44a7-a304-695c85e64403
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413012(v=OCS.15)
ms:contentKeyID: 49308566
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkRegionLink

 

_**Tópico modificado em:** 2015-03-09_

Remove um link entre duas regiões configuradas para o CAC (controle de admissão de chamadas). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse primeiro exemplo remove um link de região de rede cuja identidade for NA\_EMEA.

    Remove-CsNetworkRegionLink -Identity NA_EMEA

## EXEMPLO 2

O Exemplo 2 remove todos os links de região de rede que utilizam o perfil da política de largura de banda denominado HighBWLimits. O primeiro cmdlet chamado no exemplo é o **Get-CsNetworkRegionLink** (sem parâmetros), que recupera todos os links de região. Esta coleção de links é então canalizada ao cmdlet **Where-Object**. O cmdlet **Where-Object** examina cada membro da coleção, verificando o valor da propriedade BWPolicyProfileID. Se esta propriedade for igual a (-eq) HighBWLimits, nós canalizaremos o membro ao cmdlet **Remove-CsNetworkRegionLink**, que removerá o link.

    Get-CsNetworkRegionLink | Where-Object {$_.BWPolicyProfileID -eq "HighBWLimits"} | Remove-CsNetworkRegionLink

## Descrição detalhada

As regiões dentro de uma rede são vinculadas por meio da conectividade Wan. Esse cmdlet não afeta qualquer conexão física, mas remove o link da configuração de CAC.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsNetworkRegionLink** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkRegionLink"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do link da região de rede que se deseja remover. Como os links de região de rede são criados apenas no escopo global, esse identificador não precisa especificar um escopo. Em vez disto, ele contém uma cadeia de caracteres que é um nome exclusivo que identifica este link.</p></td>
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
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType. Aceita entrada canalizada dos objetos de link de região de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)

