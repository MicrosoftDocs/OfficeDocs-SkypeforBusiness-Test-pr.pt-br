---
title: Visualizar Informações sobre Configurações de Notificações por Push
TOCTitle: Visualizar Informações sobre Configurações de Notificações por Push
ms:assetid: be5c6b01-4294-4d17-9772-fed40201e8a5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721868(v=OCS.15)
ms:contentKeyID: 49886386
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizar Informações sobre Configurações de Notificações por Push

 

_**Tópico modificado em:** 2013-02-23_

Notificações por push, na forma de selos, ícones ou alertas, podem ser enviadas a um dispositivo móvel mesmo quando o aplicativo móvel está inativo. As notificações de push notificam um usuário de eventos como um convite de IM novo ou perdido e caixa postal. É possível ver as informações das configurações de notificações de push para dispositivos móveis usando o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Par exibir informações de notificação de push do Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Configuração de notificação de push**.

4.  Na página **Configurações de notificação de push**, clique no site que você deseja exibir, clique no menu **Editar** e em **Exibir detalhes**.

## Para exibir informações de configuração de notificação de push usando cmdlets do Windows PowerShell

É possível também exibir definições de configuração de notificação de push usando o Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsPushNotificationConfiguration**. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para exibir informações de configuração de notificação de push

  - Para exibir informações sobre todas as definições de configurações de notificação de push, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsPushNotificationConfiguration
    
    Isto irá retornar informações semelhante ao seguinte:
    
        Identity                               : Global
        EnableApplePushNotificationService     : False
        EnableMicrosoftPushNotificationService : False

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Get-CsPushNotificationConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPushNotificationConfiguration).

## Consulte Também

#### Tarefas

[Configurando notificações por push no Lync Server 2013](lync-server-2013-configuring-for-push-notifications.md)

