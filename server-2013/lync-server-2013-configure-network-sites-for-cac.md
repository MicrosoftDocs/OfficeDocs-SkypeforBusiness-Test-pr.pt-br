---
title: Configurar locais de rede para CAC no Lync Server 2013
TOCTitle: Configurar locais de rede para CAC no Lync Server 2013
ms:assetid: afcea38f-5789-45ec-97af-c6e38364950c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412840(v=OCS.15)
ms:contentKeyID: 49307795
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar locais de rede para CAC no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

> [!IMPORTANT]  
> Se você já criou sites de rede para 9-1-1 avançado ou desvio de mídia, é possível modificar os sites de rede existentes para aplicar um perfil de política de largura de banda usando o cmdlet <strong>Set-CsNetworkSite</strong>. . Para um exemplo de como modificar um site de rede, consulte <a href="lync-server-2013-create-or-modify-a-network-site.md">Criar ou modificar um site da rede no Lync Server 2013</a>.

*Sites de rede* são os escritórios ou locais dentro de cada região de rede de implantações de controle de admissão de chamadas (CAC), E9-1-1 e desvio de mídia. Use os procedimentos a seguir para criar sites de rede que se alinham a sites de rede na topologia de rede de exemplo para CAC. Estes procedimentos mostram como criar e configurar sites de rede que são restringidos pela largura de banda da WAN e, portanto, requerem políticas de largura de banda que limitam o fluxo do tráfego de áudio e vídeo em tempo real.

Na implantação de CAC de exemplo, a região América do Norte possui seis sites. Três deles são restringidos pela largura de banda da WAN: Reno, Portland e Albuquerque. Os outros três que *não* são restringidos pela largura de banda da WAN: Nova York, Chicago e Detroit. Para um exemplo de como criar ou modificar estes outros site de rede, consulte [Criar ou modificar um site da rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md).

Para exibir a topologia de rede de exemplo, consulte [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) na documentação de Planejamento.

> [!NOTE]  
> No procedimento a seguir, o Shell de Gerenciamento do Lync Server é usado para criar um site de rede. Para obter detalhes sobre como usar o Painel de Controle do Lync Server para criar um site de rede, consulte <a href="lync-server-2013-create-or-modify-a-network-site.md">Criar ou modificar um site da rede no Lync Server 2013</a>.

## Para criar sites de rede para controle de admissão de chamadas

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsNetworkSite** para criar sites de rede e aplicar um perfil de política de largura de banda para cada site. Por exemplo, execute:
    
```
        New-CsNetworkSite -NetworkSiteID Reno -Description "NA:Branch office for sales force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 10MB_Link
```
```    
        New-CsNetworkSite -NetworkSiteID Portland -Description "NA:Branch office for marketing force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 5MB_Link
```
```    
        New-CsNetworkSite -NetworkSiteID Albuquerque -Description "NA:Branch office for SouthWest sales" -NetworkRegionID EMEA -BWPolicyProfileID 10MB_Link
```

3.  Para concluir a criação de sites de rede para a topologia de exemplo, repita a etapa 2 para os sites de rede com restrição de largura de banda nas regiões EMEA e APAC.

