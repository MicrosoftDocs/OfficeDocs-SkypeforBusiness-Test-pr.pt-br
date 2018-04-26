---
title: 'Lync Server 2013: Planejamento de bypass de mídia'
TOCTitle: Planejamento de bypass de mídia
ms:assetid: 8ac732b6-8538-4d7b-b1a9-2035e419dac2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398703(v=OCS.15)
ms:contentKeyID: 49307379
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de bypass de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Desvio de mídia refere-se à remoção do Servidor de Mediação do caminho da mídia sempre que possível para chamadas cuja sinalização percorre o Servidor de Mediação.

O desvio de mídia pode aprimorar a qualidade da voz reduzindo latência, conversões desnecessárias, possibilidade de perda de pacotes e o número de pontos de falha possíveis. A escalabilidade pode ser aprimorada, porque a eliminação do processamento de mídia para chamadas desviadas reduz a carga no Servidor de Mediação. Esta redução na carga complementa a capacidade do Servidor de Mediação de controlar vários gateways.

Onde um site de filial sem um Servidor de Mediação estiver conectado a um site central por um ou mais links WAN com largura de banda restrita, o desvio de mídia diminui os requisitos de largura de banda permitindo que a mídia de um cliente em um site de filial flua diretamente para seu gateway local, sem a necessidade de fluir primeiro pelo link WAN para um Servidor de Mediação no site central e voltar.

Ao aliviar o Servidor de Mediação do processamento de mídia, o desvio de mídia também pode reduzir o número de Servidor de Mediação que uma infraestrutura Enterprise Voice exige.

A figura a seguir exibe caminhos de mídia e sinalização básicos em topologias com e sem desvio de mídia.

**Caminhos de mídia e sinalização com e sem desvio de mídia**

![Imposição da conexão de bypass de mídia do CAC de voz](images/Gg398529.4d66d529-0912-4de1-abec-266f54272eb3(OCS.15).jpg "Imposição da conexão de bypass de mídia do CAC de voz")

Como regra geral, habilite o desvio de mídia onde possível.

## Nesta seção

  - [Visão geral de bypass de mídia no Lync Server 2013](lync-server-2013-overview-of-media-bypass.md)

  - [Modos de bypass de mídia no Lync Server 2013](lync-server-2013-media-bypass-modes.md)

  - [Bypass de mídia e controle de admissão de chamadas no Lync Server 2013](lync-server-2013-media-bypass-and-call-admission-control.md)

  - [Requisitos técnicos para bypass de mídia no Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md)

## Seções relacionadas

[Implantando recursos avançados de Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

## Consulte Também

#### Tarefas

[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  

#### Conceitos

[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)

