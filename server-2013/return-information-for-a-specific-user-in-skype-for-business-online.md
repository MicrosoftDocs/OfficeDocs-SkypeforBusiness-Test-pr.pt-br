---
title: Devolver Informações para um Usuário Específico
TOCTitle: Devolver Informações para um Usuário Específico
ms:assetid: 6c8c2190-8e62-4f92-bbe9-4f692bd7ebf5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362803(v=OCS.15)
ms:contentKeyID: 56270425
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Devolver Informações para um Usuário Específico

 

_**Tópico modificado em:** 2015-06-22_

Há várias maneiras de referenciar uma conta de usuário específica quando ligar para [Get-CsOnlineUser](get-csonlineuser.md) cmdlet. Você oide usar o nome exibido dos Serviços de Domínio do Active Directory:

    Get-CsOnlineUser -Identity "Ken Myer"

Você pode usar o endereço SIP do usuário:

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

Você pode usar o nome principal de usuário (UPN) do usuário:

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

