---
title: Set-CsNetworkBandwidthPolicyProfile
TOCTitle: Set-CsNetworkBandwidthPolicyProfile
ms:assetid: 519916b9-d5a0-476e-a516-9b8a3058daf2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398338(v=OCS.15)
ms:contentKeyID: 49306708
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkBandwidthPolicyProfile

 

_**Tópico modificado em:** 2015-03-09_

Modifica um perfil existente de política de largura de banda de rede. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkBandwidthPolicyProfile [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo modifica a descrição do perfil da política de largura de banda cuja identidade for LowBWProfile. Ele faz isso chamando o cmdlet **Set-CsNetworkBandwidthPolicyProfile** com dois parâmetros: Identity, especificando o nome do perfil a modificar; e Description, especificando a nova descrição do perfil.

    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile -Description "Policy for links of less than 10MB"

## EXEMPLO 2

O Exemplo 2 modifica o limite total e o limite de sessão de transmissões de vídeo do perfil da política de largura de banda cuja identidade for LowBWLimit. Após se especificar a identidade do perfil a ser modificado, utiliza-se o parâmetro VideoBWLimit, para definir como 2500 o limite geral de vídeo. Em seguida, utiliza-se o parâmetro VideoBWSessionLimit para definir como 300 o limite de sessão individual. Este comando adicionará um perfil de vídeo ou atualizará um perfil de vídeo existente do perfil da política de largura de banda LowBWLimit. Quaisquer perfis de áudio existentes não serão afetados.

    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -VideoBWLimit 2500 -VideoBWSessionLimit 300

## EXEMPLO 3

Neste exemplo, uma nova política de largura de banda será criada e atribuída ao perfil da política de largura de banda cuja identidade for LowBWLimit. A primeira linha do exemplo é uma chamada ao cmdlet **New-CsNetworkBWPolicy**. Este cmdlet cria um novo perfil, neste caso um perfil de vídeo (-BWPolicyModality video) com um limite de 5000 kbps (-BWLimit 5000) e um limite de sessão de 200 kbps (-BWSessionLimit 200). Este novo objeto de perfil será armazenado na variável $bp. A próxima linha deste exemplo chamará o cmdlet **Set-CsNetworkBandwidthPolicyProfile**, para modificar o perfil LowBWLimit (-Identity LowBWLimit). O parâmetro BWPolicy é utilizado com o valor $bp. Isto substitui quaisquer políticas existentes neste perfil pela política recém-criada, que foi armazenada na variável $bp.

    $bp = New-CsNetworkBWPolicy -BWLimit 5000 -BWSessionLimit 200 -BWPolicyModality video
    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bp

## EXEMPLO 4

O exemplo 4 adiciona uma nova política de largura de banda ao conjunto de políticas existentes no perfil LowBWProfile. Na linha 1, chama-se o cmdlet **Get-CsNetworkBandwidthPolicyProfile**, para recuperar o perfil cuja identidade for LowBWProfile. Armazena-se este perfil na variável $a. Na próxima linha, chama-se o cmdlet **New-CsNetworkBWPolicy**, para criar uma nova política de largura de banda. Esta é uma política de áudio (-BWPolicyModality audio), com um limite de 2000 kbps (-BWLimit 2000) e um limite de sessão de 300 kbps (-BWSessionLimit 300). Esta nova política será armazenada na variável $ap.

Na linha 3, adiciona-se a nova política de áudio (armazenada em $ap) ao perfil recuperado na linha 1 (e armazenado na variável $a). Isto é feito chamando-se o método Add da propriedade BWPolicy do perfil e passando o valor de $ap. Isto pode ser lido como "Adicionar a nova política, armazenada em $ap, a BWPolicy do perfil LowBWProfile (armazenado em $a)".

Finalmente, chama-se o cmdlet **Set-CsNetworkBandwidthPolicyProfile**, para atualizar o perfil LowBWProfile. Utiliza-se o parâmetro Instance, passando-lhe o valor de $a, que contém o perfil modificado.

    $a = Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile
    $ap = New-CsNetworkBWPolicy -BWLimit 2000 -BWSessionLimit 300 -BWPolicyModality audio
    $a.BWPolicy.Add($ap)
    Set-CsNetworkBandwidthPolicyProfile -Instance $a

## EXEMPLO 5

O Exemplo 5 é idêntico em funcionalidade ao Exemplo 4: ele adiciona uma nova política de áudio a uma lista de política existentes do perfil LowBWProfile. Este método requer menos linhas, mas pode não ser tão claro. Foi incluído aqui simplesmente para demonstrar que existem modos diferentes de se fazer a mesma coisa.

Na linha 1, cria-se uma nova política de largura de banda de áudio, definindo-se um limite de largura de banda (2000), um limite de sessão (300) e armazenando-se o novo objeto na variável $ap. A seguir, chama-se o cmdlet **Set-CsNetworkBandwidthPolicyProfile**, para modificar o perfil cuja identidade for LowBWProfile. Utiliza-se o parâmetro BWPolicy para modificar a lista de políticas do perfil. Observe o valor passado para este parâmetro: @{add=$ap}. Isto é simplesmente um modo de adicionar algo a uma lista no Windows PowerShell. Inicia-se com o caractere @, seguido de um conjunto de chaves {}. Dentro dessas chaves, especifica-se a ação a ser realizada na lista. Neste caso, adicionar algo à lista. (pode-se também remover ou substituir algo.) Coloca-se um sinal de igual após a ação (add), seguido do objeto que se quer adicionar à lista. Neste caso, a nova política armazenada na variável $ap.

    $ap = New-CsNetworkBWPolicy -BWLimit 2000 -BWSessionLimit 300 -BWPolicyModality audio
    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile -BWPolicy @{add=$ap}

## Descrição detalhada

Como parte do controle de admissão de chamadas (CAC), utiliza-se uma política de largura de banda para definir as limitações de largura de banda de determinadas modalidades. (no Lync Server, as limitações de largura de banda podem ser atribuídas apenas às modalidades de áudio e vídeo). Esse cmdlet modifica um perfil de contêiner dessas políticas.

IMPORTANTE: Se um perfil contiver múltiplas políticas (por exemplo, uma política de áudio e uma de vídeo), a modificação do perfil mediante o uso das propriedades AudioBWLimit, AudioBWSessionLimit, VideoBWLimit ou VideoBWSessionLimit removerá todas as políticas existentes no perfil e as substituirá pelos novos valores. Se o perfil continha uma política para limitar o vídeo e somente o parâmetro AudioBWLimit for definido, a política de vídeo será removida e será criada uma política de áudio.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsNetworkBandwidthPolicyProfile** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkBandwidthPolicyProfile"}

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
<td><p><em>AudioBWLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A largura máxima de banda a se alocar para todas as conexões de áudio. Se uma única sessão de áudio exceder o limite de largura de banda de áudio, essa sessão não será iniciada.</p>
<p>Expresso em kbps. Por exemplo, o valor 1000 significa 1000 kbps.</p>
<p>Se for fornecido um valor para este parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro AudioBWSessionLimit, mas não para AudioBWLimit, este será definido como 0.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBWSessionLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A largura máxima de banda a se alocar por sessão de áudio. Expresso em kbps. O valor deve ser 40 ou superior.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro AudioBWLimit, mas não para AudioBWSessionLimit, este será definido como 175.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de objetos contendo perfis de política de largura de banda. Cada objeto na lista consiste em uma modalidade de largura de banda (áudio ou vídeo), uma limitação de largura de banda e uma limitação de sessão de largura de banda.</p>
<p>Se for fornecido um valor para esse parâmetro, não será possível fornecer um valor para os parâmetros AudioBWLimit, AudioBWSessionLimit, VideoBWLimit ou VideoBWSessionLimit.</p>
<p>Os objetos na lista devem ser do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType. Os objetos deste tipo podem ser criados chamando-se o cmdlet <strong>New-CsNetworkBWPolicy</strong> e a política resultante poderá, então, ser adicionada ao perfil, passando-a como o valor deste parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Uma descrição do perfil de política de largura de banda. Por exemplo, é possível usar esse parâmetro para esclarecer o uso esperado do perfil.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>Um valor de cadeia de caracteres que identifica exclusivamente o perfil de política de largura de banda a ser modificado. Ele é idêntico à propriedade BWPolicyProfileID do perfil e pode ser alterado mudando-se o valor desta propriedade. Isto é equivalente a uma operação de &quot;cortar e colar&quot;: todas as propriedades do perfil permanecerão inalteradas. Somente o seu nome mudará. Contudo, este valor não poderá ser mudado se o perfil estiver atribuído a um site de rede.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>BWPolicyProfileType</p></td>
<td><p>Uma referência a um objeto de perfil de política de largura de banda (um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType), que contém as definições que se quer utilizar para modificar o perfil. Este objeto pode ser recuperado chamando-se o cmdlet <strong>Get-CsNetworkBandwidthPolicyProfile</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoBWLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A largura máxima de banda a se alocar para todas as conexões de vídeo. Se uma única sessão de vídeo exceder o limite de largura de banda de vídeo, essa sessão não será iniciada.</p>
<p>Expresso em kbps. Por exemplo, o valor 1000 significa 1000 kbps.</p>
<p>Se você fornecer um valor para esse parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro VideoBWSessionLimit, mas não para VideoBWLimit, este será definido como 0.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBWSessionLimit</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>A largura máxima de banda a se alocar por sessão de vídeo. Expresso em kbps. O valor deve ser 100 ou superior.</p>
<p>Se for fornecido um valor para este parâmetro, não será possível fornecer um valor para o parâmetro BWPolicy.</p>
<p>Padrão: Se você fornecer um valor para o parâmetro VideoBWLimit, mas não para VideoBWSessionLimit, este será definido como 700.</p></td>
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

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType. Aceita entrada canalizada dos objetos do perfil da política de largura de banda de rede.

## Tipos de retorno

Este cmdlet não retorna um valor. Ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)

