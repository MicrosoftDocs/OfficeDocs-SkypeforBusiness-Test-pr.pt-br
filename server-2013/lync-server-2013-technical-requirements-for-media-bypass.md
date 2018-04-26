---
title: 'Lync Server 2013: Requisitos técnicos para bypass de mídia'
TOCTitle: Requisitos técnicos para bypass de mídia
ms:assetid: 6162a204-0e7c-460a-8eb2-e592c6590a8a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398435(v=OCS.15)
ms:contentKeyID: 49306883
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para bypass de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Em cada chamada para a PSTN, o Servidor de Mediação determina se a mídia do ponto de extremidade do Lync de origem pode ser enviada diretamente para um par do Servidor de Mediação sem passar pelo Servidor de Mediação. O par pode ser um gateway PSTN, um IP-PBX ou um SBC (Controlador de Borda de Sessão) em um ITSP (provedor de serviços de telefonia da Internet) associado ao tronco entre o Servidor de Mediação para o qual a chamada é encaminhada.

O desvio de mídia pode ser empregado quando os seguintes requisitos são atendidos:

  - Um par do Servidor de Mediação deve oferecer suporte aos recursos necessários para o desvio de mídia, sendo o mais importante a capacidade manipular várias respostas bifurcadas (conhecidas como "caixas de diálogo iniciais"). Contate o fabricante do seu gateway ou PBX ou seu ITSP para obter o valor do número máximo de caixas de diálogo iniciais que o gateway, o PBX ou o SBC pode aceitar.

  - O par do Servidor de Mediação deve aceitar o tráfego de mídia diretamente dos pontos de extremidade do Lync. Muitos ITSPs permitem que seu SBC receba tráfego somente do Servidor de Mediação. Contate seu ITSP para determinar se o SBC aceita tráfego de mídia diretamente dos pontos de extremidade do Lync.

  - Os clientes do Lync e um par de Servidor de Mediação devem estar bem conectados, ou seja, localizados na mesma região de rede ou em sites de rede que se conectam à região através de links WAN que não possuem restrições de largura de banda

## Consulte Também

#### Conceitos

[Modos de bypass de mídia no Lync Server 2013](lync-server-2013-media-bypass-modes.md)  
[Bypass de mídia e controle de admissão de chamadas no Lync Server 2013](lync-server-2013-media-bypass-and-call-admission-control.md)

