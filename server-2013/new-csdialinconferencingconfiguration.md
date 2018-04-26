---
title: New-CsDialInConferencingConfiguration
TOCTitle: New-CsDialInConferencingConfiguration
ms:assetid: ac0b6e22-3883-4884-aa94-18f4029c7f1e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412816(v=OCS.15)
ms:contentKeyID: 49307784
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDialInConferencingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria uma nova coleção de definições de configuração de conferências discadas. Essas definições determinam como o Lync Server responde quando os usuários entram ou saem de uma conferência discada. Mais especificamente, são retornadas informações sobre a exigência feita aos participantes de registrarem ou não o seu nome ao entrar em uma conferência e como (ou se) o sistema anunciará que alguém entrou na chamada ou a abandonou. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsDialInConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableNameRecording <$true | $false>] [-EntryExitAnnouncementsEnabledByDefault <$true | $false>] [-EntryExitAnnouncementsType <UseNames | ToneOnly>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 cria uma nova coleção de definições de configuração de conferência discada, que são aplicadas ao site de Redmond. Além disso, o parâmetro opcional EnableNameRecording é incluído para definir a propriedade EnableNameRecording como sendo False.

    New-CSDialInConferencingConfiguration -Identity site:Redmond -EnableNameRecording $False

## EXEMPLO 2

No Exemplo 2, o parâmetro InMemory é utilizado para criar uma nova coleção de definições de configuração de conferências discadas que, inicialmente, existirá somente na memória. Para isso, o exemplo primeiro chama o cmdlet **New-CSDialInConferencingConfiguration** e o parâmetro InMemory, para criar uma coleção "virtual" de definições que é armazenada na variável $x (observe que a esta coleção receberá a identidade site:Redmond). Após a criação da coleção virtual, a linha 2 será utilizada para modificar o valor da propriedade EnableNameRecording. Finalmente, a linha 3 do exemplo chamará o cmdlet **Set-CSDialInConferencingConfiguration** para transformar as definições de configuração virtual armazenadas em $x na coleção de definições aplicadas ao site de Redmond.

    $x = New-CSDialInConferencingConfiguration -Identity site:Redmond -InMemory
    $x.EnableNameRecording = $False
    Set-CSDialInConferencingConfiguration -Instance $x

## Descrição detalhada

Quando os usuários ingressam em (ou deixam) uma conferência discada, o Lync Server pode responder de formas diferentes. Por exemplo: os participantes podem ser solicitados a registrar o seu nome, para que possam entrar na conferência. Da mesma forma, os administradores podem decidir se querem que o Lync Server anuncie que os participantes discados deixaram ou ingressaram em uma conferência.

Esses "comportamentos de entrada" de conferência são gerenciados utilizando definições de configuração de conferência, que podem ser configuradas no escopo global ou de site (as definições configuradas no escopo do site têm precedência sobre as definições configuradas no escopo global). Ao instalar o Lync Server pela primeira vez, as únicas definições de configuração de conferências discadas serão as do escopo global. Entretanto, é possível criar novas definições no escopo de site utilizando o cmdlet **New-CSDialInConferencingConfiguration**.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsDialInConferencingConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDialInConferencingConfiguration"}

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
<td><p>XdsIdentity</p></td>
<td><p>Indica a identidade das definições de configuração de conferência discada a serem criadas. Como essas definições podem ser criadas apenas no escopo de site, utilize uma sintaxe similar a essa, com o prefixo &quot;site:&quot; seguidos pelo nome do site: -Identity site:Redmond.</p>
<p>Observe que só pode haver um conjunto de definições de configuração de conferência discada por site. O comando no exemplo falhará se já existir uma coleção de definições com a identidade site:Redmond.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableNameRecording</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Determina se os usuários serão solicitados ou não a registrar os seus nomes antes de entrar na conferência. Defina como True ($True), para solicitar o registro de nome; defina como False ($False), para ignorar o registro de nome. O valor padrão é True.</p></td>
</tr>
<tr class="even">
<td><p><em>EntryExitAnnouncementsEnabledByDefault</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Se este parâmetro for definido como True, anúncios serão emitidos a cada vez que um participante entrar ou deixar uma conferência. Se definido como False (o valor padrão), não serão emitidos anúncios de entrada ou saída.</p></td>
</tr>
<tr class="odd">
<td><p><em>EntryExitAnnouncementsType</em></p></td>
<td><p>Opcional</p></td>
<td><p>EntryExitAnnouncementsType</p></td>
<td><p>Indica a ação tomada pelo sistema a qualquer momento em que um participante entrar ou deixar uma conferência. Os valores válidos são:</p>
<p>UseNames. O nome da pessoa será anunciado toda vez que entrar ou deixar uma conferência (por exemplo: &quot;Ken Myer está deixando a conferência&quot;).</p>
<p>ToneOnly. Um tom será emitido a cada vez que um participante entrar ou deixar uma conferência.</p>
<p>O valor padrão é UseNames. Observe que os comunicados serão emitidos apenas se a propriedade EntryExitAnnouncementsEnabledByDefault for definida como True.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **New-CsDialInConferencingConfiguration** não aceita entrada por pipeline.

## Tipos de retorno

Cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

