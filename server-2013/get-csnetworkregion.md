---
title: Get-CsNetworkRegion
TOCTitle: Get-CsNetworkRegion
ms:assetid: 5c9eef10-16c1-45f7-ae7b-2bee0965b421
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398406(v=OCS.15)
ms:contentKeyID: 49306840
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkRegion

 

_**Tópico modificado em:** 2015-03-09_

Recupera uma ou mais regiões de rede. Regiões de rede representam hubs de rede ou backbones em uma rede corporativa. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegion [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 recupera todas as regiões de rede definidas para a organização.

    Get-CsNetworkRegion

## EXEMPLO 2

O Exemplo 2 recupera as regiões de rede com a Identity NorthAmerica. Como as identidades são únicas, esse comando recupera no máximo uma região de rede.

    Get-CsNetworkRegion -Identity NorthAmerica

## EXEMPLO 3

Esse exemplo recupera todas as regiões de rede com identidades que terminam com a cadeia de caracteres "America". Isso recuperaria regiões com identidades tais como NorthAmerica, SouthAmerica e CentralAmerica.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

## EXEMPLO 4

Esse exemplo recupera todas as regiões de rede associadas ao site central Redmond. O comando começa chamando o cmdlet **Get-CsNetworkRegion**, sem nenhum parâmetro, para recuperar uma coleção de todas as regiões de rede definidas para a implantação do Lync Server. Esta coleção é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** filtra essa coleção para retornar somente os itens (regiões de rede) nos quais o valor de CentralSite seja igual a (-eq) site:Redmond.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

## Descrição detalhada

Uma região de rede interconecta várias partes de uma rede em múltiplas áreas geográficas. Cada região de rede deve ser associada a um site central. Use este cmdlet para obter informações sobre uma ou mais regiões de rede, incluindo o site central e as configurações associadas que determinam se caminhos alternativos serão permitidos para conexões de áudio e vídeo, e que associam os sites de uma região a uma configuração de passagem livre de mídia.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsNetworkRegion** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegion"}

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
<td><p>Este parâmetro permite que você execute um pesquisa com curinga na Identity de todas as regiões de rede configuradas para a organização. Use o caracter curinga para filtrar qualquer parte da Identity.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador único da região de rede que você quer recuperar. A Identity vai estar na forma de uma cadeia de caracteres que identifica esta região de modo único. (Note que a Identity é a mesma que a NetworkRegionID.)</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de região de rede a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Retorna um ou mais objetos do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)

