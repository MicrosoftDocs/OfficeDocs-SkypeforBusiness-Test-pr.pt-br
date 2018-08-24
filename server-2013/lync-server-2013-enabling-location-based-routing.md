---
title: Habilitando o Roteamento com Base no Local no Lync Server 2013
TOCTitle: Habilitando o Roteamento com Base no Local no Lync Server 2013
ms:assetid: 029ede7e-0c4e-4ad2-af99-909ae674d6fe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994014(v=OCS.15)
ms:contentKeyID: 52057545
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando o Roteamento com Base no Local no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Assim que o Enterprise Voice for implantado e regiões de rede, sites e sub-redes forem definidos, você poderá habilitar o Roteamento com Base no Local. O Roteamento com Base no Local deve ser habilitado para os seguintes elementos do Enterprise Voice:

  - Sites de rede

  - Configurações de tronco

  - Políticas de voz

  - Configuração de roteamento

## Habilitar o Roteamento com Base no Local em Sites de Rede

Depois de ter implantado o Enterprise Voice e de ter configurado sites de rede, você estará pronto para configurar o Roteamento com Base no Local. Primeiro, você cria uma política de roteamento de voz para associar o site de rede aos usos apropriados de PSTN. Ao atribuir usos de PSTN a uma política de roteamento de voz, utilize somente os usos de PSTN associados a rotas de voz que usem um gateway PSTN local do site ou um gateway PSTN que esteja localizado em uma região onde restrições de Roteamento com Base no Local não sejam necessárias. Use o comando do Lync ServerWindows PowerShell, New-CsVoiceRoutingPolicy ou o Painel de Controle do Lync Server para criar políticas de roteamento de voz.

    New-CsVoiceRoutingPolicy -Identity <voice routing policy ID> -Name <voice routing policy name> -PstnUsages <usages>

Para obter mais informações, consulte [New-CsVoiceRoutingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsVoiceRoutingPolicy).

Para este exemplo, a tabela a tabela e os comandos do Windows PowerShell a seguir ilustram duas políticas de roteamento de voz e seus usos de PSTN associados definidos neste cenário. Somente as configurações específicas do Roteamento com Base no Local foram incluídas na tabela para fins de ilustração.

    New-CsVoiceRoutingPolicy -Identity "DelhiVoiceRoutingPolicy" -Name "Delhi voice routing policy" -PstnUsages @{add="Delhi usage", "PBX Del usage", "PBX Hyd usage"}
    New-CsVoiceRoutingPolicy -Identity "HyderabadVoiceRoutingPolicy" -Name " Hyderabad voice routing policy" -PstnUsages @{add="Hyderabad usage", "PBX Del usage", "PBX Hyd usage"}


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Política de roteamento de voz 1</th>
<th>Política de roteamento de voz 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ID da política de voz</p></td>
<td><p>Política de roteamento de voz de Délhi</p></td>
<td><p>Política de roteamento de voz de Hyderabad</p></td>
</tr>
<tr class="even">
<td><p>Usos da PSTN</p></td>
<td><p>Uso de Délhi, uso de PBX Del, uso de PBX Hyd</p></td>
<td><p>Uso de Hyderabad, uso de PBX Hyd, uso de PBX Del</p></td>
</tr>
</tbody>
</table>

  

Em seguida, configure o Roteamento com Base no Local para os sites de rede aplicáveis e associe suas políticas de roteamento de voz a eles. Use o comando do Lync ServerWindows PowerShell, New-CsNetworkSite, para habilitar o Roteamento com Base no Local e associe políticas de roteamento de voz a seus sites de rede que terão de impor restrições de roteamento.

    Set-CsNetworkSite -Identity <site ID> -EnableLocationBasedRouting <$true|$false> -VoiceRoutingPolicy <voice routing policy ID>

