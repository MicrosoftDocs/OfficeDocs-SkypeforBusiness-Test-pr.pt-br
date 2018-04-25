---
title: Get-CsNetworkInterRegionRoute
TOCTitle: Get-CsNetworkInterRegionRoute
ms:assetid: 31c38d92-1cef-40fe-bd04-26e5b373703e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425817(v=OCS.15)
ms:contentKeyID: 49306302
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterRegionRoute

 

_**Tópico modificado em:** 2015-03-09_

Recupera uma ou mais rotas que conectam regiões de rede em uma configuração do CAC (controle de admissão de chamadas). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterRegionRoute [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 recupera a rota com identidade NA\_APAC\_Route.

    Get-CsNetworkInterRegionRoute -Identity NA_APAC_Route

## EXEMPLO 2

No Exemplo 2, usamos o parâmetro Filter para recuperar todas as rotas que contenham a cadeia de caracteres APAC em qualquer lugar da Identity.

    Get-CsNetworkInterRegionRoute -Filter *APAC*

## EXEMPLO 3

Este exemplo recupera todas as rotas de região que usam o link de região de rede NA\_EMEA. O comando começa chamando o cmdlet **Get-CsNetworkInterRegionRoute**. Quando chamado sem parâmetros, este cmdlet recupera todas as rotas definidas com a configuração do CAC. Essa coleção de rotas é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** recupera todos os itens da coleção que tenham o valor NA\_EMEA em sua lista NetworkRegionLinks.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionLinks -eq "NA_EMEA"}

## EXEMPLO 4

O Exemplo 4 recupera todas as rotas de região que incluam a região NorthAmerica. A primeira parte do comando é uma chamada ao cmdlet **Get-CsNetworkInterRegionRoute**. Quando chamado sem parâmetros, este cmdlet recupera todas as rotas de região. A seguir, essa coleção de rotas é canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringe a coleção apenas às rotas que tenham NorthAmerica definido como uma das regiões da rota. Para isso, ele verifica se a rota tem um valor de NetworkRegionID1 igual a (-eq) NorthAmerica, ou (-or) um valor de NetworkRegionID2 igual a NorthAmerica.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"}

## Descrição detalhada

Todas as regiões em uma configuração do CAC precisam ter alguma maneira de acessar todas as outras regiões. Enquanto os links de regiões definem limitações de largura de banda nas conexões entre regiões e também representam os links físicos, uma rota determina qual caminho vinculado a conexão irá transpor de uma região para a outra. O cmdlet recupera informações sobre estas associações de rota.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsNetworkInterRegionRoute** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterRegionRoute"}

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
<td><p>Uma cadeia de caracteres que permite recuperar rotas correspondendo os valores de identidade à cadeia de caracteres de curinga passada como valor para o parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador único para a rota de região de rede que você deseja recuperar. As rotas de regiões de rede são criadas apenas em escopo global, então o identificador não precisa especificar um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome exclusivo para identificação de uma rota específica.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de rota inter-região da rede a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet retorna um ou mais objetos do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)

