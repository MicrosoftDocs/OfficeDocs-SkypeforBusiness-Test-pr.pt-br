---
title: Componentes usados pelo recebimento de chamadas em grupo
TOCTitle: Componentes usados pelo recebimento de chamadas em grupo
ms:assetid: 45db2f23-d486-4b20-a8cf-7b48a1f9fd3a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945625(v=OCS.15)
ms:contentKeyID: 52057611
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes usados pelo recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2013-01-30_

Atendimento de chamadas em grupo é implantado automaticamente quando você implanta o Enterprise Voice e o Aplicativo de Estacionamento de Chamada. Você habilita o atendimento de chamadas em grupo configurando a tabela de órbita Estacionamento de Chamada com intervalos de números separados denominados números de grupo de atendimento de chamadas, atribuindo em seguida usuários a grupos de atendimento de chamadas e habilitando os usuários para o atendimento de chamadas em grupo. Os componentes Lync Server a seguir suportam atendimento de chamadas em grupo:

  - **Serviço de aplicativos**   O Serviço de aplicativos fornece uma plataforma para implantação, hospedagem e gerenciamento de aplicativos de comunicações unificadas, como o Aplicativo de Estacionamento de Chamada. O Serviço de aplicativos é automaticamente instalado em cada servidor front-end em um Pool de Front-Ends e em cada servidor Standard Edition.

  - **Aplicativo de Estacionamento de Chamada**   O Aplicativo de Estacionamento de Chamada é um dos aplicativos de comunicação unificada hospedados pelo Serviço de aplicativos. O atendimento de chamadas em grupo é baseado no Aplicativo de Estacionamento de Chamada.

  - **Shell de Gerenciamento do Lync Server**   Você utiliza o Shell de Gerenciamento do Lync Server para gerenciar o atendimento de chamadas em grupo.

  - **Instrumento do kit de ferramentas SEFAUtil**   Você usa o utilitário de ativação de recurso de extensão secundária (SEFAUtil) para atribuir usuários a um grupo de atendimento de chamadas e para habilitar ou desabilitar o atendimento de chamadas para os usuários.

