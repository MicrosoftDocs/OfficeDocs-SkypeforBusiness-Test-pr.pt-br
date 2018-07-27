---
title: 'Lync Server 2013: Criar uma política de usuário para Chat Persistente'
TOCTitle: Criar uma política de usuário para Chat Persistente
ms:assetid: aa3774af-d442-4206-8a68-2fbb9102e9d6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205170(v=OCS.15)
ms:contentKeyID: 49307743
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma política de usuário para Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

No Painel de Controle do Lync Server, você define as políticas que podem ser atribuídas aos usuários em **Usuários**.

A política de usuário substitui as políticas globais e do local, mas apenas para os usuários específicos que estão atribuídos à política de usuário.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.<br />Para definir a configuração do Servidor de Chat Persistente, consulte <a href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente no Lync Server 2013</a> na documentação Implantação.

## Para criar uma política de usuário para Chat Persistente

1.  Usando uma conta de usuário atribuída à função CsPersistentChatAdministrator, CsAdministrator, ou CsUserAdministrator faça logon em qualquer computador de sua implantação interna.

2.  No menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e depois insira o URL de Admin. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]  
    > Você também pode usar cmdlets do Windows PowerShell. Consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de implantação.

3.  Na barra de navegação esquerda, clique em **Chat Persistente**, e depois, em **Chat Persistente Política**.

4.  Clique em **Novo** e em **Política do usuário**.

5.  Em **Nova Chat Persistente Política**, faça o seguinte:
    
      - Em **Nome**, especifique um nome para a nova política de usuário.
    
      - Em **Descrição**, forneça os detalhes sobre a política de usuário (por exemplo, a política Global para Chat Persistente do usuário específico).
    
      - Para controlar o Chat Persistente para todos os usuários que não são especificamente controlados através de uma política de usuário, marque ou desmarque a caixa de seleção **Ativar Chat Persistente**.

6.  Clique em **Confirmar**.

