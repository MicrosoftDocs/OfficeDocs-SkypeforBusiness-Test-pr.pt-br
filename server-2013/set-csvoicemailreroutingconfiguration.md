---
title: Set-CsVoicemailReroutingConfiguration
TOCTitle: Set-CsVoicemailReroutingConfiguration
ms:assetid: c16a0d47-318b-46e4-991c-e4842403dbe3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412948(v=OCS.15)
ms:contentKeyID: 49307994
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoicemailReroutingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica as definições que permitem aos números de telefone da rede telefônica pública comutada (PSTN) acessar os recursos Acesso ao Assinante e Atendedor Automático do UM do Exchange. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicemailReroutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AutoAttendantNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-SubscriberAccessNumber <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse exemplo habilita as definições de configuração de redirecionamento de correio de voz do site Redmond1.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True

## EXEMPLO 2

Esse exemplo modifica as definições de redirecionamento do correio de voz que se aplicarem ao site Redmond1, definindo como +14255551213 o número de telefone para o Acesso ao Assinante.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"

## Descrição detalhada

Esse cmdlet permite modificar as definições que determinam para onde serão redirecionadas as chamadas do Atendedor Automático e do Acesso ao Assinante, quando se perder a conectividade IP com um servidor do UM do Exchange.

O Atendedor Automático e o Acesso ao Assinante são recursos do UM do Exchange. O recurso Atendedor Automático proporciona reconhecimento de voz e controle de discagem de tom (multifrequência de tom dual, ou DTMF) para que os chamadores externos naveguem no sistema telefônico de uma empresa e consigam entrar em contato com o departamento ou funcionário desejado ou, quando no modo Anotação de recados, aceitem as mensagens para usuários (é recomendável adotar o redirecionamento de voz para o modo Anotação de Recado). O recurso Acesso ao Assinante permite que os usuários internos acessem a sua caixa de correio do Microsoft Outlook a partir de um telefone. Os números fornecidos por essas configurações permitem ao chamador deixar mensagens de voz para usuários do Enterprise Voice (a definição AutoAttendantNumber) e, a estes usuários, recuperar mensagens de voz, mesmo se não houver conectividade IP da implantação do Lync Server em um site remoto com o UM do Exchange no data center (a definição SubscriberAccessNumber).

Observe que essas definições não estarão disponíveis, a menos que a propriedade Enabled tenha sido definida como True.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsVoicemailReroutingConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de RBAC às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicemailReroutingConfiguration"}

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
<td><p><em>AutoAttendantNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Número de telefone do Atendedor Automático ao qual as tentativas de armazenamento de correio de voz devem ser redirecionadas.</p>
<p>O número fornecido a este parâmetro deve ser um LineUri de um objeto de contato existente.</p>
<p>O valor deve ser um número iniciado por um dígito entre 1 e 9, opcionalmente precedido por um sinal de adição (+) e seguido de qualquer número de dígitos.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se as tentativas de acessar a mensagem de voz deverão ser redirecionadas através da PSTN, quando não houver conectividade IP.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>O identificador exclusivo da configuração que se deseja modificar. Para esse cmdlet, a Identidade será Global ou Site: &lt;nomedosite&gt;, onde &lt;nomedosite&gt; é o nome do site ao qual as definições serão aplicadas.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>VoicemailReroutingConfiguration</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p>
<p>Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration, que pode ser recuperado chamando o cmdlet <strong>Get-CsVoicemailReroutingConfiguration</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>SubscriberAccessNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Número de acesso do assinante ao qual deverão se redirecionar as tentativas de recuperação de mensagens de voz.</p>
<p>O número fornecido a este parâmetro deve ser um LineUri de um objeto de contato existente.</p>
<p>O valor deve ser um número iniciado por um dígito entre 1 e 9, opcionalmente precedido por um sinal de adição (+) e seguido de qualquer número de dígitos.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration. Aceita entradas direcionadas de objetos de configuração de redirecionamento de correio de voz.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.

## Consulte Também

#### Outros Recursos

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

