---
title: Visualizando informações de rota da região de rede
TOCTitle: Visualizando informações de rota da região de rede
ms:assetid: 34dd9fa3-e695-4680-b244-3019298b5009
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688021(v=OCS.15)
ms:contentKeyID: 49886175
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de rota da região de rede

 

_**Tópico modificado em:** 2013-02-23_

Cada região de um configuração de CAC (controle de admissão de chamadas) deve ter alguma forma de acessar todas as outras regiões. Enquanto os links da região definem limitações nas conexões entre regiões e representam também os links físicos, uma rota determina o caminho vinculado que a conexão percorrerá de uma região a outra. Use os procedimentos a seguir para exibir as rotas existentes de região de rede no Painel de Controle do Lync Server 2013 ou no Shell de Gerenciamento do Lync Server 2013. Para obter detalhes sobre a criação ou modificação de rotas de região de rede, consulte [Criar ou modificar rotas da região de rede](lync-server-2013-creating-or-modifying-network-region-routes.md).

## Para exibir informações sobre a rota de região de rede no Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração da Rede** e clique em **Rota de Região**.

4.  Na página **Rota de Região**, clique na rota de região que deseja exibir.
    
    > [!NOTE]  
    > É possível ver apenas uma rota de região por vez.

5.  No menu **Editar**, clique em **Mostrar detalhes**.

## Exibindo informações sobre a rota de região de rede usando os cmdlets do Lync Server PowerShell

As informações sobre a rota de região de rede também podem ser exibidas usando o Lync Server PowerShell e o cmdlet Get-CsNetworkInterRegionRoute. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibindo informações sobre a rota de região de rede

  - Para exibir informações sobre todas as rotas de região de rede, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkInterRegionRoute
    
    Isso retornará informações semelhantes ao que segue:
    
        Identity                  : TransAmericaRoute
        NetworkRegionLinks        : {NorthwestToNortheast}
        InterNetworkRegionRouteID : TransAmericaRoute
        NetworkRegionID1          : Pacific Northwest
        NetworkRegionID2          : Northeast

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute).

## Consulte Também

#### Tarefas

[Criar ou modificar rotas da região de rede](lync-server-2013-creating-or-modifying-network-region-routes.md)  
[Excluindo rotas da região de rede existentes](lync-server-2013-deleting-existing-network-region-routes.md)

