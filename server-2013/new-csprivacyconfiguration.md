---
title: New-CsPrivacyConfiguration
TOCTitle: New-CsPrivacyConfiguration
ms:assetid: 9b7f02d7-93a5-4fa5-a74c-3fe4baf8bbfc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398807(v=OCS.15)
ms:contentKeyID: 49307585
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPrivacyConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria um novo conjunto de definições de configuração de privacidade. As definições de configuração de privacidade ajudam a determinar quanta informação os usuários disponibilizam para outros usuários. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsPrivacyConfiguration -Identity <XdsIdentity> [-AutoInitiateContacts <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayPublishedPhotoDefault <$true | $false>] [-EnablePrivacyMode <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-PublishLocationDataDefault <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 cria um novo conjunto de definições de configuração de privacidade que serão aplicadas ao site Redmond (-Identity site:Redmond). As novas configurações habilitam o modo de privacidade; para isso, o parâmetro EnablePrivacyMode é adicionado com o valor de parâmetro True. Observe que o comando falhará se o site Redmond já tiver um conjunto de configurações de privacidade.

    New-CsPrivacyConfiguration -Identity site:Redmond -EnablePrivacyMode $True

## EXEMPLO 2

O Exemplo 2 demonstra como usar o parâmetro InMemory para criar um novo conjunto de configurações de privacidade que inicialmente existe apenas na memória. Para isso, o cmdlet **New-CsPrivacyConfiguration** é chamado com os parâmetros Identity e InMemory; o objeto resultante é armazenado em uma variável chamada $x. Nesse momento, as configurações de privacidade existem somente em memória; se o cmdlet **Get-CsPrivacyConfiguration** for executado, não será exibida uma listagem para o site:Redmond.

No segundo comando, o valor da propriedade EnablePrivacyMode é definido como True. Finalmente, o terceiro comando usa o cmdlet **Set-CsPrivacyConfiguration** para transformar o conjunto virtual de configurações de privacidade em um conjunto real de configurações aplicadas ao site Redmond. Chamar o cmdlet **Set-CsPrivacyConfiguration** é crítico: se não for executado, as novas configurações de privacidade não serão aplicadas ao site Redmond e desaparecerão assim que sua sessão do Windows PowerShell for encerrada ou a variável $x for excluída.

    $x = New-CsPrivacyConfiguration -Identity site:Redmond -InMemory
    $x.EnablePrivacyMode = $True
    Set-CsPrivacyConfiguration -Instance $x

## Descrição detalhada

O Lync Server oferece aos usuários a oportunidade de compartilhar várias informações de presença com terceiros: eles podem publicar fotos de si mesmos; fornecer informações detalhadas sobre sua localização; disponibilizar automaticamente suas informações de presença a todos na organização (em vez de disponibilizá-las apenas para as pessoas na lista de Contatos).

Alguns usuários vão apreciar a oportunidade de disponibilizar essas informações a seus colegas; outros podem ficar mais relutantes em compartilhar esses dados (por exemplo, muitas pessoas podem hesitar em incluir suas fotos nos dados de presença). Como regra geral, os usuários controlam as informações que serão compartilhadas (ou não); por exemplo, os usuários podem marcar ou desmarcar uma caixa de seleção para controlar se suas informações de localização serão ou não compartilhadas com terceiros. Além disso, os cmdlets de configuração de privacidade permitem que os administradores gerenciem as configurações de privacidade dos usuários. Em alguns casos, os administradores podem habilitar ou desabilitar configurações; por exemplo, se a propriedade AutoInitiateContacts for definida como True, os integrantes da equipe serão adicionados automaticamente à lista de Contatos de cada usuário; se for definida como False, os integrantes da equipe não serão incluídos automaticamente na lista de Contatos de cada usuário.

Em outros casos, os administradores podem configurar os valores padrão no Lync e ainda permitir que os usuários modifiquem esses valores. Por exemplo, por padrão, os dados de local de usuários são publicados, mas os usuários podem impedir sua publicação. Os administradores podem alterar esse comportamento definindo a propriedade PublishLocationDataByDefault como False: nesse caso, os dados de local não serão publicados por padrão, mas os usuários terão o direito de publicar esses dados se quiserem.

As configurações de privacidade do telefone podem ser aplicadas em escopo global, em escopo de site e em escopo de serviço (embora apenas para o serviço User Server). O cmdlet **New-CsPrivacyConfiguration** permite criar novas configurações de privacidade a serem aplicadas a um site ou serviço (não é possível criar novos conjuntos em escopo global). Observe que cada site ou serviço individual só pode ter, no máximo, um único conjunto de configurações de privacidade: o comando falhará se você tentar criar um novo conjunto para o site Redmond e esse site já tiver um conjunto de configurações de privacidade.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **New-CsPrivacyConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPrivacyConfiguration"}

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
<td><p>Identificador único para as configurações de privacidade a serem criadas. Para criar um novo conjunto de configurações no escopo de site, use uma sintaxe semelhante a esta: -Identity site:Redmond. Para criar novas configurações no escopo de serviço, use uma sintaxe como esta: -Identity service:UserServer:atl-cs-001.litwareinc.com. As configurações de privacidade só podem ser criadas para o serviço User Server. Um erro ocorrerá se você tentar aplicar essas configurações a outro serviço.</p>
<p>Observe que seu comando falhará se já existirem configurações de privacidade para o site ou serviço especificado. Da mesma forma, o comando falhará se você tentar criar um novo conjunto de configurações globais.</p></td>
</tr>
<tr class="even">
<td><p><em>AutoInitiateContacts</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se for True, o Lync incluirá automaticamente seu gerente e os relatórios diretos em sua lista de Contatos. O valor padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayPublishedPhotoDefault</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se for True, a foto do usuário será publicada automaticamente no Lync. Se for False, a foto do usuário só estará disponível se ele selecionar explicitamente a opção Permitir que outros vejam minha foto. O valor padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePrivacyMode</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se for True, oferece aos usuários a oportunidade de habilitar o modo de privacidade avançado. No modo de privacidade avançado, apenas pessoas na sua lista de Contatos poderão visualizar suas informações de presença. Se for False, suas informações de presença estarão disponíveis para qualquer pessoa na organização. O valor padrão é False.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>PublishLocationDataDefault</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se for True, os dados de local serão publicados automaticamente no Lync. Se for False, os dados de local só estarão disponíveis se o usuário selecionar explicitamente a opção Mostrar minha localização para meus contatos. O valor padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta de locatário do Skype for Business Online para a qual as novas configurações de privacidade estão sendo criadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar a ID de cada um de seus locatários executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

Nenhuma. O cmdlet **New-CsPrivacyConfiguration** não aceita entrada por pipeline.

## Tipos de retorno

O cmdlet **New-CsPrivacyConfiguration** cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

