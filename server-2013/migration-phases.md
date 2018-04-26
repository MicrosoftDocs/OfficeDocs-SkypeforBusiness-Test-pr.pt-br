---
title: Fases de migração
TOCTitle: Fases de migração
ms:assetid: cb7747ba-b872-42ca-ab41-76e3c4e77d06
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205336(v=OCS.15)
ms:contentKeyID: 49308120
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fases de migração

 

_**Tópico modificado em:** 2012-09-17_

No Lync Server 2013, você define os sites da sua rede que contêm os componentes do Lync Server 2013. Um site é um conjunto de computadores bem conectados por uma rede de baixa latência e alta velocidade, como uma única LAN ou duas redes conectadas por uma rede de fibra óptica de alta velocidade.

Um *Pool de front-end* é um conjunto de servidores de front-end configurados identicamente e que trabalham juntos para oferecer serviços para um grupo de usuários comum. Um pool oferece escalabilidade e capacidade de failover aos seus usuários. Cada servidor em um pool deve executar uma função ou funções do servidor idênticas. Um Servidor Standard Edition, projetado para pequenas empresas, também define um pool e execute em um único servidor. Isto permite você ter a funcionalidade do Lync Server 2013 por um custo menor, mas não oferece uma verdadeira solução de alta disponibilidade.

As fases a seguir descrevem o processo de uma migração do pool do Lync Server 2010 para o Lync Server 2013. Para vários sites que contêm pools, cada pool individual deve seguir esta abordagem por fase.

1.  [Fase 1: Planejar a migração do Lync Server 2010](phase-1-plan-your-migration-from-lync-server-2010.md)

2.  [Fase 2: Preparar para migração](phase-2-prepare-for-migration.md)

3.  [Fase 3: Implantar o pool piloto do Lync Server 2013](phase-3-deploy-lync-server-2013-pilot-pool.md)

4.  [Fase 4: Mover usuários de teste para o pool piloto](phase-4-move-test-users-to-the-pilot-pool.md)

5.  [Fase 5: Adicionar o Servidor de Borda do Lync Server 2013 ao pool piloto](phase-5-add-lync-server-2013-edge-server-to-pilot-pool.md)

6.  [Fase 6: Mover da implatação piloto para produção](phase-6-move-from-pilot-deployment-into-production.md)

7.  [Fase 7: Concluir tarefas pós-migração](phase-7-complete-post-migration-tasks.md)

8.  [Fase 8: Encerrar os Pools herdados](phase-8-decommission-legacy-pools.md)

