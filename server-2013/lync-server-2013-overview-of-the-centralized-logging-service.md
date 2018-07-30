---
title: Visão Geral do Serviço de Registro em Log
TOCTitle: Visão Geral do Serviço de Registro em Log
ms:assetid: 975718a0-f3e3-404d-9453-6224e73bfdd0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688145(v=OCS.15)
ms:contentKeyID: 49886324
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão Geral do Serviço de Registro em Log

 

_**Tópico modificado em:** 2016-12-08_

O Serviço de Log Centralizado é projetado para fornecer um meio para coleta controlada de dados - com um escopo estrito ou amplo. Você pode coletar dados de todos os servidores na implantação ao mesmo tempo, definir elementos específicos para rastrear, definir sinalizadores de rastreamento e retornar resultados de pesquisa de um único computador ou em agregação de todos os dados de todos os servidores. O Serviço de Log Centralizado é executado em todos os servidores em sua implantação. A arquitetura do Serviço de Log Centralizado é composta pelos seguintes agentes e serviços.

  - *Agente de serviço de log centralizado*   O ClsAgent.exe é o executável de serviço que se comunica com o controlador e recebe os comandos que ele emite ao administrador. O agente é executado como um serviço em cada computador do Lync Server. Quando o agente recebe um comando, ele executa o comando, envia as mensagens aos componentes definidos para rastreamento e grava os logs de rastreamento no disco. Ele também lê os logs de rastreamento do seu computador e envia os dados de rastreamento de volta ao controlador ao ser solicitado. O ClsAgent espera os comandos nas seguintes portas: **TCP 50001**, **TCP 50002** e **TCP 50003**.

  - *Controlador de serviço de log centralizado*   O ClsControllerLib.dll é o mecanismo de execução de comando do Shell de Gerenciamento do Lync Server e do ClsController.exe. O CLSControllerLib.dll envia comandos Start, Stop, Flush e Search para o ClsAgent. Quando os comandos de pesquisa são enviados, os logs resultantes retornam ao ClsControllerLib.dll e são agregados. O controlador é responsável por enviar comandos ao agente, recebendo o status desses comandos e gerenciando os dados de arquivo de log de pesquisa, à medida que eles retornam de todos os agentes em qualquer computador no escopo de pesquisa, e agregando os dados do log em um conjunto de saída significativo e ordenado. As informações nos tópicos a seguir se concentram no uso do Shell de Gerenciamento do Lync Server. ClsController.exe está limitado a um subconjunto de recursos e funções que estão disponíveis no Shell de Gerenciamento do Lync Server. A ajuda do ClsController.exe está disponível na linha de comando, digitando `ClsController` no diretório padrão C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\ClsAgent

**Comunicações do ClsController com o ClsAgent**

![Relacionamento entre CLSController e CLSAgent.](images/JJ688145.68c90811-5cf9-4a84-95b7-ea9ffc61eac4(OCS.15).jpg "Relacionamento entre CLSController e CLSAgent.")

Você emite comandos usando a interface de linha de comando do Windows Server ou usando o Shell de Gerenciamento do Lync Server. Os comandos são executados no computador que você fez logon e enviados ao ClsAgent localmente, ou para outros computadores e pools em sua implantação.

