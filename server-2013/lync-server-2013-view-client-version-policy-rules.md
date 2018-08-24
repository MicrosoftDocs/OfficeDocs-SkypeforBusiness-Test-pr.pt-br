---
title: Exibir regras da política de versão do cliente
TOCTitle: Exibir regras da política de versão do cliente
ms:assetid: f3a0215f-f72f-4e9b-a07b-25858dc4203a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ923060(v=OCS.15)
ms:contentKeyID: 52057768
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir regras da política de versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

Uma política de versão do cliente é composta de um conjunto de regras da política de versão do cliente. Essas regras definem as ações que devem ser realizadas quando os usuários tentam fazer logon com clientes e versões do cliente específicos. Você pode exibir as regras da política de versão do cliente a partir do Painel de Controle do Lync Server 2013 ou do Shell de Gerenciamento do Lync Server 2013.

## Para exibir as regras da política de versão do cliente usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e, no botão de navegação, clique em **Política de Versão do Cliente**.

4.  Na página **Política de versão do cliente**, clique duas vezes na política que deseja exibir.

5.  As regras são exibidas na página **Editar política de versão do cliente**. Para exibir os detalhes de uma regra, selecione-a e clique em **Mostrar detalhes**.

## Exibindo regras da política de versão do cliente com os cmdlets do Windows PowerShell

Você pode exibir as regras da política de versão do cliente usando o Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsClientVersionPolicyRule**. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para exibir as regras da política de versão do cliente

  - Para exibir as regras da política de versão do cliente, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsClientVersionPolicyRule
    
    Isso retornará informações semelhantes a estas para cada regra configurada:
    
        Identity          : Global/2336c611-a243-4c5d-994b-eea8a524d0e4
        Priority          : 0
        RuleId            : 2336c611-a243-4c5d-994b-eea8a524d0e4
        Description       :
        Action            : Block
        ActionUrl         :
        MajorVersion      : 1
        MinorVersion      : 3
        BuildNumber       :
        QfeNumber         :
        UserAgent         : RTC
        UserAgentFullName :
        Enabled           : True
        CompareOp         : LEQ

Para obter detalhes, consulte o tópico da Ajuda para o cmdlet [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientVersionPolicyRule).

