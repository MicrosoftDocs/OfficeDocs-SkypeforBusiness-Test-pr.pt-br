---
title: Usando o Serviço de Registro em Log no Lync Server 2013
TOCTitle: Usando o Serviço de Registro em Log no Lync Server 2013
ms:assetid: 7b05aaef-f0ea-4649-ba8a-02e68b0cdf23
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688101(v=OCS.15)
ms:contentKeyID: 49886274
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o Serviço de Registro em Log no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

O Serviço de Log Centralizado é uma nova função em Lync Server 2013. É uma substituição melhorada para as ferramentas **OCSLogger** e **OCSTracer** fornecidas em lançamentos anteriores. Você pode usar o Serviço de Log Centralizado para realizar as seguintes tarefas:

  - Faça login em um ou mais computadores e pools de um único local e comando.

  - Pare o login em um ou mais computadores e pools de um único local e comando.

  - Busque logs em um ou mais computadores e pools de um único local e comando. É possível personalizar o comando de busca para retornar todo o conjunto de logs que foram capturados e armazenados em todas as máquinas, ou retornar um resultado reduzido que capture dados específicos.

  - Configurar as sessões de login conforme segue:
    
      - Defina um **Cenário** ou use um cenário default. Um *cenário* em Serviço de Log Centralizado é feito de escopo (global ou local), um nome de cenário para identificar o objetivo do cenário e um ou mais provedores. Você pode executar dois cenários a qualquer momento em um computador.
    
      - Use um .*provedor*local ou crie um novo provedor. Um *provedor* define o que será coletado pela sessão de registro em log, qual o detalhamento, quais componentes rastrear e quais o que sinalizadores são aplicados.
        

        > [!TIP]  
        > Se estiver familiarizado com OCSLogger, o termo <EM>provedores</EM> se refere à coleta de <STRONG>componentes</STRONG> (por exemplo, S4, SIPStack), um <STRONG>tipo de registro de log</STRONG> (por exemplo, WPP, EventLog ou IIS logfile), um <STRONG>nível de rastreamento</STRONG> (por exemplo, All, verbose, debug) e <STRONG>sinalizadores</STRONG> (por exemplo, TF_COMPONENT, TF_DIAG). Esses itens são definidos no provedor (uma Windows PowerShell variável) e repassados ao Serviço de Log Centralizado comando.

    
      - Configure os computadores e pools dos quais deseja coletar registros log.
    
      - Defina o escopo da sessão de registro log nas opções**Local** (executa capturas de registro log em computadores somente naquele local) ou **Global** (executa capturas de registro log em todos os computadores da implantação).

O Serviço de Log Centralizado é extremamente potente e pode atender praticamente todas as necessidades de resolução de problemas —grandes ou pequenos. Da análise da possível causa a problemas de desempenho, o Serviço de Log Centralizado pode ser uma ferramenta importante para qualquer administrador. Todos os exemplos são mostrados usando Shell de Gerenciamento do Lync Server. Há um componente de linha de comando para o Serviço de Log Centralizado chamado **CLSController.exe**. A ajuda para a ferramenta de linha de comando está disponível na própria ferramenta. Por esta razão, a primeira linha neste exemplo é uma chamada ao cmdlet do nm-winshell-2nd Read-Host. Usando Shell de Gerenciamento do Lync Server, você pode acessar muitos outros recursos configuráveis. Você deve sempre considerar Shell de Gerenciamento do Lync Server como o primeiro e único método ao usar o Serviço de Log Centralizado.

Os tópicos nesta seção explicam como usar o Serviço de Log Centralizado e fornecem exemplos de como usar seus diversos recursos.

## Nesta seção

  - [Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)

  - [Gerenciando as configurações do serviço de registro em log centralizado usando PowerShell](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)

  - [Entendendo as configurações do serviço de registro em log centralizado](lync-server-2013-understanding-centralized-logging-service-configuration-settings.md)

  - [Usando Iniciar para o Serviço de Registro em Log para Capturar Logs](lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md)

  - [Usando Parar para o Serviço de Registro em Log](lync-server-2013-using-stop-for-the-centralized-logging-service.md)

  - [Usando Buscar em Logs de Captura criados para o Serviço de Registro em Log](lync-server-2013-using-search-on-capture-logs-created-by-the-centralized-logging-service.md)

  - [Lendo Registros de Captura do Serviço de Registro em Log](lync-server-2013-reading-capture-logs-from-the-centralized-logging-service.md)

