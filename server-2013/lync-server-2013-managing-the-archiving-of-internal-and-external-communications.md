---
title: Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013
TOCTitle: Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013
ms:assetid: 6c2cf941-3204-4f1a-a7e0-416c828056d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204977(v=OCS.15)
ms:contentKeyID: 49307031
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-09_

No Lync Server 2013, você usa as políticas de arquivamento para habilitar e desabilitar o arquivamento de comunicações internas e externas se não usar a integração do Microsoft Exchange ou se tiver usuários que não estão hospedados no Exchange 2013 cujas caixas de correio estão no Bloqueio In-loco. Isso inclui as seguintes políticas de arquivamento:

  - Uma política global que é criada por padrão quando você implanta o Lync Server 2013.

  - Políticas opcionais nos níveis do site e do usuário que você pode criar e usar para especificar como o arquivamento é implementado para sites ou usuários específicos.

Você inicialmente configura políticas de arquivamento quando implanta o arquivamento, mas pode alterar, adicionar e excluir políticas após a implantação. No Painel de Controle do Lync Server 2013, você pode usar a página **Política de Arquivamento** do grupo **Arquivamento e Monitoramento** para gerenciar políticas nos níveis global, do site e do usuário. Se você integrar o armazenamento do Lync Server ao armazenamento do Exchange 2013, as políticas de usuário do Exchange prevalecerão sobre as políticas de arquivamento do Lync Server 2013.

Para obter detalhes sobre como as políticas são implementadas, incluindo a hierarquia das políticas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) nas documentações de planejamento, implantação e operações.

> [!NOTE]  
> Para controlar a implementação do arquivamento, você deve especificar opções nas configurações de arquivamento, como se mensagens instantâneas e conferências serão arquivadas, o uso do modo crítico e as opções de limpeza. Por padrão, nenhuma opção é habilitada na configuração de arquivamento global nem em qualquer configuração de arquivamento de site ou pool. Você deve especificar todas as opções desejadas nas configurações de arquivamento antes de habilitar o arquivamento das comunicações internas e externas nas políticas de arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools</a> na documentação de operações.<br />Se você habilitar a integração do Microsoft Exchange para sua implantação, as políticas do Exchange controlarão se o arquivamento será habilitado para os usuários que estão hospedados no Exchange 2013 e cujas caixas de correio estão em Bloqueio In-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de implantação.

## Nesta seção

  - [Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos](lync-server-2013-creating-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-specific-sites-or-users.md)

  - [Mudar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para sua Empresa, Sites ou Usuários](lync-server-2013-changing-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-your-organization-sites-or-us.md)

  - [Aplicar uma política de arquivamento aos usuários](lync-server-2013-applying-an-archiving-policy-to-users.md)

  - [Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server](lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md)

  - [Excluindo uma política de arquivamento](lync-server-2013-deleting-an-archiving-policy.md)

