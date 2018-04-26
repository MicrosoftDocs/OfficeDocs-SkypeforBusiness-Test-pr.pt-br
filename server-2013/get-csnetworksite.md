---
title: Get-CsNetworkSite
TOCTitle: Get-CsNetworkSite
ms:assetid: 9627869d-101f-4668-bee2-01fce1d84cbd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398766(v=OCS.15)
ms:contentKeyID: 49307521
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkSite

 

_**Tópico modificado em:** 2015-03-09_

Recupera um ou mais locais de rede definidos para o controle de admissão de chamadas (CAC) ou Enhanced 9-1-1 (E9-1-1). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkSite [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Chamar o cmdlet **Get-CsNetworkSite** sem nenhum parâmetro retorna todos os locais de rede configurados para CAC ou E911 na implantação do Lync Server.

    Get-CsNetworkSite

## EXEMPLO 2

Este comando recupera o site com a identidade (e, por definição, o NetworkSiteID) Redmond.

    Get-CsNetworkSite -Identity Redmond

## EXEMPLO 3

O comando no Exemplo 3 chama o cmdlet **Get-CsNetworkSite** com o parâmetro Filter. O valor do parâmetro Filter é NA\*, indicando que esse comando recuperará todos os sites cuja identidade começar com a cadeia de caracteres NA e seguido de qualquer número de caracteres. Isto retornará sites como NARedmond, NAVancouver e NAChicago.

    Get-CsNetworkSite -Filter NA*

## EXEMPLO 4

O Exemplo 4 utiliza dois cmdlets, **Get-CsNetworkSite** e **Where-Object**, para recuperar todos os sites que fizerem parte da região NorthAmerica. O comando começa chamando o cmdlet **Get-CsNetworkSite** sem parâmetros, para recuperar todos os sites da rede. Esta coleção de sites será direcionada para o cmdlet **Where-Object**, que filtrará a coleção, procurando todos os sites na coleção cuja propriedade NetworkRegionID for igual a (-eq) NorthAmerica.

    Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"}

## Descrição detalhada

Os sites de rede são os escritórios ou locais configurados em cada região de uma implantação do CAC ou E9-1-1. Este cmdlet recupera as definições de um ou mais sites existentes.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsNetworkSite** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkSite"}

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
<td><p>Uma cadeia de caracteres curinga permite recuperar múltiplos sites com base na correspondência entre a identidade do site e o valor de filtro.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do site de rede que se deseja recuperar. Como os sites são criados apenas no escopo global, não é necessário especificar um escopo. Em vez disso, é preciso especificar apenas o ID do site (observe que este é o mesmo valor que o NetworkSiteID de um site de rede).</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de local de rede na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkSite](new-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)

