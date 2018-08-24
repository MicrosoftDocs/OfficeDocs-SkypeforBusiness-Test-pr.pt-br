---
title: 'Lync Server 2013: Topologias suportadas'
TOCTitle: Topologias suportadas
ms:assetid: 3475d430-0394-491b-a09b-ba85bd62be70
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425833(v=OCS.15)
ms:contentKeyID: 49306339
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologias suportadas no Lync Server 2013

 

_**Tópico modificado em:** 2014-01-14_

O Lync Server 2013 suporta a implantação de sites locais em uma organização e a integração de implantações locais com implantações do Skype for Business Online, conhecida como implantação híbrida. Em uma implantação híbrida, alguns usuários são hospedados no local e outros, online.

Para implantações locais, o Lync Server 2013 oferece suporte à implantação de um ou mais sites que podem ser dimensionados para atender aos requisitos de alta disponibilidade e local. É possível estruturar esses sites e seus componentes para atender aos requisitos de acesso e resiliência de sua organização.

Uma implantação local do Lync Server 2013 consiste no seguinte:

  - A implantação deve conter pelo menos um site central (também conhecido como data center). Cada site central deve conter pelo menos um pool de Front-Ends Enterprise Edition ou servidor Standard Edition. Isso consiste no seguinte:
    
      - O pool de Front-Ends Enterprise Edition, que consiste em um ou mais servidores de Front-End (normalmente, pelo menos dois servidores de Front-End para dimensionamento) e um servidor de Back-End separado. Um pool de Front-Ends pode conter um máximo de 12 servidores de Front-End. O balanceamento de carga é exigido para servidores de Front-End. Para o tráfego SIP, é recomendável o balanceamento de carga DNS, mas o balanceamento de carga de hardware também é suportado. Se usar o balanceamento de carga DNS para o tráfego SIP, você ainda precisará de um balanceador de carga de hardware para o tráfego HTTP. É recomendável o espelhamento de SQL Server para uma alta disponibilidade dos bancos de dados. O banco de dados de back-end exige uma instância separada, mas você pode colocar o banco de dados de arquivamento, de monitoramento, de chat persistente e de conformidade do chat persistente com ele. Lync Server 2013 oferece suporte ao uso de um cluster compartilhado para os compartilhamentos de arquivos de sua implantação. Para obter detalhes sobre os requisitos de armazenamento de bancos de dados, consulte [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md). Para obter detalhes sobre os requisitos de armazenamento de arquivos, consulte [Suporte a armazenamento de arquivo no Lync Server 2013](lync-server-2013-file-storage-support.md).
        
        > [!IMPORTANT]  
        > Se colocar os bancos de dados do Lync Server, é altamente recomendável avaliar todos os fatores que podem afetar a disponibilidade e o desempenho. Para verificar os recursos de failover, é recomendável testar todos os cenários de failover.    
      - Servidor Standard Edition que inclui um banco de dados do SQL Server Express colocado.

  - A implantação também pode ter uma ou mais filiais associadas a um site central.

Esta seção descreve os sites e componentes de uma implantação do Lync Server 2013. Para obter detalhes do planejamento de site, topologia e componente do Lync Server 2013, consulte [Conhecimentos básicos de topologia para planejamento do Lync Server 2013](lync-server-2013-topology-basics-you-must-know-before-planning.md) e [Topologias de referência no Lync Server 2013](lync-server-2013-reference-topologies.md) na documentação de planejamento. Para obter detalhes sobre a integração de componentes de versões anteriores, consulte [Caminhos de migração suportados e cenários de coexistência no Lync Server 2013](lync-server-2013-supported-migration-paths-and-coexistence-scenarios.md).

> [!NOTE]  
> Pools alongados não são suportados para funções de servidor front-end, de borda, de mediação e de diretor.

## Topologias e componentes do site central (local)

