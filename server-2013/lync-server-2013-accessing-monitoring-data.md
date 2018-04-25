---
title: Acessando dados de monitoramento no Lync Server 2013
TOCTitle: Acessando dados de monitoramento no Lync Server 2013
ms:assetid: 845385ca-5532-4fa2-91b9-51c6de6fec91
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688116(v=OCS.15)
ms:contentKeyID: 49886291
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Acessando dados de monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

Os dados de monitoramento são armazenados em um par de bancos de dados SQL Server databases: LcsCdr para registro de detalhes das chamadas e QoEMetrics para dados sobre a qualidade da experiência. Não há nada de especial nesses dois bancos de dados, o que significa que os dados armazenados neles podem ser acessados por meio das ferramentas que você usa normalmente para acessar e analisar dados do SQL Server.

Uma ferramenta que você pode usar para acessar e análise dados de monitoramento são os Relatórios de monitoramento do Lync Server. Os Relatórios de monitoramento são um conjunto de relatórios padrão publicados pelo Microsoft SQL Server Reporting Service. Esses relatórios, que podem ser acessados por meio de navegadores, fornecem informações de uso, diagnóstico de camada e qualidade de mídia, todos com base em registros de detalhes das chamadas call detail recording (CDR) e qualidade da experiência (QoE) armazenados nos bancos de dados de CDR e QoE. Os Relatórios de monitoramento são disponibilizados com o Lync Server 2013 e podem ser instalados a partir do Assistente de implantação do Lync Server após a instalação do Lync Server e da configuração do monitoramento.

Os Relatórios de monitoreamente requerem o uso do SQL Server Reporting Service. O SQL Server Reporting Service pode ser instalado ao mesmo tempo que o SQL Server é instalado ou a qualquer momento após a instalação do próprio SQL Server.

Para obter mais informações, consulte o tópico [Instalando Relatórios de Monitoramento do Lync Server 2013](lync-server-2013-installing-lync-server-2013-monitoring-reports.md) no guia de implantação do Lync Server 2013.

