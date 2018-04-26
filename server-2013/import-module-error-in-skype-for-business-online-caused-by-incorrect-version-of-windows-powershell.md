---
title: Importar Erro de Módulo Causado pela Versão Incorreta do Windows PowerShell
TOCTitle: Importar Erro de Módulo Causado pela Versão Incorreta do Windows PowerShell
ms:assetid: 6c209f41-2b97-4dda-b0b7-e5b582d3e6b6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362802(v=OCS.15)
ms:contentKeyID: 56270424
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importar Erro de Módulo Causado pela Versão Incorreta do Windows PowerShell

 

_**Tópico modificado em:** 2015-06-22_

O módulo conector Skype for Business Online pode ser executado apenas sob Windows PowerShell 3.0. Se você tentar importar o módulo sob uma versão anterior do Windows PowerShell, o processo de importação falhará com uma mensagem de erro similar a esta:

    Import-Module :   A versão do PowerShell carregada é '2.0'. O módulo 'D:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnector.psd1' requer no mínimo a versão '3.0' do PowerShell para ser executado. Verifique a instalação do PowerShell e tente novamente.

A única forma de solucionar o problema é instalar o Windows PowerShell 3.0, que está disponível no Centro de Download da Microsoft em <http://www.microsoft.com/en-us/download/details.aspx?id=29939>.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

