---
title: Set-CsOutboundTranslationRule
TOCTitle: Set-CsOutboundTranslationRule
ms:assetid: fbf82146-7884-418c-8239-66c0ca0f2ba6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413073(v=OCS.15)
ms:contentKeyID: 49308699
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsOutboundTranslationRule

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma regra de conversão de saída existente. Uma regra de conversão de saída converte números de telefone no formato de discagem local para interação com sistemas PBX (central privada de comutação telefônica). Este cmdlet foi introduzido no Lync Server 2010..

## Sintaxe

    Set-CsOutboundTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsOutboundTranslationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo modifica a regra de conversão de saída cuja identidade for site:Redmond/Prefix Redmond. Incluímos uma Descrição, que explica que esta regra deve converter números do formato E.164 em um número de telefone de sete dígitos. Além disso, especificaram-se os valores de Pattern e Translation, o que modificará os valores existentes dessas propriedades. Esses valores convertem um número E.164 (nesse caso, 12 dígitos começando com +1425), especificado pela expressão regular no Padrão, em um número de sete dígitos, removendo os cinco primeiros dígitos. Por exemplo, o número +14255551212 seria convertido no número 5551212.

    Set-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond" -Description "Convert to seven digits" -Pattern '^\+1425(\d{7})$' -Translation '$1'

## EXEMPLO 2

Este exemplo modifica a propriedade Name de uma regra de conversão de saída. Observe que isso resulta na alteração da Identidade dessa regra. O primeiro comando desse exemplo é uma chamada ao cmdlet **Get-CsOutboundTranslationRule**. Especificamos uma Identidade de site:Redmond\\OBR1, que retornará uma regra de conversão apresentando a Identidade dada. Em vez de exibir essa regra, a atribuímos à variável $a. A linha 2 desse exemplo atribui a cadeia de caracteres "Outbound Rule 1" à propriedade Name da variável $a, a variável que contém uma referência à regra site:Redmond/OBR1. Na última linha desse exemplo, chamamos o cmdlet **Set-CsOutboundTranslationRule** especificando o parâmetro Instance e passando-o para a variável $a. Se agora chamarmos o cmdlet **Get-CsOutboundTranslationRule** com um valor de Identidade site:Redmond/OBR1, nada será retornado. Isso ocorre porque a regra com essa Identidade não existe mais. Ela foi substituída pela mesma regra com a Identidade site:Redmond/Outbound Rule 1.

    $a = Get-CsOutboundTranslationRule -Identity "site:Redmond/OBR1"
    $a.Name = "Outbound Rule 1"
    Set-CsOutboundTranslationRule -Instance $a

## Descrição detalhada

O Lync Server normaliza números de telefone para o formato E.164. No entanto, muitos sistemas de PBX não conseguem lidar com esse formato. As regras de conversão de saída convertem o número para o formato de discagem local antes de enviá-lo para o Servidor de Mediação ou Gateway. Chame esse cmdlet para modificar uma regra de conversão de saída existente.

Cada regra de conversão de saída é associada a uma configuração de tronco. Isso significa que a utilização desse cmdlet para modificar uma regra afetará a configuração de tronco correspondente. É possível associar mais de uma regra de conversão de saída a cada configuração. Portanto, a Identidade de cada regra consiste em um escopo, juntamente com um nome exclusivo no escopo (no formato escopo/nome – por exemplo, site:Redmond/OBR1). A regra é automaticamente associada à configuração de tronco com o mesmo escopo. O ato de chamar o cmdlet **Set-CsOutboundTranslationRule** é a maneira recomendada de alterar as regras de conversão de saída em uma configuração de tronco.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsOutboundTranslationRule** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsOutboundTranslationRule"}

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
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma descrição intuitiva da regra de conversão de saída. Essa descrição pode ser usada para ajudar os administradores a identificar claramente o propósito da regra.</p></td>
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
<td><p>O identificador exclusivo da regra de conversão de saída que se deseja modificar. A Identidade consiste no escopo, seguido de um nome exclusivo ao âmbito de cada escopo. Por exemplo, site:Redmond/OutboundRule1.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>TranslationRule</p></td>
<td><p>Uma referência de objeto a uma regra de conversão de saída. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule, que pode ser recuperado chamando o cmdlet <strong>Get-CsOutboundTranslationRule</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Pattern</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma expressão regular que representa o padrão numérico ao qual a Conversão será aplicada.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Se um número corresponder ao Padrão de mais de uma regra de conversão de saída, as regras serão aplicadas por ordem de prioridade. Use esse parâmetro para atribuir uma prioridade à regra.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma expressão regular que será aplicada ao número que corresponde ao Padrão, para preparar esse número para roteamento de saída.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule. Aceita entradas canalizadas dos objetos de regra de conversão de saída.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.

## Consulte Também

#### Outros Recursos

[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)

