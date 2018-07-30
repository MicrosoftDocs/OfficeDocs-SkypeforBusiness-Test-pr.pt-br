---
title: 'Lync Server 2013: Incluindo o suporte de segurança'
TOCTitle: Incluindo o suporte de segurança
ms:assetid: 4b1d9125-7488-419b-85dd-a8dd3ab5add3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398299(v=OCS.15)
ms:contentKeyID: 49306631
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Incluindo o suporte de segurança no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-02_

Sua empresa pode exigir que a central de segurança se envolva em uma chamada de emergência. Para ajudar a decidir como integrar a Central de Segurança à sua implantação do E9-1-1, você deve responder às perguntas a seguir.

  - **Você deseja que o suporte de segurança seja notificado quando houver uma chamada de emergência?**  
    Você pode configurar a política de local para que o Lync Server envie alertas de mensagem instantânea para os endereços SIP do Lync de uma ou mais equipe de segurança. Esses alertas contêm o nome, o número e o local da pessoa que está fazendo a chamada de emergência e facilitam a segurança na assistência com a situação de emergência.

<!-- end list -->

  - **Deseja estabelecer conferência com o suporte de segurança em cada chamada de emergência?**  
    Se tiver suporte do provedor de serviços de emergência, você poderá configurar a política de local para incluir um número de retorno de chamada com cada chamada de emergência. Esse número é usado pelo provedor para estabelecer conferência com a equipe de segurança da sua organização em chamadas de emergência. Essa conferência pode ser configurada na política de local para ser unidirecional (somente escuta) ou bidirecional.

> [!NOTE]  
> Se desejar, você pode configurar uma equipe de segurança diferente para cada política de local. Isso permite personalizar a resposta para áreas diferentes da empresa ou criar um comportamento diferente para chamadas de emergência que originam da parte interna em oposição à parte externa da rede. Você pode usar grupos de distribuição para especificar o pessoal que você deseja notificar.
