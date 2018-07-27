---
title: Pré-requisitos de configuração do recebimento de chamadas em grupo e direitos do usuário
TOCTitle: Pré-requisitos de configuração do recebimento de chamadas em grupo e direitos do usuário
ms:assetid: 8757b1d3-751d-49c3-b1b8-b678f663f18e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945641(v=OCS.15)
ms:contentKeyID: 52057645
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos de configuração do recebimento de chamadas em grupo e direitos do usuário

 

_**Tópico modificado em:** 2013-01-30_

O recebimento de chamadas de grupo é um recurso de gerenciamento de chamadas que é instalado por padrão quando você implanta o Enterprise Voice. Este tópico descreve o que é necessário ter no local antes de configurar o recebimento de chamadas de grupo e os direitos do usuário que são necessários para executar as tarefas de configuração.

Esta seção considera que você leu a documentação de planejamento relacionada ao recebimento de chamadas de grupo (consulte [Planejando para o recebimento de chamadas em grupo no Lync Server 2013](lync-server-2013-planning-for-group-call-pickup.md)).

## Pré-requisitos de configuração do recebimento de chamadas de grupo

O recebimento de chamadas de grupo requer os seguintes componentes:

  - Serviço de aplicativos

  - Aplicativo de Estacionamento de Chamada

Estes componentes são instalados automaticamente ao implantar o Enterprise Voice.

## Direitos do usuário de configuração do recebimento de chamadas de grupo

Você usa as seguintes ferramentas administrativas para configurar o recebimento de chamadas de grupo:

  - Shell de Gerenciamento do Lync Server

  - Ferramenta do Kit de recursos da SEFAUtil

Use o Shell de Gerenciamento do Lync Server para criar e gerenciar os grupos de recebimento de chamadas na tabela da órbita do Estacionamento de Chamada. Use a ferramenta do Kit de recursos da SEFAUtil para atribuir um grupo de recebimento de chamadas e ativar ou desativar o recebimento de chamadas de grupo para usuários.

Configurar o recebimento de chamadas de grupo requer qualquer uma das seguintes funções administrativas, dependendo da tarefa:

  - **CsVoiceAdministrator:** Esta função de administrador pode criar, configurar e gerenciar todas as políticas e configurações relacionadas à voz.

  - **CsUserAdministrator:** Esta função de administrador pode ativar o recebimento de chamadas de grupo para os usuários. Esta função de administrador também possui acesso à exibição somente leitura para todas as configurações de voz.

  - **CsServerAdministrator:** Esta função de administrador pode gerenciar, monitorar e solucionar problemas de servidores e serviços.

  - **CsAdministrator:** Esta função de administrador pode executar todas as tarefas do CsVoiceAdministrator, CsServerAdministrator e CsUserAdministrator.

> [!NOTE]  
> Para obter detalhes sobre direitos administrativos, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de planejamento.

## Consulte Também

#### Conceitos

[Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)  

#### Outros Recursos

[Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)

