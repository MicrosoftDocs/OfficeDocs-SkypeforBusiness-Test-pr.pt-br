---
title: Shell de gerenciamento do Lync Server
TOCTitle: Shell de gerenciamento do Lync Server
ms:assetid: 674b523b-c0b7-4ed6-9e67-afa6e8ac7e12
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398474(v=OCS.15)
ms:contentKeyID: 49306960
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Shell de gerenciamento do Lync Server

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2010 introduziu um grande conjunto de recursos novos e aprimorados em comparação ao que havia disponível no Microsoft Office Communications Server 2007 R2. Um dos aprimoramentos está na forma de gerenciar a implementação. Por exemplo, a nova interface do usuário, chamada Painel de Controle do Lync Server, que representa uma mudança considerável em relação ao que a maioria das pessoas está acostumada com o Console de Gerenciamento Microsoft. Outro aperfeiçoamento importante na capacidade de gerenciamento é a inclusão do Windows PowerShell.

O Windows PowerShell permite que você gerencie aplicativos da Microsoft a partir da linha de comando. Ele inclui um ambiente de linha de comando, comandos específicos de produtos e uma linguagem de script completa. O Windows PowerShell foi lançado como uma versão para download do sistema operacional Windows no final de 2006 e foi incorporado como a interface de linha de comando para gerenciamento do Microsoft Exchange Server 2007. Desde então, ele continuou a crescer e foi incorporado à maioria dos produtos Microsoft Server, entre os quais o mais recente é o Microsoft Lync Server 2013. O Lync Server 2010 introduziu quase 550 cmdlets específicos de produto que você pode usar para gerenciar todos os aspectos da sua implantação.

As seções a seguir contêm uma lista de cmdlets e suas descrições. Essas informações também estão disponíveis diretamente da linha de comando. Simplesmente digite o seguinte no prompt de comando do Shell de Gerenciamento do Lync Server:

    Get-Help <cmdlet name> -Full

Por exemplo, para recuperar a Ajuda no prompt de comando, no cmdlet **New-CsVoicePolicy**, digite o seguinte:

    Get-Help New-CsVoicePolicy -Full

Informações importantes sobre o Windows PowerShell no Lync Server 2013:

  - Para executar os cmdlets do Lync Server, abra o Shell de Gerenciamento do Lync Server.
    

    > [!WARNING]  
    > Se você abrir uma janela do Windows PowerShell em vez do Shell de Gerenciamento do Lync Server, por padrão, não poderá executar os cmdlets do Lync Server. Para executar os cmdlets do Lync Server a partir do Windows PowerShell, primeiro digite o seguinte no prompt de comando do Windows PowerShell:<BR>Import-Module Lync



  - O Shell de Gerenciamento do Lync Server é instalado automaticamente em cada Servidor Front-End Enterprise Edition ou servidor Standard Edition do Lync Server.

  - Informações novas e atualizadas, scripts de exemplo e ajuda para começar e saber mais sobre os cmdlets do Windows PowerShell e do Microsoft Lync Server 2013 estão disponíveis no Blog do Lync Server Windows PowerShell [http://go.microsoft.com/fwlink/?linkid=203150\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x416).

