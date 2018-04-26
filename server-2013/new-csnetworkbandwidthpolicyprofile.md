---
title: New-CsNetworkBandwidthPolicyProfile
TOCTitle: New-CsNetworkBandwidthPolicyProfile
ms:assetid: 84940891-37a6-45fc-972d-05b95aa71ba9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398675(v=OCS.15)
ms:contentKeyID: 49307336
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBandwidthPolicyProfile

 

_**Tópico modificado em:** 2015-03-09_

Cria um novo perfil de política de largura de banda de rede. Esse cmdlet também pode ser usado para definir as políticas de largura de banda dentro do perfil. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 cria um novo perfil de política de largura de banda, denominado LowBWLimits. Esse novo perfil terá duas políticas atribuídas, uma política de áudio e uma de vídeo (as duas únicas políticas possíveis no Lync Server). A política de áudio é adicionada ao perfil usando-se o parâmetro AudioBWLimit, para atribuir um limite, nesse caso, de 2000 kbps a conexões de áudio geral e o parâmetro AudioBWSessionLimit, para atribuir 200 kbps como o limite a sessões de áudio individuais. O mesmo é realizado para criar limites de sessão de vídeo, mas usando-se os parâmetros VideoBWLimit e VideoBWSessionLimit.

    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimits -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400 -VideoBWSessionLimit 500

## Descrição detalhada

Como parte do controle de admissão de chamadas (CAC), utiliza-se uma política de largura de banda para definir as limitações de largura de banda para determinadas modalidades (no Lync Server, as limitações de largura de banda podem ser atribuídas apenas às modalidades de áudio e vídeo). Esse cmdlet cria um perfil de contêiner para essas políticas. Ao chamar esse cmdlet, defina as políticas individuais dentro do contêiner, especificando as limitações de largura de banda de áudio e vídeo.

Os perfis de política de largura de banda são aplicados a sites de rede chamando-se o cmdlet **New-CsNetworkSite** ou o cmdlet **Set-CsNetworkSite**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsNetworkBandwidthPolicyProfile** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBandwidthPolicyProfile"}

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
<td><p>Um valor de cadeia de caracteres que identifica de forma exclusiva a política. Todos os perfis de política de largura de banda são criados no escopo global. Portanto, o escopo é implícito e apenas um nome exclusivo precisa ser especificado ao se criar um novo perfil de política de largura de banda. Observe que esse valor também preenche a propriedade BWPolicyProfileID do perfil.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBWLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>A largura máxima de banda a se alocar para todas as conexões de áudio. Se uma única sessão de áudio exceder o limite de largura de banda de áudio, essa sessão não será iniciada.</p>
<p>Expresso em kbps. Por exemplo, o valor 1000 significa 1000 kbps.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro AudioBWSessionLimit, mas não para AudioBWLimit, este será definido como 0.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioBWSessionLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>A largura máxima de banda a se alocar por sessão de áudio. Expresso em kbps. O valor deve ser 40 ou superior.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro AudioBWLimit, mas não para AudioBWSessionLimit, este será definido como 175.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Uma lista de objetos contendo perfis de política de largura de banda. Cada objeto na lista consiste em uma modalidade de largura de banda (áudio ou vídeo), uma limitação de largura de banda e uma limitação de sessão de largura de banda.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para os parâmetros AudioBWLimit, AudioBWSessionLimit, VideoBWLimit, ou VideoBWSessionLimit.</p>
<p>É possível criar objetos na lista chamando-se o cmdlet <strong>New-CsNetworkBWPolicy</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma descrição do perfil de política de largura de banda. Por exemplo, é possível usar esse parâmetro para esclarecer o uso esperado do perfil.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoBWLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>A largura máxima de banda a se alocar para todas as conexões de vídeo. Se uma única sessão de vídeo exceder o limite de largura de banda de vídeo, essa sessão não será iniciada.</p>
<p>Expresso em kbps. Por exemplo, o valor 1000 significa 1000 kbps.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro VideoBWSessionLimit, mas não para VideoBWLimit, este será definido como 0.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBWSessionLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>A largura máxima de banda a se alocar por sessão de vídeo. Expresso em kbps. O valor deve ser 100 ou superior.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro VideoBWLimit, mas não para VideoBWSessionLimit, este será definido como 700.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

## Consulte Também

#### Outros Recursos

[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)

