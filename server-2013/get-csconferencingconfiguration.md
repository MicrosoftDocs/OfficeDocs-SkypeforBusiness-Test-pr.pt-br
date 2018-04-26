---
title: Get-CsConferencingConfiguration
TOCTitle: Get-CsConferencingConfiguration
ms:assetid: db4ab3bc-071c-4f73-a3a0-62dc8aed48a1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398965(v=OCS.15)
ms:contentKeyID: 49308320
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferencingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre as definições de configuração de conferências da organização. As definições de conferências determinam aspectos como o tamanho máximo permitido do conteúdo e dos folhetos da conferência, o período de cortesia do conteúdo (ou seja, o tempo que o conteúdo será armazenado antes de ser excluído) e os URLs dos downloads internos e externos do cliente suportado. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsConferencingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 retorna informações sobre todas as definições de configuração de conferências atualmente em uso na organização. Isto é feito chamando o cmdlet **Get-CsConferencingConfiguration** sem nenhum parâmetro.

    Get-CsConferencingConfiguration

## EXEMPLO 2

No Exemplo 2, as informações de configuração de conferências são retornadas para o site de Redmond (-Identity site:Redmond). Como as Identidades são exclusivas, esse comando sempre retornará, no máximo, uma única coleção de definições de configuração de conferências.

    Get-CsConferencingConfiguration -Identity site:Redmond

## EXEMPLO 3

O comando mostrado no Exemplo 3 retorna informações sobre todas as definições de configuração de conferências que foram aplicadas ao escopo do site. Para isso, o cmdlet **Get-CsConferencingConfiguration**é chamado junto com o parâmetro Filter. O valor de filtro "site:\*" garante que apenas as configurações cuja Identidade começa com o valor de cadeia de caracteres "site:" serão retornadas.

    Get-CsConferencingConfiguration -Filter "site:*"

## EXEMPLO 4

O Exemplo 4 retorna informações sobre todas as definições de configuração de conferências nas quais a organização não está definida como Litwareinc. Para realizar esta tarefa, o comando chama primeiro o cmdlet **Get-CsConferencingConfiguration** sem nenhum parâmetro. Isso retorna uma coleção de todas as definições de configuração de conferências usadas na organização. A coleção resultante é então canalizada ao cmdlet **Where-Object**, que seleciona apenas as configurações cuja propriedade Organization não é igual a Litwareinc.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Litwareinc"}

## EXEMPLO 5

No Exemplo 5, as informações são retornadas apenas para as definições de configuração de conferências cujo espaço máximo de armazenamento de conteúdo é superior a 100 megabytes. Para isso, o comando chama primeiro o cmdlet **Get-CsConferencingConfiguration** sem nenhum parâmetro para retornar uma coleção de todas as definições de configuração de conferências. Esta coleção é então canalizada ao cmdlet **Where-Object**, que seleciona as configurações cujo espaço de armazenamento de conteúdo é superior a 100 megabytes.

    Get-CsConferencingConfiguration | Where-Object {$_.MaxContentStorageMB -gt 100}

## Descrição detalhada

Quando se trata de conferências, o gerenciamento e a administração são divididos entre dois conjuntos de cmdlets. Se quiser gerenciar os aspectos que os usuários podem ou não fazer (por exemplo: se eles podem convidar participantes anônimos para entrar em uma conferência, oferecer o compartilhamento de aplicativos em uma conferência ou transferir arquivos em uma conferência), será necessário usar os cmdlets **CsConferencingPolicy**.

Além das atividades do usuário, os administradores precisam gerenciar o Lync Server Serviço de Webconferência. Por exemplo: os administradores precisam realizar ações, como especificar o valor máximo de armazenamento de conteúdo alocado para uma única conferência e especificar o período de cortesia antes que o conteúdo da conferência seja automaticamente excluído. Também deve-se permitir que eles especifiquem as portas usadas para atividades como compartilhamento de aplicativos e transferência de arquivos.

Estas últimas atividades podem ser gerenciadas usando-se os cmdlets **CsConferencingConfiguration**. Estes cmdlets permitem gerenciar os próprios servidores. Os cmdlets **CsConferencingConfiguration** (que podem ser aplicados aos escopos globais, de site e de serviço) não são usados para especificar se um usuário pode ou não compartilhar aplicativos durante uma conferência. No entanto, se o compartilhamento de aplicativos for permitido, esses cmdlets permitem indicar quais portas deverão ser usadas para essa atividade. Da mesma forma, os cmdlets permitem especificar os limites de armazenamento e os períodos de validade, bem como os indicadores para URLs internos e externos nos quais os usuários podem obter ajuda e recursos relacionados às conferências.

O cmdlet **Get-CsConferencingConfiguration** permite aos administradores retornarem informações sobre todas as definições de configuração de conferências em uso nas suas organizações.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsConferencingConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferencingConfiguration"}

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
<td><p>Permite utilizar caracteres curingas ao especificar a Identidade das definições de configuração de conferências a ser retornada. Por exemplo, esta sintaxe retorna todas as definições configuradas no escopo de site: -Filter &quot;site:*&quot; Esta sintaxe retorna todas as definições configuradas no escopo de serviço: -Filter &quot;service:*&quot;.</p>
<p>Observe que não é possível utilizar os parâmetros Filter e Identity no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identificador exclusivo da coleção de definições de configuração de conferências a ser recuperada. Para recuperar as definições globais, use essa sintaxe: -Identity global. Para recuperar as definições configuradas no escopo de site, utilize uma sintaxe similar a esta: -Identity &quot;site:Redmond&quot;. Para recuperar as definições configuradas no escopo de serviço, utilize uma sintaxe similar a esta: -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Se esse parâmetro não for incluído, o cmdlet <strong>Get-CsConferencingConfiguration</strong> retornará todas as definições de configuração de conferências em uso na organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados de configuração de conferências na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsConferencingConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsConferencingConfiguration** retorna as instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings.

## Consulte Também

#### Outros Recursos

[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

