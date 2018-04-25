---
title: Falha de logon para o usuário
TOCTitle: Falha de logon para o usuário
ms:assetid: 006020cd-34d0-4a78-b5b4-e382d95ef04d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn329053(v=OCS.15)
ms:contentKeyID: 56270357
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Falha de logon para o usuário

 

_**Tópico modificado em:** 2015-06-22_

Quando você tentar fazer uma conexão remota ao Skype for Business Online, deverá fornecer o nome de usuário e a senha de uma conta de usuário do Skype for Business Online válida. Caso você não faça isso, o logon falhará junto com uma mensagem de erro semelhante a esta:

    Get-CsWebTicket : Início de sessão falhou para o usuário 'davibarros@litwareinc.com'. Crie um novo objeto PSCredential, assegurando-se de que tem o nome se usuário e a senha corretas.

Se você acha que está usando uma conta de usuário válida e que tem a senha correta, tente fazer logon novamente. Se isso falhar, use as mesmas credenciais e tente fazer logon em <https://login.microsoftonline.com/>. Se você não conseguir fazer logon ali, entre em contato com o Suporte do Office 365.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

