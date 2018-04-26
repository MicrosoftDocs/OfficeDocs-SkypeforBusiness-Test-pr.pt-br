---
title: New-CsNetworkMediaBypassConfiguration
TOCTitle: New-CsNetworkMediaBypassConfiguration
ms:assetid: 24055ae5-7fc8-4ca5-9e65-ac3a1f17b405
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425718(v=OCS.15)
ms:contentKeyID: 49306150
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkMediaBypassConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria novas definições globais para desvio de mídia. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsNetworkMediaBypassConfiguration [-AlwaysBypass <$true | $false>] [-BypassID <String>] [-Enabled <$true | $false>] [-EnableDefaultBypassID <$true | $false>] [-EnabledForAudioVideoConferences <$true | $false>] [-ExternalBypassMode <Off | ICE | Any>] [-InternalBypassMode <Off | ICE | Any>]

## Exemplos

## EXEMPLO 1

Os comandos deste exemplo habilitam o desvio de mídia e o configuram, de forma a sempre tentar efetuar o desvio. A primeira linha do exemplo é uma chamada ao cmdlet **New-CsNetworkMediaBypassConfiguration**. São passados dois parâmetros a este cmdlet: AlwaysBypass e Enabled, ambos definidos como True ($true). A definição de Enabled como True habilita o desvio de mídia, enquanto a definição de AlwaysBypass como True garante que se tentará efetuar o desvio de mídia em todas as chamadas. (observe que a definição desses dois parâmetros gerará automaticamente um valor para a propriedade BypassID.) O cmdlet **New-CsNetworkMediaBypassConfiguration** cria o objeto somente na memória. Portanto, atribuímos esse objeto à variável $a.

A configuração de desvio de mídia é armazenada com as definições de configuração de rede. Consequentemente, na linha 2 do exemplo, as alterações de configuração de desvio de mídia foram salvas à configuração de rede, chamando-se o cmdlet **Set-CsNetworkConfiguration** e passando-se o objeto de configuração de desvio de mídia ($a) que foi criado na linha 1 para o parâmetro MediaBypassSettings.

    $a = New-CsNetworkMediaBypassConfiguration -AlwaysBypass $true -Enabled $true
    Set-CsNetworkConfiguration -MediaBypassSettings $a

## EXEMPLO 2

Não há cmdlet **Set-CsNetworkMediaBypassConfiguration** em Lync Server. Portanto, para modificar as definições existentes, deve-se criar uma nova configuração (conforme mostra o Exemplo 1) para substituir a configuração existente, ou modificar as definições, recuperando as existentes, modificando-as e utilizando o cmdlet **Set-CsNetworkConfiguration** para salvar as alterações. Este exemplo demonstra o desligamento da opção Always Bypass pela utilização desta opção.

A primeira linha do exemplo recupera as definições de desvio de mídia existentes. Ela faz isso chamando o cmdlet **Get-CsNetworkConfiguration**. A chamada a este cmdlet está entre parênteses, para garantir que o cmdlet seja concluído antes da execução de qualquer outra parte do comando. O cmdlet **Get-CsNetworkConfiguration** recupera todas as definições da configuração de uma rede completa. Devido ao interesse apenas nas definições de desvio de mídia, especificamos a propriedade MediaBypassSettings, para que recupere apenas essas definições. As definições são atribuídas à variável $a.

Na linha 2, as definições armazenadas foram modificadas na variável $a, atribuindo-se o valor False ($false) à propriedade AlwaysBypass. Finalmente, na linha 3, chamamos o cmdlet **Set-CsNetworkConfiguration**, passando o parâmetro MediaBypassSettings à variável $a, que salva a alteração feita à propriedade AlwaysBypass.

    $a = (Get-CsNetworkConfiguration).MediaBypassSettings
    $a.AlwaysBypass = $false
    Set-CsNetworkConfiguration -MediaBypassSettings $a

## Descrição detalhada

Este cmdlet cria definições globais para desvio de mídia de conexões de áudio.

Diferentemente da maioria dos cmdlets New- de Lync Server, este não salva imediatamente a nova configuração. Ele cria as definições de configuração somente na memória. O objeto criado por este cmdlet deve ser salvo em uma variável e, em seguida, atribuído à propriedade MediaBypassSettings da configuração de rede. (para obter mais detalhes, consulte a seção Exemplos neste tópico).

