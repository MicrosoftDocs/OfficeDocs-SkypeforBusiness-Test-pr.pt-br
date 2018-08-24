---
title: 'Lync Server 2013: IM e presença'
TOCTitle: IM e presença
ms:assetid: 6a93ae95-3b64-410b-ab72-74dea232f065
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg417162(v=OCS.15)
ms:contentKeyID: 49307017
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# IM e presença no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-07_

O IM (sistema de mensagens instantâneas) e a presença são automaticamente instalados em todas as implantações do Lync Server.

As informações de *presença* permitem que os usuários abordem os colegas no momento certo e com a forma certa de comunicação para levar a um ambiente de trabalho mais produtivo. A presença de um usuário é uma coleção de informações que incluem disponibilidade, disposição para se comunicar, observações adicionais (como o local e o status) e como o usuário pode ser contatado. A presença foi aprimorada no Lync Server com imagens, informações sobre o local e um avançado conjunto de estados de presença que inclui "Ausente do Trabalho", "Não Perturbe" e "Volto Logo", além dos estados básicos, como "Disponível", "Ocupado" e "Em Conferência". Os administradores também podem definir estados de presença personalizados, específicos da empresa.

A opções de gerenciamento de contatos e de acesso do usuário permitem aos usuários controlar as informações que outras pessoas podem ver. Os usuários podem definir diferentes níveis de contatos, cada um deles pode exibir diferentes níveis de informações de presença.

Ao observar uma lista de Contatos, os usuários podem encontrar tudo o que precisam saber. Os ícones coloridos simples indicam o status de presença de outros usuários e imagem e o local também são mostrados.

Com a integração entre o Lync Server e outros produtos, como o Outlook e o SharePoint, sempre que o nome do contato aparece (como em uma mensagem de email ou em um site de equipe), as informações de status e de contato também são exibidas. Além disso, se você implantar o Exchange 2013, o Lync Server e o Exchange 2013 poderão compartilhar um repositório unificado de contatos que pode ser acessado pelos clientes dos dois produtos.

Com as mensagens instantâneas no Lync Server, os usuários podem enviar mensagens rapidamente para outros com informações imediatas. Se você preferir, os usuários também poderão se comunicar com usuários de redes públicas de mensagens instantâneas, como MSN/Windows Live, Yahoo\! e AOL. Observe que uma licença separada pode ser necessária para a conectividade de serviços públicos de IM com Windows Live, AOL e Yahoo\!. O Lync Server também inclui compatibilidade com o protocolo XMPP, para que seus usuários possam trocar mensagens instantâneas e informações de presença com usuários de serviços XMPP como o Google Talk.

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


O histórico de conversa permite aos usuários controlar as conversas de mensagens instantâneas antigas e recuperar as informações que podem ter sido comunicadas por mensagens instantâneas meses atrás.

O recurso Chat Persistente permite que os usuários ingressem em conversas com vários participantes baseadas em tópicos que são preservadas com o passar do tempo. As mensagens publicadas nas salas de chat (fóruns de discussão) podem ser persistentes (ou seja, disponível ao longo do tempo), para que pessoas de locais e departamentos diferentes possam participar, mesmo quando não estiverem todas online ao mesmo tempo.

Se sua organização precisa seguir as normas de conformidade, você pode implantar um recurso de arquivamento de mensagens para arquivar o conteúdo de mensagens instantâneas para todos os usuários da sua organização ou para apenas determinados usuários especificados por você. Se você também implantar o Exchange 2013, seu arquivo de mensagens instantâneas poderá ser integrado ao recurso Bloqueio In-loco do Exchange para proporcionar uma experiência unificada de administração da conformidade.

