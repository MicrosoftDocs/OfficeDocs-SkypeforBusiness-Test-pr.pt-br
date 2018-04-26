---
title: Monitoramento de arquivos de log de rastreamento de solicitação do IIS
TOCTitle: Monitoramento de arquivos de log de rastreamento de solicitação do IIS
ms:assetid: b6730e92-6d74-4fa7-a83f-50b7bdadbffa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690034(v=OCS.15)
ms:contentKeyID: 49307874
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitoramento de arquivos de log de rastreamento de solicitação do IIS

 

_**Tópico modificado em:** 2016-12-08_

Quando você habilita o rastreamento de solicitação do IIS (Serviços de Informações da Internet) para o Serviço de Mobilidade do Lync Server, os arquivos de log gerados podem consumir até três gigabytes de espaço em disco por dia. O registro em log do rastreamento IIS está habilitado por padrão. Monitore o Servidores Front-End para se certificar de que não fiquem sem espaço em disco.

Por padrão, o IIS armazena os arquivos de log em %SystemDrive%\\inetpub\\logs\\LogFiles.

Para desativar o rastreamento de solicitação IIS para todo um servidor, na linha de comando, digite o seguinte:

    %SystemDrive%\Windows\System32\inetsrv\appcmd set config /section:httpLogging /dontLog:True

Para obter detalhes sobre o comando **httpLogging**, consulte [http://go.microsoft.com/fwlink/?linkid=234927\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=234927%26clcid=0x416).

