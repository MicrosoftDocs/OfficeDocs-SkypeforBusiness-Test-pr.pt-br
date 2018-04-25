---
title: 'Lync Server 2013: Visão geral de implantação'
TOCTitle: Visão geral de implantação
ms:assetid: da67555e-f410-4c37-9996-d511f37da8d1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205305(v=OCS.15)
ms:contentKeyID: 49308306
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de implantação para Lync Server 2013

 

_**Tópico modificado em:** 2013-03-12_

A principal diferença entre o Lync Server 2013  Enterprise Edition e o Lync Server 2013  Standard Edition é que o Standard Edition não suporta recursos de alta disponibilidade incluídos com o Enterprise Edition. Para alta disponibilidade, você precisa implantar vários Servidores Front-End em um pool e é possível espelhar o servidor executando o SQL Server. Com o Enterprise Edition é possível escolher posicionar ou definir um Servidor de Mediação autônomo. O Servidor de Monitoramento e o Servidor de Arquivamento podem usar um servidor autônomo executando o SQL Server. Em alternativa, eles podem ter instâncias do SQL Server executando o servidor do banco de dados para o Servidores Front-End e pools.

O servidor executando o Lync Server 2013Standard Edition é destinado para pequenas empresas e locais remotos, que são removidos geograficamente da implantação principal da organização. Dois servidores Servidor Standard Edition pareados para falha em caso de desastre podem suportar até 5.000 usuários. Não é possível fazer o pool do Servidores Standard Edition como você faz Servidores Front-End no Enterprise Edition. Além disso, o banco de dados do SQL Server que o Standard Edition usa é um servidor posicionado executando o SQL Server Express projetado para lidar com cargas de trabalho do Servidor Standard Edition. Isto não quer dizer que todas as funções devem residir em um Servidor Standard Edition. É possível ter o Servidor de Mediação autônomo e Servidores de Borda. O banco de dados do SQL Server para o Repositório de Gerenciamento Central e para fins do Lync Server 2013 deve residir no Servidor Standard Edition posicionado com o servidor executando o SQL Server. O Servidor de Monitoramento e o Servidor de Arquivamento usa um servidor autônomo com o banco de dados do SQL Server.

