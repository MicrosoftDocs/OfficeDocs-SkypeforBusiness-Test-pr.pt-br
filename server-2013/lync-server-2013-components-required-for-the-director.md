---
title: 'Lync Server 2013: Componentes necessários para o diretor'
TOCTitle: Componentes necessários para o diretor
ms:assetid: 15c7c8d4-b93f-4386-b2d1-d76dab8f801e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398228(v=OCS.15)
ms:contentKeyID: 49305989
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes necessários para o diretor no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

O único componente necessário para criar e configurar um Diretor é implantar a função de servidor de Diretor. Você faz isso usando a Construtor de Topologias e define um pool de computador único ou um pool de múltiplos computadores no nó do Pool de diretores. Após ter definido o Diretor ou o Pool de diretores, execute a Assistente de Implantação do Lync Server no computador que será um Diretor. No caso de um Pool de diretores, você executa a Assistente de Implantação do Lync Server em cada servidor que será um membro do pool.

## Topologias

Você pode implementar um servidor de Diretor único ou um pool de Pool de diretores. Os Diretor são sempre um servidor ou pool separados, não colocado com nenhuma outra função de servidor em Lync Server 2013.

> [!NOTE]  
> Caso não implante o Diretores, o Servidor Front-End ou o Pool de Front-Endsassumirão a função do Diretor.

Um pool de Diretores deve ter a carga balanceada. Você pode:

  - Criar uma topologia que usa um balanceador de carga de hardware para serviços web e balanceamento de carga DNS (Domain Name System) para os outros tipos de tráfego.
    
    [Pool de diretores em escala - balanceamento de carga de DNS e balanceador de carga de hardware no Lync Server 2013](lync-server-2013-scaled-director-pool-dns-load-balancing-and-hardware-load-balancer.md)

  - Criar uma topologia que usa um balanceador de carga de hardware para o balanceamento de carga necessário ao Pool de diretores.
    
    [Pool de diretores em escala - balanceador de carga de hardware no Lync Server 2013](lync-server-2013-scaled-director-pool-hardware-load-balancer.md)

