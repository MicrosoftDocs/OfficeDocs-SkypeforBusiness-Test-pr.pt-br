---
title: New-CsClientVersionConfiguration
TOCTitle: New-CsClientVersionConfiguration
ms:assetid: e7aac850-9e29-4d18-8929-74a89e9355cd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399029(v=OCS.15)
ms:contentKeyID: 49308447
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientVersionConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria uma nova coleção especificada de configurações de versão de cliente. As configurações de versão de cliente determinam se o Lync Server verifica ou não o número de versão de cada aplicativo cliente que faz logon no sistema. Se a filtragem de versão de cliente estiver habilitada, a capacidade desse aplicativo cliente acessar o sistema será baseada nas configurações definidas na diretiva de versão de cliente apropriada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 cria uma nova coleção de definições de configuração de versão do cliente para o site de Redmond. Nesse comando, o parâmetro Enabled é definido como False, indicando que a filtragem do cliente está desabilitada no site de Redmond.

    New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False

## EXEMPLO 2

O Exemplo 2 mostra como você pode criar uma nova coleção de definições de configuração de versão do cliente na memória, modificar essa coleção e transformar essas configurações virtuais em uma coleção real de configurações aplicadas ao site de Redmond. Para isso, o primeiro comando utiliza o cmdlet **New-CsClientVersionConfiguration** e o parâmetro InMemory para criar uma nova coleção de definições apenas na memória, com a Identidade site:Redmond. Esta coleção é armazenada em uma variável denominada $x e existi apenas na memória: se você encerrar a sessão do Windows PowerShell ou excluir a variável $x, essas definições de configuração de versão do cliente desaparecerão e nunca serão aplicadas ao site de Redmond.

No comando 2, o valor da propriedade DefaultAction das definições virtuais é definido como Block. No comando 3, o cmdlet **Set-CsClientVersionConfiguration** é utilizado para transformar as definições virtuais em uma coleção real de definições de configuração de versão do cliente aplicada ao site de Redmond.

    $x = New-CsClientVersionConfiguration -Identity site:Redmond -InMemory
    $x.DefaultAction = "Block" 
    Set-CsClientVersionConfiguration -Instance $x

## Descrição detalhada

O Lync Server fornece aos administradores uma margem de manobra considerável na especificação do software cliente (e, igualmente importante, no número de versão do software) que os usuários podem utilizar para efetuar o registro no sistema. Por exemplo: não há razão técnica que exija dos usuários o registro no Lync Server utilizando o Lync; não há limitações técnicas que impeçam os usuários de efetuarem o logon utilizando o Microsoft Office Communicator 2007 R2.

No entanto, é possível que haja alguns motivos não-técnicos pelos quais você prefira que seus usuários não efetuem o logon usando o Office Communicator 2007 R2. Por exemplo: o Office Communicator 2007 R2 não oferece apoio a todos os recursos e capacidades encontradas no Lync. Consequentemente, os usuários que efetuarem o logon com o Office Communicator 2007 R2 terão experiência diferente da de usuários que efetuarem o logon utilizando o Lync. Isto pode criar dificuldades para os usuários e também para os funcionários da assistência técnica, que deverão fornecer suporte para alguns aplicativos cliente diferentes.

Se criar problemas para sua organização, é possível implementar um filtro de versão do cliente que especifique os aplicativos cliente que poderão ser utilizados para efetuar o registro no Lync Server. Ao se instalar o Lync Server, será instalado e habilitado um conjunto global de definições de configuração de versão cliente. Essas definições são utilizadas para determinar se a filtragem de versão do cliente está ou não habilitada.

Além das definições globais, o cmdlet **New-CsClientVersionConfiguration** permite criar as definições de configuração de versão do cliente no escopo de site. Quando as definições de configuração de versão do cliente forem aplicadas no escopo de site, elas terão precedência sobre as definições globais. Por exemplo: suponhamos que você tenha habilitado a filtragem de versão do cliente no escopo global e, em seguida, tenha criado uma coleção separada de definições para o site de Redmond, na qual a filtragem de versão do cliente esteja desabilitada. Nesse caso, a filtragem de versão do cliente será desabilitada para todos os usuários que possuírem contas no site de Redmond.

No entanto, observe que os usuários anônimos são afetados apenas pelas configurações globais. O motivo é que eles não são associados a um site.

Observe que a configuração de versão do cliente não é um recurso de segurança. A tecnologia consiste na emissão de relatórios próprios, por parte dos aplicativos cliente, e não tenta verificar a autenticidade de um aplicativo, nem a do número da versão que ele afirma ser.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsClientVersionConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientVersionConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Representa o identificador exclusivo a ser atribuído à nova coleção de definições de configuração de versão do cliente. Como só é possível criar novas coleções no escopo do site, a Identity sempre terá o prefixo &quot;site:&quot; seguido do nome do site; por exemplo &quot;site:Redmond&quot;. Observe que o comando anterior falhará se já existir uma coleção das definições com a Identidade site:Redmond.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultAction</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction</p></td>
<td><p>Indica a ação a ser tomada se um usuário tentar fazer o logon em um aplicativo cliente cujo número de versão não puder ser localizado na política de versão do cliente relevante. DefaultAction deve ser definido com um dos seguintes valores:</p>
<p>Permitir. O aplicativo cliente poderá fazer logon.</p>
<p>AllowWithUrl. O aplicativo cliente poderá fazer logon. Além disso, será exibida uma caixa de mensagem para o usuário que inclui o URL de uma página da Web na qual o usuário poderá baixar um aplicativo cliente aprovado. O URL dessa página deve ser especificado como o valor da propriedade DefaultUrl.</p>
<p>Bloquear. O aplicativo cliente não poderá fazer logon.</p>
<p>BlockWithUrl. O aplicativo cliente não poderá fazer logon. No entanto, a caixa de mensagem &quot;Acesso Negado&quot; exibida para o usuário incluirá o URL de uma página da Web na qual o usuário poderá baixar um aplicativo cliente aprovado. O URL dessa página deve ser especificado como o valor da propriedade DefaultUrl.</p>
<p>Essa propriedade será ignorada se a propriedade Enabled for definida como False. Quando a propriedade Enabled for definida como False, não ocorrerá qualquer tipo de filtragem de versão do cliente.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultURL</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o URL da página da web na qual os usuários poderão fazer download de um aplicativo cliente aprovado. Se for especificado e se DefaultAction for definido como BlockWithUrl, esse URL aparecerá na caixa de mensagem &quot;Acesso negado&quot; exibida sempre que um usuário tentar fazer o logon em um aplicativo cliente não suportado.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se a filtragem de versão do cliente está habilitada ou não. Se a propriedade Enabled for True, o servidor verificará o número de versão de cada aplicativo cliente que tentar fazer o logon. Em seguida, o servidor permitirá ou negará o acesso, com base na política de versão do cliente relevante. Se a propriedade Enabled for False, qualquer aplicativo cliente capaz de fazer o logon poderá fazê-lo.</p>
<p>O valor padrão é True.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
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

Nenhuma. O cmdlet **New-CsClientVersionConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

Cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

