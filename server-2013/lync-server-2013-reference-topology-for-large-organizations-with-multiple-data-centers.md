---
title: "Lync Server 2013: Topologia de ref. em grandes org. com vários data centers"
TOCTitle: Topologia de referência em grandes organizações com vários data centers
ms:assetid: 9a6aeae6-629b-49e6-9804-7ef369d7c3dc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398797(v=OCS.15)
ms:contentKeyID: 49307573
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologia de referência para Lync Server 2013 em grandes organizações com vários data centers

 

_**Tópico modificado em:** 2012-10-22_

A topologia de referência para uma grande organização com suporte a vários data centers destina-se a qualquer tamanho de organização com mais de um local central. A topologia exata no diagrama destina-se a uma organização com 50.000 usuários, com 20.000 usuários no Local Central A e 20.000 no Local Central B, e um total de 10.000 no Local Central C e filiais. O tipo de topologia mostrado neste diagrama pode acomodar organizações com qualquer número de usuários.

Além da alta disponibilidade fornecida por pools dos Servidores Front-End, essa topologia adiciona suporte à recuperação de desastres. Os Pools de Front-Ends nos Locais Centrais A e B são pareados juntos. Se um desses pools cair, o administrador pode mudar os serviços dos usuários afetados para o pool pareado no site não afetado.

Esta topologia é mostrada em vários diagramas, com uma visão geral primeiro seguida por exibições detalhadas dos locais centrais.

**Visão geral da topologia de referência para grandes organizações com vários data centers**

![Topologia de referência para vários data centers](images/Gg398797.471e1ce9-be11-44b9-9f4a-59e0551b7b30(OCS.15).jpg "Topologia de referência para vários data centers")

**Topologia de referência para grandes organizações: Visão detalhada do Local Central A**

![Topologias de referência de planejamento A](images/Gg398797.dab33f19-e77b-42da-9047-858fb9851264(OCS.15).jpg "Topologias de referência de planejamento A")

**Topologia de referência para grandes organizações: Visão detalhada do Local Central B**

![Topologias de referência de planejamento B](images/Gg398797.5ccaf1d4-bd53-4cb7-96fe-723147334e7f(OCS.15).jpg "Topologias de referência de planejamento B")

**Topologia de referência para grandes organizações: Visão detalhada do Local Central C**

