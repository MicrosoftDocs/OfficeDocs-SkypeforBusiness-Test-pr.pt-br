---
title: 'Lync Server 2013: Lista de verificação de tronco SIP'
TOCTitle: Lista de verificação de tronco SIP
ms:assetid: 94f4f03e-19d5-4198-92be-e4076dbb959a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398755(v=OCS.15)
ms:contentKeyID: 49307498
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de tronco SIP para Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Antes de implantar um tronco SIP, você e seu provedor de serviços devem trocar algumas informações básicas de conexão sobre seus respectivos pontos de extremidade de tronco SIP.

Obtenha as informações a seguir para cada gateway ITSP com o qual você se conectará:

  - Endereço IP

  - FQDN (nome de domínio totalmente qualificado)

> [!NOTE]  
> O provedor de serviços pode pedir a você que se conecte a mais de um gateway ITSP. Neste caso, você deve configurar uma conexão entre cada gateway ITSP e cada Servidor de Mediação em seu pool.

As informações que você fornece aos seu provedor de serviços dependem do tipo de conexão do seu tronco SIP:

  - Para MPLS (Multiprotocol Label Switching) ou conexões de rede privada, forneça ao ITSP o Endereço IP roteável publicamente do roteador em sua rede de perímetro (também conhecida como sub-rede filtrada). Verifique se o gateway ou Controlador de Borda de Sessão no ITSP pode alcançar este endereço. Também fornece ao ITSP, o FQDN do seu Servidor de Mediação.

  - Para conexões VPN (rede virtual privada ), forneça ao ITSP o endereço IP do seu servidor VPN.

## Considerações de Certificado

Para determinar se você precisa de um certificado para tronco SIP, verifique com seu ITSP sobre suporte de protocolo:

1.  Se seu ITSP oferecer suporte somente ao protocolo TCP, não será necessário um certificado.

2.  Se seu ITSP oferecer suporte ao protocolo TLS, o ITSP deverá fornecer um certificado a você.

> [!NOTE]  
> O SIP funciona em conjunto com protocolo RTP ou SRTP, os protocolos que gerenciam os dados de voz reais em chamadas VoIP.

## Processo de implantação

Para implementar o lado do Lync Server da conexão do tronco SIP, siga estas etapas:

1.  Usando o Lync Server  Construtor de Topologias, crie e configure a topologia do domínio SIP. Para detalhes, consulte “ [Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md)” na documentação de Implantação.

2.  Usando o Painel de Controle do Lync Server, configure o roteamento de voz para o novo domínio SIP. Para detalhes, consulte " [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md)" na documentação de Implantação.

3.  Teste a conectividade usando o cmdlet **Test-CsPstnOutboundCall**. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server ou a Ajuda para o Shell de Gerenciamento do Lync Server.

