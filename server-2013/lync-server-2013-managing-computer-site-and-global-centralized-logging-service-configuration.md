---
title: Gerenciando a configuração do computador, local e de serviço de registro em log centralizado global
TOCTitle: Gerenciando a configuração do computador, local e de serviço de registro em log centralizado global
ms:assetid: 93b9a354-9aea-4b3a-a4fe-68a89f436196
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688138(v=OCS.15)
ms:contentKeyID: 49886318
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando a configuração do computador, local e de serviço de registro em log centralizado global

 

_**Tópico modificado em:** 2014-02-04_

O Serviço de Log Centralizado pode ser executado em um escopo que inclui um único computador, um pool de computadores, em um escopo de site (isto é, um site definido como o site da Redmond que contém uma coleção de computadores e pools em sua implantação), ou em um escopo global (isto é, todos os computadores e pools em sua implantação).

Para configurar o escopo do Serviço de Log Centralizado usando o Shell de Gerenciamento do Lync Server, é necessário ser membro dos grupos de segurança de controle de acesso baseado em funções (RBAC) CsAdministrator ou CsServerAdministrator, ou uma função RBAC personalizada que contenha um desses dois grupos. Para retornar uma lista de todas as funções RBAC em que esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada), execute o seguinte comando do Shell de Gerenciamento do Lync Server ou do prompt Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "<Lync Server 2013 cmdlet>"}

Por exemplo:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

> [!NOTE]  
> O Windows PowerShell fornece a você mais opções e opções de configuração adicionais que não estão disponíveis usando o CLSController.exe. O CLSController oferece um método rápido de conciso para executar comandos, mas está limitado ao conjunto de comandos disponíveis para o CLSController. O Windows PowerShell não é limitado apenas ao comando disponível ao processador de comandos do CLSController, e fornece um conjunto mais amplo de comandos e um conjunto mais rico de opções. Por exemplo, o CLSController.exe fornece a você opções de escopo para computadores e pools. Com o Windows PowerShell, você pode indicar computadores ou pools na maioria dos comandos, e quando você definir novos cenários (o CLSController tem um número finito de cenários que não podem ser modificados pelo usuário), é possível definir um escopo de site ou global. Esse recurso poderoso do Windows PowerShell permite definir um cenário de escopo de site ou global, mas limita o log real a um computador ou pool.<br />Há diferenças fundamentais entre os comandos da linha de comando que você pode executar no Windows PowerShell ou CLSController. O Windows PowerShell fornece um método rico para configurar e definir cenários, e para reutilizar esses cenários de maneira significativa para seus cenários de solução de problemas. Embora o CLSController does forneça uma maneira rápida e eficiente para emitir comandos e obter resultados, o conjunto de comandos do CLSController está limitado aos comandos finitos que você tem disponível na linha de comando. Ao contrário dos cmdlets Windows PowerShell, o CLSController não pode definir novos cenários, gerenciar escopo em nível de site ou global, e muitas outras limitações de um conjunto de comandos finito que pode ser dinamicamente configurado. Embora o CLSController forneça um meio para execução rápida, o Windows PowerShell fornece um meio para estender a funcionalidade do Serviço de Log Centralizado além do que é possível no CLSController.

Um escopo de computador exclusivo pode ser definido durante a execução de um comando [Search-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Search-CsClsLogging), [Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging), [Start-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Start-CsClsLogging), [Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging), [Sync-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Sync-CsClsLogging) e [Update-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Update-CsClsLogging) usando o parâmetro –Computers. Esse parâmetro aceita uma lista separada por vírgulas de FQDNs (nomes de domínio totalmente qualificados) para o computador de destino.


> [!TIP]
> Você pode também definir –Pools e uma lista separada por vírgula de pools na qual você deseja executar os comandos de log.



Os escopos de Site e Global são definidos nos cmdlets **New-**, **Set-**, e **Remove-**Serviço de Log Centralizado. Os exemplos a seguir demonstram como definir o escopo de um site ou global.

> [!IMPORTANT]  
> Os comandos mostrados podem conter parâmetros e conceitos que são abordados em outras seções. O exemplo de comandos tem a finalidade de demonstrar o uso do parâmetro <strong>–Identity</strong> para definir escopo e os outros parâmetros são incluídos para a integridade e para especificar o escopo. Para obter detalhes sobre os cmdlets do <strong>Set-CsClsConfiguration</strong>, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration">Set-CsClsConfiguration</a> na documentação Operações.

## Para recuperar a configuração atual do Serviço de Log Centralizado

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Get-CsClsConfiguration

Use os cmdlets **New-CsClsConfiguration** e **Set-CsClsConfiguration** para criar uma nova configuração ou para atualizar uma configuração existente.

Quando o **Get-CsClsConfiguration** é executado, ele exibe informações semelhantes à seguinte captura de tela, onde a implantação atualmente tem a configuração global, mas nenhuma configuração de site definida:

