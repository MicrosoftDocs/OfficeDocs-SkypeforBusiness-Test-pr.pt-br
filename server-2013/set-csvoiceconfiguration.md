---
title: Set-CsVoiceConfiguration
TOCTitle: Set-CsVoiceConfiguration
ms:assetid: dbab35ac-9a55-41d2-a726-9a26b2ff8e85
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398967(v=OCS.15)
ms:contentKeyID: 49308323
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma lista de configurações de teste de voz. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-VoiceTestConfigurations <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

São necessárias diversas etapas para modificar uma configuração de voz de teste em uma configuração de voz. Neste exemplo, iniciamos recuperando o objeto de configuração de voz, chamando o cmdlet **Get-CsVoiceConfiguration**. Atribuímos o objeto recuperado (haverá somente um) à variável $a.

Na linha 2 desse exemplo, recuperamos o conteúdo da propriedade VoiceTestConfigurations, que é uma coleção de objetos de configuração de teste de voz, da variável $a. Em seguida, canalizamos essa coleção para o cmdlet **Where-Object**, no qual pesquisamos na coleção o objeto de configuração de teste de voz cujo Name for igual à cadeia de caracteres TestConfig2. Atribuímos este objeto à variável $b.

Em seguida, modificamos o objeto configuração de teste de voz TestConfig2 atribuindo novos valores às propriedades DialedNumber e ExpectedTranslatedNumber. Ao atualizar este objeto, atualizamos o objeto na variável $a. No entanto, este objeto ainda está apenas na memória. Na etapa final, precisamos salvar estas alterações, passando $a para o parâmetro Instance do cmdlet **Set-CsVoiceConfiguration**.

Esta não é a maneira recomendada de modificar uma configuração de voz. Para modificar uma configuração de voz, altere as configurações de teste de voz individuais com o cmdlet **Set-CsVoiceTestConfiguration**, conforme mostrado aqui:

Set-CsVoiceTestConfiguration -Identity TestConfig2 -DialedNumber 5551212 -ExpectedTranslatedNumber +5551212

Esta linha realizará a mesma tarefa exibida no Exemplo 1.

    $a = Get-CsVoiceConfiguration
    $b = $a.VoiceTestConfigurations | Where-Object {$_.Name -eq "TestConfig2"}
    $b.DialedNumber = "5551212"
    $b.ExpectedTranslatedNumber = "+5551212"
    Set-CsVoiceConfiguration -Instance $a

## Descrição detalhada

As configurações de teste de voz são usadas para testar um número de telefone em relação a uma política de voz, rota e plano de discagem específico. Este cmdlet pode ser usado para modificar configurações de teste de voz de uma lista contendo todas as configurações de teste de voz para uma implantação do Lync Server.

Esse cmdlet modifica um objeto do tipo VoiceConfiguration. Esse objeto é simplesmente um objeto de contêiner para configurações de testes de voz. Portanto, o uso deste cmdlet não é recomendável. Para modificar as configurações de voz, modifique as configurações de teste de voz individuais chamando o cmdlet **Set-CsVoiceTestConfiguration**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsVoiceConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>O escopo deste objeto. O único valor possível para este parâmetro é Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>VoiceConfiguration</p></td>
<td><p>Uma referência a um objeto de configuração de voz (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration). Um objeto desse tipo pode ser recuperado chamando-se o cmdlet <strong>Get-CsVoiceConfiguration</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceTestConfigurations</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de todas as configurações de teste de voz (objetos Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration) definidas para a implantação do Lync Server.</p>
<p>Você pode modificar objetos de configuração de teste de voz usando o cmdlet <strong>Set-CsVoiceTestConfiguration</strong>. Está é a maneira recomendada para modificar configurações nesta lista.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration. O cmdlet **Set-CsVoiceConfiguration** aceita a entrada por pipeline de um objeto de configuração de voz.

## Tipos de retorno

O cmdlet **Set-CsVoiceConfiguration** não retorna nenhum valor ou objeto. Em vez disso, ele configura as instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration.

## Consulte Também

#### Outros Recursos

[Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)  
[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

