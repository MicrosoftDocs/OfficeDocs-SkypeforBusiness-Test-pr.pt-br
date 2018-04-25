---
title: Remove-CsCallParkOrbit
TOCTitle: Remove-CsCallParkOrbit
ms:assetid: b8e7c236-f8de-45bd-966b-60c815b37aed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412901(v=OCS.15)
ms:contentKeyID: 49307904
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCallParkOrbit

 

_**Tópico modificado em:** 2015-03-09_

Remove um intervalo específico de órbita de estacionamento de chamadas. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Neste exemplo, o cmdlet **Remove-CsCallParkOrbit** é usado para excluir o intervalo de órbita de estacionamento de chamadas com o nome Redmond CPO 1.

    Remove-CsCallParkOrbit -Identity "Redmond CPO 1"

## EXEMPLO 2

O comando nesse exemplo remove todos os intervalos de órbitas de estacionamento de chamadas que tiverem sido definidos para uma organização. O comando primeiro chama o cmdlet **Get-CsCallParkOrbit** sem parâmetros, para recuperar todos os intervalos de órbitas de estacionamento de chamadas definidos. Em seguida, direciona essa coleção de intervalos de órbitas de estacionamento de chamadas para o cmdlet **Remove-CsCallParkOrbit**, que remove cada órbita de estacionamento de chamadas.

    Get-CsCallParkOrbit | Remove-CsCallParkOrbit

## EXEMPLO 3

Este comando remove todos os intervalos de órbitas de estacionamento de chamadas cuja identidade incluir a cadeia de caracteres "Redmond", como "Redmond 501", "CP Redmond 1" e "ARedmond". O comando primeiro chama o cmdlet **Get-CsCallParkOrbit** com o parâmetro Filter, para recuperar todos os intervalos de órbitas de estacionamento de chamadas cuja Identidade contiver a cadeia de caracteres Redmond. Esta coleção é direcionada para o cmdlet **Remove-CsCallParkOrbit**, que remove todos os itens da coleção.

    Get-CsCallParkOrbit -Filter *Redmond* | Remove-CsCallParkOrbit

## Descrição detalhada

O cmdlet **Remove-CsCallParkOrbit** exclui o intervalo de órbita de estacionamento de chamadas com o nome passado para o parâmetro Identity, que é obrigatório. Cada órbita de estacionamento de chamada dentro de uma organização deve ter um intervalo exclusivo de números. A remoção de uma órbita de estacionamento de chamada libera o intervalo que estava naquela órbita de estacionamento de chamada. Em seguida, os números liberados podem ser usados em uma órbita de estacionamento de chamada definida recentemente.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsCallParkOrbit** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCallParkOrbit"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O nome do intervalo de órbita de estacionamento de chamadas. Este nome foi atribuído pelo administrador ao definir o intervalo de órbita de estacionamento de chamadas.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de realizar as alterações.</p></td>
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

Objeto Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit. Aceita entradas direcionada dos objetos de órbita de estacionamento de chamadas.

## Tipos de retorno

Este cmdlet não retorna um valor. Remove um objeto do tipo Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit.

## Consulte Também

#### Outros Recursos

[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

