---
title: Excluindo uma política de arquivamento
TOCTitle: Excluindo uma política de arquivamento
ms:assetid: 4739a691-41cc-4128-8bb8-6d5a4c02107a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520989(v=OCS.15)
ms:contentKeyID: 49306586
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo uma política de arquivamento

 

_**Tópico modificado em:** 2013-02-23_

Você pode excluir uma política de usuário ou uma política de site. A política global não pode ser removida. Se você tentar excluir a política global, o Lync Server 2013 automaticamente redefine a política para os valores padrão.

> [!NOTE]  
> Se você ativar a integração do Microsoft Exchange para a implantação, as políticas Exchange controlam se o arquivamento está ativado para usuários hospedados no Exchange 2013 e têm as caixas de correio no Bloqueio In-loco. Para detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.

## Para excluir uma política de usuário ou site para arquivamento

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.

4.  Na lista de políticas de arquivamento, clique na política de usuário ou site que deseja excluir, clique em **Editar** e em **Excluir**.

5.  Clique em **Confirmar**.

## Removendo políticas de arquivamento utilizando cmdlets Shell de Gerenciamento do Lync Server

As políticas de arquivamento também podem ser excluídas utilizando o Windows PowerShell e o cmdlet **Remove-CsArchivingPolicy**. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Removendo uma política de arquivamento específica

  - Como exemplo, o **Remove-CsArchivingPolicy** exclui a política com a Identidade site:Redmond. Observe que quando uma política configurada no escopo do site é excluída, os usuários gerenciados anteriormente pela política do site irão automaticamente ser governados pela política de arquivamento global. O comando a seguir remove o arquivamento aplicado ao site Redmond:
    
        Remove-CsArchivingPolicy -Identity site:Redmond

## Removendo todas as políticas de arquivamento aplicadas ao escopo por usuário

  - Este comando remove todas as políticas de arquivamento aplicadas ao escopo por usuário:
    
        Get-CsArchivingPolicy -Filter "tag:*" | Remove-CsArchivingPolicy

## Removendo todas as políticas de arquivamento que desativam o arquivamento interno

  - Este comando remove todas as políticas de arquivamento onde o arquivamento interno foi desativado:
    
        Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False} | Remove-CsArchivingPolicy

Para mais informações, consulte o tópico de ajuda para o cmdlet [Remove-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsArchivingPolicy).

## Consulte Também

#### Outros Recursos

[Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

