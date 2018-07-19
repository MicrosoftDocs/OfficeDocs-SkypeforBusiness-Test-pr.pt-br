---
title: Excluir um conjunto existente de definições de configuração da versão do cliente
TOCTitle: Excluir um conjunto existente de definições de configuração da versão do cliente
ms:assetid: 70bf1216-d0d2-45ce-881f-b8edadf3cec7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898480(v=OCS.15)
ms:contentKeyID: 52057658
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto existente de definições de configuração da versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

Se você deseja remover as definições de configuração do cliente que foram configuradas anteriormente para um site, você pode remover as configurações a partir de Painel de Controle do Lync Server 2013 ou de Shell de Gerenciamento do Lync Server 2013.

## Para remover as definições de configuração de cliente usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Configuração de Versão do Cliente**.

4.  Selecione o site, clique em **Editar**, depois em **Excluir** e por fim clique em **OK**.

## Para remover as configurações da versão de cliente pelo uso de cmdlets Windows PowerShell

Você pode excluir as configurações de versão de cliente usando o cmdlet **Remove-CsClientVersionConfiguration**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShellPara obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma coleção especificada das definições de configuração de versão de cliente

  - O comando a seguir remove as definições de configuração de versão de cliente aplicadas ao site Redmond:
    
        Remove-CsClientVersionConfiguration -Identity "site:Redmond"

## Para remover todas as definições de configuração de versão de cliente aplicadas no escopo do site

  - Esse comando remove todas as definições de configuração de versão de cliente configuradas no escopo do site:
    
        Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

## Para remover todas as definições de versão de cliente com base no valor da propriedade DefaultAction

  - E esse comando remove todas as definições de configuração de versão de cliente em que a ação padrão tiver sido definida como "Bloquear":
    
        Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block" | Remove-CsClientVersionConfiguration

Para detalhes, veja o tópico Ajuda para o cmdlet [Remove-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClientVersionConfiguration).

