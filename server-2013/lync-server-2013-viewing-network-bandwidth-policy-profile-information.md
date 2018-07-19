---
title: Visualizando informações de perfil de política de largura de banda
TOCTitle: Visualizando informações de perfil de política de largura de banda
ms:assetid: eed453fc-04e9-4971-959c-6fad54bf1c96
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721931(v=OCS.15)
ms:contentKeyID: 49886471
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de perfil de política de largura de banda

 

_**Tópico modificado em:** 2013-02-23_

Como parte do Controle de Admissão de Chamadas (CAC), uma política de largura de banda é usada para definir as limitações de largura de banda de determinadas modalidades. No Microsoft Lync Server 2013, somente as modalidades de áudio e vídeo podem ter limitações de largura de banda. É possível definir limitações gerais de largura de banda e de sessão. Você pode usar o Painel de Controle do Lync Server para criar, modificar ou excluir um perfil contêiner destas políticas. Cada perfil de política de largura de banda pode ser associado com um ou mais sites da rede. Use os procedimentos a seguir para exibir um perfil de política de largura de banda. Para criar ou modificar um perfil de política de largura de banda, consulte [Criar ou modificar perfis da política de largura de banda](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md).

## Para modificar um perfil de política de largura de banda

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  No menu de navegação à esquerda, clique em **Configuração de Rede** e depois em **Política de Largura de Banda**.

4.  Na página **Política de Largura de Banda**, clique no perfil da política de largura de banda que deseja modificar.

5.  No menu **Editar**, clique em **Exibir detalhes**.

## Exibindo Informações de Perfis de Política de Largura de Banda Usando os Cmdlets do Lync Server PowerShell

Os perfis de largura de banda da rede também podem ser exibidos usando o Lync Server PowerShell e o cmdlet Get-CsNetworkBandwidthPolicyProfile. Esse cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibindo Informações de Perfis de Política de Largura de Banda da Rede

  - Para exibir informações sobre todos os perfis de política de largura de banda da rede, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsNetworkBandwidthPolicyProfile
    
    Isso retornará informações parecidas com:
    
        Identity          : RedmondBandwidthPolicy
        BWPolicy          : {BWLimit=200;BWSessionLimit=200;
                            BWPolicyModality=Audio, 
                            BWLimit=1400;BWSessionLimit=500;
                            BWPolicyModality=Video}
        BWPolicyProfileID : RedmondBandwidthPolicy
        Description       :

Para obter mais informações, consulte o tópico do cmdlet [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile).

## Consulte Também

#### Tarefas

[Criar ou modificar perfis da política de largura de banda](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)  
[Excluindo perfis da política de largura de banda da rede](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)  

#### Outros Recursos

[Configurar controle de admissão de chamada no Lync Server 2013](lync-server-2013-configure-call-admission-control.md)

