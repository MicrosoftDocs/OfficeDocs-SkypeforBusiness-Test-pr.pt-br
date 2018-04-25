---
title: Remove-CsNetworkInterSitePolicy
TOCTitle: Remove-CsNetworkInterSitePolicy
ms:assetid: daf1afc8-cce4-4192-8ba4-05d26817198e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398963(v=OCS.15)
ms:contentKeyID: 49308302
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkInterSitePolicy

 

_**Tópico modificado em:** 2015-03-09_

Remove uma política entre sites de rede que define as limitações de largura de banda entre sites que estiverem diretamente ligados em uma configuração do controle de admissão de chamadas (CAC). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse exemplo remove a política do site de rede cuja Identidade for Reno\_Portland.

    Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

## EXEMPLO 2

No Exemplo 2, removemos todas as políticas de site de rede definidas na configuração de CAC. Começamos chamando o cmdlet **Get-CsNetworkInterSitePolicy** para recuperar uma coleção de todas as políticas de site da rede. Esta coleção é então canalizada ao cmdlet **Remove-CsNetworkInterSitePolicy**, que remove cada item da coleção.

    Get-CsNetworkInterSitePolicy | Remove-CsNetworkInterSitePolicy

## Descrição detalhada

Quando os sites de uma rede compartilham um link direto, é possível definir limitações de largura de banda às conexões de áudio e vídeo entre esses dois sites. Este cmdlet remove uma política de site de rede, que associa uma política de limitação de largura de banda a dois sites conectados diretamente.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsNetworkInterSitePolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterSitePolicy"}

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
<td><p>O identificador exclusivo da política do site de rede que se deseja remover. As políticas de site de rede são criadas apenas no escopo global, de forma que não é necessário que esse identificador especifique um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome exclusivo que identifica a política do site.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType. Aceita entrada canalizada dos objetos da política entre sites de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