Embora uma topologia de site central deva incluir um pool de Front-Ends ou servidor Standard Edition, cada site central também pode conter o seguinte:

  - Diversos pools de Front-Ends, que podem estar no mesmo domínio ou em domínios diferentes. No entanto, todos os servidores de Front-End de um pool de Front-Ends e o servidor de Back-End desse pool devem estar no mesmo domínio.

  - Diversos Servidores Standard Edition.

  - Servidor Office Web Apps, que é usado com aplicativos Web do Office em Lync Server 2013 para lidar com o compartilhamento e com a renderização de apresentações do Microsoft PowerPoint.

  - Servidor de borda ou pool de bordas em sua rede de perímetro, se quiser que a implantação ofereça suporte a parceiros federados, conectividade pública de IM (de mensagens instantâneas), um gateway XMPP (Extensible Messaging and Presence Protocol), acesso de usuário remoto, participação de usuários anônimos em reuniões ou Unificação de Mensagens (UM) do Exchange. Não é possível colocar nenhuma outra função de servidor com o servidor de borda. É recomendável o balanceamento de carga DNS, quando apropriado, mas o balanceamento de carga de hardware também é suportado. As interfaces de borda interna e externa devem usar o mesmo tipo de balanceamento de carga. Não é possível usar o balanceamento de carga DNS em uma interface de borda e o balanceamento de carga de hardware na outra interface de borda. Para obter detalhes sobre os requisitos de balanceamento de carga e sobre o suporte, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) na documentação de planejamento e [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de implantação.

  - Servidor de mediação ou pool, se quiser oferecer suporte ao Enterprise Voice ou à conferência discada em um pool de Front-Ends do site central. Dependendo da implantação de suporte do Enterprise Voice, é possível colocar o servidor de mediação em um pool de Front-Ends (o padrão) ou implantar um servidor de mediação ou pool autônomo. É possível usar balanceamento de carga DNS, de hardware ou de aplicativo (quando apropriado) para distribuir o tráfego do par do gateway do pool de servidores de mediação, inclusive um gateway PSTN (rede telefônica pública comutada), PBX IP ou SBC (controle de borda da sessão) do tronco SIP. Para obter detalhes sobre o planejamento da topologia apropriada do servidor de mediação, consulte [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md) na documentação de planejamento.

  - Servidor de Chat Persistente, se quiser que os usuários possam participar de conversas com vários participantes e baseadas em tópico que persistam ao longo do tempo. Para oferecer mais capacidade e confiabilidade aprimorada, sua topologia poderá conter vários computadores executando o Servidor de Chat Persistente. Não é possível colocar o Servidor de Chat Persistente com outras funções de servidor em um pool do Enterprise. No entanto, é possível colocar o Servidor de Chat Persistente em um servidor Standard Edition. O chat persistente exige um banco de dados e, se você implementar a conformidade de chat persistente, um banco de dados de conformidade de chat persistente, porém os bancos de dados poderão ser colocados com o banco de dados de arquivamento, de monitoramento ou no servidor de Back-End de um pool de Front-Ends Enterprise Edition. Para obter detalhes sobre o planejamento da topologia apropriada do Servidor de Chat Persistente, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de planejamento.

  - Monitoramento, se quiser oferecer suporte à coleta de dados sobre sua QoE (experiência de qualidade) de áudio/vídeo e CDR (gravação de detalhes da chamada) para o Enterprise Voice e as conferências de áudio/vídeo de sua implantação. Como opção, também é possível instalar o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager), que usa CDR de monitoramento e dados de QoE para gerar alertas quase em tempo real, mostrando a integridade da confiabilidade da chamada e a qualidade da mídia. O monitoramento, quando implantado, é colocado em servidores Fron-End ou um servidor Standard Edition. O monitoramento exige um banco de dados, mas o banco de dados pode ser colocado com o banco de dados de arquivamento, de chat persistente, do conformidade de chat persistente ou no servidor Back-End de um pool de Front-Ends Enterprise Edition.

  - Arquivamento, se quiser arquivar comunicações de mensagens instantâneas e conteúdo de reuniões (por motivos de conformidade) em sua implantação. O arquivamento, quando implantado, é colocado em servidores de Front-End ou em um servidor Standard Edition. O armazenamento do arquivamento exige a implantação de um banco de dados de arquivamento ou integração com o armazenamento do Exchange 2013. Se usar as duas, o que é conhecido como *modo misto* , o armazenamento do Exchange 2013 será usado parar armazenar dados de arquivos de usuários que estão hospedados no Exchange 2013 e o banco de dados de arquivamento será usado para arquivar os dados de todos os outros usuários de sua implantação. Se precisar de uma banco de dados de arquivamento, ele poderá ser colocado no banco de dados de monitoramento, de chat persistente, de conformidade do chat persistente ou no servidor de Back-End de um pool de Front-Ends. Para obter detalhes sobre o planejamento da topologia de arquivamento apropriada, consulte [Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md) na documentação de planejamento.

  - Diretor ou pool de diretores, se quiser facilitar a resiliência e o redirecionamento de solicitações de usuários do Lync Server 2013 para o pool base do usuário, que pode ser um pool de Front-Ends Enterprise Edition ou um servidor Standard Edition. É recomendável que seja implantado um diretor ou pool de diretores em cada site central que ofereça suporte ao acesso de usuários externos e em cada site central no qual é feita a implantação de um ou mais pools de Front-Ends. Cada pool de diretores pode conter um máximo de dez diretores. Um diretor não pode ser colocado com nenhuma outra função de servidor. Para obter detalhes sobre o planejamento da topologia de diretor apropriada, consulte [Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) na documentação de planejamento.

  - Proxy reverso, que não é um componente do Lync Server 2013, mas será exigido se você quiser oferecer suporte ao compartilhamento de conteúdo da Web com usuários federados ou suporte ao tráfego do Mobility. Não é possível colocar um servidor proxy reverso com uma função de servidor do Lync Server 2013, mas é possível implementar o suporte ao proxy reverso para uma implantação do Lync Server 2013 ao configurar o suporte a um servidor proxy reverso existente em sua organização e que é usado para outros aplicativos. Para obter detalhes sobre servidores proxy reversos, consulte [Configurando servidores de proxy reverso para o Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md) na documentação de implantação.

