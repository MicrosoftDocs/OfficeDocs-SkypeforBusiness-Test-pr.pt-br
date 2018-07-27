---
title: Migrando servidores de Arquivamento e de Monitoramento
TOCTitle: Migrando servidores de Arquivamento e de Monitoramento
ms:assetid: 8d879253-ad76-42b7-8386-e44b110239cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688124(v=OCS.15)
ms:contentKeyID: 49886304
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando servidores de Arquivamento e de Monitoramento

 

_**Tópico modificado em:** 2012-10-02_

Se você implantou o Servidor de Arquivamento e o Servidor de Monitoração em seu Office Communications Server 2007 R2, pode implantar esses servidores em seu ambiente do Lync Server 2013 depois de migrar seus pools de Front-End. Se as funcionalidades de arquivamento e monitoração forem cruciais para a organização, no entanto, você deverá adicionar o Arquivamento e Monitoramento ao pool piloto antes de migrar, de forma que a funcionalidade fique disponível durante o processo de migração.

Se você deseja as funcionalidades de arquivamento e monitoração durante a migração e a fase de coexistência, lembre-se das considerações a seguir:

  - Os dados de arquivamento e monitoração não são movidos para a implementação do Lync Server 2013. Os dados submetidos ao backup antes de desprogramar o ambiente de legado serão seu histórico da atividade no Office Communications Server 2007 R2.

  - A versão para Office Communications Server 2007 R2 do Servidor de Arquivamento e Servidor de Monitoração só pode ser associada com um pool de Front-End do Office Communications Server 2007 R2. No Lync Server 2013, o Arquivamento e Monitoramento não são mais funções de servidor, mas serviços integrados no pool de Front-End do Lync Server 2013.

  - Durante o período em que suas implantações legada e do Lync Server 2013 coexistirem, a versão do Office Communications Server 2007 R2 de Servidor de Arquivamento e Servidor de Monitoração coletará dados para os usuários hospedados em pools do Office Communications Server 2007 R2. A versão do Lync Server 2013 de Servidor de Arquivamento e Servidor de Monitoração coleta dados para os usuários hospedados em pools do Lync Server 2013.
    
    > [!NOTE]  
    > Durante a fase de migração, quando você ainda está usando seu servidor borda de legado com o novo pool piloto do Lync Server 2013, a versão do Office Communications Server 2007 R2 de Servidor de Arquivamento continua coletando dados para os usuários hospedados em pools do Office Communications Server 2007 R2 e a versão do Lync Server 2013 de Servidor de Arquivamento coleta dados para usuários hospedados em pools do Lync Server 2013.

  - Se você usar uma solução de arquivamento e monitoração de terceiros junto com o Servidor de Arquivamento e o Servidor de Monitoração, converse com o fornecedor sobre quando e como precisa integrar a solução com o Lync Server 2013.

