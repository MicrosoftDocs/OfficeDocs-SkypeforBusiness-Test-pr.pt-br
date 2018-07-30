---
title: 'Lync Server 2013: Configurar políticas para controlar o acesso de usuário público'
TOCTitle: Configurar políticas para controlar o acesso de usuário público
ms:assetid: 090aea0f-ef0b-49da-9c80-02d9279f2fa6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520946(v=OCS.15)
ms:contentKeyID: 49305811
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar políticas para controlar o acesso de usuário público no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A conectividade de IM (mensagem instantânea) pública permite que os usuários em sua organização usem IM para se comunicar com usuários de serviços de IM fornecidos por provedores de serviço de IM público, incluindo a rede Windows Live de serviços de Internet, Yahoo\! e AOL. Configure uma ou mais políticas de acesso de usuário externo para controlar se os usuários públicos podem colaborar com usuários internos do Lync Server. A conectividade por IM pública é um recurso adicionado que depende da configuração de sua implantação e dos usuários. Também depende do provisionamento do serviço no provedor de IM pública. Para obter mais informações sobre como provisionar sua implantação para usar os provedores públicos, consulte o guia “Public IM Connectivity Provisioning Guide for Microsoft Lync Server, Office Communications Server, and Live Communications Server”: <http://go.microsoft.com/fwlink/?linkid=269821>

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


Para acessar o site de Provisionamento de Conectividade IM Pública do Microsoft Lync Server, use o seguinte link: <http://go.microsoft.com/fwlink/?linkid=212638>

Para controlar o acesso do usuário público, é possível configurar políticas no nível global, site e de usuário. Para obter detalhes sobre os tipos de políticas que você pode configurar, consulte [Configurando suporte para acesso de usuário externo no Lync Server 2013](lync-server-2013-configuring-support-for-external-user-access.md) na documentação Implantação ou na documentação Planejamento. As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

No caso de convites de IM, a resposta depende do software cliente. A solicitação é aceita a menos que remetentes externos sejam explicitamente bloqueados por uma regra configurada pelo usuário (ou seja, as configurações nas listas de cliente **Permitir** e **Bloquear** do usuário). Além disso, os convites de IM podem ser bloqueados se um usuário optar por bloquear toda IM de usuários que não estão na lista **Permitir**.

> [!NOTE]  
> É possível configurar políticas para controlar o acesso ao usuário público, mesmo se você não tiver habilitado a federação para sua organização. No entanto, as políticas configuradas entram em vigor somente quando a federação está habilitada para sua organização. Para obter detalhes sobre como habilitar a federação, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a> na documentação Implantação ou na documentação Operações. Além disso, se você especificar uma política de usuário para controlar acesso do usuário público, a política se aplicará somente aos usuários habilitados para Lync Server e configurados para usar a política. Para obter detalhes sobre como especificar usuários que pode fazer logon no Lync Server, consulte <a href="lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md">Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013</a> na documentação Implantação ou na documentação Operações.

Use o procedimento a seguir para configurar uma política para suportar o acesso de usuários de um ou mais provedores de IM público.

## Para configurar uma política de acesso externo para suportar o acesso de usuário público

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso do Usuário Externo** e em **Política de Acesso Externo**.

4.  Na página **Política de Acesso Externo**, execute um dos seguintes procedimentos:
    
      - Para configurar a política global a fim de suportar o acesso de usuário público, clique na política global, em **Editar** e clique em **Mostrar detalhes**.
    
      - Para criar uma nova política de site, clique em **Nova** e em **Política de site**. Em **Selecionar um Site**, clique no site apropriado na lista e em **OK**.
    
      - Para criar uma nova política de usuário, clique em **Novo** e clique em **Política de Usuário**. Em **Nova Política de Acesso Externo**, crie um nome exclusivo no campo **Nome** que indica o que a política de usuário cobre (por exemplo, **EnablePublicUsers** para uma política de usuário que permite comunicações para usuários públicos).
    
      - Para alterar uma política existente, clique na política adequada listada na tabela, clique em **Editar** e em **Exibir detalhes**.

5.  (Opcional) Se você deseja adicionar ou editar uma descrição, especifique a informação da política em **Descrição**.

6.  Siga um destes procedimentos:
    
      - Para habilitar o acesso de usuários públicos à política, marque a caixa de seleção **Habilitar comunicações com usuários públicos**.
    
      - Para desabilitar o acesso de usuários públicos à política, desmarque a caixa de seleção **Habilitar comunicações com usuários públicos**.

7.  Clique em **Confirmar**.

Para habilitar o acesso ao usuário público, é necessário habilitar o suporte para federação em sua organização. Para obter detalhes, consulte [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md).

Se for uma política de usuário, também será necessário aplicar a política aos usuários públicos para os quais você deseja permitir a colaboração com usuários públicos. Para obter detalhes, consulte [Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md).

## Consulte Também

#### Tarefas

[Criar ou editar fornecedores SIP públicos federados no Lync Server 2013](lync-server-2013-create-or-edit-public-sip-federated-providers.md)  

#### Outros Recursos

[Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

