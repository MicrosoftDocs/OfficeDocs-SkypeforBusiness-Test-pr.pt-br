---
title: 'Lync Server 2013: Tempo de recuperação para failover e failback de pool'
TOCTitle: Tempo de recuperação para failover e failback de pool
ms:assetid: 902c658f-8442-4d0d-b3ad-bf795ecd550d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205079(v=OCS.15)
ms:contentKeyID: 49307438
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tempo de recuperação para failover e failback de pool no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-10_

Para failover e failback de pool, o alvo projetado para objetivo de tempo de recuperação (RTO) é de 30 minutos. Este é o tempo necessário para o failover acontecer, após os administradores terem determinado que houve um desastre e iniciar os procedimentos de failover. Isso não inclui o tempo para os administradores avaliarem a situação e tomar uma decisão, nem inclui o tempo dos usuários entrarem novamente após o failover ser concluído.

Para failover e failback de pool, o alvo projetado para objetivo de tempo de recuperação (RTO) é de 30 minutos. Isso representa o tempo medido dos dados que pode ser perdido devido ao desastre, devido à latência de replicação do serviço de backup. Por exemplo, se um pool cai às 10:00 A.M., e o RPO é 30 minutos, os dados gravados no pool entre 9:30 A.M. e 10:00 A.M. podem não ter sido replicados no pool de back up, e serão perdidos.

Todos os números de RTO e RPO neste documento supõem que os dois data centers estão localizados na mesma região com alta velocidade e trasporte de baixa latência entre os dois locais. Esses números são medidos para um pool com 40.000 usuários ativos ao mesmo tempo e 200.000 usuários habilitados para Lync com respeito ao modelo de usuário predefinido, onde não há backlog na replicação de dados. Eles estão sujeitos à alteração baseado no teste e validação de desempenho.

