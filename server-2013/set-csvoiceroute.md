---
title: Set-CsVoiceRoute
TOCTitle: Set-CsVoiceRoute
ms:assetid: b786aec0-946e-4ce5-812e-25e5d8cfa4d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412893(v=OCS.15)
ms:contentKeyID: 49307884
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceRoute

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma rota de voz. As rotas de voz contêm instruções que informam ao Lync Server como rotear chamadas de usuários do Enterprise Voice para números de telefone na PSTN (rede telefônica pública comutada) ou em uma PBX (Central Privada de Comutação). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AlternateCallerId <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-NumberPattern <String>] [-Priority <Int32>] [-PstnGatewayList <PSListModifier>] [-PstnUsages <PSListModifier>] [-SuppressCallerId <$true | $false>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este comando define a Descrição da rota de voz Route1 para "Test Route".

    Set-CsVoiceRoute -Identity Route1 -Description "Test Route"

## EXEMPLO 2

O comando neste exemplo modifica a rota de voz com a identidade Route1, para adicionar o uso da PSTN Interurbano à lista de usos desta rota de voz. A chamada interurbana deve estar na lista de usos de PSTN globais (que podem ser recuperados chamando o cmdlet **Get-CsPstnUsage**).

    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{add="Long Distance"}

## EXEMPLO 3

Este exemplo modifica a rota de voz denominada Route1, preenchendo a lista da rota de usos da PSTN com todos os usos existentes na organização. O primeiro comando neste exemplo recupera a lista de usos PSTN globais. Observe que a chamada para o cmdlet **Get-CsPstnUsage** está entre parênteses; isso significa que primeiro recuperamos um objeto que contém informações sobre o uso da PSTN (como há somente um uso de PSTN global, será recuperado somente um objeto). O comando então recupera a propriedade Usage deste objeto. Essa propriedade, que contém uma lista de usos da PSTN, é atribuída à variável $x. Na segunda linha deste exemplo, o cmdlet **Set-CsVoiceRoute** é chamado para modificar a rota de voz cuja identidade for Route1. Observe o valor passado ao parâmetro PstnUsages: @{replace=$x}. Este valor informa que tudo na lista de PstnUsages correspondente a essa rota deve ser substituído pelo conteúdo de $x, que contém a lista de usos de PSTN recuperada na linha 1.

    $x = (Get-CsPstnUsage).Usage
    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{replace=$x}

## EXEMPLO 4

Este conjunto de comandos modifica a propriedade Name da rota de voz com a identidade Route1 para RouteA. Alterar a propriedade Name modifica automaticamente a propriedade Identity, neste caso para RouteA.

Na primeira linha, o cmdlet **Get-CsVoiceRoute** é chamado para recuperar a rota de voz com a identidade Route1. O objeto retornado é armazenado na variável $x. Em seguida, será atribuído o valor de cadeia de caracteres "RouteA" à propriedade Name desse objeto. Finalmente, o objeto (contido na variável $ x) é passado para o parâmetro Instance do cmdlet **Set-CsVoiceRoute**, para efetuar a mudança.

    $x = Get-CsVoiceRoute -Identity Route1
    $x.Name = "RouteA"
    Set-CsVoiceRoute -Instance $x

## EXEMPLO 5

Esse exemplo modifica a rota de voz denominada Route1 e preenche a lista de gateways PSTN (PstnGatewayList) dessa rota com a função de servidor do gateway cuja Identidade for PstnGateway:192.168.0.100. Na primeira linha desse exemplo, o cmdlet **Get-CsVoiceRoute** é chamado para recuperar a rota de voz que desejamos modificar (Rota 1, nesse caso). Em seguida, o método Add é chamado na propriedade PstnGatewayList de Route1. Passamos ao método Add a Identity do serviço que desejamos adicionar. Finalmente, chamamos o cmdlet **Set-CsVoiceRoute**, passando ao parâmetro Instance a variável $y, que atualizará Route1 (armazenada em $y) com o gateway PSTN recém-adicionado.

    $y = Get-CsVoiceRoute -Identity Route1
    $y.PstnGatewayList.Add("PstnGateway:192.168.0.100")
    Set-CsVoiceRoute -Instance $y

## Descrição detalhada

Use este cmdlet para modificar uma rota de voz existente. As rotas de voz são associadas a políticas de voz por meio de usos da PSTN. Uma rota de voz inclui uma expressão regular que identifica quais números de telefone serão roteados por uma determinada rota de voz: os números de telefone que combinam com a expressão regular serão roteados por esta rota.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsVoiceRoute** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceRoute"}

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
<td><p><em>AlternateCallerId</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Se o parâmetro SuppressCallerId for definido como True, o valor do parâmetro AlternateCallerId será exibido aos destinatários, e não ao número real do chamador. Este número deve ser um número válido e pode ser usado para representar uma divisão dentro de uma organização, como Suporte ou Recursos Humanos</p>
<p>Se o parâmetro SuppressCallerId for definido como False, o parâmetro AlternateCallerId será ignorado.</p>
<p>Os valores devem combinar com a expressão regular (\+)?[1-9]\d*(;ext=[1-9]\d*)?. Em outras palavras, o valor pode iniciar com um sinal de mais (+), mas não é necessário; deve consistir em qualquer número de dígitos; e pode ser seguido por uma extensão que inicia com ;ext= seguida por qualquer número de dígitos (observe que se uma extensão for incluída, a cadeia de caracteres deverá ser colocada entre aspas duplas).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma descrição para que serve esta rota de telefone.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>A identidade exclusiva da rota de voz (se o nome da rota contiver um espaço, como Test Route, você deverá colocar a cadeia de caracteres completa entre parênteses).</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>Rota</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route e pode ser recuperado chamando o cmdlet <strong>Get-CsVoiceRoute</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberPattern</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma expressão regular que especifica os números de telefone aos quais se aplica esta rota. Os números que combinam com este modelo serão roteados segundo o restante das configurações de roteamento. Por exemplo: o modelo de número padrão [0-9] {10} especifica um número de 10 dígitos que contém qualquer dígito de 0 a 9.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>Um número pode ser resolvido para diversas rotas de voz. A prioridade determina a ordem na qual serão aplicadas as rotas, se houver mais de uma rota possível.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnGatewayList</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Um Servidor de Mediação pode ser associado a diversos gateways. Este parâmetro contém uma lista de gateways associados a essa rota de voz. Cada membro desta lista deve ser a Identidade do serviço do gateway PSTN ou Servidor de Mediação. O valor poderá fazer referência a um Servidor de Mediação apenas se a Servidor de Mediação estiver configurada para o Microsoft Office Communications Server 2007 ou Microsoft Office Communications Server 2007 R2. No caso do Lync Server, um gateway PSTN deve ser utilizado. A Identidade do serviço é uma cadeia de caracteres no formato ServiceRole:FQDN, onde ServiceRole é o nome da função de serviço (PSTNGateway) e FQDN é o nome de domínio totalmente qualificado do pool ou o endereço IP do servidor. Por exemplo: PSTNGateway:redmondpool.litwareinc.com. As identidades de serviço podem ser recuperadas chamando o comando Get-CsService | Select-Object Identity.</p>
<p>Se forem realizadas alterações em uma rota de voz e a lista PstnGatewayList for deixada vazia, ou se a alteração feita remover todos os itens na lista, você receberá uma mensagem de aviso informando que os usuários não poderão realizar chamadas PSTN.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Uma lista de usos de PSTN (como Local ou Interurbano) que podem ser aplicados a esta rota de voz. O uso de PSTN deve ser um uso existente (os usos da PSTN podem ser recuperados chamando o cmdlet <strong>Get-CsPstnUsage</strong>).</p>
<p>Se forem realizadas alterações em uma rota de voz e a lista PstnGatewayList for deixada vazia, ou se a alteração feita remover todos os itens na lista, você receberá uma mensagem de aviso informando que os usuários não poderão realizar chamadas PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><em>SuppressCallerId</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Determina se um ID de chamador será revelado em chamadas de saída. Se este parâmetro for definido como True, o ID do chamador será suprimido. No lugar do ID real, o valor do AlternateCallerId será exibido. Quando SuppressCallerId for definido como True, deverá ser fornecido o valor de AlternateCallerId.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route. O cmdlet **Set-CsVoiceRoute** aceita entrada por pipeline de objetos de rota de voz.

## Tipos de retorno

O cmdlet **Set-CsVoiceRoute** não retorna um valor ou objeto. Em vez disso, o cmdlet configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route.

## Consulte Também

#### Outros Recursos

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsService](get-csservice.md)

