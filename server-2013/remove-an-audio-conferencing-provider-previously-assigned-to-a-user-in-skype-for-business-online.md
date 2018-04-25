---
title: Remover um provedor de audioconferência atribuído anteriormente a um usuário
TOCTitle: Remover um provedor de audioconferência atribuído anteriormente a um usuário
ms:assetid: 85d59e6c-d646-4908-9767-adb48763f6de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362808(v=OCS.15)
ms:contentKeyID: 56270441
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover um provedor de audioconferência atribuído anteriormente a um usuário

 

_**Tópico modificado em:** 2015-06-22_

Para remover todos os provedores de audioconferência atribuídos a um usuário, execute o cmdlet [Remove-CsUserAcp](remove-csuseracp.md) sem nenhum parâmetro (além do parâmetro Identity, que indica o usuário em questão):

    Remove-CsUserAcp -Identity "Ken Myer"

Se vários provedores de audioconferência tiverem sido atribuídos a um usuário, você poderá remover um único provedor incluindo o parâmetro Name, seguido do nome do provedor a ser removido:

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Contoso ACP"

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

