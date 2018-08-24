---
title: Excluir uma política de versão do cliente existente
TOCTitle: Excluir uma política de versão do cliente existente
ms:assetid: b88aaa25-97ff-4eb6-bd34-b97332cd6890
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ923064(v=OCS.15)
ms:contentKeyID: 52057717
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir uma política de versão do cliente existente

 

_**Tópico modificado em:** 2013-02-23_

Se você deseja excluir uma política de versão de cliente que estava configurada anteriormente, você pode excluí-la a partir de Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para excluir políticas de versão de cliente com o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Política de Versão do Cliente**.

4.  Na página **Política de Versão de Cliente**, selecione a política de versão de cliente que deseja excluir, clique em **Editar** e então em **Excluir**.

## Para excluir políticas de versão de cliente com os cmdlets Windows PowerShell

Você pode excluir as políticas de versão de cliente usando o cmdlet **Remove-CsClientVersionPolicy**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShellPara obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma política de versão de cliente específica

  - Este comando exclui a política de versão de cliente aplicada ao site Redmond:
    
        Remove-CsClientVersionPolicy -Identity site:Redmond

## Para remover todas as políticas de versão de cliente aplicadas ao escopo do site

  - Este comando remove todas as políticas de versão de cliente configuradas no escopo do site:
    
        Get-CsClientVersionPolicy -Fiter "site:*" | Remove-CsClientVersionPolicy

## Para remover políticas de versão de cliente que não incluem um agente do usuário específico

  - E esse comando remove qualquer política de versão de cliente que não inclua uma regra para o agente do usuário do Windows Phone Lync (WPLync):
    
        Get-CsClientVersionPolicy | Where-Object {$_.Rules -notmatch "UserAgent=WPLync" | Remove-CsClientVersionPolicy

Para detalhes, consulte o tópico Ajuda para o cmdlet [Remove-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClientVersionPolicy).

