---
title: Falha ao Conectar ao Servidor da ID do Live
TOCTitle: Falha ao Conectar ao Servidor da ID do Live
ms:assetid: 701af721-dd6a-4f48-96f9-94e89c644201
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362811(v=OCS.15)
ms:contentKeyID: 56270427
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Falha ao Conectar ao Servidor da ID do Live

 

_**Tópico modificado em:** 2015-06-22_

Tipicamente, há três razões para que sua tentativa de conexão falhe com a seguinte mensagem de erro:

    Get-CsWebTicket : Falha ao conectar servidores do Live ID. Verifique se o proxy está habilitado ou se o computador tem uma conexão de rede com servidores do Live ID.

Geralmente, esse erro significa que o Assistente de Sign-in do Microsoft Online Services não está funcionando. Você pode verificar o status desse serviço executando o seguinte comando do prompt Windows PowerShell:

    Get-Service "msoidsvc"

Se o serviço não está funcionando, inicie o serviço usando esse comando:

    Start-Service "msoidsvc"

Se o serviço está funcionando, você pode encontrar problemas com a conexão de rede entre seu computador e o Servidor de Autenticação da ID do Microsoft Live. Para verificar isso, abra o Internet Explorer e navegue para <https://login.microsoftonline.com/.> Tente efetuar o login no Office 365 a partir daqui. Se falhar, você está, provavelmente, está tendo problemas com a conexão de rede.

Menos comumente, é possível que a URl de Conexão para o Servidor de Autenticação de ID da Microsoft Live tenha sido configurada para o valor errado. Se você já determinou que o Assistente Sign-in está funcionando e que você não teve problemas de conectividade de rede, esse pode ser o problema. Neste caso, entre em contato com o Suporte Office 365.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

