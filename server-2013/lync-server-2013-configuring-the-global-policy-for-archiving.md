---
title: Configurando a política global de arquivamento
TOCTitle: Configurando a política global de arquivamento
ms:assetid: 58341d6b-c3ff-4dd9-b1c7-0048f33861ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204906(v=OCS.15)
ms:contentKeyID: 49306779
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a política global de arquivamento

 

_**Tópico modificado em:** 2012-10-09_

Ao implantar seu Servidores Front-End, o Lync Server cria uma política global para arquivamento. Por padrão, o arquivamento está desabilitado na política global. A política global controla se o arquivamento está habilitador para comunicações internas e externas para toda a sua implantação, a menos que você configure as políticas de site ou de usuário, o que substitui a política global ou se você utiliza a integração do Microsoft Exchange para alguns ou todos os seus usuários. Se você utilizar a integração do Microsoft Exchange, a política global não se aplicará a quaisquer usuários que estejam hospedados no Exchange 2013 e tenham suas caixas de correio colocadas em bloqueio In-loco.

Para obter detalhes sobre como as políticas de arquivamento funcionam, incluindo a hierarquia para políticas globais, de site e de usuários, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) Documentação de planejamento, de implantação ou de operações.

> [!NOTE]  
> Se você habilitar a integração do Microsoft Exchange para a sua implantação, as políticas de bloqueio In-loco do Exchange controlam se o arquivamento é habilitado para usuários que estejam hospedados no Exchange 2013 e tenham suas caixas de correio colocadas em bloqueio In-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na Documentação de implantação.<br />Você deve especificar todas as opções apropriadas nas configurações de arquivamento antes de habilitar o arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na Documentação de implantação.

## Para configurar a política global para arquivamento ao utilizar bancos de dados de arquivamento do Lync Server

1.  A partir da conta do usuário que foi atribuída à função CsArchivingAdministrator ou CsAdministrator, faça o logon em qualquer computador na sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre os diferentes métodos que você pode utilizar para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.

4.  Na página **Política de Arquivamento**, clique em **Global**, clique em **Editar** e, em seguida, clique em **Mostrar detalhes**.

5.  Em **Editar Política de Arquivamento - Global**, faça o seguinte:
    
      - Em **Nome**, se não desejar usar o nome padrão de global, especifique um novo nome para a política global.
    
      - Em **Descrição**, forneça informações sobre o que a política é (por exemplo, a política global para *divisionName*).
    
      - Para controlar o arquivamento de comunicações internas para todos os sites e usuários que não estivem sendo controlados especificamente por meio de uma política de site ou de usuário, marque ou desmarque a caixa de seleção **Arquivar comunicações internas**.
    
      - Para controlar o arquivamento de comunicações externas para todos os sites e usuários que não estivem sendo controlados especificamente por meio de uma política de site ou de usuário, marque ou desmarque a caixa de seleção **Arquivar comunicações externas**.

6.  Clique em **Confirmar**.

