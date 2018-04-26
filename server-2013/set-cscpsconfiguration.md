---
title: Set-CsCpsConfiguration
TOCTitle: Set-CsCpsConfiguration
ms:assetid: 9c2c0ad1-12f8-47b6-a7ec-60d91c9685bf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412721(v=OCS.15)
ms:contentKeyID: 49307591
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCpsConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma coleção existente de configurações do serviço de Estacionamento de Chamadas. O estacionamento de chamadas é um serviço que permite a um usuário "estacionar" uma chamada telefônica de entrada. O estacionamento de uma chamada a transfere para um número em um intervalo especificado, ou órbita, e imediatamente a coloca em espera. Alguém (não somente a pessoa que originalmente atendeu à chamada) pode retomar a conversa de qualquer telefone simplesmente inserindo o número correto. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCpsConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CallPickupTimeoutThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnableMusicOnHold <$true | $false>] [-Force <SwitchParameter>] [-MaxCallPickupAttempts <Int32>] [-OnTimeoutURI <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 modifica a configuração do serviço de Estacionamento de Chamadas com a Identidade site:Redmond1 definindo o número máximo de vezes em que uma chamada estacionada tocará de volta ao telefone de atendimento como 2. Isto é feito pela inclusão do parâmetro MaxCallPickupAttempts, com valor de parâmetro igual a 2.

    Set-CsCpsConfiguration -Identity site:Redmond1 -MaxCallPickupAttempts 2

## EXEMPLO 2

O Exemplo 2 é uma variação do comando exibido no Exemplo 1; mas neste caso, em vez de definirmos apenas uma configuração, definimos todas as configurações do serviço de Estacionamento de Chamadas com o valor de propriedade MaxCallPickupAttempts igual a 2. Para isso, o cmdlet **Get-CsCpsConfiguration** é usado para recuperar uma coleção de todas as configurações do serviço de Estacionamento de Chamadas em uso na organização. Esta coleção é então direcionada para o cmdlet **Set-CsCpsConfiguration**, que toma cada item individual na coleção e define o valor da propriedade MaxCallPickupAttempts como 2.

    Get-CsCpsConfiguration | Set-CsCpsConfiguration -MaxCallPickupAttempts 2

## EXEMPLO 3

Este exemplo modifica a configuração do estacionamento de chamadas para o site Redmond1, definindo o tempo que se passará antes que uma chamada estacionada toque de volta (contido na propriedade CallPickupTimeoutThreshold) como 45 segundos.

    Set-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:00:45

## Descrição detalhada

Este cmdlet é usado para modificar uma configuração existente do serviço de Estacionamento de Chamadas. Uma configuração do serviço de Estacionamento de Chamadas especifica o que acontece a uma chamada uma vez que seja estacionada. Por exemplo, se uma chamada estacionada não for respondida depois de um período de tempo, pode ser automaticamente expedida a outra pessoa, como um administrador, ou a um Grupo de Resposta. As chamadas podem ser configuradas para tocar depois de certo período de tempo para assegurar que a chamada não seja esquecida. Além disso, o serviço de Estacionamento de Chamadas pode ser configurado para tocar música de espera para o chamador enquanto a chamada estiver estacionada.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsCpsConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCpsConfiguration"}

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
<td><p><em>CallPickupTimeoutThreshold</em></p></td>
<td><p>Opcional</p></td>
<td><p>TimeSpan</p></td>
<td><p>A quantidade de tempo que passará após uma chamada ser estacionada, antes que toque de volta ao telefone pelo qual a chamada foi atendida.</p>
<p>Deve ser inserido no formato hh:mm:ss (hh = horas, mm = minutos, ss = segundos)</p>
<p>Valor Mínimo: 10 segundos (00:00:10); Valor Máximo: 10 minutos (00:10:00)</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMusicOnHold</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Determina se a música é reproduzida para o chamador enquanto a chamada é estacionada.</p>
<p>O Lync Server é enviado com um arquivo de Música de Espera padrão. É possível modificar este arquivo (modificando a música que o chamador ouve enquanto estacionado) com o cmdlet <strong>Set-CsCallParkServiceMusicOnHoldFile</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime eventuais avisos de confirmação que seriam exibidos para a realização de alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador único da configuração que você deseja modificar. A Identidade especifica o escopo no qual a configuração é aplicada, Global ou um local específico (no local de formato: &lt;nomedolocal&gt;, como local:Redmond).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>CallParkServiceSettings</p></td>
<td><p>Uma referência de objeto para um objeto de configuração do serviço de Estacionamento de Chamadas, do tipo Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings. Este objeto pode ser recuperado chamando o cmdlet <strong>Get-CsCpsConfiguration</strong>. O objeto então pode ser modificado e as modificações salvas passando o objeto de volta para o cmdlet <strong>Set-CsCpsConfiguration</strong> neste parâmetro.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCallPickupAttempts</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>O número de vezes que uma chamada estacionada tocará de volta ao telefone de atendimento antes de abandonar e encaminhar a chamada ao URI (Uniform Resource Identifier). O URI de fallback é estabelecido com o parâmetro OnTimeoutURI.</p>
<p>Valor Mínimo: 1; Valor Máximo: 10</p></td>
</tr>
<tr class="even">
<td><p><em>OnTimeoutURI</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>O endereço SIP do usuário ou Grupo de Resposta ao qual as chamadas estacionadas sem resposta serão roteadas. A chamada estacionada será roteada depois do número de chamadas de retorno definidas com o parâmetro MaxCallPickupAttempts. Se o parâmetro for definido como Null, OnTimeoutURI será ignorado e a chamada estacionada será desconectada após tentativas mal-sucedidas de chamadas de retorno.</p>
<p>Os valores devem ser URIs de SIP, começando com a cadeia de caracteres sip:. Por exemplo, sip:rgs1@litwareinc.com.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings. Aceita entrada por pipeline de objetos do serviço de Estacionamento de Chamadas.

## Tipos de retorno

Modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

## Consulte Também

#### Outros Recursos

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

