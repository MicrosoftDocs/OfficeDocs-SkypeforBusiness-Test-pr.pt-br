---
title: Estabelecendo uma estratégia de restauração e backup
TOCTitle: Estabelecendo uma estratégia de restauração e backup
ms:assetid: f545a75f-bbc4-4968-b510-8f6f3920112b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202195(v=OCS.15)
ms:contentKeyID: 52057760
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Estabelecendo uma estratégia de restauração e backup

 

_**Tópico modificado em:** 2013-03-26_

Antes de poder desenvolver um plano de backup e restauração para o Lync Server, você precisa desenvolver uma estratégia adequada para as metas de sua organização. Para desenvolver uma estratégia de backup e restauração, você deverá:

  - Estabelecer prioridades de negócios.

  - Identificar os requisitos de backup e restauração.

## Estabelecer as prioridades comerciais

Avaliar as prioridades comerciais da sua organização. Geralmente, as prioridades comerciais primárias que afetam sua estratégia de backup e restauração são as seguintes:

  - Requisitos de continuidade comercial

  - Plenitude de dados

  - Criticidade de dados

  - Requisitos de portabilidade

  - Restrições de custo

Necessidades comerciais como essas ajudam a determinar os SLAs (contrato de nível de serviço) desenvolvidos com seus clientes. Os contratos de nível de serviço influenciam muito sua estratégia de backup e recuperação.

## Identificar os requisitos de backup e restauração

As prioridades de negócios e os contratos de nível de serviço atuam na determinação dos requisitos de sua organização para backup e restauração do Lync Server. Identifique e documente seus requisitos para o seguinte:

  - **Frequência dos backups**   Lembre-se de que, exceto para os pools de front-ends nas relações emparelhadas conforme descrito em [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md), o Lync Server oferece suporte apenas ao modelo de recuperação simples, o que significa que a restauração é feita para o último backup completo. Planeje detalhadamente a frequência em que você precisará de um backup completo. Para obter detalhes sobre as práticas recomendadas de frequência de backup, consulte [Práticas recomendadas para backup e restauração](lync-server-2013-best-practices-for-backup-and-restoration.md).

  - **Ferramentas de backup e restauração**   Inclua quem usará as ferramentas e em quais computadores. Para detalhes sobre as ferramentas analisadas neste tópico e as permissões necessárias, consulte [Requisitos de backup e restauração: ferramentas e permissões](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md).

  - **Localização do backup**   Identifica se os backups são mantidos local ou remotamente, levando em consideração a segurança e acessibilidade. Especifique a mídia a ser usada para os backups.

  - **Requisitos de hardware e software**   Identifique e documente seus requisitos de hardware e software exigidos, incluindo o hardware para armazenamento de backup e restauração de componentes específicos e qualquer conectividade de rede e software necessária para suportar o backup e restauração. Conforme você desenvolve seus requisitos de hardware e software, lembre-se dos vários cenários de restauração a seguir.

  - **Cenários de restauração**   Eis aqui o processo de restauração para os seguintes cenários:
    
      - Um pool do Lync Server falha. Esse cenário exige a recompilação de cada servidor no pool.
    
      - Um Servidor Standard Edition falha. Este cenário exige a recompilação do servidor em um computador novo ou limpo e bancos de dados de restauração.
    
      - Perda do Repositório de Gerenciamento Central. Como mínimo, este cenário exige a restauração e publicação do Repositório de Gerenciamento Central.
    
      - Perda do servidor back-end quando o Repositório de Gerenciamento Central ainda estiver funcionando normalmente. Este cenário exige a recompilação do servidor em um computador novo ou limpo e a restauração dos bancos de dados.
    
      - Um servidor membro de um pool do Lync Server falha. Esse cenário exige a recompilação do servidor em um computador novo ou limpo.
    
      - Um Repositório de Arquivos falha. Este cenário exige a restauração do servidor de arquivos ou cluster de arquivos.
    
      - Um banco de dados de arquivamento, monitoramento ou chat persistente falha. Este cenário exige a recriação dos bancos de dados e, caso os dados sejam críticos a sua organização, a restauração dos dados. Os dados de arquivamento, monitoramento e chat persistente não são necessários para o backup e a execução do Lync Server.

