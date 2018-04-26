---
title: New-CsConferenceDirectory
TOCTitle: New-CsConferenceDirectory
ms:assetid: fd5a4369-10cd-4337-94df-51bcaee4fde9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413080(v=OCS.15)
ms:contentKeyID: 49308711
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsConferenceDirectory

 

_**Tópico modificado em:** 2015-03-09_

Cria um novo diretório de conferência para uso na organização. Os diretórios de conferências são usados para ajudar os usuários de conferências discadas a localizar as informações da conferência. Este cmdlet foi introduzido no Lync Server 2010..

## Sintaxe

    New-CsConferenceDirectory -HomePool <String> -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Cria um novo diretório de conferência com a Identidade 42. Esse diretório será hospedado em pool atl-cs-001.litwareinc.com.

    New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"

## Descrição detalhada

Ao se criar um URI de conferência discada, atribui-se um endereço SIP exclusivo a esse URI. No entanto, é difícil converter os endereços SIP para dispositivos que não sejam compatíveis com SIP. Por exemplo: um telefone da rede telefônica pública comutada (PSTN) não pode converter um endereço SIP. Por isso, o Lync Server usa diretórios de conferências como uma maneira de contribuir para que esses dispositivos localizem e se conectem com conferências discadas. Isso é realizado criando-se um diretório de conferência SIP que esteja associado a cada URI de conferência discada e que seja identificado por um valor inteiro, em vez de um URI do SIP. Assim, telefones e outros dispositivos da PSTN podem usar esses números, em vez de um URI SIP ao se conectarem a conferências. O número do diretório é incluído na identificação da conferência da PSTN inserida pelos usuários durante a conexão com uma conferência discada.

Os diretórios de conferências podem ser criados chamando-se o cmdlet **New-CsConferenceDirectory**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsConferenceDirectory** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsConferenceDirectory"}

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
<td><p><em>HomePool</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Nome de domínio totalmente qualificado do pool de registradores no qual será hospedado o novo diretório de conferências. Por exemplo: -Identity atl-cs-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Identificador numérico exclusivo do novo diretório de conferência. As Identidades podem ser qualquer valor inteiro entre 0 e 9999. No entanto, as identidades devem ser exclusivas. (por exemplo, não é possível haver dois diretórios com a Identidade 575.) Não é necessário seguir qualquer tipo de ordem numérica ao se criar novos diretórios. Por exemplo, é possível criar um diretório com a Identidade 999, seguido de um diretório com a Identidade 2, um diretório com a Identidade 438 e assim por diante.</p></td>
</tr>
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
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
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

Nenhuma. O cmdlet **New-CsConferenceDirectory** não aceita a entrada por pipeline.

## Tipos de retorno

Cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories.

## Consulte Também

#### Outros Recursos

[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

