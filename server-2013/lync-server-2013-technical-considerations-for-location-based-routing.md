---
title: 'Lync Server 2013: Considerações técnicas para Roteamento Baseado em Local'
TOCTitle: Considerações técnicas para Roteamento Baseado em Local
ms:assetid: 2e2a9199-7c6f-48d3-9adb-3873fc4f8c4e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994027(v=OCS.15)
ms:contentKeyID: 52057592
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Considerações técnicas para Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-09_

Ao planejar o Roteamento com Base no Local, você deve considerar o impacto nos seguintes cenários.

## Recuperação de desastres

Durante uma falha do pool principal para um pool de backup, bem como ao restaurar operações normais para o pool primário, o Roteamento com Base no Local continua aplicado todo o tempo durante um desastre e procedimento de recuperação.

## Aparelho de Filial Persistente

A configuração do Roteamento com Base no Local gera um impacto sobre o planejamento de onde você implementa os gateways associados a seu Aparelho de Filial Persistente. O gateway associado a seu SBA deve estar localizado no mesmo local da rede de seu Aparelho de Filial Persistente; caso contrário, os usuários hospedados em seu Aparelho de Filial Persistente não terão permissão para realizar chamadas de saída se o Roteamento com Base no Local não estiver configurado. Quando a conexão WAN entre seu Aparelho de Filial Persistente e o local central falhar, as restrições de Roteamento com Base no Local permanecerão impostas.

## Consulte Também

#### Outros Recursos

[Planejamento de Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)

