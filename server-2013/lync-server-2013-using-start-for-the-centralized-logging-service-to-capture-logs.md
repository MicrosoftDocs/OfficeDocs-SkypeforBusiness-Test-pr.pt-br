---
title: Usando Iniciar para o Serviço de Registro em Log para Capturar Logs
TOCTitle: Usando Iniciar para o Serviço de Registro em Log para Capturar Logs
ms:assetid: 0512b9ce-7f5b-48eb-a79e-f3498bacf2de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687958(v=OCS.15)
ms:contentKeyID: 49886087
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Iniciar para o Serviço de Registro em Log para Capturar Logs

 

_**Tópico modificado em:** 2013-02-21_

Para capturar logs de rastreamento usando Serviço de Log Centralizado, você deve emitir um comando para fazer um registro em log em um ou mais computadores ou pools. Você também deve emitir parâmetros que definem quais computadores ou pools, qual cenário executar (por exemplo, AlwaysOn, outro cenário pré definido ou um cenário que você criou), quais componentes Lync Server (por exemplo, S4, SipStack) para rastrear

Para capturar informação certa, é necessário certificar-se de usar o cenário correto para coletar informação relevante ao problema. Em Serviço de Log Centralizado, um cenário é o conceito de habilitar o registro em log com base em um conjunto de componentes do servidor. níveis de log e sinalzadores, o que é muito mais eficiente e útil que ter que definir esses elementos por servidor. Você define e especifica um cenário para executar e o cenário é executado consistentemente em todos os servidores e pools no escopo da infraestrutura.

O cenário padrão é chamado de **AlwaysOn**. O objetivo do AlwaysOn é executar o cenários constantemente, conforme o nome do cenário implica. O cenário AlwaysOn coleta informações de nível informativo (obeserve que o nível de log informativo inclui Fatal, Erro e Aviso, além das mensagens informativas) para boa parte da maioria dos componentes de servidor comum. AlwaysOn coleta informções antes, durante e após o problema ocorrer. Isso difere drasticamente do comportamento típico das ferramentas de log anteriores, tais como OCSLogger. É possível executar OCSLogger após o problema ocorrer, tornando seus eforços para resolução de problemas mais dificil, pois os dados que você possui são reativos e não proativos. Se AlwaysOn não possui a informação que você está procurando a fim de indicar o componente do problema e um curso de ação para corrigi-lo (o que provavelmente não fornece a amplitude e profundidade dos provedores em AlwaysOn), ele indicará um nível adequado de informação para determinar o que mais dee ser feito, como criar um novo cenário, juntar outras informações, realizar uma busca diferente para coletar informações mais detalhadas, e assim por diante.

O Serviço de Log Centralizado dá duas formas de emitir comandos. Um número de tópicos são focados diretamente no uso de Windows PowerShell através de Shell de Gerenciamento do Lync Server. A habildade de usar um número de configurações e comandos complexos favorce o Windows PowerShell para o uso de Serviço de Log Centralizado . Porque Windows PowerShell através de Shell de Gerenciamento do Lync Server é quase úbico para todas as funções em Lync Server, somente os comandos Windows PowerShell são discutidos.

> [!NOTE]  
> Caso decida usar o conjunto de comandos disponível na linha de comando, é possível conseguir ajuda com o CLSController.exe ao digitar <code>ClsController.exe</code>. Por padrão, <strong>ClsController.exe</strong>é instalado no diretório C:\Arquivos de Programas\Microsoft Lync Server 2013\ClsAgent.

## Para executar Start-CsClsLogging com Windows PowerShell usando comandos básicos

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Inicie um cenário de log com Serviço de Log Centralizado digitando o seguinte:
    
        Start-CsClsLogging -Scenario <name of scenario>
    
    Por exemplo, para iniciar o cenário **AlwaysOn**, digite:
    
        Start-CsClsLogging -Scenario AlwaysOn
    
    > [!NOTE]  
    > O cenário The AlwaysOn não possui uma duração padrão. Este cenário será executado até que o pare precisamente com o cmdlet <strong>Stop-CsClsLogging</strong>. Para detalhes, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging">Stop-CsClsLogging</a>. Para todos os outros cenários, a duração padrão é 4 horas.

3.  Pressione Enter para executar o comenando.
    
    > [!NOTE]  
    > Pode levar algum tempo (30 a 60 segundos) para que os os comandos sejam executados e que recebam o status de volta dos computadores em sua implantação.    
    ![Executando Start-CsClsLogging.](images/JJ687958.c5be7413-8cef-4de7-9712-944d20cc2fa4(OCS.15).jpg "Executando Start-CsClsLogging.")

4.  Para iniciar outro cenários, use o cmdlet **Start-CsClsLogging** com o nome do cenário adicional para executar o seguinte (por exemplo, o cenário **Autenticação**):
    
        Start-CsClsLogging -Scenario Authentication
    
    > [!IMPORTANT]  
    > É possível ter um total de dois cenários sendo executados em qualquer computador a qualquer momento. Se o comando é global no escopo, todos os computadores em sua implantação executarão o cenário ou cenários. Para iniciar um terceiro cenário, você deve parar o log no computador, pool, site ou escopo global em que você queira executar o novo cenario. Caso tenho iniciado um escopo global, é possível parar o log em um ou ambos cenários em um ou mais computadores e pools. Para detalhe sobre o gerenciamento de quais cenários estão sendo executados, consulte <a href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">Usando Parar para o Serviço de Registro em Log</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging">Stop-CsClsLogging</a>.

## Executar Start-CsClsLogging com Windows PowerShell usando comandos avançados

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Parâmetros adicionais estão disponíveis para gerenciar os comandos de log. É possível usar –Duração para ajustar o tempo em que o cenário será executado. Também é possível definir –Computadores, uma lista de nomes de domínios completamente qualificados de computadores (FQDNs) separados por vírgula, ou –Pools, uma lista separada por vírgula de FQDNs para pools que você quer executar o log.
    
    Voce inicia uma sessão de log para o cenário *UserReplicator* no pool “pool01.contoso.net”. Você também define duração da sessão de log em 8 horas. Para isso, digite:
    
        Start-CsClsLogging -Scenario UserReplicator -Duration 8:00 -Pools "pool01.contoso.net"
    
    O execução com sucesso deste cenário devolve um resultado como o seguinte:
    
    ![Executando Start-CsClsLogging.](images/JJ687958.399f0c2e-c08c-40ab-b6c6-381dddc12fe9(OCS.15).jpg "Executando Start-CsClsLogging.")
    
    Observe que neste exemplo, o cenário AlwaysOn é executado e o cenário UserReplicator também está sendo executado.

## Consulte Também

#### Conceitos

[Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)

