---
title: Criar ou modificar regiões de rede
TOCTitle: Criar ou modificar regiões de rede
ms:assetid: bd08bb66-5976-4ece-b45c-7de19569f814
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182579(v=OCS.15)
ms:contentKeyID: 49307961
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar regiões de rede

 

_**Tópico modificado em:** 2012-11-01_

Uma região de rede interconecta várias partes de uma rede por diversas áreas geográficas. Cada região de rede deve ser associada a um local central. O local central é o local de data Center no qual o serviço de política de largura de banda do controle de admissão de chamadas está sendo executado. É possível usar o Painel de Controle do Lync Server para configurar as regiões de rede. As regiões de rede incluem configurações que determinam se os caminhos alternativos pela Internet são permitidos para conexões de áudio e vídeo. No Painel de Controle do Lync Server é possível criar, modificar ou excluir uma região de rede. Use este tópico para criar e modificar regiões de rede. Para obter detalhes sobre como excluir regiões de rede existentes, consulte [Excluindo regiões de rede existentes](lync-server-2013-deleting-existing-network-regions.md).

## Para criar uma região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à direita, clique em **Configuração de Rede** e clique em **Região**.

4.  Na página **Região**, clique em **Novo**.

5.  Na página **Nova Região**, digite um valor no campo **Nome**. Esse valor precisa ser exclusivo dentro de sua implantação do Microsoft Lync Server 2013.

6.  Na lista suspensa **Site central**, selecione o site central para essa região de rede.

7.  A caixa de seleção **Habilitar caminho alternativo do áudio** está marcada por padrão. Esse campo determina se as chamadas de áudio serão roteadas por um caminho alternativo, caso a largura de banda adequada não exista no caminho primário. Desmarque essa caixa de seleção somente se precisar desativar o descarregamento para a Internet. Se qualquer uma de suas chamadas for uma chamada pela Internet, essa caixa de seleção deverá ser marcada, independente das configurações de largura de banda.

8.  A caixa de seleção **Habilitar caminho alternativo do vídeo** está marcada por padrão. Esse campo determina se as chamadas de vídeo serão roteadas por um caminho alternativo, caso a largura de banda adequada não exista no caminho primário. Desmarque essa caixa de seleção somente se precisar desativar o descarregamento para a Internet. Se qualquer uma de suas chamadas for uma chamada pela Internet, essa caixa de seleção deverá ser marcada, independente das configurações de largura de banda.

9.  (Opcional) Digite um valor no campo **Descrição** para fornecer mais informações sobre essa região que não podem ser expressas somente pelo nome.

10. Clique em **Confirmar**.

A tabela **Sites associados** não é usada para criar uma região de rede. Você associa um site a uma região quando cria ou modifica o site. Para obter detalhes, consulte [Criar ou modificar sites de rede](lync-server-2013-creating-or-modifying-network-sites.md).

## Para modificar uma região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à direita, clique em **Configuração de Rede** e clique em **Região**.

4.  Na página **Região**, clique na região que você deseja modificar.

5.  No menu **Editar**, clique em **Mostrar detalhes**.

6.  Na página **Editar Região**, é possível modificar as configurações para habilitar e desabilitar caminhos alternativos de áudio e vídeo e alterar a descrição (para obter detalhes, consulte a seção "Para criar uma região de rede" acima neste tópico.

7.  Clique em **Confirmar**.

Não é possível modificar os **Sites associados** nesta página. A lista de sites associados é fornecida para referência de modo que você fique ciente de quais sites serão afetados quando você modificar as configurações de região.

## Consulte Também

#### Tarefas

[Excluindo regiões de rede existentes](lync-server-2013-deleting-existing-network-regions.md)  
[Configurar regiões de rede para CAC no Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md)  

#### Outros Recursos

[New-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegion)  
[Set-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkRegion)  
[Remove-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkRegion)  
[Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)

