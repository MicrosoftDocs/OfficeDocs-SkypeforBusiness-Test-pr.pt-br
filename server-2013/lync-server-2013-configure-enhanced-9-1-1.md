---
title: 'Lync Server 2013: Configurar 9-1-1 Avançado'
TOCTitle: Configurar 9-1-1 Avançado
ms:assetid: 5967de00-c8b9-4923-86da-6ad3369a4cad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398390(v=OCS.15)
ms:contentKeyID: 49306802
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar 9-1-1 Avançado no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-24_

O 9-1-1 Avançado (E9-1-1) é um recurso de notificação de emergência que associa o número de telefone de quem está ligando a um endereço cívico ou de uma rua. Usando essas informações, o PSAP (Ponto de Atendimento de Segurança Pública) consegue expedir imediatamente os serviços de emergência para o chamador com problemas.

Para oferecer suporte ao E9-1-1, o Lync Server 2013 deve ser capaz de associar corretamente um local a um cliente e garantir que essas informações sejam usadas para rotear a chamada de emergência para o PSAP mais próximo.

Para obter detalhes sobre como planejar uma implantação do E9-1-1, consulte [Planejamento para serviços de emergência (E9-1-1) no Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md).

> [!IMPORTANT]  
> O Lync Server 2013 só oferece suporte ao E9-1-1 nos Estados Unidos. Para implantar o E9-1-1, você precisará configurar uma conexão de SIP com um provedor de serviços de E9-1-1 qualificado ou implantar um gateway de ELIN (número de identificação de local de emergência) em um provedor de serviços de E9-1-1 com uma PSTN (Rede Telefônica Pública Comutada). Para obter detalhes, consulte <a href="lync-server-2013-enhanced-9-1-1-e9-1-1-and-mediation-server.md">9-1-1 Avançado (E9-1-1) e Servidor de Mediação no Lync Server 2013</a>. Para obter detalhes sobre como configurar conexões de tronco, consulte <a href="lync-server-2013-configure-a-trunk-with-media-bypass.md">Configurar um tronco com bypass de mídia no Lync Server 2013</a>.

## Nesta seção

  - [Configurar um roteamento de voz do E9-1-1 no Lync Server 2013](lync-server-2013-configure-an-e9-1-1-voice-route.md)

  - [Criar políticas de localização no Lync Server 2013](lync-server-2013-create-location-policies.md)

  - [Configurar informações de local para o E9-1-1 no Lync Server 2013](lync-server-2013-configure-site-information-for-e9-1-1.md)

  - [Configurar o banco de dados de localização no Lync Server 2013](lync-server-2013-configure-the-location-database.md)

  - [Configurar os recursos do E9-1-1 Avançado no Lync Server 2013](lync-server-2013-configure-advanced-e9-1-1-features.md)

