---
title: 'Lync Server 2013: Visão geral do tronco SIP'
TOCTitle: Visão geral do tronco SIP
ms:assetid: 204f2c21-436f-4b2d-93ea-d6db98fa2952
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398285(v=OCS.15)
ms:contentKeyID: 49306114
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-05_

A implantação de troncos SIP pode ser um grande passo para a simplificação das telecomunicações da sua organização e a preparação para os últimos aperfeiçoamentos nas comunicações em tempo real. Umas das principais vantagens de troncos SIP é que você pode consolidar as conexões da sua organização com a PSTN em um local central, ao contrário do seu anterior, o tronco TDM, que normalmente exige um tronco separado de cada local.

## Tronco SIP no Lync Server

As capacidades de tronco SIP do Lync Server 2013 permitem o seguinte:

  - Um usuário corporativo, dentro ou fora do firewall corporativo, pode fazer uma chamada local ou de longa distância especificada por um número compatível com o E.164 que seja terminado no PSTN como um serviço do provedor correspondente.

  - Qualquer assinante do PSTN pode entrar em contato com um usuário corporativo dentro ou fora do firewall corporativo ao discar um número DID (Discagem Direta Interna) associado àquele usuário da empresa.

## Redução de custo

As reduções de custo associadas ao tronco SIP podem ser substanciais:

  - Geralmente, as chamadas de longa distância custam menos através de um tronco SIP.

  - Você pode cortar os custos de gerenciamento e reduzir a complexidade da implementação.

  - A interface de tarifa básica (BRI) e a interface de tarifa primária (PRI) podem ser eliminadas se você conectar um tronco SIP diretamente ao ITSP, por um custo significativamente inferior. Nos troncos TDM, os provedores de serviço cobram as chamadas por minuto. O custo do tronco SIP pode ser baseado no uso da largura de banda, e você pode comprar incrementos menores e mais econômicos. (O custo real depende do modelo de serviço do que você escolhe).

## Tronco SIP versus hospedagem de um gateway PSTN ou IP-PBX

Uma vez que os troncos SIP se conectam diretamente ao provedor de serviço, você pode eliminar os seus gateways PSTN e seu custo de gerenciamento e complexidade. O uso de um tronco SIP pode levar a cortes substanciais no custo, através da manutenção e administração reduzida.

## Serviços de VoIP expandidos

Os recursos de voz são frequentemente o principal motivo para implantar o tronco SIP, mas o suporte de voz é apenas a primeira etapa. Com o tronco SIP, é possível estender as capacidades VoIP e habilitar o Lync Server 2013 para oferecer um conjunto de serviços mais avançado. Por exemplo:

  - Detecção de presença avançada para dispositivos não executando o Lync Server 2013 pode oferecer melhor integração com telefones móveis, permitindo ver quando um usuário está em uma chamada de celular.

  - As chamadas de emergência E9-1-1 permitem que as autoridades que atendem ao 911 determinem a localização do chamador a partir do número do telefone.

> [!NOTE]  
> Consulte o ITSP para obter uma lista de serviços que eles suportam e podem habilitar para sua organização.
