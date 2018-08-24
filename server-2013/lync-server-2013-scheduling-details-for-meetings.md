---
title: Detalhes de agendamentos
TOCTitle: Detalhes de agendamentos
ms:assetid: 39ca6fff-2c15-4347-9f1f-6c8687a39a49
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204823(v=OCS.15)
ms:contentKeyID: 49306436
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Detalhes de agendamentos

 

_**Tópico modificado em:** 2012-10-04_

Depois de fazer uma verificação para assegurar que nenhuma outra reunião esteja agendada na hora solicitada, a equipe de suporte a grandes reuniões, que lida com a solicitação, agenda a reunião no pool de grandes reuniões. Use o Suplemento Reunião Online para Outlook que é instalado com o cliente do Lync Server 2013 para realizar essa tarefa, usando as credenciais de um usuário habilitado para o Lync Server no pool de grandes reuniões dedicado.

Para assegurar a melhor experiência do usuário, é importante agendar a grande reunião com os níveis de acesso corretos e as configurações da reunião que são apropriadas para as necessidades do organizador da reunião. É recomendável seguir as configurações de agendamento definidas nas opções de reunião do Lync:

  - Use um novo espaço de reunião para cada grande reunião em vez de reutilizar o espaço dedicado da reunião.

  - Especifique os níveis de acesso à reunião conforme segue:
    
      - Se pelo menos um convidado for de fora da organização, defina o tipo de reunião como **Para qualquer pessoa (sem restrição)**. Isso permite que você evite ter que gerenciar um possível grande saguão quando a reunião estiver em andamento.
    
      - Se a reunião for somente interna, defina o tipo de acesso à reunião como **Para qualquer pessoa de minha organização**.
        
        > [!NOTE]  
        > Evite definir o tipo de acesso à reunião como <strong>Pessoas que eu convidar da minha empresa</strong>, pois quando essa configuração é usada, os organizadores devem adicionar os endereços de email de todos os usuários à lista de convidados e você não pode convidar um grupo de distribuição.<br />        Evite definir o tipo de acesso à reunião como <strong>Apenas eu, o organizador da reunião</strong>, pois esta configuração exige que todos os participantes da reunião, inclusive apresentadores, sejam colocados no saguão no tempo de execução da reunião. A pessoa responsável pela execução da grande reunião deverá monitorar a escalação do saguão e aceitar os novos usuários que estão no saguão.

  - Permita que usuários ligando de telefones entrem na reunião automaticamente marcando a configuração **Chamadores entram diretamente**.

  - Convide explicitamente os seguintes usuários:
    
      - Organizador e representante da reunião (solicitante)
    
      - A lista de apresentadores fornecida pelo solicitante da reunião
    
    > [!NOTE]  
    > Se o tipo de acesso à reunião estiver definido como <strong>Pessoas que eu escolher</strong>, será preciso adicionar explicitamente cada participante da grande reunião como convidado da reunião.

  - Gerencie explicitamente os apresentadores, em vez de definir a opção de apresentador como um dos valores promovidos automaticamente. Certifique-se de adicionar os seguintes usuários como apresentadores:
    
      - Organizador e representante da reunião (solicitante)
    
      - A lista de apresentadores fornecida pelo solicitantes da grande reunião
    
    > [!NOTE]  
    > Ao gerenciar explicitamente os apresentadores, é possível controlar o número de apresentadores para que você possa limitá-los a um número pequeno o suficiente para que seja possível conduzir uma grande reunião eficiente. Se a maioria dos participantes da reunião tiverem a função de participante, isso ajudará a reduzir as chances de alguém acidentalmente assumir o controle da apresentação, excluindo a apresentação do PowerPoint, ativando/desativando o áudio dos apresentadores e outras interrupções na reunião.

  - Marque a configuração **Desativar o áudio de todos os participantes** para assegurar que apenas os apresentadores possam transmitir áudio para a reunião.

  - Marque a configuração **Bloquear vídeo dos participantes** para assegurar que apenas os apresentadores possam transmitir vídeo para a reunião.

A figura a seguir mostra as configurações recomendadas para o Suplemento Reunião Online para Outlook.

![Opções de reunião de conferência](images/JJ204823.54e4e70d-06b0-45cd-8d94-bab649cd5dc0(OCS.15).jpg "Opções de reunião de conferência")

