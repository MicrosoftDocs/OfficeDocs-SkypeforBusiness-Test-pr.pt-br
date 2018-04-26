---
title: Set-CsVoiceTestConfiguration
TOCTitle: Set-CsVoiceTestConfiguration
ms:assetid: 7b95fc95-ec0e-4bb3-aed1-e8b72e305999
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398614(v=OCS.15)
ms:contentKeyID: 49307219
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceTestConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica um cenário de teste que você pode usar para testar números de telefone contra rotas e regras especificadas. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceTestConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DialedNumber <String>] [-ExpectedRoute <String>] [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>] [-Force <SwitchParameter>] [-TargetDialplan <String>] [-TargetVoicePolicy <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo define o número discado da configuração de teste de voz para TestConfig1 como 14255551212. Este é o número que será verificado contra a diretiva de voz e rota para garantir que a normalização ocorra conforme esperado, bem como garantir que as rotas corretas e os planos de discagem estejam sendo aplicadas.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 14255551212

## EXEMPLO 2

Este exemplo modifica as definições da configuração de teste de voz TestConfig1. O comando define o TargetDialplan para o perfil de discagem para site:Redmond1. Como uma modificação no plano de discagem pode significar uma modificação em regras de normalização, o ExpectedTranslationNumber também foi modificado para refletir o que é esperado das regras de normalização daquele plano de discagem.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -TargetDialplan site:Redmond1 -ExpectedTranslatedNumber "+912065551212"

## Descrição detalhada

Antes da implementação de rotas e diretivas de voz, é uma boa ideia testá-las em vários números de telefone para garantir que os resultados sejam os esperados. Você pode fazer isto modificando cenários de teste com este cmdlet.

O cmdlet **Set-CsVoiceTestConfiguration** modifica a rota de voz, o uso, o plano de discagem e a diretiva de voz contra o qual um número de telefone especificado será testado. Todas estas informações podem ser definidas e recuperadas com outros cmdlets, conforme especificado nas descrições de parâmetro deste tópico.

As configurações modificadas com este cmdlet são testadas usando o cmdlet **Test-CsVoiceTestConfiguration**.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsVoiceTestConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceTestConfiguration"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O número de telefone que você deseja usar para testar as diretivas, usos etc.</p>
<p>Deve ser 512 caracteres ou menos.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedRoute</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O nome da rota de voz esperada para ser usado durante o teste de configuração. Se uma rota diferente for usada, baseada no plano de discagem de destino e na diretiva de voz, o teste falhará. Você pode recuperar as rotas de voz disponíveis chamando o cmdlet <strong>Get-CsVoiceRoute</strong>.</p>
<p>Deve ser 256 caracteres ou menos.</p></td>
</tr>
<tr class="even">
<td><p><em>ExpectedTranslatedNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O número de telefone no formato que você espera vê-lo depois da conversão. Este é o valor do parâmetro DialedNumber após a normalização. Se você executar o cmdlet <strong>Test-CsVoiceTestConfiguration</strong> e o DialedNumber não resultar no valor em ExpectedTranslatedNumber, o teste notificará como Falha.</p>
<p>Deve ser 512 caracteres ou menos.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedUsage</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O nome do uso de PSTN esperado para ser usado durante o teste de configuração. Se um uso de PSTN diferente for usado, baseado no plano de discagem de destino e na diretiva de voz, o teste falhará. Você pode recuperar usos disponíveis chamando o cmdlet <strong>Get-CsPstnUsage</strong>.</p>
<p>Deve ser 256 caracteres ou menos.</p></td>
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
<td><p>Uma cadeia de caracteres que identifica unicamente a configuração de teste que você deseja recuperar.</p>
<p>O valor deste parâmetro não inclui o escopo, pois este objeto só pode ser criado no escopo global. Por isso, só um nome é necessário.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>TestConfiguration</p></td>
<td><p>Um objeto de tipo Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration que contém uma configuração de teste de voz existente com as modificações que você gostaria de fazer àquela configuração. Um objeto desse tipo pode ser recuperado com o cmdlet <strong>Get-CsVoiceTestConfiguraton</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetDialplan</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>A Identidade do plano de discagem a ser usado para este teste. Os planos de discagem podem ser recuperados chamando o cmdlet <strong>Get-CsDialPlan</strong>.</p>
<p>Deve ser 40 caracteres ou menos.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetVoicePolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>A Identidade da diretiva de voz contra a qual executar este teste. As diretiva de voz podem ser recuperadas chamando o cmdlet <strong>Get-CsVoicePolicy</strong>.</p>
<p>Deve ser 40 caracteres ou menos.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration. Aceita entrada em pipeline de objetos de configuração de teste de voz.

## Tipos de retorno

Este cmdlet retorna um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.

## Consulte Também

#### Outros Recursos

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)

