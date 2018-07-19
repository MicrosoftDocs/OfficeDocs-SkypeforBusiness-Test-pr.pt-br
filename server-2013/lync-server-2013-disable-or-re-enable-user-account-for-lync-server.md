---
title: Habilitar ou reabilitar uma conta de usuário para o Lync Server
TOCTitle: Habilitar ou reabilitar uma conta de usuário para o Lync Server
ms:assetid: 12497d00-f665-4a97-be68-854c5a8be4fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429696(v=OCS.15)
ms:contentKeyID: 49305936
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou reabilitar uma conta de usuário para o Lync Server

 

_**Tópico modificado em:** 2016-04-04_

Após habilitar uma conta de usuário em Usuários e Computadores do Active Directory, você poderá usar os seguintes procedimentos para habilitar um novo usuário para o Microsoft Lync Server 2010 ou desabilitar uma conta de usuário já habilitada no Lync Server 2010 sem perder as configurações do Lync Server 2010 definidas para a conta de usuário. Como você não perde as configurações da conta de usuário do Lync Server 2010, pode reabilitar uma conta de usuário já habilitada sem ter que reconfigurá-la.

## Para desabilitar ou reabilitar uma conta de usuário do Lync Server habilitada anteriormente

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Usuários**.

4.  Na caixa **Usuários de pesquisa**, digite todo ou a primeira parte do nome de exibição, primeiro nome, último nome, nome de conta do Gerenciador de contas de segurança (SAM), endereço SIP ou alinhe o Identificador de recurso uniforme (URI) da conta do usuário que você quer desabilitar ou reabilitar e clique em **Localizar**.

5.  Na tabela, clique na conta de usuário que você quer habilitar ou reabilitar.

6.  No menu **Ação**, faça o seguinte:
    
      - Para desabilitar a conta de usuário temporariamente para o Lync Server 2013 , clique em **Desabilitar temporariamente para o Lync Server**.
    
      - Pra habilitar a conta de usuário para o Lync Server 2013, clique em **Reabilitar para o Lync Server**.

## Como desabilitar e reabilitar uma conta de usuário utilizando cmdlets do Windows PowerShell

Contas de usuário também podem ser temporariamente desabilitadas e reabilitadas mais tarde usando cmdlet **Set-CsUser**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Como desabilitar uma conta de usuário

  - Para desabilitar uma conta temporariamente, defina o valor da propriedade Enabled como falso ($False). Por exemplo:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $False

## Como reabilitar uma conta de usuário

  - Para reabilitar uma conta de usuário, defina o valor da propriedade Enabled como verdadeiro ($True). Por exemplo:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $True

Para mais informações, consulte o tópico de ajuda para o cmdlet [Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUser).

## Consulte Também

#### Tarefas

[Adicionar e habilitar uma nova conta de usuário ao Lync Server](lync-server-2013-add-and-enable-user-account-for-lync-server.md)  

#### Outros Recursos

[Habilitando e desabilitando usuários para Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

