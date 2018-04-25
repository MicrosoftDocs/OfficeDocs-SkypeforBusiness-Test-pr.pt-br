---
title: O modelo de usuário de conferência
TOCTitle: O modelo de usuário de conferência
ms:assetid: ba4bbba9-f2e3-4cab-8eba-b51f12133cab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205199(v=OCS.15)
ms:contentKeyID: 49307915
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# O modelo de usuário de conferência

 

_**Tópico modificado em:** 2012-10-22_

Uma parte importante do modelo de usuário de conferência do Lync Server é o tamanho da reunião. Depois de coletar dados de vários pontos de dados (como descrito na seção anterior), nós determinados o seguinte:

  - A maioria das reuniões é composta por pequenas reuniões colaborativas com uma média de quatro a seis participantes

  - Aproximadamente 80 por cento das reuniões tem menos de 20 participantes.

  - 99,98 por cento das reuniões tem menos de 100 participantes.

Além do tamanho da reunião, o modelo de usuário de conferência também considera vários fatores, como:

  - **Reuniões simultâneas**   O número de usuários simultâneos esperados nas reuniões?

  - **Mix de mídia**   Quais tipos de mídia estão disponíveis e que os usuários usarão em reuniões?

  - **Tipos de usuários**   Os usuários são internos, remotos, federados ou anônimos?

  - **Tempo de participação da reunião**   Quanto tempo todos os usuários de uma reunião levam para participar dela?

Para obter detalhes sobre o modelo do usuário, consulte [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md).

Para determinar o número de reuniões e usuários para usar em testes foi realizado o seguinte:

  - Pegamos o número total de usuários em uma organização (por exemplo, 80.000 usuários) e multiplicamos pela taxa de simultaneidade da reunião (por exemplo, 5% de todos os usuários) para determinar o número total de usuários esperados em reuniões simultâneas (neste exemplo, 4000 usuários).

  - Dividimos o número total de usuários pelo número de Lync Server 2013, Servidores Front-End na implantação (por exemplo, 8 servidores) para determinar o número estimado de participantes da reunião por Servidor Front-End (neste exemplo, 500 usuários por Servidor Front-End).

  - Dividimos o número de usuários por Servidor Front-End pelo tamanho médio da reunião (por exemplo, 4 usuários) para determinar o número médio estimado de reuniões por Servidor Front-End (neste exemplo, 125 reuniões por Servidor Front-End).

  - Para obter a carga por mídia em cada Servidor Front-End, estimamos o mix de mídia. Por exemplo, considerando que 75% das reuniões requerem mais do que suporte a áudio e que 50% destas requerem compartilhamento de aplicativos, totalizando uma média de 47 reuniões e 188 usuários conectados simultaneamente a cada Servidor Front-End para o compartilhamento de aplicativos.

  - Testado em vários tamanhos de reunião (com base em nosso modelo de usuário de até 250 usuários em um pool compartilhado) para garantir a escalabilidade do servidor.

