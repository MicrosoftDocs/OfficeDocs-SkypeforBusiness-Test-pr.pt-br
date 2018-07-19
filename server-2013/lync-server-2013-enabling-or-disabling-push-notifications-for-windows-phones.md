---
title: Habilitar ou Desabilitar Notificações por Push para Windows Phones
TOCTitle: Habilitar ou Desabilitar Notificações por Push para Windows Phones
ms:assetid: a34f0c5c-4228-40e3-9d93-bc0b5df4895d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688162(v=OCS.15)
ms:contentKeyID: 49886347
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou Desabilitar Notificações por Push para Windows Phones

 

_**Tópico modificado em:** 2013-02-23_

Notificações por push, na forma de selos, ícones ou alertas, podem ser enviadas a um Windows Phone mesmo quando o aplicativo móvel está inativo. As notificações por push notificam um usuário sobre eventos como convites de IM e caixas postais novos ou perdidos. Você pode ativar ou desativar as notificações por push para dispositivos Windows Phone usando Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para ativar as notificações por push de Windows Phone do Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e depois no botão de navegação **Configuração da notificação por push**.

4.  Na página **Configuração da notificação por push**, clique no site que deseja editar, clique no menu **Editar** e depois em **Exibir detalhes**.

5.  Clique na caixa de seleção **Habilitar as notificações por push da Microsoft**.

6.  Clique em **Confirmar**.

## Para desativar as notificações por push de Windows Phone do Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e depois no botão de navegação **Configuração da notificação por push**.

4.  Na página **Configuração da notificação por push**, clique no site que deseja editar, clique no menu **Editar** e depois em **Exibir detalhes**.

5.  Apague a caixa de seleção **Habilitar as notificações por push da Microsoft**.

6.  Clique em **Confirmar**.

## Para ativar ou desativar as notificações por push para Windows Phone usando os cmdlets do Windows PowerShell

Você pode ativar ou desativar as notificações por push do Windows Phone usando o cmdlet **Set-CsPushNotificationConfiguration**. Você pode executar esse cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ativar as notificações por push de Windows Phone

  - Para ativar as notificações por push de Windows Phone, defina o valor da propriedade EnableMicrosoftPushNotificationService para Verdadeiro ($True). Por exemplo:
    
        Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableMicrosoftPushNotificationService $True

## Para desativar as notificações por push de Windows Phone

  - Para desativar as notificações por push de Windows Phone, defina o valor da propriedade EnableMicrosoftPushNotificationService para Falso ($False). Por exemplo:
    
        Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableMicrosoftPushNotificationService $False

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Set-CsPushNotificationConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsPushNotificationConfiguration).

## Consulte Também

#### Tarefas

[Configurando notificações por push no Lync Server 2013](lync-server-2013-configuring-for-push-notifications.md)

