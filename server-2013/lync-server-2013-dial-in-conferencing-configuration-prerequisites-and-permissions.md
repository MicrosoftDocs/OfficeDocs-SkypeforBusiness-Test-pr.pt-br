---
title: 'Lync Server 2013: Pré-requisitos e permissões de configuração de conferência discada'
TOCTitle: Pré-requisitos e permissões de configuração de conferência discada
ms:assetid: b3b251e5-78ac-44a2-8c36-2a061c9b2314
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412865(v=OCS.15)
ms:contentKeyID: 49307841
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos e permissões de configuração de conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-20_

A conferência discada é um componente opcional da carga de trabalho de Conferência do Lync Server 2013. Os componentes que você precisa instalar para poder configurar a conferência discada são implantados quando a Construtor de Topologias para projetar a topologia e configurar o pool de Front-Ends ou o servidor Standard Edition. Este tópico descreve o que você precisa fazer para poder configurar a conferência discada.

Esta seção supõe que você leu as seções de planejamento relacionadas à carga de trabalho Conferência e conferência discada em particular.

## Pré-requisitos de configuração de conferência discada

A conferência discada exige os seguintes componentes do Lync Server 2013:

  - UCAS (Unified Communications Application Service) (chamado de *Serviço de Aplicativo* )

  - Aplicativo Atendedor de Conferência

  - Aplicativo Comunicado de Conferência

  - Página da Web Configurações de Conferência Discada

  - Pelo menos um Servidor de mediação do Lync Server 2013 e pelo menos um gateway PSTN

Você implanta esses componentes quando usa o Construtor de Topologias para definir e publicar sua topologia e implanta um pool Front-End ou um servidor Standard Edition. Se você estiver implantando o Enterprise Voice, deverá implantá-lo antes de configurar a conferência discada. Se você não estiver implantando o Enterprise Voice, poderá implantar um Servidor de mediação e um gateway PSTN (Rede Telefônica Comutada Pública) ao implantar seu pool Front-End ou servidor Standard Edition.

> [!NOTE]  
> Se você estiver atualizando a partir do Office Communications Server 2007 R2 para o Lync Server 2013, implante a conferência discada em cada pool que você planeja usar para hospedar conferências do Lync Server 2013. Para obter detalhes sobre como migrar conferências discadas, consulte <a href="migration-from-office-communications-server-2007-r2-to-lync-server-2013.md">Migração do Office Communications Server 2007 R2 para Lync Server 2013</a>.

Esta seção supõe que você fez o seguinte:

  - Aplicou as atualizações mais recentes no seu ambiente do Office Communications Server 2007 R2, se estiver migrando para o Lync Server 2013.

  - Usou o Construtor de Topologias para projetar e configurar sua topologia. Durante a especificação da carga de trabalho Conferência, você selecionou a opção de conferência discada. Para obter detalhes sobre como definir sua topologia, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md) na documentação Implantação.

  - Publicou sua topologia e configurou o pool Front-End ou servidor Standard Edition. Para obter detalhes sobre como publicar a topologia e instalar o Lync Server 2013, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) na documentação Implantação.
    
    > [!NOTE]  
    > Ao instalar sua topologia publicada, a página da Web Configurações de Conferência Discada é instalada no servidor Front-End ou servidor Standard Edition como parte dos Serviços da Web.    
    > [!IMPORTANT]  
    > Se você alterar o caminho para o Repositório de Arquivos em Construtor de Topologias após a implantação do Lync Server 2013, será necessário reiniciar os aplicativos Atendedor de Conferência e Anúncio de Conferência para usar o novo caminho.

  - Implantou o Enterprise Voice. Se não estiver implantando o Enterprise Voice, você terá implantado um Servidor de mediação no servidor Front-End Enterprise Edition ou servidor Standard Edition, ou terá implantado um Servidor de mediação autônomo e um gateway PSTN. Para obter detalhes sobre como implantar o Enterprise Voice, consulte [Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) na documentação Implantação. Para obter detalhes sobre como instalar um Servidor de mediação autônomo e um gateway PSTN, consulte [Implantando Servidores de Mediação e definindo pares no Lync Server 2013](lync-server-2013-deploying-mediation-servers-and-defining-peers.md) na documentação Implantação.

O fluxograma a seguir mostra as etapas que devem ser executadas antes de você poder configurar a conferência discada e as etapas executadas para configurar a conferência discada.

**Implantando a conferência discada**

![Implantação de conferência discada](images/Gg412865.fde8c246-b5ed-4323-a6e7-af1983a5ec86(OCS.15).jpg "Implantação de conferência discada")

## Permissões de conferência discada

Para configurar a conferência discada, é necessário usar as seguintes ferramentas administrativas:

  - Painel de Controle do Lync Server 2013

  - Shell de Gerenciamento do Lync Server

Use essas ferramentas administrativas para definir as configurações de conferência discada e os planos, políticas e outras configurações de discagem exigidas pela conferência discada.

A configuração de uma conferência discada exige qualquer uma das funções administrativas a seguir, dependendo da tarefa:

  - **CsVoiceAdministrator**   Essa função de administrador pode criar, configurar e gerenciar configurações e políticas relacionadas a voz.

  - **CsUserAdministrator**   Essa função de administrador pode habilitar e desabilitar usuários para o Lync Server e atribuir políticas existentes, como políticas de conferência e políticas de PIN, aos usuários.

  - **CsAdministrator**   Essa função de administrador pode executar todas as tarefas de CsVoiceAdministrator e CsUserAdministrator.

## Consulte Também

#### Conceitos

[Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)