Neste exemplo, a tabela a seguir ilustra o Roteamento com Base no Local para dois sites de rede diferentes, Délhi e Hyderabad, definidos neste cenário usando o Lync ServerWindows PowerShell. Somente as configurações específicas do Roteamento com Base no Local foram incluídas na tabela para fins de ilustração.

    Set-CsNetworkSite -Identity "Delhi" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "DelhiVoiceRoutingPolicy"
    Set-CsNetworkSite -Identity "Hyderabad" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "HyderabadVoiceRoutingPolicy"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Site 1 (Délhi)</th>
<th>Site 2 (Hyderabad)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome do site</p></td>
<td><p>Site 1 (Délhi)</p></td>
<td><p>Site 2 (Hyderabad)</p></td>
</tr>
<tr class="even">
<td><p>EnableLocationBasedRouting</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p>Política de roteamento de voz</p></td>
<td><p>Política de roteamento de voz de Délhi</p></td>
<td><p>Política de roteamento de voz de Hyderabad</p></td>
</tr>
<tr class="even">
<td><p>Sub-redes</p></td>
<td><p>Sub-rede 1 (Délhi)</p></td>
<td><p>Sub-rede 2 (Hyderabad)</p></td>
</tr>
</tbody>
</table>



## Habilitar o Roteamento com Base no Local para troncos

Antes que uma configuração de tronco possa ser habilitada para o Roteamento com Base no Local, você precisará criar uma configuração de tronco para cada tronco em cada site de rede. Use o comando do Lync ServerWindows PowerShell, New-CsTrunkConfiguration, para criar uma configuração de tronco. Se vários troncos estiverem associados a um determinado sistema (isto é, Gateway ou PBX), cada configuração de tronco deverá ser modificado para habilitar restrições da Rotação com Base no Local.

    New-CsTrunkConfiguration -Identity < trunk configuration ID>

Para obter mais informações, consulte [New-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTrunkConfiguration).

Para este exemplo, os comandos do Windows PowerShell a seguir ilustram a criação de uma configuração de tronco para cada tronco na implantação definida neste cenário.

    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 1 DEL-GW>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 2 HYD-GW>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 3 DEL-PBX>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 4 HYD-PBX>"

Assim que uma configuração de tronco for configurada por tronco, você poderá usar o comando do Lync ServerWindows PowerShell, Set-CsTrunkConfiguration, para habilitar o Roteamento com Base no Local para seus troncos que devem impor restrições de roteamento. Habilite o Roteamento com Base no Local para troncos que roteiem chamadas para gateways de PSTN que roteiem chamadas para PSTN e associe o site de rede onde o gateway está localizado.

    Set-CsTrunkConfiguration -Identity <trunk configuration ID> -EnableLocationRestriction $true -NetworkSiteID <site ID>

Para obter mais informações, consulte [New-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTrunkConfiguration).

Neste exemplo, o Roteamento com Base no Local é habilitado para cada tronco associado a gateways de PSTN em Délhi e em Hyderabad:

    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 1 DEL-GW -EnableLocationRestriction $true -NetworkSiteID "Delhi"
    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 2 HYD-GW -EnableLocationRestriction $true -NetworkSiteID "Hyderabad"

  

Não habilite o Roteamento com Base no Local para troncos que não roteiem chamadas à PSTN; você ainda deverá associar o tronco ao site de rede onde o sistema está localizado à medida que restrições do Roteamento com Base no Local tenham de ser impostas para chamadas de PSTN que estejam chegando a pontos de extremidade conectados por meio desse tronco. Para este exemplo, o Roteamento com Base no Local não está habilitado para cada tronco associado a sistemas PBX em Délhi e em Hyderabad:

    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 3 DEL-PBX -EnableLocationRestriction $false -NetworkSiteID "Delhi"
    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 4 HYD-PBX -EnableLocationRestriction $false -NetworkSiteID "Hyderabad"

  
