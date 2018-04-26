---
title: Get-CsNetworkRegionLink
TOCTitle: Get-CsNetworkRegionLink
ms:assetid: dc5cb988-13e2-4af4-8b36-0aaa58ebf1c5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398972(v=OCS.15)
ms:contentKeyID: 49308329
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkRegionLink

 

_**Tópico modificado em:** 2015-03-09_

Recupera um ou mais links entre regiões de rede configuradas para o controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegionLink [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 recupera todos os links de região de rede definidos em uma implantação do Lync Server.

    Get-CsNetworkRegionLink

## EXEMPLO 2

O Exemplo 2 recupera informações sobre (no máximo) um link de região de rede, o link cuja Identidade for NA\_EMEA.

    Get-CsNetworkRegionLink -Identity NA_EMEA

## EXEMPLO 3

Nesse exemplo, utilizamos o parâmetro Filter para recuperar todos os links de região de rede que contiverem a cadeia de caracteres EMEA no seu nome (Identidade). Observe os caracteres \*, um antes da cadeia de caracteres EMEA e um depois. Isso significa que qualquer caractere, ou caracteres, pode vir antes ou depois da cadeia de caracteres; a cadeia de caracteres EMEA deve estar incluída em alguma posição da Identidade. Isso irá recuperar links com nomes como NA\_EMEA, EMEA\_APAC e EMEA2\_SA.

    Get-CsNetworkRegionLink -Filter *EMEA*

## EXEMPLO 4

Este exemplo recupera todos os links de região de rede que contêm EMEA como uma das duas regiões a serem vinculadas. Inicialmente, o exemplo chama o cmdlet **Get-CsNetworkRegionLink** sem parâmetros, o que recuperará todos os links de região. Esta coleção de links é então canalizada ao cmdlet **Where-Object**. O cmdlet **Where-Object** pesquisa individualmente cada membro da coleção, verificando os valores das propriedades NetworkRegionID1 e NetworkRegionID2. Se uma dessas propriedades for igual a EMEA, ou seja, se NetworkRegionID1 for igual a (-eq) EMEA ou (-or) NetworkRegionID2 for igual a (-eq) EMEA, este item será mantido na coleção e exibido.

    Get-CsNetworkRegionLink | Where-Object {$_.NetworkRegionID1 -eq "EMEA" -or $_.NetworkRegionID2 -eq "EMEA"}

## Descrição detalhada

As regiões dentro de uma rede são vinculadas por meio da conectividade Wan. Esse cmdlet recupera um ou vários links de região que estiverem definidos dentro das definições de configuração da rede para a implantação do Lync Server.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsNetworkRegionLink** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegionLink"}

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
<td><p>Aceita uma cadeia de caracteres curinga, que é usada para recuperar links de rede com base na correspondência com o valor da Identidade.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do link da região de rede que se deseja recuperar. Como os links de região de rede são criados apenas no escopo global, esse identificador não precisa especificar um escopo. Em vez disto, ele contém uma cadeia de caracteres, que é um nome exclusivo que identifica este link (observe que esse valor é o mesmo que NetworkRegionLinkID.)</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de link de região de rede na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Recupera um ou mais objetos do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)

