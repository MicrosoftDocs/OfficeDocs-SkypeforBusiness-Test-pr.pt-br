---
title: Adicionar uma política de local para um site local no Lync Server 2013
TOCTitle: Adicionar uma política de local para um site local no Lync Server 2013
ms:assetid: 43bfab8a-3d6b-4ca4-8425-879fd910502e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425936(v=OCS.15)
ms:contentKeyID: 49306539
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar uma política de local para um site local no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-24_

Os exemplos a seguir mostram como adicionar a política de local **Redmond**, definida em [Criar políticas de localização no Lync Server 2013](lync-server-2013-create-location-policies.md), a um site de rede existente e como criar um novo site de rede que use a política de local **Redmond**.

Para obter detalhes sobre como trabalhar com sites de rede, consulte a documentação do Shell de Gerenciamento do Lync Server para os cmdlets a seguir:

  - **New-CsNetworkSite**

  - **Get-CsNetworkSite**

  - **Set-CsNetworkSite**

  - **Remove-CsNetworkSite**

## Para atribuir uma política de local a um site de rede existente

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute os cmdlets a seguir para modificar um site de rede existente.
    
    Atribua a política de Local marcada **Redmond** a um site de rede existente denominado **Redmond**.
    
        Set-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"

## Para atribuir uma política de local a um novo site de rede

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o seguinte cmdlet para criar um novo site de rede.
    
    Crie um novo site de rede na região de rede e atribua a política de local marcada **Redmond**.
    
        New-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"

