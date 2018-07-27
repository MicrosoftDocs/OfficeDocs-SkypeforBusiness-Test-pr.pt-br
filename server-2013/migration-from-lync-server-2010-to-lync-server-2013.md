---
title: Migração do Lync Server 2010 para o Lync Server 2013
TOCTitle: Migração do Lync Server 2010 para o Lync Server 2013
ms:assetid: ef99d4a9-a666-4a92-9994-4d7930f70d55
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205369(v=OCS.15)
ms:contentKeyID: 49308537
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migração do Lync Server 2010 para o Lync Server 2013

 

_**Tópico modificado em:** 2012-09-17_

Os tópicos desta seção guiam você ao longo do processo de migração do Lync Server 2010 para o Lync Server 2013.

> [!IMPORTANT]  
> Este documento descreve as etapas geralmente necessárias para realizar cada fase de migração. Não resolve todos os cenários de migração possíveis ou de topologia de implantação herdada. Portanto, você pode não precisar realizar cada etapa descrita ou pode precisar realizar etapas adicionais, dependendo da sua implantação. Este documento também oferece exemplos de etapas de verificação. Estas etapas de verificação são oferecidas para ajudar na compreensão do que é necessário procurar para garantir que cada fase seja concluída com êxito conforme você progride na sua implantação. Personalize estas etapas de verificação para seu processo de migração específico.

Este guia oferece informações específicas para atualizar sua implantação existente. Explica como alterar sua topologia existente. Este guia não aborda a implementação de novos recursos. Quando um procedimento detalhado é documentado em outro local, este guia orienta você para o documento ou seção adequado.

Este documento define os termos conforme especificados na lista a seguir.

  - *migração*   
    Movendo sua implantação de produção de uma versão anterior de Lync Server 2010 para Lync Server 2013.

<!-- end list -->

  - *atualização*   
    Instalar uma versão mais nova do software em um servidor ou computador cliente.

<!-- end list -->

  - *coexistência*   
    O ambiente temporário que existe durante a migração quando algumas funcionalidades podem ter sido migradas para o Lync Server 2013 e outra funcionalidade permanece na versão anterior do Lync Server 2010.

<!-- end list -->

  - *interoperabilidade*   
    A capacidade da sua implantação operar com êxito durante o período de coexistência.

## Nesta seção

  - [Antes de começar a migração](before-you-begin-the-migration.md)

  - [Fase 1: Planejar a migração do Lync Server 2010](phase-1-plan-your-migration-from-lync-server-2010.md)

  - [Fase 2: Preparar para migração](phase-2-prepare-for-migration.md)

  - [Fase 3: Implantar o pool piloto do Lync Server 2013](phase-3-deploy-lync-server-2013-pilot-pool.md)

  - [Fase 4: Mover usuários de teste para o pool piloto](phase-4-move-test-users-to-the-pilot-pool.md)

  - [Fase 5: Adicionar o Servidor de Borda do Lync Server 2013 ao pool piloto](phase-5-add-lync-server-2013-edge-server-to-pilot-pool.md)

  - [Fase 6: Mover da implatação piloto para produção](phase-6-move-from-pilot-deployment-into-production.md)

  - [Fase 7: Concluir tarefas pós-migração](phase-7-complete-post-migration-tasks.md)

  - [Fase 8: Encerrar os Pools herdados](phase-8-decommission-legacy-pools.md)

