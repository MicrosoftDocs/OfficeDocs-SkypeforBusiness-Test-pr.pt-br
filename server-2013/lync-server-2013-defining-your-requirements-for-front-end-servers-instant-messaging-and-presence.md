---
title: 'Lync Server 2013: Definindo seus requisitos para Servidores Front-End Servers, sistema de mensagens instantâneas e presença'
TOCTitle: Definindo seus requisitos para Servidores Front-End Servers, sistema de mensagens instantâneas e presença
ms:assetid: c21198bc-520c-4d17-8b84-7ff1475b9b0a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412956(v=OCS.15)
ms:contentKeyID: 49308014
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos para Servidores Front-End Servers, sistema de mensagens instantâneas e presença no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-07_

A principal tarefa do planejamento para mensagem instantânea (IM) e presença é garantir que você possua Servidores de Front-End suficientes para seus usuários.

## Habilitando a comunicação com usuários externos

É possível aumentar muito os benefícios do seu investimento no Lync Server habilitando seus usuários a se comunicarem com usuários externos. Os usuários externos podem incluir:

  - **Usuários remotos**   Os proprietários de sua própria organização, quando estão trabalhando fora de seus firewalls e estão usando seus laptops ou outros dispositivos do Lync Server.

  - **Usuários federados**   Usuários de empresas com as quais você trabalha que também executam o Lync Server. Para permitir que seus usuários entrem em contato facilmente com esses usuários, crie relacionamentos federados com essas empresas.

  - **Usuários públicos**   Usuários de serviços de IM pública, como serviços de IM fornecidos pela rede do Windows Live de serviços de Internet, Yahoo\! e AOL e usuários de provedores e servidores que usam o XMPP (Extensible Messaging and Presence Protocol), como Google Talk e Jabber.
    
    > [!NOTE]  
    > Observe que talvez seja necessário ter uma licença separada para conectividade de IM pública com o Windows Live, AOL e Yahoo!    
    > [!IMPORTANT]  
    > <ul>    
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>    
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>    
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>    </ul>


Para habilitar qualquer um ou todos esses cenários, é necessário implantar um Servidor de Borda para ajudar a permitir as comunicações seguras entre sua implantação do Lync Server e os usuários externos. Os usuários remotos de sua organização e os usuários em organizações federadas poderão ver a presença um do outro e se comunicar usando IM. Para obter detalhes sobre como habilitar a comunicação com usuários externos, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) na documentação Planejamento.

## Arquivando conteúdo de IM

O Lync Server oferece recursos que você pode usar se sua organização devem seguir os regulamentos de conformidade. É possível usar o Arquivamento para arquivar o conteúdo de mensagens IM para todos os usuários em sua organização ou para apenas determinados usuários especificados. Para obter detalhes, consulte [Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md) na documentação de Planejamento.

Se você também possui o Microsoft Exchange Server 2013 implantado, é possível integrar o arquivamento dos dados do Exchange com o arquivamento dos dados do Lync Server e usar uma única ferramenta para pesquisar ambos os tipos de dados arquivados. Para obter mais informações, consulte [Configurando o Microsoft Lync Server 2013 para usar arquivamento do Microsoft Exchange Server 2013](configuring-lync-server-2013-to-use-microsoft-exchange-server-2013-archiving.md).

