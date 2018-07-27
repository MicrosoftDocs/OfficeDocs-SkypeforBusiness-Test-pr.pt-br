---
title: Criar ou modificar uma nova política de versão do cliente
TOCTitle: Criar ou modificar uma nova política de versão do cliente
ms:assetid: 4be6e449-aa82-4b46-abb1-d31281573a72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898476(v=OCS.15)
ms:contentKeyID: 52057625
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma nova política de versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

Você pode utilizar políticas de versão de cliente para especificar as versões de clientes que são suportadas em seu ambiente. Utilizar versionamento de cliente pode ajudar a reduzir os custos associados com suportar múltiplas versões de clientes. Também pode aprimorar a experiência de usuário como um todo, porque quando versões de cliente mais recentes e antigas interagem, os recursos disponíveis podem ser limitados pela versão mais antiga do cliente. Você pode criar ou modificar políticas de versão de cliente a partir de Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para criar ou modificar políticas de versão de cliente utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**.
    
    > [!NOTE]  
    > A guia <strong>Política de Versão de Cliente</strong> está selecionada por padrão.

4.  Na página **Política de Versão de Cliente**, siga um dos seguintes procedimentos:
    
      - Para criar uma nova política de versão, clique em **Nova** e selecione **Política de site**, **Política de pool** ou **Política de usuário**, então clique em **OK**.
    
      - Para modificar a política global ou outra política existente de versão de cliente, clique em **Editar** e depois em **Exibir detalhes**.

5.  Na página **Editar política de versão de cliente**, crie ou modifique regras conforme descrito em [Criar ou modificar uma nova regra da política de versão do cliente](lync-server-2013-create-or-modify-a-new-client-version-policy-rule.md).

## Para criar ou modificar políticas de versão de cliente utilizando Cmdlets Windows PowerShell

Você pode criar políticas de versão de cliente utilizando o cmdlet **New-CsClientVersionPolicy** e modificá-las utilizando o cmdlet **Set-CsClientVersionPolicy**. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para criar uma nova política de versão de cliente no escopo de site

  - O comando a seguir cria uma nova política de versão de cliente aplicada ao site Redmond. Como não há parâmetros adicionais especificados, a nova política utilizará as configurações padrão de versão de cliente.
    
        New-CsClientVersionPolicy -Identity "site:Redmond"

## Para criar uma nova política de versão de cliente no escopo de usuário

  - Para criar uma política por usuário, utilize um comando similar a esse:
    
        New-CsClientVersionPolicy -Identity "RedmondClientVersionPolicy"

Para detalhes, veja os tópicos de Ajuda para os cmdlets [New-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientVersionPolicy) e [Set-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionPolicy).

