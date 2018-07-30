---
title: Configurando cenários para o serviço de registro em log centralizado
TOCTitle: Configurando cenários para o serviço de registro em log centralizado
ms:assetid: 6c3bf826-e7fd-4002-95dc-01020641ef01
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688085(v=OCS.15)
ms:contentKeyID: 49886254
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando cenários para o serviço de registro em log centralizado

 

_**Tópico modificado em:** 2016-12-08_

Os cenários definem o escopo (ou seja, global, site, pool ou computador) e quais provedores usar no Serviço de Log Centralizado. Ao utilizar cenários, você habilita ou desabilita o rastreamento em provedores (por exemplo, S4, SIPStack, mensagens instantâneas e Presença). Ao configurar um cenário, você pode agrupar todos os provedores de uma determinada coleção lógica que aborda uma condição de problema específica. Se você achar que um cenário precisa ser modificado para atender às suas necessidades de solução de problemas e logon, as Ferramentas de Depuração do Lync Server 2013 fornecem um módulo do Windows PowerShell denominado *ClsController.psm1* que contém uma função chamada *Edit-CsClsScenario*. O objetivo do módulo é editar as propriedades do cenário nomeado. Exemplos do funcionamento desse módulo são fornecidos neste tópico. As Ferramentas de Depuração do Lync Server 2013 são baixadas do seguinte link: [http://go.microsoft.com/fwlink/?LinkId=285257](http://go.microsoft.com/fwlink/?linkid=285257)

> [!IMPORTANT]  
> Para qualquer dado escopo (global, site, pool ou computador), é possível executar no máximo dois cenários por vez. Para determinar quais cenários estão em execução no momento, use o Windows PowerShell e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsScenario">Get-CsClsScenario</a>. Usando o Windows PowerShell e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsScenario">Set-CsClsScenario</a>, é possível alterar dinamicamente quais cenários estão em execução. Você pode modificar quais cenários estão em execução durante uma sessão de registro em log para ajustar ou refinar os dados coletados e de quais provedores.

Para executar as funções do Serviço de Log Centralizado usando o Shell de Gerenciamento do Lync Server, você precisa ser um membro dos grupos de segurança do RBAC (controle de acesso baseado em função) CsAdministrator ou CsServerAdministrator ou de uma função do RBAC personalizada que contenha um desses dois grupos. Para retornar uma lista de todas as funções do RBAC às quais este cmdlet foi atribuído (incluindo funções do RBAC personalizadas que você mesmo criou), execute o seguinte comando a partir do Shell de Gerenciamento do Lync Server ou do prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

Por exemplo:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

O restante deste tópico concentra-se em como definir um cenário, modificar um cenário, recuperar quais cenários estão em execução, remover um cenário e especificar o que um cenário contém para otimizar a solução de problemas. Há duas maneiras de emitir comandos do Serviço de Log Centralizado. Você pode usar o CLSController.exe, que fica localizado por padrão no diretório C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent, ou pode usar o Shell de Gerenciamento do Lync Server para emitir comandos do Windows PowerShell. A distinção importante é que, quando você usa o CLSController.exe na linha de comando, há uma seleção finita de cenários disponíveis. Quando você usa o Windows PowerShell, pode definir novos cenários para uso em suas sessões de registro em log.

Conforme introduzidos em [Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md), os elementos de um cenário são:

  - **Provedores**   Se você já conhece o OCSLogger, os provedores são os componentes que você escolhe para informar ao OCSLogger do que o mecanismo de rastreamento deverá coletar logs. Os provedores são os mesmos componentes e, em muitos casos, têm o mesmo nome que os componentes do OCSLogger. Se você não está familiarizado com o OCSLogger, os provedores são componentes específicos de função de servidor dos quais o Serviço de Log Centralizado pode coletar logs. Para obter detalhes sobre a configuração de provedores, consulte [Configurando provedores do serviço de registro em log centralizado](lync-server-2013-configuring-providers-for-centralized-logging-service.md).

  - **Identidade**   O parâmetro –Identity define o escopo e o nome do cenário. Por exemplo, você pode definir um escopo "global" e identificar o cenário como “LyssServiceScenario”. Ao combinar os dois, você define a identidade (por exemplo, “global/LyssServiceScenario”).
    
    Opcionalmente, você pode usar os parâmetros –Name e –Parent. Você define o parâmetro Name para identificar exclusivamente o cenário. Se usá-lo, também deverá usar Parent para adicionar o cenário ao escopo global ou site.
    
    > [!IMPORTANT]  
    > Se você usar os parâmetros Name e Parent, não poderá usar o parâmetro <strong>–Identity</strong>.

## Para criar um novo cenário com o cmdlet New-CsClsScenario

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para criar um novo cenário para uma sessão de registro em log, use [New-CsClsProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsProvider) e defina o nome do cenário (ou seja, como ele será identificado exclusivamente). Escolha um tipo de formato de registro em log entre WPP (ou seja, o pré-processador de rastreamento de software do Windows, que é o padrão), EventLog (ou seja, o formato de log de eventos do Windows) ou IISLog (ou seja, o arquivo de formato ASCII baseado no formato de arquivo de log do IIS). Em seguida, defina o nível (conforme definido em Níveis de registro em log neste tópico) e os sinalizadores (conforme definido em Sinalizadores neste tópico).
    
    Para este cenário de exemplo, usaremos LyssProvider como a variável de provedor de exemplo.
    
    Para criar um cenário usando as opções definidas, digite:
    
        New-CsClsScenario -Identity <scope>/<unique scenario name> -Provider <provider variable>
    
    Por exemplo:
    
        New-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider $LyssProvider
    
    Formato alternativo usando –Name e –Parent:
    
        New-CsClsScenario -Name "LyssServiceScenario" -Parent "site:Redmond" -Provider $LyssProvider

## Para criar um novo cenário com vários provedores usando o cmdlet New-CsClsScenario

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Há um limite de dois cenários por escopo. No entanto, não há um limite quanto ao número de provedores. Neste exemplo, suponha que criamos três provedores e você deseja atribuir todos eles ao cenário que está definindo. Os nomes das variáveis dos provedores são LyssProvider, ABServerProvider e SIPStackProvider. Para definir e atribuir vários provedores a um cenário, digite o seguinte em um Shell de Gerenciamento do Lync Server ou prompt de comando do Windows PowerShell:
    
        New-CsClsScenario -Identity "site:Redmond/CollectDataScenario" -Provider @{Add=$LyssProvider, $ABServerProvider,  $SIPStackProvider}
    
    > [!NOTE]  
    > Como é conhecida no Windows PowerShell, a convenção para criar uma tabela hash de valores usando <code>@{&lt;variable&gt;=&lt;value1&gt;, &lt;value2&gt;, &lt;value&gt;...}</code> é conhecida como <em>splatting</em>. Para obter detalhes sobre o splatting no Windows PowerShell, consulte <a href="http://go.microsoft.com/fwlink/?linkid=267760%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=267760&amp;clcid=0x416</a>.

## Para modificar um cenário existente com o cmdlet Set-CsClsScenario

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Há um limite de dois cenários por escopo. Você pode alterar quais cenários estão em execução a qualquer momento, mesmo quando uma sessão de coleta de log está em andamento. Se você redefinir os cenários em execução, a sessão de registro em log atual parará de usar o cenário que foi removido e começará a usar o novo cenário. No entanto, as informações de log que já foram coletadas com o cenário removido permanecerão nos logs coletados. Para definir um novo cenário, faça o seguinte (pressupondo a adição de um provedor já definido chamado “S4Provider”):
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Add=<new provider to add>}
    
    Por exemplo:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Add=$S4Provider}
    
    Se você desejar substituir provedores, defina um único provedor ou uma lista separada por vírgulas de provedores para substituir o conjunto atual. Se você desejar substituir apenas um de vários provedores, adicione os provedores atuais junto com os novos provedores para criar um novo conjunto de provedores que contenha os provedores novos e existentes. Para substituir todos os provedores por um novo conjunto, digite o seguinte:
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Replace=<providers to replace existing provider set>}
    
    Por exemplo, para substituir o conjunto atual de $LyssProvider, $ABServerProvider e $SIPStackProvider por $LyssServiceProvider:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider}
    
    Para substituir apenas o provedor $LyssProvider do conjunto atual de $LyssProvider, $ABServerProvider e $SIPStackProvider por $LyssServiceProvider, digite o seguinte:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider, $ABServerProvider, $SIPStackProvider}

