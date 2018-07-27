---
title: Configurando Políticas de Arquivamento para Usuários
TOCTitle: Configurando Políticas de Arquivamento para Usuários
ms:assetid: 1bbb45df-0590-4c66-9d65-d25526f57790
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204722(v=OCS.15)
ms:contentKeyID: 49306049
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Políticas de Arquivamento para Usuários

 

_**Tópico modificado em:** 2012-10-09_

É possível habilitar ou desabilitar o Arquivamento para usuários específicos criando e configurando uma política de Arquivamento para usuários e aplicando a política para usuários ou grupos de usuários específicos. As políticas de usuário substituem qualquer política global ou locais. As políticas de arquivamento se aplicam apenas se você não usar a integração do Microsoft Exchange ou se você usar a integração do Microsoft Exchange, mas possui alguns usuários que não estão hospedados no Exchange 2013 e possuem caixas de correio colocadas em Retenção Local.

Para obter detalhes sobre como as políticas de Arquivamento funcionam, incluindo a hierarquia para políticas de usuário, global e local, consulte a documentação de Planejamento, de Implantação ou Operações do [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md).

> [!NOTE]  
> Se você habilitar a integração do Microsoft Exchange para sua implantação, as políticas de Retenção Local do Exchange controlam se o arquivamento está habilitado para usuários hospedados no Exchange 2013 e possuem caixas de correio em Retenção Local. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.<br />Você deve especificar todas as opções adequadas nas configurações de Arquivamento antes de habilitar o Arquivamento de comunicações internas e externas nas políticas de Arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na documentação de Implantação.

## Nesta seção

  - [Configurando Políticas de Usuário para Arquivamento no Lync Server](lync-server-2013-setting-up-user-policies-for-archiving-in-lync-server.md)

  - [Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server](lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md)

