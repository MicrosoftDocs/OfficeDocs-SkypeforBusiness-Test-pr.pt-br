---
title: Get-CsPstnUsage
TOCTitle: Get-CsPstnUsage
ms:assetid: 9dc82b88-303b-4678-8298-0dbc769f6781
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412734(v=OCS.15)
ms:contentKeyID: 49307623
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPstnUsage

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre registros de uso da PSTN (rede telefônica pública comutada) em sua organização. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPstnUsage [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Este comando retorna a lista de uso de PSTN global disponível dentro da organização.

    Get-CsPstnUsage

## EXEMPLO 2

O comando neste exemplo retorna uma lista de todos os usos de PSTN definidos, com um uso listado em cada linha de saída. Quando o cmdlet **Get-CsPstnUsage** é chamado sozinho, retorna a identidade e a lista de usos. Se a lista de uso tiver mais de três ou quatro entradas, a lista estará abreviada na saída, semelhante a:

Uso: {Interna, Local, Interurbano, Internacional...}

Use o comando neste exemplo para exibir somente uma lista de usos. A saída será semelhante a esta:

Interno

Local

Interurbano

Internacional

Restricted

    (Get-CsPstnUsage).Usage

## EXEMPLO 3

Este comando retorna todos os nomes de uso de PSTN que tenham a cadeia de caracteres "tern" em qualquer lugar do nome. Por exemplo, este comando retornará "Interno" e "Internacional", mas não "Local" ou "Interurbano".

A primeira parte deste comando é o cmdlet **Get-CsPstnUsage** entre parênteses, que significa que a primeira coisa que acontece é a recuperação de todos os usos da PSTN. A propriedade .Usage retorna apenas as informações de uso da PSTN, e não a identidade. Esta lista de usos é então direcionada para o cmdlet **ForEach-Object**, que procura as cadeias de caracteres de uso um de cada vez. A declaração If compara a cadeia de caracteres de uso atual com a cadeia de caracteres "\*tern\*" (o \* são caracteres curingas) e exibe qualquer ocorrência que combine com o padrão.

    (Get-CsPstnUsage).Usage | ForEach-Object {if ($_ -like "*tern*") {$_}}

## Descrição detalhada

Os usos da PSTN são valores de cadeia de caracteres utilizados para autorização de chamada. O uso de PSTN vincula uma diretiva de voz a uma rota. O cmdlet **Get-CsPstnUsage** recupera a lista de todos os usos de PSTN disponíveis dentro de uma organização.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsPstnUsage** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPstnUsage"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>O parâmetro Filter permite recuperar apenas os usos de PSTN com identidade correspondente a uma cadeia de caracteres curinga específica. Entretanto, a única identidade disponível para usos de PSTN é a Global, então este parâmetro não será útil para este cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>O nível ao qual estas configurações são aplicadas. A única identidade que pode ser aplicada aos usos de PSTN é a Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de uso da PSTN a partir do armazenamento de dados local, e não do Repositório de Gerenciamento Central principal.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Get-CsPstnUsage** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PSTNUsages.

## Consulte Também

#### Outros Recursos

[Set-CsPstnUsage](set-cspstnusage.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

