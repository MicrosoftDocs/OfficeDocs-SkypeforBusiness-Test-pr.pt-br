---
title: Configurar regiões de rede para CAC no Lync Server 2013
TOCTitle: Configurar regiões de rede para CAC no Lync Server 2013
ms:assetid: ea3ff988-dd5a-4bc4-bec5-39a0fb09793a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399051(v=OCS.15)
ms:contentKeyID: 49308480
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar regiões de rede para CAC no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

> [!IMPORTANT]  
> Se você já tiver criado regiões de rede para E9-1-1 ou desvio de mídia, você pode modificar as regiões de rede existentes adicionando configurações específicas ao controle de admissão de chamadas usando o cmdlet <strong>Set-CsNetworkRegion</strong>. Para ver um exemplo de como modificar uma região de rede, consulte <a href="lync-server-2013-create-or-modify-a-network-region.md">Criar ou modificar uma região de rede no Lync Server 2013</a>.

*Regiões de rede* são hubs de rede ou backbones usados na configuração do CAC (controle de admissão de chamadas), E9-1-1 e desvio de mídia. Use os procedimentos a seguir para criar regiões de rede que alinham as regiões de rede no exemplo de topologia de rede para CAC. Para exibir o exemplo de topologia de rede, consulte [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) na documentação Planejamento.

O exemplo de topologia de rede para CAC tem três regiões: América do Norte, EMEA e APAC. Cada região tem um site central especificado. Para a região da América do Norte, o site central designado é chamado CHICAGO. O procedimento a seguir mostra um exemplo de como é possível usar o cmdlet **New-CsNetworkRegion** para criar a região América do Norte.

> [!NOTE]  
> No procedimento a seguir, o Shell de Gerenciamento do Lync Server é usado para criar uma região de rede. Para obter detalhes sobre como usar o Painel de Controle do Lync Server para criar uma região de rede, consulte <a href="lync-server-2013-create-or-modify-a-network-region.md">Criar ou modificar uma região de rede no Lync Server 2013</a>.

## Para criar uma região de rede para controle de admissão de chamada

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para cada região que você precisa criar, execute o cmdlet **New-CsNetworkRegion**. Por exemplo, para criar a região América do Norte, execute:
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"

3.  Repita a etapa 2 para criar as regiões de rede EMEA e APAC.

