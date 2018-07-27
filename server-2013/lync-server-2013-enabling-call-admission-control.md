---
title: Habilitando o controle de admissão de chamada
TOCTitle: Habilitando o controle de admissão de chamada
ms:assetid: 015f5c8f-2f90-4b9e-8149-b33767e90582
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520942(v=OCS.15)
ms:contentKeyID: 49305672
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando o controle de admissão de chamada

 

_**Tópico modificado em:** 2012-11-01_

O serviço de controle de admissão de chamadas (CAC) é uma rede de regiões, sites e sub-redes que permite impor restrições às transmissões de áudio e vídeo com base na largura de banda disponível. Após configurar a rede CAC, habilite o CAC para impor as limitações de largura de banda. Isso pode ser feito no Painel de Controle do Lync Server.

## Para ativar CAC de Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de Rede** e então clique em **Global**.

4.  Na página **Global**, clique na configuração **Global**.
    
    > [!NOTE]  
    > Apenas uma rede pode ser configurada para qualquer implantação Microsoft Lync Server 2013, portanto nunca haverá mais do que uma configuração de rede na lista. Você não pode renomear a configuração Global.

5.  No menu **Editar**, clique em **Mostrar detalhes**.

6.  Na página **Editar Configuração Global**, marque a caixa de seleção **Habilitar controle de admissão de chamadas** e então clique em **Confirmar**.

Quando você clica em **Confirmar**, você executa um teste da configuração. A caixa de diálogo **Editar Configurações Globais** é fechada, retornando você à página **Global**. Você receberá uma viso sobre qualquer erro ou inconsistência descoberta em sua configuração de rede que a impeça de funcionar corretamente (por exemplo, se cada região não estiver conectada às outras regiões através de uma rota intrarregional).

Caso faça alterações em sua configuração de rede, você pode executar a verificação de validação novamente abrindo a configuração Global e clicando em **Confirmar**. Você não precisa desativar o CAC primeiro: deixe a caixa de seleção marcada e clique em **Confirmar**. Você pode fazer isso a qualquer hora sem fazer nenhuma alteração na configuração.

## Consulte Também

#### Conceitos

[Visão geral do controle de admissão de chamada no Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md)  

#### Outros Recursos

[Planejamento para controle de admissão de chamada no Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md)  
[Configurar controle de admissão de chamada no Lync Server 2013](lync-server-2013-configure-call-admission-control.md)  
[Get-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkConfiguration)  
[Set-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkConfiguration)  
[Remove-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkConfiguration)

