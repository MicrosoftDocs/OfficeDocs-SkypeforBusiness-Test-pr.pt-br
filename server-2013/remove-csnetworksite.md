---
title: Remove-CsNetworkSite
TOCTitle: Remove-CsNetworkSite
ms:assetid: 07b543a6-3aa0-4fce-85f9-9ddc75d7b14f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398135(v=OCS.15)
ms:contentKeyID: 49305792
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkSite

 

_**Tópico modificado em:** 2015-03-09_

Remove um site de rede que tenha sido definido para o CAC (controle de admissão de chamadas) ou para o E9-1-1 (Enhanced 9-1-1). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo remove o site com parâmetro Identity Vancouver da configuração do CAC ou do E9-1-1.

    Remove-CsNetworkSite -Identity Vancouver

## EXEMPLO 2

O Exemplo 2 remove todos os sites que estejam usando um perfil de diretiva de largura de banda chamado LowBWProfile da configuração do CAC ou do E9-1-1. O exemplo primeiro chama o cmdlet **Get-CsNetworkSite** para recuperar todos os sites da rede. Essa coleção de sites é canalizada para o cmdlet **Where-Object**, que restringe a coleção apenas aos sites que tenham BWPolicyProfileID igual a (-eq) LowBWProfile. Essa nova coleção é então encaminhada para o cmdlet **Remove-CsNetworkSite** para a remoção desses sites.

    Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Remove-CsNetworkSite

## Descrição detalhada

Sites de rede são os escritórios ou locais configurados em cada região de uma implementação do CAC ou do E9-1-1. Este cmdlet remove um site da configuração do CAC ou do E9-1-1.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Remove-CsNetworkSite** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkSite"}

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
<td><p>O identificador único do site de rede que será removido. Os sites são criados apenas em escopo global, não é necessário especificar um escopo. Em vez disso, é preciso especificar apenas a ID do site.</p></td>
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
<td><p>Suprime eventuais avisos de confirmação que seriam exibidos antes da realização das alterações.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType. Aceita entrada em pipeline de objetos de site de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkSite](new-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)

