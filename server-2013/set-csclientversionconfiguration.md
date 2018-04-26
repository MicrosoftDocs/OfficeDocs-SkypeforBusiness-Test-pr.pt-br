---
title: Set-CsClientVersionConfiguration
TOCTitle: Set-CsClientVersionConfiguration
ms:assetid: 7cd2e86f-2d31-4db2-9d0f-f1418fd4aba2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398623(v=OCS.15)
ms:contentKeyID: 49307238
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientVersionConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica a coleção especificada de configurações de versão de cliente. As configurações de versão de cliente determinam se o Lync Server verifica ou não o número de versão de cada aplicativo cliente que faz logon no sistema. Se a filtragem de versão de cliente estiver habilitada, a capacidade desse aplicativo cliente acessar o sistema será baseada nas configurações definidas na diretiva de versão de cliente apropriada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientVersionConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

No Exemplo 1, o cmdlet **Set-CsClientVersionConfiguration** é usado para modificar a coleção de configurações com Identidade "site:Redmond". Nesse caso, o parâmetro Enabled é definido como False para desabilitar as configurações de versão de cliente.

    Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False

## EXEMPLO 2

No Exemplo 2, a propriedade DefaultUrl é modificada para todas as configurações de versão de cliente em uso no momento na organização. Para fazer isso, o comando chama primeiro o cmdlet **Get-CsClientVersionConfiguration** sem parâmetros adicionais para retornar todas as configurações de versão de cliente. Essas informações são canalizadas para o cmdlet **Set-CsClientVersionConfiguration**, que define o valor de DefaultUrl de todas as coleções de configurações como https://litwareinc.com/csclients.

    Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"

## EXEMPLO 3

No Exemplo 3, são feitas modificações em todas as configurações de versão de cliente nas quais DefaultAction esteja definido como Block. Para realizar essa tarefa, o comando primeiro usa o cmdlet **Get-CsClientVersionConfiguration** para retornar todas as configurações de versão de cliente em uso no momento. Essas informações são canalizadas para o cmdlet **Where-Object**, que seleciona somente os itens nos quais a propriedade DefaultAction seja igual a "Block". Essa coleção filtrada é então canalizada para o cmdlet **Set-CsClientVersionConfiguration**, que faz duas coisas com cada item na coleção: 1) define DefaultAction como BlockWithUrl e 2) define DefaultUrl como https://litwareinc.com/csclients.

    Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block"} | Set-CsClientVersionConfiguration -DefaultAction "BlockWithUrl" -DefaultURL "https://litwareinc.com/csclients"

## Descrição detalhada

O Lync Server oferece aos administradores uma liberdade considerável para especificar o software de cliente (e igualmente importante, o número de versão desse software) que os usuários podem usar para fazer logon no sistema. Por exemplo, não há razão técnica que exija que os usuários façam logon no Lync Server com o Lync; do ponto de vista técnico, nada impede que os usuários façam logon usando o Microsoft Office Communicator 2007 R2.

Por outro lado, pode haver algumas razões não técnicas para que você prefira que seus usuários não façam logon usando o Office Communicator 2007 R2. Por exemplo, o Office Communicator 2007 R2 não tem suporte a todos os recursos e capacidades encontrados no Lync; com isso, os usuários que fizerem logon com o Office Communicator 2007 R2 terão uma experiência diferente dos que fizerem logon com o Lync. Isso pode criar dificuldades para seus usuários; também pode criar dificuldades para a equipe de suporte técnico, que precisa oferecer suporte a vários aplicativos cliente diferentes.

Se isso representar um problema para sua organização, é possível empregar a filtragem de versão de cliente para especificar quais aplicativos cliente podem ser usados para fazer logon no Lync Server. Quando o Lync Server é instalado, um conjunto global de configurações de versão de cliente é instalado e habilitado. Essas configurações são usadas para determinar se a filtragem de versão de cliente deve ou não ser habilitada. Além das configurações globais, as configurações de versão de cliente também podem ser aplicadas em escopo de site; nessas instâncias, as configurações de site terão prioridade sobre as configurações globais.

O cmdlet **Set-CsClientVersionConfiguration** permite a modificação de uma coleção existente de configurações de versão de cliente.

Observe que a configuração de versão de cliente não é um recurso de segurança. A tecnologia depende do autorrelatório de aplicativos cliente, e não tenta verificar se um aplicativo é de fato aquele que diz ser, nem se o número de versão desse aplicativo está correto.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsClientVersionConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientVersionConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultAction</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction</p></td>
<td><p>Indica a ação a ser tomada caso um usuário tente fazer logon a partir de um aplicativo cliente cujo número de versão não conste da diretiva de versão de cliente apropriada. DefaultAction deve ser definido para um dos valores seguintes:</p>
<p>Allow. O aplicativo cliente terá permissão para fazer logon.</p>
<p>AllowWithUrl. O aplicativo cliente terá permissão para fazer logon. Além disso, uma caixa de mensagem será exibida ao usuário, incluindo a URL de uma página da Web na qual o usuário poderá baixar um aplicativo cliente aprovado. A URL dessa página deve ser especificada como o valor da propriedade DefaultUrl.</p>
<p>Block. O aplicativo cliente não poderá fazer logon.</p>
<p>BlockWithUrl. O aplicativo cliente não poderá fazer logon. No entanto, a caixa de mensagem &quot;Acesso negado&quot; exibida ao usuário incluirá a URL da página da Web na qual o usuário pode baixar um aplicativo cliente aprovado. A URL dessa página deve ser especificada como o valor da propriedade DefaultUrl.</p>
<p>Essa propriedade será ignorada se a propriedade Enabled estiver definida como False. Quando a propriedade Enabled estiver definida como False, nenhum tipo de filtragem de versão será realizado.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultURL</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a URL da página da Web na qual os usuários podem baixar um aplicativo cliente aprovado. Se for especificado e se DefaultAction estiver definido como BlockWithURL, a URL aparecerá na caixa de mensagem &quot;Acesso negado&quot; sempre que um usuário tentar fazer logon a partir de um aplicativo cliente não suportado.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se a filtragem de versão de cliente está habilitada ou desabilitada. Se a propriedade Enabled for True, o servidor irá verificar o número de versão de cada aplicativo cliente que tentar fazer logon; o servidor então permitirá ou não o acesso com base na diretiva de versão de cliente apropriada. Se a propriedade Enabled for False, qualquer aplicativo cliente capaz de fazer logon terá permissão para fazê-lo.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Representa o identificador exclusivo das configurações de versão de cliente a serem modificadas. Para modificar as configurações globais, use uma sintaxe como esta: -Identity global. Para modificar configurações atribuídas em escopo de site, use uma sintaxe semelhante a esta: &quot;site:Redmond&quot;.</p>
<p>Se o parâmetro não for incluído, o cmdlet <strong>Set-CsClientVersionConfiguration</strong> irá definir automaticamente as configurações globais.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>Objetos ClientVersionPolicy</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration. O cmdlet **Set-CsClientVersionConfiguration** aceita instâncias em pipeline do objeto de configuração de versão de cliente.

## Tipos de retorno

O cmdlet **Set-CsClientVersionConfiguration** não retorna um valor ou objeto. Em vez disso, o cmdlet configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)

