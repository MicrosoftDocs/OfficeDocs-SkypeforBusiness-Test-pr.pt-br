---
title: Exibir informações de política do PIN
TOCTitle: Exibir informações de política do PIN
ms:assetid: 1d48b060-d77f-44ee-b70f-3ce128aedac4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687985(v=OCS.15)
ms:contentKeyID: 49886124
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações de política do PIN

 

_**Tópico modificado em:** 2013-02-23_

É possível usar a guia **Política PIN** para exibir o número de identificação pessoal (PIN) de autenticação de usuários que estão se conectando ao Lync 2013 com Telefones IP. Para usar a autenticação PIN, certifique-se de que **Habilitar Autenticação PIN** esteja selecionado nas configurações do Web Service. Para obter detalhes, consulte [Modificar configurações de Web Service existentes](lync-server-2013-modify-existing-web-service-configuration-settings.md).

Siga estas etapas para modificar uma política de PIN de nível do usuário ou nível local.

## Para exibir informações sobre uma política de PIN no Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Política de PIN**.

4.  Na página **Política de PIN**, clique em uma política, em **Editar** e em **Exibir detalhes**.

## Exibir Políticas de PIN usando cmdlets do Lync Server PowerShell

É possível exibir políticas de PIN usando o Windows PowerShell e o cmdlet Get-CsPinPolicy. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibindo Políticas de PIN

  - Para exibir informações sobre todas as suas políticas de PIN, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsPinPolicy
    
    Isto retornará informações semelhantes a esta:
    
        Identity             : Global
        Description          :
        MinPasswordLength    : 5
        PINHistoryCount      : 0
        AllowCommonPatterns  : False
        PINLifetime          : 0
        MaximumLogonAttempts :

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsPinPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPinPolicy).

## Consulte Também

#### Tarefas

[Modificar configurações de Web Service existentes](lync-server-2013-modify-existing-web-service-configuration-settings.md)  
[Criar uma nova política de PIN](lync-server-2013-create-a-new-pin-policy.md)