![Amostra de saída do Get-CsClsConfiguration.](images/JJ688138.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Amostra de saída do Get-CsClsConfiguration.")

## Para recuperar a configuração atual do Serviço de Log Centralizado do armazenamento local do computador

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Get-CsClsConfiguration -LocalStore

Ao usar o primeiro exemplo, onde **Get-CsClsConfiguration** não especifica nenhum parâmetro, o comando referencia o Repositório de Gerenciamento Central para os dados. Se você especificar o parâmetro –LocalStore, o comando referencia o LocalStore do computador em vez do Repositório de Gerenciamento Central.

## Para recuperar uma lista de cenários definidos no momento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Get-CsClsConfiguration -Identity <scope and name> | Select-Object -ExpandProperty Scenarios
    
    Por exemplo, para recuperar os cenários definidos no escopo global:
    
        Get-CsClsConfiguration -Identity "global" | Select-Object -ExpandProperty Scenarios

O cmdlet **Get-CsClsConfiguration** sempre exibe os cenários que fazem parte de uma dada configuração de escopo. Na maioria dos casos, nem todos os cenários são exibidos e estão truncados. O comando usado aqui lista todos os cenários e as informações parciais sobre quais provedores, configurações e sinalizadores são usados.

## Par atualizar um escopo global do Serviço de Log Centralizado usando Windows PowerShell

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Set-CsClsConfiguration -Identity <scope> -EtlFileRolloverSizeMB <size for logging file in megabytes>
    
    Por exemplo:
    
        Set-CsClsConfiguration -Identity "global" -EtlFileRolloverSizeMB 40

O comando diz ao CLSAgent em cada computador e pool na implantação para definir o tamanho do valor de sobreposição no arquivo de rastreamento para 40 megabytes. Os computadores e pools em todos os sites são afetados pelo comando, e definirão seu valor configurado de sobreposição de log de rastreamento para 40 megabytes.

## Para atualizar um escopo de site do Serviço de Log Centralizado usando Windows PowerShell

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Set-CsClsConfiguration -Identity <scope/site name> -EtlFileRolloverSizeMB <size for logging file in megabytes> -EtlFileFolder <default location %TEMP%\Tracing>
    
    Por exemplo:
    
        Set-CsClsConfiguration -Identity "site/Redmond" -EtlFileRolloverSizeMB 40 -EtlFileFolder "C:\LogFiles\Tracing" 
    
    > [!NOTE]  
    > Como observado no exemplo, o local padrão dos arquivos de log é %TEMP%\Tracing. No entanto, como é o CLSAgent que está gravando o arquivo, e o CSLAgent é executado no Serviço de Rede, a variável %TEMP% expande para %WINDIR%\ServiceProfiles\NetworkService\AppData\Local.

O comando diz ao CLSAgent em cada computador e pool no site da Redmond para definir o tamanho do valor de sobreposição no arquivo de rastreamento para 40 megabytes. Os computadores e pools em outros sites não serão afetados pelo comando, e continuarão a usar o valor atualmente configurado de sobreposição de log de rastreamento definido pelo padrão (20 megabytes) ou durante o início da sessão de log.

## Para criar uma nova configuração do Serviço de Log Centralizado

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        New-CsClsConfiguration -Identity <scope and name> [CsClsConfiguration options for this site]
    
    > [!NOTE]  
    > New-CsClsConfiguration fornece acesso a um grande número de definições de configuração adicionais. Para obter detalhes sobre as opções de configuração, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsConfiguration">Get-CsClsConfiguration</a> e <a href="lync-server-2013-understanding-centralized-logging-service-configuration-settings.md">Entendendo as configurações do serviço de registro em log centralizado</a>.    
    Por exemplo, para criar uma nova configuração que defina uma pasta de rede para arquivos de cache, o período de tempo de sobreposição dos arquivos de log e tamanho de sobreposição dos arquivos de log, você deverá digitar:
    
        New-CsClsConfiguration -Identity "site:Redmond" -CacheFileNetworkFolder "\\fs01.contoso.net\filestore\logfiles" -EtlFileRolloverMinutes 120 -EtlFileRolloverSizeMB 40

Você deve planejar cuidadosamente a criação de novas configurações e como definir as novas propriedades do Serviço de Log Centralizado. Você deve ter cuidado ao fazer alterações e ter certeza que compreende o impacto da sua capacidade de registrar cenários de problema corretamente. Você deve fazer alterações na configuração que melhorarão sua capacidade de gerenciar logs para um tamanho e período de sobreposição que permita resolver problemas, quando surgirem.

## Para remover uma configuração existente do Serviço de Log Centralizado.

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Digite o seguinte no prompt de linha de comando:
    
        Remove-CsClsConfiguration -Identity <scope and name>
    
    Por exemplo, para remover uma configuração do Serviço de Log Centralizado que você criou para aumentar o tempo de sobreposição do arquivo de log, aumente o tamanho do arquivo de log de sobreposição, e defina o local de cache de arquivo de log para um compartilhamento de rede, da seguinte maneira:
    
        Remove-CsClsConfiguration -Identity "site:Redmond"
    
    > [!NOTE]  
    > Esta é a nova configuração que foi criada no procedimento &quot;Para criar uma nova configuração do Serviço de Log Centralizado.&quot;

Se decidir remover a configuração no nível do site, o site usará as configurações globais.

## Consulte Também

#### Conceitos

[Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### Outros Recursos

[Gerenciando as configurações do serviço de registro em log centralizado usando PowerShell](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)  
[Set-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration)  
[Get-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsConfiguration)  
[New-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsConfiguration)  
[Remove-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsConfiguration)

