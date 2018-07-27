---
title: 'Lync Server 2013: Configurar políticas para controle de acesso de usuário remoto'
TOCTitle: Configurar políticas para controle de acesso de usuário remoto
ms:assetid: 8f556849-692b-44a0-9514-4468fc9a39d0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398725(v=OCS.15)
ms:contentKeyID: 49307452
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

Configure uma ou mais políticas de acesso de usuários externos para controlar se usuários remotos podem colaborar com usuários internos do Lync Server. Para controlar o acesso de usuários remotos, você pode configurar políticas no nível global, de site e de usuários. As políticas de site substituem a política global, enquanto as políticas de usuário substituem as políticas de site e as políticas globais. Para detalhes sobre os tipos de políticas que você pode configurar, consulte [Gerenciando de federação e acesso externo ao Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md). As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

> [!NOTE]  
> Você pode configurar políticas para controlar o acesso de usuários remotos, mesmo se o acesso de usuários remotos não estiver habilitado para a sua organização. No entanto, as políticas configuradas entram em vigor somente quando o acesso de usuários remotos for habilitado para a sua organização. Para obter detalhes sobre como habilitar o acesso de usuários remotos, consulte <a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a>. Além disso, se você especificar uma política de usuário para controlar o acesso de usuários remotos, a política será aplicada somente a usuários que estiverem habilitados para o Lync Server e configurados para usar a política. Para detalhes sobre como especificar usuários que podem entrar no Lync Server a partir de locais remotos, consulte <a href="lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md">Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013</a>.

Use o procedimento a seguir para configurar cada política de acesso externo que desejar usar para controlar o acesso de usuários remotos.

> [!NOTE]  
> Este procedimento descreve como configurar uma política somente para permitir comunicações com usuários remotos, mas cada política configurada para suportar o acesso de usuários remotos pode configurar também o acesso de usuários federados e de usuários públicos. Para detalhes sobre como configurar políticas para oferecer suporte a usuários federados, consulte <a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Configurar políticas para controlar acesso de usuário federado no Lync Server 2013</a>. Para detalhes sobre como configurar políticas para oferecer suporte a usuários públicos, consulte <a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Criar ou editar fornecedores SIP públicos federados no Lync Server 2013</a>.

## Para configurar uma política de acesso externo para oferecer suporte ao acesso de usuários remotos

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso do Usuário Externo** e em **Política de Acesso Externo**.

4.  Na página **Política de Acesso Externo**, execute um dos seguintes procedimentos:
    
      - Para configurar a política global para oferecer suporte ao acesso de usuários remotos, clique na política global, clique em **Editar** e em **Exibir detalhes**.
    
      - Para criar uma nova política de site, clique em **Nova** e em **Política de site**. Em **Selecionar um Site**, clique no site apropriado na lista e em **OK**.
    
      - Para criar uma nova política de usuário, clique em **Novo** e em **Política de usuário**. Em **Nova Política de Acesso Externo**, crie um nome único no campo **Nome** que indique o que a política de usuário cobre (por exemplo, **HabilitaUsuáriosRemotos** para uma política de usuário que habilite comunicações para usuários remotos).
    
      - Para alterar uma política existente, clique na política adequada listada na tabela, clique em **Editar** e em **Exibir detalhes**.

5.  (Opcional) Se você deseja adicionar ou editar uma descrição, especifique a informação da política em **Descrição**.

6.  Siga um destes procedimentos:
    
      - Para habilitar o acesso de usuários remotos para a política, selecione a opção **Habilitar comunicações com usuários remotos**.
    
      - Para desabilitar o acesso de usuários remotos para a política, desmarque a opção **Habilitar comunicações com usuários remotos**.

7.  Clique em **Confirmar**.

Para habilitar o acesso de usuários remotos, você também deve habilitar o suporte ao acesso de usuários remotos em sua organização. Para detalhes, consulte [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) na documentação de Implantação ou de Operações.

Se esta for uma política de usuário, você também deve aplicá-la aos usuários que deseja que tenham permissão para se conectar remotamente. Para detalhes, consulte [Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md) na documentação de Implantação ou de Operações.

