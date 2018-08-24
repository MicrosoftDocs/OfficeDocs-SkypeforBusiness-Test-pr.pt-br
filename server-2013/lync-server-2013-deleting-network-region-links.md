---
title: Excluindo links da região de rede
TOCTitle: Excluindo links da região de rede
ms:assetid: 839273cd-d23f-4b38-84e6-d2dc972f49cd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688114(v=OCS.15)
ms:contentKeyID: 49886293
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo links da região de rede

 

_**Tópico modificado em:** 2012-11-01_

É possível configurar links entre duas regiões da rede como parte do serviço de controle de admissão de chamadas (CAC). As regiões da rede são vinculadas por meio de conectividade WAN física. É possível usar Painel de Controle do Lync Server para excluir links existentes entre duas regiões derede. Paraobter mais detalhes sobre como criar ou modificar um link de região de rede, consulte [Configurando links da região de rede](lync-server-2013-configuring-network-region-links.md)

## Para excluir links de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da rede** e, em seguida, em **Links de região**.

4.  Na página **Links de região**, clique no link deregião que deseja excluir.
    
    > [!NOTE]  
    > É possível excluir mais de um link de região de uma vez. Para isso, mantenha a tecla CTRL pressionada e selecione vários links de região. Para selecionar todos os links de região, clique em <strong>Selecionar todos</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, selecione **Excluir**.

6.  Clique em **OK**.

## Consulte Também

#### Tarefas

[Configurando links da região de rede](lync-server-2013-configuring-network-region-links.md)

