---
title: 'Lync Server 2013: Visão Geral do Diretor'
TOCTitle: Visão Geral do Diretor
ms:assetid: cf9919b3-e16b-47c5-be1d-2c4bc64f44ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398879(v=OCS.15)
ms:contentKeyID: 49308162
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão Geral do Diretor no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Um Diretor é um servidor executando o Lync Server 2013 que autentica as solicitações do usuário, mas não hospeda qualquer conta de usuário. É possível opcionalmente implantar o Diretor nos seguintes dois cenários:

  - Se você habilitar o acesso pelos usuários externos implantando o Servidores de Borda, também é necessário implantar um Diretor. Neste cenário, o Diretor autentica os usuários externos e passa seu tráfego para servidores internos. Quando um Diretor é usado para autenticar usuários externos, libera os servidores do Pool de Front-Ends da sobrecarga da autenticação de desempenho destes usuários. Também ajuda a vedar o Pools de Front-Ends interno de tráfego malicioso como ataques de negação de serviço. Se a rede é preenchida com tráfego externo inválido em tal ataque, este tráfego termina no Diretor.

  - Se você implantar vários Pools de Front-Ends no site central, adicionando um Diretor para este site, é possível reduzir as solicitações de autenticação e melhorar o desempenho. Neste cenário, todas as solicitações vão primeiro para o Diretor, que direciona para o Pool de Front-Ends correto.

