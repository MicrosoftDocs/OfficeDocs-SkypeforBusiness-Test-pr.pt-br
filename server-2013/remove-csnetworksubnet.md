---
title: Remove-CsNetworkSubnet
TOCTitle: Remove-CsNetworkSubnet
ms:assetid: 251ddb5c-4837-4810-b46f-d276f9535653
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425726(v=OCS.15)
ms:contentKeyID: 49306159
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkSubnet

 

_**Tópico modificado em:** 2015-03-09_

Remove uma sub-rede de rede existente. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo remove todas as sub-redes com a identidade (o ID da sub-rede) 172.11.15.0.

    Remove-CsNetworkSubnet -Identity 172.11.15.0

## EXEMPLO 2

O Exemplo 2 remove todas as sub-redes associadas ao site de Vancouver. Para fazer isso, começamos chamando o cmdlet **Get-CsNetworkSubnet**. Isto recuperará uma coleção de todas as sub-redes definidas na implantação do Lync Server. Essa coleção de sub-redes é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** usa esta coleção e a restringe apenas às sub-redes cujo NetworkSiteID for igual a (-eq) Vancouver. Agora que a coleção consiste apenas em sub-redes associadas ao site de Vancouver, ela será canalizada para o cmdlet **Remove-CsNetworkSubnet**, que removerá cada item na coleção.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Remove-CsNetworkSubnet

## Descrição detalhada

Cada sub-rede deve ser associada a um site de rede a fim de determinar o local geográfico do host que pertence a essa sub-rede. Utilize este cmdlet para remover uma sub-rede de rede.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsNetworkSubnet** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkSubnet"}

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
<td><p>O identificador exclusivo da sub-rede que se deseja remover. Este valor será um endereço IP (como 174.11.12.0).</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType. Aceita entrada em pipeline dos objetos de sub-rede de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)

