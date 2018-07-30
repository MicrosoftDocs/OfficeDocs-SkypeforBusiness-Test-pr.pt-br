---
title: Excluindo regiões de rede existentes
TOCTitle: Excluindo regiões de rede existentes
ms:assetid: c7293a2f-2b49-4c4a-903f-f7edcea2bc5f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721882(v=OCS.15)
ms:contentKeyID: 49886404
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo regiões de rede existentes

 

_**Tópico modificado em:** 2013-02-21_

Uma região de rede interconecta várias partes de uma rede entre várias áreas geográficas. Cada região de rede deve ser associada com um local central. O local central é o local do centro de dados no qual o serviço da política de largura de banda CAC está funcionando. É possível usar o Painel de Controle do Lync Server para configurar regiões de rede. As regiões de rede incluem configurações que determinam se os caminhos alternativos através da Internet são permitidos para conexões de áudio e vídeo. Do Painel de Controle do Lync Server, é possível criar, modificar ou excluir uma região de rede. Use este tópico para excluir regiões de rede existentes. Para obter detalhes sobre a criação e modificação de regiões de rede, consulte [Criar ou modificar regiões de rede](lync-server-2013-creating-or-modifying-network-regions.md)

## Para excluir uma região de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à direita, clique em **Configuração de Rede** e clique em **Região**.

4.  Na página **Região**, clique na região que você deseja excluir.
    
    > [!NOTE]  
    > É possível excluir mais de uma região por vez. Para fazer isso, pressione CTRL e selecione várias regiões enquanto mantém pressionada a tecla CTRL. Ou, para selecionar todas as regiões, clique em <strong>Selecionar tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.
    

    > [!WARNING]
    > Uma região de rede não pode ser removida se estiver associada a um site de rede. Se você quiser tentar remover uma região associada a um site, receberá uma mensagem de erro. Para ver se um região está associada a algum site, selecione a região e clique em <STRONG>Mostrar detalhes</STRONG> no menu <STRONG>Editar</STRONG>.



## Consulte Também

#### Tarefas

[Criar ou modificar regiões de rede](lync-server-2013-creating-or-modifying-network-regions.md)

