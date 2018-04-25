---
title: Habilitar/desabilitar a federação com provedores públicos de mensagens instantâneas
TOCTitle: Habilitar/desabilitar a federação com provedores públicos de mensagens instantâneas
ms:assetid: 8609682c-97d3-48e6-a243-d84c1f9c8419
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362809(v=OCS.15)
ms:contentKeyID: 56270442
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar/desabilitar a federação com provedores públicos de mensagens instantâneas

 

_**Tópico modificado em:** 2015-06-22_

Para habilitar seus usuários para comunicação com usuários que tenham contas em um provedor público de mensagens instantâneas, use o cmdlet [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) e defina a propriedade AllowPublicUsers property como Verdadeira ($True):

    Set-CsTenantFederationConfiguration -AllowPublicUsers $True

Observe que, então, você deverá usar o cmdlet [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) para especificar os provedores públicos de mensagens instantâneas com os quais seus usuários terão permissão para se comunicar.

Para desabilitar a federação com provedores públicos, defina a propriedade AllowPublicUsers novamente como Falsa ($False):

    Set-CsTenantFederationConfiguration -AllowPublicUsers $False

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

