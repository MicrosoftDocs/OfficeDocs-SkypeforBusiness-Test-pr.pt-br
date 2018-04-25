---
title: Set-CsRoutingConfiguration
TOCTitle: Set-CsRoutingConfiguration
ms:assetid: ab69c6e8-262a-4ecb-b1af-513383c494fe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412811(v=OCS.15)
ms:contentKeyID: 49307758
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRoutingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma lista de rotas de voz. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsRoutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

São necessárias diversas etapas para modificar uma rota de voz dentro de uma configuração de roteamento. Neste exemplo, iniciamos recuperando o objeto de configuração de roteamento chamando o cmdlet **Get-CsRoutingConfiguration**. Atribuímos o objeto recuperado (haverá somente um) à variável $a.

Na linha 2 deste exemplo, recuperamos o conteúdo da propriedade Rota da variável $a, que é uma coleção de objetos de rota de voz. Então, direcionamos esta coleção para o cmdlet **Where-Object**, em que pesquisamos na coleção todos os objetos de rota de voz com um Nome correspondente à cadeia de caracteres LocalRoute. Atribuímos este objeto à variável $b.

Em seguida, modificamos o objeto de rota de voz LocalRoute, atribuindo o valor $False à propriedade SuppressCallerId. Ao atualizar este objeto, atualizamos o objeto na variável $a. Entretanto, este objeto continua apenas na memória. Na etapa final, precisamos salvar estas alterações, passando $a para o parâmetro Instance do cmdlet **Set-CsRoutingConfiguration**.

Esta não é a maneira recomendada de modificar uma configuração de roteamento. Para modificar uma configuração de roteamento, altere cada rota de voz individual com o cmdlet **Set-CsVoiceRoute**, como exibido aqui:

Set-CsVoiceRoute -Identity LocalRoute -SuppressCallerId $False

Esta linha realizará a mesma tarefa exibida no Exemplo 1.

    $a = Get-CsRoutingConfiguration
    $b = $a.Route | Where-Object {$_.Name -match "LocalRoute"}
    $b.SuppressCallerId = $False
    Set-CsRoutingConfiguration -Instance $a

## Descrição detalhada

As rotas de voz contêm instruções que informam ao Lync Server como rotear chamadas de usuários do Enterprise Voice para números de telefone na PSTN (rede telefônica pública comutada) ou em uma PBX (Central Privada de Comutação). Com este cmdlet, é possível modificar as definições de qualquer rota de voz definida dentro de uma implantação do Lync Server.

O uso deste cmdlet não é recomendado. Para modificar as configurações de roteamento, modifique as rotas de voz individuais chamando o cmdlet **Set-CsVoiceRoute**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsRoutingConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRoutingConfiguration"}

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
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Quando definido como True, o roteamento de voz será gerenciado levando em consideração a localização do usuário que está fazendo a chamada e do usuário que a está recebendo. O valor padrão é False.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>O escopo da configuração de roteamento. Deve ser Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>PstnRoutingSettings</p></td>
<td><p>Um objeto de configuração de roteamento (Microsoft.Rtc.Management.WritablConfig.Policy.Voice.PstnRoutingSettings). Um objeto desse tipo pode ser recuperado chamando o cmdlet <strong>Get-CsRoutingConfiguration</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Route</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de todas as rotas de voz (objetos Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route) definidas na implantação do Lync Server.</p>
<p>Para modificar objetos de rotas de voz individuais, o cmdlet <strong>Set-CsVoiceRoute</strong> deve ser usado. Esta é a maneira recomendada para modificar rotas nesta lista.</p></td>
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

Objeto Microsoft.Rtc.WritableConfig.Management.Policy.Voice.PSTNRoutingSettings. Aceita entrada direcionada de um objeto de configuração de roteamento.

## Tipos de retorno

O cmdlet **Set-CsRoutingConfiguration** não retorna um valor ou objeto. Em vez disso, configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings.

## Consulte Também

#### Outros Recursos

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

