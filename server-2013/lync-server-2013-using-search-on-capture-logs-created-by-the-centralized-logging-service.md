---
title: Usando Buscar em Logs de Captura criados para o Serviço de Registro em Log
TOCTitle: Usando Buscar em Logs de Captura criados para o Serviço de Registro em Log
ms:assetid: 1b75b218-d84f-47a7-8a0a-b7e016b1cc79
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687982(v=OCS.15)
ms:contentKeyID: 49886120
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Buscar em Logs de Captura criados para o Serviço de Registro em Log

 

_**Tópico modificado em:** 2013-02-21_

O recurso de pesquisa no Serviço de Log Centralizado é útil e poderoso pelos seguintes motivos:

  - Sua pesquisa e seus resultados são executados em um único computador, em um escopo de grupo, site ou global, com base no critério que você definir.

  - Suas pesquisas podem ser iniciadas de forma ampla e reduzidas para um critério mais definido como hora, componente ou computador. Você pesquisa nos mesmos registros e não precisa executar uma sessão de registro em log novamente quando o critério de pesquisa mudar.

  - Os resultados da sua pesquisa são reunidos de todos os computadores e pools no escopo, coletados e agregados em um único arquivo de resultados que representa todos os resultados do critério de pesquisa (limitado para cenários em execução e os dados capturados pelos cenários). Você usa ferramentas familiares como o **Snooper** ou o **Bloco de notas** para ler o arquivo de resultados e rastrear mensagens pela sua implantação.

O CLSAgent em cada computador cria os logs com base no cenário ou cenários (dois cenários por computador podem estar funcionando em um determinado momento). Os logs e seu índice e arquivos de cache associados são gerenciados pelo CLSAgent. Ao definir e executar uma pesquisa, o comando de pesquisa instrui o CLSAgent sobre qual informação deve ser recuperada. O CLSAgent executa a consulta nos arquivos de log, arquivos de cache e arquivos de índice e coloca-os na ordem de tempo delta, entrada mais antiga primeiro e continuando para a última entrada mais recente. O CLSController agrega (combina) os logs e os coloca na ordem de tempo delta, entrada mais antiga primeiro e continuando para a última entrada mais recente.

Após cada pesquisa, o cmdlet **Sync-CsClsLogging** é executado e descarrega o cache usado pelas pesquisas (não deve ser confundido com os arquivos de cache mantidos pelo CLSAgent). Descarregar o cache ajuda a garantir que há um log limpo e um armazenamento de captura de arquivo de rastreamento no CLSController para a próxima operação de pesquisa.

Para obter mais benefícios do Serviço de Log Centralizado, você precisa ter um bom conhecimento de como configurar a pesquisa para devolver apenas mensagens de rastreamento do computador e registros de grupo que são relevantes para o que você está pesquisando novamente. problemas

Para executar as funções de pesquisa do Serviço de Log Centralizado usando o Shell de Gerenciamento do Lync Server, você deve ser membro dos grupos de segurança RBAC CsAdministrator ou CsServerAdministrator ou uma função RBAC personalizada que contém qualquer um destes dois grupos. Para devolver uma lista de todas as funções RBAC que este cmdlet foi atribuído (incluindo qualquer função RBAC personalizada que você criou sozinho), execute o seguinte comando no prompt do Shell de Gerenciamento do Lync Server ou Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

Por exemplo:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

O lembrete deste tópico se focaliza em como definir uma pesquisa para otimizar sua resolução de problemas.

## Para executar uma pesquisa básica usando o Serviço de Log Centralizado

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Certifique-se de ter o cenário AlwaysOn em execução na sua implantação no escopo global e digite o seguinte no prompt de comando:
    
        Search-CsClsLogging -OutputFilePath <string value of path and file to write the output file>
    
    > [!NOTE]  
    > Por padrão, o Search-CsClsLogging envia os resultados da pesquisa para o console. Se você deseja salvar os resultados da pesquisa em um arquivo, use –OutputFilePath <em>&lt;caminho do arquivo totalmente qualificado da sequência&gt;</em>. Para definir o parâmetro –OutputFilePath, ofereça um caminho e um nome de arquivo como parte do parâmetro em um formato de sequência entre aspas (por exemplo; C:\LogFiles\SearchOutput.txt). Neste exemplo, você deve garantir que o diretório C:\LogFiles exista e que você possui permissões para arquivos de Leitura e Gravação (permissão NTFS Modificar) na pasta. O resultado é anexado e não é substituído. Se você precisa separar arquivos, defina um nome de arquivo diferente para cada pesquisa.    
    Por exemplo:
    
        Search-CsClsLogging -OutputFilePath "C:\LogFiles\logfile.txt"

## Para executar uma pesquisa básica em um pool ou computador usando o Serviço de Log Centralizado

1.  Para limiar a pesquisa para um pool ou computador específico, use o parâmetro –Computers com o computador definido por um nome totalmente qualificado do computador, entre aspas e separado por vírgulas, como a seguir:
    
        Search-CsClsLogging -Computers <string value of computer names> -OutputFilePath <string value of path and file to write the output file>
    
    Por exemplo:
    
        Search-CsClsLogging -Computers "fe01.contoso.net" -OutputFilePath "C:\LogFiles\logfile.txt"

2.  Para pesquisar mais de um computador, digite vários nomes do computador entre aspas e separados por vírgulas, como o seguinte:
    
        Search-CsClsLogging -Computers "fe01.contoso.net", "fe02.contoso.net", "fe03.contoso.net" -OutputFilePath "C:\LogFiles\logfile.txt"

