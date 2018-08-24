---
title: 'Lync Server 2013: Componente do Servidor de Mediação'
TOCTitle: Componente do Servidor de Mediação
ms:assetid: 5b19edef-4a54-43c9-aa12-5643b8108355
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398399(v=OCS.15)
ms:contentKeyID: 49306817
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componente do Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Você deverá implantar o Lync Server 2013, Servidor de Mediação se implantar a carga de trabalho do Enterprise Voice. Esta seção descreve a funcionalidade básica, as dependências, as topologias básicas e as diretrizes de planejamento.

O Servidor de Mediação converte a sinalização e, em algumas configurações, a mídia entre seu Lync Server 2013 interno, a infraestrutura do Enterprise Voice e um gateway PSTN (rede telefônica pública comutada) ou um tronco do protocolo SIP. No lado do Lync Server 2013, o Servidor de Mediação escuta em um único endereço de transporte MTLS (TLS mútuo). No lado do gateway, o Servidor de Mediação escuta em todas as portas de escuta associadas a troncos definidos no documento da topologia. Todos os gateways qualificados devem oferecer suporte a TLS, mas também podem habilitar TCP. TCP tem suporte em gateways que não oferecem suporte a TLS.

Se você também tiver um PBX (Public Branch Exchange) existente no seu ambiente, o Servidor de Mediação manipulará chamadas entre os usuários do Enterprise Voice e o PBX. Se o PBX for um IP-PBX, você poderá criar uma conexão SIP direta entre o PBX e o Servidor de Mediação. Se o PBX for um TDM (Time Division Multiplex) PBX, você também deverá implantar um gateway PSTN entre o PBX e o Servidor de Mediação.

O Servidor de Mediação é colocado no Servidor Front-End por padrão. O Servidor de Mediação também pode ser implantado em um pool autônomo por motivos de desempenho ou quando você implanta o entroncamento SIP, caso em que o pool autônomo é altamente recomendável.

Se você implantar conexões SIP diretas com um gateway PSTN qualificado que oferece suporte a bypass de mídia e balanceamento de carga DNS, um pool do Servidor de Mediação autônomo não será necessário. Um Pool do servidor de mediação autônomo não é necessário porque os gateways qualificados são capazes de balancear a carga DNS para um pool de Servidores de Mediação e eles podem receber o tráfego de qualquer Servidor de Mediação em um pool.

Nós também recomendamos que você coloque o Servidor de Mediação em um Pool de Front-Ends quando tiver implantado IP-PBXs ou conecte-se a um Controlador de Borda da Sessão (SBC) do Provedor do servidor de telefonia Internet, contanto que as seguintes condições sejam cumpridas:

  - O IP-PBX ou o SBC está configurado para receber tráfego de qualquer Servidor de Mediação no pool e pode direcionar o tráfego uniformemente para todos os Servidor de Mediação no pool.

  - O IP-PBX não suporta bypass de mídia, mas o Pool de Front-Ends hospedando o Servidor de Mediação pode lidar com a transcodificação de voz para chamadas nas quais o bypass de mídia não é aplicável.

É possível usar o Microsoft Lync Server 2013, Ferramenta de Planejamento para avaliar se Pool de Front-Ends onde você deseja posicionar o Servidor de Mediação pode lidar com a carga. Se o seu ambiente não pode cumprir estes requisitos, você deve implantar um Pool do servidor de mediação autônomo.

Estas são as principais funções do Servidor de Mediação:

  - Criptografia e descriptografia de SRTP no lado do Lync Server

  - Conversão do SIP em TCP (para gateways que não oferecem suporte a TLS) para SIP em MTLS (TLS mútuo)

  - Conversão de fluxos de mídia entre o Lync Server e o par de gateway do Servidor de Mediação

  - Conexão de clientes externos à rede com componentes internos de ICE, que permitem a passagem de NATs e firewalls.

  - Atuação como intermediário nos fluxos de chamadas aos quais um gateway não oferece suporte, como chamadas de funcionários remotos em um cliente do Enterprise Voice

  - Em implantações que incluem tronco SIP, trabalho conjunto com o provedor de serviços de tronco SIP para oferecer suporte à PSTN, o que elimina a necessidade de um gateway PSTN

A figura a seguir mostra os protocolos de sinalização e de mídia usados pelo Servidor de Mediação durante a comunicação com um gateway PSTN básico e a infraestrutura do Enterprise Voice.

**Protocolos de sinalização e a mídia usados pelo Servidor de Mediação**

![Diagrama dos protocolos do servidor de mediação](images/Gg398399.c3d39ba0-e323-4a58-8f07-4e80d3278af2(OCS.15).jpg "Diagrama dos protocolos do servidor de mediação")

> [!NOTE]  
> Se você estiver usando TCP ou RTP/RTCP (em vez de SRTP ou SRTCP) na rede entre o gateway PSTN e o Servidor de Mediação, recomendamos que tome medidas para ajudar a garantir a segurança e a privacidade da rede.

## Nesta seção

  - [Tronco M:N no Lync Server 2013](lync-server-2013-m-n-trunk.md)

  - [Controle de admissão de chamada e Servidor de Mediação no Lync Server 2013](lync-server-2013-call-admission-control-and-mediation-server.md)

  - [9-1-1 Avançado (E9-1-1) e Servidor de Mediação no Lync Server 2013](lync-server-2013-enhanced-9-1-1-e9-1-1-and-mediation-server.md)

  - [Bypass de mídia e Servidor de Mediação no Lync Server 2013](lync-server-2013-media-bypass-and-mediation-server.md)

  - [Componentes e topologias para o Servidor de Mediação no Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md)

  - [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md)