![Topologias de referência de planejamento C](images/Gg398797.7238ca40-340c-491f-b497-ddc2665dadb6(OCS.15).jpg "Topologias de referência de planejamento C")

  - **Pools de Front-Ends estão emparelhados para habilitar a Recuperação de Desastre.**   Os Pools de Front-Ends no Site A e no Site B estão emparelhados entre si para oferecer suporte para recuperação de desastre. Se o pool em um site falhar, o administrador pode fazer failover dos usuários desse site para o Pool de Front-Ends emparelhado no outro site, com o mínimo de interrupção do serviço para os usuários. Cada um desses dois pools de Front-Ends possui seis servidores, o que é suficiente para todos os 40.000 usuários em ambos os pools no caso de failover. Para obter mais informações, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

  - **Servidores Back-End estão espelhados**   Para oferecer alta disponibilidade para recursos de usuários básicos, a organização implantou um par espelhado de Servidores Back-End para cada Pool de Front-Ends. Esta é uma topologia opcional, e você pode optar por implantar um único Servidor Back-End.

  - **Usar um servidor Standard Edition no site de filial.**   Esta organização considera o Local C como uma filial porque possui apenas 600 funcionários. No entanto, os usuários lá possuem muitas conferências de A/V entre si. Se fosse implantado no Lync Server, como um site de filial, as mídias para essas conferências passariam ao longo da rede de longa distância (WAN) de um site central com o Servidor de Front End implantado. Para evitar essa carga potencial na largura de banda, eles instalaram um par de servidores Standard Edition no local, que hospedará essas conferências. E como os servidores Standard Edition estão instalados lá, o Lync Server, por definição, considera-o uma central, e ele é tratado como tal no Construtor de Topologias e Ferramenta de Planejamento.
    
    Apenas um servidor Standard Edition seria o suficiente para o desempenho aqui, mas a organização implantou dois e os pareou para fornecer alta disponibilidade e caso de um servidor cair.
    
    Embora o Local C seja considerado um local central, não é necessário implantar Servidores de Borda nele. Neste exemplo, o Local C usa os Servidores de Borda implantados no Local A.

  - **Monitoramento e arquivamento**   Esta organização implantou tanto monitoramento quanto arquivamento. Ao implantar monitoramento e arquivamento, eles são executados em cada servidor de front end. Os bancos de dados desses recursos podem ser colocados com o banco de dados de back end, ou localizados em um servidor separado. Esta organização localizou esses bancos de dados em um servidor separado dos servidores de backend, no Local Central B. Os bancos de dados recebem dados do monitoramento e arquivamento dos servidores de front end em todos os sites.

  - **Opções de implantação de site de filial.**   Essa organização na realidade tem mais de 50 filiais, apenas três das quais são mostradas nos diagramas detalhados. Os Sites de Filial 1 e 3 não possuem um link WAN resiliente com o site central, então possuem o Aparelho de Filial Persistente implantado para fornecer serviços de telefonia caso o link WAN com o site central caia. O Site de Filial 2, no entanto, possui um link WAN resiliente, então você só precisa de um gateway de rede telefônica pública comutada (PSTN). O gateway PSTN implantado lá suporta bypass de mídia, para que nenhum Servidor de Mediação seja necessário no Site de Filial B. Para detalhes sobre como decidir o que instalar em um site de filial, consulte [Planejamento para resiliência do Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md) na documentação de Planejamento.

  - **Tronco SIP e Servidor de Mediação.**   Observe que no Local Central B, o Servidor de Mediação não está colocado junto com os Servidores Front End. Isso acontece porque um Servidor de Mediação autônomo é recomendado para locais que usam o tronco SIP. Na maioria das demais instâncias é recomendável colocar o Servidor de Mediação junto com o Servidor Front End. Para detalhes sobre topologias do Servidor de Mediação, consulte [Componentes e topologias para o Servidor de Mediação no Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) na documentação de Planejamento.

  - **O Chat Persistente está implantado.**   Esta organização implantou os servidores necessários para permitir o Chat Persistente. Ela implantou vários servidores de front end de Chat Persistente para lidar com a carga do número de usuários no pool e para fornecer alta disponibilidade. Ela também implantou Conformidade para Chat Persistente, e localizou o armazenamento de Chat Persistente e armazenamento de conformidade de Chat Persistente em servidores separados. Esses armazenamentos podem ser colocados, e podem até mesmo serem colocados com o servidor de back end, mas essa organização escolheu separá-los para fornecer melhor desempenho.

  - **Balanceamento de carga DNS.**   O pool de Front End e o pool do Servidor de Borda possuem implantado o balanceamento de carga DNS para o tráfego SIP. Isso elimina a necessidade de balanceadores de carga de hardware para a interface interna dos Servidores de Borda e diminui significativamente a quantidade de tempo perdido na configuração e manutenção dos balanceadores de carga de hardware para os outros pools, visto que os balanceadores de carga de hardware são necessários apenas para tráfego HTTP. Para detalhes sobre o balanceamento de carga DNS, consulte [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md) na documentação de Planejamento.

  - **Implantação da UM do Exchange.**  O Lync Server trabalha com implantações *locais* da Unificação de Mensagens (UM) do Exchange e com a UM do Exchange *hospedada* . O Local Central A inclui um Servidor Unificação de Mensagens (UM) do Exchange que executa o Microsoft Exchange Server, não o Lync Server. A funcionalidade do UM do Exchange para o Lync Server é executada no pool de Front End.
    
    O Local Central B usa o Exchange hospedado, portanto a funcionalidade do Servidor de UM do Exchange UM também é hospedada.
    
    Para obter detalhes sobre o uso do UM do Exchange, consulte [Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) e [Integração de Unificação de Mensagens do Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md) na documentação de Planejamento.

  - **Servidor dos aplicativos web do Office.**   Recomendamos implantar o Servidor dos aplicativos web do Office ou o farm do Servidor dos aplicativos web do Office em todas as organizações que usam webconferência. Você pode implantar um único farm do Servidor dos aplicativos web do Office em um local que serve tráfego de todos os sites, ou implantá-lo em cada local. O Servidor dos aplicativos web do Office possibilita slides do Powerpoint em webconferências. Para obter mais informações, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Diretores podem ser adicionados.**   Se essa organização desejasse aumentar a segurança contra ataques de negação de serviço, ela poderia também implantar um pool de Diretores. Um Diretor é uma função de servidor opcional e separada no Lync Server que não abriga contas de usuários ou fornece presença ou serviços de conferência. Ele serve como um servidor de próximo salto interno para o qual um Servidor de Borda roteia tráfego SIP de entrada destinado a servidores internos. O Diretor pré-autentica solicitações de entrada e as redireciona para o pool ou servidor primário. A pré-autenticação no Diretor possibilita recusar solicitações de contas de usuário desconhecidas à implantação. Um Diretor ajuda a isolar os servidores de Front End de tráfego mal intencionado, como ataques de negação de serviço (DoS). Se a rede for inundada por tráfego externo inválido em tal ataque, o trafego termina no Diretor.

  - **System Center Operations Manager está implantado.**  Recomendamos monitorar a integridade da implantação do Lync Server para garantir disponibilidade do serviço aos usuários finais. Você pode monitorar o Lync com o Pacote de Gerenciamento do System Center Operations Manager para o Lync que está disponível como download gratuito da Microsoft. Com o Pacote de Gerenciamento do Lync, você pode obter de forma proativa alertas em tempo real quando os problemas ocorrerem, executar transações sintéticas para testar a funcionalidade ponta a ponta do Lync, obter relatórios de disponibilidade de serviço e assim por diante.  Isso auxilia a responder de forma proativa a problemas com sua implantação antes que os usuários finais passem por eles.
    
    Esta organização implantou um servidor System Center Operations Manager em cada local central.

