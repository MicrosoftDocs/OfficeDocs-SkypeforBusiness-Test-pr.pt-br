---
title: 'Lync Server 2013: Definindo seus requisitos para Arquivamento'
TOCTitle: Definindo os requisitos de sua organização para Arquivamento
ms:assetid: ce0fc0f6-7704-4b80-bf19-a1fa9818fc7a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205276(v=OCS.15)
ms:contentKeyID: 49308151
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos para Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-09_

Se sua organização deve seguir os regulamentos de conformidade, é possível implantar o Arquivamento para habilitar o suporte de arquivamento para mensagem instantânea (IM) e conferência (reuniões) do Lync Server 2013. Para obter detalhes sobre o tipo de conteúdo que pode ser arquivado, consulte [Visão geral de Arquivamento no Lync Server 2013](lync-server-2013-overview-of-archiving.md) na documentação de Planejamento.

Para implementar o Arquivamento, você precisa primeiro decidir como atender os requisitos da sua organização para Arquivamento. Isto exige determinar o seguinte:

  - **Quando implantar o Arquivamento**. É possível implantar o Arquivamento como parte da sua implantação inicial do Lync Server 2013 ou pode adicioná-lo a uma implantação existente. Você implanta o Arquivamento usando o Construtor de Topologias para adicioná-lo em sua topologia e publicar a topologia.

  - **Arquivar comunicações internas ou externas ou não**. É possível habilitar o arquivamento para comunicações internas (comunicações entre usuários internos), comunicações externas (comunicações que incluem pelo menos um usuário fora da sua rede interna) ou ambos. É possível especificar estas opções para toda sua organização ou é possível especificá-lo para locais ou pools específicos. Por padrão, nenhuma opção é habilitada.
    
    > [!NOTE]  
    > Se você usar a integração do Microsoft Exchange para armazenar os dados arquivados, suas configurações do Exchange controlam se as comunicações do Lync são arquivadas. Se sua implantação inclui várias florestas, você deve sincronizar as configurações entre Lync Server e Exchange. Controlar o arquivamento para comunicações internas ou externas está disponível apenas para a política do Lync. Para o arquivamento integrado do Exchange, ambos serão arquivados ou não arquivados.

  - **Por que habilitar o Arquivamento**. É possível habilitar e desabilitar o Arquivamento para toda sua implantação a nível global e pode habilitar e desabilitar o Arquivamento para sites e usuários específicos. Em cada um destes níveis, você especifica se deve habilitar o arquivamento de sessões de IM (ponto a ponto), conferências (reuniões, que são sessões de várias partes) ou ambos. Por padrão, o Arquivamento está desabilitado.

  - **Como o Arquivamento crítico funciona para os usuários na sua organização**. Se o arquivamento é fundamental para missão da sua organização, é possível especificar que o Lync Server 2013 funcione no modo crítico, que bloqueia sessões de IM e conferência se o arquivamento falhar. Por exemplo:
    
      - Se o serviço de Arquivamento estiver temporariamente indisponível para enviar uma mensagem para a fila de banco de dados ou inserir uma mensagem no banco de dados), a funcionalidade de IM e conferência é bloqueada na implantação até que o suporte de arquivamento seja restaurado.
    
      - Se um usuário de conferência carregar um arquivo, mas o arquivo não pode ser copiado para o repositório de arquivo de arquivamento, a funcionalidade de conferência é bloqueada na implantação até que o problema seja resolvido, mas a funcionalidade de IM não é bloqueada.
    
    É possível configurar esta opção a nível global, nível local ou nível do pool. Por padrão, o modo crítico não está habilitado.

  - **Usar a integração do Microsoft Exchange ou não**. Esta opção integra o armazenamento de Arquivamento com seu armazenamento do Exchange 2013, para que seus dados arquivados do Lync Server e dados arquivados do Exchange 2013 são armazenados juntos no Exchange. É possível usar a integração do Microsoft Exchange para armazenar os dados de arquivamento para usuários hospedados no Exchange 2013, se suas caixas de correio foram colocados em Retenção Local. Se você não tiver uma implantação do Exchange 2013 ou se você prefere não integrar ou se possui qualquer usuário do Lync não hospedado no Exchange 2013, é possível implantar bancos de dados de Arquivamento separados utilizando o SQL Server para armazenar dados arquivados das comunicações do Lync. É possível configurar a opção de integração do Microsoft Exchange a nível global, local e do pool. Por padrão, a integração do Microsoft Exchange não está habilitada.

  - **Como os dados arquivados devem ser gerenciados**. O banco de dados de arquivamento não é destinado para retenção de longo prazo e o Lync Server 2013 não oferece uma solução de e-discovery (pesquisa) para dados arquivados, portanto, os dados precisam ser movidos para outro armazenamento. O Lync Server não oferece uma ferramenta de exportação de sessão que você pode usar para exportar dados arquivados e que cria transcrições de pesquisa para os dados arquivados. Para a política global e para cada política de usuário e local que você criar, é possível habilitar a exclusão de dados e especificar uma das seguintes opções:
    
      - Excluir os dados de arquivamento exportados e os dados de arquivamento armazenados após um número específico de dias. O número mínimo de dias que você pode especificar é um dia. O número máximo de dias que você pode especificar é 2562 dias.
    
      - Excluir apenas dados de arquivamento exportados. Esta opção exclui todos os registros exportados e os marca como seguro para excluir através da ferramenta de exportação de sessão.
    
    É possível configurar esta opção a nível global, nível local e nível de pool. Por padrão, a exclusão não está habilitada.

