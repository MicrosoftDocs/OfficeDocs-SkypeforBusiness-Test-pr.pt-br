---
title: Configurando e atribuindo políticas de arquivamento
TOCTitle: Configurando e atribuindo políticas de arquivamento
ms:assetid: acd18ea8-c7f1-4178-871a-cd3b75bdaa8b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205175(v=OCS.15)
ms:contentKeyID: 49307771
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando e atribuindo políticas de arquivamento

 

_**Tópico modificado em:** 2012-10-01_

No Lync Server 2013, é possível usar políticas para ativar e desativar o arquivamento de comunicações internas e externas para usuários hospedados em Lync Server 2013. Isso inclui as seguintes Políticas de arquivamento:

  - Uma política global criada por padrão ao implantar o Lync Server 2013.

  - As políticas opcionais de nível de site e do usuário que você pode criar e usar para especificar como o arquivamento é implementado para sites e usuários específicos.

As políticas de arquivamento são configuradas inicialmente ao implantar o Arquivamento, mas você pode alterar, adicionar e excluir políticas após a implantação. No Painel de Controle do Lync Server 2013, é possível usar a página **Política de arquivamento** do grupo **Arquivamento e monitoramento** para gerenciar políticas a nível global, de site e de usuário.

> [!NOTE]  
> Para controlar a implementação do Arquivamento, você deve especificar opções nas configurações de Arquivamento, como se é necessário arquivar IM ou conferências, o uso do modo crítico e as opções de limpeza. Por padrão, nenhuma opção está ativada na configuração de Arquivamento global ou em qualquer configuração de Arquivamento de site ou pool. É necessário especificar todas as opções apropriadas nas configurações de Arquivamento antes de ativá-lo para comunicações internas ou externa nas Políticas de arquivamento. Para obter mais detalhes, consulte <a href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools</a> na documentação de operações.<br />Se você integrar seu armazenamento do Lync Server com o armazenamento do Exchange 2013, as políticas de usuário do Exchange têm preferência sobre as políticas de arquivamento do Lync Server 2013, mas apenas para os usuários que estão hospedados em Exchange 2013 e que possuem caixas de correio com Bloqueio in-loco.

Para obter detalhes sobre como as políticas são implementadas, incluindo a hierarquia das políticas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, de Implantação ou de Operações. Para obter detalhes sobre como gerenciar políticas após a implantação, consulte [Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md) na documentação de operações.

## Nesta seção

  - [Configurando a política global de arquivamento](lync-server-2013-configuring-the-global-policy-for-archiving.md)

  - [Configurando políticas de site para arquivamento](lync-server-2013-setting-up-site-policies-for-archiving.md)

  - [Configurando Políticas de Arquivamento para Usuários](lync-server-2013-setting-up-archiving-policies-for-users.md)

