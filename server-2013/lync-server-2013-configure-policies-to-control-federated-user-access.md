---
title: 'Lync Server 2013: Configurar políticas para controlar acesso de usuário federado'
TOCTitle: Configurar políticas para controlar acesso de usuário federado
ms:assetid: 5485e208-81e4-4e59-9aeb-1232c11dd8a2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398359(v=OCS.15)
ms:contentKeyID: 49306734
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar políticas para controlar acesso de usuário federado no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Quando você configurar políticas para fornecer suporte às comunicações de parceiros federados, as políticas se aplicam aos usuários de domínios federados. Você pode configurar uma ou mais políticas de acesso de usuário externas para controlar se usuários de domínios federados podem colaborar com seus usuários do Lync Server 2013. Para controlar o acesso de usuários federados, você pode configurar políticas no nível global, de site e de usuário. As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

> [!NOTE]  
> Você pode configurar políticas para controlar o acesso de usuário federado, mesmo que não tenha habilitado a federação para sua organização. No entanto, as políticas que configurar só terão efeito quando a federação for habilitada para a sua organização. Para obter detalhes sobre como habilitar a federação, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a> na documentação de Implantação ou de Operações. Além disso, se você especificar uma política de usuário para controlar o acesso de usuário federado, essa política se aplicará apenas aos usuários habilitados para o Lync Server 2013 e configurados para utilizar a política.

## Para configurar uma política para suportar o acesso por usuários de domínios federados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso do Usuário Externo** e em **Política de Acesso Externo**.

4.  Na página **Política de Acesso Externo**, execute um dos seguintes procedimentos:
    
      - Para configurar a política global para oferecer suporte ao acesso de usuário federado, clique na política global, clique em **Editar** e em **Mostrar detalhes**.
    
      - Para criar uma nova política de site, clique em **Nova** e em **Política de site**. Em **Selecionar um Site**, clique no site apropriado na lista e em **OK**.
    
      - Para criar uma nova política de usuário, clique em **Nova** e em **Política de usuário**. Em **Nova Política de Acesso Externo**, crie um nome exclusivo no campo **Nome** que indica o a abrangência da política de usuário (por exemplo, **EnableFederatedUsers** para uma política de usuário que permite comunicações para usuários públicos).
    
      - Para alterar uma política existente, clique na política adequada listada na tabela, clique em **Editar** e em **Exibir detalhes**.

5.  (Opcional) Se você deseja adicionar ou editar uma descrição, especifique a informação da política em **Descrição**.

6.  Siga um destes procedimentos:
    
      - Para habilitar o acesso de usuário federado na política, marque a caixa de seleção **Habilitar comunicações com usuários federados**.
    
      - Para desabilitar o acesso de usuário federado na política, desmarque a caixa de seleção **Habilitar comunicações com usuários federados**.

7.  Clique em **Confirmar**.

Para habilitar o acesso do usuário federado, você também deve habilitar o suporte para federação em sua organização. Para obter detalhes, consulte [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md).

Se essa for uma política de usuário, você também deverá aplicar a política aos usuários que também devem ser capazes de colaborar com usuários federados. Para obter detalhes, consulte [Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md).

## Para configurar uma política existente usando o Windows PowerShell para oferecer suporte ao acesso de usuários de domínios federados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Digite o seguinte no Shell de Gerenciamento do Lync Server:
    
        Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAcess <$true, $false> -EnablePublicCloudAudioVideoAcess <$true, $false> -EnableOutsideAcess <$true, $false>
    
    Um exemplo de comando que definirá a política global para habilitar o acesso de usuários federados, acesso ao domínio XMPP, acesso de usuário remoto, acesso de provedor público e conceder a capacidade de utilizar áudio e vídeo para provedores públicos que os suportem:
    
        Set-CsExternalAccessPolicy -Identity global -EnableFederationAccess $true -EnableXmppAccess $true -EnableOutsideAccess $true -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
    

    > [!TIP]
    > O parâmetro “EnablePublicCloudAudioVideoAccess” não possui uma seleção correspondente no Painel de Controle do Lync Server



## Para criar uma nova política usando o Windows PowerShell para oferecer suporte ao acesso de usuários de domínios federados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Digite o seguinte no Shell de Gerenciamento do Lync Server:
    
        New-CsExtenalAccessPolicy -Identity <name of site or user policy - you cannot create a new global policy using New-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAccess <$true, $false> -EnablePublicCloudAudioVideoAccess <$true, $false> -EnableOutsideAccess <$true, $false>
    
    Um exemplo de criação de uma nova política de site:
    
        New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true -EnableOutsideAccess $true -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true

## Para excluir ou redefinir uma política usando o Windows PowerShell para oferecer suporte ao acesso de usuários de domínios federados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Digite o seguinte no Shell de Gerenciamento do Lync Server
    
        Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy> 
    
    Um exemplo de redefinição de política global (A política global somente pode ter sua configuração removida. A política não pode ser excluída):
    
        Remove-CsExternalAccessPolicy -Identity global 
    
    Para remover uma política de site, digite:
    
        Remove-CsExternalAccessPolicy -Identity site:Redmond 
    
    Exclua a política de site de Redmond. Para excluir uma política de usuário chamada UserEAPPolicy, digite:
    
        Remove-CsExternalAccessPolicy -Identity UserEAPPolicy

## Consulte Também

#### Tarefas

[Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  
[Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)  

#### Outros Recursos

[Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
[Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)  
[Set-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExternalAccessPolicy)  
[New-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsExternalAccessPolicy)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy)  
[Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)

