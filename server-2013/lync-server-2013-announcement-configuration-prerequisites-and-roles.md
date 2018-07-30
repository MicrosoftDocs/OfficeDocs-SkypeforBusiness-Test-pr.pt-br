---
title: 'Lync Server 2013: Pré-requisitos e funções de configuração de Comunicado'
TOCTitle: Pré-requisitos e funções de configuração de Comunicado
ms:assetid: 82f2dfe9-4c5e-4d65-96a1-96495d506ea4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398658(v=OCS.15)
ms:contentKeyID: 49307300
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos e funções de configuração de Comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-25_

O anúncio é um recurso de gerenciamento de chamadas do Enterprise Voice. Este tópico descreve as implementações necessárias antes de configurar o Anúncio e as atribuições de função necessárias para executar as tarefas de configuração.

Esta seção pressupõe que você leu a documentação de planejamento relacionada ao Comunicado (consulte [Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)).

## Pré-requisitos de Configuração do Comunicado

O Aplicativo Comunicado requer os seguintes componentes:

  - Serviço de aplicativos

  - Aplicativo Grupo de Resposta

  - Repositório de Arquivos (para armazenar arquivos de áudio)

Todos estes componentes são instalados por padrão ao implantar o Enterprise Voice.

## Funções da configuração do Comunicado

Você pode usar as seguintes ferramentas administrativas para configurar os Comunicados:

  - Painel de Controle do Lync Server

  - Shell de Gerenciamento do Lync Server

Configurar o Aplicativo Comunicado requer uma das seguintes funções administrativas:

  - **CsVoiceAdministrator** Esta função de administrador pode criar, configurar e gerenciar todas as configurações de voz e políticas, incluindo todas as configurações do Comunicado.

  - **CsServerAdministrator** Este administrador pode gerenciar, monitorar, solucionar problemas de servidores e serviços e definir todas as configurações do Comunicado.

  - **CsAdministrator** Esta função de administrador pode realizar todas as tarefas administrativas e modificar todas as configurações.

  - **CsViewOnlyAdministrator** Esta função de administrador pode exibir a implantação para monitorar a sua integridade.

> [!NOTE]  
> Para obter detalhes sobre os direitos administrativos, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento.

## Consulte Também

#### Conceitos

[Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)  

#### Outros Recursos

[Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)

