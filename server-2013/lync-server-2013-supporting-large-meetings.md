---
title: Suporte a Reuniões Grandes usando Lync Server 2013
TOCTitle: Suporte a Reuniões Grandes usando Lync Server 2013
ms:assetid: 509a424f-a33d-4e72-8f87-a3ec7bb1ddeb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204894(v=OCS.15)
ms:contentKeyID: 49306696
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a Reuniões Grandes usando Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

Reuniões grandes não seguem o modelo de teste descrito na seção anterior, pois elas possuem as seguintes características:

  - O formato da reunião é uma apresentação de um-para-muitos.

  - Um ou alguns usuários são representados e todos eles participam somente como participantes.

  - O compartilhamento de apresentação do PowerPoint é a principal atividade de colaboração de dados.

  - O áudio é exigido e o vídeo também pode ser utilizado.

  - Uma pessoa dedicada, geralmente, o organizador da reunião ou um assistente do organizador, define a reunião com antecedência.

  - Uma equipe dedicada (não os apresentadores) conduz a reunião, incluindo estabelecer uma conexão para uma reunião online, verificar se o áudio, vídeo e compartilhamento de slides estão funcionando, gerenciar lobby e funções dos usuários, ligar e desligar o microfone dos participantes, responder perguntas e gerenciar gravações, conforme apropriado.

Fornecer suporte a reuniões grandes com até 1.000 usuários requer correção de problemas relacionados ao modelo de hardware compartilhado e ao modelo sem reserva.

Para ter recursos de CPU e memória suficientes para as reuniões com até 1.000 usuários, o Servidores Front-End hospedado não deve hospedar quaisquer outras mensagens instantâneas (IM) e presença ou cargas de trabalho do Enterprise Voice. Também não deve hospedar quaisquer outras reuniões, independente do tamanho das outras reuniões. Isso significa que as reuniões hospedadas com até 1.000 usuários requerem a configuração do pool do Lync Server separada que seja dedicada ás reuniões grandes hospedadas com até 1.000 usuários.

Um pool do Lync Server que é dedicado às reuniões grandes hospedadas deve hospedar uma ou somente uma reunião com até 1.000 usuários ao mesmo tempo, dessa forma, os horários das reuniões precisam ser reservados com antecedência por meio de um processo de agendamento fora da banda para garantir o suporte dedicado do Servidores Front-End. Para suportar mais de uma reunião grande ao mesmo tempo, recomendamos a configuração de vários pool de reuniões grandes dedicados.

Recomendamos que uma pessoa dedicada conduza e monitore uma parte de uma grande reunião online. Essa pessoa deve ser o organizador, delegado do organizador ou apresentador, ou um membro da equipe de suporte à reunião grande dedicada, dependendo das preferências da organização.

Nas seções a seguir, descreveremos como implementar um pool dedicado para reuniões grandes, incluindo as práticas recomendadas para utilizar o Lync Server 2013 para suportar cenários de reuniões grandes.

## Nesta seção

  - [Configurar suporte para grandes reuniões](lync-server-2013-setting-up-support-for-large-meetings.md)

  - [Gerenciamento grandes reuniões](lync-server-2013-managing-large-meetings.md)

