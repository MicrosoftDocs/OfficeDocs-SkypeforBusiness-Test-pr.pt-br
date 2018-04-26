---
title: Set-CsPstnUsage
TOCTitle: Set-CsPstnUsage
ms:assetid: ecba9ed6-4845-4035-933e-0c540d530b72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399069(v=OCS.15)
ms:contentKeyID: 49308512
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPstnUsage

 

_**Tópico modificado em:** 2015-03-09_

Modifica um conjunto de cadeias de caracteres que identificam os usos da PSTN permitidos. Esse cmdlet pode ser usado para adicionar utilizações à lista de utilizações da PSTN ou remover utilizações da lista. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPstnUsage [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Usage <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este comando adiciona a cadeia de caracteres "Internacional" à lista atual de usos da PSTN disponíveis.

    Set-CsPstnUsage -Identity global -Usage @{add="International"}

## EXEMPLO 2

Este comando remove a cadeia de caracteres "Local" da lista de usos da PSTN disponíveis.

    Set-CsPstnUsage -Identity global -Usage @{remove="Local"}

## EXEMPLO 3

O comando nesse exemplo desempenha a mesma ação que o comando no Exemplo 2: ele remove o uso da PSTN "Local". Este exemplo mostra o comando sem o parâmetro Identity especificado. A única identidade disponível para o cmdlet **Set-CsPstnUsage** é a identidade Global. A omissão do parâmetro Identity causará a adoção do padrão Global.

    Set-CsPstnUsage -Usage @{remove="Local"}

## EXEMPLO 4

Este comando substitui tudo na lista de usos pelos valores Internacional e Restrito. Todos os usos existentes anteriormente serão removidos.

    Set-CsPstnUsage -Usage @{replace="International","Restricted"}

## Descrição detalhada

Os usos da PSTN são valores de cadeia de caracteres que são usados para a autorização de chamadas. Um uso da PSTN vincula uma política de voz a uma rota. O cmdlet **Set-CsPstnUsage** é usado para adicionar ou remover usos de telefone de e para a lista de uso. Esta lista é global, portanto pode ser usada por políticas e rotas de toda a implantação do Lync Server.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsPstnUsage** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPstnUsage"}

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
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>O escopo no qual se aplicam estas definições. A identidade deste cmdlet é sempre Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>PstnUsages</p></td>
<td><p>Uma referência a um objeto de uso do PSTN. Esse objeto deve ser do tipo PstnUsages e pode ser recuperado chamando o cmdlet <strong>Get-CsPstnUsage</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>Usage</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Contém uma lista de cadeias de caracteres de uso disponíveis. Estas entradas podem ser de qualquer valor de cadeia de caracteres.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages. Aceita entradas canalizadas de objetos de utilizações da PSTN.

## Tipos de retorno

Este cmdlet não retorna um valor ou um objeto. Em vez disso, ele configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages.

## Consulte Também

#### Outros Recursos

[Get-CsPstnUsage](get-cspstnusage.md)

