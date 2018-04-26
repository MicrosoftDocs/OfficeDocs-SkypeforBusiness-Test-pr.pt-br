---
title: Migrar reuniões e conteúdo de reuniões existentes
TOCTitle: Migrar reuniões e conteúdo de reuniões existentes
ms:assetid: 30516731-2ae1-4a6d-a7e1-d3f05778c954
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688011(v=OCS.15)
ms:contentKeyID: 49886158
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar reuniões e conteúdo de reuniões existentes

 

_**Tópico modificado em:** 2013-02-22_

Quando uma conta do usuário é movida do Lync Server 2010 para um servidor do Lync Server 2013, a seguinte informação é movida com essa conta do usuário:

  - **As reuniões já foram programadas pelo usuário**. Isto inclui mover os diretórios de conferência e dados de conferência.

  - **Número de identificação pessoal (PIN) do usuário**. O PIN atual do usuário continua a funcionar até vencer ou o usuário solicitar um novo PIN.

A seguinte informação de conta do usuário não é movida para o novo servidor.

  - **Conteúdo da reunião**. Para poder mover o conteúdo compartilhado durante uma reunião, por exemplo, PowerPoint, Quadro de Avisos, anexos ou dados do pool, use o parâmetro **-MoveConferenceData** como parte do cmdlet **Move-CsUser**.

