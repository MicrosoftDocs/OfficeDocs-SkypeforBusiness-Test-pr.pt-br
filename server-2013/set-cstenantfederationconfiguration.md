---
title: Set-CsTenantFederationConfiguration
TOCTitle: Set-CsTenantFederationConfiguration
ms:assetid: e13c2f55-7a68-4174-a0da-5eec8c65f64c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994080(v=OCS.15)
ms:contentKeyID: 52057740
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantFederationConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Gerencia as definições de configuração da federação para seus locatários Microsoft Lync Online. Essas definições são usadas para determinar quais domínios (se houver) seus usuários têm permissão de comunicação.

O cmdlet **Set-CsTenantFederationConfiguration** pode ser usado apenas com Skype for Business Online.

## Sintaxe

    Set-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Force] [-Verbose] [-WhatIf] [-Confirm]Set-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Instance <PSObject>] [-Force] [-Verbose] [-WhatIf] [-Confirm]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 desativa a comunicação com os provedores públicos para o locatário com o ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354".

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowPublicUsers $False

Note que o parâmetro Tenant é opcional. Se você omitir esse parâmetro, Windows PowerShell irá inserir automaticamente o ID do locatário correto com base nas informações de sua conexão.

## Exemplo 2

O Exemplo 2 mostra como você pode desativar a comunicação do provedor público para todos os locatários em sua organização. Para tanto, o comando chama primeiro o cmdlet **Get-CsTenant** para retornar uma coleão de todos os locatários disponíveis. Essa coleção, então, é canalizada para o cmdlet **Select-Object**, que seleciona apenas a propriedade TenantId de cada item na coleção. Essa coleão de IDs do locatárioe é canalizada, então, para o cmdlet **ForEach-Object**. O cmdlet F**orEach-Object**, depois, obtém cada ID do locatárioe e executa o cmdlet **Set-CsTenantFederationConfiguration** nesse ID, definindo a propriedade AllowPublicUsers de cada locatário para Falso ($False).

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantId -AllowPublicUsers $False}

## Exemplo 3

No Exemplo 3, o domínio fabrikam.com é atribuído como o único domínio na lista de domínios bloqueados para o locatório com o ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354". Para tanto, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeDomainPattern** para criar um novo objeto do domínio para fabrikam.com. Esse objeto do domínio é armazenado em uma variável denominada $x.

O segundo comando no exemplo, então, usa o cmdlet **Set-CsTenantFederationConfiguration** para atualizar a lista de domínios bloqueados. Usar o método Substituir assegura que a lista existente de domínios bloqueados será substituída pela nova lista: uma lista que contém apenas o domínio fabrikam.com.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Replace=$x}

## Exemplo 4

Os comandos mostrados no Exemplo 4 removem fabrikam.com da lista de domínios bloqueados pelo locatário com o ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354". Assim, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeDomainPattern** para criar um objeto do domínio para fabrikam.com. O objeto do domínio resultante é, então, armazenado em uma variável denominada $x.

Então, o segundo comando no exemplo usa o cmdlet **Set-CsTenantFederationConfiguration** e o método Remover para remover fabrikam.com da lista de domínios bloqueados para o locatário especificado.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Remove=$x}

## Exemplo 5

Os comandos mostrados no Exemplo 5 adicionam o domínio fabrikam.com à lista de domínios bloqueados pelo locatário com o ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354". Para adicionar um novo domínio bloqueado, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeDomainPattern** para criar um objeto do domínio para fabrikam.com. Esse objeto é armazenado na variável denominada $x.

Após o objeto do domínio ter sido criado, o segundo comando usa o cmdlet **Set-CsTenantFederationConfiguration** e o método Adicionar para adicionar fabrikam.com a quaisquer domínios já na lista de domínios bloqueados.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Add=$x}

## Exemplo 6

O Exemplo 6 mostra como você pode remover todos os domínios atribuídos à lista de domínios bloqueados para determinado locatário. Assim, apenas inclua o parâmetro BlockedDomains e defina o valor do parâmetro para null ($Null). Quando o comando terminar, a lista de domínios bloqueados será limpa para o locatário com o ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354".

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $Null

## Descrição Detalhada

Federação é um serviço que permite aos usuários trocarem MI e informações de presença com os usuários de outros domínios. Com Lync Online, os administradores podem usar as definições de configuração da federação para controlar:

  -   
    Se os usuários podem ou não se comunicar com pessoas de outros domínios e se puderem, com quais domínos eles têm permissão para a comunicação.

  -   
    Se os usuários podem ou não se comunicar com pessoas que têm contas na MI pública e provedores de presença, como o Windows Live, AOL e Yahoo.

