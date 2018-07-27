---
title: Migração do Office Communications Server 2007 R2 para Lync Server 2013
TOCTitle: Migração do Office Communications Server 2007 R2 para Lync Server 2013
ms:assetid: f3fa4f5f-e9a2-4fb7-a12d-20f04173e697
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205375(v=OCS.15)
ms:contentKeyID: 49308588
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migração do Office Communications Server 2007 R2 para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Os tópicos desta seção guiam você ao longo do processo de migração do Office Communications Server 2007 R2 para o Lync Server 2013

> [!IMPORTANT]  
> Este documento descreve as etapas geralmente necessárias para realizar cada fase de migração. Não resolve todos os cenários de migração possíveis ou de topologia de implantação herdada. Portanto, você pode não precisar realizar cada etapa descrita ou pode precisar realizar etapas adicionais, dependendo da sua implantação. Este documento também oferece exemplos de etapas de verificação. Estas etapas de verificação são oferecidas para ajudar na compreensão do que é necessário procurar para garantir que cada fase seja concluída com êxito conforme você progride na sua implantação. Personalize estas etapas de verificação para seu processo de migração específico.

Este guia oferece informações específicas para atualizar sua implantação existente. Explica como alterar sua topologia existente. Este guia não aborda a implementação de novos recursos. Quando um procedimento detalhado é documentado em outro local, este guia orienta você para o documento ou seção adequado.

Este documento define os termos conforme especificados na lista a seguir.

  - *migração*   
    Movendo sua implantação de produção de uma versão anterior de Office Communications Server 2007 R2 para Lync Server 2013.

<!-- end list -->

  - *atualização*   
    Instalar uma versão mais nova do software em um servidor ou computador cliente.

<!-- end list -->

  - *coexistência*   
    O ambiente temporário que existe durante a migração quando algumas funcionalidades podem ter sido migradas para o Lync Server 2013 e outra funcionalidade permanece na versão anterior do Office Communications Server 2007 R2.

<!-- end list -->

  - *interoperabilidade*   
    A capacidade da sua implantação operar com êxito durante o período de coexistência.

## Nesta seção

  - [Antes de começar a migração](before-you-begin-the-migration_1.md)

  - [Fases de migração](migration-phases_1.md)

  - [Fase 1: Planeje sua migração do Office Communications Server 2007 R2](phase-1-plan-your-migration-from-office-communications-server-2007-r2.md)

  - [Fase 2: Preparar para migração](phase-2-prepare-for-migration_1.md)

  - [Fase 3: Implantar pool piloto do Lync Server 2013](phase-3-deploy-lync-server-2013-pilot-pool_1.md)

  - [Fase 4: Mesclar topologias](phase-4-merge-topologies.md)

  - [Fase 5: Configurar o pool piloto](phase-5-configure-the-pilot-pool.md)

  - [Fase 6: Mover usuários ao pool piloto](phase-6-move-users-to-the-pilot-pool.md)

  - [Fase 7: Adicionar o Servidor de Borda do Lync Server 2013 ao pool piloto](phase-7-add-lync-server-2013-edge-server-to-pilot-pool.md)

  - [Fase 8: Mover de implantação piloto para produção](phase-8-move-from-pilot-deployment-into-production.md)

  - [Fase 9: Concluir tarefas pós-migração](phase-9-complete-post-migration-tasks.md)

  - [Fase 10: Site herdado encerrado](phase-10-decommission-legacy-site.md)

