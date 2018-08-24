---
title: Configurando opções de arquivamento
TOCTitle: Configurando opções de arquivamento
ms:assetid: b2f7f74d-e1ad-494e-9d46-5eb0efe5fb29
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205182(v=OCS.15)
ms:contentKeyID: 49307836
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando opções de arquivamento

 

_**Tópico modificado em:** 2012-10-10_

No Painel de Controle do Lync Server 2013, é possível usar as configurações de Arquivamento para especificar como o arquivamento é implementado. Isso inclui as seguintes configurações de Arquivamento:

  - Um configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações opcionais de nível do site e pool que você pode criar e usar para especificar como o arquivamento é implementado para sites específicos ou pools.

Inicialmente, as configurações de Arquivamento são definidas ao implantar o Arquivamento, mas você pode alterar, adicionar e excluir configurações depois da implantação. No Painel de Controle do Lync Server 2013, é possível usar a página **Configuração de arquivamento** do grupo **Arquivamento e monitoramento** para gerenciar configurações a nível global, de site e pool. Para obter detalhes sobre como as configurações de Arquivamento são implementada, incluindo quais opções você pode especificar e a hierarquia de configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações. Para obter detalhes sobre como gerenciar depois da implantação, consulte [Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md) na documentação de Operações.

> [!NOTE]  
> Para usar o arquivamento, você deve configurar políticas de Arquivamento para especificar se é necessário ativar o arquivamento para comunicações internas, externas ou ambas tendo em vista os usuários hospedados no Lync Server 2013. Por padrão, o arquivamento não está ativado para comunicações internas ou externas. Antes de ativar o Arquivamento em qualquer política, é necessário especificar os configurações de Arquivamento apropriadas para a implantação e, opcionalmente, para sites e pools específicos, como descrito nesta seção. Para obter detalhes sobre como ativar o Arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de Implantação.<br />Se não usar a integração de Microsoft Exchange para todos os usuários em sua implantação, você deve configurar políticas de Arquivamento para especificar se é necessário ativar o arquivamento para comunicações internas, externas ou ambas. Por padrão, o arquivamento não está ativado para comunicações internas ou externas tendo em vista o arquivamento de dados usando os bancos de dados de Arquivamento do Lync Server 2013. Antes de ativar o Arquivamento em qualquer política, você deve especificar as configurações de Arquivamento apropriadas para a implantação e, opcionalmente, para sites e pools específicos, como descrito nesta seção. Para obter detalhes sobre como ativar o Arquivamento usando os bancos de dados de Arquivamento do Lync Server 2013, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de Implantação.

## Nesta seção

  - [Configurando opções de arquivamento em nível global](lync-server-2013-configuring-archiving-options-at-the-global-level.md)

  - [Configurando opções de arquivamento para um local](lync-server-2013-configuring-archiving-options-for-a-site.md)

  - [Configurando opções de arquivamento para um pool](lync-server-2013-configuring-archiving-options-for-a-pool.md)

