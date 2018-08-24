---
title: Configurando Políticas de Usuário para Arquivamento no Lync Server
TOCTitle: Configurando Políticas de Usuário para Arquivamento no Lync Server
ms:assetid: 22d6cc76-6b5c-4a8c-bb8a-7996450ec085
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204742(v=OCS.15)
ms:contentKeyID: 49306130
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Políticas de Usuário para Arquivamento no Lync Server

 

_**Tópico modificado em:** 2012-10-10_

Habilitar ou desabilitar o Arquivamento para usuários específicos hospedados no Lync Server 2013 exige a criação e configuração de uma ou mais políticas do usuário e a aplicação da política adequada para usuários ou grupos de usuários específicos. As políticas de usuário substituem as políticas local e global, mas apenas para usuários hospedados no Lync Server 2013.

Os usuários são sempre hospedados no Lync Server. Se a integração do Microsoft Exchange está habilitada, os usuários cujas caixas de correio estão no Microsoft Exchange Server 2013, não precisam ter políticas de Arquivamento no Lync Server gerenciado. Estes usuários com Arquivamento serão gerenciados pela Retenção Local do Exchange.

Para obter detalhes sobre como as políticas de Arquivamento funcionam, incluindo a hierarquia para políticas globais, locais e de usuário, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação e Operações.

> [!NOTE]  
> Se você habilitou a integração do Microsoft Exchange para sua implantação, as políticas de Retenção Local do Exchange controlam se o arquivamento está habilitado para usuários hospedados no Exchange 2013. O arquivamento destes usuários exigem que eles tenham caixas de correio em Retenção Local. Para obter mais detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.<br />Você deve especificar todas as opções adequadas nas configurações de Arquivamento antes de habilitá-lo. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na documentação de Implantação.

## Nesta seção

  - [Criando e Configurando Políticas de Usuário para Arquivamento no Lync Server](lync-server-2013-creating-and-configuring-user-policies-for-archiving-in-lync-server.md)

  - [Aplicando uma política de arquivamento do Lync Server ao usuário](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md)

