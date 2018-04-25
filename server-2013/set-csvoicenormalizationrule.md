---
title: Set-CsVoiceNormalizationRule
TOCTitle: Set-CsVoiceNormalizationRule
ms:assetid: 68850abb-4ac7-4ae1-bb6e-d991385f92a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398491(v=OCS.15)
ms:contentKeyID: 49306982
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceNormalizationRule

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma regra de normalização de voz. As regras de normalização de voz são usadas para converter um requisito de discagem de telefone (por exemplo, a discagem de 9 para acessar uma linha externa) no formato de número de telefone E.164 usado pelo Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceNormalizationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-IsInternalExtension <$true | $false>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo define a descrição da regra Prefix Redmond no site de Redmond para "Adicionar um prefixo a todos os números no site de Redmond".

    Set-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond" -Description "Add a prefix to all numbers on site Redmond"

## EXEMPLO 2

Este exemplo modifica a regra de normalização de voz com a Identidade global/SeattleFourDigit. A nova Descrição foi especificada para refletir as modificações à regra. Além disso, um valor de Tradução foi especificado que modifica a regra para traduzir qualquer número que combina com o modelo existente desta regra para o mesmo número, mas com o prefixo +1206556. Por exemplo, se o modelo existente combinasse com qualquer número de quatro dígitos e o número 1234 fosse inserido, esta regra traduziria aquele ramal ao número +12065561234.

    Set-CsVoiceNormalizationRule -Identity global/SeattleFourDigit -Description "Translate an internal four-digit extension" -Translation '+1206556$1'

## EXEMPLO 3

O Exemplo 3 altera o nome da regra de normalização. Tenha em mente que a alteração do nome também alterará a parte do nome da identidade. O cmdlet **Set-CsVoiceNormalizationRule** não possui um parâmetro Name. Portanto, para modificar o nome, chamaremos primeiramente o cmdlet **Get-CsVoiceNormalizationRule**, para recuperar a regra cuja Identidade for global/RedmondFourDigit e atribuir o objeto retornado à variável $a. Em seguida, designaremos a cadeia de caracteres RedmondRule à propriedade Name do objeto. A seguir, passaremos a variável para o parâmetro Instance do cmdlet **Set-CsVoiceNormalizationRule**, para tornar a modificação permanente.

    $a = Get-CsVoiceNormalizationRule -Identity global/RedmondFourDigit
    $a.name = "RedmondRule"
    Set-CsVoiceNormalizationRule -Instance $a

## Descrição detalhada

Este cmdlet modifica uma regra chamada normalização de voz. Essas regras fazem parte integrante da autorização de telefones e do roteamento de chamadas. Elas definem os requisitos para converter (ou traduzir) números de um formato interno Lync Server para um formato padrão (E.164). A compreensão de expressões regulares é útil na definição de padrões de números que serão convertidos.

As regras que são modificadas usando este cmdlet fazem parte do plano de discagem e, além de serem acessíveis através do cmdlet **Get-CsVoiceNormalizationRule**, também podem ser acessadas pela propriedade NormalizationRules devolvida por uma chamada para o cmdlet **Get-CsDialPlan**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsVoiceNormalizationRule** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceNormalizationRule"}

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
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma descrição intuitiva da regra de normalização.</p>
<p>Comprimento máximo da cadeia de caracteres: 512 caracteres.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Um identificador exclusivo para a regra. A identidade especificada deve incluir o escopo seguido por uma barra invertida seguida pelo nome; por exemplo: site:Redmond/Rule1, onde site:Redmond é o escopo e Rule1 é o nome.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>NormalizationRule</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais. Este objeto deve ser do tipo NormalizationRule e pode ser recuperado chamando-se o cmdlet <strong>Get-CsVoiceNormalizationRule</strong></p></td>
</tr>
<tr class="even">
<td><p><em>IsInternalExtension</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se for definido como True, o resultado da aplicação desta regra será um número interno à empresa. Se for definido como False, a aplicação da regra resultará em um número externo. Esse valor será ignorado se o valor da propriedade OptimizeDeviceDialing do plano de discagem associado for definido como False.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Pattern</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma expressão regular à qual o número discado deve corresponder, para que esta regra seja aplicada.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>A ordem na qual serão aplicadas as regras. É possível que um número coincida com mais de uma regra. Este parâmetro define a ordem na qual as regras testarão o número.</p></td>
</tr>
<tr class="odd">
<td><p><em>Translation</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>O modelo de expressão regular que será aplicado ao número para convertê-lo no formato E.164.</p>
<p></p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule. O cmdlet **Set-CsVoiceNormalizationRule** aceita entrada canalizada dos objetos de regra de normalização de voz.

## Tipos de retorno

O cmdlet **Set-CsVoiceNormalizationRule** não retorna um valor ou objeto. Em vez disso, o cmdlet configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule.

## Consulte Também

#### Outros Recursos

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)

