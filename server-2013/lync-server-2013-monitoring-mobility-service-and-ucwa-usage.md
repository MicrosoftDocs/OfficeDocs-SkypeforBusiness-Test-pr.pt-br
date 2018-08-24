---
title: Monitorando o uso do serviço de mobilidade e do UCWA
TOCTitle: Monitorando o uso do serviço de mobilidade e do UCWA
ms:assetid: 8389b37a-ca3e-4047-8b51-85bc07da87e8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690025(v=OCS.15)
ms:contentKeyID: 49307317
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitorando o uso do serviço de mobilidade e do UCWA

 

_**Tópico modificado em:** 2013-02-14_

Você deve monitorar continuamente a CPU e a memória usada pelo Unified Communications Web API (UCWA) e pelo Mobility Service (Mcx) do Lync Server. Para monitorar o uso, você pode usar uma das opções a seguir:

**Para Unified Communications Web API (UCWA):**

  - O processo de trabalho da **LyncUcwa** em Gerenciador dos Serviços de Informações da Internet (IIS). No painel **Processos de Trabalho**, examine as colunas **CPU %** e **Bytes Particulares (KB)** (memória).

  - Os contadores de desempenho da **CPU** e do **Processador**.

Na maioria das implantações o uso da CPU do UWCA deve estar abaixo de 15%, em média. O uso de memória deve ficar dentro dos limites descritos em [Monitoramento de limites de capacidade de memória do servidor](lync-server-2013-monitoring-for-server-memory-capacity-limits.md).

Além de contadores de uso de CPU e memória, você pode usar os contadores de desempenho a seguir para ajudar a determinar quando um servidor está sobrecarregado com solicitações:

  - **LS:WEB – Throttling and Authentication\\WEB – Total Requests in Processing**, que indica o número de solicitações Web pendentes no servidor. Quando esse contador chega a 10.000, as solicitações subsequentes falharão com o erro "503 - serviço indisponível".

  - **ASP.NET\\Requests Queued** (deve ser sempre zero),

> [!NOTE]  
> Se você atender ou exceder esses valores, você deve rever e recomputar seu planejamento de capacidade para o tamanho correto da CPU, número de núcleos e memória para os computadores hospedando os serviços Web.

**Para o Mobility Service (Mcx):**

  - Os processos de trabalho da **CSIntMcxAppPool** e da **CSExtMcxAppPool** em Gerenciador dos Serviços de Informações da Internet (IIS). No painel **Processos de Trabalho**, examine as colunas (memória) **CPU %** e **Bytes Particulares (KB)**.

  - Os contadores de desempenho da **CPU** e do **Processador**.

Na maioria das implantações o uso da CPU do Mobility Service deve estar abaixo de 15%, em média. O uso de memória deve ficar dentro dos limites descritos em [Monitoramento de limites de capacidade de memória do servidor](lync-server-2013-monitoring-for-server-memory-capacity-limits.md).

Além de contadores de uso de CPU e memória, você pode usar os contadores de desempenho ASP.NET a seguir para ajudar a determinar quando um servidor está sobrecarregado com solicitações:

  - **ASP.NET v2.0.50727\\Requests Current**, que indica o número de solicitações Web pendentes no servidor. Quando esse contador chega a 5.000, as solicitações subsequentes falharão com a mensagem de erro "503 - serviço indisponível".

  - **ASP.NET\\Requests Queued** (deve ser sempre zero),

> [!NOTE]  
> Se você atender ou exceder esses valores, você deve rever e recomputar seu planejamento de capacidade para o tamanho correto da CPU, número de núcleos e memória para os computadores hospedando os serviços Web.

## Consulte Também

#### Conceitos

[Monitoramento de limites de capacidade de memória do servidor](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

