---
title: 'Lync Server 2013: Requisitos para publicar uma topologia'
TOCTitle: Requisitos para publicar uma topologia
ms:assetid: 841cdf5d-d884-414d-ab50-3bb681b622ed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg195733(v=OCS.15)
ms:contentKeyID: 49307325
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos para publicar uma topologia no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Este tópico descreve os requisitos de infraestrutura e software específicos para publicar uma topologia, seja utilizando o Construtor de Topologias ou a interface de linha de comando do Shell de Gerenciamento do Lync Server 2013. Esses requisitos são adicionais aos requisitos gerais de sistema operacional, software e permissões aplicáveis a todas as ferramentas administrativas do Lync Server 2013. Certifique-se de que todos os requisitos de ferramentas administrativas sejam atendidos antes da publicação da topologia.

  - É necessário executar o Construtor de Topologias em um computador que ingressou no mesmo domínio ou floresta da implantação do Lync Server 2013 que você estiver criando para que as etapas de preparação do Serviços de Domínio Active Directory já estejam concluídas, permitindo que você use as ferramentas administrativas no computador para publicar com êxito sua topologia.

  - Os computadores definidos na topologia devem ingressar no domínio e no AD DS, exceto os Servidores de Borda. No entanto, os computadores não precisam estar online quando você publica a topologia.

  - O compartilhamento de arquivo para o pool deve ser criado e está disponível para usuários remotos.

  - Para publicar um Pool de Front-Ends Enterprise Edition, o Servidor Back-End baseado no SQL Server deve ser ingressado ao domínio no qual você está implantando os servidores online e configurado com as regras de firewall adequadas para torná-lo disponível para usuários remotos. Para obter detalhes sobre como especificar exceções de firewall, consulte [Compreendendo os requisitos de firewall para Servidor SQL com Lync Server 2013](lync-server-2013-understanding-firewall-requirements-for-sql-server.md). Para outros detalhes sobre a configuração de SQL Server, consulte [Configurar o SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-for-lync-server.md).
    
    > [!NOTE]  
    > A Servidor Standard Edition tem um banco de dados colocado que aceitará a configuração publicada. Primeiro você deve executar a tarefa de instalação <strong>Prepare primeiro o servidor Standard Edition</strong> na Assistente de Implantação do Lync Server.

## Consulte Também

#### Tarefas

[Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md)  
[Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md)  

#### Conceitos

[Requisitos de software de ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-software-requirements.md)  
[Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md)  

#### Outros Recursos

[Direitos e permissões de administrador necessários para configuração e administração do Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

