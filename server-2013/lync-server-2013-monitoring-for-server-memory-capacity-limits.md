---
title: Monitoramento de limites de capacidade de memória do servidor
TOCTitle: Monitoramento de limites de capacidade de memória do servidor
ms:assetid: 1697ea71-6fcf-480d-b4e9-cd79f94d247e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh689982(v=OCS.15)
ms:contentKeyID: 49305997
ms.date: 12/29/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitoramento de limites de capacidade de memória do servidor

 

_**Tópico modificado em:** 2016-12-08_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.


> [!WARNING]
> A informação neste tópico que se refere ao Planejamento de capacidade pertence apenas a clientes Lync 2010 Mobile e ao Serviço de mobilidade (Mcx). O Planejamento de capacidade para a API Web de comunicação unificada (UCWA), usada pelos clientes Lync 2013 Móvel, é fornecida pelo Lync Server 2013, Ferramenta de Planejamento.



Dois contadores de desempenho de mobilidade podem ajudar a determinar o uso atual e ajudar a planejar a capacidade para o Serviço de mobilidade do Lync Server 2013 (Mcx), assim como monitorar o uso de memória para a UCWA. para a UCWA, a categoria do contador é **LS:WEB – UCWA**. Para o Serviço de mobilidade (Mcx), os contadores estão sob a categoria**LS:WEB - Serviço de comunicação móvel**. Os contadores para monitoramento são:

  - **Contagem atual da sessão ativa com as assinaturas de presença ativa**, que é o número atual de pontos de extremidade registrados através do Serviço de mobilidade ou UCWA que tem assinaturas de presença ativa (número de usuários móveis sempre conectados)

  - **Contagem atual de sessão ativa**, que é o número atual de pontos de extremidade registrados através do Serviço de Mobilidade ou UCWA

Se a diferença entre **Contagem atual de sessão ativa com assinaturas de presença ativa** e **Contagem atual de sessão ativa** for pequena com o passar do tempo, isso significar que a maioria dos usuários de dispositivos móveis possui um dispositivo sempre conectado, como um dispositivo Android ou Nokia (somente para Mcx). Dispositivos UCWA sempre conectados incluem dispositivos Apple e Android executando clientes móveis do Lync 2013. Se **Contagem atual de sessão ativa** for muito maior que **Contagem atual de sessão ativa com assinaturas de presença ativa**, isso mostra que mais usuários estão usando um dispositivo de ponto de extremidade de plano de fundo, como um dispositivo Apple iOS ou um Windows Phone com Mcx. (O Windows Phone é o único cliente Lync 2013 móvel que se registrará assim).

Você deve definir um limite nos contadores de desempenho de **Contagem atual de sessão ativa com assinaturas de presença ativa** e **Contagem atual de sessão ativa** com base no seu uso esperado, nos resultados de planejamento de capacidade e monitoramento em andamento de Serviço de mobilidade e outros contadores do Servidor Front-End. Os limites que você definir devem permitir a avaliação da capacidade do servidor e emitir alertas quando a capacidade for excedida.

Para determinar os limites apropriados, é preciso primeiro determinar quanto de memória está disponível no Servidor Front-End para o Serviço de mobilidade. Monitore os contadores determinar quando você precisa planejar uma capacidade extra, de acordo com a fórmula a seguir:

Memória total usada pelo Serviço de mobilidade Mcx (MB) = 164 + (400 + 134) / 1024 \* **Contagem atual de sessão ativa com assinaturas de presença ativa** + 400 / 1024 \* (**Contagem atual de sessão ativa** – **Contagem atual de sessão ativa com assinaturas de presença ativa**)

> [!IMPORTANT]  
> A Calculadora de capacidade do Microsoft Lync Server 2010 é uma planilha que é pré-populada com todas as fórmulas que permitem um planejador determinar quais requisitos ser~~ao necessários para os servidores, incluindo CPU, memória e disco rígido. Você pode baixar a planilha e o documento associado em: <a href="http://go.microsoft.com/fwlink/?linkid=212657" class="uri">http://go.microsoft.com/fwlink/?linkid=212657</a>

O Servidor Front-End precisa de memória suficiente disponível para dar suporte ao Serviço de mobilidade em situações de failover. Você pode monitorar a memória disponível atualmente no Servidor Front-End usando o contador **Memória\\Mbytes disponíveis**, ou usar a equação mencionada anteriormente para planejar a quantidade de memória que você espera que o Serviço de mobilidade use.

Caso a quantidade de memória disponível no Servidor Front-End seja menor que 1.500 MB quando você planeja o número esperado de usuários de mobilidade, você precisa adicionar mais hardware para dar suporte ao Serviço de Mobilidade. Para obter mais detalhes, consulte "Exemplos de Cenário" em [Monitorando a mobilidade de desempenho no Lync Server 2013](lync-server-2013-monitoring-mobility-for-performance.md) na documentação de Operações.

## Consulte Também

#### Outros Recursos

[Monitorando a mobilidade de desempenho no Lync Server 2013](lync-server-2013-monitoring-mobility-for-performance.md)

