---
title: 'Lync Server 2013: Visão geral dos cenários de criação do fluxo de trabalho'
TOCTitle: Visão geral dos cenários de criação do fluxo de trabalho
ms:assetid: 05e0c175-0f1a-4bb1-b048-c68584d00649
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204646(v=OCS.15)
ms:contentKeyID: 49305741
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral dos cenários de criação do fluxo de trabalho no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-17_

Ao criar um fluxo de trabalho, há duas possibilidades de cenário:

  - **O Administrador cria e configura o fluxo de trabalho** — O membro da função CsResponseGroupAdministrator (ou equivalente) cria e ativa o fluxo de trabalho e todos os elementos no fluxo de trabalho, tais como os grupos de agente, filas, férias e horário comercial, música de espera, etc.

  - **O Administrador cria o fluxo de trabalho e o Gerente configura as opções** — O membro da função CsResponseGroupAdministrator (ou equivalente) define o o URI do SIP principal, Nome de exibição, atribui um membro ou membros da função CsResponseGroupManager e seleciona uma fila e ativa o fluxo de trabalho. O CsResponseGroupManager pode então fazer logon e editar a configuração do fluxo de trabalho criando grupos de agente e também atribui o grupo à fila, configurando o número de telefone, férias e horário comercial, música de espera, etc.
    
    > [!NOTE]  
    > Quando quiser criar um fluxo de trabalho gerenciado, é necessário criar o fluxo como ativo. Após salvar um fluxo gerenciado e ativo, é possível modificar e desativar o fluxo de trabalho.
