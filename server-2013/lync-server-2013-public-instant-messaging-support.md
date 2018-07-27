---
title: 'Lync Server 2013: Suporte ao sistema de mensagens instantâneas públicas'
TOCTitle: Suporte ao sistema de mensagens instantâneas públicas
ms:assetid: 1f45163b-52c6-4a78-b9c8-dfe3abe4e5eb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204732(v=OCS.15)
ms:contentKeyID: 49306101
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte ao sistema de mensagens instantâneas públicas no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-07_

O Lync Server 2013 suporta o uso de provedores de conectividade de IM pública licenciada, assim como o uso de Protocolo de Presença e Mensagem eXtensible (XMPP) para implementar um tipo especial de federação que permite um Lync Server acessar parceiros de domínio XMPP configurados usando o cliente do Lync 2013.

## Suporte do provedor de conectividade de IM público

Os parceiros de conectividade de mensagem instantânea pública suportados atualmente são:

  - America Online

  - Windows Live

  - Yahoo\!

Para comunicações com usuários do Windows Live, o Lync Server 2013 suporta IM ponto a ponto e chamadas de áudio e vídeo. Para comunicações com AOL e Yahoo\!, o Lync Server 2013 suporta IM ponto a ponto. Uma licença separada pode ser necessária.

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


## Suporte de Federação XMPP

A federação XMPP suporta a comunicação de usuários do Lync com usuários de domínio XMPP configurado que usam um provedor público, como GTalk. As comunicações com estes usuários podem incluir o seguinte:

  - IM ponto a ponto e presença

  - Criação de contatos federados XMPP no cliente Lync

