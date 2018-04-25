---
title: 'Lync Server 2013: Componentes usados pelo Estacionamento de Chamadas'
TOCTitle: Componentes usados pelo Estacionamento de Chamadas
ms:assetid: c7ffbee3-0ce1-48c0-bb56-af098b41d6d6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398824(v=OCS.15)
ms:contentKeyID: 49308087
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes usados pelo Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-13_

O Aplicativo de Estacionamento de Chamada é automaticamente instalado quando você implanta o Enterprise Voice. Você habilita o Estacionamento de Chamada configurando a política de voz. Os componentes do Lync Server 2013 a seguir oferecem suporte ao Aplicativo de Estacionamento de Chamada:

  - **Serviço de aplicativos**   O Serviço de aplicativos fornece uma plataforma pata implantação, hospedagem e gerenciamento de aplicativos de comunicações unificadas, como o Aplicativo de Estacionamento de Chamada. O Serviço de aplicativos é automaticamente instalado em cada Servidor Front-End em um Pool de Front-Ends e em cada servidor Standard Edition.

  - **Aplicativo de Estacionamento de Chamada**   O Aplicativo de Estacionamento de Chamada é um dos aplicativos de comunicação unificados hospedados pelo Serviço de aplicativos. Ele é incluído automaticamente quando você implantar o Enterprise Voice. O Estacionamento de Chamada estaciona e recupera chamadas e gerencia as órbitas de estacionamento de chamada.

  - **Arquivo de música em espera**   Se a música estiver habilitada, o arquivo de música será reproduzido enquanto uma chamada está estacionada. Um arquivo de música padrão é incluído quando o Aplicativo de Estacionamento de Chamada é instalado.

  - **Repositório de Arquivos**   O Aplicativo de Estacionamento de Chamada usa o Repositório de Arquivos para armazenar arquivos de áudio personalizados.

  - **Painel de Controle do Lync Server**   É possível usar o Painel de Controle do Lync Server para configurar a tabela de órbita de estacionamento de chamada e habilitar o Estacionamento de Chamada para usuários.

  - **Shell de Gerenciamento do Lync Server**   Toda configuração do Aplicativo de Estacionamento de Chamada pode ser executada usando os cmdlets do Shell de Gerenciamento do Lync Server.

