---
title: 'Lync Server 2013: Componentes de conectividade de PSTN'
TOCTitle: Componentes de conectividade de PSTN
ms:assetid: 6b2a3f7d-760f-4f09-8432-312c98a7e6b7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398504(v=OCS.15)
ms:contentKeyID: 49307025
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes de conectividade de PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Uma solução de VoIP em nível empresarial deve fornecer chamadas de e para a PSTN (rede telefônica pública comutada), sem redução de QoS (Qualidade de Serviço). Além disso, os usuários não devem perceber a tecnologia subjacente ao fazer e receber chamadas. Da perspectiva do usuário, uma chamada entre a infraestrutura do Enterprise Voice e a PSTN deve ser igual a qualquer outra sessão SIP.

Para conexões PSTN, você pode implantar um tronco SIP ou um gateway PSTN (com um PBX, também conhecido como um link do SIP Direto, ou sem um PBX).

## Tronco SIP

Como alternativa ao uso de gateways PSTN, você pode conectar sua solução Enterprise Voice à PSTN usando o tronco SIP. O tronco SIP permite os seguintes cenários:

  - Um usuário corporativo dentro ou fora do firewall corporativo pode fazer uma chamada local ou interurbana especificada por um número em conformidade com E.164 que é encerrado no PSTN como um serviço do provedor de serviços correspondente.

  - Qualquer assinante do PSTN pode entrar em contato com um usuário corporativo dentro ou fora do firewall corporativo ao discar um número DID (Discagem Direta Interna) associado àquele usuário.

O uso dessa solução de implantação requer um provedor de serviços de tronco SIP.

## Gateways PSTN

Os gateways PSTN são dispositivos de terceiros que convertem a sinalização e a mídia entre a infraestrutura do Enterprise Voice e uma PSTN ou um PBX. Os gateways PSTN funcionam com o Servidor de Mediação para apresentar uma chamada PSTN ou PBX para um cliente do Enterprise Voice. O Servidor de Mediação também apresenta as chamadas dos clientes do Enterprise Voice ao gateway PSTN para roteamento para a PSTN ou o PBX. Para obter uma lista dos parceiros que trabalham com a Microsoft para fornecer dispositivos que funcionam com o Lync Server, consulte o site dos Parceiros de Comunicações Unificadas Microsoft em [http://go.microsoft.com/fwlink/p/?linkId=202836](http://go.microsoft.com/fwlink/p/?linkid=202836).

## Centrais privadas de comutação telefônica

Se você tiver uma infraestrutura existente de voz que usa uma PBX (central privada de comutação telefônica), poderá usar sua PBX com o Lync Server Enterprise Voice.

Os cenários de integração de PBX com o Enterprise Voice aceitos são:

  - IP-PBX que oferece suporte ao desvio de mídia, com um Servidor de Mediação.

  - IP-PBX que requer um gateway PSTN autônomo.

  - Conexão PBX TDM, com um gateway PSTN autônomo.

> [!NOTE]  
> O desvio de mídia não irá interoperar com cada gateway PSTN, IP-PBX e SBC. A Microsoft testou um conjunto de gateways PSTN e SBCs com parceiros certificados e fez alguns testes com IP-PBXs da Cisco. O desvio de mídia é compatível somente com produtos e versões listados no Programa de Interoperabilidade Aberta de Comunicações Unificadas – Lync Server em <a href="http://go.microsoft.com/fwlink/p/?linkid=214406">http://go.microsoft.com/fwlink/p/?linkId=214406</a>.

Para obter detalhes sobre parceiros que oferecem soluções do Enterprise Voice, consulte o site dos Parceiros de Comunicações Unificadas Microsoft em [http://go.microsoft.com/fwlink/p/?linkId=202836](http://go.microsoft.com/fwlink/p/?linkid=202836).

Para obter detalhes sobre parceiros que oferecem soluções de hardware do Enterprise Voice, incluindo gateways PSTN, consulte o site dos Parceiros de Comunicações Unificadas Microsoft [http://go.microsoft.com/fwlink/p/?linkId=202836](http://go.microsoft.com/fwlink/p/?linkid=202836).

