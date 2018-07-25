---
title: 'Lync Server 2013: Estimando uso e tráfego de voz'
TOCTitle: Estimando uso e tráfego de voz
ms:assetid: 621b08fb-f894-4d91-ac38-e443401b098b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398439(v=OCS.15)
ms:contentKeyID: 49306895
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Estimando uso e tráfego de voz para Lync Server 2013

 

_**Tópico modificado em:** 2012-08-07_

O Microsoft Lync Server 2013, Ferramenta de Planejamento usa a métrica a seguir para estimar o tráfego de usuários em cada local e o número de portas necessárias para dar suporte a esse tráfego.

   Para **Tráfego leve** (uma chamada PSTN por usuário por hora), calcula-se 15 usuários por porta

   Para **Tráfego médio**, (duas chamadas PSTN por usuário por hora), calcula-se 10 usuários por porta

   Para **Tráfego pesado** (três ou mais chamadas PSTN por usuário por hora), calcula-se 5 usuários por porta

O número de portas determina o número de Servidor de Mediação e de gateways que serão necessários. Os gateways PSTN (rede telefônica pública comutada) que a maioria das organizações considera implantar variam de 2 até 960 portas (há gateways com ainda mais portas, mas eles são usados principalmente por provedores de serviços de telefonia).

Por exemplo, uma organização com 10.000 usuários e tráfego médio exigiria 1000 portas. O número de gateways necessário seria igual o número total de portas necessárias, conforme determinado pela capacidade total dos gateways.

