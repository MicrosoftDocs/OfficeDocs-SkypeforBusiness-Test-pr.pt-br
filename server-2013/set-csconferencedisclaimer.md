---
title: Set-CsConferenceDisclaimer
TOCTitle: Set-CsConferenceDisclaimer
ms:assetid: 97afce6d-b031-466d-a170-3ca50d6df245
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398776(v=OCS.15)
ms:contentKeyID: 49307543
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConferenceDisclaimer

 

_**Tópico modificado em:** 2015-03-09_

Modifica os valores de propriedade do aviso de isenção de responsabilidade de conferência utilizado na organização. O aviso de isenção de responsabilidade de conferência é uma mensagem exibida para usuários que participam da conferência usando um hiperlink (por exemplo, usuários que colaram um link para a conferência em um navegador como o Windows Internet Explorer). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsConferenceDisclaimer [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Body <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Header <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 modifica as propriedades Header e Body do aviso de isenção de responsabilidade de conferência da organização. Como só é possível ter um único aviso de isenção de responsabilidade, não é necessário especificar a identidade ao executar o cmdlet **Set-CsConferenceDisclaimer**.

    Set-CsConferenceDisclaimer -Header "Litwareinc.com Online Conference" -Body "Important note: Conferencing proceedings are recorded and archived."

## Descrição detalhada

Ao configurar parâmetros de conferência, os administradores podem incluir um aviso de isenção legal de responsabilidade para os participantes, a ser exibido quando eles entrarem em conferências hospedadas pelo Lync Server. Esse aviso de isenção de responsabilidade é normalmente utilizado para explicar leis de propriedade jurídica e intelectual que se relacionam com a conferência. O usuários não podem entrar em uma conferência sem concordar com as estipulações dispostas no aviso de isenção de responsabilidade. Observe que, no entanto, esse aviso de isenção de responsabilidade é exibido somente a usuários que entram em uma conferência usando um hiperlink.

O Lync Server permite uma única instância global do aviso de isenção de responsabilidade de conferência. O cmdlet **Set-CsConferenceDisclaimer** permite modificar o aviso de isenção de responsabilidade de conferência usado na organização.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsConferenceDisclaimer** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferenceDisclaimer"}

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
<td><p><em>Body</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Conteúdo do aviso de isenção de responsabilidade de conferência.</p></td>
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
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Header</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Título dado ao aviso de isenção de responsabilidade de conferência.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identidade exclusiva do aviso de isenção de responsabilidade de conferência. Como só é possível ter uma única instância global do aviso de isenção de responsabilidade de conferência, não é necessário especificar uma identidade ao chamar o cmdlet <strong>Set-CsConferenceDisclaimer</strong>. Entretanto, é possível utilizar a sintaxe a seguir para fazer referência ao aviso de isenção de responsabilidade global: -Identity global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>Objeto ConferenceDisclaimer</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer. O cmdlet **Set-CsConferenceDisclaimer** aceita entrada por pipeline dos objetos do aviso de isenção de responsabilidade da conferência.

## Tipos de retorno

O cmdlet **Set-CsConferenceDisclaimer** não retorna qualquer objeto ou valor. Em vez disso, modifica instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer.

## Consulte Também

#### Outros Recursos

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)  
[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

