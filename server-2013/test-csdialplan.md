---
title: Test-CsDialPlan
TOCTitle: Test-CsDialPlan
ms:assetid: e6618394-82c5-4bc2-85cc-97ac4686a1aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399024(v=OCS.15)
ms:contentKeyID: 49308432
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsDialPlan

 

_**Tópico modificado em:** 2015-03-09_

Testa um número de telefone em relação a um plano de discagem (anteriormente conhecido como perfil de localidade) e retorna a regra de normalização que será aplicada ao número, bem como o número convertido depois que a regra de normalização tiver sido aplicada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsDialPlan -DialedNumber <PhoneNumber> -Dialplan <LocationProfile>

## Exemplos

## EXEMPLO 1

Este exemplo executa um teste em relação ao plano de discagem com a Identidade site:Redmond. Primeiramente, executa-se o cmdlet **Get-CsDialPlan**, para recuperar o plano de discagem com a Identidade site:Redmond. Esse objeto de plano de discagem será então canalizado para o cmdlet **Test-CsDialPlan**, no qual se testa o plano de discagem em relação ao número de telefone 14255559999. A saída será DialedNumber, depois que uma regra de normalização de voz com uma correspondência de padrões tiver sido aplicada. Se houver mais de uma regra de normalização no site com um padrão de correspondência, será aplicada a regra com o valor de Prioridade mais baixo. Se não houver nenhuma regra com padrões correspondentes ao valor de DialedNumber (por exemplo, se a regra de normalização coincidir com o padrão de um número de onze dígitos e você tiver fornecido um número de sete dígitos), nenhum valor será retornado.

A saída deste comando inclui um número de telefone e uma regra de normalização. A regra de normalização tem diversas propriedades e, por padrão, esta saída será abreviada por reticências (...). Para exibir todas as propriedades e os valores da regra de normalização de voz retornada, canaliza-se a saída para o cmdlet **Format-List**, antes que esta seja exibida na tela. Isto listará o número de telefone e a regra de normalização em linhas separadas e as propriedades de regra de normalização e os valores serão quebrados para se ajustarem à tela.

    Get-CsDialPlan -Identity site:Redmond | Test-CsDialPlan -DialedNumber 14255559999 | Format-List

## EXEMPLO 2

O Exemplo 2 é idêntico ao Exemplo 1, exceto pelo fato de que, em vez de canalizar os resultados da operação Get diretamente para o cmdlet **Test-CsDialPlan**, o objeto será primeiramente armazenado na variável $a e, em seguida, será passado como o valor para o parâmetro DialPlan a ser utilizado como plano de discagem em relação ao qual será executado o teste.

Como no Exemplo 1, concluímos este comando ao canalizar a saída ao cmdlet **Format-List** para que possamos exibir mais informações sobre a regra de normalização de voz que aparece por padrão.

    $a = Get-CsDialPlan -Identity site:Redmond
    Test-CsDialPlan -DialedNumber 14255559999 -Dialplan $a | Format-List

## EXEMPLO 3

Este exemplo executa um teste de plano de discagem em relação a todos os planos de discagem definidos na implantação do Lync Server. Primeiramente, executa-se o cmdlet **Get-CsDialPlan** (sem parâmetros), para recuperar todos os planos de discagem. A coleção de planos de discagem que é retornada será então canalizada para o cmdlet **Test-CsDialPlan**, no qual cada plano de discagem na coleção será testado em relação ao número de telefone 2065559999. A saída será uma lista de números convertidos, juntamente com a regra de normalização de voz aplicada, cada qual correspondendo aos planos de discagem na coleção. Se nenhuma regra de normalização de voz de um plano de discagem se aplicar ao valor de DialedNumber de um determinado plano de discagem (por exemplo, se a regra de normalização coincidir com o padrão de um número de onze dígitos e você tiver fornecido um número de sete dígitos), haverá uma linha em branco na lista desse plano de discagem.

Por padrão, a saída abrevia a exibição completa da regra de normalização de voz que foi aplicada. Nos Exemplos 1 e 2, pudemos exibir a saída inteira canalizando os resultados do teste ao cmdlet **Format-List**. Neste exemplo, canalizamos a saída ao cmdlet **Format-Table** e incluímos o parâmetro Wrap. Isto mostra cada entrada no formato de tabela (uma coluna para o número convertido e outra para a regra de normalização de voz aplicada), mas ela quebra a saída. Portanto, a regra de normalização quebrará dentro da coluna.

    Get-CsDialPlan | Test-CsDialPlan -DialedNumber 2065559999 | Format-Table -Wrap

## Descrição detalhada

Este cmdlet permite definir os resultados da aplicação de um plano de discagem a um determinado número de telefone. Os planos de discagem oferecem informações, incluindo como as regras de normalização são aplicadas, requeridas para habilitar os usuários do Enterprise Voice para fazer chamadas telefônicas. Considerando um número discado e um plano de discagem, este cmdlet verificará qual regra de normalização dentro do plano de discagem será aplicada e qual será o número traduzido.

É possível utilizar este cmdlet para solucionar problemas com conversões de números ou para verificar a aplicação das regras em relação a certos números.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Test-CsDialPlan** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialPlan"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PhoneNumber</p></td>
<td><p>O número de telefone em relação ao qual se quer testar o plano de discagem especificado no parâmetro Dialplan.</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="even">
<td><p><em>Dialplan</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>LocationProfile</p></td>
<td><p>Um objeto que contém uma referência ao plano de discagem em relação ao qual se quer testar o número especificado no parâmetro DialedNumber.</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile. Aceita entrada canalizada de objetos de planos de discagem.

## Tipos de retorno

Retorna um objeto do tipo Microsoft.Rtc.Management.Voice.LocationProfileTestResult.

## Consulte Também

#### Outros Recursos

[New-CsDialPlan](new-csdialplan.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)

