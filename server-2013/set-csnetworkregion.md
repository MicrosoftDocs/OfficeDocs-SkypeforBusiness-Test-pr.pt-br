---
title: Set-CsNetworkRegion
TOCTitle: Set-CsNetworkRegion
ms:assetid: ffa1774b-ac60-4392-ad55-07bb887bf945
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413089(v=OCS.15)
ms:contentKeyID: 49308728
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkRegion

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma região de rede existente. As regiões de rede representam hubs de rede ou backbones em uma rede corporativa. Este cmdlet foi introduzido no Lync Server 2010..

## Sintaxe

    Set-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkRegion [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AudioAlternatePath <$true | $false>] [-BWAlternatePaths <PSListModifier>] [-BypassID <String>] [-CentralSite <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-VideoAlternatePath <$true | $false>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Neste exemplo, modifica-se a região de rede denominada Vancouver. O parâmetro Description recebe o valor "Região norte-americana". Se existir uma Descrição na região NorthAmerica, esse comando a substituirá por esse valor. Se nenhuma Descrição tiver sido definida, esse comando a definirá.

    Set-CsNetworkRegion -Identity NorthAmerica -Description "North American Region"

## EXEMPLO 2

Este exemplo modifica a região de rede chamada EMEA e fornece a ela uma nova configuração de caminho alternativo de vídeo. Para isso, chamamos o cmdlet **Set-CsNetworkRegion** passando a Identidade EMEA. Em seguida, especificamos o parâmetro VideoAlternatePath, passando o valor $False. A configuração de VideoAlternatePath como False indica que, se não houver disponibilidade de largura de banda adequada, a chamada de vídeo não será roteada para um caminho alternativo. Em vez disso, ela simplesmente não será concluída.

    Set-CsNetworkRegion -Identity EMEA -VideoAlternatePath $False

## EXEMPLO 3

O Exemplo 3 atribui à região de rede Ásia o mesmo conjunto de definições de caminho alternativo que tiver sido atribuído à região NorthAmerica. A primeira linha nesse exemplo recupera uma instância da região de rede NorthAmerica e a atribui à variável $a. A segunda linha inicialmente recupera o conteúdo da propriedade BWAlternatePaths ou da região NorthAmerica (armazenada na variável $a): $a.BWAlternatePaths. Essa será uma coleção de todas as definições de caminho alternativo na região NorthAmerica.

A próxima ação consiste em canalizar essa coleção de configuração para a função foreach. Foreach lidará com um item da coleção por vez, realizando as ações nas seguintes chaves. Nesse caso, a ação consiste em chamar o cmdlet **Set-CsNetworkRegion** com a Identidade Ásia para definir as propriedades da região Ásia. O próximo parâmetro é BWAlternatePaths. Passamos o valor @{add=$\_} a esse parâmetro. A variável $\_ representa o item atual da coleção, nesse caso, o caminho alternativo atual. A porção @{add=} do valor adiciona esse item à coleção BWAlternatePaths da região Ásia.

    $a = Get-CsNetworkRegion -Identity NorthAmerica
    $a.BWAlternatePaths | foreach {Set-CsNetworkRegion -Identity Asia -BWAlternatePaths @{add=$_}}

## Descrição detalhada

Uma região de rede interconecta diversas partes de uma rede em diversas áreas geográficas. Toda região de rede deve ser associada a um site central. O site central é o site do data center no qual estiver em execução o serviço de política de largura de banda do controle de admissão de chamadas (CAC). Utilize esse cmdlet para modificar uma região de rede existente, inclusive definições que determinam se são permitidos caminhos alternativos para as conexões de áudio e vídeo, e associar esses sites à região com uma configuração de desvio de mídia.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkRegion** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkRegion\\b"}

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
<td><p><em>AudioAlternatePath</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Esse parâmetro determina se as chamadas de áudio serão roteadas por um caminho alternativo, caso não haja largura de banda adequada no caminho primário.</p>
<p>Esse parâmetro preenche a propriedade BWAlternatePaths. O valor fornecido para esse parâmetro é armazenado na propriedade AlternatePath do elemento de caminho alternativo com o valor BWPolicyModality de Áudio.</p>
<p>Caso seja fornecido um valor para esse parâmetro, não será possível especificar um valor para o parâmetro BWAlternatePaths.</p>
<p>Se qualquer uma das suas chamadas for uma chamada pela Internet, esse valor deve ser True, independentemente das configurações de largura de banda.</p></td>
</tr>
<tr class="even">
<td><p><em>BWAlternatePaths</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de objetos que contêm informações sobre quais caminhos de conexão alternativa são permitidos, caso não haja possibilidade de efetuar uma solicitação de mídia no caminho preferido (por exemplo, se os limites nesse caminho tiverem sido excedidos). Os objetos de caminho alternativo devem ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType. É possível criar objetos desse tipo chamando-se o cmdlet <strong>New-CsNetworkBWAlternatePath</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>BypassID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Um GUID (identificador global exclusivo). Este GUID é utilizado para associar regiões de rede às configurações de desvio de mídia em uma configuração de rede do CAC ou Enhanced 9-1-1 (E9-1-1). (Utilize este valor de BypassID ao chamar o cmdlet <strong>New-CsNetworkMediaBypassConfiguration</strong>).</p>
<p>Esse parâmetro pode ser gerado automaticamente quando a região for criada (chamando-se o cmdlet <strong>New-CsNetworkRegion</strong>). Não é recomendável alterar esse valor. Caso especifique um valor, faça-o no formato de um GUID (por exemplo: 3b24a047-dce6-48b2-9f20-9fbff17ed62a). Será emitida uma confirmação, solicitando a confirmação da intenção de se definir manualmente esse valor.</p></td>
</tr>
<tr class="even">
<td><p><em>CentralSite</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O site central que executa o serviço de política de largura de banda. Esse serviço deve ser habilitado para usar o CAC. Esse serviço é executado no Servidor Front-End ou no Servidor Standard Edition.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma cadeia de caracteres que descreve a região. Este parâmetro pode ser utilizado para fornecer uma explicação mais descritiva sobre a função da região, superando o que pode ser expresso apenas pela identidade.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo da região de rede que se deseja modificar. A identidade terá o formato de uma cadeia de caracteres que identifica a região de forma exclusiva.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSObject</p></td>
<td><p>Uma referência a um objeto de região de rede. Este objeto deve ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType e pode ser recuperado chamando o cmdlet <strong>Get-CsNetworkRegion</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoAlternatePath</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Esse parâmetro determina se as chamadas de vídeo serão roteadas por um caminho alternativo, caso não haja largura de banda adequada no caminho primário.</p>
<p>Esse parâmetro preenche a propriedade BWAlternatePaths. O valor fornecido para esse parâmetro é armazenado na propriedade AlternatePath do elemento de caminho alternativo com o valor BWPolicyModality de Vídeo.</p>
<p>Caso seja fornecido um valor para esse parâmetro, não será possível especificar um valor para o parâmetro BWAlternatePaths.</p>
<p>Se qualquer uma das suas chamadas for uma chamada pela Internet, esse valor deve ser True, independentemente das configurações de largura de banda.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType. Aceita entradas canalizadas dos objetos de região de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[New-CsNetworkBWAlternatePath](new-csnetworkbwalternatepath.md)

