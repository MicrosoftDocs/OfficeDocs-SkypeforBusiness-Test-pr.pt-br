---
title: Retornar Informações Específicas para Usuários Específicos
TOCTitle: Retornar Informações Específicas para Usuários Específicos
ms:assetid: bbee85bd-d8a7-4b28-90d7-45c43eee48f6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362838(v=OCS.15)
ms:contentKeyID: 56270465
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retornar Informações Específicas para Usuários Específicos

 

_**Tópico modificado em:** 2015-06-22_

Por padrão, o cmdlet [Get-CsOnlineUser](get-csonlineuser.md) retorna grandes quantidades de informação para cada conta de usuário Skype for Business Online. Se você está interessado em apenas um subconjunto de informações, canalize os dados retornados para o cmdlet **Select-Object**. Por exemplo, esse comando retorna todos os dados para o usuário Ken Myer, e usa o cmdlet **Select-Object** para limitar as informações mostradas na tela para os Serviços de Domínio Active Directory de Ken para exibir o nome e o plano de discagem:

    Get-CsOnlineUser -Identity "Ken Myer" | Select-Object DisplayName, DialPlan

Os comandos a seguir retornam a exibição do nome e do plano de discagem para todos os usuários.

    Get-CsOnlineUser | Select-Object DisplayName, DialPlan

Para encontrar as propriedades de uma conta de usuário Skype for Business Online, use este comando:

    Get-CsOnlineUser | Get-Member

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

