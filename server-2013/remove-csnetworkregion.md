---
title: Remove-CsNetworkRegion
TOCTitle: Remove-CsNetworkRegion
ms:assetid: 661dce40-f601-4181-b8f1-3277a76d5df4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398466(v=OCS.15)
ms:contentKeyID: 49306944
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkRegion

 

_**Tópico modificado em:** 2015-03-09_

Remove uma região de rede existente. As regiões de rede representam hubs de rede ou backbones em uma rede corporativa. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkRegion -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 remove a região de rede cuja identidade for NorthAmerica. Como as identidades são exclusivas, esse comando remove apenas uma região de rede.

    Remove-CsNetworkRegion -Identity NorthAmerica

## EXEMPLO 2

Este exemplo remove todas as regiões de rede associadas ao site central Redmond. O comando inicialmente chama o cmdlet **Get-CsNetworkRegion** sem parâmetros para recuperar uma coleção de todas as regiões de rede definidas para a implantação do Lync Server. Esta coleção é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** filtra essa coleção retornando apenas os itens (regiões de rede) cujo valor CentralSite for igual a (-eq) site:Redmond. Depois que a coleção tiver sido restrita a estes itens, essa nova coleção será canalizada para o cmdlet **Remove-CsNetworkRegion**, que removerá cada item na coleção.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"} | Remove-CsNetworkRegion

## EXEMPLO 3

Esse exemplo remove a região de rede cuja identidade for NorthAmerica. Entretanto, uma região não pode ser removida se estiver associada a um site. Portanto, este exemplo remove primeiramente qualquer associação entre a região NorthAmerica e um site.

O exemplo inicialmente chama o cmdlet **Get-CsNetworkSite** sem parâmetros recuperando uma coleção de todos os sites de rede definidos para a implantação do Lync Server. Esta coleção é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** filtra essa coleção retornando apenas os itens (sites de rede) cujo valor NetworkRegionID for igual a (-eq) NorthAmerica. Depois que a coleção tiver sido restrita a estes itens, esta nova coleção será canalizada para o cmdlet **Set-CsNetworkSite**. Para cada site contendo o NetworkRegionID NorthAmerica, define-se o NetworkRegionID como sendo Null. Isto remove a referência à região neste site. Entretanto, um site não pode ter um ID de desvio se não estiver associado a um site. Portanto, além de remover a referência à região definindo o NetworkRegionID como Null, deve-se remover também a associação de desvio, definindo BypassID como Null.

Depois que a linha 1 tiver sido concluída, qualquer site que tiver sido associado à região NorthAmerica deixará de ser vinculado à região ou a quaisquer definições de desvio. Neste ponto, é possível chamar a linha 2, que removerá a região de rede.

    Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"} | Set-CsNetworkSite -NetworkRegionID $null -BypassID $null
    Remove-CsNetworkRegion -Identity "NorthAmerica"

## Descrição detalhada

Uma região de rede interconecta diversas partes de uma rede em diversas áreas geográficas. Toda região de rede deve ser associada a um site central. O site central é o site do data center no qual o serviço de política de largura de banda estiver em execução. Utilize este cmdlet para remover uma região de rede.

Observe que uma região de rede não pode ser removida se estiver associada a um site de rede (em outras palavras, NetworkRegionID de qualquer site é igual à identidade da região). Se você tentar remover uma região associada a um site, receberá uma mensagem de erro.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsNetworkRegion** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkRegion"}

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
<td><p>O identificador exclusivo da região de rede que se deseja remover. A identidade terá o formato de uma cadeia de caracteres que identifica a região de forma exclusiva.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType. Aceita entrada em pipeline dos objetos de região de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)

