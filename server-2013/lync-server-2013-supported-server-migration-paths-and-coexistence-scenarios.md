---
title: 'Lync Server 2013: Caminhos de migração de servidor suportado e cenários de coexistência'
TOCTitle: Caminhos de migração de servidor suportado e cenários de coexistência
ms:assetid: 2a6a730f-7f80-45f9-9540-3edfdaa265fb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425764(v=OCS.15)
ms:contentKeyID: 49306210
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Caminhos de migração de servidor suportado e cenários de coexistência no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-16_

O Lync Server 2013 dá suporte à migração de qualquer um dos seguintes itens:

  - Microsoft Lync Server 2010

  - Microsoft Office Communications Server 2007 R2

A migração de um ambiente executando ambas as versões anteriores não é suportada. A migração de versões anteriores, como o Microsoft Office Communications Server 2007 ou o Live Communications Server 2005, não é suportada. Se suas implantações anteriores incluiu o Chat de Grupo, você deve migrar separadamente.

## Métodos de migração

A migração de todas as topologias e funções de servidor do Lync Server é suportada. É possível migrar de uma topologia para uma topologia diferente, incluindo do servidor Standard Edition para o servidor Enterprise Edition.

O Lync Server 2013 suporta apenas o seguinte método de migração:

   **Migração lado a lado.** Na migração lado a lado, o Lync Server 2013 é implantando junto com uma implantação existente do Microsoft Lync Server 2010 ou do Office Communications Server 2007 R2 e, em seguida, você transfere as operações para o novo servidor e move os usuários para o Lync Server 2013. Esse método exige plataformas de servidor adicionais, incluindo hardware e software, durante a migração, e nomes de sistema e de pool são diferentes na nova configuração. Se for necessário reverter para a versão anterior, você poderá retornar as operações para os servidores anteriores.

A migração entre florestas do Serviços de Domínio Active Directory não é suportada.

O caminho de migração recomendado é uma abordagem de base. Para obter detalhes sobre a migração de uma versão anterior, incluindo a fase adequada da implantação de componente, consulte os seguintes tópicos na documentação de Migração:

  - [Migração do Lync Server 2010 para o Lync Server 2013](migration-from-lync-server-2010-to-lync-server-2013.md)

  - [Migração do Office Communications Server 2007 R2 para Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md)

  - [Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)

## Cenários de coexistência

O Lync Server 2013 pode coexistir com componentes de uma implantação do Lync Server 2010 ou do Office Communications Server 2007 R2. A implantação simultânea do Lync Server 2013 com Lync Server 2010 e Office Communications Server 2007 R2 (implantação simultânea de todas as três versões) não é suportada.

Durante uma migração em fases na qual uma implantação anterior do Lync Server 2013 ou do Office Communications Server 2007 R2 coexiste temporariamente com a nova implantação do Lync Server 2010, o suporte para o roteamento de versão mista é limitado. Para obter detalhes, consulte a documentação Migração.

Você deve separar e distinguir os computadores executando o Microsoft SQL Server 2008 R2 ou o Microsoft SQL Server 2012 para suas instâncias do banco de dados do Lync Server 2013. Não é possível usar a mesma instância do SQL Server para um pool de Front-end do Lync Server 2013 que você usa para um Lync Server 2010 ou pool de front-end do Office Communications Server 2007 R2. Se você definir e configurar o Lync Server 2013 no Construtor de Topologias para uma implantação que já possui o Lync Server 2010 ou Office Communications Server 2007 R2 implantado, Construtor de Topologias não permitirá definir uma instância de um Lync Server 2013 que já está em uso na topologia.

O Construtor de Topologias exibirá a seguinte mensagem para informar deste problema: "O SQL server \[FQDN do servidor\] já contém uma instância do SQL hospedando a função 'Repositório do Usuário'."

> [!NOTE]  
> Se você pretende implantar funções do servidor novos para sua implantação do Lync Server 2013, deve primeiro atualizar sua implantação existente conforme descrito na documentação de Migração e de Implantação e implantar as novas funções do servidor conforme descrito na documentação de Planejamento e Implantação. Se estiver migrando de uma versão anterior do Chat de Grupo, migre por último, após concluir o processo para migrar todos os outros componentes do Lync Server 2010 ou Office Communications Server 2007 R2.

Para requisitos de coexistência específicos e outros detalhes sobre a coexistência e migração do Lync Server 2010 ou Office Communications Server 2007 R2 e componentes do Lync Server 2013, consulte [Migração do Lync Server 2010 para o Lync Server 2013](migration-from-lync-server-2010-to-lync-server-2013.md) e [Migração do Office Communications Server 2007 R2 para Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md) na documentação de Migração. Para obter detalhes sobre a versão mista de suporte para clientes, consulte [Clientes com suporte de implantações anteriores no Lync Server 2013](lync-server-2013-supported-clients-from-previous-deployments.md).

