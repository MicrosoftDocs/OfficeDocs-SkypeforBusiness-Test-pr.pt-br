---
title: Exibir definições de configuração da versão do cliente
TOCTitle: Exibir definições de configuração da versão do cliente
ms:assetid: c72df4e6-a889-4cb6-86f7-8334d7774c6e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ923062(v=OCS.15)
ms:contentKeyID: 52057708
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir definições de configuração da versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

As configurações da versão cliente são usadas para ativar ou desativar o controle de versão do cliente. A configuração da versão do cliente global é instalada com o Lync Server 2013 e é usada para habilitar ou desabilitar o controle da versão do cliente de toda a implantação do servidor. Quando a configuração Global é habilitada, quaisquer políticas de versão do cliente existentes entrarão em vigor quando os usuários tentarem fazer logon. É possível visualizar as configurações da versão de cliente a partir do Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

> [!NOTE]  
> Como os usuários anônimos não são associados a um usuário, site ou serviço, eles são afetados somente por políticas de nível global.

## Para visualizar as configurações de versão de cliente utilizando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Configuração de Versão do Cliente**.

4.  Dê um duplo clique no nome da configuração de versão do cliente que você deseja visualizar.

## Visualização de as configurações da versão de cliente pelo uso de cmdlets Windows PowerShell

Você pode visualizar as configurações de versão de cliente usando o cmdlet **Get-CsClientVersionConfiguration**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShellPara obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar as informações de configuração da versão de cliente

  - Para exibir informações sobre todas as as configurações da versão de cliente, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsClientVersionConfiguration
    
    Isso retornará informações parecidas com:
    
        Identity      : Global
        DefaultAction : Allow
        DefaultURL    :
        Enabled       : True

Para detalhes, consulte o tópico Ajuda para o cmdlet [Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientVersionConfiguration).

