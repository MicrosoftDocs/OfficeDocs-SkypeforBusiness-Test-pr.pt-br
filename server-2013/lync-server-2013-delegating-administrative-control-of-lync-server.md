---
title: 'Lync Server 2013: Delegando o controle administrativo do Lync Server'
TOCTitle: Delegando o controle administrativo do Lync Server 2013
ms:assetid: 0f378eff-8ef4-4c60-9fd2-67d7ee259ef8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520951(v=OCS.15)
ms:contentKeyID: 49305894
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Delegando o controle administrativo do Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

No Lync Server 2013, as tarefas administrativas são delegadas aos usuários utilizando o novo recurso RBAC (controle de acesso baseado na função). Ao instalar o Lync Server, algumas funções RBAC são criadas para você. Essa funções correspondem a grupos de segurança universal no Serviços de Domínio Active Directory. Por exemplo, a função RBAC CsHelpDesk corresponde ao grupo CsHelpDesk encontrado no contêiner de Usuários nos Serviços de Domínio Active Directory. Além disso, cada função RBAC está associada a um conjunto de cmdlets Lync ServerWindows PowerShell. Esses cmdlets representam as tarefas que podem ser executadas pelos usuários quem receberam determinada função RBAC. Por exemplo, a função CsHelpDesk recebeu os cmdlets Lock-CsClientPin e UnlockCsClientPin. Isso significa que os usuários que receberam a função CsHelpDesk podem bloquear e desbloquear números PIN de usuários. No entanto, a função CsHelpDesk não recebeu a atribuição do cmdlet New-CsVoicePolicy. Isso significa que os usuários que receberam a função CsHelpDesk não podem criar novas políticas de voz.

## Exibindo informações sobre as funções RBAC

É possível recuperar informações básicas sobre as funções RBAC executando o comando a seguir a partir do Shell de Gerenciamento do Lync Server:

    Get-CsAdminRole

Lembre-se de que a Identidade da função RBAC (por exemplo, CsVoiceAdministrator) tem um mapeamento direto para um grupo de segurança encontrado no contêiner de Usuários nos Serviços de Domínio Active Directory.

Para visualizar uma lista de cmdlets que foram designados a uma função, use um comando semelhante a este:

    Get-CsAdminRole -Identity "CsHelpDesk" | Select-Object -ExpandProperty Cmdlets

## Atribuindo uma função RBAC a um usuário

Para atribuir uma função RBAC a um usuário, é necessário adicionar esse usuário a um grupo de segurança adequado do Active Directory. Por exemplo, para atribuir a função CsLocationAdministrator a um usuário, é necessário adicionar esse usuário ao grupo CsLocationAdministrator. Isso pode ser feito com o seguinte procedimento:

**Para atribuir um usuário a um grupo de segurança**

1.  Usando uma conta que tenha permissão para modificar a associação a um grupo do Active Directory, faça logon em um computador em que os usuários e computadores do Active Directory tenham sido instalados.

2.  Clique em **Iniciar** , clique em **Todos os Programas** , clique em **Ferramentas Administrativas** e, em seguida, clique em **Usuários e Computadores do Active Directory** .

3.  Em Usuários e Computadores do Active Directory, expanda o nome do seu domínio e clique no contêiner de **Usuários** .

4.  Clique com o botão direito no grupo de segurança **CsLocationAdministrator** e clique em **Propriedades** .

5.  Na caixa de diálogo **Propriedades** , na guia **Membros** , clique em **Adicionar** .

6.  Na caixa de diálogo **Selecionar Usuários, Computadores, Contatos ou Grupos** , digite o nome de usuário ou nome de exibição do usuário a ser adicionado ao grupo (por exemplo, **Ken Myer** ) na caixa **Inserir os nomes de objeto a selecionar** e clique em **OK** .

7.  Na caixa de diálogo **Propriedades** , clique em **OK** .

Para verificar se a função RBAC foi atribuída, use o cmdlet [Get-CsAdminRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAdminRoleAssignment), passando o cmdlet theSamAccountName (nome de logon do Active Directory) do usuário. Por exemplo, execute este comando a partir do Shell de Gerenciamento do Lync Server:

    Get-CsAdminRoleAssignment  -Identity "kenmyer"

