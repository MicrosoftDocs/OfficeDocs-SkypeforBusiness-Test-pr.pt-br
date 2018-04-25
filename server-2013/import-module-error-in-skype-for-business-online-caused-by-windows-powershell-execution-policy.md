---
title: Erro do módulo de importação causado por política de execução do Windows PowerShell
TOCTitle: Erro do módulo de importação causado por política de execução do Windows PowerShell
ms:assetid: 4bc093ca-fd30-44c9-a0a3-16f78698df2b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362786(v=OCS.15)
ms:contentKeyID: 56270387
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Erro do módulo de importação causado por política de execução do Windows PowerShell

 

_**Tópico modificado em:** 2016-12-08_

A política de execução do Windows PowerShell ajuda a determinar que arquivos de configuração podem ser carregados no console do Windows PowerShell e que scripts um usuário poderá executar desse console. No mínimo, o módulo Conector do Skype for Business Online não poderá ser importado, a menos que a política de execução seja definida como RemoteSigned. Caso não seja, então você receberá a seguinte mensagem de erro quando tentar importar o módulo:

    Import-Module : File C:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnectorStartup.psm1 não pode ser carregado porque a execução de scripts está desativada no sistema. Para mais informações, consulte about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.

Para resolver esse problema, inicie o Windows PowerShell como administrador e então execute o seguinte comando:

    Set-ExecutionPolicy RemoteSigned

Para obter detalhes sobre a política de execução, consulte o tópico da Ajuda em [http://go.microsoft.com/fwlink/?LinkID=135170](http://go.microsoft.com/fwlink/?linkid=135170).

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

