---
title: Visualizando informações de link da região de rede
TOCTitle: Visualizando informações de link da região de rede
ms:assetid: 7b6b2ea2-83d8-4376-afb2-70e5d2cf6444
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688102(v=OCS.15)
ms:contentKeyID: 49886276
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de link da região de rede

 

_**Tópico modificado em:** 2013-02-23_

Você pode visualizar os links entre duas regiões de redes como parte do controle de admissão de chamadas (CAC). Regiões dentro de uma rede são vinculadas por conectividade de WAN física. Você pode usar o Painel de Controle do Lync Server para ver um link existente entre duas regiões de rede. Para detalhes sobre como criar ou modificar um link de região de rede, consulte [Configurando links da região de rede](lync-server-2013-configuring-network-region-links.md).

## Para ver um link de região de rede em Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração da rede** e em **Link da região**.

4.  Na página **Link da região**, clique no link da região que você deseja ver.
    
    > [!NOTE]  
    > Você pode ver informações somente sobre um link da região por vez.

5.  No menu**Editar**, selecione **Mostras detalhes**.

## Visualizar Informações do Link de Região de rede Usando Shell de Gerenciamento do Lync Server Cmdlets

Você também pode visualizar links de região de rede usando Shell de Gerenciamento do Lync Server e **Get-CsNetworkRegionLink** cmdlet. Você pode executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ver informações do link de região de rede

  - Para ver informações sobre todos os links de região de rede, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkRegionLink
    
    Esse comando retorna informações semelhantes às seguintes:
    
        Identity            : NorthwestToCalifornia
        BWPolicyProfileID   :
        NetworkRegionLinkID : NorthwestToCalifornia
        NetworkRegionID1    : Pacific Northwest
        NetworkRegionID2    : California

Para detalhes, consulte [Get-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink).

## Consulte Também

#### Tarefas

[Configurando links locais de rede](lync-server-2013-configuring-network-site-links.md)

