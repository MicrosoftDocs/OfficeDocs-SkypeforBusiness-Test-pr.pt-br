---
title: Permitir Federação com Todos os Domínios
TOCTitle: Permitir Federação com Todos os Domínios
ms:assetid: d26f1057-a76c-447a-9efe-72efdce4c15e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362855(v=OCS.15)
ms:contentKeyID: 56270475
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Permitir Federação com Todos os Domínios

 

_**Tópico modificado em:** 2015-06-22_

Se quiser que seus usuários consigam se comunicar com usuários de outro domínio siga estas duas etapas. Primeiro, use o cmdlet [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md) para criar uma instância do objeto AllowAllKnownDomains:

    $x = New-CsEdgeAllowAllKnownDomains

Depois, contacte o cmdlet [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) e ajuste os valores de propriedades do AllowedDomains para a variável (neste exemplo, $x) que contenham o objeto AllowAllKnownDomains:

    Set-CsTenantFederationConfiguration -AllowedDomains $x

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

