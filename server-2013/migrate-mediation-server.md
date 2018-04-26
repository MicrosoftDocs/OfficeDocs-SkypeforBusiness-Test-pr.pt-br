---
title: Migrar o Servidor de Mediação
TOCTitle: Migrar o Servidor de Mediação
ms:assetid: b0b77121-2c8f-413e-b276-dbf1038361d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205173(v=OCS.15)
ms:contentKeyID: 49307812
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar o Servidor de Mediação

 

_**Tópico modificado em:** 2012-09-28_

O seu Servidor de mediação é mesclado a sua topologia piloto do Lync Server 2013 ao executar o assistente de Mesclagem. No entanto, é possível configurar o Servidor de mediação do Lync Server 2013 depois que todos os usuários são migrados, pois um pool do Office Communications Server 2007 R2 não pode ser comunicar com um Servidor de mediação do Lync Server 2013. Durante a migração lado a lado, o pool do Lync Server 2013 se comunica com o Servidor de mediação do Office Communications Server 2007 R2.

Ao configurar o seu Servidor de mediação do Lync Server 2013, você também deve atualizar ou substituir seus gateways do Office Communications Server 2007 R2. Os gateways do Office Communications Server 2007 R2 não oferecem suporte ao Servidor de mediação do Lync Server 2013. É necessário implantar gateways certificados para Lync Server 2013 e associá-los ao Servidor de mediação do Lync Server 2013. Esta etapa é necessária antes de você encerrar totalmente sua implantação do Office Communications Server 2007 R2.

Os tópicos nesta seção descrevem as tarefas de configuração que você precisa executar depois de concluir a migração do Servidor de mediação do Lync Server 2013. A transição do Servidor de mediação colocado para um Servidor de mediação independente é uma tarefa opcional.

  - [Configurar o Servidor de Mediação](configure-mediation-server.md)

  - [Alterar rotas de voz para usar o novo Servidor de Mediação do Lync Server 2013](change-voice-routes-to-use-the-new-lync-server-2013-mediation-server.md)

  - [Transição de um Servidor de Mediação colocado em conjunto com um Servidor de Mediação autônomo (opcional)](transition-a-collocated-mediation-server-to-a-stand-alone-mediation-server-optional.md)

