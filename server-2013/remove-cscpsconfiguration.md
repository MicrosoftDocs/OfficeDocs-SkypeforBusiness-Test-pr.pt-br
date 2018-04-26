---
title: Remove-CsCpsConfiguration
TOCTitle: Remove-CsCpsConfiguration
ms:assetid: 546343e1-a2e4-4bc0-bf6d-c8ae9bb3e690
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398358(v=OCS.15)
ms:contentKeyID: 49306733
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCpsConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Remove uma configuração existente de serviço Estacionamento de chamadas. O estacionamento de chamadas é um serviço que permite que um usuário "estacione" uma chamada telefônica recebida. O estacionamento de uma chamada a transfere para um número em um intervalo especificado (órbita) e imediatamente a coloca em espera. Alguém (não somente a pessoa que originalmente tiver atendido à chamada) pode retomar a conversa de qualquer telefone, bastando digitar o número correto. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsCpsConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 usa o cmdlet **Remove-CsCpsConfiguration** para excluir a configuração do serviço Estacionamento de chamadas cuja identidade for site:Redmond1. Uma vez que as identidades são únicas, este comando resultará em somente uma configuração a ser excluída.

    Remove-CsCpsConfiguration -Identity site:Redmond1

## EXEMPLO 2

No Exemplo 2, serão excluídas todas as configurações de serviço Estacionamento de chamadas que tiverem sido definidas no escopo de site. Para executar esta tarefa, o comando usa primeiramente o cmdlet **Get-CsCpsConfiguration** e o parâmetro Filter, para retornar todas as configurações do serviço Estacionamento de chamadas que tiverem sido definidas no escopo de site; o caractere curinga site:\* garante que somente as configurações cuja identidade for iniciada pelo valor da cadeia de caracteres site: serão retornadas. Esta coleção filtrada será então canalizada para o cmdlet **Remove-CsCpsConfiguration**, que excluirá cada item na coleção. Observe que sempre que se remover as definições do serviço Estacionamento de chamadas de um site, ele passará automaticamente a usar as definições do serviço Estacionamento de chamadas configuradas no escopo global.

    Get-CsCpsConfiguration -Filter site:* | Remove-CsCpsConfiguration

## Descrição detalhada

Este cmdlet é usado para remover a configuração do serviço Estacionamento de chamadas. Uma configuração do serviço Estacionamento de chamadas especifica o que acontece à chamada depois que ela é estacionada. Por exemplo, se uma chamada estacionada não for respondida após um período de tempo, ela poderá ser automaticamente encaminhada a uma outra pessoa (um administrador, por exemplo) ou a um Grupo de Resposta. As chamadas podem ser configuradas para tocar depois de certo período de tempo, para assegurar que a chamada não será esquecida. Além disso, o serviço Estacionamento de chamadas pode ser configurado para tocar música em espera para o chamador enquanto a chamada estiver estacionada.

Este cmdlet pode ser usado para remover quaisquer configurações do Estacionamento de chamadas, inclusive a configuração Global. No caso da configuração Global, entretanto, a configuração na verdade não será removida. Em vez disso, ela será simplesmente redefinida com o seu valor padrão.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsCpsConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCpsConfiguration"}

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
<td><p>O identificador exclusivo da configuração do serviço Estacionamento de chamadas que se deseja remover. O identificador será global ou site:&lt;nomedosite&gt;, onde &lt;nomedosite&gt; é o nome do local ao qual se aplica a configuração.</p></td>
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
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings. Aceita entrada canalizada dos objetos de configuração do serviço Estacionamento de chamadas.

## Tipos de retorno

Remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

## Consulte Também

#### Outros Recursos

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

