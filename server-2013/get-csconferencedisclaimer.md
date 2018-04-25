---
title: Get-CsConferenceDisclaimer
TOCTitle: Get-CsConferenceDisclaimer
ms:assetid: 2382aaef-9c5e-43f8-99de-6c880134db7d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425714(v=OCS.15)
ms:contentKeyID: 49306134
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferenceDisclaimer

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre o aviso de isenção de responsabilidade de conferência usado na organização. O aviso de isenção de responsabilidade de conferência é uma mensagem que é exibida aos usuários que ingressam na conferência usando um hyperlink (por exemplo: usuários que colam o link para a conferência em um navegador, como o Windows Internet Explorer). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDisclaimer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 retorna informações sobre o aviso de isenção de responsabilidade de conferência configurado para uso na organização. Como se está limitado a um único aviso de isenção de responsabilidade (configurado no escopo global), não é necessário especificar uma identidade ao se executar este comando.

    Get-CSConferenceDisclaimer

## Descrição detalhada

Ao configurar as definições de conferências, os administradores podem incluir um aviso de isenção legal de responsabilidade para os participantes, quando eles entrarem em conferências hospedadas pelo Lync Server. Este aviso de isenção geralmente é usado para explicar leis de propriedade legal e intelectual referentes à conferência, e os usuários não poderão participar sem concordar com as cláusulas estabelecidas nesse aviso. Observe que esse aviso de isenção só será mostrado aos usuários que ingressarem em uma conferência usando um hyperlink.

O cmdlet **Get-CsConferenceDisclaimer** permite exibir o corpo e o cabeçalho do aviso de isenção de responsabilidade da organização.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsConferenceDisclaimer** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDisclaimer"}

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
<td><p>Permite utilizar valores de caracteres curinga ao se fazer referência a um aviso de isenção de responsabilidade de conferência. Como só é possível haver uma instância global do aviso de isenção de responsabilidade de conferência, não há motivo para utilizar o parâmetro Filter. Entretanto, é possível utilizar a seguinte sintaxe para fazer referência ao aviso de isenção de responsabilidade global: -Filter &quot;g*&quot;. Esta sintaxe retorna todos os avisos de isenção de responsabilidade de conferência cuja identidade começar com a letra &quot;g&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identidade exclusiva do aviso de isenção de responsabilidade de conferência. Como só é possível haver uma única instância global do aviso de isenção de responsabilidade de conferência, não é necessário especificar uma identidade ao se chamar o cmdlet <strong>Get-CsConferenceDisclaimer</strong>. No entanto, é possível utilizar a seguinte sintaxe para fazer referência ao aviso de isenção de responsabilidade global: -Identity global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados do aviso de isenção de responsabilidade da conferência na réplica local do Repositório de Gerenciamento Central, em vez do próprio Repositório de Gerenciamento Central.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Get-CsConferenceDisclaimer** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer.

## Consulte Também

#### Outros Recursos

[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

