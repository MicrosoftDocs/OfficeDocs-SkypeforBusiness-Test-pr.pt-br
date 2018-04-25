---
title: Remove-CsPrivacyConfiguration
TOCTitle: Remove-CsPrivacyConfiguration
ms:assetid: 32052c51-953d-4278-9425-306245d297ed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425821(v=OCS.15)
ms:contentKeyID: 49306312
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPrivacyConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Remove uma coleção existente de definições de configuração de privacidade. As definições de configuração de privacidade ajudam a determinar quanta informação os usuários tornam disponível a outros usuários. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsPrivacyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 retorna as definições de configuração de privacidade atribuídas ao site de Redmond. Quando essas definições forem excluídas, os usuários no site de Redmond herdarão automaticamente as definições globais de configuração de privacidade.

    Remove-CsPrivacyConfiguration -Identity site:Redmond

## EXEMPLO 2

No Exemplo 2, todas as definições de configuração de privacidade atribuídas ao escopo de site serão excluídas. Para fazer isso, o comando chama primeiramente o cmdlet **Get-CsPrivacyConfiguration**, juntamente com o parâmetro -Filter. O valor de filtro "site:\*" garante que serão retornadas apenas as definições cuja identidade for iniciada pelos caracteres "site". Esta coleção filtrada será então canalizada para o cmdlet **Remove-CsPrivacyConfiguration**, que removerá cada item na coleção.

    Get-CsPrivacyConfiguration -Filter "site:*" | Remove-CsPrivacyConfiguration

## EXEMPLO 3

O comando exibido no Exemplo 3 exclui todas as definições de configuração de privacidade nas quais o modo privacidade tiver sido desabilitado. Para realizar essa tarefa, o comando chama primeiramente o cmdlet **Get-CsPrivacyConfiguration** sem quaisquer parâmetros; isto retorna uma coleção de todas as definições de configuração de privacidade em uso na organização. Esta coleção será canalizada para o cmdlet **Where-Object**, que selecionará apenas as definições nas quais a propriedade EnablePrivacyMode for igual a False. Em seguida, essa coleção filtrada será redirecionada para o cmdlet **Remove-CsPrivacyConfiguration**, que excluirá cada item da coleção.

    Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Remove-CsPrivacyConfiguration

## Descrição detalhada

O Lync Server fornece aos usuários a oportunidade de compartilhar uma gama de informações de presença com outras pessoas: elas podem publicar uma fotografia de si mesmas, fornecer informações de localização detalhada, disponibilizar automaticamente informações de presença a todas as pessoas da organização (em vez de disponibilizá-las apenas a pessoas de sua lista de Contatos).

Alguns usuários acolherão a oportunidade de disponibilizar estas informações a seus colegas; é possível que outros usuários sejam mais relutantes em compartilhar esses dados. (por exemplo, muitas pessoas poderão hesitar em incluir suas fotos nos seus dados de presença.) Como regra geral, os usuários têm controle sobre as informações que eles compartilharão (ou não). Por exemplo, os usuários podem marcar ou desmarcar uma caixa de seleção, controlando se as suas informações de local serão compartilhadas ou não com outras pessoas. Além disso, os cmdlets de configuração de privacidade permitem aos administradores gerenciar as definições de privacidade dos seus usuários. Em alguns casos, os administradores podem habilitar ou desabilitar as definições. Por exemplo, se a propriedade AutoInitiateContacts for definida como True, os membros da equipe serão adicionados automaticamente à lista de contatos de cada usuário; se ela for definida como False, os membros da equipe não serão adicionados automaticamente à lista de contatos de cada usuário.

Em outros casos, os administradores podem configurar os valores padrão no Lync Server, continuando a permitir que os usuários alterem esses valores. Por exemplo, por padrão, publicam-se os dados de localização dos usuários, apesar de eles terem o direito de interromper a sua publicação. Ao definir a propriedade PublishLocationDataByDefault como sendo False, os administradores podem alterar esse comportamento: neste caso, os dados de localização não serão publicados por padrão, apesar dos usuários ainda terem o direito de publicar esses dados, se assim optarem.

As definições de configuração de privacidade podem ser aplicadas no escopo global, escopo do site e no escopo de serviço (embora apenas para o serviço Servidor de Usuários). O cmdlet **Remove-CsPrivacyConfiguration** fornece uma maneira de excluir definições que tiverem sido configuradas no escopo do site ou serviço; por exemplo, se executar o cmdlet concomitantemente às definições configuradas no escopo de site, elas serão excluídas e as definições de privacidade dos usuários naquele site serão governadas pela coleção global. O cmdlet **Remove-CsPrivacyConfiguration** também pode ser executado concomitantemente à coleção global; entretanto, esta coleção não será excluída. Em vez disso, todas as propriedades desta coleção serão redefinidas com seus valores padrão. Por exemplo, suponha que a propriedade EnablePrivacyMode tenha sido alterada previamente como sendo True. Se a coleção global for "excluída", EnablePrivacyMode será revertida a seu valor padrão False.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsPrivacyConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPrivacyConfiguration"}

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
<td><p>Identificador único das definições de configuração de privacidade a serem removidas. Para remover definições configuradas no escopo do site, utilize uma sintaxe similar a esta: -Identity site:Redmond. Para remover as definições no nível do serviço, utilize uma sintaxe como esta: -Identity service:UserServer:atl-cs-001.litwareinc.com.</p>
<p>O cmdlet <strong>Remove-CsPrivacyConfiguration</strong> pode também ser executada concomitantemente à coleção global de definições. Neste caso, entretanto, as definições globais não serão excluídas. Em vez disso, todas as propriedades desta coleção serão redefinidas com seus valores padrão.</p></td>
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
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>GUID da conta inquilino do Skype for Business Online na qual as definições de configuração de privacidade estão sendo excluídas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar a ID inquilino de cada um dos seus inquilinos executando esse comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration. O cmdlet **Remove-CsPrivacyConfiguration** aceita a entrada canalizada do objeto de configuração de privacidade.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Remove-CsPrivacyConfiguration** exclui instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

