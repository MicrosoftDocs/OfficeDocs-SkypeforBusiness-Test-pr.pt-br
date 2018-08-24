---
title: Movendo Grupos de Resposta a um Novo Pool
TOCTitle: Movendo Grupos de Resposta a um Novo Pool
ms:assetid: da0db765-41e5-430b-b5a7-5418ec5ff2a7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205298(v=OCS.15)
ms:contentKeyID: 49308291
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Movendo Grupos de Resposta a um Novo Pool

 

_**Tópico modificado em:** 2012-11-01_

O Lync Server 2013 introduzir novo suporte de cmdlet para mover grupos de resposta de um pool para outro, mesmo quando o FQDN é diferente.

Use as etapas no procedimento anterior para mover grupos de resposta de um Pool de Front-Ends para outro Pool de Front-Ends com um FQDN diferente.

> [!NOTE]  
> Em um ambiente de coexistência, é possível mover os grupos de resposta apenas entre Lync Server 2013Pools de Front-Ends.

## Para mover grupos de resposta para um pool com um FQDN diferente

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Exporte os grupos de resposta no pool de origem. Na linha de comando, digite:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source FQDN>" -FileName "<export file name>"
    
    Por exemplo:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -FileName "C:\RgsExportSource.zip"
    
    Para remover os grupos de resposta de um pool de origem durante a exportação, inclua o parâmetro –RemoveExportedConfiguration. Por exemplo:
    
        Export-CsRgsConfiguration -Source ApplicationServer:source.contoso.com -FileName "C:\RgsExportSource.zip" -RemoveExportedConfiguration

3.  Importe os grupos de resposta para o pool de destino e atribua o pool de destino como o novo proprietário. Na linha de comando, digite:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<destination pool>" -FileName "<export file name>" -OverwriteOwner
    
    Se você também deseja copiar as configurações de nível de aplicativo do Grupo de Resposta do pool de origem para o pool de destino, inclua o parâmetro –ReplaceExistingSettings. É possível definir apenas um conjunto de configurações a nível de aplicativo por pool. Se você copiar as configurações a nível de aplicativo do pool de origem para o pool de destino, as configurações do pool de origem substituem as configurações para o pool de destino. Se você não copiar as configurações a nível de aplicativo do pool de origem, as configurações existentes do pool de destino se aplicam aos grupos de resposta importados.
    
    Por exemplo:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:destination.contoso.com" -FileName "C:\RgsExportSource.zip" -OverwriteOwner -ReplaceExistingSettings
    
    > [!NOTE]  
    > As configurações a nível de aplicativo incluem a configuração de música em espera padrão, o arquivo de áudio de música em espera padrão, o período de espera do agente e a configuração de contexto da chamada. Para exibir estas definições de configuração, execute o cmdlet <strong>Get-CsRgsConfiguration</strong>. Para obter detalhes sobre este cmdlet, consulte <a href="https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration">Get-CsRgsConfiguration</a>.

4.  Verifique se a importação teve êxito ao exibir a configuração do grupo de resposta importado fazendo o seguinte:
    
      - Verifique se todos os fluxos de trabalho foram importados. Na linha de comando, digite o seguinte:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verifique se todas as filas foram importadas. Na linha de comando, digite o seguinte:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verifique se todos os grupos de agente foram importados. Na linha de comando, digite o seguinte:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verifique se todas as horas comerciais foram importadas. Na linha de comando, digite o seguinte:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<destination pool FQDN>" 
    
      - Verifique se todos os conjuntos de feriados foram importados. Na linha de comando, digite o seguinte:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<destination pool FQDN>" 

5.  Verifique se a importação teve êxito ao realizar uma chamada para um dos grupos de resposta e verificando se a chamada foi tratada corretamente.

6.  Agentes de solicitação membros de grupos de agente formais para se conectar em seus grupos de agentes no pool de destino.

7.  Se você não removeu anteriormente grupos de resposta do pool de origem, remova os grupos de resposta do pool de origem. Na linha de comando, digite:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source pool FQDN> -RemoveExportedConfiguration -FileName "<temporary export file name>"
    
    Por exemplo:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -RemoveExportedConfiguration -FileName "C:\TempRGsConfiguration.zip"

