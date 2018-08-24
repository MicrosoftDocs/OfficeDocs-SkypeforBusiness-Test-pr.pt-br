---
title: Remover uma conta de usuário do Lync Server
TOCTitle: Remover uma conta de usuário do Lync Server
ms:assetid: 2f512aba-e358-45ae-af58-74312ee9c514
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688008(v=OCS.15)
ms:contentKeyID: 49886155
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover uma conta de usuário do Lync Server

 

_**Tópico modificado em:** 2013-02-22_

É possível usar o seguinte procedimento para remover uma conta de usuário adicionada anteriormente no Lync Server 2013.

> [!NOTE]  
> Remover um usuário pode causar a perda de qualquer configuração definida para a conta de usuário. Se você gostaria de desabilitar temporariamente uma conta de usuário, consulte o tópico <a href="lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md">Habilitar ou reabilitar uma conta de usuário para o Lync Server</a>.

## Para remover uma conta de usuário do Lync Server Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou a primeira parte do nome de exibição, nome, sobrenome, nome da conta SAM, endereço SIP ou URI de linha da conta de usuário que você deseja desabilitar ou reabilitar e clique em **Encontrar**.

5.  Na tabela, clique na conta de usuário que deseja remover.

6.  No menu **Ação**, selecione **Remover do Lync Server** e uma caixa de diálogo aparece.

7.  Na caixa de diálogo, selecione **OK** para remover o usuário.

## Remover uma conta do usuário utilizando os cmdlets do Lync Server PowerShell

Também é possível remover as contas de usuário utilizando o cmdlet Disable-CsUser. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Removendo uma conta do usuário

  - Para remover uma conta de usuário, utilize o cmdlet Disable-CsUser. Por exemplo:
    
        Disable-CsUser -Identity "Ken Myer"
    
    Após este comando ser executado, não há forma de reabilitar a conta e suas configurações anteriores. Ao invés disso, você precisará usar o cmdlet Enable-CsUser para criar uma nova conta para Ken Myer.

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Disable-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Disable-CsUser).

## Consulte Também

#### Tarefas

[Habilitar ou reabilitar uma conta de usuário para o Lync Server](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)  

#### Outros Recursos

[Habilitando e desabilitando usuários para Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

