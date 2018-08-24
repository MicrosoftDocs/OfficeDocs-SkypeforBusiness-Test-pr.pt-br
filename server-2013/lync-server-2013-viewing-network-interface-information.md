---
title: Visualizando informações de interface de rede
TOCTitle: Visualizando informações de interface de rede
ms:assetid: e7dbb1ec-62b3-48be-a419-c493df5740e6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721916(v=OCS.15)
ms:contentKeyID: 49886455
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de interface de rede

 

_**Tópico modificado em:** 2013-02-23_

## Visualizando Informações de Interface de Rede Usando os Cmdlets do Shell de Gerenciamento do Lync Server

Você pode visualizar informações de interface de rede usando os cmdlet Shell de Gerenciamento do Lync Server e **Get-CsNetworkInterface**. Você pode executar este cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar informações de interface de rede

  - Para visualizar informações de interface de rede, digite o comando a seguir no Shell de Gerenciamento do Lync Server e então pressione ENTER:
    
        Get-CsNetworkInterface
    
    Esse comando retorna informações similares as seguintes para cada interface de rede:
    
        Identity              : dc.vdomain.com/Primary/1
        ComputerFqdn          : dc.vdomain.com
        IPAddress             : 0.0.0.0
        IPv6Address           :
        Interface             : Primary
        InterfaceNumber       : 1
        ConfiguredFqdn        :
        ConfiguredIPAddress   :
        ConfiguredIPv6Address :

Para obter detalhes, consulte [Get-CsNetworkInterface](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterface).

