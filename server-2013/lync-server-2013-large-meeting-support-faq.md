---
title: FAQ sobre Suporte do Lync Server 2013 a Grandes Reuniões
TOCTitle: FAQ sobre Suporte do Lync Server 2013 a Grandes Reuniões
ms:assetid: 34b4fb6a-e35c-47e8-8ab1-f8331741fed2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204804(v=OCS.15)
ms:contentKeyID: 49306342
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# FAQ sobre Suporte do Lync Server 2013 a Grandes Reuniões

 

_**Tópico modificado em:** 2012-10-22_

A seção a seguir oferece respostas às perguntas comuns sobre a criação e execução de grandes reuniões.

## P: Quantos usuários podem participar de uma grande reunião?

O modelo de usuário do Lync Server especifica limites de 250 usuários em um pool compartilhado ou 1.000 usuários em um pool dedicado a grandes reuniões, mas esses números representam apenas o número de usuários testados e apenas para o conjunto específico de hardware usado nos testes. Com base nos testes, é recomendável manter esses limites para tamanhos máximos. No entanto, é possível controlar o número real de participantes permitidos em reuniões de sua organização configurando uma ou mais políticas de conferência (que são configuradas usando os cmdlets Windows PowerShell no Shell de Gerenciamento do Lync Server ou usando o Painel de Controle do Lync Server). O número especificado em uma política de conferência pode ser qualquer número inteiro de 32 bits entre 1 e 4.294.967.295, mas o tamanho recomendado está entre 2 e 250 participantes e o valor padrão é 250.

## P: Quantas reuniões ou cargas de trabalho posso ter em um pool dedicado a grandes reuniões?

Para assegurar a melhor experiência do usuário em grandes reuniões de até 1.000 participantes, é recomendável hospedar apenas uma única grande reunião por vez em um pool dedicado a grandes reuniões. É recomendável também não permitir que nenhuma outra carga de trabalho seja executada no pool enquanto a grande reunião estiver em andamento.

## P: Os organizadores de grandes reuniões devem ser hospedados no pool dedicado?

Não. É recomendável não hospedar nenhum usuário além da equipe dedicada que gerencia o agendamento de grandes reuniões no pool dedicado. Isso impede que outras comunicações em tempo real causem problemas com as grandes reuniões hospedadas no pool. Você deve agendar grandes reuniões no pool dedicado usando uma conta de usuário da equipe de agendamento da grande reunião. Você deve adicionar a conta de usuário do organizador da reunião (o usuário que solicita uma grande reunião) como um apresentador da grande reunião.

## P: Quais são as modalidades de mídia que posso usar em uma grande reunião?

As grandes reuniões com até 1.000 usuários podem conter áudio, vídeo, compartilhamento do PowerPoint, quadros de comunicações e sondagem de presença.

## P: Posso usar IM (mensagens instantâneas) em grupo nas grandes reuniões?

Sim. No entanto, grandes números de mensagens instantâneas, especialmente quando enviadas por um grande número de participantes da reunião, podem afetar a experiência do usuário devido a problemas com a rolagem rápida do texto na janela de IM. A entrega de uma grande quantidade de mensagens instantâneas de até 1.000 usuários também pode introduzir cargas significativas do servidor, o que pode afetar o desempenho. Normalmente, IMs são necessárias apenas para Q\&As (perguntas e respostas).

## P: Os usuários podem participar de grandes reuniões ligando de um telefone?

Sim. Se o pool do Lync Server 2013 estiver implantado apropriadamente e habilitado para conferência discada, os usuários poderão participar de grandes reuniões por meio de discagem. Nossos testes mostraram que até 15% dos 1.000 usuários podem participar de uma grande reunião por um período de 10 minutos.

## P: Posso hospedar grandes reuniões em uma topologia virtual?

As grandes reuniões ainda não foram testadas em uma topologia virtual, portanto não há suporte para o uso de máquinas virtuais a fim de hospedar um pool dedicado a grandes reuniões.

