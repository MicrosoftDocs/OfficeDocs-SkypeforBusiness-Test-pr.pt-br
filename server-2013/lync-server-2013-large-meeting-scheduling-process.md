---
title: Processo de agendamento de reunião grande
TOCTitle: Processo de agendamento de reunião grande
ms:assetid: de267458-885f-4176-a8d7-1a218e67640e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205334(v=OCS.15)
ms:contentKeyID: 49308330
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de agendamento de reunião grande

 

_**Tópico modificado em:** 2012-10-22_

Como apenas uma reunião grande por vez é suportada em um pool de reunião grande exclusivo, recomendamos implementar um grande processo de programação da reunião para ajudar a evitar conflitos de grande reunião. O objetivo desse processo de programação é facilitar a configuração de grandes reuniões. Tal capacidade não é oferecida diretamente pelos clientes do Lync Server ou Lync Server. Uma forma de implementar tal processo é usar o sistema de ticket da equipe de suporte da sua organização, se disponível.

Para organizadores de grandes reuniões, programar uma grande reunião envolve concluir as seguintes etapas:

1.  O organizador da reunião ou representante determina a hora, a duração e o tamanho da uma próxima reunião, além da lista de apresentadores. Se o tamanho da reunião antecipado excede 250 usuários ou para garantir a melhor experiência do usuário para uma reunião com menos de 250 usuários, o organizador ou representante envia uma solicitação para uma grande reunião.

2.  A equipe de programação verifica para ver se a data e hora solicitada está disponível. Como suportamos apenas uma única grande reunião em um pool exclusivo por vez, a equipe de programação precisa verificar o calendário de grandes reuniões para determinar se há outra reunião programada para a data e hora solicitada. Se a hora da reunião está disponível, a equipe aprova a solicitação da reunião.

3.  Se a solicitação é aprovada, a equipe de programação (usando credenciais em um pool exclusivo) usa o Suplemento de Reunião Online para Lync 2013 com o Outlook para definir uma reunião em um pool de reunião grande exclusivo. A URL a ser usada para participar a reunião é oferecida ao solicitador como parte do aviso de aprovação.

4.  O organizador da reunião ou representante usa o Outlook para programar a próxima reunião, adicionando a URL para participar da reunião ao convite. O organizador da reunião ou representante especifica os usuários a serem convidados e envia o convite.
    
    A figura a seguir mostra uma solicitação comum e fluxo de trabalho de aprovação para programar grandes reuniões.
    
    ![Fluxo de trabalho de agenda da conferência](images/JJ205334.5d8b1f62-1dc3-47bf-bf8f-be2d8899ab9d(OCS.15).jpg "Fluxo de trabalho de agenda da conferência")

