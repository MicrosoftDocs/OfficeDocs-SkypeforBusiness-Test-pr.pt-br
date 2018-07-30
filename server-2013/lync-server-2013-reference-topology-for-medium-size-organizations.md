---
title: 'Lync Server 2013: Topologia de referência em organizações de médio porte'
TOCTitle: Topologia de referência em organizações de médio porte
ms:assetid: 446b0914-2198-445e-ab6e-94802acebd5c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425939(v=OCS.15)
ms:contentKeyID: 49306545
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologia de referência para Lync Server 2013 em organizações de médio porte

 

_**Tópico modificado em:** 2013-10-07_

A topologia de referência com alta disponibilidade e um único data center é projetada para uma organização de pequeno a médio porte com um local central. A topologia exata no diagrama a seguir destina-se a uma empresa com 20.000 usuários.

**Topologia de referência para organizações de médio porte**

![Diagrama de topologia de referência para o data center único](images/Gg425939.12b574fd-0b14-4563-a88c-3c8b0809bb90(OCS.15).jpg "Diagrama de topologia de referência para o data center único")

  - **Acomodar mais usuários, adicionando mais Servidores Front-End.** A topologia exata neste diagrama tem três Servidores Front-End para fornecer suporte a 20.000 usuários. Se você tiver um único site central e mais usuários, poderá simplesmente adicionar mais Servidores Front-End ao pool. O número máximo de usuários por pool é 80.000 com doze Servidores Front-End.
    
    No entanto, a topologia de site único pode dar suporte a mais usuários adicionando outro pool de Front-End ao site.

  - **Recuperação de desastres pode ser adicionado.**    Para esta organização, a alta disponibilidade para seus serviços Lync Server é um recurso necessário, mas a recuperação de desastres, não. O pool Servidores Front-End que eles têm implantado fornece alta disponibilidade.
    
    Se eles quiserem adicionar a capacidade de recuperação de desastres, pode-se considerar estabelecer outro centro de dados e adicionar outro pool de Front End, pareando-o com o pool de Front End no datacenter atual. Então, caso ocorra um desastre que afete o pool primário, os administradores podem falhar os usuários para o pool de backup.

  - **Servidores Back-End estão espelhados.**   Para fornecer mais disponibilidade para recursos de usuário básico, a organização implantou um par espelhado de Servidores Back-End para cada Pool de Front-Ends. Esta é uma nova opção de topologia para Lync Server 2013, e é opcional. Você pode escolher implantar a um único Servidor Back-End.

  - **Monitorando opções de banco de dados do servidor.**    Esta organização implantou o Monitoramento para garantir a qualidade das chamadas do Enterprise Voice e conferências de A/V. O Monitoramento é implantado em todos os Servidores de Front End e o banco de dados de Monitoramento é alocado com os Servidores de Back End. Também fornecemos suporte a topologias o qual o banco de dados de Monitoramento está localizado em um servidor separado.

  - **Alta disponibilidade do servidor de borda.**    Nesta organização de exemplo com 20.000 usuários, apenas um Servidor de Borda é suficiente para o desempenho. No entanto, há um pool de dois Servidores de Borda implantado para fornecer alta disponibilidade.

  - **Opções de implantação de site de filiais.**    A organização nesta topologia tem o Enterprise Voice implantado como sua solução de voz. O Site de Filial 1 não tem um link WAN (rede remota) resiliente ao site central, para que ele tenha um Aparelho de Filial Persistente implantado para manter muitos recursos do Lync Server no caso do link WAN ao site central desativar. No entanto, o Site de Filial 2 tem um link WAN resiliente, portanto, apenas um gateway PSTN (rede telefônica pública comutada) é necessário. O gateway PSTN implantado tem suporte para bypass de mídia, portanto, nenhum Servidor de Mediação é necessário na Filial 2. Para obter detalhes sobre como decidir o que implantar em um site de filia, consulte [Planejamento de resiliência de voz no site da filial no Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md) na documentação de Planejamento.

  - **Balanceamento de carga do DNS.**    O pool de Front-Ends e de Servidores de Borda têm balanceamento de carga do DNS para tráfego SIP implantado. Isso elimina a necessidade de balanceadores de carga de hardware para os Servidores de Borda e reduz significativamente a configuração e a manutenção dos balanceadores de carga de hardware para os outros pools, pois os balanceadores de carga de hardware são necessários somente para tráfego HTTP. Para obter detalhes sobre o balanceamento de carga do DNS, consulte [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md) na documentação de Planejamento.

  - **Implantação do Exchange do UM.** Essa topologia de referência inclui um Unificação de Mensagens (UM) do Exchange Server, que executa o Microsoft Exchange Server, não o Lync Server.
    
    Para obter detalhes sobre o uso do UM do Exchange, consulte [Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) e [Integração de Unificação de Mensagens do Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md) na documentação de Planejamento.

  - **Servidor do Office Web Apps.** Recomendamos implantar um Servidor Office Web Apps ou farm do Servidor Office Web Apps Server em toda organização que utilize webconferência. O Servidor Office Web Apps torna possível que slides do Powerpoint sejam apresentados em webconferências. Para mais informações, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Servidores de Borda são recomendados.**    Embora não seja necessário implantar um Servidor de Borda, é recomendável para qualquer tamanho de implantação. Você pode maximizar o investimento do Lync Server implantando um Servidor de Borda para prestar serviço a usuários que atualmente estão fora dos firewalls de sua organização. Os benefícios incluem o seguinte:
    
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


  - **Diretores podem ser adicionados.**    Se a organização deseja ajudar a aumentar a segurança contra ataques de negação de serviço, ela pode também implantar um pool de Diretores. Um Diretor é uma função de servidor opcional separado em Lync Server que não armazena contas de usuário ou fornece serviços de presença ou conferência. Serve como uma servidor de próximo salto interno o qual um Servidor de Borda roteia o tráfego SIP interno para servidores internos. O Diretor pré-autentica solicitações internas e redireciona-as a um pool de hospedagem de usuário ou servidor. A pré-autenticação no Diretor permite soltar solicitações de contas de usuário desconhecidas para implantação. Um Diretor auxilia na impermeabilização dos Servidores Front End de tráfego malicioso, como ataques de negação de serviço (DoS). Se a rede estiver inundada de tráfego externo inválido em um ataque deste tipo, o tráfego é interrompido no Diretor.

  - **System Center Operations Manager é recomendado.**   Recomendamos que você monitore a integridade da sua implantação do Servidor Lync para ajudar a garantir a disponibilidade de serviço para usuários finais. Você pode monitorar o Lync com o Pacote de Gerenciamento System Center Operations Manager para Lync que está disponível por download gratuito da Microsoft. Com o Pacote de Gerenciamento Lync, você pode obter de forma proativa alertas em tempo real quando os problemas ocorrerem, executar transações sintéticas para testar a funcionalidade ponta a ponta do Lync, obter relatórios de disponibilidade de serviço e assim por diante.  Isso auxilia a responder de forma proativa a questões com sua implantação antes que os usuários finais os experimente.

