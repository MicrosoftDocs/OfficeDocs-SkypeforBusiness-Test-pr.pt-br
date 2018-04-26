---
title: 'Lync Server 2013: Novos recursos do aplicativo de Grupo de Resposta'
TOCTitle: Novos recursos do aplicativo de Grupo de Resposta
ms:assetid: 569544b4-fa97-429b-97e6-568afab6c19b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398373(v=OCS.15)
ms:contentKeyID: 49306757
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novos recursos do aplicativo de Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

O aplicativo Grupo de Resposta permite rotear e enfileirar chamadas de entrada para pessoas designadas para finalidades especiais, tais como serviço de cliente, uma assistência técnica interna, ou suporte de telefone geral para um departamento.

Os seguintes recursos do aplicativo do Grupo de Resposta são novos no Lync Server 2013:

  - **Função do Gerenciador**
    
    O Lync Server 2013 introduz uma nova função do Gerenciador do Grupo de Resposta. Agora, há duas funções de gerenciamento para grupos de respostas: Grupo de Resposta Gerenciador e Grupo de Resposta Administrador. Enquanto os administradores do Grupo de Resposta ainda podem configurar qualquer elemento de qualquer grupo de respostas, os gerenciadores podem configurar somente determinados elementos, somente para os grupos de respostas que eles possuem.
    
    Essa melhoria no modelo de administração beneficia a escalabilidade do Grupo de respostas, especialmente para os cenários de implantação de grande porte.

  - **Alta disponibilidade**
    
    A alta disponibilidade suporta o Aplicativo Grupo de Resposta, na forma de espelhamento do SQL Server, está habilitada como parte da configuração geral e da implantação de alta disponibilidade do Lync Server 2013. Se você configurar a alta disponibilidade e perder a conectividade com o servidor Back-End primário, a função Grupo de respostas não seja afetada pelo aproveitamento do servidor Back-End espelhado.
    
    O suporte ao espelhamento SQL Server do Aplicativo Grupo de Resposta não pode ser habilitado individualmente ou configurado fora da configuração de alta disponibilidade geral do Lync Server 2013.

  - **Recuperação de desastres**
    
    A recuperação de desastres que suporta o Aplicativo Grupo de Resposta está habilitada como parte da configuração e implantação do Pools de Front-Ends emparelhado, que é parte da configuração de recuperação de desastres geral do Lync Server 2013. Além disso, os cmdlets de importação e exportação do Grupo de respostas suportam o processo de failover para o pool de backup e o processo de failback para o pool primário ou para um novo pool. Se uma interrupção ocorrer no pool primário, os grupos de respostas podem ser transferidos para o pool de backup e, em seguida, voltarem a funcionar no pool primário ou em um novo pool no qual a interrupção tenha terminado.

## Consulte Também

#### Outros Recursos

[Planejamento de grupos de resposta no Lync Server 2013](lync-server-2013-planning-for-response-groups.md)

