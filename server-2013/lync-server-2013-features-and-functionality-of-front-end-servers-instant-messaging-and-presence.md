---
title: 'Lync Server 2013: Recursos e funcionalidades de servidores front-end, mensagens instantâneas e presença'
TOCTitle: Recursos e funcionalidades de servidores front-end, mensagens instantâneas e presença
ms:assetid: 05b29536-dcd7-49b5-934a-2ebf20ddc45c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398109(v=OCS.15)
ms:contentKeyID: 49305740
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos e funcionalidades de servidores front-end, mensagens instantâneas e presença no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-17_

Servidores Front End fornecem a maioria da funcionalidade do Lync Server. Há duas edições disponíveis: Lync Server Enterprise Edition, que é desenvolvida principalmente para grandes organizações e Lync Server Standard Edition, que desenvolvidamente principalmente para organizações menores que queiram um investimento de hardware menor e não necessitam de alta disponibilidade. Ambas edições suportam todoso os Lync Server fluxos de trabalho incluindo IM, presença, conferência e Enterprise Voice.

A mensagem instantânea (IM) permite que os usuários se comuniquem entre si em tempo real em seus computadores usando mensagens textuais. Tanto as sessões de IM de duas partes como as multipartes são suportadas. Um participante de uma conversa por IM de duas partes pode adicionar um terceiro participante à conversa a qualquer momento. Quando isso acontece, a janela de conversa muda para dar suporte aos recursos de conferência.

> [!IMPORTANT]  
> Os clientes do Lync e do Communicator quando envolvidos em uma comunicação exclusiva, é geralmente referida como de ponto a ponto. Tecnicamente, os dois clientes estão se comunicando em uma conversa exclusiva, com a unidade de controle de multipontos de Mensagens Instantâneas (IMMCU) no meio. O IMMCU é um componente do Servidor Front-End. Colocar o IMMCU no fluxo de trabalho de comunicação necessário permite a gravação de detalhes da chamada e outros recursos que o Servidor Front-End habilita. A comunicação parte de uma porta de fonte dinâmica no cliente para a porta do Servidor Front-End TLS/TCP/5061 (pressupondo o uso da camada de segurança de transporte recomendada). Conforme projetada, a comunicação de ponto a ponto (assim como as IMs de várias partes) só é possível quando o Lync Server e o IMMCU estão ativos e disponíveis.

A *Presença* fornece informações a usuários sobre o status de outros na rede. O status de presença de um usuário fornece informações para ajudar outros usuários a decidir se devem tentar entrar em contato com o usuário e se devem fazê-lo por mensagem instantânea, telefone ou e-mail. A Presença encoraja a comunicação instantânea quando possível, mas também dá informações sobre se um usuário está em reunião ou fora do escritório, indicando que a comunicação instantânea não é possível. O status de presença é exibido como um ícone de presença no Lync e em outros aplicativos com alerta de presença, incluindo o cliente de mensagens e de colaboração do Microsoft Outlook, as tecnologias do Microsoft SharePoint, o Microsoft Word e o software de planilhas do Microsoft Excel. O ícone de presença representa a disponibilidade e a propensão do usuário para se comunicar naquele momento.

