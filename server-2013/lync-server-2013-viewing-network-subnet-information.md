---
title: Visualizando informações de subrede
TOCTitle: Visualizando informações de subrede
ms:assetid: 46f165f2-efe3-4cc1-9fee-a78b7f2ed41e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688044(v=OCS.15)
ms:contentKeyID: 49886203
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de subrede

 

_**Tópico modificado em:** 2013-02-23_

Você pode utilizar o seguinte procedimento para visualizar uma sub-rede da rede. Do Painel de Controle do Lync Server, você pode criar, modificar ou excluir uma sub-rede da rede. Para detalhes sobre a criação ou modificação de sub-redes de rede, consulte [Criar ou modificar subredes](lync-server-2013-create-or-modify-network-subnets.md).

## Para visualizar uma sub-rede de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e, então, em **Sub-rede**.

4.  Na página de **Sub-rede**, clique na sub-rede que deseja visualizar.
    
    > [!NOTE]  
    > Você só pode visualizar uma sub-rede por vez.

5.  No menu **Editar**, clique em **Exibir detalhes…**.

## Visualizando informação de configuração de sub-rede da rede utilizando os cmdlets do Lync Server PowerShell

Informações de sub-rede da rede também podem ser visualizadas utilizando o Lync Server PowerShell e o cmdlet Get-CsNetworkSubnet. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Visualizando informações de sub-rede da rede

  - Para visualizar informações sobre todas as sub-redes da rede, digite o comando a seguir no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkSubnet
    
    Isso irá retornar uma informação similar a esta:
    
        Identity      : 172.11.15.0
        MaskBits      : 28
        Description   :
        NetworkSiteID : Redmond
        SubnetID      : 172.11.15.0

Para mais informações, consulte o tópico de ajuda para o cmdlet [Get-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSubnet).

## Consulte Também

#### Tarefas

[Criar ou modificar subredes](lync-server-2013-create-or-modify-network-subnets.md)  
[Excluir subredes](lync-server-2013-deleting-network-subnets.md)

