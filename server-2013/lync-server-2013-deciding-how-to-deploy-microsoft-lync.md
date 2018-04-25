---
title: 'Lync Server 2013: Decidindo como implantar o Microsoft Lync'
TOCTitle: Decidindo como implantar o Microsoft Lync
ms:assetid: 6ca677d3-745d-4935-8f05-19274a8bccf2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204979(v=OCS.15)
ms:contentKeyID: 49307024
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Decidindo como implantar o Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

Durante o planejamento do Lync, a primeira grande decisão é como implantar o Microsoft Lync: como Lync Server 2013 no local ou Skype for Business Online com Microsoft Office 365 na nuvem.

  - **Lync Server 2013 no local** : esta opção fornece o conjunto completo de recursos do Lync e proporciona o máximo de flexibilidade ao configurar, personalizar e operar a implantação. Todos os servidores são instalados no local e mantidos por sua organização. Uma implantação no local fornece a gama completa de recursos do Lync Server.

  - **Skype for Business Online na nuvem**Skype for Business Online foi desenvolvido para organizações que desejam os benefícios de custo e agilidade de mensagens instantâneas, presença e reuniões com base na nuvem sem sacrificar os recursos de nível corporativo do Lync Server. Com o Skype for Business Online, a Microsoft implanta e mantém a infraestrutura de servidores necessária e cuida dos procedimentos constantes de manutenção, patches e upgrades. Alguns recursos disponíveis na implantação no local não estão disponíveis no Skype for Business Online.

O melhor tipo de implantação para você depende das cargas de trabalho que deseja implantar e da situação geográfica e de negócios de sua organização.

## Lync Server

Uma implantação do Lync Server no local é melhor nas seguintes situações:

  - **Recursos completos do Enterprise Voice**   caso planeje implantar uma solução completa do Enterprise Voice para substituir o PBX ou que utilize recursos avançados de chamadas, será necessário realizar uma implantação do Lync Server no local. Esse tipo de implantação oferece suporte a conectividade direta com sistemas e troncos PBX, além de recursos de telefonia avançados como grupos de resposta e estacionamento de chamada. Atualmente, o Lync Online não oferece suporte a esses recursos.

  - **Controles de qualidade de mídia**   Caso deseje a gama completa de recursos de garantia de qualidade de mídia, como CAC (controle de admissão de chamadas) e QoS (qualidade de serviço), convém realizar a implantação no local.

  - **Chat persistente**   Caso precise implantar chat persistente na organização, escolha a implantação no local.

  - **Aplicativos de servidores de terceiros**   Apenas as implantações no local podem trabalhar com aplicativos de terceiros confiáveis que utilizam a Microsoft Unified Communications Managed API (UCMA).

  - **Empresas multinacionais/multirregionais que necessitam de suporte regional**   Caso tenha data centers em vários países ou regiões e necessite de servidores implantados e gerenciados nas regiões, a implantação no local é a melhor, pois fornece esses recursos de gerenciamento regional.

  - **Controle completo de políticas, relatórios e upgrades**   Com uma implantação do Lync Server no local, você obtém acesso ao conjunto completo de políticas de servidor e cliente, Monitoramento e outros relatórios e tempo dos upgrades. O Lync Online fornece um subconjunto de configurações e relatórios de políticas, além de uma janela limitada, porém significativa, de aceitação de upgrades.

## Lync Online

Caso nenhum dos fatores na lista anterior seja essencial para você, escolha o Lync Online, que possui implantação e gerenciamento mais simples. O Lync Online fornece um conjunto robusto de IM, presença e conferências, além de permitir chamadas de voz e vídeo por IP entre usuários da organização.

