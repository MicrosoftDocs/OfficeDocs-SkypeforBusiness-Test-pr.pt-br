---
title: Remove-CsConferencingConfiguration
TOCTitle: Remove-CsConferencingConfiguration
ms:assetid: a3dff4b0-100b-46fa-9078-d3b0d4914d87
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412767(v=OCS.15)
ms:contentKeyID: 49307672
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConferencingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Remove o conjunto especificado de definições de configuração de conferências. As definições de conferência determinam aspectos como o tamanho máximo permitido do conteúdo e dos folhetos da conferência, o período de cortesia do conteúdo e as URLs dos downloads internos e externos do cliente suportado. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 exclui as definições de configuração de conferência aplicadas ao site de Redmond. Quando configurações de site como essas são excluídas, os usuários no site herdarão automaticamente as definições encontradas nas definições de configuração de conferência global.

    Remove-CsConferencingConfiguration -Identity site:Redmond

## EXEMPLO 2

No Exemplo 2, o comando exclui todas as definições de configuração de conferência aplicadas ao escopo do site. Para isso, o comando primeiro chama o cmdlet **Get-CsConferencingConfiguration** com o parâmetro Filter; o valor de filtro "site:" garante que apenas as definições que possuem uma Identidade que comece com os caracteres "site:" sejam retornadas. Esse conjunto filtrado é então direcionado para o cmdlet **Remove-CsConferencingConfiguration**, que exclui cada item no conjunto.

    Get-CsConferencingConfiguration -Filter site:* | Remove-CsConferencingConfiguration

## EXEMPLO 3

O Exemplo 3 exclui todas as definições de configuração de conferência em que a organização não esteja definida como Litwareinc. Para isso, primeiro o comando chama o cmdlet **Get-CsConferencingConfiguration** sem nenhum parâmetro, que retorna um conjunto de todas as definições de configuração de conferências usadas na organização. Esse conjunto é então direcionado para o cmdlet **Where-Object**, que seleciona apenas as definições cuja propriedade Organization seja diferente de Litwareinc. Finalmente, o conjunto filtrado é direcionado para o cmdlet **Remove-CsConferencingConfiguration**, que exclui todas as definições no conjunto.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Litwareinc"} | Remove-CsConferencingConfiguration

## Descrição detalhada

Nas conferências, o gerenciamento e a administração são divididos entre dois conjuntos de cmdlets. Se você quiser gerenciar as ações dos usuários (por exemplo, se podem convidar participantes anônimos para entrar em uma conferência, oferecer o compartilhamento de aplicativos em uma conferência, transferir arquivos em uma conferência), será necessário usar os cmdlets **CsConferencingPolicy**.

Além das atividades do usuário, os administradores precisam gerenciar o Serviço de Webconferência. Por exemplo: os administradores precisam realizar ações como especificar o valor máximo de armazenamento de conteúdo alocado para uma única conferência e especificar o período de cortesia antes que o conteúdo da conferência seja automaticamente excluído. Também é necessário permitir que eles especifiquem as portas usadas para atividades como compartilhamento de aplicativos e transferência de arquivos.

Estas últimas atividades podem ser gerenciadas usando os cmdlets **CsConferencingConfiguration**. Estes cmdlets permitem gerenciar os próprios servidores. Os cmdlets **CsConferencingConfiguration** (que podem ser aplicados aos escopos globais, de site e de serviço) não são usados para especificar se um usuário pode ou não compartilhar aplicativos durante uma conferência. No entanto, se o compartilhamento de aplicativos for permitido, esses cmdlets permitem indicar quais portas deverão ser usadas para essa atividade. Da mesma forma, os cmdlets permitem especificar os limites de armazenamento e os períodos de validade, bem como os indicadores para URLs internas e externas, nas quais os usuários podem obter ajuda e recursos relacionados às conferências.

O cmdlet **Remove-CsConferencingConfiguration** permite excluir qualquer conjunto personalizado de definições de configuração de conferências criado para uso na organização. Ao excluir um conjunto de definições, qualquer servidor previamente afetado por essas definições ficará sob a jurisdição do próximo conjunto na hierarquia (serviço – site – escopo). Se as definições excluídas tiverem sido aplicadas ao escopo do serviço, os servidores serão gerenciados pelas definições de site. Se não houver definições no escopo do site, os servidores serão gerenciados pelas definições globais. Da mesma forma, se as definições no escopo do site forem excluídas, os servidores anteriormente gerenciados pelas definições de site serão gerenciados pelas definições globais.

Observe que também é possível executar o cmdlet **Remove-CsConferencingConfiguration** concomitantemente às definições globais. Neste caso, entretanto, as definições globais não serão removidas porque o Lync Server não permite excluí-las. Em vez disso, todas as propriedades no conjunto global reassumirão os seus valores padrão. Por exemplo, se você tiver alterado anteriormente o valor máximo de armazenamento de conteúdo para 200 megabytes, esta propriedade será revertida para o valor padrão de 100 megabytes.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsConferencingConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferencingConfiguration"}

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
<td><p>Identificador exclusivo do conjunto de definições de configuração de conferência a ser removido. Para remover as definições configuradas no escopo do site, use uma sintaxe semelhante a esta: -Identity &quot;site:Redmond&quot;. Para remover as definições configuradas no escopo do serviço, use uma sintaxe semelhante a esta: -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>O cmdlet <strong>Remove-CsConferencingConfiguration</strong> também pode ser executado concomitantemente às definições globais. Neste caso, entretanto, essas definições não serão removidas. Em vez disso, todas as propriedades simplesmente reassumirão seus valores padrão.</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings. O cmdlet **Remove-CsConferencingConfiguration** aceita instâncias por pipeline do objeto de configuração de conferências.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Remove-CsConferencingConfiguration** exclui instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings.

## Consulte Também

#### Outros Recursos

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

