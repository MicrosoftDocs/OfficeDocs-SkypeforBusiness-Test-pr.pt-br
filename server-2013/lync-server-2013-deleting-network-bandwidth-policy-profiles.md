---
title: Excluindo perfis da política de largura de banda da rede
TOCTitle: Excluindo perfis da política de largura de banda da rede
ms:assetid: 4d6beda8-6aa5-4d5e-8a07-363598f0e0c8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688050(v=OCS.15)
ms:contentKeyID: 49886215
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo perfis da política de largura de banda da rede

 

_**Tópico modificado em:** 2012-11-01_

Como parte do controle de admissão de chamadas (CAC), é usada uma política de largura de banda para definir os limites de largura de banda para algumas modalidades. No Microsoft Lync Server 2013, apenas as modalidades de áudio e vídeo podem ter limites de bandas atribuídos. Você pode configurar os limites gerais de banda e os limites de sessão. Você pode usar o Painel de Controle do Lync Server para criar, modificar ou excluir um perfil de contêiner para essas políticas. Use os seguintes procedimentos para excluir um perfil de política de largura de banda de rede. Para obter informações detalhadas sobre como criar ou modificar um perfil de política de largura de banda de rede, consulte [Criar ou modificar perfis da política de largura de banda](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md).

## Para excluir um perfil de política de largura de banda

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e, em seguida, clique em **Política de largura de banda**.

4.  Na página **Política de largura de banda**, clique no perfil de política de largura de banda que você deseja excluir.
    
    > [!NOTE]  
    > Você pode excluir mais de um perfil por vez. Para isso, pressione CTRL e selecione vários perfis mantendo a tecla CTRL pressionada. Ou, para selecionar perfis, clique em <strong>Selecionar tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.
    

    > [!WARNING]
    > Você não pode excluir um perfil de política de largura de banda que esteja associado a um site da rede. É preciso primeiro remover a associação com o site antes de poder excluir o perfil. Para obter informações mais detalhadas sobre como modificar um site da rede, consulte <A href="lync-server-2013-creating-or-modifying-network-sites.md">Criar ou modificar sites de rede</A>.



## Consulte Também

#### Tarefas

[Criar ou modificar perfis da política de largura de banda](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)  
[Visualizando informações de perfil de política de largura de banda](lync-server-2013-viewing-network-bandwidth-policy-profile-information.md)  

#### Outros Recursos

[Configurar controle de admissão de chamada no Lync Server 2013](lync-server-2013-configure-call-admission-control.md)  
[Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)

