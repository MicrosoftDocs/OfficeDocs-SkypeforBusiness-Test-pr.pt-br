---
title: Modificar um tronco no Construtor de Topologia no Lync Server 2013
TOCTitle: Modificar um tronco no Construtor de Topologia no Lync Server 2013
ms:assetid: 81055a82-c6f8-47b2-9779-223b1d842f36
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688110(v=OCS.15)
ms:contentKeyID: 49886285
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar um tronco no Construtor de Topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Siga estes passos para modificar o endereço IP de mídia alternativa e identificador alternativo de bypass de um tronco.

## Para modificar o endereço IP de mídia alternativa de um tronco

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsPstnGateway e modifique o campo AlternateBypassId no Shell de Gerenciamento do Lync Server.
    
        Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -RepresentativeMediaIP <IP address>

## Para modificar o BypassID alternativo de um tronco

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsPstnGateway e modifique o campo AlternateBypassId no Shell de Gerenciamento do Lync Server.
    
        Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -AlternateBypassID <identifier>

