---
title: Desabilitar um usuário para o Enterprise Voice
TOCTitle: Desabilitar um usuário para o Enterprise Voice
ms:assetid: 462002d8-21df-4d77-bf7f-4d059d6a4bb2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688043(v=OCS.15)
ms:contentKeyID: 49886202
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Desabilitar um usuário para o Enterprise Voice

 

_**Tópico modificado em:** 2012-09-21_

Use o procedimento a seguir para Enterprise Voice para uma conta de usuário ativada para Lync Server 2013.

## Para desativar uma conta de usuário para Enterprise Voice

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou a primeira parte de um nome de exibição, primeiro nome, sobrenome, nome da conta do Gerenciador de contas de segurança (SAM), endereço SIP ou linha do Uniform Resource Identifier (URI) da conta de usuário que deseja ativar e, então, clique em **Localizar**.

5.  Na tabela, clique na conta de usuário que deseja ativar para o Enterprise Voice.

6.  No menu **Editar**, clique em **Exibir detalhes**.

7.  Na página **Editar usuário do servidor Lync**, sob **Telefonia**, clique em qualquer opção exceto **Enterprise Voice**.
    
    > [!NOTE]  
    > Para restringir um usuário de fazer chamadas de vídeo ou áudio utilizando o Lync, em <strong>Telefonia</strong>, clique em <strong>Áudio/vídeo desativado</strong>.

8.  Clique em **Confirmar**.

O usuário agora está apto a utilizar o recurso Enterprise Voice.

## Consulte Também

#### Tarefas

[Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md)  

#### Outros Recursos

[Gerenciando o Enterprise Voice para usuários](lync-server-2013-managing-enterprise-voice-for-users.md)  
[Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md)

