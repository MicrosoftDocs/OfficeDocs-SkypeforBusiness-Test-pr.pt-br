---
title: 'Lync Server 2013: Bypass de mídia e Servidor de Mediação'
TOCTitle: Bypass de mídia e Servidor de Mediação
ms:assetid: 8ed35f95-05cd-4b5d-8470-442d2323df71
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398719(v=OCS.15)
ms:contentKeyID: 49307432
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Bypass de mídia e Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Desvio de mídia é um recurso do Lync Server que permite que o administrador configure o roteamento de chamadas para que ela flua de forma direta entre o ponto de extremidade do usuário e o gateway de PSTU (rede de telefonia comutada pública) sem atravessar o Servidor de Mediação. O desvio de mídia aprimora a qualidade das chamadas reduzindo a latência, a conversão desnecessária, a possibilidade de perda de pacotes e o número de possíveis pontos de falha. Onde um local remoto sem um a Servidor de Mediação estiver conectado a um local central por um ou mais links WAN com largura de banda limitada, o desvio de mídia reduz o requisito de largura de banda permitindo que a mídia de um cliente em um local remoto flua diretamente para seu gateway local sem passar primeiro pelo link WAN para um Servidor de Mediação no site central e voltar. Essa redução no processamento da mídia também complementa a capacidade do Servidor de Mediação de controlar vários gateways.

O desvio de mídia e o controle de admissão de chamadas (CAC) são mutuamente exclusivos. Se o desvio de mídia for empregado para uma chamada, o CAC não é executado para esta chamada. Assume-se que não existem links com largura de banda restrita envolvidos na chamada.

## Consulte Também

#### Conceitos

[Controle de admissão de chamada e Servidor de Mediação no Lync Server 2013](lync-server-2013-call-admission-control-and-mediation-server.md)  

#### Outros Recursos

[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