Os administradores podem usar o cmdlet **Set-CsTenantFederationConfiguration** para ativar e desativar a federação com outros domínios e a federação com os provedores públicos. E mais, esse cmdlet pode ser usado para indicar expressamente os domínios com os quais os usuários podem comunicar-se e/ou os domínios com os quais eles não têm permissão de comunicação. Porém, os administradores devem usar o cmdlet **Set-CsTenantPublicProvider** para inidicar a MI pública e os provedores de presença com os quais os usuários podem e não podem comunicar-se.

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
<td><p><em>AllowedDomains</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.IAllowedDomainsChoice</p></td>
<td><p>Os objetos do domínio (criados usando o cmdlet <strong>New-CsEdgeAllowList</strong> ou o cmdlet <strong>New-CsEdgeAllowAllKnownDomains</strong>) que representam os domínios com os quais os usuários têm permissão para comunicar-se, Se o cmdlet <strong>New-CsEdgeAllowAllKnownDomains</strong> for usado, então, os usários poderão comunicar-se com qualquer domínio que não aparece na lista de domínios bloqueados. Se o cmdlet <strong>New-CsEdgeAllowList</strong> for usado, então, os usuários poderão comunicar-se apenas com os domínios que foram adicionados à lista de domínios bloqueados.</p>
<p>Note que os valores de string não podem ser passados diretamente para o parâmetro AllowedDomains. Ao contrário, você deve criar uma referência do objeto usando o cmdlet <strong>New-CsEdgeAllowList</strong> ou o cmdlet <strong>New-CsEdgeAllowAllKnownDomains</strong> e usar a variável de referência do objeto como o valor do parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowFederatedUsers</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Quando definido para True (o valor padrão), os usuários terão uma permissão em potencial para se comunicarem com os usuários de outros domínios. Se essa propriedade for definida para False, então, os usuários não poderão comunicar-se com os usuários de outros domínios, independentemente dos valores atribuídos às propriedades AllowedDomains e BlockedDomains properties.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPublicUsers</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Quando definido para True (o valor padrão), os usuários terão uma permissão em potencial para se comunicarem com os usuários com contas na MI pública e provedores de presença, como o Windows Live, Yahoo e AOL. A coleção de provedores públicos com os quais os usuários podem comunica-ser é gerenciada usando o cmdlet Set-CsTenantPublicProvider.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockedDomains</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se a propriedade AllowedDomains foi definida para AllowAllKnownDomains, então, os usuários terão permissão de se comunicarem com os usuários de qualquer domínio, exceto os domínios que aparecem na lista de domínios bloqueados. Se a propriedade AllowedDomains não foi definida para AllowAllKnownDomains, então, a lista bloqueada será ignorada e os usuários poderão comunicar-se apenas com os domínios que foram adicionados expressamente à lista de domínios permitidos.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes de executar o comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não fatal que pode ocorrer ao executar o comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Especifica a coleção de definições da configuração da federação do locatário a ser modificada. Como cada locatário é limitado a uma única coleção global de definições da federação, não é necessário incluir esse paràmetro ao chamar o cmdlet <strong>Set-CsTenantFederationConfiguration</strong>. Se você escolher usar o parâmetro Identity, também terá que incluir o parâmetro Tenant. Por exemplo:</p>
<p>Set-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p></td>
</tr>
<tr class="odd">
<td><p><em>SharedSipAddressSpace</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Quando definido para True, indica que os usuários hospedados em Lync Online usam o mesmo domínio SIP dos usuários hospedados na versão local de Lync Server. O valor padrão é False, significando que os dois conjuntos de usuários dados têm domínios SIP diferentes.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>O identificador global exclusivo (GUID) da conta do locatário cujas definções da federação estão sendo modificadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você estiver usando uma sessão remota de Windows PowerShell e estiver conectado apenas a Skype for Business Online, não precisará incluir o parâmetro Tenant. Ao contrário, o ID do locatário será preenchido automaticamente para você com base nas informações de sua conexão. O paràmetro Tenant é basicamente para usar em uma implantação híbrida.</p></td>
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

O cmdlet **Set-CsTenantFederationConfiguration** aceita instâncias canalizadas do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings.

## Tipos de retorno

Nenhum. Ao contrário, o cmdlet **Set-CsTenantFederationConfiguration** modifica as instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings.

## Consulte Também

#### Outros Recursos

[Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

