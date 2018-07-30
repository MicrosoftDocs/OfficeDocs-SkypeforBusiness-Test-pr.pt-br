---
title: Criar ou modificar um conjunto de definições de configuração da versão do cliente
TOCTitle: Criar ou modificar um conjunto de definições de configuração da versão do cliente
ms:assetid: 4e6faffd-a36f-40f1-8734-78d84b7df921
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898477(v=OCS.15)
ms:contentKeyID: 52057627
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um conjunto de definições de configuração da versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

Definições de configuração de versão de cliente são utilizadas para ligar ou desligar o controle de versão de cliente. A configuração global de versão de cliente é instalada com o Lync Server e é utilizada para habilitar ou desabilitar controle de versão de cliente para toda a implantação do servidor. Você também pode configurar definições de configuração de versão de cliente para sites individuais. Você pode criar ou modificar definições de configuração de versão de cliente a partir de Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

> [!NOTE]  
> Já que usuários anônimos não são associados com um usuário, site ou serviço, usuários anônimos são afetados somente por políticas de nível global.

## Para criar ou modificar definições de configuração de versão de cliente utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e então clique no botão de navegação **Configuração de Versão do Cliente**.

4.  Na página **Configuração de Versão do Cliente**, faça o seguinte:
    
      - Para criar uma nova configuração, clique em **Nova**, selecione um site, clique em **OK** para o nome e por fim atualize as configurações.
    
      - Para modificar uma configuração selecione-a, clique em **Editar**, em **Exibir detalhes** e faça as alterações necessárias às configurações.

## Para criar ou modificar definições de configuração de versão de cliente utilizando Cmdlets Windows PowerShell

Você pode criar definições de configuração de versão de cliente utilizando o cmdlet **New-CsClientVersionConfiguration** e modificá-las utilizando o cmdlet **Set-CsClientVersionConfiguration**. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para criar uma nova coleção especificada de configurações de versão de cliente

  - O comando a seguir cria um novo conjunto de configurações de versão de cliente que será aplicado ao site de Redmond: neste exemplo, o versionamento de cliente está desabilitado para o site Redmond.
    
        New-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $False

## Para habilitar versionamento de cliente para um site

  - Esse comando habilita o versionamento de cliente para o site Redmond.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

## Para desabilitar o versionamento de cliente para uso na organização

  - Neste exemplo, o versionamento de cliente está desabilitado para todas as definições de configuração de versão de cliente em uso na organização.
    
        Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration  -Enabled $False

Para detalhes, consulte o tópico Ajuda para os cmdlets [New-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientVersionConfiguration) e [Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionConfiguration).

