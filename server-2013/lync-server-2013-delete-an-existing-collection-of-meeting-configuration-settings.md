---
title: Excluir um conjunto existente das configurações de reunião
TOCTitle: Excluir um conjunto existente das configurações de reunião
ms:assetid: 92ff8a91-05c5-4047-a533-5dff12f22299
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688136(v=OCS.15)
ms:contentKeyID: 49886315
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto existente das configurações de reunião

 

_**Tópico modificado em:** 2013-02-23_

Você pode excluir uma configuração de site ou de usuário. A configuração global não pode ser removida. Se você excluir a configuração global, ela será automaticamente redefinida para os valores padrão.

## Para excluir uma configuração de site ou de reunião

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Configuração da reunião**.

4.  Na lista de configuração de reunião, clique na configuração de site ou pool que deseja excluir, clique em Editar e em Excluir.

## Remoção das definições de configuração de reunião usando os cmdlets PowerShell do Lync Server

As configurações de reunião podem ser excluídas usando o Windows PowerShell e o cmdlet Remove-CsMeetingConfiguration. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Remoção de uma coleção específica de definições de configuração de reunião

  - Este comando remove as definições de configuração de reunião aplicadas ao site da Redmond:
    
        Remove-CsMeetingConfiguration -Identity "site:Redmond"

## Remoção de todas as definições de configuração de reunião aplicadas ao escopo do site

  - Este comando remove todas as definições de configuração de reunião aplicadas ao escopo do site:
    
        Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration

## Remoção de todas as definições de configuração de reunião que admitem usuários anônimos como padrão

  - E este remove todas as configurações que permitem que usuários anônimos sejam admitidos como padrão:
    
        Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Remove-CsMeetingConfiguration](ttps://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsMeetingConfiguration).