> [!NOTE]  
> No Lync Server 2013, as conferências de áudio/vídeo, o monitoramento e o arquivamento são executados em servidores de Front-End e não são mais funções de servidor separadas.

Todos os pools de Front-Ends e servidores Standard Edition que você implanta em um site central compartilham qualquer um dos seguintes itens implantados no site central:

  - Diretor ou pool de Diretor

  - Servidor de Mediação autônomo ou pool

  - Servidor Office Web Apps

  - Servidor de Borda ou pool de Borda

  - Pool ou servidor de chat persistente

  - Monitoramento

  - Arquivamento

> [!NOTE]  
> Um servidor do UM do Exchange poderá ser implementado com sua implantação do Lync Server 2013 se você quiser oferecer suporte à integração do sistema de unificaçã de mensagens do Exchange 2013, porém esse não é um componente do site do Lync Server 2013.

Vários sites centrais também podem compartilhar qualquer um dos seguintes itens que você implanta em um site central:

  - Servidor de Mediação autônomo ou pool

  - Servidor de Borda ou pool de Borda

  - Pool ou servidor de chat persistente

  - Arquivamento

  - Monitoramento

> [!NOTE]  
> Um servidor do UM do Exchange pode ser implementado em sua implantação do Lync Server 2013 e compartilhado por vários sites centrais, mas esse não é um componente do site do Lync Server 2013.

Para obter detalhes sobre as funções de servidor do Lync Server 2013, consulte [Funções do servidor no Lync Server 2013](lync-server-2013-server-roles.md) na documentação de planejamento.

Para ver um resumo do suporte à colocação do servidor do Lync Server 2013, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md).

Além das funções e da funcionalidade do servidor abordadas nesta seção, o Lync Server 2013 tem componentes e opções adicionais, que podem incluir alguns ou todos os seguintes itens:

  - Firewalls

  - Gateway de PSTN (se implantar o Enterprise Voice)

  - Servidor do UM do Exchange

  - Balanceamento de carga de DNS

  - Balanceadores de carga de hardware

  - Bancos de dados do SQL Server

  - Compartilhamentos de arquivo

Para obter detalhes sobre todos os recursos, componentes e opções do Lync Server 2013, consulte a documentação de planejamento.

## Topologias e componentes do site da filial (local)

Uma site de filial é associado a um site central e cada Aparelho de Filial Persistente em um site de filial é associado a um pool de Front-Ends Enterprise Edition ou um servidor Standard Edition no site central associado. Os sites de filial dependem do site central para a maioria de suas funcionalidades, portanto os componentes de um site de filial contêm apenas o seguinte:

  - Um Aparelho de Filial Persistente, que combina um gateway de PSTN com algumas funcionalidades do Lync Server. Um servidor de mediação pode ser colocado com a instância do registrador no Aparelho de Filial Persistente e é possível implantar um servidor de mediação autônomo ou pool de servidores de mediação.

  - Um Servidor de Ramificação Persistente, que é um servidor que executa o Windows Server, que tem o software do registrador e do servidor de mediação do Lync Server 2013 instalado.

  - Um gateway de PSTN autônomo (que não faz parte do Aparelho de Ramificação Persistente) e o servidor de mediação autônomo.

Os requisitos para Servidores de Filial Persistente são iguais aos requisitos para qualquer função de servidor do Lync Server 2013.

