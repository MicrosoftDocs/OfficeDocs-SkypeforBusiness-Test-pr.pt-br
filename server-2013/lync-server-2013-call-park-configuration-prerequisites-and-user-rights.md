---
title: 'Lync Server 2013: Pré-requisitos de Estacionamento de Chamadas e direitos de usuário'
TOCTitle: Pré-requisitos de Estacionamento de Chamadas e direitos de usuário
ms:assetid: 25b8cfe0-e4e7-487c-9e78-8c040f629059
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425730(v=OCS.15)
ms:contentKeyID: 49306160
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos de Estacionamento de Chamadas e direitos de usuário no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-10_

O Estacionamento de Chamada é um recurso de gerenciamento de chamada instalado por padrão ao implantar o Enterprise Voice. Este tópico descreve o que você precisa ter antes de poder configurar o Estacionamento de Chamada e os direitos de usuário que você precisará para realizar tarefas de configuração.

> [!IMPORTANT]  
> Arquivos de música em espera personalizada para o Aplicativo de Estacionamento de Chamada não são armazenados como parte do processo de recuperação de desastres do Lync Server 2013 e os arquivos serão perdidos se forem carregados para o pool danificado, corrompido ou apagado. Sempre mantenha uma cópia reserva separada dos arquivos de música em espera personalizada que você carregou para o Estacionamento de Chamada.

Esta seção assume que você leu a documentação de planejamento relacionada ao Estacionamento de Chamada (consulte [Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)).

## Estacionamento de Chamada Pré-requisitos de configuração

Estacionamento de Chamada requer os seguintes componentes:

  - Serviço de aplicativos

  - Aplicativo de Estacionamento de Chamada

Estes componentes são instalados automaticamente ao implantar o Enterprise Voice.

Se você deseja que os chamadores ouçam música enquanto a chamada estiver estacionada, um arquivo de música em espera também é necessário. Um arquivo de música em espera padrão é instalado automaticamente ao implantar o Enterprise Voice. É possível substituir o arquivo padrão com seu próprio arquivo de música em espera. O Estacionamento de Chamada usa o Repositório de Arquivos para manter o arquivo de áudio.

## Direitos do Usuário de Configuração do Estacionamento de Chamada

Você pode utilizar as seguintes ferramentas administrativas para configurar o Estacionamento de Chamada:

  - Painel de Controle do Lync Server

  - Shell de Gerenciamento do Lync Server

É possível usar estas ferramentas para configurar a tabela de órbita do Estacionamento de Chamada e definir outras configurações usadas pelo Estacionamento de Chamada.

Configurar o Estacionamento de Chamada exige qualquer uma das seguintes funções administrativas, dependendo da tarefa:

  - **CsVoiceAdministrator :** Esta função de administrador pode criar, configurar e gerenciar todas as políticas e configurações relacionadas à voz.

  - **CsUserAdministrator :** Esta função de administração pode habilitar o Estacionamento de Chamada na política de voz. Esta função de administração também pode ter acesso de exibição somente leitura para todas as configurações de voz.

  - **CsServerAdministrator :** Esta função de administrador pode gerenciar, monitorar e solucionar problemas de servidores e serviços.

  - **CsAdministrator :** Esta função de administrador pode executar todas as tarefas do CsVoiceAdministrator, CsServerAdministrator e CsUserAdministrator.

> [!NOTE]  
> Para obter detalhes sobre direitos administrativos, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de planejamento.

## Consulte Também

#### Conceitos

[Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)  

#### Outros Recursos

[Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)

