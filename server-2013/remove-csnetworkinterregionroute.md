---
title: Remove-CsNetworkInterRegionRoute
TOCTitle: Remove-CsNetworkInterRegionRoute
ms:assetid: 91948c03-2bcb-4e25-b0b6-23827e85bbb3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398743(v=OCS.15)
ms:contentKeyID: 49307475
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkInterRegionRoute

 

_**Tópico modificado em:** 2015-03-09_

Remove uma rota que conecta regiões da rede na configuração de um controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 remove a rota cuja identidade for NA\_APAC\_Route.

    Remove-CsNetworkInterRegionRoute -Identity NA_APAC_Route

## EXEMPLO 2

O Exemplo 2 remove todas as rotas de região que incluírem a região NorthAmerica. A primeira parte do comando é uma chamada ao cmdlet **Get-CsNetworkInterRegionRoute**. Este cmdlet, chamado sem parâmetros, recuperará todas as rotas de região. A seguir, esta coleção será canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringirá a coleção apenas às rotas que tiverem NorthAmerica definida como uma de suas regiões. Ela faz isso verificando se a rota tem um valor de NetworkRegionID1 igual a (-eq) NorthAmerica ou (-or) um valor NetworkRegionID2 igual a NorthAmerica. Quando a coleção contiver apenas as rotas que incluem a região NorthAmerica, a coleção será canalizada para o cmdlet **Remove-CsNetworkInterRegionRoute**, que removerá cada uma destas rotas.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"} | Remove-CsNetworkInterRegionRoute

## Descrição detalhada

Cada região contida em uma configuração CAC deve ter uma forma de acessar outra região. Enquanto os vínculos de região definem limitações de largura de banda nas conexões entre regiões e representam os vínculos físicos, uma rota determina o caminho vinculado que a conexão percorrerá de uma região à outra. Este cmdlet remove uma dessas associações de rota.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsNetworkInterRegionRoute** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterRegionRoute"}

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
<td><p>O identificador exclusivo da rota da região da rede que se deseja remover. Como as rotas de região de rede são criadas apenas no escopo global, esse identificador não precisa especificar um escopo. Em vez disto, ele contém uma cadeia de caracteres, que é um nome exclusivo que identifica a rota.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType. Aceita entrada canalizada de objetos de rota entre regiões de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

