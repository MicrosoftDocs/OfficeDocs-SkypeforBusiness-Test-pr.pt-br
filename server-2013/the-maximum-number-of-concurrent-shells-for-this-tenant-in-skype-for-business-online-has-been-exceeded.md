---
title: O número máximo de shells simultâneos para este inquilino excedeu
TOCTitle: O número máximo de shells simultâneos para este inquilino excedeu
ms:assetid: a4c91ffa-fdcc-414c-b941-a0d36c906825
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362832(v=OCS.15)
ms:contentKeyID: 56270456
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# O número máximo de shells simultâneos para este inquilino excedeu

 

_**Tópico modificado em:** 2015-06-22_

Embora cada administrador possa ter até três conexões simultâneas a um inquilino Skype for Business Online, nenhum inquilino pode ter mais de nove conexões simultâneas. Por exemplo, três administradores podem ter, cada um, três sessões abertas. Se um quarto administrador tentar fazer uma conexão (resultando em um total de 10 conexões simultâneas), essa tentativa falha com a seguinte mensagem de erro:

    New-PSSession : [admin.vdomain.com] Falha na conexão ao servidor remoto admin.vdomain.com com a seguinte mensagem de erro: O serviço WS-Management não pode processar a solicitação. O número máximo de shells simultâneos para esse locatário foi excedido. Feche shells existentes ou aumente a cota para esse locatário. para mais informações, consulte o tópico Ajuda about_Remote_Troubleshooting.

A única maneira de resolver este problema é fechar uma ou mais das conexões anteriores. Quando você terminar uma sessão do Skype for Business Online, recomendamos usar o cmdlet **Remove-PSSession** para finalizar a sessão. Isso ajuda a evitar esse problema.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

