---
title: 'Lync Server 2013: Visão geral de acesso de usuário externo'
TOCTitle: Visão geral de acesso de usuário externo
ms:assetid: 97aded6c-5fa3-4225-95a6-9ad094d61654
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398775(v=OCS.15)
ms:contentKeyID: 49307542
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Nesta documentação, usamos o termo *usuário externo* para definir uma grande categoria de usuários que se comunica com seus usuários do Lync Server 2013 e Lync 2013 de fora do firewall. Usuários externos que você pode autorizar a comunicar o Lync Server 2013 com usuário internos (isto é, usuários que entraram no Lync Server de dentro do firewall) podem incluir:

  - **Usuários remotos**   Usuários da sua organização que entram no Lync Server de fora do firewall.

  - **Usuário federados**   Usuários que têm uma conta com um cliente ou organização parceira de confiança, como Lync Server 2010, Lync Server 2013 ou Office Communications Server 2007 R2. Usuário federados podem também ser membros de organizações parceiras definidas, usando protocolo XMPP (extensible messaging and presence protocol) por meio de proxy XMPP no Servidor de Borda e gateway XMPP no Servidor Front-End ou pool. Uma relação de confiança definida, chamada federação, não está relacionada ou é dependente de uma relação de confiança do Serviços de Domínio Active Directory.
    
    > [!NOTE]  
    > A data de fim de vida de junho de 2014 para o AOL e o Yahoo! foi anunciada. Para detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.

  - **Usuários de Conectividade pública de mensagens instantâneas**   Contatos que seus usuários estabelecem através de serviços de conectividade a redes públicas de IM (Windows Live, Yahoo\! e AOL).

  - **Usuários móveis**   Usuários que são membros da sua organização e que usam um smartphone ou tablet com sign in de cliente Lync Mobile em sua implantação interna e que podem se comunicar com outras classes de usuários. O usuário móvel usa serviços de mobilidade publicados através de proxy reverso para acessar a implantação interna. Para obter detalhes sobre recursos e capacidades disponíveis ao Lync Mobile, consulte as Tabelas de Comparação de Clientes Móveis em [http://go.microsoft.com/fwlink/?linkid=234777\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=234777%26clcid=0x416).

  - **Usuários anônimos**   Usuários que não possuem uma conta de usuário no Serviços de Domínio Active Directory da sua organização ou em um domínio federado com suporte, mas receberam convites para participar remotamente de uma conferência local.

Sua implantação de borda fornece acesso externo para os seguintes tipos de comunicação:

  - **IM e presença**   Usuários externos autorizados podem participar de conversas de IM e conferências e podem obter informações sobre o status de presença uns dos outros. Usuários de provedores de serviços públicos de IM podem participar de conversas de IM com usuários individuais do Lync Server em sua organização e acessar informações de presença, mas não podem participar de conferências de IM com vários participantes baseadas no Lync Server. É uma comunicação estritamente ponto-a-ponto. A transferência de arquivos não é suportada para usuários de provedores de serviços públicos de IM e áudio/vídeo em comunicações ponto-a-ponto são suportados para usuários do Windows Messenger 2011, mas não para usuários de provedores de serviços públicos de IM.
    
    Ambos os protocolos SIP e XMPP são suportados. Para fornecer serviços para XMPP, consulte [Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md).

  - **Webconferências**   Usuários externos autorizados podem participar de conferências hospedadas em sua implantação do Lync Server. Usuários remotos, federados e anônimos podem ser habilitados para participação em webconferências, mas usuários de IM públicos não podem participar de conferências. Dependendo das opções selecionadas, usuários habilitados para webconferências podem participar de compartilhamentos de área de trabalho e aplicativos e podem agir como organizadores ou apresentadores de reunião.

  - **Conferências de A/V**   Usuários externos autorizados podem participar em conferências de áudio e vídeo que sua implantação de Lync Server hospeda. Áudio/vídeo em comunicações ponto-a-ponto são suportados por usuários do Windows Messenger 2011, mas não de outros provedor de serviços públicos de IM.

Para controlar as comunicações, você pode configurar uma ou mais políticas que definem como os usuários dentro e fora do seu firewall se comunicam entre si. Você também pode configurar definições e aplicar políticas para usuários internos individuais ou para tipos específicos de usuários externos, para controlar as comunicações com usuários externos.

Funções do Lync Server 2013 usadas para fornecer acesso externo:

**Servidor de borda**   O Servidor de Borda é um servidor ou pool de servidores que executa os serviços que permitem acesso externo à IM e presença, conferência, áudio/vídeo e outros serviços de mídia (por exemplo, transferência de arquivo). Opcionalmente, você pode configurar o Servidor de Borda para federar com outra implantação de Lync Server ou Office Communications Server 2007 R2, outras implantações de XMPP. O recurso opcional de conectividade IM pública é ativado e configurado através do Servidor de Borda.

**Diretor**   O Diretor é um servidor opcional ou pool de servidores executado o a função Lync Server 2013  Diretor que pré-autentica solicitações de usuário e de rota à página inicial dos usuários Servidor Front-End ou Pool de Front-Ends, mas não hospeda nenhuma conta de usuário.

**Proxy Reverso**   Um proxy reverso é um termo geral para servidores especializados que publicam recursos disponíveis na rede interna e recuperam informações de clientes do recurso publicado. O Lync Server 2013 usa o proxy reverso para publicar uma série de recursos, como reuniões de conferência, locais de participação de conferência, o catálogo de endereços, expansão da lista de distribuição, download de conteúdo de encontro, atualização de dispositivo, serviços de mobilidade, etc. Um proxy reverso que pode atender aos requisitos de publicação dos locais de recursos necessários pode ser usado. O Microsoft Forefront Threat Management Gateway (TMG) 2010 é usado como exemplo para ilustrar as regras de publicação necessárias, mas o Forefront TMG 2010 não é obrigatório.

> [!IMPORTANT]  
> Lync Server 2013 suporta IPv4 e IPv6. O Windows Server 2008 R2, Windows Server 2012 e Windows Server 2012 R2 usam uma pilha dupla que pode usar tanto IPv4 quanto IPv6 ao mesmo tempo. Isso é importante, devido à natureza transitória de uma implantação mudando de IPv4 para IPv6. O IPv4 pode ser suportado em algumas áreas, onde em outras áreas da implantação, o IPv6 pode ser usado. Isso é importante especialmente onde implantações de Internet e internas estão em questão. Os clientes externos devem se comunicar através de um proxy reverso para usar serviços como mobilidade, reuniões, download de catálogo de endereços, etc. No momento, o Forefront Threat Management Gateway 2010 e Internet Security and Acceleration Server 2006 não suportam endereço IPv6, independentemente da versão do sistema operacional em que são implantados. Você deve planejar de acordo, em relação ao uso de IPv6 e IPv4, pois eles se relacionam a clientes externos.
