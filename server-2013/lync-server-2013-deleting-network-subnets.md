---
title: Excluir subredes
TOCTitle: Excluir subredes
ms:assetid: c1850f38-40a3-48c9-b6f1-f181c5e63b6b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721873(v=OCS.15)
ms:contentKeyID: 49886392
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir subredes

 

_**Tópico modificado em:** 2013-02-21_

É possível usar o seguinte procedimento para excluir uma subrede. No Painel de Controle do Lync Server, é possível criar, modificar ou excluir uma subrede. Para obter detalhes sobre como criar ou modificar subredes, consulte [Criar ou modificar subredes](lync-server-2013-create-or-modify-network-subnets.md)

Na maioria das implantações do Microsoft Lync Server 2013 onde o controle de admissão de chamada (CAC) está implementado, existem geralmente um grande número de subredes. Por causa disso, é frequentemente melhor configurar subredes do Shell de Gerenciamento do Lync Server. Desde local, é possível chamar o **New-CsNetworkSubnet** em conjunto com o cmdlet Windows PowerShell**Import-CSV**. Usando estes cmdlets em conjunto, é possível ler nas configurações de subrede de um arquivo de valores separados por vírgula (.csv) e criar várias subredes ao mesmo tempo. Para ver exemplos de como criar subredes de um arquivo .csv, consulte [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet).

## Para excluir uma subrede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da rede** e clique em **Sub-rede**.

4.  Na página **Subrede**, clique na subrede que deseja excluir.
    
    > [!NOTE]  
    > Você pode excluir mais de uma subrede simultaneamente. Para isso, pressione a tecla CTRL e selecione várias subredes mantendo a tecla CTRL pressionada. Em alternativa, para selecionar todas as subredes, clique em <strong>Selecionar todas</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.

## Consulte Também

#### Tarefas

[Criar ou modificar subredes](lync-server-2013-create-or-modify-network-subnets.md)

