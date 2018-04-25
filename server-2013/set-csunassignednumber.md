---
title: Set-CsUnassignedNumber
TOCTitle: Set-CsUnassignedNumber
ms:assetid: e7f52423-58d1-410a-9071-731bde45d3d4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399033(v=OCS.15)
ms:contentKeyID: 49308446
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUnassignedNumber

 

_**Tópico modificado em:** 2015-03-09_

Modifica um intervalo existente de números não atribuídos e as regras de roteamento que se aplicarem a esses números. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -AnnouncementName <String> -AnnouncementService <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Priority <Int32>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse exemplo modifica o intervalo de número não-atribuído cujo nome for UNSet1. Primeiro, passamos para o parâmetro Identity o valor UNSet1, o nome do intervalo de números atribuídos que queremos modificar. Utilizam-se os parâmetros NumberRangeStart (+14255551000) e NumberRangeEnd (+14255551900) para modificar o intervalo de números não atribuídos ao qual se aplicará o comunicado ou o Atendedor Automático especificado.

    Set-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"

## EXEMPLO 2

Este exemplo modifica o Comunicado de todas as configurações de intervalo de números não atribuídos que têm atualmente um Comunicado com a cadeia de caracteres "Bem-vindo" no nome. Primeiro, o cmdlet **Get-CsUnassignedNumber** é chamado para recuperar todas as configurações de números não atribuídos. Canalizamos esta coleção de definições ao cmdlet **Where-Object**, que restringe a coleção apenas às configurações cuja propriedade AnnouncementName contém (-match) a cadeia de caracteres Bem-vindo. Assim que essas configurações forem recuperadas, elas serão canalizadas ao cmdlet **Set-CsUnassignedNumber**, onde modificaremos o ID do Servidor de Aplicativos do Serviço de Comunicados (ApplicationServer:redmond.litwareinc.com) com o parâmetro AnnouncementService e o nome do novo comunicado (Comunicado do Suporte Técnico) com o parâmetro AnnouncementName. Observe que, mesmo que o novo Comunicado tenha um nome diferente, mas o mesmo ID do serviço, você deverá especificar o ID do serviço em conjunto com o nome.

    Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Set-CsUnassignedNumber -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Help Desk Announcement"

## Descrição detalhada

Os números não atribuídos são números de telefone que foram atribuídos a uma organização, mas não a usuários ou telefones específicos. É possível especificar que Lync Server encaminhe chamadas para certos destinos, quando se chamar um número não atribuído. Este cmdlet modifica as definições que especificam esse roteamento.

Para modificar algumas das configurações desse cmdlet, é necessário que Comunicados já esteja definido no sistema ou que haja um Atendedor Automático do UM do Exchange configurado. Para determinar se você tem Comunicados, chame o cmdlet **Get-CsAnnouncement**. Para criar um novo Comunicado, chame o cmdlet **New-CsAnnouncement**. Para verificar as configurações do Atendedor Automático do UM do Exchange, execute o cmdlet **Get-CsExUmContact**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsUnassignedNumber** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUnassignedNumber"}

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
<td><p><em>AnnouncementName</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O nome do Comunicado que será usado para gerenciar as chamadas destinadas a esse intervalo de números.</p></td>
</tr>
<tr class="even">
<td><p><em>AnnouncementService</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O nome de domínio totalmente qualificado (FQDN) ou ID do serviço do servidor de Comunicados.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExUmAutoAttendantPhoneNumber</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O número de telefone do Atendedor Automático do UM do Exchange para o qual serão roteadas as chamadas nesse intervalo. O contato do Atendedor Automático do UM do Exchange já deve estar definido, para que se possa atribuir um valor a esse parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O nome exclusivo do intervalo de números não-atribuídos que estão sendo modificados.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>DisplayAnnouncementVacantNumberRange</p></td>
<td><p>Uma referência a um objeto que contém definições de números não-atribuídos. Este objeto deve ser do tipo Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange e pode ser recuperado chamando-se o cmdlet <strong>Get-CsUnassignedNumber</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O último número no intervalo de números não-atribuídos. Deve ser maior ou igual ao número fornecido para NumberRangeStart. Para especificar um intervalo de um número, use o mesmo número para NumberRangeStart e NumberRangeEnd.</p>
<p>Os números devem corresponder à expressão regular (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. Isso significa que o número pode começar com a cadeia de caracteres tel: (se você não especificar essa cadeia de caracteres, ela será adicionada automaticamente para você), um sinal de adição (+) e um dígito de 1 a 9. O número de telefone pode ter até 17 dígitos e pode ser seguido de um ramal no formato ;ext=, seguido do número do ramal.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O primeiro número no intervalo de números não-atribuídos. Deve ser menor ou igual ao valor fornecido para NumberRangeEnd.</p>
<p>Os números devem corresponder à expressão regular (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. Isso significa que o número pode começar com a cadeia de caracteres tel: (se você não especificar essa cadeia de caracteres, ela será adicionada automaticamente), um sinal de adição (+) e um dígito de 1 a 9. O número de telefone pode ter até 17 dígitos e pode ser seguido de um ramal no formato ;ext=, seguido do número do ramal.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>É possível que intervalos de números não-atribuídos se sobreponham. Se um número estiver dentro de mais de um intervalo, o intervalo com a prioridade mais alta terá efeito.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange. Aceita entradas canalizadas de objetos de números não atribuídos.

## Tipos de retorno

Este cmdlet não retorna um valor. Modifica um objeto do tipo Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.

## Consulte Também

#### Outros Recursos

[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)  
[New-CsAnnouncement](new-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Get-CsExUmContact](get-csexumcontact.md)

