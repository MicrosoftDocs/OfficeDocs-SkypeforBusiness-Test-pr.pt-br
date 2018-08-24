---
title: Visão Geral de Webconferência no Lync Server 2013
TOCTitle: Visão Geral de Webconferência no Lync Server 2013
ms:assetid: 40616dc4-f705-4890-85bf-79f76a033a9b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425913(v=OCS.15)
ms:contentKeyID: 49306493
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão Geral de Webconferência no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Com a Webconferência, os usuários podem compartilhar e colaborar em documentos, como apresentações do PowerPoint, durante suas conferências. Além disso, os usuários podem compartilhar toda ou parte da área de trabalho com os outros em tempo real, dando a impressão de que todas as pessoas da conferência estão reunidas ao redor da mesma mesa da reunião.

## Quadro de comunicações e anotações

Um quadro de comunicações é uma tela em branco que pode ser usada para colaboração com texto, tinta, desenhos e imagens. As anotações feitas nos quadros de comunicações podem ser vistas por todos os participantes da reunião. O recurso de quadro de comunicações aprimora a colaboração ao permitir que os participantes da reunião discutam ideias, façam brainstorm, anotações e outros.

## Sondagem

O recurso de sondagem aprimora a colaboração ao permitir que os apresentadores determinem rapidamente as preferências dos participantes. Durante reuniões online e conversas, os apresentadores podem utilizar a sondagem para obter respostas anônimas dos participantes. Todos os apresentadores podem ver os resultados e podem escondê-los ou mostrá-los aos presentes.

## Compartilhamento de aplicativo e compartilhamento de Desktop

Durante uma conferência, você pode compartilhar todo o desktop, um aplicativo individual ou monitores individuais em um ambiente de vários monitores. À parte de apenas visualizar o conteúdo, os outros participantes na conferência também podem solicitar controle da sua tela e, com permissão, interagir com o conteúdo (incluindo rolar e editar).

> [!NOTE]  
> Os participantes que estão visualizando a conferência podem assumir o controle e iniciar o compartilhamento de conteúdo durante a reunião.

## Compartilhamento do PowerPoint

Em Lync 2010 PowerPoint, as apresentações eram visualizadas em uma de duas formas. Para usuários executando o Lync 2010, as apresentações do PowerPoint eram exibidas utilizando o formato PowerPoint 97-2003 e eram visualizadas utilizando uma cópia incorporada do visualizador do PowerPoint. Para usuários executando o Lync Web App, as apresentações do PowerPoint eram convertidas para arquivos de HTML dinâmico e, então, visualizados utilizando uma combinação desses arquivos DHTML personalizados e Silverlight. Apesar de normalmente ser eficaz, essa abordagem possuía algumas limitações:

  - O Visualizador do PowerPoint incorporado (que fornecia a melhor experiência de visualização) só está disponível na plataforma Windows.

  - Muitos dispositivos móveis (incluindo alguns dos telefones móveis mais populares) não suportam o Silverlight.

  - A abordagem do Visualizador do PowerPoint e DHTML/Silverlight não suporta todos os recursos (como a transição de slides e vídeo incorporado) que são encontrados nas edições mais recentes do PowerPoint.

Para ajudar a resolver essas questões e melhorar a experiência geral dos usuários apresentando ou visualizando apresentações do PowerPoint, o Lync Server 2013 emprega Office Web Apps e o Servidor Office Web Apps para lidar com as apresentações do PowerPoint. Entre outras vantagens, essa nova abordagem permite:

  - Exibições de alta resolução e melhor suporte para capacidades do PowerPoint, como animações, transições de slides e vídeo incorporado.

  - Dispositivos móveis adicionais para acessar tais apresentações. Isso porque o Lync Server 2013 utiliza DHTML e JavaScript padrão para difundir apresentações do PowerPoint em vez do DHTML personalizado e Silverlight.

  - Usuários com os privilégios adequados para rolar uma apresentação do PowerPoint independente da apresentação propriamente dita. Por exemplo, enquanto Ken Myer está apresentando a apresentação dele, Pilar Ackerman pode olhar qualquer slide que desejar sem afetar a apresentação do Ken.