Você controla o Arquivamento usando um dos seguintes métodos:

  - **Políticas de arquivamento**. Você usa um ou mais políticas de Arquivamento para habilitar e desabilitar o arquivamento de comunicações externas e internas. Por padrão, nenhum arquivamento está habilitado. Você habilita ou desabilita o Arquivamento para comunicações internas, comunicações externas ou ambos em sua implantação usando a política global padrão. Não é possível excluir a política global. É possível especificar uma ou mais políticas locais opcionais para habilitar ou desabilitar o Arquivamento para comunicações internas e externas de locais específicos. Também é possível especificar uma ou mais políticas de usuário para habilitar ou desabilitar o Arquivamento para usuários e grupos de usuários específicos. As políticas a nível de usuário substituem as políticas locais. As políticas a nível local substituem as políticas a nível global. As políticas a nível de usuário são implementadas apenas para usuários específicos configurados para usar a política. Mensagens instantâneas de grupo e conferências são arquivadas apenas se uma política para pelo menos um dos participantes é configurada para habilitar o arquivamento.
    
    > [!NOTE]  
    > Se você usar a integração do Microsoft Exchange, as políticas do Exchange 2013 substituem as políticas de Arquivamento do Lync Server para todos os usuários hospedados nos servidores do Exchange 2013.

  - **Configurações de Arquivamento**. Você usa uma ou mais configurações de Arquivamento para especificar a maioria das opções de Arquivamento descritas anteriormente neste tópico, exceto para habilitar o arquivamento de comunicações internas e externas (configuradas usando políticas de Arquivamento, conforme descrito no indicador anterior). As configurações de arquivamento inclui a configuração global padrão e as configurações de pool e local opcionais. Não é possível excluir a configuração global. As configurações a nível de pool substituem as configurações a nível local. As configurações a nível local substituem as configurações a nível global.

Como parte da sua análise de requisitos, você precisa determinar como configurar a configuração de Arquivamento global e a política de Arquivamento global. Você também precisa determinar seus requisitos para qualquer configuração de Arquivamento de nível local, configurações de Arquivamento de nível de pool, políticas de Arquivamento de nível local e políticas de Arquivamento de nível de usuário.

Se você implantar o Arquivamento para um pool de Front-end ou servidor do Standard Edition, você deve também habilitá-lo para todos os outros pools de Front-end e servidores do Standard Edition na sua implantação. Você precisa fazer isso porque os usuários cujas comunicações precisam ser arquivadas podem ser convidados para uma conversa de IM de grupo ou reuniões hospedadas em um pool diferente. Se o arquivamento não está habilitado no pool onde a conversa ou reunião é hospedada, todos os dados de conferência podem não ser arquivados. O arquivamento ainda funciona para os usuários habilitados para arquivamento e todas as mensagens de IM, mas o conteúdo de conferência e eventos podem não ser arquivados.

> [!NOTE]  
> Para habilitar a delegação de tarefas administrativas enquanto mantém os padrões de segurança da sua organização, o Lync Server 2013 usa RBAC. Com RBAC, o privilégio administrativo é concedido atribuindo usuários às funções administravas predefinidas. Para configurar políticas de Arquivamento do Lync e configurações de Arquivamento, o usuário deve ser atribuído à função CsArchivingAdministrator (a não ser que a configuração seja realizada diretamente no servidor onde o Arquivamento é implantado, ao invés de remotamente de outro computador). Para obter detalhes sobre o RBAC, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento. Para obter uma lista de direitos, permissões e funções do usuário necessárias para implantação de arquivamento, consulte <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lista de verificação da implantação para Arquivamento no Lync Server 2013</a>, que está disponível na documentação de Planejamento e de Implantação.<br />Se você usar a integração do Microsoft Exchange, a configuração das políticas do Exchange exigem direitos e permissões de administrador adequadas. Para obter detalhes, consulte a documentação do Exchange 2013.
