---
title: Visão geral de conferência A/V no Lync Server 2013
TOCTitle: Visão geral de conferência A/V no Lync Server 2013
ms:assetid: 9583de87-4618-4a99-a47a-45e8cc4cc221
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ619186(v=OCS.15)
ms:contentKeyID: 49307506
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de conferência A/V no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A conferência A/V permite comunicações de áudio de vídeo em tempo real entre seus usuários. Ao implantar a conferência, você pode escolher habilitar e usar a Webconferência e a conferência A/V, ou apenas a Webconferência.

Para planejar a conferência A/V, você precisa saber a largura de banda de rede necessária para o tipo de mídia de conferência que sua organização requer. Isso pode incluir áudio, vídeo e vídeo panorâmico.

Antes de permitir usuários para conferência A/V, certifique-se de que sua rede pode lidar com a carga resultante. Sem largura de banda suficiente, a experiência do usuário pode ser degradada severamente. Você pode usar o controle de admissão de chamadas (CAC) para gerenciar a largura de banda da rede usada pela conferência A/V. Isso é importante em redes restritas, como links de largura de banda limitada entre centrais e filiais. Para obter detalhes, consulte [Visão geral do controle de admissão de chamada no Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md). Para obter detalhes sobre requisitos de largura de banda de mídia, consulte [Requisitos de largura de banda de rede para tráfego de mídia no Lync Server 2013](lync-server-2013-network-bandwidth-requirements-for-media-traffic.md).

Se você implantar uma conferência de áudio na sua rede, os usuários precisarão de dispositivos de áudio, como fones de ouvido, para participar em uma conferência de áudio. Se você implantar conferência de vídeo, será necessário implantar dispositivos de vídeo, como webcams, para os usuários. Recomendamos que você use dispositivos de comunicações unificadas (UC) certificados pela Microsoft para todos os tipos de dispositivos, para garantir uma experiência ideal ao usuário. Para obter detalhes sobre dispositivos com certificação UC, consulte "Telefones e dispositivos para Lync" em [http://go.microsoft.com/fwlink/?linkid=263861\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=263861%26clcid=0x416). Para dispositivos de áudio e vídeo, a implantação de vídeo e treinamento do usuário são etapas importantes a serem consideradas e planejadas.

As seções a seguir descrevem os recursos para conferência de áudio e vídeo, incluindo informações sobre gerenciamento de largura de banda e seleção de clientes apropriados.

## Recursos de conferência de áudio

O Lync Server 2013 fornece vários recursos que você pode usar para configurar a experiência de conferência de áudio para o usuário, incluindo:

  - **Mudo do microfone dos participantes**   O apresentador pode usar essa configuração para retirar o áudio de todos os participantes na conferência e colocar a conferência em um estado no qual aqueles que não forem apresentadores não poderão ativar o áudio.

  - **Anúncios de entrada/saída da conferência**  Se você ativou a conferência discada, os apresentadores podem usar essa configuração para ligar ou desligar os anúncios de entrada/saída para minimizar distrações, enquanto a conferência estiver em andamento.

  - **Adicionar um usuário discando a eles**   Os apresentadores e participantes que tiverem permissão, podem adicionar números PSTN às conferências e fazer com que a conferência ligue para esses números.

## Recursos de videoconferência

O Lync Server 2013 fornece vários recursos que você pode usar para configurar a experiência de conferência de vídeo do usuário, incluindo:

  - **Visualização de galeria**   Em conferências de vídeo que tenham mais que duas pessoas, os usuários podem automaticamente ver todos na conferência. Se a conferência tiver mais que cinco participantes, o vídeo dos participantes mais ativos serão exibidos na linha superior e apenas a foto dos outros participantes será exibida. O vídeo de vários participantes está ativado como padrão. Para obter detalhes sobre como configurar ou desligar o vídeo de vários participantes, consulte [Configuriando largura de banda de vídeo no Lync Server 2013](lync-server-2013-configuring-video-bandwidth.md).

  - **Vídeo panorâmico**   Se um dispositivo de conferência de vídeo de mesa redonda estiver instalado na sala de conferências, esse recurso fornecerá uma visão de 360 graus da sala de conferência. A faixa de vídeo panorâmico está disponível apenas em dispositivos de mesa redonda.

  - **Modo de vídeo apenas apresentador**   Os apresentadores podem configurar a reunião de forma que apenas o vídeo deles seja exibido. Isso evita distrações em reuniões grandes, quando várias transmissões de vídeo estão disponíveis e travadas para diferentes fontes. Esse modo também é aplicado ao vídeo capturado e fornecido por dispositivos de mesa redonda.

  - **Vídeo HD**   Os usuários podem experimentar resoluções de até HD 1080P em chamadas entre duas pessoas e conferências de vários participantes.

  - **Destaque de vídeo**  Os apresentadores podem configurar a reunião para que apenas o vídeo de um participante selecionado seja visto pelos outros participantes na conferência. Esse modo também se aplica ao vídeo capturado e fornecido pelos dispositivos de mesa redonda de vídeo panorâmico.

