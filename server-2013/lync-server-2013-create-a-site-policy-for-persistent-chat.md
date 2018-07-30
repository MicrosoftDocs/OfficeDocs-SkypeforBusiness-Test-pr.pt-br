---
title: 'Lync Server 2013: Criar uma política de site para chat persistente'
TOCTitle: Criar uma política de site para chat persistente
ms:assetid: 1327ff5c-b859-4010-a240-e0b2b084b5bd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204693(v=OCS.15)
ms:contentKeyID: 49305951
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma política de site para chat persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Para cada site implantado, você pode criar uma política do Chat Persistente específica por site.

A configuração da política de site substitui a política global, mas somente para o site específico coberto pela política de site.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.<br />Para definir a configuração do Servidor de Chat Persistente, consulte <a href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente no Lync Server 2013</a> na documentação Implantação.

## Para criar uma política do Chat Persistente para um site

1.  Usando uma conta de usuário atribuída à função CsPersistentChatAdministrator, CsAdministrator, ou CsUserAdministrator faça logon em qualquer computador de sua implantação interna.

2.  No menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e depois insira o URL de Admin. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Chat Persistente**, depois em **Chat Persistente Política**.
    
    > [!IMPORTANT]  
    > Você também pode usar o cmdlets Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de Implantação.

4.  Clique em **Nova** e em **Política de site**.

5.  Em **Selecionar um Site**, clique no site ao qual a política é aplicada.

6.  Em **Nova Política do Chat Persistente**, faça o seguinte:
    
      - Em **Nome**, especifique um nome para a nova política de site (por exemplo, Redmond).
    
      - Em **Descrição**, forneça detalhes sobre o que é a política de site (por exemplo, política de sala de chat para Redmond).
    
      - Para controlar o Chat Persistente para todos os sites não especificamente controlados através de uma política de site, marque ou desmarque a caixa de seleção **Habilitar Chat Persistente**.

7.  Clique em **Confirmar**.

