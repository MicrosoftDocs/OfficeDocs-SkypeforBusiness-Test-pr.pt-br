---
title: Remove-CsConferenceDirectory
TOCTitle: Remove-CsConferenceDirectory
ms:assetid: c2c62a14-f3f3-472f-bf91-1fcea9e45425
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412961(v=OCS.15)
ms:contentKeyID: 49308024
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConferenceDirectory

 

_**Tópico modificado em:** 2015-03-09_

Remove um diretório de conferência existente. Os diretórios de conferência são usados para ajudar os usuários de conferências discadas a localizar informações da conferência. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 exclui o diretório de conferências cuja Identidade for 2.

    Remove-CsConferenceDirectory -Identity 2

## EXEMPLO 2

O Exemplo 2 exclui todos os diretórios de conferências encontrados no serviço UserServer:atl-cs-001.litwareinc.com. Para isso, o comando primeiro chama o cmdlet **Get-CsConferenceDirectory** sem nenhum parâmetro, retornando uma coleção de todos os diretórios de conferências em uso na organização. Essa coleção será então direcionada para o cmdlet **Where-Object**, que selecionará apenas os diretórios hospedados no serviço UserServer:atl-cs-001.litwareinc.com. Por sua vez, essa coleção filtrada será então direcionada para o cmdlet **Remove-CsConferenceDirectory**, que a excluirá.

    Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"} | Remove-CsConferenceDirectory

## Descrição detalhada

Ao criar um Identificador de recurso uniforme (URI) de conferência discada, um endereço SIP exclusivo é atribuído a esse URI. No entanto, é difícil converter os endereços SIP para dispositivos que não sejam compatíveis com SIP. Por exemplo: um telefone da rede telefônica pública comutada (PSTN) não pode converter um endereço SIP. Por isso, o Lync Server usa diretórios de conferências como uma maneira de contribuir para que esses dispositivos localizem e se conectem a conferências discadas. Isso é realizado criando um diretório de conferência SIP que seja associado a cada URI de conferência discada e identificado por um valor inteiro, em vez de um URI do SIP. Assim, telefones e outros dispositivos da PSTN podem usar esses números, em vez de um URI do SIP ao se conectarem a conferências. O número do diretório é incluído na identificação da conferência PSTN inserida pelos usuários durante a conexão com uma conferência discada.

Os diretórios de conferência são criados usando o cmdlet **New-CsConferenceDirectory**. Ocasionalmente, será necessário excluir um ou vários desses diretórios. Por exemplo: pode ser necessário desativar o pool em que foram hospedados os diretórios. Os diretórios de conferências podem ser removidos chamando o cmdlet **Remove-CsConferenceDirectory**. Observe que, se for necessário transferir um diretório de um pool para outro, isso poderá ser feito chamando o cmdlet **Move-CsConferenceDirectory**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsConferenceDirectory** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferenceDirectory"}

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
<td><p>Identidade numérica do diretório de conferência a ser removido.</p></td>
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
<td><p>Quando estiver presente, remove o diretório de conferência mesmo se o pool que hospeda o diretório estiver indisponível. Por padrão, o cmdlet <strong>Remove-CsConferenceDirectory</strong> não removerá os diretórios se o pool correspondente não puder ser contatado.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories. O cmdlet **Remove-CsConferenceDirectory** aceita entradas direcionadas dos objetos do diretório da conferências.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Removes-CsConferenceDirectory** exclui instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories.

## Consulte Também

#### Outros Recursos

[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)

