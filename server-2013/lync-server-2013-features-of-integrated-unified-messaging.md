---
title: 'Lync Server 2013: Recursos de Unificação de Mensagens integrada'
TOCTitle: Recursos de Unificação de Mensagens integrada e do Lync Server
ms:assetid: 094f549d-fccc-43ab-9f39-6ddd18130915
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398144(v=OCS.15)
ms:contentKeyID: 49305818
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos de Unificação de Mensagens integrada e do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013, Enterprise Voice utiliza a Unificação de Mensagens (UM) do Exchange infraestrutura do fea-ent-voice para fornecer atendimento de chamadas, notificação de chamadas, acesso de voz (incluindo caixa postal) e serviços de atendedor automático.

## Atendimento de chamadas

O atendimento de chamadas é o recebimento das mensagens de voz em favor dos usuários cujas ligações não são atendidas ou estão ocupados. Ele inclui uma saudação pessoal, a gravação de uma mensagem e seu envio ao Transporte de Hub do Exchange Server para ficar na fila de entrega à caixa de correio do usuário, que está armazenada no servidor de caixa de correio do Exchange.

Se o chamador deixar uma mensagem, está é roteada até a Caixa de entrada do usuário. Se o chamador optar por não deixar uma mensagem, uma notificação de chamada perdida será armazenada na caixa de correio do usuário. Os usuários podem, então, acessar sua Caixa de entrada usando o cliente de mensagem e de colaboração do Microsoft Outlook, o Outlook Web Access, a tecnologia Exchange ActiveSync ou o Outlook Voice Access. O assunto e a prioridade das chamadas podem ser exibidos de uma maneira muito semelhante àquela do e-mail.

## Outlook Voice Access

O Outlook Voice Access habilita o acesso de um usuário Enterprise Voice o Enterprise Voice não apenas ao correio de voz, mas também à caixa de entrada do Exchange, incluindo e-mail, calendário e contatos de uma interface de telefonia. O número de acesso do assinante é designado por um administrador do UM do Exchange.

## Atendedor automático

O atendedor automático é um recurso do UM do Exchange que pode ser usado para configurar um número de telefone o qual usuário de fora pode discar para contatar representantes da empresa. Especificamente, ele fornece uma série de avisos de voz que auxiliam um chamador externo a navegar por um sistema de menus. A lista de opções disponíveis é configurada no servidor do UM do Exchange pelo administrador do UM do Exchange.

## Serviços de fax

UM do Exchange inclui recursos de fax, que permitem aos usuários receber fax de entrada em suas Caixas de Correio do Exchange. Para obter detalhes, consulte "Unificação de Mensagens" na documentação do Microsoft Exchange Server em [http://go.microsoft.com/fwlink/p/?linkId=135652](http://go.microsoft.com/fwlink/p/?linkid=135652).

> [!NOTE]  
> Os serviços de fax fornecidos pelo servidor UM do Exchange não estão disponíveis em implantações do Lync Server integradas ao Microsoft Exchange Server 2010, Exchange 2010 com o pacote de serviços mais recente, ou Exchange 2013.
