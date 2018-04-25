---
title: Test-CsVoicePolicy
TOCTitle: Test-CsVoicePolicy
ms:assetid: 4d631e36-3a9d-4ca2-913f-8c9f4e93183d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398310(v=OCS.15)
ms:contentKeyID: 49306655
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoicePolicy

 

_**Tópico modificado em:** 2015-03-09_

Testa um número telefônico contra a política de voz e determina qual rota de voz seria usada contra a política de voz para esse número. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsVoicePolicy -TargetNumber <PhoneNumber> -VoicePolicy <VoicePolicy> [-Force <SwitchParameter>] [-RouteSettings <PstnRoutingSettings>]

## Exemplos

## EXEMPLO 1

Este exemplo executa um teste da política de voz contra a política de voz com Identity site:Redmond. Primeiro o cmdlet **Get-CsVoicePolicy** é executado para recuperar a diretiva com a Identidade site:Redmond. Este objeto de diretiva é então direcionado para o cmdlet **Test-CsVoicePolicy**, onde a diretiva é testada contra o número de telefone +14255559999. A saída vai ser a primeira rota de voz (baseada na propriedade Priority da rota) que tem um padrão de número combinando com o valor TargetNumber e um uso de telefone combinando com um uso de telefone na diretiva. Se nenhuma rota correspondente for encontrada (por exemplo, se o padrão de número corresponde ao padrão para um número de 11 dígitos e você fornece um número de 7 dígitos) um valor nulo vai ser retornado.

    Get-CsVoicePolicy -Identity site:Redmond | Test-CsVoicePolicy -TargetNumber "+14255559999"

## EXEMPLO 2

Exemplo 2 é idêntico ao Exemplo 1, exceto que ao invés de direcionar os resultados da operação Get diretamente para o cmdlet **Test-CsVoicePolicy**, o objeto é primeiro armazenado na variável $a e passado como o valor para o parâmetro VoicePolicy para ser usado como a política contra a qual o teste vai ser executado.

    $a = Get-CsVoicePolicy -Identity site:Redmond
    Test-CsVoicePolicy -TargetNumber "+14255559999" -VoicePolicy $a

## EXEMPLO 3

Este exemplo executa um teste da política de voz contra todas as políticas de voz definidas na implantação Lync Server. Primeiro o cmdlet **Get-CsVoicePolicy** é executado (sem nenhum parâmetro) para recuperar todas as diretivas de voz. A coleção de diretivas que é retornada é então direcionada ao cmdlet **Test-CsVoicePolicy**, onde cada diretiva na coleção é verificada para uma rota correspondente, baseado no número de telefone de destino fornecido (+12065559999) e nos usos de telefones. A saída será uma lista de rotas correspondentes junto com os usos de telefone que foram correspondidos.

    Get-CsVoicePolicy | Test-CsVoicePolicy -TargetNumber "+12065559999"

## Descrição detalhada

As políticas de voz são vinculadas a rotas de voz através de usos de PSTN (rede telefônica pública comutada). Uma chamada de um usuário a quem foi designada uma política de voz específica pode apenas ser enviada através de uma rota que tem uso PSTN combinando com um uso na política, além de um padrão de número que combina com o número discado. Chame o cmdlet **Test-CsVoicePolicy** para determinar qual (se alguma) rota vai ser usada para encaminhar uma chamada de um usuário com uma política de voz específica, assim como qual uso de telefone vincula a política à rota.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Test-CsVoicePolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoicePolicy"}

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
<td><p><em>TargetNumber</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PhoneNumber</p></td>
<td><p>O número de telefone contra o qual executar o teste. Este número deveria estar no formato E.164 (assim como +14255551212).</p></td>
</tr>
<tr class="even">
<td><p><em>VoicePolicy</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>VoicePolicy</p></td>
<td><p>Uma referência ao objeto de diretiva de voz contra a qual o teste será executado. Os objetos da diretiva de voz podem ser recuperados chamando-se o cmdlet <strong>Get-CsVoicePolicy</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime os prompts de confirmação ou mensagens de erro não fatal que podem ocorrer quando você executa o cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>RouteSettings</em></p></td>
<td><p>Opcional</p></td>
<td><p>PstnRoutingSettings</p></td>
<td><p>Configurações de rota contra as quais executar o teste. As configurações de rota podem ser recuperadas com uma chamada ao cmdlet <strong>Get-CsRoutingConfiguration</strong>.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy. Aceita entrada em pipeline dos objetos de diretiva de voz.

## Tipos de retorno

Retorna um objeto do tipo Microsoft.Rtc.Management.Voice.VoicePolicyTestResult.

## Consulte Também

#### Outros Recursos

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)

