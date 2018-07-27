---
title: Remover arquivos de atualização de dispositivo não associados a um dispositivo
TOCTitle: Remover arquivos de atualização de dispositivo não associados a um dispositivo
ms:assetid: ecebbf73-b456-4990-a91d-308b84d39404
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994084(v=OCS.15)
ms:contentKeyID: 52057751
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover arquivos de atualização de dispositivo não associados a um dispositivo

 

_**Tópico modificado em:** 2013-02-20_

Sempre que novas atualizações de dispositivo são carregadas no sistema, uma regra correspondente de atualização de dispositivo é criada. Por padrão, a essas novas regras de atualização de dispositivo é atribuído o estado Pendente. Isso significa que as regras podem ser baixadas e instaladas em dispositivos de teste, mas não em dispositivos de produção, o que permite que você teste as atualizações antes de disponibilizá-las aos usuários. Baseado nos testes, você aceita e implanta ou rejeita e exclui a atualização. Quando você rejeita uma atualização, ela é dissociada da respectiva regra de atualização de dispositivo.


Os arquivos da atualização de dispositivo que não estão mais associados a um dispositivo podem ser removidos usando o Windows PowerShell e o cmdlet **Clear-CsDeviceUpdateFile**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


  - Por exemplo, o seguinte comando remove todas as regras da atualização de dispositivo do servidor Web atl-cs-001.litwareinc.com que não estão mais associadas a um dispositivo:
    
        Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"

Para obter detalhes, consulte o tópico da Ajuda para o cmdlet [Clear-CsDeviceUpdateFile](https://docs.microsoft.com/en-us/powershell/module/skype/Clear-CsDeviceUpdateFile).

