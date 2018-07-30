---
title: 'Lync Server 2013: Topologia de referência em pequenas organizações '
TOCTitle: 'Topologia de referência em pequenas organizações '
ms:assetid: 0453aeee-c41f-44e6-a6e0-aaace526ca08
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398095(v=OCS.15)
ms:contentKeyID: 49305717
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologia de referência para Lync Server 2013 em pequenas organizações

 

_**Tópico modificado em:** 2013-10-07_

A topologia de referência para pequenas organizações mostra como é possível implantar uma solução robusta, altamente disponível implantando somente três servidores executando o Lync Server.

**Topologia de referência para pequenas organizações**

![Diagrama de topologia de referência que implanta três servidores](images/Gg398095.25196d0d-dd07-451b-83ba-94c0ddf59030(OCS.15).jpg "Diagrama de topologia de referência que implanta três servidores")

  - **Par de servidores Standard Edition implantado**     Essa organização conta com 4.000 usuários em seu local central. A organização implementou dois servidores Standard Edition e os parearem a fim de habilitar a alta disponibilidade e a recuperação de desastre. Cada servidor hospeda 2.000 usuários, mas as informações sobre todos os usuários são sincronizadas entre os dois servidores. Se um ficar inativo, um administrador poderá fazer o failover de tais usuários para que sejam atendidos pelo outro servidor, com o mínimo de perturbação para os usuários. Para obter mais informações sobre recursos de alta disponibilidade e recuperação de desastre no Lync Server 2013, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

  - **A implantação de um Servidor de Borda é recomendada.**    Embora não seja necessário ter um Servidor de Borda para IM, presença e conferência, nós o recomendamos até mesmo para pequenas implantações. É possível maximizar o investimento no Lync Server com a implantação de um Servidor de Borda para fornecer serviço aos usuários atualmente fora dos firewalls da organização. Os benefícios incluem:
    
      - Os próprios usuários da sua organização podem usar a funcionalidade do Lync Server se estiverem trabalhando de casa ou estiverem viajando.
    
      - Os usuários podem convidar usuários externos a participar de reuniões.
    
      - Se você tiver uma organização de parceiro, fornecedor ou cliente que também usa o Lync Server, poderá formar um *relacionamento federado* com essa organização. Em seguida, sua implantação do Lync Server reconhecerá os usuários dessa organização federada, levando a melhor colaboração.
    
      - Seus usuários podem trocar mensagens instantâneas com usuários de serviços públicos de mensagens instantâneas, incluindo qualquer um ou todos os seguintes: Windows Live, AOL, Yahoo\! e Google Talk\!. Observe que uma licença separada pode ser necessária para a conectividade de mensagens instantâneas públicas com esses serviços.
        
        > [!IMPORTANT]  
        > <ul>        
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>        
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>        
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>        </ul>


  - **Sobrevivência do site filial.**    Essa organização está executando um programa piloto do recurso Enterprise Voice do Lync Server. Alguns usuários estão usando o Lync Server como única solução de voz. Alguns desses usuários pilotos do Voice estão localizados no site filial. O site filial não possui um link confiável de rede de longa distância (WAN) até o site central, assim, um Aparelho de Filial Persistente é implantado lá. Com essa implantação, mesmo que o link de WAN pare de funcionar, os usuários do site filial ainda poderão fazer e receber chamadas (tanto chamadas dentro da organização quanto PSTN), ainda terão a funcionalidade do correio de voz, assim como a comunicação por mensagens instantânea (IM) entre duas partes. Os usuários ainda podem ser autenticados quando um link WAN estiver indisponível.

  - **Implantação do Exchange do UM.** Essa topologia de referência inclui um Unificação de Mensagens (UM) do Exchange Server, que executa o Microsoft Exchange Server, não o Lync Server.
    
    Para obter detalhes sobre o uso do UM do Exchange, consulte [Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) e [Integração de Unificação de Mensagens do Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md) na documentação de Planejamento.

  - **Office Web Apps Server.** Recomendamos a implantação de um farm do Office Web Apps Server ou do Office Web Apps Server em toda organização que usa webconferência. O Office Web Apps Server possibilita a apresentação de slides do PowerPoint em webconferências. Para obter mais informações, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

