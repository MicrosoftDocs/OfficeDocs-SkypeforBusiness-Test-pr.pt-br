---
title: Remove-CsConferenceDisclaimer
TOCTitle: Remove-CsConferenceDisclaimer
ms:assetid: 196252a1-2526-4944-9064-01d1846f3266
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398243(v=OCS.15)
ms:contentKeyID: 49306026
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConferenceDisclaimer

 

_**Tópico modificado em:** 2015-03-09_

Limpa o texto do cabeçalho e do corpo do aviso de isenção de responsabilidade de conferência utilizado na organização. O aviso de isenção de responsabilidade de conferência é uma mensagem que é exibida para os usuários que participam da conferência usando um hyperlink (por exemplo: usuários que colaram um link para a conferência em um navegador como o Windows Internet Explorer). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsConferenceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 redefine os valores de propriedade do aviso de isenção de responsabilidade global. Isto significa que o cabeçalho e corpo do aviso de isenção de responsabilidade serão definidos com valores nulos, fornecendo um aviso de isenção de responsabilidade em branco.

    Remove-CsConferenceDisclaimer -Identity global

## Descrição detalhada

Ao configurar parâmetros de conferência, os administradores podem incluir um aviso de isenção legal de responsabilidade para os participantes, quando eles entrarem em conferências hospedadas pelo Lync Server. Esse aviso de isenção de responsabilidade é normalmente utilizado para explicar leis de propriedade jurídica e intelectual que se relacionarem com a conferência. O usuários não podem entrar em uma conferência sem concordar com as estipulações dispostas no aviso de isenção de responsabilidade. Observe que esse aviso de isenção de responsabilidade é mostrado somente aos usuários que entrarem em uma conferência usando um hyperlink.

O Lync Server permite uma única instância global do aviso de isenção de responsabilidade de conferência. O cmdlet **Remove-CsConferenceDisclaimer** permite redefinir o aviso de isenção de responsabilidade de conferência: Ao se executar esse cmdlet, definem-se os valores do cabeçalho e do corpo do aviso de isenção de responsabilidade como sendo nulos.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsConferenceDisclaimer** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferenceDisclaimer"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identidade exclusiva do aviso de isenção de responsabilidade de conferência a ser removido. Como só é possível haver uma única instância global do aviso de isenção de responsabilidade de conferência, continuará a ser necessário utilizar o parâmetro Identity para chamar o cmdlet <strong>Remove-CsConferenceDisclaimer</strong>:</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer. O cmdlet **Remove-CsConferenceDisclaimer** aceita entradas canalizadas dos objetos do aviso de isenção de responsabilidade da conferência.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Remove-CsConferenceDisclaimer** redefine instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer com os seus valores de propriedade padrão.

## Consulte Também

#### Outros Recursos

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