## Para remover um cenário existente com o cmdlet Remove-CsClsScenario

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Se você desejar remover um cenário que foi definido anteriormente, digite o seguinte:
    
        Remove-CsClsScenario -Identity <name of scope and scenario>
    
    Por exemplo, para remover o cenário definido site:Redmond/LyssServiceScenario:
    
        Remove-CsClsScenario -Identity "site:Redmond/LyssServiceScenario"

O cmdlet **Remove-CsClsScenario** remove o cenário especificado, mas os rastreamentos que foram coletados ainda estarão disponíveis nos logs para pesquisa.

## Para carregar e descarregar o cmdlet Edit-CsClsScenario usando o módulo ClsController.psm1

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.
    
    > [!IMPORTANT]  
    > O módulo ClsController.psm1 é fornecido como um download da Web separado. O módulo faz parte das ferramentas de depuração do Lync Server 2013. Por padrão, as ferramentas de depuração são instaladas no diretório C:\Program Files\Lync Server 2013\Debugging Tools.

2.  No Windows PowerShell, digite:
    
        Import-Module "C:\Program Files\Lync Server 2013\Debugging Tools\ClsController.psm1"
    

    > [!TIP]
    > Se o módulo for carregado com êxito, você será redirecionado para o prompt de comando do Windows PowerShell. Para confirmar que o módulo está carregado e que Edit-CsClsScenario está disponível, digite <CODE>Get-Help Edit-CsClsScenario</CODE>. Você deverá ver a sinopse básica da sintaxe de EditCsClsScenario.



