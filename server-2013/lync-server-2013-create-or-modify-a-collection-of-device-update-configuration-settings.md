---
title: Criar ou modificar um conjunto de definições de configuração de atualização de dispositivo
TOCTitle: Criar ou modificar um conjunto de definições de configuração de atualização de dispositivo
ms:assetid: 3e8ce95f-a8c8-417c-b1f7-0f759a567aff
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994029(v=OCS.15)
ms:contentKeyID: 52057587
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um conjunto de definições de configuração de atualização de dispositivo

 

_**Tópico modificado em:** 2016-12-08_

As definições de configuração de dispositivo podem ser criadas (somente no escopo do site) utilizando Windows PowerShell e o cmdlet **New-CsDeviceUpdateConfiguration**, podendo ser também modificadas utilizando o cmdlet **Set-CsDeviceUpdateConfiguration**. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou então de uma sessão remota de Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


## Para criar novas configurações de atualização de dispositivo que usem os valores padrão

  - Esse comando cria um novo conjunto de configurações de atualização de dispositivo para o site Redmond:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond"
    
    Como nenhum parâmetro além do parâmetro obrigatório Identity foi especificado no comando anterior, o novo conjunto de configurações usará os valores padrão para todas suas propriedades.

## Para alterar o valor de apenas uma propriedade ao criar novas configurações de atualização de dispositivo

  - Para criar configurações que usem valores de propriedade diferentes, basta incluir o parâmetro e valor de parâmetro adequados. Por exemplo, para criar um conjunto de configurações de atualização de dispositivo que por padrão excluam arquivos de log antigos a cada 21 dias, use um comando como este:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00"

## Para alterar valores de várias propriedades ao criar novas configurações de atualização de dispositivo

  - Valores múltiplos de propriedade podem ser modificados incluindo parâmetros múltiplos. Por exemplo, esse comando define o intervalo de limpeza de logs em 21 dias e o intervalo de liberação de logs em 30 minutos:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00" -LogFlushInterval "00:30:00"

Para detalhes sobre como modificar configurações de dispositivo existentes, consulte o tópico Ajuda para o cmdlet [Set-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsDeviceUpdateConfiguration). Para detalhes sobre como criar conjuntos de configurações, veja o tópico Ajuda para o cmdlet [New-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsDeviceUpdateConfiguration).

