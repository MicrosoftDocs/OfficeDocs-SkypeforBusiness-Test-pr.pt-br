---
title: Excluir uma política de conferência existente
TOCTitle: Excluir uma política de conferência existente
ms:assetid: 709ed771-790f-4bf1-a4de-b37ca5168688
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688089(v=OCS.15)
ms:contentKeyID: 49886259
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir uma política de conferência existente

 

_**Tópico modificado em:** 2013-02-23_

Siga estas etapas para excluir uma política de conferência no nível do usuário ou no nível do local.

> [!NOTE]  
> Você não pode excluir a política global de conferência.

## Para excluir uma política de conferência de site ou usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Política de Conferência**.

4.  Na lista de políticas de conferência, clique na política de site ou usuário que deseja excluir, clique em Editar e em Excluir.

## Removendo políticas de conferência usando cmdlets do Shell de Gerenciamento do Lync Server

Você também pode excluir configurações de tronco usando o Shell de Gerenciamento do Lync Server e o cmdlet **Remove-CsConferencingPolicy**. Você pode executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma política de conferência especificada

  - O comando a seguir remove a política de conferência com a identidade RedmondConferencingPolicy:
    
        Remove-CsConferencingPolicy -Identity "RedmondConferencingPolicy"

## Para remover todas as políticas de conferência aplicadas ao escopo por usuário

  - O comando a seguir remove todas as políticas de conferência configuradas no escopo por usuário:
    
        Get-CsConferencingPolicy -Filter "tag:*" | Remove-CsConferencingPolicy

## Para remover todas as políticas de conferência que permitem a gravação por usuários externos

  - O comando a seguir exclui todas as políticas de conferência que permitem que os usuários externos registrem a conferência:
    
        Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToRecordMeetings -eq $True} | Remove-CsConferencingPolicy

Para obter detalhes, consulte [Remove-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsConferencingPolicy).