O ClsAgent mantém um arquivo de índice de todos os arquivos .CACHE que ele tem na máquina local. O ClsAgent os aloca de forma que fiquem distribuídos uniformemente nos volumes definidos na opção CacheFileLocalFolders, nunca consumindo mais de 80% de cada volume (isto é, o local do cache local e a porcentagem configuráveis usando o cmdlet **Set-CsClsConfiguration**). O ClsAgent é responsável também por expirar arquivos de log de rastreamento de eventos antigos no cache (.etl) para fora da máquina local. Após duas semanas (isto é, o cronograma configurável usando o cmdlet **Set-CsClsConfiguration**, esses arquivos são copiados para um compartilhamento de arquivos e excluído do computador local. Para obter detalhes, consulte [Set-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration). Quando uma solicitação de pesquisa é recebida, os critérios de pesquisa são usados para selecionar o conjunto de arquivos .etl em cache para realizar a pesquisa baseada nos valores no índice mantido pelo agente.

> [!NOTE]  
> Arquivos que são movidos do computador local para o compartilhamento de arquivos podem ser pesquisados pelo ClsAgent. Assim que o ClsAgent move os arquivos para o compartilhamento de arquivos, a expiração e remoção de arquivos não são mantidas pelo ClsAgent. Você deve definir uma tarefa administrativa para monitorar o tamanho dos arquivos no compartilhamento de arquivos e excluí-los ou arquivá-los.

Os arquivos de log resultantes podem ser lidos e analisados usando várias ferramentas, incluindo **Snooper.exe** e qualquer ferramenta que possa ler um arquivo de texto, como **Notepad.exe**. Snooper.exe faz parte das Ferramentas de Debug do Lync Server 2013 e está disponível como um download Web.

Assim como o OCSLogger, o Serviço de Log Centralizado tem vários componentes para serem rastreados comparativamente, e fornece opções para selecionar sinalizadores, como TF\_COMPONENT e TF\_DIAG. O Serviço de Log Centralizado também retém as opções do nível de log do OCSLogger.

A vantagem mais importante do uso do Windows PowerShell, em comparação à linha de comando ClsController é que você pode configurar e definir novos cenários usando provedores selecionados que lidam com o espaço de problema, sinalizadores personalizados e níveis de log. Os cenários disponíveis no ClsController são limitados àqueles definidos pelo executável.

Nas versões anteriores, o OCSLogger.exe era fornecido para permitir que os administradores e equipe de suporte coletassem arquivos de rastreamento de computadores na implantação. O OCSLogger, apesar de todos seus pontos fortes, tinha um problema. Você podia apenas coletar logs em um computador, em um dado momento. Você podia fazer logon em vários computadores usando cópias separadas do OCSLogger, mas terminava com vários logs e sem uma maneira fácil de agregar os resultados.

Quando um usuário solicita uma pesquisa de log, o ClsController determina quais máquinas devem receber as solicitações (isto é, baseado nos cenários selecionados). Ele também determina se a pesquisa precisa ser enviada ao compartilhamento de arquivos quando os arquivos .etl salvos forem localizados. Quando os resultados da pesquisa retornam ao ClsController, o controlador funde os resultados em um único conjunto de resultados ordenado pelo horário, que é apresentado ao usuário. Os usuários podem salvar os resultados da pesquisa em sua máquina local para análises posteriores.

Ao iniciar uma sessão de log, você especifica cenários que são relativos ao problema que está tentando resolver. Você pode ter dois cenários sendo executados a qualquer momento. Um desses cenários deve ser o cenário AlwaysOn (sempre ativado). Como o nome implica, ele deve estar sempre sendo executado em sua implantação, coletando informações em todos os computadores, pools e componentes.

> [!IMPORTANT]  
> Como padrão, o cenário AlwaysOn não está em execução em sua implantação. É necessário iniciar explicitamente o cenário. Assim que for iniciado, ele continuará a ser executado até que seja interrompido explicitamente, e o estado de execução persistirá depois de reinicializações dos computadores. Para obter detalhes sobre iniciar e interromper cenário, consulte <a href="lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md">Usando Iniciar para o Serviço de Registro em Log para Capturar Logs</a> e <a href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">Usando Parar para o Serviço de Registro em Log</a>.

Quando ocorrer um problema, inicie um segundo cenário que está relacionado ao problema relatado. Reproduza o problema e interrompa o log para o segundo cenário. Inicie suas pesquisas de log relativas ao problema relatado. A coleção agregada de logs produz um arquivo de log que contém mensagens de rastreamento de todos os computadores em seu site ou escopo global de sua implantação. Se a pesquisa retornar mais dados que você possa analisar (geralmente conhecido como razão sinal-ruído, onde o ruído é muito alto), execute outra pesquisa com parâmetros mais restritos. Neste ponto, você pode começar a notar padrões que são exibidos e que podem ajudar a obter um foco mais claro do problema. Finalmente, após realizar algumas pesquisas refinadas, você poderá encontrar dados que sejam relevantes ao problema e descobrir a causa.


> [!TIP]
> Ao ser apresentado a um cenário de problema no Lync Server, comece se perguntando "o que eu já sei sobre o problema?". Se você quantificar os limites do problema, será possível eliminar uma grande parte das entidades operacionais no Lync Server.<BR>Considere um exemplo de cenário no qual você sabe que os usuários não estão recebendo resultados atualizados ao procurar por um contato. Não faz sentido procurar por problemas nos componentes de mídia, Enterprise Voice, conferência e uma série de outros componentes. Você pode não saber onde está realmente o problema: no cliente, ou é um problema no lado dos servidor? Os contatos são coletados do Active Directory pelo User Replicator e fornecido ao cliente por meio do Servidor do Catálogo de Endereços (ABServer). O ABServer obtém suas atualizações dos banco de dados RTC (onde o User Replicator os grava) e os coleta nos arquivos do catálogo de endereços, como padrão, às 1:30 AM. Os clientes do Lync Server recuperam o novo catálogo de endereços em uma programação aleatória. Como você sabe como o processo funciona, é possível reduzir sua procura pela causa potencial a um problema relacionado à coleta de dados do Active Directory pelo User Replicator, o ABServer não estar recuperando e criando os arquivos de catálogo de endereços, ou os clientes não estarem baixando os arquivos de catálogo de endereços.


