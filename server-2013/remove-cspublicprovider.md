---
title: Remove-CsPublicProvider
TOCTitle: Remove-CsPublicProvider
ms:assetid: b9eec2f4-cf36-41b7-8023-67790cc8d4cd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412906(v=OCS.15)
ms:contentKeyID: 49307926
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Remove um provedor público configurado para uso em sua organização. Um provedor público é uma organização que fornece ao público em geral mensagens instantâneas, presença e serviços relacionados. O Lync Server é enviado com três provedores públicos configurados, mas não habilitados: Yahoo\!, AOL e MSN. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsPublicProvider -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 exclui o provedor público cuja Identidade for Messenger. Depois que este comando tiver sido concluído, Messenger não aparecerá mais na lista de provedores públicos configurados. Nesse momento, a única maneira de restabelecer a federação com o Messenger é recriando o provedor.

    Remove-CsPublicProvider -Identity "Messenger"

## EXEMPLO 2

O Exemplo 2 exclui todos os provedores públicos configurados para uso na organização. Para isso, o comando primeiro usa o cmdlet **Get-CsPublicProvider**, para retornar um conjunto de todos os provedores públicos configurados. Esse conjunto é então direcionado para o cmdlet **Remove-CsPublicProvider**, que, por sua vez, exclui cada provedor na coleção.

    Get-CsPublicProvider | Remove-CsPublicProvider

## EXEMPLO 3

No Exemplo 3, todos os provedores públicos que estiverem desabilitados serão removidos do conjunto de provedores públicos configurados. Para realizar essa tarefa, o comando primeiro usa o cmdlet **Get-CsPublicProvider**, para retornar um conjunto de todos os provedores públicos configurados. Este conjunto é direcionado para o cmdlet **Where-Object**, que seleciona apenas os provedores cuja propriedade Enable for igual a False. Este conjunto filtrado é então direcionado para o cmdlet **Remove-CsPublicProvider**, que exclui todos os itens no conjunto.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Remove-CsPublicProvider

## Descrição detalhada

A federação é uma forma segundo a qual duas organizações podem definir uma relação de confiança que facilita a comunicação entre os dois grupos. Quando uma federação é estabelecida, os usuários nas duas organizações podem enviar mensagens instantâneas entre si, se registrar para notificação de presença e se comunicar entre si utilizando aplicativos SIP como o Lync 2013. O Lync Server permite três tipos de federação: 1) federação direta entre uma organização e a outra, 2) federação entre uma organização e um provedor público e 3) federação entre uma organização e um provedor de hospedagem de terceiros.

Um provedor público é uma organização que fornece serviços de comunicação SIP para o público em geral. Quando uma relação de federação com um provedor público é estabelecida, a federação é efetivamente estabelecida com qualquer usuário que tenha uma conta hospedada por esse provedor. Por exemplo, se você estabelecer uma federação com o Messenger (MSN), os usuários serão capazes de trocar mensagens instantâneas e informações de presença com qualquer um que tenha uma conta de mensagens instantâneas do Messenger (MSN).

Para estabelecer uma federação com um provedor público, é preciso criar e habilitar um novo provedor público (além disso, o provedor público precisará criar um relacionamento de federação com você). Se, posteriormente, você decidir encerrar esse relacionamento, utilize o cmdlet **Remove-CsPublicProvider** para excluir o provedor público. Ao excluir um provedor público, ele será removido da lista de parceiros federados; a partir daí, a única forma de restabelecer o relacionamento é recriar o provedor. Se, em vez disso, você optar por suspender temporariamente o relacionamento, utilize o cmdlet **Disable-CsPublicProvider**. Quando um provedor público é desabilitado, ele não será excluído da lista de parceiros federados; em vez disso, será simplesmente marcado como desabilitado e a comunicação entre a organização e esse provedor será suspensa. Para restabelecer o relacionamento, é possível utilizar o cmdlet **Enable-CsPublicProvider** para reabilitar o provedor.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsPublicProvider** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPublicProvider"}

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
<td><p>Identificador exclusivo do provedor público a ser removido. Normalmente, a Identidade é o nome do website que oferece os serviços (por exemplo: Yahoo!, AOL, MSN, etc.).</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider. O cmdlet **Remove-CsPublicProvider** aceita instâncias direcionadas do objeto de provedor público.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet exclui instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## Consulte Também

#### Outros Recursos

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

