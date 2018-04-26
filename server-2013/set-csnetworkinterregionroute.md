---
title: Set-CsNetworkInterRegionRoute
TOCTitle: Set-CsNetworkInterRegionRoute
ms:assetid: 5d9da3c0-56fc-401d-baf3-ed6c0f50f53d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398410(v=OCS.15)
ms:contentKeyID: 49306850
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkInterRegionRoute

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma rota existente que conecta regiões de rede em uma configuração de controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkInterRegionRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-NetworkRegionLinkIDs <String>] [-NetworkRegionLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse exemplo modifica a rota NA\_APAC\_Route, mudando aos links da região que serão atravessadas ao longo da rota. O parâmetro NetworkRegionLinkIDs é usado com o valor de “NA\_SA,SA\_APAC”, o qual substitui quaisquer links existentes com os dois especificados naquela cadeia de caracteres.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinkIDs "NA_SA,SA_APAC"

## EXEMPLO 2

Como o Exemplo 1, o Exemplo 2 modifica os links dentro da rota NA\_APAC\_Route. Neste exemplo, entretanto, em vez de substituir todos os links para aquela rota usando o parâmetro NetworkRegionLinkIDs, o parâmetro NetworkRegionLinks é usado para adicionar um link à lista de links que já existe naquela rota. Nesse caso, o link SA\_EMEA é adicionado à rota. A sintaxe @{add=\<link\>} adiciona um elemento à lista de links. Você pode também usar a sintaxe @{replace=\<link\>} para substituir todos os links existentes por aqueles especificados por \<link\> (que essencialmente se comporta da mesma forma que usando NetworkRegionLinkIDs), ou a sintaxe @{remove=\<link\>} para remover um link da lista.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinks @{add="SA_EMEA"}

## EXEMPLO 3

O Exemplo 3 modifica a rota chamada NA\_Route5. Este exemplo muda uma das regiões que compõem esta rota. O parâmetro NetworkRegionID2 é usado para especificar a nova região e o parâmetro NetworkRegionLinkIDs é usado para criar uma nova lista de links para conectar as regiões desta rota.

    Set-CsNetworkInterRegionRoute -Identity NA_Route5 -NetworkRegionID2 SouthAmerica -NetworkRegionLinkIDs "NA_SA,SA_APAC"

## Descrição detalhada

Toda região em uma configuração CAC deve ter uma forma de acessar todas as outras regiões. Enquanto os links de regiões definem limitações de largura de banda nas conexões entre regiões e também representam os links físicos, uma rota determina qual caminho vinculado a conexão irá transpor de uma região para a outra. Esse cmdlet modifica aquela associação da rota.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsNetworkInterRegionRoute** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkInterRegionRoute"}

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
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime todos os avisos de confirmação que seriam exibidos antes que as alterações sejam feitas.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador único para a rota da região de rede que você quer modificar. As rotas de regiões de rede são criadas apenas em escopo global, então o identificador não precisa especificar um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome único para identificação da rota.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>InterNetworkRegionRouteType</p></td>
<td><p>Uma referência de objeto a uma rota de região existente. Este objeto tem que ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType, o qual pode ser recuperado chamando-se o cmdlet <strong>Get-CsNetworkInterRegionRoute</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A Identity (NetworkRegionID) de uma das duas regiões conectadas através dessa rota. O valor passado a esse parâmetro precisa ser uma região diferente do valor do parâmetro NetworkRegionID2. (Em outras palavras, você não pode encaminhar uma região a si mesma.) Além disso, a combinação de NetworkRegionID1 e NetworkRegionID2 tem que ser única (por exemplo, você não pode ter duas rotas definidas que conectam NorthAmerica e EMEA).</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A Identity (NetworkRegionID) de uma das duas regiões conectadas através dessa rota. O valor passado a esse parâmetro precisa ser uma região diferente do valor do parâmetro NetworkRegionID1. (Em outras palavras, você não pode encaminhar uma região a si mesma.) Além disso, a combinação de NetworkRegionID1 e NetworkRegionID2 tem que ser única (por exemplo, você não pode ter duas rotas definidas que conectam NorthAmerica e EMEA).</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionLinkIDs</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Permite que você especifique todos os links para essa rota como uma cadeia de caracteres de valores separados por vírgula. Os valores são as identidades (NetworkRegionLinkIDs) dos links da região. Se você digitar valores tanto para NetworkRegionLinkIDs quanto para NetworkRegionLinks, NetworkRegionLinkIDs vai ser ignorado. Quaisquer links modificados usando este parâmetro vão substituir todos os links existentes na rota.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Um objeto lista contendo as identidades (NetworkRegionLinkIDs) dos links da região que se aplicam à esta rota. Para esse cmdlet, esse parâmetro difere de NetworkRegionLinkIDs em que, além de poder substituir todos os links existentes para esta rota, você pode também adicionar ou remover links individuais.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType. Aceita entrada canalizada de objetos de rota inter-região de rede.

## Tipos de retorno

Esse cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

