---
title: 'Lync Server 2013: Configurar a política global para Chat Persistente'
TOCTitle: Configurar a política global para Chat Persistente
ms:assetid: 6176eb5c-19de-4c07-bcc0-2e38f8965966
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204951(v=OCS.15)
ms:contentKeyID: 49306885
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar a política global para Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Você pode usar apenas a política global padrão para habilitar as configurações do Chat Persistente para todos os usuários de sua implantação. Além disso, pode especificar políticas adicionais para sites e usuários a fim de controlar se o Chat Persistente será habilitado para usuários e sites específicos.

Você não pode excluir a política global. Se você tentar excluí-la, a configuração será redefinida para os valores padrão.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.<br />Para definir a configuração do Servidor de Chat Persistente, consulte <a href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente no Lync Server 2013</a> na documentação Implantação.

## Para configurar a política global para o Chat Persistente

1.  Usando uma conta de usuário atribuída à função CsPersistentChatAdministrator, CsAdministrator, ou CsUserAdministrator faça logon em qualquer computador de sua implantação interna.

2.  No menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela do navegador e insira a URL do administrador. Para obter detalhes sobre os diferentes métodos que podem ser usados para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md) na documentação de operações.
    
    > [!IMPORTANT]  
    > Você também pode usar cmdlets do Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de implantação.

3.  No Painel de Controle do Lync Server, clique em **Chat Persistente**, depois em **Política do Chat Persistente**.

4.  Clique em **Global** na lista de políticas, clique em **Editar** e depois em **Mostrar detalhes**.

5.  Em **Editar Política de Chat Persistente - Global**, faça o seguinte:
    
      - Em **Nome**, especifique um novo nome para a política global, se não desejar usar o padrão "Global".
    
      - Em **Descrição**, forneça os detalhes sobre a política de usuário (por exemplo, política global para *centralSiteName* ).
    
      - Para controlar o Chat Persistente para todos os sites e usuários que não são controlados especificamente por uma política de site ou de usuário, marque ou desmarque a caixa de seleção **Habilitar Chat Persistente**.

6.  Clique em **Confirmar**.

