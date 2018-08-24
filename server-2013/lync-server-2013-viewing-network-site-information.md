---
title: Visualizando informações de site de rede
TOCTitle: Visualizando informações de site de rede
ms:assetid: 24a97d98-b168-4016-81bf-c2c478092b87
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687996(v=OCS.15)
ms:contentKeyID: 49886137
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de site de rede

 

_**Tópico modificado em:** 2013-02-23_

Os sites de rede são escritórios ou locais configurados dentro de cada região de um controle de admissão de chamada (CAC) ou implantação de 9-1-1 Avançado. É possível exibir informações do local de rede no Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server. Para obter detalhes sobre a criação ou modificação de locais de rede, consulte [Criar ou modificar sites de rede](lync-server-2013-creating-or-modifying-network-sites.md).

## Para exibir informações do local de rede no Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de rede** e em **Local**.

4.  Na página **Local**, clique no local que deseja exibir.
    
    > [!NOTE]  
    > É possível exibir apenas informações de um local por vez.

5.  No menu **Editar**, clique em **Exibir detalhes**.

## Para exibir a informação do site de rede usando os cmdlets Shell de Gerenciamento do Lync Server

É possível exibir informações do local de rede usando o cmdlet Get-CsNetworkSite. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para exibir a informação do local de rede

  - Para exibir informações sobre todos os locais de rede, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkSite
    
    Isto retornará informações semelhantes a seguinte:
    
        Identity          : Redmond
        NetworkSiteID     : Redmond
        Description       :
        NetworkRegionID   : Pacific Northwest
        BypassID          : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        BWPolicyProfileID :
        LocationPolicy    :

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Get-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSite).

## Consulte Também

#### Tarefas

[Criar ou modificar sites de rede](lync-server-2013-creating-or-modifying-network-sites.md)  
[Excluir um site de rede existente](lync-server-2013-deleting-an-existing-network-site.md)

