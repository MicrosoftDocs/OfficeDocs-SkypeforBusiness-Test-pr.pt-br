---
title: Excluindo rotas da região de rede existentes
TOCTitle: Excluindo rotas da região de rede existentes
ms:assetid: 6256ff80-5f1e-48b4-928b-24aeb3c1a0e7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688074(v=OCS.15)
ms:contentKeyID: 49886240
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo rotas da região de rede existentes

 

_**Tópico modificado em:** 2012-11-01_

Cada região de uma configuração de CAC (controle de admissão de chamadas) deve ter alguma maneira de acessar todas as outras regiões. Enquanto os links de regiões definem limitações de largura de banda nas conexões entre regiões e também representam os links físicos, uma rota determina qual caminho vinculado a conexão percorrerá de uma região para a outra. Você pode usar o Painel de Controle do Lync Server para configurar as rotas de região de rede. No Painel de Controle do Lync Server, você pode criar, modificar ou excluir uma rota de região de rede. Use este tópico para excluir rotas de região de rede existentes. Para obter detalhes sobre como criar ou modificar rotas de região de rede, consulte [Criar ou modificar rotas da região de rede](lync-server-2013-creating-or-modifying-network-region-routes.md).

## Para excluir uma rota de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de Rede** e depois em **Rota de Região**.

4.  Na página **Rota de Região**, clique na rota de região que deseja excluir.
    
    > [!NOTE]  
    > Você pode excluir mais de uma rota de região por vez. Para fazer isso, pressione CTRL e selecione várias rotas de região mantendo pressionada a tecla CTRL. Para selecionar todas as rotas da região, clique em <strong>Selecionar tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.

## Consulte Também

#### Tarefas

[Criar ou modificar rotas da região de rede](lync-server-2013-creating-or-modifying-network-region-routes.md)  

#### Conceitos

[Configurar uma Rota de Região de Rede](https://technet.microsoft.com/pt-br/library/gg133706\(v=ocs.15\))  

#### Outros Recursos

[New-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterRegionRoute)  
[Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterRegionRoute)  
[Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterRegionRoute)  
[Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute)

