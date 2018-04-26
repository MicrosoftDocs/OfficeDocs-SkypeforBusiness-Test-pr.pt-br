---
title: Enable-CsPublicProvider
TOCTitle: Enable-CsPublicProvider
ms:assetid: 98370dfd-9a53-41a8-a1f3-bb7a516c3c5e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398780(v=OCS.15)
ms:contentKeyID: 49307546
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Habilita um provedor público configurado para uso na organização. Um provedor público é uma organização que fornece ao público em geral mensagens instantâneas, presença e serviços relacionados. O Lync Server é enviado com três provedores públicos configurados, mas não habilitados: Yahoo\!, AOL e MSN. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Enable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Enable-CsPublicProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 habilita o provedor público cuja identidade for Messenger. Este comando retornará um erro se o Messenger já estiver habilitado.

    Enable-CsPublicProvider -Identity "Messenger"

## EXEMPLO 2

O Exemplo 2 habilita todos os provedores públicos que estiverem desabilitados. Para realizar essa tarefa, o comando primeiro usa o cmdlet **Get-CsPublicProvider** para retornar um conjunto de todos os provedores públicos configurados para uso na organização. Esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona apenas os provedores cuja propriedade Enabled for igual a False. Esse conjunto filtrado é direcionado para o cmdlet **Enable-CsPublicProvider**, que habilita cada provedor no conjunto.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Enable-CsPublicProvider

## EXEMPLO 3

O Exemplo 3 habilita todos os provedores públicos que não estiverem habilitados, desde que o nível de verificação desses provedores esteja definido como AlwaysVerifiable. Para isso, o comando primeiro chama o cmdlet **Get-CsPublicProvider** para retornar uma coleção de todos os provedores públicos em uso na organização. Esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona os provedores que atenderem a dois critérios: 1) a propriedade VerificationLevel deve ser igual a AlwaysVerifiable e 2) a propriedade Enabled deve ser igual a False (o operador -and informa ao cmdlet **Where-Object** que, para serem selecionados, os objetos devem atender a todos os critérios especificados). Esse conjunto filtrado é direcionado para o cmdlet **Enable-CsPublicProvider**, que habilita cada provedor na coleção.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -eq "AlwaysVerifiable" -and $_.Enabled -eq $False} | Enable-CsPublicProvider

## Descrição detalhada

A federação é uma forma segundo a qual duas organizações podem definir uma relação de confiança que facilita a comunicação entre si. Quando uma federação é estabelecida, os usuários nas duas organizações podem enviar mensagens instantâneas entre si, se registrar para notificação de presença e se comunicar entre si utilizando aplicativos SIP como o Lync 2013. O Lync Server permite três tipos de federação: 1) federação direta entre uma organização e a outra, 2) federação entre uma organização e um provedor público e 3) federação entre uma organização e um provedor de hospedagem de terceiros.

Um provedor público é uma organização que fornece serviços de comunicação SIP para o público em geral. Quando se estabelece uma relação de federação com um provedor público, a federação é efetivamente estabelecida em qualquer usuário que tenha uma conta hospedada por esse provedor. Por exemplo, se você estabelecer uma federação com o MSN, os usuários serão capazes de trocar mensagens instantâneas e informações de presença com qualquer um que tenha uma conta de mensagens instantâneas do MSN Messenger.

Para estabelecer uma federação com um provedor público, é preciso criar e habilitar um novo provedor público (além disso, o provedor público precisará criar um relacionamento de federação com você). Os provedores públicos podem ser habilitados quando forem criados ou, posteriormente, utilizando o cmdlet **Enable-CsPublicProvider**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Enable-CsPublicProvider** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Enable-CsPublicProvider"}

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
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Identificador exclusivo do provedor público a ser habilitado. A Identidade é normalmente o nome do website que fornece os serviços (por exemplo, Yahoo!, AOL e MSN).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>Objeto DisplayPublicProvider</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider. O cmdlet **Enable-CsPublicProvider** aceita instâncias por pipeline do objeto de provedor público.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet habilita instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## Consulte Também

#### Outros Recursos

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

