---
title: Restaurando as configurações do grupo de resposta
TOCTitle: Restaurando as configurações do grupo de resposta
ms:assetid: 4f8e1949-925d-4538-be1d-9ac7c06b2aca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202174(v=OCS.15)
ms:contentKeyID: 52057628
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando as configurações do grupo de resposta

 

_**Tópico modificado em:** 2013-02-18_

Se você implantou o Aplicativo Grupo de Resposta e precisa restaurar um Servidor Back End ou um Servidor Standard Edition, também precisa restaurar as definições de configuração do Grupo de Resposta.

## Para restaurar as definições de configuração do Grupo de Resposta

1.  Na linha de comando, digite:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<pool FQDN>" -OverwriteOwner -FileName "<path and file name of the backed up file at $Backup>"
    
    Por exemplo:
    
        Import-CsRgsConfiguration -Destination "service: ApplicationServer:pool01.contoso.com" -OverwriteOwner -FileName "C:\RgsConfiguration.zip"

