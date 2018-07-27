---
title: Habilitar ou desabilitar o controle de versão do cliente
TOCTitle: Habilitar ou desabilitar o controle de versão do cliente
ms:assetid: 33a98cb9-a979-4bb6-afb2-512f601d7ac5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898475(v=OCS.15)
ms:contentKeyID: 52057595
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar o controle de versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

As definições de configuração da versão do cliente são usadas para ativar ou desativar o controle da versão do cliente, seja globalmente ou para locais específicos.A configuração de versão de cliente global é instalada com Lync Server 2013 e é usada para ativar ou desativar o controle de versão de cliente para toda a implantação do servidor. Quando a configuração global é ativada, qualquer política de versão de cliente que você tenha terá efeito quando os usuários tentarem fazer logon. Você pode desativar a configuração de versão de cliente global se não quiser que nenhum controle de versão de cliente ocorra. Você pode ativar ou desativar a versão de cliente a partir do Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

> [!NOTE]  
> Como os usuários anônimos não são associados a um usuário, site ou serviço, eles são afetados somente por políticas de nível global.

## Para ativar ou desativar a versão de cliente usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Configuração de Versão de Cliente**.

4.  Faça o seguinte:
    
      - Para ativar ou desativar globalmente a versão de cliente, clique duas vezes na configuração **Global** e então modifique as configurações.
    
      - Para ativar ou desativar a versão do cliente para um local específico, clique em **Novo**, selecione o local, clique em **OK** e então modifique as configurações para o local.

## Ativar ou desativar a versão de cliente usando cmdlets Windows PowerShell

Você pode ativar ou desativar a versão de cliente ao usar o cmdlet **Set-CsClientVersionConfiguration**. Você pode executar esse cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ativar a versão de cliente

  - Você pode ativar a versão de cliente ao definir a propriedade **Enabled** como Verdadeira ($True).
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

## Para desativar a versão de cliente

  - Você pode desativar a versão de cliente ao definir a propriedade **Enabled** como Falsa ($False).
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

Para obter detalhes, consulte o tópico de Ajuda do cmdlet [Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionConfiguration). en-us