As definições criadas com este cmdlet podem ser recuperadas somente pelo acesso à propriedade MediaBypassSettings da configuração de rede global. Para recuperar essas definições, execute o seguinte comando: (Get-CsNetworkConfiguration).MediaBypassSettings.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsNetworkMediaBypassConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkMediaBypassConfiguration"}

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
<td><p><em>AlwaysBypass</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>A definição dessa definição como True tentará efetuar o desvio de mídia de todas as chamadas.</p>
<p>Defina este valor de parâmetro como True apenas se o controle de admissão de chamadas (CAC) estiver desabilitado. Defina esse parâmetro como True aprenas para implantações em que:</p>
<p>- não houver necessidade de controle de largura de banda.</p>
<p>- não houver necessidade de configração minuciosa para determinar quando o desvio deverá ocorrer.</p>
<p>- houver conectividade plena entre gateways e clientes.</p>
<p>Se o parâmetro Enabled for definido como True e AlwaysBypass for definido como False, o desvio lógico usará os sites e as regiões da configuração de rede para determinar quando o desvio será possível.</p>
<p>Se AlwaysBypass for definido como True, mas o valor do parâmetro Enabled não tiver sido definido como True, será exibida uma mensagem de aviso: A definição AlwaysBypass será ignorada se Enabled for definido como False.</p>
<p>A definição de AlwaysBypass e Enabled como True gerará automaticamente um ID de desvio, que será armazenado na propriedade BypassID.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>O ID de desvio de mídia. Se o parâmetro AlwaysBypass for definido como True e um valor for fornecido para esse parâmetro, esse BypassID será associado a todas as sub-redes. Se AlwaysBypass for False, o valor de BypassID será associado a todas as sub-redes que não forem encontradas nos sites e nas regiões da configuração de rede.</p>
<p>Este ID deve estar no formato de um GUID (por exemplo, 96f14dea-5170-429a-b92b-f1cb909c4bb6). No entanto, normalmente, você não terá de definir ou alterar esse parâmetro. Este valor é gerado automaticamente quando Enabled é definido como True e: 1) AlwaysBypass estiver definido como True, ou 2) o parâmetro EnableDefaultBypassID estiver definido como True.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Defina este parâmetro como True, para habilitar o desvio de mídia. Nesse ponto, as decisões de desvio serão baseadas no valor da configuração de AlwaysBypass, como a seguir:</p>
<p>- se AlwaysBypass for True, tente o desvio de todas as chamadas.</p>
<p>- se AlwaysBypass for False, use o site e a região de configuração da rede para determinar se o desvio é possível.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDefaultBypassID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Esse valor apenas se aplica quando AlwaysBypass for definido como False.</p>
<p>A definição deste valor como True gerará automaticamente um ID de desvio padrão. Este valor gerado automaticamente será armazenado na propriedade BypassID.</p>
<p>Este parâmetro será útil quando houver um núcleo bem conectado com os sites remotos que tiverem vínculos restritos de largura de banda. O administrador precisará definir apenas as sub-redes associadas aos sites remotos por meio de sites e regiões da configuração de rede. Quaisquer sub-redes associadas ao núcleo não precisarão ser definidas e o desvio será tentado automaticamente entre essas sub-redes.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnabledForAudioVideoConferences</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Indica se o bypass de mídia deve ser usado para conferências de áudio/vídeo. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalBypassMode</em></p></td>
<td><p>Opcional</p></td>
<td><p>BypassModeEnumType</p></td>
<td><p>Reservado para uso futuro. O Lync Server não fornece suporte ao desvio de mídia externo.</p>
<p>Padrão: Desativada</p></td>
</tr>
<tr class="odd">
<td><p><em>InternalBypassMode</em></p></td>
<td><p>Opcional</p></td>
<td><p>BypassModeEnumType</p></td>
<td><p>O valor desse parâmetro controla quando clientes que se conectam no interior da rede da organização podem tentar realizar o desvio de mídia. Se Enabled estiver definido como True, esse valor será automaticamente alterado para Qualquer. Outros valores desse parâmetro são reservados para uso futuro.</p>
<p>Padrão: Desativada</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.MediaBypassSettingsType.

## Consulte Também

#### Outros Recursos

[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)

