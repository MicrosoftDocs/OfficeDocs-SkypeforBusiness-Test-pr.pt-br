---
title: New-CsVoiceRegex
TOCTitle: New-CsVoiceRegex
ms:assetid: a1a498b7-8353-40bd-9c02-424c95743ec3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412751(v=OCS.15)
ms:contentKeyID: 49307655
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceRegex

 

_**Tópico modificado em:** 2015-03-09_

Cria um padrão de expressão regular e uma tradução para traduzir números de telefone para diferentes formatos. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsVoiceRegex -AtLeastLength <Int32> [-DigitsToPrepend <String>] [-DigitsToStrip <Int32>] [-StartsWith <String>] <COMMON PARAMETERS>

    New-CsVoiceRegex -ExactLength <Int32> [-DigitsToPrepend <String>] [-DigitsToStrip <Int32>] [-StartsWith <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## Exemplos

## EXEMPLO 1

Este exemplo cria um novo padrão e uma tradução de expressão regular. Esta expressão inclui um padrão que deve ter exatamente sete caracteres (-ExactLength 7) e removerá os três primeiros dígitos do número correspondente (-DigitsToStrip 3). O Padrão criado por esta expressão regular será ^\\d{3}(\\d{4})$, enquanto a Tradução será $1. Por exemplo, o número 5551212 corresponderia a este padrão e a tradução resultante seria 1212: o número de sete dígitos, com os três primeiros dígitos retirados.

    $regex = New-CsVoiceRegex -ExactLength 7 -DigitsToStrip 3

## EXEMPLO 2

Este exemplo também cria um novo padrão e uma tradução de expressão regular, mas segue usando estes três valores para criar uma nova regra de normalização de voz. Na primeira linha, o cmdlet **New-CsVoiceRegEx** é chamado, para criar uma expressão regular em que o número correspondente deve ter pelo menos sete caracteres (-AtLeastLength 7) e começar por 1 (-StartsWith "1"). Os resultados deste comandos são atribuídos à variável $regex.

Na segunda linha, o cmdlet **New-CsVoiceNormalizationRule** é chamado. Damos à nova regra um nome exclusivo. Neste caso, regra global/interna. A seguir, atribuímos como Padrão à regra de normalização o Padrão que criamos na chamada do cmdlet **New-CsVoiceRegex**: -Pattern $regex.Pattern. Fazemos o mesmo com a Tradução, atribuindo a Tradução criada na chamada do cmdlet **New-CsVoiceRegex**: -Translation $regex.Translation.

Observação: O Padrão criado neste exemplo é ^(1\\d{5}\\d+)$. Isso pode ser decifrado como um número que começa por 1 (1) seguido de cinco dígitos (\\d{5}) e de qualquer número de dígitos (\\d+). Adiciona até um número de pelo menos sete dígitos (1, mais 5, mais 1 ou mais) que começa por 1, exatamente o que solicitamos.

    $regex = New-CsVoiceRegex -AtLeastLength 7 -StartsWith "1"
    New-CsVoiceNormalizationRule "global/internal rule" -Pattern $regex.Pattern -Translation $regex.Translation

## Descrição detalhada

As expressões regulares são usadas para coincidir com padrões de caracteres. O Lync Server usa expressões regulares para converter números de telefone de e para diversos formatos, inclusive números discados, E. 164 e formatos PBX (Central Privada de Comutação) local e PSTN (Rede telefônica pública comutada). Até que se aprenda a sintaxe e as regras de formato das expressões regulares, a definição dessas regras de conversão poderá ser confusa. O cmdlet **New-CsVoiceRegex** fornece parâmetros que permitem especificar determinados critérios e, em seguida, gera a expressão regular.

Use este cmdlet para ajudá-lo a gerar expressões regulares a serem usadas como valores Pattern e Translation nas regras de normalização (cmdlet **New-CsVoiceNormalizationRule**), regras de conversão de saída (cmdlet **New-CsOutboundTranslationRule**) e valores NumberPattern de rotas de voz (cmdlet **New-CsVoiceRoute**).

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsVoiceRegex** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceRegex"}

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
<td><p><em>AtLeastLength</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Int32</p></td>
<td><p>O comprimento mínimo necessário para que a cadeia de caracteres (número de telefone) corresponda à expressão. Por exemplo, se você estiver definindo uma regra de normalização que afeta apenas os números que devam ter pelo menos sete dígitos (ou caracteres) de comprimento, especifique o valor 7 para esse parâmetro.</p>
<p>Você deverá inserir um valor para esse parâmetro ou para o parâmetro ExactLength. Não é possível inserir valores para ambos.</p></td>
</tr>
<tr class="even">
<td><p><em>ExactLength</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Int32</p></td>
<td><p>O comprimento da cadeia de caracteres (número do telefone) deve corresponder à expressão regular. Por exemplo, se desejar que uma regra de normalização afete apenas números de dez dígitos, especifique o valor 10 para este parâmetro.</p>
<p>Você deve inserir um valor para esse parâmetro ou para o parâmetro AtLeastLength. Não é possível inserir valores para ambos.</p></td>
</tr>
<tr class="odd">
<td><p><em>DigitsToPrepend</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma cadeia de caracteres que especifica os caracteres ou números a serem adicionados ao início do número do telefone. O valor inserido para este parâmetro afetará o valor Translation, com caracteres precedentes ao número que corresponde à expressão regular Pattern. Por exemplo, se o número que corresponde ao padrão for 5551212 e o valor DigitsToPrepend for 425, o número traduzido será 4255551212 (presumindo que nenhuma outra tradução tenha sido aplicada).</p></td>
</tr>
<tr class="even">
<td><p><em>DigitsToStrip</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>O número de caracteres para retirar do início da cadeia de caracteres (número do telefone). Por exemplo, se o número 2065551212 for inserido e DigitsToStrip for 3, o número será traduzido como 5551212</p></td>
</tr>
<tr class="odd">
<td><p><em>StartsWith</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>O primeiro caractere da cadeia de caracteres (número de telefone). A cadeia de caracteres não corresponderá à expressão regular, a menos que comece com a cadeia de caracteres especificada no parâmetro StartsWith. Por exemplo, se for especificado o valor &quot;+1&quot; para StartsWith, apenas os números que comecem por +1 corresponderão a este padrão e serão traduzidos. Observe que o número de caracteres na cadeia de caracteres StartsWith será incluído nos totais de ExactLength e AtLeastLength. Por exemplo: se você tiver especificado 10 como ExactLength e +1 como cadeia de caracteres StartsWith, um número de telefone correspondente terá oito caracteres de comprimento, precedido por +1, perfazendo um total de dez dígitos.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.Voice.OcsVoiceRegex.

## Consulte Também

#### Outros Recursos

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[New-CsVoiceRoute](new-csvoiceroute.md)

