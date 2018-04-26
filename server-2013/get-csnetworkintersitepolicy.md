---
title: Get-CsNetworkInterSitePolicy
TOCTitle: Get-CsNetworkInterSitePolicy
ms:assetid: a4a64048-f8d7-483a-9565-0c6f3b0937b7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412769(v=OCS.15)
ms:contentKeyID: 49307689
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterSitePolicy

 

_**Tópico modificado em:** 2015-03-09_

Recupera uma ou mais políticas entre sites de rede, que definem limitações de largura de banda entre sites que estiverem diretamente vinculados em uma configuração do CAC (controle de admissão de chamadas). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterSitePolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Chamar o cmdlet **Get-CsNetworkInterSitePolicy** sem parâmetros recuperará todas as políticas de site de rede definidas entre dois sites de redes diretamente vinculados.

    Get-CsNetworkInterSitePolicy

## EXEMPLO 2

Esse exemplo recupera a política do site de rede com a Identidade Reno\_Portland.

    Get-CsNetworkInterSitePolicy -Identity Reno_Portland

## EXEMPLO 3

O Exemplo 3 recupera todas as políticas de site de rede que possuem a cadeia de caracteres Reno em qualquer posição do valor Identidade. Os caracteres curinga (\*) dentro do valor passado para o parâmetro Filter indicam "qualquer caractere ou conjunto de caracteres". Em outras palavras, a cadeia de caracteres \*Reno\* corresponderá a valores de Identidade que começarem por qualquer caractere (ou caracteres), seguidos pela cadeia de caracteres Reno e seguidos por qualquer caractere (ou caracteres).

    Get-CsNetworkInterSitePolicy -Filter *Reno*

## EXEMPLO 4

Esse exemplo recupera todas as políticas de site de rede aos quais não tiver sido atribuído um perfil de política de largura de banda. O comando começa chamando o cmdlet **Get-CsNetworkInterSitePolicy**, que, como visto no Exemplo 1, recupera uma coleção de todas as políticas de site de rede. Esta coleção será então direcionada para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringirá a coleção apenas às políticas de site que não possuírem um perfil de política de largura de banda atribuído. Isso é feito mediante comparações, verificando se a propriedade BWPolicyProfileID de cada política de site é igual a (-eq) Null ($null).

    Get-CsNetworkInterSitePolicy | Where-Object {$_.BWPolicyProfileID -eq $null}

## Descrição detalhada

Quando os sites de rede compartilham um link direto, é possível definir as limitações de largura de banda de conexões de áudio e vídeo entre esses dois sites. Esse cmdlet recupera uma ou várias políticas de site de rede que associam definições de limitação de largura de banda a sites diretamente conectados.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsNetworkInterSitePolicy** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterSitePolicy"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Uma cadeia de caracteres que contém caracteres curinga que buscarão políticas de site com valores de Identidade a eles correspondentes.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador único da política de site de rede que se deseja recuperar. As políticas de site de rede são criadas apenas no escopo global. Portanto, esse identificador não precisa especificar um escopo. Em vez disso, ele contém uma cadeia de caracteres que é um nome exclusivo que identifica a política.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera as informações de política entre sites de rede na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Remove um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

