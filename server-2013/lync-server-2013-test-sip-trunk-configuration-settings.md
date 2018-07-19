---
title: Testar as Configurações do Tronco SIP no Lync Server 2013
TOCTitle: Testar as Configurações do Tronco SIP no Lync Server 2013
ms:assetid: c8712308-0e2d-4e39-8f90-d1a250487a94
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721880(v=OCS.15)
ms:contentKeyID: 49886406
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Testar as Configurações do Tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

As definições de configuração de tronco SIP definem o relacionamento e as capacidades entre um Servidor de Mediação e gateway PSTN, um PBX-IP ou um SBC no provedor de serviços. Estas configurações fazem coisas como especificar:

  - Se o bypass de mídia deve ser habilitado nos troncos.

  - As condições nas quais os pacotes RTCP são enviados.

  - Se a criptografia SRTP é obrigatória em cada tronco.

Ao instalar o Microsoft Lync Server 2013, um conjunto global de definições de configuração de tronco SIP é criado para você. Além disso, os administradores podem criar conjuntos de configurações personalizadas no escopo local ou de serviço (apenas para o serviço de gateway PSTN). Os administradores também podem usar o cmdlet Test-CsTrunkConfiguration para verificar que um tronco pode converter um número conforme discado por um usuário para um número que pode ser tratado pelo gateway.

As definições de configuração de tronco podem ser testadas apenas usando o Windows PowerShell e o cmdlet [Test-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsTrunkConfiguration). Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Definições de configuração do tronco de teste

  - Este comando verifica se as definições de configuração para o local Redmond podem converter corretamente o número discado 4255551212.
    
        $trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
        Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $trunk

