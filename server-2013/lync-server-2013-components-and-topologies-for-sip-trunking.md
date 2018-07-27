---
title: 'Lync Server 2013: Componentes e topologias para tronco SIP'
TOCTitle: Componentes e topologias para tronco SIP
ms:assetid: 8ed9a9d0-517e-4f36-a131-22cdafa257fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398720(v=OCS.15)
ms:contentKeyID: 49307433
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

A figura a seguir representa a topologia de troncos SIP no Lync Server.

**Topologia de troncos SIP**

![Topologia de tronco SIP](images/Gg398720.669fb55d-7c81-4e21-9421-fabc43d6e064(OCS.15).jpg "Topologia de tronco SIP")

Conforme mostra o diagrama, uma VPN (rede virtual privada) IP é usada para a conectividade entre a rede corporativa e o provedor de serviços da rede de telefonia pública comutada (PSTN). O objetivo desta rede privada é fornecer conectividade IP, aprimorar a segurança e (opcionalmente) obter garantias de qualidade de serviços (QoS). Devido à natureza de uma VPN, não é necessário usar protocolo TLS para o tráfego de sinalização SIP ou SRTP para tráfego de mídia. As conexões entre a empresa e o provedor de serviços consistem, portanto, em conexões TCP básicas para SIP e RTP básico (via protocolo UDP) em mídia encapsulada através de uma VPN IP. Certifique-se de que todos os firewalls entre os roteadores VPN possuem portas abertas para permitir a comunicação e que os endereços IP nas bordas externas dos roteadores VPN sejam roteáveis publicamente.

> [!IMPORTANT]  
> Entre em contato com seu provedor de serviços para determinar se ele oferece suporte para alta disponibilidade, incluindo failover. Em caso positivo, será necessário determinar os procedimentos para configurá-lo. Por exemplo, é necessário configurar somente um endereço IP e um tronco SIP em cada Servidor de Mediação ou vários troncos SIP em cada Servidor de Mediação?<br />Se houver vários site central, pergunte também se o provedor de serviço é capaz de habilitar conexões de e para outro site central.

> [!NOTE]  
> Para troncos SIP, é altamente recomendável implantar o Servidor de Mediação autônomo. Para detalhes, consulte <a href="lync-server-2013-deploying-mediation-servers-and-defining-peers.md">Implantando Servidores de Mediação e definindo pares no Lync Server 2013</a> na documentação de Implantação.

## Como proteger o Servidor de Mediação para troncos SIP

Para fins de segurança, você deve configurar uma LAN virtual (VLAN) para cada conexão entre os dois roteadores VPN. O processo real para configurar uma VLAN varia de um fabricante de roteador para outro. Para detalhes, entre em contato com o fornecedor do seu roteador.

É recomendável seguir estas orientações:

  - Configure uma LAN virtual (VLAN) entre o Servidor de Mediação e o roteador VPN na rede de perímetro (também conhecida como sub-rede filtrada).

  - Não permita que pacotes de transmissão ou multicast sejam transferidos do roteador para a VLAN.

  - Bloqueie quaisquer regras de roteamento que direcionem o tráfego do roteador para qualquer lugar exceto o Servidor de Mediação.

Se você usa um servidor VPN, é recomendável seguir as seguintes orientações:

  - Configure uma VLAN entre o servidor VPN e o Servidor de Mediação.

  - Não permita que pacotes de transmissão ou multicast sejam transferidos do servidor VPN para a VLAN.

  - Bloqueie qualquer regra de roteamento que direcione o tráfego do servidor VPN para qualquer lugar exceto o Servidor de Mediação.

  - Criptografe dados na VPN usando encapsulamento de roteamento genérico (GRE).

