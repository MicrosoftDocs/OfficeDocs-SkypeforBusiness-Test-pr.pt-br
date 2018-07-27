---
title: 'Lync Server 2013: Atribuir políticas de conferência para suporte de usuários anônimos'
TOCTitle: Atribuir políticas de conferência para suporte de usuários anônimos
ms:assetid: 662de022-1111-40f7-bad4-f2b686f30973
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521007(v=OCS.15)
ms:contentKeyID: 49306946
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir políticas de conferência para suporte de usuários anônimos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Por padrão, nenhum usuário tem permissão para convidar usuários anônimos para participar de uma reunião. Você controla quem pode convidar usuários anônimos configurando uma política de conferência para oferecer suporte a usuários anônimos e aplicando essa política a usuários específicos. Para obter detalhes sobre como configurar políticas de conferência para oferecer suporte a usuários anônimos, consulte [Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md) e [Gerenciando de federação e acesso externo ao Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md).

Use o procedimento desta seção para aplicar uma política de conferência que já você criou para um ou mais usuários ou grupos de usuários.

> [!NOTE]  
> Além de configurar e aplicar uma política para permitir que os usuários convidem usuários anônimos, você deve também habilitar o suporte a usuários anônimos em sua organização. Para obter detalhes, consulte <a href="lync-server-2013-configure-policies-to-control-public-user-access.md">Configurar políticas para controlar o acesso de usuário público no Lync Server 2013</a>.

## Para configurar uma política de usuário para participação anônima em reuniões

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e execute um dos seguintes procedimentos:
    
    1.  Para criar uma nova política de usuário, clique em **Nova** e em **Política de usuário** . Crie um nome exclusivo no campo **Nome** que indica o a abrangência da política de usuário (por exemplo, **EnableAnonymous** para uma política de usuário que permite comunicações para usuários anônimos).
    
    2.  Para configurar uma política de usuário existente, clique na política adequada listada na tabela, clique em **Editar** e em **Exibir detalhes** .

4.  Na caixa de diálogo **Políticas de Conferência** , marque a caixa de seleção **Permitir que os participantes convidem usuários anônimos** .

5.  Clique em **Confirmar** .

6.  Na barra de navegação esquerda, clique em **Usuários** e pesquise a conta de usuário que deseja configurar.

7.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes** .

8.  Em **Editar Usuário do Lync Server** , **Política de conferência** , selecione a política de usuário com a configuração de acesso de usuário anônimo que você deseja aplicar a este usuário.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> aplicam as configurações padrão de instalação do servidor e são aplicadas automaticamente pelo servidor.

Para permitir que os usuários convidem usuários anônimos para conferências, você também deve habilitar o suporte para usuários anônimos na sua organização. Para obter detalhes, consulte [Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md) na documentação de Implantação ou na documentação de Operações.

