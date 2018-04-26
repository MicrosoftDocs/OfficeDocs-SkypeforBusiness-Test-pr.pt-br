---
title: 'Lync Server 2013: Tronco SIP do site da filial'
TOCTitle: Tronco SIP do site da filial
ms:assetid: c4d9dfcd-8baa-41ea-9677-48b0e429429d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412974(v=OCS.15)
ms:contentKeyID: 49308045
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tronco SIP do site da filial no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Em alguns casos, talvez seja necessário implementar o tronco SIP distribuído no site de filial selecionado. Para determinar se um tronco SIP é necessário para um site de filial, revise as informações em [Como implementar tronco SIP no Lync Server 2013?](lync-server-2013-how-do-i-implement-sip-trunking.md)

Para obter detalhes sobre as opções de topologia suportadas para implantação de troncos SIP nos site de filial, consulte [Soluções de resiliência do site de filial no Lync Server 2013](lync-server-2013-branch-site-resiliency-solutions.md).

## Análise de requisitos do tronco SIP do exemplo de site de filial

Ao decidir sobre a implantação de um tronco SIP do site de filial, você precisa realizar uma análise de custo específico do site. Por exemplo, uma empresa que tem um site central em Redmond, Washington, e um site de filial em Nova Iorque devem realizar uma análise para determinar se precisam implementar um tronco SIP a partir do site de Nova York para um provedor de serviços local.

Para determinar se um tronco SIP distribuído em Nova Iorque é uma opção com bom custo benefício, identifique quais números DID usarão o tronco SIP e analise o número de chamadas feitas de Nova Iorque para áreas diferentes de Redmond (425). É possível ter uma terminação DID para o site de filial no site central. Por exemplo, o site central de Redmond pode hospedar números DID para o site de filial de Nova Iorque. Se o custo de implementação de um tronco SIP distribuído for menor do que o custo dessas chamadas, considere a implementação de um tronco SIP no site de filial de Nova Iorque.

## Outros requisitos de tronco SIP do site de filial

A opção entre uma implantação de um tronco SIP em vez de um gateway tem base na diferença entre as cobranças de PSTN de longa distância de cada opção. Se você implantar um tronco SIP do site de filial, também precisará determinar sua resiliência e seus requisitos de banda larga. Se o link entre seu site de filial e site central for resiliente e tiver largura de banda suficiente, você poderá implantar um tronco SIP ou um gateway. Não é necessário implantar um Aparelho de Filial Persistente no site de filial. Se o link entre seu site de filial e site central não for resiliente, implante um Aparelho de Filial Persistente ou um Servidor de Filial Persistente com um gateway ou tronco SIP no site de filial.

