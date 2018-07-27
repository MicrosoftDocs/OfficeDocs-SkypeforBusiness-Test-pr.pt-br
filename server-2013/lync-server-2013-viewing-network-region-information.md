---
title: Visualizando informações da região de rede
TOCTitle: Visualizando informações da região de rede
ms:assetid: 665740d0-a3ed-460f-8337-5ed945f90589
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688076(v=OCS.15)
ms:contentKeyID: 49886243
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações da região de rede

 

_**Tópico modificado em:** 2013-02-23_

Uma região de rede interconecta várias partes de uma rede de diversas áreas geográficas. Cada região de rede deve ser associada a um site central. O site central é o site de datacenter no qual o serviço de política de largura de banda CAC (controle de admissão de chamadas) está sendo executado. É possível usar o Painel de Controle do Lync Server para exibir as regiões de rede. As regiões de rede incluem configurações que determinam se caminhos alternativos pela Internet são permitidos para conexões de áudio e vídeo. Use este tópico para exibir as regiões de rede existentes. Para obter detalhes sobre como criar e modificar regiões de rede existentes, consulte [Criar ou modificar regiões de rede](lync-server-2013-creating-or-modifying-network-regions.md).

## Para exibir informações sobre uma região de rede com o Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de Rede** e depois em **Região**.

4.  Na página **Região**, clique na região que deseja exibir.
    
    > [!NOTE]  
    > É possível exibir apenas uma região por vez.

5.  No menu **Editar**, clique em **Mostrar detalhes**.

## Exibindo informações de regiões de rede usando os cmdlets do Windows PowerShell

Você pode visualizar as informações de regiões de rede usando o Windows PowerShell e o cmdlet **Get-CsNetworkRegion**. Ele pode executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar as informações de regiões de rede

  - Para exibir informações sobre todas as regiões de rede, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkRegion
    
    Isso retornará informações semelhantes às seguintes:
    
        Identity         : Pacific Northwest
        Description      :
        BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        CentralSite      : Site:Redmond1
        BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                           BWPolicyModality=Video;AlternatePath=True}
        NetworkRegionID  : Pacific Northwest

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink).

## Consulte Também

#### Tarefas

[Criar ou modificar regiões de rede](lync-server-2013-creating-or-modifying-network-regions.md)  
[Excluindo regiões de rede existentes](lync-server-2013-deleting-existing-network-regions.md)