3.  Para descarregar os módulos, digite:
    
        Remove-Module ClsController
    

    > [!TIP]
    > Se o módulo for descarregado com êxito, você será redirecionado para o prompt de comando do Windows PowerShell. Para confirmar que o módulo foi descarregado, digite <CODE>Get-Help Edit-CsClsScenario</CODE>. O Windows PowerShell tentará localizar a ajuda do cmdlet e falhará.



## Para remover um provedor existente de um cenário com o módulo Edit-ClsController

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para remover um provedor do cenário AlwaysOn, digite:
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to remove> -Remove
    
    Por exemplo:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Remove
    
    Os parâmetros ScenarioName e ProviderName são posicionais (ou seja, devem ser definidos na posição esperada na linha de comando). O nome do parâmetro não precisa ser explicitamente definido se o nome do cenário estiver na segunda ou na terceira posição em relação ao nome do cmdlet na primeira posição. Usando essas informações, o comando anterior seria digitado como:
    
        Edit-CsClsScenario AlwaysOn ChatServer -Remove
    
    A colocação posicional dos valores de parâmetro aplica-se somente a –Scenario e –Provider. Todos os outros parâmetros devem ser definidos explicitamente.

## Para adicionar um provedor a um cenário com o cmdlet Edit-ClsController

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para adicionar um provedor ao cenário AlwaysOn, digite:
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to add> -Level <string of type level> -Flags <string of type flags>
    
    Por exemplo:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Level Info -Flags TF_COMPONENT
    
    \-Loglevel pode ser do tipo Fatal, Error, Warning, Info, Verbose, Debug ou All. –Flags pode ser qualquer um dos sinalizadores aos quais o provedor oferece suporte, como TF\_COMPONENT, TF\_DIAG. –Flags também pode ter o valor ALL.
    
    O exemplo anterior também pode ser digitado com o uso do recurso posicional do cmdlet. Por exemplo, para adicionar o provedor ChatServer ao cenário AlwaysOn, digite:
    
        Edit-CsClsScenario AlwaysOn ChatServer -Level Info -Flags ALL

