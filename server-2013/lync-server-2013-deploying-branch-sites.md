---
title: 'Lync Server 2013: Implantando sites de filial'
TOCTitle: Implantando sites de filial
ms:assetid: 1475dee0-66ae-4ee5-b6f1-7409b4bbff45
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398217(v=OCS.15)
ms:contentKeyID: 49305969
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando sites de filial no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Os usuários de filial aproveitam melhor a funcionalidade do Lync Server 2013 do servidor no local central ao qual a filial está associada. Cada filial está associada a exatamente um local central. Para fazer chamadas de/para a PSTN (Rede Telefônica Pública Comutada), uma filial deve incluir qualquer um dos itens a seguir:

  - Um gateway PSTN e, possivelmente, um Servidor de Mediação

  - Um tronco SIP

  - Uma infraestrutura existente de voz com uma central privada de comutação telefônica (PBX)

  - Um Aparelho de Filial Persistente

  - Um Servidor de Filial Persistente

Sites de filial com um Aparelho de Filial Persistente ou um Servidor de Filial Persistente são mais resilientes durante falhas da rede de longa distância ou do site central do que sites de filial sem uma dessas soluções. Por exemplo, em um site com um Aparelho de Filial Persistente ou um Servidor de Filial Persistente implantado, os usuários ainda podem fazer e receber chamadas PSTN se a rede que conecta o site de filial ao site central estiver inoperante. Outra forma de alcançar resiliência do site de filial é com o uso de um gateway PSTN ou um tronco SIP com uma implantação de escala completa do Lync Server no site de filial.

Para detalhes sobre qual implantação do site de filial é a correta para a sua organização, incluindo pré-requisitos e outras considerações de planejamento, consulte [Planejamento de conectividade de PSTN no Lync Server 2013](lync-server-2013-planning-for-pstn-connectivity.md) e [Planejamento de resiliência de voz no site da filial no Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md) na documentação de Planejamento.

## Nesta seção

  - [Fornecendo conectividade de PSTN ao site da filial no Lync Server 2013](lync-server-2013-providing-pstn-connectivity-at-a-branch-site.md)

  - [Implantando Aplicativo ou Servidor de Filial Persistente com Lync Server 2013](lync-server-2013-deploying-a-survivable-branch-appliance-or-server.md)

