---
title: 'Lync Server 2013: Failover do repositório do Gerenciamento Central'
TOCTitle: Failover do repositório do Gerenciamento Central
ms:assetid: f464d715-68a4-462c-9584-00f41ab10db0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205376(v=OCS.15)
ms:contentKeyID: 49308609
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failover do repositório do Gerenciamento Central no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

O Repositório de Gerenciamento Central contém dados de configuração de servidores e serviços na sua implantação do Lync 2013. Ele oferece um armazenamento mais robusto e esquematizado dos dados necessários para definir, configurar, manter, administrar, descrever e operar uma implantação do Lync 2013. Ele também valida os dados para garantir a consistência da configuração.

Cada implantação do Lync inclui um Repositório de Gerenciamento Central, que é hospedado pelo Servidor Back-End de um Pool de Front-Ends.

Quando você estabelece um emparelhamento de pools que inclui o pool que hospeda o Repositório de Gerenciamento Central, um banco de dados de backup do Repositório de Gerenciamento Central é definido no pool de backup e os serviços do Repositório de Gerenciamento Central são instalados em ambos os pools. Em nenhum momento um dos dois bancos de dados do Repositório de Gerenciamento Central é o mestre ativo e o outro em espera. O conteúdo é replicado pelo Serviço de Backup do mestre ativo para o em espera.

Durante o failover de um pool que envolve os pools que hospedam o Repositório de Gerenciamento Central, o administrador deve transferir o processamento do Repositório de Gerenciamento Central antes de transferir o processamento do Pool de Front-Ends.

Após a reparação do desastre, não é necessário transferir de volta o processamento do Repositório de Gerenciamento Central. Após o reparo, o Repositório de Gerenciamento Central no pool de backup original pode permanecer como o mestre ativo.

Os alvos projetados do failover de Repositório de Gerenciamento Central para objetivo de tempo de recuperação (RTO) e para objetivo de ponto de recuperação (RPO) é de 5 minutos.

