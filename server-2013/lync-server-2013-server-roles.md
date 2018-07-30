---
title: 'Lync Server 2013: Funções do servidor'
TOCTitle: Funções do servidor
ms:assetid: 7137fc06-fca2-4e5f-9db5-10c7c29a788c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398536(v=OCS.15)
ms:contentKeyID: 49307074
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Funções do servidor no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-07_

Cada servidor que executa o Lync Server executa uma ou mais *funções de servidor* . A função de servidor é um conjunto definido de funcionalidades do Lync Server oferecidas por esse servidor. Você não precisa implantar todas as funções de servidor disponíveis na sua rede. Instale somente as funções com a funcionalidade desejada.

Mesmo se você não estiver familiarizado com as funções de servidor em Lync Server, o Ferramenta de Planejamento poderá orientá-lo para a melhor solução para os servidores que você precisa implantar, com base nos recursos que você deseja. Esta seção fornece uma visão geral sobre as funções de servidor e os recursos gerais que eles fornecem:

  - Servidor Standard Edition

  - Servidor de front-end e Servidor de back-end

  - Servidor de Borda

  - Servidor de Mediação

  - Diretor

  - Servidor de front-end de bate-papo persistente

  - Repositório de chats persistentes (servidor back-end de chats persistentes)

  - Repositório de conformidade de chats persistentes (servidor back-end de conformidade de chats persistentes)

Na maioria das funções de servidor, para escalabilidade e alta disponibilidade você pode implantar *pools* de vários servidores, todos executando a mesma função de servidor. Cada servidor em um pool deve executar uma função ou funções de servidor. Para a maioria dos tipos de pools no Lync Server, você deve implantar um balanceador de carga para difundir o tráfego entre os diversos servidores no pool. O Lync Server oferece suporte a balanceamento de carga DNS (sistema de nomes de domínio) e balanceadores de carga de hardware.

## Servidor Standard Edition

O servidor Standard Edition foi projetado para pequenas empresas e para projetos piloto de grandes organizações. Permite muitos dos recursos do Lync Server, incluindo os bancos de dados necessários para ser executado em um único servidor. Isso permite que você tenha a funcionalidade do Lync Server a um custo menor, mas não oferece uma verdadeira solução de alta disponibilidade.

O servidor Standard Edition permite que você use mensagens instantâneas (IM), presença, conferência e Enterprise Voice, todos executados em um único servidor.

Para uma solução de alta disponibilidade, use Lync Server Enterprise Edition.

## Servidor de front-end e Servidor de back-end

No Lync Server Enterprise Edition, o servidor Front End é a função núcleo do servidor e executa muitas funções básicas do Lync Server. O servidor Front End, juntamente com os servidores Back-End que fornecem o banco de dados, são as únicas funções de servidor necessárias para qualquer implantação do Lync Server Enterprise Edition.

Um *pool de Front-Ends* é um conjunto de servidores Front-End, configurados de forma idêntica, que trabalham juntos para fornecer serviços a um grupo de usuários comuns. Um pool de vários servidores executando a mesma função fornece a capacidade de escalabilidade e failover.

O servidor Front-End inclui:

  - Registro e autenticação de usuário

  - Informações de presença e troca do cartão contato

  - Serviços de catálogo de endereço e expansão de lista de distribuição

  - Funcionalidade de mensagens instantâneas, incluindo conferências de mensagens instantâneas com vários participantes

  - Webconferências, conferências de discagem PSTN e conferências A/V (se implantadas)

  - Hospedagem de aplicativos, tanto para aplicativos incluídos com Lync Server (por exemplo, o Atendedor de conferência e Aplicativo Grupo de Resposta) e aplicativos de terceiros

  - Opcionalmente, Monitoramento para coletar informações de uso na forma de CDRs (registros de detalhes de chamada) e CERs (registros de erros de chamada). Essas informações fornecem métricas sobre a qualidade da mídia (áudio e vídeo) que atravessa sua rede para chamadas e conferências A/V do Enterprise Voice.

  - Componentes da Web para tarefas compatíveis com base na Web, como agendador da Web e iniciador de ingresso.

  - Opcionalmente, Arquivamento para arquivar comunicações de mensagens instantâneas e conteúdo de reunião por motivos de conformidade. Para obter detalhes, consulte [Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md) na documentação de planejamento.
    
    No Lync Server 2010 e versões anteriores, Monitoramento e Arquivamento eram funções de servidor separadas, não alocadas no servidor front-end.

  - Opcionalmente, e o chat persistente estiver habilitado, serviços Web de chat persistente para gerenciamento de salas de chat e serviços Web de chat persistente para upload/download de arquivos.

Os pools front-end também são o repositórios principal de dados de usuários e conferências. As informações sobre cada usuário são replicadas em três servidores front-end no pool, e o backup delas é realizado nos servidores back-end.