Pontos de extremidade que estejam conectados a sistemas que não roteiem chamadas para o PSTN (isto é, um PBX) terão restrições semelhantes aos pontos de extremidade do Lync de usuários habilitados para o Roteamento com Base no Local. Isso significa que esses usuários poderão fazer e receber chamadas de e para um usuário do Lync, independentemente do local do usuário. Eles também poderão fazer e receber chamadas de e para outros sistemas que não roteiem chamadas para a rede PSTN (isto é, um ponto de extremidade conectado a um PBX diferente) independentemente do site de rede ao qual o sistema está associado. Todas as chamadas de entrada, chamadas de saída, transferências de chamada e encaminhamento de chamada envolvendo pontos de extremidade de PSTN estarão sujeitas a imposições do Roteamento com Base no Local. Tais chamadas deverão usar somente gateways de PSTN definidos como locais para tais sistemas.

A tabela a seguir ilustra a configuração de tronco de quatro troncos em dois sites de rede diferentes: dois conectados a gateways de PSTN e dois conectados a sistemas PBX.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>EnableLocationRestriction</th>
<th>NetworkSiteID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PstnGateway:Trunk 1 DEL-GW</p></td>
<td><p>True</p></td>
<td><p>Site 1 (Délhi)</p></td>
</tr>
<tr class="even">
<td><p>PstnGateway:Trunk 2 HYD-GW</p></td>
<td><p>True</p></td>
<td><p>Site 2 (Hyderabad)</p></td>
</tr>
<tr class="odd">
<td><p>PstnGateway:Trunk 3 DEL-PBX</p></td>
<td><p>False</p></td>
<td><p>Site 1 (Délhi)</p></td>
</tr>
<tr class="even">
<td><p>PstnGateway:Trunk 4 HYD-PBX</p></td>
<td><p>False</p></td>
<td><p>Site 2 (Hyderabad)</p></td>
</tr>
</tbody>
</table>



## Habilitar o Roteamento com Base no Local para políticas de voz

Para impor o Roteamento com Base no Local para usuários específicos, configure a política de voz desses usuários para impedir o desvio de chamada tarifada de PSTN. Use o comando do Lync ServerWindows PowerShell, New-CsVoicePolicy, para criar uma nova política de voz ou Set-CsVoicePolicy, se estiver usando uma política existentes, para habilitar o Roteamento com Base no Local ao impedir o desvio de chamada tarifada de PSTN.

    Set-CsVoicePolicy -Identity <voice policy ID> -PreventPSTNTollBypass <$true|$false>

Para obter mais informações, consulte [New-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsVoicePolicy).

Para este exemplo, a tabela e os comandos do Windows PowerShell a seguir ilustram a habilitação da prevenção do desvio de chamada tarifada de PSTN para as políticas de voz de Délhi e de Hyderabad definidas neste cenário. Somente as configurações específicas do Roteamento com Base no Local foram incluídas na tabela para fins de ilustração.

    Set-CsVoicePolicy -Identity "Delhi voice policy" -PreventPSTNTollBypass $true
    Set-CsVoicePolicy -Identity "Hyderabad voice policy" -PreventPSTNTollBypass $true


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Política de voz 1</th>
<th>Política de voz 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ID da política de voz</p></td>
<td><p>Política de voz de Délhi</p></td>
<td><p>Política de voz de Hyderabad</p></td>
</tr>
<tr class="even">
<td><p>Usos da PSTN</p></td>
<td><p>Uso de Délhi, uso de PBX Del, uso de PBX Hyd</p></td>
<td><p>Uso de Hyderabad, uso de PBX Hyd, uso de PBX Del</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>



## Habilitar o Roteamento com Base no Local na configuração de roteamento

Por fim, habilite globalmente o Roteamento com Base no Local para sua configuração de roteamento. Use o comando do Lync ServerWindows PowerShell, New-CsRoutingConfiguration, para habilitar o Roteamento com Base no Local.

    Set-CsRoutingConfiguration -EnableLocationBasedRouting $true

Para obter mais informações, consulte [Set-CsRoutingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRoutingConfiguration).

> [!NOTE]  
> embora o Roteamento com Base no Local deva ser habilitado via configuração global, o conjunto de regras a ser aplicado só será imposto aos sites, usuários e troncos para os quais ele foi configurado como especificado nesta documentação.


## Consulte Também

#### Outros Recursos

[Configurando o Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-configuring-location-based-routing.md)

