---
title: Desabilitar bypass de mídia de rede
TOCTitle: Desabilitar bypass de mídia de rede
ms:assetid: 936d2678-d712-4589-b172-b5793013652f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688141(v=OCS.15)
ms:contentKeyID: 49886317
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Desabilitar bypass de mídia de rede

 

_**Tópico modificado em:** 2012-10-15_

As configurações de desvio de mídia aplicam-se globalmente por toda a implantação do Microsoft Lync Server 2013. O desvio de mídia permite que chamadas ignorem o Servidor de Mediação. Para obter detalhes sobre quando usar o desvio de mídia, consulte [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) na seção de Planejamento. Você pode desativar o desvio de mídia do Painel de Controle do Lync Server. Para obter detalhes sobre a ativação e configuração do desvio de mídia, consulte [Habilitar bypass de mídia de rede](lync-server-2013-enabling-network-media-bypass.md)

## Para desativar o desvio de mídia

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da Rede** e clique em **Global**.

4.  Na página **Global**, clique na configuração **Global**. Há sempre apenas uma configuração, sempre chamada de Global.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Na página **Editar Configuração Global**, desmarque a caixa de seleção **Ativar desvio de mídia**.

7.  Clique em **Confirmar** para salvar suas alterações.

## Consulte Também

#### Tarefas

[Habilitar bypass de mídia de rede](lync-server-2013-enabling-network-media-bypass.md)

