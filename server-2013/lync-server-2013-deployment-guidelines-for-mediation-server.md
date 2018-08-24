---
title: 'Lync Server 2013: Orientações de implantação para Servidor de Mediação'
TOCTitle: Orientações de implantação para Servidor de Mediação
ms:assetid: 7cc22b87-18d9-45e6-8402-015abd20f2e5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398622(v=OCS.15)
ms:contentKeyID: 49307230
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Orientações de implantação para Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve algumas diretrizes de planejamento para a implantação do Servidor de Mediação. Depois de revisar essas diretrizes, recomendamos que você use a Ferramenta de Planejamento para criar e exibir topologias alternativas possíveis, que poderão servir como modelos para a possível aparência da topologia ajustada final que você decidir implantar.

## Servidores de mediação autônomos ou colocados Servidor de Mediação?

O Servidor de Mediação é colocado por padrão no Servidor Standard Edition ou Servidor Front-End em um Pool de Front-Ends em locais centrais. O número de chamadas PSTN pode ser manipulado e o número de máquinas necessárias no pool dependerá do seguinte:

  - o número de pares de gateway que controla o Pool do servidor de mediação

  - o tráfego de alto volume por meio desses gateways

  - a porcentagem de chamadas que ignoram o Servidor de Mediação

Durante o planejamento, tenha em consideração as exigências de processamento de mídia para chamadas PSTN de conferências A/V não configuradas por bypass de mídia, além do processamento necessário para interações de sinalização para diversas chamadas em horário de pico que precisam de suporte. Se não houver CPU suficiente, você deve implantar um pool autônomo de Servidor de Mediação e gateways PSTN, IP-PBXs e SBCs deverão ser divididos em subgrupos controlados pelo Servidor de Mediação colocado em um pool e autônomo Servidor de Mediação em um ou mais pools autônomos.

Se você implantou os gateways PSTN, PBXs IP ou SBCs que não suportam os recursos corretos para interagir com um pool de Servidor de Mediação, incluindo os seguintes, eles precisarão ser associados a um pool autônomo que consiste em um único Servidor de Mediação:

  - Executar o balanceamento de carga DNS de camada de rede em Servidor de Mediação em um pool (ou caso contrário, rotear tráfego uniformemente para todos os Servidor de Mediação em um pool)

  - Aceitar tráfego de qualquer Servidor de Mediação em um pool

É possível usar o Microsoft Lync Server 2013, Ferramenta de Planejamento para avaliar se o pool de front-end onde você deseja posicionar o Servidor de Mediação pode lidar com a carga. Se o seu ambiente não pode cumprir estes requisitos, você deve implantar um pool do Pool do servidor de mediação autônomo.

## Considerações sobre o site central e site de filial

Os Servidor de Mediação no site central podem ser usados para rotear chamadas para gateways IP PBXs ou PSTN em sites de filial. Se você implantar os troncos SIP, no entanto, é necessário implantar um Servidor de Mediação no site onde termina cada tronco. Com um Servidor de Mediação no site central para rotear chamadas a um gateway PBX IP ou PSTN de uma filial não requer o uso de bypass de mídia. No entanto, se você pode ativar o bypass de mídia, isso irá reduzir a latência do caminho de mídia e, conseqüentemente, resultar em uma melhor qualidade mídia, porque o caminho de mídia não é mais necessário para seguir o caminho de sinalização. O bypass de mídia também irá diminuir a carga de processamento no pool.

> [!NOTE]  
> O desvio de mídia não irá interoperar com cada gateway PSTN, IP-PBX e SBC. A Microsoft testou um conjunto de gateways PSTN e SBCs com parceiros certificados e fez alguns testes com IP-PBXs da Cisco. O desvio de mídia é compatível somente com produtos e versões listados no Programa de Interoperabilidade Aberta de Comunicações Unificadas – Lync Server em <a href="http://go.microsoft.com/fwlink/p/?linkid=268730">http://go.microsoft.com/fwlink/p/?LinkId=268730</a>.

Se a flexibilidade do site de filial for necessária, um Aparelho de Filial Persistente ou uma combinação de um Servidor Front-End, um Servidor de Mediação e um gateway devem ser implantados na filial. (A suposição sobre a resiliência do site de filial é que a presença e conferência não são resilientes no site.) Para obter orientação sobre planejamento de voz de filial, consulte [Planejamento de resiliência de voz no site da filial no Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md).

Para interações com um PBX IP, se o IP-PBX não suporta corretamente as interações de mídia inicial com várias caixas de diálogo anteriores e interações RFC 3960, pode haver corte do primeiro "Olá" para chamadas de entrada de IP-PBX aos Lync pontos de extremidade. Esse comportamento pode ser mais grave se um Servidor de Mediação em um site central estiver roteando chamadas a um PBX IP onde a rota termina em um site de filial, porque é necessário mais tempo para concluir a sinalização. Se você enfrentar esse comportamento, implantar um Servidor de Mediação da filial é a única maneira de reduzir o corte do primeiro "Olá".

Finalmente, se o site central tiver um PBX TDM ou se o IP-PBX não elimina a necessidade de um gateway PSTN, você deve implantar um gateway na rota de chamada que conecta o Servidor de Mediação e o PBX.

> [!NOTE]  
> Para aprimorar o desempenho de mídia do Servidor de Mediação autônomo, você deve habilitar o RSS (receive-side scaling) nos adaptadores de rede nesses servidores. O RSS permite que pacotes de entrada sejam manipulados em paralelo por vários processadores no servidor. Para obter detalhes, consulte &quot;Aprimoramentos do Receive-Side Scaling no Windows Server&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?LinkId=268731</a>. Para obter detalhes sobre como ativar RSS, consulte a documentação do seu adaptador de rede.
