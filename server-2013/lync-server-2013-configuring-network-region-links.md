---
title: Configurando links da região de rede
TOCTitle: Configurando links da região de rede
ms:assetid: 952bc93e-e6aa-4539-85c7-2b15f14eb382
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182551(v=OCS.15)
ms:contentKeyID: 49307500
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando links da região de rede

 

_**Tópico modificado em:** 2012-11-01_

Você pode configurar links entre duas regiões de rede como parte do controle de admissão de chamadas. Regiões dentro de uma rede são vinculadas por conectividade de WAN física. Você pode usar o Painel de Controle do Lync Server para definir um link entre duas regiões de rede e definir as limitações de largura de banda em conexões de áudio e vídeo entre essas regiões. Para obter detalhes sobre a exclusão de um link de região de rede existente, consulte [Excluindo links da região de rede](lync-server-2013-deleting-network-region-links.md).

## Para criar um link de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de Rede** e em **Link de Região**.

4.  Na página **Link de Região**, clique em **Novo**.

5.  Em **Novo Link de Região**, digite um valor no campo **Nome**.
    
    > [!NOTE]  
    > Este valor deve ser único em sua implantação do Lync Server 2013.

6.  Na lista suspensa **Região de rede \#1**, selecione uma das duas regiões a serem vinculadas.

7.  Na lista suspensa **Região de rede \#2**, selecione a outra região a ser vinculada. Esta deve ser diferente da região selecionada como Região de rede \#1.

8.  (Opcional) Se você desejar colocar limites de largura de banda em chamadas de áudio e vídeo entre essas regiões, selecione um perfil de política de largura de banda na lista suspensa **Política de largura de banda**.

9.  Clique em **Confirmar**.

## Para modificar um link de região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de Rede** e em **Link de Região**.

4.  Na página **Link de Região**, clique no link de região que deseja modificar.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Em **Editar Link de Região**, você pode modificar as regiões que estão vinculadas ou o perfil de política de largura de banda para este link.

7.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Excluindo links da região de rede](lync-server-2013-deleting-network-region-links.md)  

#### Outros Recursos

[New-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegionLink)  
[Set-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkRegionLink)  
[Remove-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkRegionLink)  
[Get-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)

