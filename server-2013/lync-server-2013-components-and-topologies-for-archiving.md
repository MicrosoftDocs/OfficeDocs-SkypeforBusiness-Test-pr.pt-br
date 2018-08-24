---
title: 'Lync Server 2013: Componentes e topologias para Arquivamento'
TOCTitle: Componentes e topologias para Arquivamento
ms:assetid: 5893063d-a44a-4034-aba9-cbe883ecf710
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204916(v=OCS.15)
ms:contentKeyID: 49306791
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-09_

Se você quiser arquivar o conteúdo de mensagens instantâneas e conferências do Lync Server 2013, é possível implementar o arquivamento no Lync Server.

## Componentes de arquivamento

O recurso de arquivamento inclui os seguintes componentes:

  - **Operadores de arquivamento**. Os operadores de arquivamento (também conhecido como operadores de coleta de dados unificados) são instalados e ativados automaticamente em cada pool de Front-Ends e servidor Standard Edition. Embora os operadores de arquivamento sejam ativados automaticamente, nenhuma mensagem será realmente capturada até o arquivamento ser habilitado e configurado adequadamente.

  - **Armazenamento de dados de arquivamento**. O armazenamento de dados do Lync Server 2013 pode ser uma das seguintes opções:
    
      - Armazenamento do Exchange 2013. Se você habilitar a opção de integração do Microsoft Exchange, as caixas de correio dos usuários hospedadas no servidor do Exchange 2013 utilizarão o armazenamento do Exchange 2013 para os dados arquivados, mas somente se as caixas de correio tiverem sido colocadas em bloqueio In-loco.
    
      - Armazenamento do SQL Server. Se você tiver usuários na sua implantação que estejam hospedados no Lync Server 2013, será possível configurar os bancos de dados de arquivamento que executam uma versão suportada do SQL Server para habilitar esses usuários.

O arquivamento também requer armazenamento de arquivos, mas o arquivamento utiliza o mesmo armazenamento de arquivos como servidores Front-End ou servidor Standard Edition.

Para obter uma lista de requisitos de hardware e de software para arquivamento, consulte [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) e [Suporte a software e à infraestrutura de servidor no Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md) na Documentação de suporte.

## Topologias suportadas

Você implanta o arquivamento em cada pool que possui usuários que requerem suporte ao arquivamento. O arquivamento é executado no Servidores Front-End nos pools do Enterprise Edition e no Servidores Standard Edition. O armazenamento de dados de arquivamento pode ser o seguinte:

  - Integrado ao armazenamento do Exchange 2013

  - Implantado utilizando bancos de dados do SQL Server separados

Se a sua implantação do Exchange 2013 não incluir todos os usuários na sua implantação do Lync Server, você deve utilizar a integração do Microsoft Exchange para os usuários cujas caixas de correio estejam hospedadas nos servidores do Exchange 2013 e deve implantar bancos de dados do SQL Server separados para todos os usuários do Lync para serem utilizados para arquivamento.

## Colocação com suporte

O Lync Server 2013 suporta uma variedade de cenários de colocação, permitindo a você ter flexibilidade para economizar custos de hardware executando múltiplos componentes em um servidor (se você tem uma pequena organização) ou executando componentes individuais em servidores diferentes (se você tiver uma grande organização que precisa de escalabilidade e desempenho). Os fatores de escalabilidade certamente devem ser considerados antes de você decidir se quer colocar componentes.

O arquivamento é implantado no Servidores Front-End de um pool ou Servidores Standard Edition. Para obter detalhes sobre os componentes que podem ser colocados lá, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md) na Documentação de suporte.

Se você utilizar bancos de dados do SQL Server separados para o arquivamento, em vez de ou além de integrar o armazenamento ao armazenamento do Exchange 2013, você pode colocar o banco de dados de arquivamento com qualquer uma das seguintes opções:

  - Banco de dados de monitoramento

  - Banco de dados back-end de um pool de Front-Ends Enterprise Edition

> [!NOTE]  
> O servidor que estiver hospedando o banco de dados de arquivamento pode hospedar outros bancos de dados. No entanto, ao considerar colocar o banco de dados de arquivamento com outros bancos de dados, saiba que se você estiver arquivando as mensagens de muitos usuários, o espaço em disco necessário para o banco de dados de arquivamento poderá aumentar bastante. Por essa razão, não recomendamos a colocação do banco de dados de arquivamento no banco de dados back-end.

Se você colocar o banco de dados de arquivamento com o banco de dados de monitoramento, banco de dados back-end ou ambos, é possível utilizar uma instância SQL exclusiva para qualquer ou todos os bancos de dados ou uma instância SQL separada para cada banco de dados, com a seguinte limitação:

  - Cada instância SQL pode conter somente um banco de dados back-end exclusivo, um banco de dados de monitoramento exclusivo e um banco de dados de arquivamento exclusivo.

Para obter detalhes sobre a colocação de todas as funções de servidor e bancos de dados, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md) na documentação de suporte.