Além disso, um pool de Front-Ends na implantação também executa o *Servidor de gerenciamento Central* , que gerencia e implanta os dados de configuração básica em todos os servidores que executam o Lync Server. O Servidor de Gerenciamento Central também oferece o Shell de Gerenciamento do Lync Server e os recursos de transferência de arquivo.

Os servidores back-end são servidores de banco de dados que executam o Microsoft SQL Server. Eles fornecem os serviços de bancos de dados ao pool front-end. Os servidores back-end atuam como repositórios de backup dos dados de usuários e conferências do pool e são os repositórios principais de outros bancos de dados, como o banco de dados Grupo de Resposta. Você pode ter um único servidor back-end, mas uma solução que usa o espelhamento SQL Server é recomendada para failover. Os servidores back-end não executam softwares do Lync Server.

> [!IMPORTANT]  
> Não recomendamos colocar bancos de dados do Lync Server com outros bancos de dados. Caso contrário, a disponibilidade e o desempenho poderão ser afetados.

As informações armazenadas nos bancos de dados do servidor Back-End incluem informações de presença, listas de contatos dos usuários, dados de conferência, incluindo os dados persistentes sobre o estado de todas as conferências atuais e dados de agendamento de conferência.

## Servidor de Borda

O Servidor de Borda permite que os usuários se comuniquem e colaborem com usuários fora dos firewalls da organização. Esses usuários externos podem incluir os próprios usuários da organização que atualmente trabalham externamente, os usuários de organizações parceiras federadas e usuários externos que foram convidados para participar de conferências hospedadas em sua implantação do Lync Server O Servidor de Borda também permite a conectividade com os serviços de conectividade a redes públicas de IM, incluindo Windows Live, AOL, Yahoo\! e Google Talk.

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


A implantação do servidor de borda também habilita serviços de mobilidade, com suporte à funcionalidade do Lync em dispositivos móveis. Os usuários podem usar os dispositivos móveis Apple iOS, Android, Windows Phone ou Nokia com suporte para realizar atividades como enviar e receber mensagens instantâneas, exibir contatos e exibir presença. Além disso, os dispositivos móveis oferecem suporte a alguns recursos do Enterprise Voice, como clicar para ingressar em uma conferência, telefonar via trabalho, alcance de número único, caixa postal e chamadas perdidas. O recurso de mobilidade também oferece suporte a *notificações por push* para dispositivos móveis que não oferecem suporte a aplicativos em execução em segundo plano. Uma notificação por push é uma notificação enviada a um dispositivo móvel sobre um evento que ocorre enquanto o aplicativo móvel está inativo.

Os servidores de borda também incluem um proxy XMPP completamente integrado, com um gateway XMPP incluído nos servidores front-end. Você pode configurar esses componentes XMPP para permitir que os usuários do Lync Server 2013 adicionem contatos a parceiros com base em XMPP (como Google Talk) para mensagens instantâneas e presença.

Para obter detalhes, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) na documentação de Planejamento.

## Servidor de Mediação

O Servidor de Mediação é um componente necessário para a implementação de Enterprise Voice e conferência de discagem. O Servidor de Mediação traduz a sinalização e, em algumas configurações, a mídia entre sua infraestrutura Lync Server interna e um gateway de rede telefônica pública comutada (PSTN), IP-PBX ou um tronco de protocolo SIP. Você pode executar o Servidor de Mediação colocado no mesmo servidor do servidor front-end ou separado em um pool de Servidor de Mediação independente.

Para obter detalhes, consulte [Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md) na documentação de Planejamento.

## Diretor

Os diretores podem autenticar solicitações de usuários do Lync Server, mas não hospedam contas de usuários nem fornecem serviços de presença ou conferência. Os diretores são mais úteis para aprimorar a segurança em implantações que permitam o acesso de usuários externos. O diretor pode autenticar solicitações antes de enviá-las a servidores internos. No caso de ataque de negação de serviço, o ataque termina no diretor e não atinge os servidores front-end. Para obter detalhes, consulte [Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) na documentação de planejamento.

## Funções do Servidor de Chat Persistente

O chat persistente permite que os usuários participem de conversações baseadas em tópicos com várias pessoas. Essas conversas persistem ao longo do tempo. O servidor front-end de chat persistente executa o serviço de chat persistente. O servidor back-end de chat persistente armazena os dados de histórico e as informações sobre categorias e salas de chat. O servidor back-end de conformidade de chat persistente (opcional) pode armazenar o conteúdo de chats e eventos de conformidade para fins de conformidade.

Os servidores que executam o Lync ServerStandard Edition também podem executar o chat persistente colocado no mesmo servidor. Você não pode colocar o servidor front-end de chat persistente com o Enterprise EditionServidor Front-End.

Para obter detalhes, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md).

## Consulte Também

#### Conceitos

[Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md)  

#### Outros Recursos

[Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md)  
[Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md)  
[Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)

