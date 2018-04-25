---
title: New-CsNetworkBWPolicy
TOCTitle: New-CsNetworkBWPolicy
ms:assetid: bbc91bd1-453c-4ae6-bb77-3b6be9429ed0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412916(v=OCS.15)
ms:contentKeyID: 49307948
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBWPolicy

 

_**Tópico modificado em:** 2015-03-09_

Cria uma política de largura de banda que pode ser aplicada ao perfil de política de largura de banda. No Lync Server, a política se aplica à largura de banda de áudio ou vídeo. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsNetworkBWPolicy -BWLimit <UInt32> -BWPolicyModality <Audio | Video> -BWSessionLimit <UInt32>

## Exemplos

## EXEMPLO 1

Esse exemplo cria uma nova política de largura de banda e a atribui à variável $bwp. Todos os parâmetros do cmdlet **New-CsNetworkBWPolicy** são obrigatórios. Neste exemplo, é especificado um limite total de largura de banda (BWLimit) de 2000 kbps e um limite de sessão de largura de banda (BWSessionLimit) de 300 kbps, aplicando-os a sessões de vídeo (-BWPolicyModality).

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video

## EXEMPLO 2

O Exemplo 2 amplia o âmbito do Exemplo 1, atribuindo a nova política de largura de banda a um perfil de política. O comando na linha 1 é idêntico ao Exemplo 1: cria limitações de largura de banda de vídeo. Em seguida, a linha 2 chama o cmdlet **New-CsNetworkBandwidthPolicyProfile** para adicionar essa política a um novo perfil. O novo perfil recebe a Identidade LowBWLimit. Em seguida,o parâmetro BWPolicy é usado, dando a ele o valor $bwp, que é a variável que contém a nova política de largura de banda recém criada na Linha 1.

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video
    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bwp

## Descrição detalhada

Esse cmdlet cria uma nova política de largura de banda. Uma política de largura de banda é usada para definir as limitações de largura de banda de determinadas modalidades (no Lync Server, as limitações de largura de banda podem ser atribuídas apenas às modalidades de áudio e vídeo). A política de largura de banda é criada apenas na memória. Portanto, a saída deve ser atribuída a uma variável e, em seguida, passada como um valor para o parâmetro BWPolicy do cmdlet **New-CsNetworkBandwidthPolicyProfile** ou **Set-CsNetworkBandwidthPolicyProfile**. As políticas de largura de banda se aplicam a perfis de políticas, que podem armazenar diversas políticas de um único perfil e são parte da configuração de rede global para o CAC.

Observe que o método recomendado de atribuição de políticas de áudio e vídeo consiste em atribui-las diretamente a um perfil de política de largura de banda, chamando o cmdlet **New-CsNetworkBandwidthPolicyProfile** ou **Set-CsNetworkBandwidthPolicyProfile** e especificando valores para os parâmetros AudioBWLimit, AudioBWSessionLimit, VideoBWLimit e VideoBWSessionLimit.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsNetworkBWPolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWPolicy"}

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
<td><p><em>BWLimit</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.UInt32</p></td>
<td><p>A largura de banda total máxima (em kbps) de todas as sessões simultâneas do tipo especificado no parâmetro BWPolicyModality.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
<td><p>Determina qual tipo de largura de banda será limitada.</p>
<p>Valores válidos: Áudio, vídeo</p></td>
</tr>
<tr class="odd">
<td><p><em>BWSessionLimit</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.UInt32</p></td>
<td><p>A largura de banda máxima (em kbps), permitida a uma única sessão do tipo especificado no parâmetro BWPolicyModality.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

