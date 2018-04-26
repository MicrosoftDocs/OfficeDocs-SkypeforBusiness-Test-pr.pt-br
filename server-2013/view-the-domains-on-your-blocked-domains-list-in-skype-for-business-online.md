---
title: Visualizar os Domínios em sua Lista de Domínios Bloqueados
TOCTitle: Visualizar os Domínios em sua Lista de Domínios Bloqueados
ms:assetid: 67c65dbf-1a68-4c77-aabd-bed5001b4267
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362797(v=OCS.15)
ms:contentKeyID: 56270417
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizar os Domínios em sua Lista de Domínios Bloqueados

 

_**Tópico modificado em:** 2015-06-22_

Para visualizar todos os domínios na sua lista de domínios bloqueados, ligue o cmdlet[Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) cmdlet, e redirecione os dados devolvidos para o cmdlet**Select-Object**:

    Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty BlockedDomains

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

