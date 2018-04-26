---
title: Get-CsCpsConfiguration
TOCTitle: Get-CsCpsConfiguration
ms:assetid: d81ee8fe-d02b-4f60-a4d5-6aa84f65d156
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398948(v=OCS.15)
ms:contentKeyID: 49308273
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCpsConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre o serviço Estacionamento de chamadas. O estacionamento de chamadas é um serviço que permite que um usuário "estacione" uma chamada telefônica recebida. O estacionamento de uma chamada a transfere para um número em um intervalo especificado (órbita) e imediatamente a coloca em espera. Qualquer pessoa (não somente a pessoa que originalmente atendeu a chamada) pode retomar a conversa de qualquer telefone no sistema inserindo o número correto. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCpsConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 recupera uma coleção de todas as configurações do serviço Estacionamento de chamadas que tiverem sido definidas para uso na organização.

    Get-CsCpsConfiguration

## EXEMPLO 2

O Exemplo 2 recupera apenas as configurações do serviço Estacionamento de chamadas cuja Identidade for site:Redmond1.

    Get-CsCpsConfiguration -Identity site:Redmond1

## EXEMPLO 3

No Exemplo 3, o parâmetro Filter é usado para retornar todas as configurações do serviço de Estacionamento de Chamadas que foram definidas no escopo do site. A cadeia de caracteres curinga site:\* informa ao cmdlet **Get-CsCpsConfiguration** que retorne somente as configurações cuja identidade começa pelo valor de cadeia de caracteres site:.

    Get-CsCpsConfiguration -Filter site:*

## EXEMPLO 4

Como no Exemplo 3, neste exemplo usamos o parâmetro Filter para recuperar um subconjunto de todas as configurações definidas do serviço Estacionamento de chamadas. Neste caso, efetuamos a filtragem da cadeia de caracteres \*:re\*, que retornará as configurações de Estacionamento de chamadas de todos os sites cujos nomes forem iniciados pelas letras re, como Redmond1, Redmond2 e RemoteComputer.

    Get-CsCpsConfiguration -Filter *:re*

## EXEMPLO 5

O Exemplo 5 retorna todas as configurações do serviço de Estacionamento de Chamadas que não reproduzem música quando um chamador é colocado em espera. Para isso, o comando usa primeiro o cmdlet **Get-CsCpsConfiguration** para recuperar todas as configurações do serviço de Estacionamento de Chamadas definidas para uso na organização. Esta coleção é então canalizada ao cmdlet **Where-Object**, que, por sua vez, aplica um filtro que limita os dados retornados aos itens cuja propriedade EnableMusicOnHold é igual a (-eq) False.

    Get-CsCpsConfiguration | Where-Object {$_.EnableMusicOnHold -eq $False}

## Descrição detalhada

Este cmdlet é usado para recuperar uma ou mais configurações do serviço Estacionamento de chamadas. Uma configuração do serviço Estacionamento de chamadas especifica o que acontecerá a uma chamada quando ela for estacionada. Por exemplo, se uma chamada estacionada não for atendida após um período de tempo, ela poderá ser automaticamente encaminhada a uma outra pessoa (um administrador, por exemplo) ou a um Grupo de Resposta. As chamadas também podem ser configuradas para tocar depois de certo período de tempo, para assegurar que a chamada não será esquecida. Além disso, o serviço Estacionamento de chamadas pode ser configurado para tocar música em espera para o chamador enquanto a chamada estiver estacionada.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsCpsConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCpsConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite executar uma busca de caracteres curinga, para recuperar somente as configurações com valores de identidade que coincidirem com a cadeia de caracteres curinga.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>O identificador exclusivo da configuração do serviço Estacionamento de chamadas que se deseja recuperar. O identificador será Global ou site:&lt;nomedosite&gt;, onde &lt;nomedosite&gt; é o nome do local ao qual se aplica a configuração.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações do serviço Estacionamento de chamadas na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Recupera um ou mais objetos do tipo Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

## Consulte Também

#### Outros Recursos

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

