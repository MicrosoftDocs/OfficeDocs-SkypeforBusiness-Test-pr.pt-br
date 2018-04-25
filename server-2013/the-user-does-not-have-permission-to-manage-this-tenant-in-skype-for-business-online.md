---
title: O Usuário Não Tem Permissão para Gerenciar esse Locatário
TOCTitle: O Usuário Não Tem Permissão para Gerenciar esse Locatário
ms:assetid: 714ccf81-9451-4585-b62d-979f2a606315
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362812(v=OCS.15)
ms:contentKeyID: 56270428
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# O Usuário Não Tem Permissão para Gerenciar esse Locatário

 

_**Tópico modificado em:** 2015-06-22_

Você não pode fazer uma conexão Windows PowerShell remota para Skype for Business Online a menos que você seja um mebro do grupo dos Administradores de Locatário. Se você não for, sua tentativa de conexão falhará, e você receberá a seguinte mensagem de erro:

    New-PSSession : [admin.vdomain.com] Falha ao processar dados do servidor remoto admin.vdomain.com com a seguinte mensagem de erro: O usuário 'usuario@foo.com' não tem permissão para gerenciar este locatário. Podem ser concedidas permissões atribuindo ao usuário a função RBAC apropriada. Para mais informações, consulte o t+opico Ajuda about_Remote_Troubleshooting Help topic.

Se você acha que você é, ou deveria ser, um membro do grupo de Administradores de Locatário, você precisa entrar em contato com o SuporteOffice 365.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

