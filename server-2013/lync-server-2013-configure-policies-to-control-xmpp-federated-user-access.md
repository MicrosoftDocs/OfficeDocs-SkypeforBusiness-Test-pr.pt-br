---
title: 'Lync Server 2013: Configurar políticas para controlar o acesso de usuário federado'
TOCTitle: Configurar políticas para controlar o acesso de usuário federado
ms:assetid: 0fe0ff75-e52a-4e3e-923a-64f6412ac4e4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ552446(v=OCS.15)
ms:contentKeyID: 49305904
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar políticas para controlar o acesso de usuário federado no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Esta documentação é preliminar e está sujeita a alterações. Os tópicos em branco são incluídos como espaços reservados.

Ao configurar políticas para oferecer suporte a parceiros federados do protocolo XMPP, as políticas aplicam-se a usuários dos domínios XMPP federados, mas não a usuários de provedores de serviços de mensagens instantâneas (IM) do protocolo SIP (por exemplo, Windows Live), ou domínios SIP federados. Configure um **Parceiro Federado XMPP** para cada domínio XMPP federado para os quais deseja permitir que seus usuários adicionem contatos e se comuniquem. Políticas de parceiros federados XMPP estão disponíveis somente em um único escopo, e embora não sejam definidas como políticas globais, agem como uma. Para definir uma política global, de site ou de usuário para Parceiros Federados XMPP, configure o escopo da política primeiro criando e configurando a Política de Acesso Externo para o escopo necessário. Para detalhes sobre os tipos de políticas que podem ser configuradas para acesso externo e federação, consulte [Gerenciando de federação e acesso externo ao Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md) na documentação de Operações.

> [!NOTE]  
> Todas as políticas de <strong>Federação de Acesso Externo</strong> são aplicadas através de provisionamento em banda. As políticas que se aplicam ao usuário, pertencem a um site ou são globais no escopo são comunicadas ao cliente durante o login. Você pode configurar políticas para controlar o acesso de parceiros federados XMPP, mesmo se não tiver habilitado a federação XMPP para a sua organização. No entanto, as políticas configuradas produzem efeito somente quando você tem a federação de parceiros XMPP implantada, habilitada e configurada para a sua organização. Para detalhes sobre a implantação e configuração da federação de parceiros XMPP, consulte <a href="lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md">Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público no Lync Server 2013</a> na documentação de Implantação. Além disso, se você especificar uma política de usuário na Política de Acesso Externo para controlar parceiros federados XMPP, a política será aplicada somente aos usuários habilitados para o Lync Server 2013 e configurados para usar a política.

## Para editar uma política global para parceiros federados XMPP

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso do Usuário Externo** e em **Política de Acesso Externo** .

4.  Na página **Política de Acesso Externo** , faça o seguinte para a política global:

5.  Clique na política global, clique em **Editar** e em Exibir detalhes.

6.  Forneça uma descrição para a política global (opcional).

7.  Selecione **Habilitar comunicações com usuários federados** .

8.  Selecione **Habilitar comunicações com usuários federados XMPP** .

9.  Clique em **Confirmar** para salvar suas alterações na política global.

## Para criar uma política de site ou de usuário para parceiros federados XMPP

1.  Clique em **Novo** e em **Política de site** ou **Política de usuário** . Em **Selecionar um Site** , clique no site apropriado na lista e clique em **OK** .

2.  Forneça uma descrição para a política de site (opcional).

3.  Na política de site ou de usuário, selecione **Habilitar comunicações com usuários federados** .

4.  Selecione **Habilitar comunicações com usuários federados XMPP** .

5.  Clique em **Confirmar** para salvar suas mudanças para a política local ou do usuário.

## Para editar uma política existente para parceiros federados XMPP

1.  Para alterar uma política existente, selecione a política desejada na lista, clique em **Editar** e em **Exibir detalhes** .

2.  Altere ou atualize a descrição da política (opcional).

3.  Marque ou desmarque a opção **Habilitar comunicações com usuários federados** .

4.  Marque ou desmarque a opção **Habilitar comunicações com usuários federados XMPP** .

5.  Clique em **Confirmar** para salvar suas alterações na política.

## Para editar uma política existente para parceiros federados XMPP usando Windows PowerShell

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Digite o seguinte no Shell de Gerenciamento do Lync Server:
    
        Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    Um comando de exemplo que definirá a política global para acesso de usuários federados como True (habilitado) e acesso a domínio XMPP como True (habilitado):
    
        Set-CsExternalAccessPolicy -Identity global -EnableFederationAccess $true -EnableXmppAccess $true

## Para criar um site ou política de usuário para parceiros federados XMPP usando Windows PowerShell

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Digite o seguinte no Shell de Gerenciamento do Lync Server:
    
        New-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    Um comando de exemplo que definirá uma política de site para o site Redmond para o acesso de usuários federados como habilitado e acesso ao domínio XMPP como habilitado:
    
        New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true

## Para excluir uma política existente para parceiros federados XMPP usando Windows PowerShell

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Digite o seguinte no Shell de Gerenciamento do Lync Server:
    
        Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy>
    
    Um comando de exemplo que excluirá uma política de usuário:
    
        Remove-CsExternalAccessPolicy -Identity EAPUserPolicySetXMPP

4.  Um comando de exemplo que redefinirá a política global para a configuração padrão:
    
        Remove-CsExternalAccessPolicy -Identity global

## Consulte Também

#### Tarefas

[Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)  
[Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  

#### Outros Recursos

[Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
[Set-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExternalAccessPolicy)  
[New-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsExternalAccessPolicy)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy)  
[Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)

