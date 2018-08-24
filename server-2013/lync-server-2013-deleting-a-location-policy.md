---
title: Excluindo uma política de local
TOCTitle: Excluindo uma política de local
ms:assetid: 8ca9ba10-f45f-435a-b39c-519d251e9085
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688125(v=OCS.15)
ms:contentKeyID: 49886301
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo uma política de local

 

_**Tópico modificado em:** 2012-10-10_

No Lync Server 2013, você pode usar a política de local para aplicar configurações relacionadas à funcionalidade do 9-1-1 Avançado (E9-1-1) e às configurações de local de usuários ou contatos. A política de local determina se o usuário está habilitado para o E9-1-1 e, se estiver, qual será o comportamento de uma chamada de emergência. Por exemplo, é possível usar a política de local para definir o número que constitui uma chamada de emergência (por exemplo, 911 nos Estados Unidos), se a segurança da empresa deve ser automaticamente notificada e como a chamada é roteada.

Você pode configurar as políticas de local a partir do grupo **Configuração de rede**no Painel de Controle do Lync Server 2013. Em Painel de Controle do Lync Server você pode visualizar, criar, modificar ou excluir políticas de local. Usar os procedimentos a seguir excluirá uma política de local. Para obter detalhes sobre a criação ou modificação das políticas de local, consulte [Criar ou modificar uma política de local](lync-server-2013-creating-or-modifying-a-location-policy.md).

## Para excluir uma política de local

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação, clique em **Configuração de rede** e clique em **Política de local**.

4.  Na página **Política de local**, selecione a política de local que você quer excluir.
    
    > [!NOTE]  
    > Você pode excluir mais que uma política de local ao mesmo tempo. Para isso, mantenha a tecla CTRL e selecione várias políticas. Ou, para selecionar todas as políticas, clique em <strong>Selecionar tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.
    
    > [!IMPORTANT]  
    > Você não pode excluir uma política de local Global. Se você tentar excluir a política Global, você receberá uma mensagem de aviso, e essa política será redefinida aos seus valores padrão.

## Consulte Também

#### Tarefas

[Criar ou modificar uma política de local](lync-server-2013-creating-or-modifying-a-location-policy.md)  
[Visualizando informações de política de local](lync-server-2013-viewing-location-policy-information.md)

