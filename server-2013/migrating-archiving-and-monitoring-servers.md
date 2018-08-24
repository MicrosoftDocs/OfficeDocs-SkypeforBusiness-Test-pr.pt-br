---
title: Migrando servidores de Arquivamento e de Monitoramento
TOCTitle: Migrando servidores de Arquivamento e de Monitoramento
ms:assetid: 77831579-df45-4697-b8c5-207b74a07a40
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205015(v=OCS.15)
ms:contentKeyID: 49307163
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando servidores de Arquivamento e de Monitoramento

 

_**Tópico modificado em:** 2012-10-02_

Se você implantou o Servidor de Arquivamento e o Monitoring Server em seu ambiente do Lync Server 2010, pode implantar esses servidores em seu ambiente do Lync Server 2013 depois de migrar seus pools de Front-End. Se as funcionalidades de arquivamento e monitoração forem críticas para a organização, no entanto, adicione arquivamento e monitoramento ao ao pool piloto do Lync Server 2013 antes de migrar, de forma que a funcionalidade fique disponível durante o processo de migração.

Se você deseja as funcionalidades de arquivamento e monitoração durante o processo de migração, lembre das considerações a seguir:

  - Os dados de arquivamento e monitoração não são movidos para a implementação do Lync Server 2013. Os dados submetidos ao backup antes de desprogramar o ambiente de legado serão seu histórico da atividade no ambiente do Lync Server 2010.

  - A versão para Lync Server 2010 do Servidor de Arquivamento e Servidor de Monitoração só pode ser associada com um pool de Front-End do Lync Server 2010. No Lync Server 2013, o Arquivamento e Monitoramento não são mais funções de servidor, mas serviços integrados no pool de Front-End do Lync Server 2013.

  - Durante o período em que o legado e a implementação do Lync Server 2013 coexistirem, a versão do Lync Server 2010 de Servidor de Arquivamento e Monitoring Server coleta dados para os usuários hospedados em pools do Lync Server 2010. Arquivamento e Monitoramento no Lync Server 2013 coletam dados para os usuários hospedados em pools do Lync Server 2013.
    
    > [!NOTE]  
    > Durante a fase de migração, quando você ainda está usando servidor de borda legado com o novo pool piloto do Lync Server 2013, a versão do Lync Server 2010 de Servidor de Arquivamento continua coletando dados para os usuários hospedados em pools do Lync Server 2010 e o Arquivamento no Lync Server 2013 coleta dados para usuários hospedados em pools do Lync Server 2013.

  - Se você usar uma solução de arquivamento e monitoração de terceiros junto com Arquivamento e Monitoramento no Lync Server 2013, consulte seu fornecedor sobre quando e como precisa integrar a solução com o Lync Server 2013.

