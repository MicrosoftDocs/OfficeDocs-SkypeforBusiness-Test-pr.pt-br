---
title: 'Lync Server 2013: Planejamento para emparelhamento de pool Front-End'
TOCTitle: Planejamento para emparelhamento de pool Front-End
ms:assetid: cca5773d-57ff-45ce-a7b4-f82ae697c477
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205293(v=OCS.15)
ms:contentKeyID: 49308140
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para emparelhamento de pool Front-End no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-28_

Para melhor capacidade de recuperação de desastres no Lync Server 2013, implante pares de pools do Front-End pools em dois locais dispersos geograficamente. Cada site contém um pool de Front-End que é emparelhado com um pool de Front-End correspondente em outro local. Ambos os locais estão ativos e o Serviço de Backup do Lync Server oferece replicação de dados em tempo real para manter os pools sincronizados. O Serviço de Backup é um novo recurso no Lync Server 2013, projetado para suportar a solução de recuperação de desastres. Está instalado em um pool de Front-End ao emparelhar o pool com outro pool de Front-End.

Se o pool em um local falhar, é possível fazer o failover dos usuários deste pool para o pool em outro local, que oferece serviços para todos os usuários em ambos os pools. Para fins de planejamento de capacidade, cada pool deve ser atribuído para lidar com cargas de trabalho de todos os usuários em ambos os pools em caso de desastre.

## Nesta seção

  - [Opções e práticas recomendadas de emparelhamento de pool com suporte para o Lync Server 2013](lync-server-2013-supported-pool-pairing-options-and-best-practices.md)

  - [Relacionamentos de Registradores de backup no Lync Server 2013](lync-server-2013-backup-registrar-relationships.md)

  - [Tempo de recuperação para failover e failback de pool no Lync Server 2013](lync-server-2013-recovery-time-for-pool-failover-and-pool-failback.md)

  - [Failover do repositório do Gerenciamento Central no Lync Server 2013](lync-server-2013-central-management-store-failover.md)

  - [Segurança de dados de emparelhamento do pool Front End no Lync Server 2013](lync-server-2013-front-end-pool-pairing-data-security.md)

