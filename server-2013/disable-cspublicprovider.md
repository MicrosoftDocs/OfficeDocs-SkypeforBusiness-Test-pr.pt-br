---
title: Disable-CsPublicProvider
TOCTitle: Disable-CsPublicProvider
ms:assetid: df1338ea-fe6d-45da-a39c-86108bb54ef5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398984(v=OCS.15)
ms:contentKeyID: 49308338
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Desabilita um provedor público configurado para uso na organização. Um provedor público é uma organização que fornece ao público em geral mensagens instantâneas, presença e serviços relacionados. O Lync Server é enviado com três provedores públicos configurados, mas não habilitados: Yahoo\!, AIM (AOL); e Messenger (MSN). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Disable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Disable-CsPublicProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 desabilita o provedor público cuja Identidade for Messenger. Este comando retornará um erro se MSN já estiver desabilitado.

    Disable-CsPublicProvider -Identity "Messenger"

## EXEMPLO 2

O Exemplo 2 desabilita todos os provedores públicos atualmente habilitados. Para isso, o comando usa primeiro o cmdlet **Get-CsPublicProvider** para retornar uma coleção de todos os provedores públicos atualmente em uso na organização. Esta coleção é canalizada ao cmdlet **Where-Object**, que seleciona apenas os provedores cuja propriedade Enable é igual a True. Por sua vez, esta coleção filtrada é canalizada ao cmdlet **Disable-CsPublicProvider**, que desabilita cada provedor da coleção.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsPublicProvider

## EXEMPLO 3

O comando mostrado no Exemplo 3 desabilita todos os provedores públicos atualmente habilitados, com um nível de verificação definido como AlwaysVerifiable. Para realizar esta tarefa, o comando chama primeiro o cmdlet **Get-CsPublicProvider** para retornar uma coleção de todos os provedores públicos atualmente em uso na organização. Esta coleção é então canalizada ao cmdlet **Where-Object**, que seleciona os provedores que atendem a dois critérios: 1) a propriedade VerificationLevel deve ser igual a AlwaysVerifiable e 2) a propriedade Enabled deve ser igual a True (o operador -and informa ao cmdlet **Where-Object** que os objetos devem atender a todos os critérios especificados para serem selecionados). Esta coleção filtrada é canalizada ao cmdlet **Disable-CsPublicProvider**, que desabilita cada provedor dessa coleção.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsPublicProvider

## Descrição detalhada

A federação é uma forma segundo a qual duas organizações podem definir uma relação de confiança que facilita a comunicação entre si. Quando se estabelece uma federação, os usuários nas duas organizações podem enviar mensagens instantâneas entre si, se registrar para notificação de presença e se comunicar entre si utilizando aplicativos SIP como o Lync 2013. O Lync Server permite três tipos de federação: 1) federação direta entre uma organização e a outra, 2) federação entre uma organização e um provedor público e 3) federação entre uma organização e um provedor de hospedagem de terceiros.

Um provedor público é uma organização que fornece serviços de comunicação SIP para o público em geral. Quando se estabelece uma relação de federação com um provedor público, a federação é efetivamente estabelecida com qualquer usuário que tenha uma conta hospedada por esse provedor. Por exemplo, se você estabelecer uma federação com o Messenger (MSN), os usuários serão capazes de trocar mensagens instantâneas e informações de presença com qualquer um que tenha uma conta de mensagens instantâneas do Messenger (MSN).

Para estabelecer uma federação com um provedor público, é preciso criar e habilitar um novo provedor público (além disso, o provedor público precisará criar um relacionamento de federação com você). Ao se criar um provedor público, será possível habilitar ou desabilitar esse relacionamento de federação. Se um provedor público for habilitado, os usuários da organização poderão trocar mensagens instantâneas e informações de presença com pessoas que possuírem contas no provedor público. Se um provedor público for desabilitado, a capacidade de se comunicar com pessoas que possuírem contas com o provedor público será suspensa e permanecerá assim até que o provedor seja habilitado novamente. Se precisar suspender temporariamente o relacionamento com o provedor, utilize o cmdlet **Disable-CsPublicProvider**. Se preferir excluir esse provedor, utilize o cmdlet **Remove-CsPublicProvider**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Disable-CsPublicProvider** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsPublicProvider"}

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
<td><p>Identificador exclusivo do provedor público a ser desabilitado. Normalmente, a Identidade é o nome do website que oferece os serviços (por exemplo: Yahoo!, AOL, MSN, etc.).</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider. O cmdlet **Disable-CsPublicProvider** aceita instâncias por pipeline do objeto de provedor público.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet desabilita instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## Consulte Também

#### Outros Recursos

[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

