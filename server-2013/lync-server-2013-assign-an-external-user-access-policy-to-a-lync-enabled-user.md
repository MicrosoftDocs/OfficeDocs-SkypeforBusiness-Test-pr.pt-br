---
title: 'Lync Server 2013: Atribuir uma política de usuário externo a um usuário habilitado do Lync'
TOCTitle: Atribuir uma política de usuário externo a um usuário habilitado do Lync
ms:assetid: 736fcaad-9f95-4896-b767-e199d86a00a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398551(v=OCS.15)
ms:contentKeyID: 49307108
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Se o usuário tiver sido habilitado para o Lync Server, você poderá configurar a federação SIP, a federação XMPP, o acesso de usuário remoto e a conectividade a redes públicas de mensagens instantâneas (IM) no Painel de Controle do Lync Server aplicando as políticas adequadas a usuários específicos. Por exemplo, se você criou uma política para oferecer suporte ao acesso de usuário remoto, deverá aplicá-la ao usuário antes que ele possa se conectar ao Lync Server de um local remoto e colaborar com usuários internos do local remoto.

> [!NOTE]  
> Para oferecer suporte ao acesso de usuário externo, você deve ativar o suporte para cada tipo de acesso de usuário externo ao qual deseja oferecer suporte e configurar as políticas apropriadas e outras opções para controlar o uso. Para obter detalhes, consulte <a href="lync-server-2013-configuring-support-for-external-user-access.md">Configurando suporte para acesso de usuário externo no Lync Server 2013</a> na documentação de implantação ou <a href="lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md">Gerenciando de federação e acesso externo ao Lync Server 2013</a> na documentação de Operações.

Use o procedimento neste tópico para aplicar uma política de acesso de usuário externo criada anteriormente para uma ou mais contas de usuário.

## Para aplicar uma política de usuário externo a uma conta de usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** e pesquise a conta de usuário que deseja configurar.

4.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar Usuário do Lync Server**, em **Política de acesso externo**, selecione a política de usuário que você deseja aplicar.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> são aplicadas nas configurações do servidor padrão ou de política global.

## Atribuindo políticas de acesso externo por usuário usando os cmdlets Windows PowerShell

As políticas de acesso externo por usuário podem ser atribuídas utilizando os cmdlets Windows PowerShell e Grant-CsExternalAccessPolicy . Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para atribuir uma política de acesso externo por usuário a um único usuário

  - Este comando atribui a política de acesso externo por usuário RedmondExternalAccessPolicy ao usuário Ken Myer.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName "RedmondExternalAccessPolicy"

## Para atribuir uma política de acesso externo por usuário a vários usuários

  - Este comando atribui a política de acesso externo por usuário USAExternalAccessPolicy a todos os usuários com contas no OU UnitedStates no Active Directory. Para obter mais informações sobre o parâmetro OU usado neste comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -OU "ou=UnitedStates,dc=litwareinc,dc=com" | Grant-CsExternalAccessPolicy -PolicyName "USAExternalAccessPolicy"

## Para cancelar a atribuição de uma política de acesso externo por usuário

  - Este comando cancela a atribuição de qualquer política de acesso externo por usuário atribuída a Ken Myer. Após o cancelamento da atribuição da política por usuário, Ken Myer será automaticamente gerenciado usando a política global ou a política de site local (se houver). Um política de site tem prioridade sobre a política global.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy).