3.  Se você precisa pesquisar todo um pool ao invés de um único computador, altere o parâmetro –Computers para –Pools, remova o nome do computador e substitua com o pool ou pools entre aspas separados por vírgulas.
    
    Por exemplo:
    
        Search-CsClsLogging -Pools "pool01.contoso.net" -OutputFilePath "C:\Logfiles\logfile.txt"

4.  Ao usar os comandos de pesquisa, os pools podem ser qualquer pool na sua implantação, como Pools de Front-Ends, Pools de borda, Pools de Servidor de Chat Persistente ou outros que estão definidos como um pool em sua implantação.
    
    Por exemplo:
    
        Search-CsClsLogging -Pools "pool01.contoso.net", "pchatpool01.contoso.net", "intedgepool01.contoso.net" -OutputFilePath "C:\Logfiles\logfile.txt"

## Para executar uma pesquisa usando parâmetros de tempo

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Por padrão, o horário inicial para o parâmetro de tempo específico da pesquisa é 30 minutos antes da hora que você iniciar a pesquisa. Em outras palavras, se você iniciar sua pesquisa às 16:00 horas, irá pesquisar os registros dos computadores e pools que você definir de 15:30 horas as 16:00 horas. Se você precisa pesquisar 60 minutos ou 3 horas antes da hora atual, use o parâmetro –StartTime e defina a sequência de data e hora para indicar a hora que você deseja que a pesquisa inicie.
    
    Por exemplo, usando –StartTime e –EndTime para definir um intervalo de data e hora, é possível definir uma pesquisa entre 8 e 9 horas no dia 20/11/2012 em seu pool. É possível definir o caminho de resultado para gravar os resultados em um arquivo chamado c:\\logfile.txt como a seguir:
    
        Search-CsClsLogging -Pools "pool01.contoso.net" -StartTime "11/20/2012 08:00:00 AM" -EndTime "11/20/2012 09:00:00 AM" -OutputFilePath "C:\Logfiles\logfile.txt"
    
    > [!NOTE]  
    > A sequência data e hora que você especificar pode ser “data hora” ou “hora data”. O comando analisará a sequência e usará os valores adequados para data e hora.

3.  Se você deseja recuperar os logs começando às 11:00 horas em 20/11/2012, você define –StartTime. O intervalo de hora padrão para a pesquisa é de 30 minutos, a não ser que você defina um –EndTime específico. A pesquisa resultante retornará logs do computador ou pools definidos de 11:00 horas a 11:30 horas.
    
    Por exemplo:
    
        Search-CsClsLogging -Pools "pool01.contoso.net" -StartTime "11/20/2012 11:00:00 AM" -OutputFilePath "C:\Logfiles\logfile.txt"

4.  Para conduzir uma pesquisa dos logs dentro de um período de tempo específico, defina –StartTime e –EndTime. Você precisa de logs de 13:00 horas às 14:45 horas no computador edge01.contoso.net.
    
    Por exemplo:
    
        Search-CsClsLogging -Computers "edge01.contoso.net" -StartTime "11/20/2012 1:00:00 PM" -EndTime "11/20/2012 2:45:00 PM" -OutputFilePath "C:\Logfiles\logfile.txt"

## Para executar uma pesquisa avançada usando outro critério e opções correspondentes

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para executar um comando para coletar rastreamentos de componentes específicos, digite o seguinte:
    
        Search-CsClsLogging -Components <components to search on> -OutputFilePath <fully qualified path to output logs>
    
    Por exemplo:
    
        Search-CsClsLogging -Components "SIPStack","S4","UserServices" -OutputFilePath "C:\Logfiles\logfile.txt"
    
    A pesquisa resultante retorna todas as entradas de log com componentes de rastreamento para SIPStack, S4 e UserServices em todos os computadores e pools na sua implantação pelos últimos 30 minutos.

3.  Para limitar a pesquisa com os mesmos componentes para apenas o seu Pool de Front-Ends chamado pool01.contoso.net, digite:
    
        Search-CsClsLogging -Components "SIPStack","S4","UserServices" -OutputFilePath "C:\Logfiles\logfile.txt"

4.  A lógica de pesquisa padrão para comando com vários parâmetros é usar o OR lógico com cada um dos parâmetros definidos. É possível alterar este comportamento especificando o parâmetro **–MatchAll**. Para fazer isso, digite o seguinte:
    
        Search-CsClsLogging -CallId "d0af828e49fa4dcb99f5f80223a634bc" -Components "SIPStack","S4","UserServices" -MatchAll -OutputFilePath "C:\Logfiles\logfile.txt"

5.  Se seus cenários estão definidos para ser executado constantemente, como AlwaysOn, ou se definiu logs do cenário de longa execução podem sair da máquina local em um compartilhamento de arquivos. Você define o compartilhamento de arquivos usando o parâmetro CacheFileNetworkFolder usando New-CsClsConfiguration para criar uma nova configuração ou modificar uma configuração existente com Set-CsClsConfiguration. Se você não deseja que a pesquisa inclua o compartilhamento de arquivos no conjunto de logs para pesquisar, use o parâmetro SkipNetworkLogs como a seguir:
    
        Search-CsClsLogging -Components "SIPStack","S4","UserServices" -StartTime "11/1/2012 00:00:01 AM" -EndTime "11/20/2012 2:45:00 PM" -SkipNetworkLogs -OutputFilePath "C:\Logfiles\logfile.txt"

