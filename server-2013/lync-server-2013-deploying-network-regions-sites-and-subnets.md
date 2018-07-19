---
title: Implantação de regiões de rede, sites e sub-redes no Lync Server 2013
TOCTitle: Implantação de regiões de rede, sites e sub-redes no Lync Server 2013
ms:assetid: c4b75601-3538-4d07-8d23-1ad90459ae48
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994067(v=OCS.15)
ms:contentKeyID: 52057707
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantação de regiões de rede, sites e sub-redes no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Uma vez que o Enterprise Voice é implementado, você precisa configurar:

  - Regiões da rede

  - Locais da rede

  - Sub-redes de rede

## Definir regiões de rede

Use o comando Lync ServerWindows PowerShell, New-CsNetworkRegion ou Painel de Controle do Lync Server para definir as regiões da rede.

    New-CsNetworkRegion -NetworkRegionID <region ID> -CentralSite <site ID>

Para obter mais informações consulte [New-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegion).

Para esse exemplo, o seguinte comando Windows PowerShell ilustra a região da rede, região 1 (Índia), definida nesse cenário.

    New-CsNetworkRegion -NetworkRegionID "India" -CentralSite "India Central Site"


## Definir Locais da Rede

Use o comando Lync ServerWindows PowerShell, New-CsNetworkSite ou o Painel de Controle do Lync Server para definir os locais da rede.

    New-CsNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>

Para obter mais informações consulte [New-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSite).

Para esse exemplo, a seguinte tabela e o comando Lync ServerWindows PowerShell ilustram os locais da rede definidos nesse cenário. Somente as configurações que são específicas para o Roteamento com Base no Local são incluídas na tabela para fins ilustrativos.

    New-CsNetworkSite -NetworkSiteID "Delhi" -NetworkRegionID "India"
    New-CsNetworkSite -NetworkSiteID "Hyderabad" -NetworkRegionID "India"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Local 1 (Délhi)</th>
<th>Local 2 (Híderabade)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ID do Local</p></td>
<td><p>Local 1 (Délhi)</p></td>
<td><p>Local 2 (Hiderabade)</p></td>
</tr>
<tr class="even">
<td><p>ID da Região</p></td>
<td><p>Região 1 (Índia)</p></td>
<td><p>Região 1 (Índia)</p></td>
</tr>
</tbody>
</table>



## Definir Sub-redes de Redes

Use o comando Lync ServerWindows PowerShell, New-CsNetworkSubne, ou o Painel de Controle do Lync Server para definir as sub-redes de redes e atribuí-las aos locais da rede.

    New-CsNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>

Para obter mais informações consulte [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet).

Para esse exemplo, a seguinte tabela e o comando Windows PowerShell ilustram a atribuição de sub-redes de redes para os locais da rede, Délhi e Híderabade, definidos nesse cenário. Somente as configurações que são específicas para o Roteamento com Base no Local são incluídas na tabela para fins ilustrativos.

    New-CsNetworkSubnet -SubnetID "192.168.0.0" -MaskBits "24" -NetworkSiteID "Delhi"
    New-CsNetworkSubnet -SubnetID "192.168.1.0" -MaskBits "24" -NetworkSiteID "Hyderabad"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Local 1 (Délhi)</th>
<th>Local 2 (Hiderabade)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ID da sub-rede</p></td>
<td><p>192.168.0.0</p></td>
<td><p>192.168.1.0</p></td>
</tr>
<tr class="even">
<td><p>Máscara</p></td>
<td><p>24</p></td>
<td><p>24</p></td>
</tr>
<tr class="odd">
<td><p>ID do Local</p></td>
<td><p>Local 1 (Délhi)</p></td>
<td><p>Local 2 (Híderabade)</p></td>
</tr>
</tbody>
</table>



## Consulte Também

#### Outros Recursos

[Configurando o Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-configuring-location-based-routing.md)

