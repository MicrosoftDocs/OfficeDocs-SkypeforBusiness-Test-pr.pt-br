---
title: Criar ou modificar perfis da política de largura de banda
TOCTitle: Criar ou modificar perfis da política de largura de banda
ms:assetid: 08a2e18f-9b0d-4a2f-aa14-13bbf79ec745
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520945(v=OCS.15)
ms:contentKeyID: 49305805
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar perfis da política de largura de banda

 

_**Tópico modificado em:** 2012-10-15_

Como parte do serviço de controle de admissão de chamadas (CAC), utiliza-se uma política de largura de banda para definir as limitações de largura de banda para determinadas modalidades. No Microsoft Lync Server 2013, as limitações de largura de banda podem ser atribuídas apenas às modalidades de áudio e vídeo. Você pode definir limitações gerais de largura de banda e limitações para as sessões. É possível usar o Painel de Controle do Lync Server para criar ou modificar um perfil de contêiner para essas políticas. Cada perfil de política de largura de banda pode ser associado a um ou mais sites de rede. Para excluir um perfil de política de largura de banda, consulte [Excluindo perfis da política de largura de banda da rede](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)

## Para criar um novo perfil de política de largura de banda

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de Rede** e depois em **Política de largura de banda**.

4.  Na página **Política de largura de banda**, clique em **Novo**.

5.  Em **Novo Perfil de Política de Largura de Banda**, digite um nome no campo **Nome**. Esse nome deve ser único entre todos os perfis de política de largura de banda.

6.  No campo **Limite de áudio**, digite um valor numérico. Esse valor é a quantidade máxima de largura de banda a ser alocada a todas as conexões de áudio, expressa em kbps.

7.  Insira um valor numérico no campo **Limite da sessão de áudio**. Esse valor é a quantidade máxima de largura de banda a ser alocada para uma conexão de áudio individual, expressa em kbps. Esse valor precisa ser igual a ou maior que 40.

8.  Insira um valor numérico no campo **Limite de vídeo**. Esse valor é quantidade máxima de largura de banda a ser alocada para todas as conexões de vídeo, expressa em kbps.

9.  Insira um valor numérico no campo **Limite de sessão de vídeo**. Esse valor é a quantidade máxima de largura de banda a ser alocada para uma conexão de vídeo individual, expressa em kbps. Esse valor precisa ser igual a ou maior que 100.

10. (Opcional) Digite um valor no campo **Descrição** para fornecer mais informações sobre esse perfil da política de largura de banda que não pode ser expressa somente pelo nome.

11. Clique em **Confirmar**.
    
    > [!NOTE]  
    > Criar um novo perfil de política de largura de banda não reforça as restrições de largura de banda automaticamente. É preciso, primeiro, associar o perfil da política com um site. Para obter mais detalhes sobre como associar um perfil de política com um site, consulte <a href="lync-server-2013-creating-or-modifying-network-sites.md">Criar ou modificar sites de rede</a>.

## Para modificar um perfil de política de largura de banda

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e clique em **Política de largura de banda**.

4.  Na página **Política de largura de banda**, clique no perfil da política de largura de banda que você quer modificar.

5.  No menu **Editar**, clique em **Mostrar detalhes**.

6.  Na página **Editar Perfil de Política de Largura de Banda**, modifique os campos conforme necessário (para obter mais detalhes, consulte a seção "Para criar um novo perfil de política de largura de banda", já vista neste tópico).

7.  Clique em **Confirmar**.
    
    > [!NOTE]  
    > Ao modificar o perfil de política de largura de banda, as limitações de largura de banda de todos os sites da rede associados a esse perfil serão atualizadas imediatamente.

## Consulte Também

#### Tarefas

[Excluindo perfis da política de largura de banda da rede](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)  

#### Outros Recursos

[Configurar controle de admissão de chamada no Lync Server 2013](lync-server-2013-configure-call-admission-control.md)  
[New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkBandwidthPolicyProfile)  
[Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkBandwidthPolicyProfile)  
[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

