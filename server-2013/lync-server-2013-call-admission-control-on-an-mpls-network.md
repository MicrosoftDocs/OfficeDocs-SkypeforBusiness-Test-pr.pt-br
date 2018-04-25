---
title: 'Lync Server 2013: Controle de admissão de chamadas em uma rede MPLS'
TOCTitle: Controle de admissão de chamadas em uma rede MPLS
ms:assetid: 0beec6be-2431-4255-a3d2-512dd030e66a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398168(v=OCS.15)
ms:contentKeyID: 49305856
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Controle de admissão de chamadas em uma rede MPLS com o Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

Em uma rede de Comutação de Rótulo Multiprotocolo (MPLS), todos os sites são conectados por uma malha completa. Isto é, todos os sites são conectados diretamente à nuvem MPLS, e cada site é provisionado com largura de banda a ser usada em um link WAN para a nuvem MPLS. Não existe hub de rede nem local central para controlar o roteamento IP. A figura abaixo mostra uma rede simples com base na tecnologia MPLS.

**Exemplo de rede MPLS**

![CAC com MPLS](images/Gg398168.54602e6e-ec11-4dae-936d-b01acda8a179(OCS.15).jpg "CAC com MPLS")

Para implantar um controle de admissão de chamada (CAC) em uma rede MPLS, é preciso criar uma região de rede para representar a nuvem MPLS, bem como criar um site de rede para representar cada site de satélite MPLS. A figura a seguir ilustra como a região de rede e os sites de rede devem ser configurados para representar a rede MPLS de exemplo na figura anterior. Os limites gerais da largura de banda e os limites de sessão da largura de banda têm base na capacidade do link WAN a partir de cada site de rede até a região de rede que representa a nuvem MPLS.

**Região de rede e sites de rede para uma rede MPLS**

![Diagrama do Controle de Admissão de Chamadas (CAC) com MPLS](images/Gg398168.f8f76283-5c0c-4133-8a78-3fbbfd016dc4(OCS.15).jpg "Diagrama do Controle de Admissão de Chamadas (CAC) com MPLS")

