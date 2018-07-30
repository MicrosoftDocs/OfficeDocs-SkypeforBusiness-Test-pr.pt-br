---
title: 'Lync Server 2013: Aplicar uma política de Chat Persistente a um usuário ou grupo de usuários'
TOCTitle: Aplicar uma política de Chat Persistente a um usuário ou grupo de usuários
ms:assetid: 809ef4e0-8d42-4feb-b7c0-3995f39867a7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205038(v=OCS.15)
ms:contentKeyID: 49307273
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Aplicar uma política de Chat Persistente a um usuário ou grupo de usuários no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Se um usuário tiver sido habilitado para Lync Server 2013, você poderá aplicar as políticas adequadas a usuários específicos para habilitá-los ou desabilitá-los a Servidor de Chat Persistente.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.<br />Para definir a configuração do Servidor de Chat Persistente, consulte <a href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente no Lync Server 2013</a> na documentação Implantação.

Use o procedimento neste tópico para aplicar uma política de usuário Chat Persistente criada anteriormente para uma ou mais contas de usuário ou grupos de usuários.

## Para aplicar uma política de usuário Chat Persistente a uma conta de usuário

1.  Usando uma conta de usuário atribuída à função CsPersistentChatAdministrator, CsAdministrator, ou CsUserAdministrator faça logon em qualquer computador de sua implantação interna.

2.  No menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e depois insira o URL de Admin. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** e pesquise a conta de usuário que deseja configurar.

4.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar usuário do Lync Server** em **Chat Persistente política**, selecione a política de usuário do Chat Persistente que você deseja aplicar.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> são aplicadas na política de eficácia padrão. Essas configurações são aplicadas automaticamente pelo servidor.

6.  Clique em **Confirmar**.

