---
title: Exibir os domínios em sua lista de domínios permitidos
TOCTitle: Exibir os domínios em sua lista de domínios permitidos
ms:assetid: 13bceaba-5c4f-431f-864f-9e374cafa986
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362772(v=OCS.15)
ms:contentKeyID: 56270372
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir os domínios em sua lista de domínios permitidos

 

_**Tópico modificado em:** 2015-06-22_

Para exibir todos os domínios em sua lista de domínios permitidos, use [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) e a seguinte sintaxe:

    Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty AllowedDomains | Select-Object AllowedDomain

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

