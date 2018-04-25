---
title: 'Lync Server 2013: Visão geral do aplicativo de Comunicado'
TOCTitle: Visão geral do aplicativo de Comunicado
ms:assetid: 2abee804-2599-48bb-90b2-15df0bae5e20
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204757(v=OCS.15)
ms:contentKeyID: 49306225
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do aplicativo de Comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-13_

Ao implantar o Aplicativo Comunicado, você precisa configurar uma tabela de número não atribuído que determina a ação a ser realizada quando alguém discar um número não atribuído. A tabela de número não atribuído contém intervalos de número de telefone válidos para a organização e especifica qual Aplicativo Comunicado lida com cada intervalo. Quando um chamador disca um número válido para sua organização, mas não atribuído a ninguém, o Lync Server pesquisa o número na tabela de roteamento de número não atribuído, identifica qual intervalo o número está e direciona a chamada para o Aplicativo Comunicado especificado para esse intervalo. O Aplicativo Comunicado atende a chamada e reproduz uma mensagem de áudio (se configurado) e desconecta a chamada ou transfere-a para um destino predeterminado, como para um operador. É possível usar cmdlets do Shell de Gerenciamento do Lync Server para configurar várias mensagens de áudio ou para transferir destinos.

Como você configura a tabela de número não atribuído depende de como você deseja usá-la. Se você possui números específicos que não estão mais em uso e deseja reproduzir mensagens que são personalizadas para cada número, é possível inserir estes números específicos na tabela de número não atribuído. Por exemplo, se você alterou o número do seu atendimento ao cliente, é possível inserir o número do serviço antigo e associá-lo com um anúncio que oferece o novo número. Se você deseja reproduzir uma mensagem geral para qualquer pessoa que ligar para um número não atribuído, como funcionários que deixaram a organização, é possível inserir intervalos para todas as extensões válidas em sua organização. A tabela de número não atribuído é invocada sempre que um ligador chama um número que não está atribuído atualmente.

No Lync Server 2013, o Aplicativo Comunicado é instalado automaticamente com o Aplicativo Grupo de Resposta. Os aplicativos Anúncio e Grupo de Resposta são componentes padrões de uma implantação do Enterprise Voice: Quando implantar o Enterprise Voice, ambos estes aplicativos são implantados automaticamente.

