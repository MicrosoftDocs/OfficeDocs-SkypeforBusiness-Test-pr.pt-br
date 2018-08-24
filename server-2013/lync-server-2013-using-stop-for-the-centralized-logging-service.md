---
title: Usando Parar para o Serviço de Registro em Log
TOCTitle: Usando Parar para o Serviço de Registro em Log
ms:assetid: 09ac093e-8f30-4874-84b4-12548ac8c898
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687964(v=OCS.15)
ms:contentKeyID: 49886093
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Parar para o Serviço de Registro em Log

 

_**Tópico modificado em:** 2012-11-01_

É possível parar uma sessão de registro em log em execução no momento com o cmdlet Stop-CsClsLogging. Geralmente, não há muitas situações nas quais é necessário parar uma sessão de registro em log. Por exemplo, é possível pesquisar logs e alterar as configurações sem antes precisar parar o registro em log. Se você tiver dois cenários em execução, por exemplo AlwaysOn e UserReplicator, e for necessário coletar informações relacionadas à Autenticação, será necessário parar um dos outros cenários (em um escopo global, site, pool ou computador) antes de poder iniciar a execução do cenário de Autenticação. Para obter detalhes, consulte [Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging).

> [!NOTE]  
> Ao determinar quais cenários podem ser executados em uma determinada implantação, pool ou computador, é necessário se lembrar de que você está limitado à execução de dois cenários <strong>por computador</strong>. Se você estiver registrando em log uma atividade em um pool, trate um pool como uma entidade única. Na maioria dos casos, não faria sentido executar cenários diferentes em cada computador em um pool. Não faz sentido analisar o problema sobre o qual você está coletando dados e pensar sobre qual cenário faz mais sentido em um determinado computador na implantação geral. Por exemplo, se você considerar o cenário UserReplicator, haverá pouco valor na execução do UserReplicator em um Servidor de Borda ou Pool de borda.<br />Depois de entender o problema e o escopo do impacto, faça escolhas cuidadosas sobre quais cenários executar em quais computadores e pools. Embora o cenário AlwaysOn faça sentido para um aplicativo de escopo amplo, pois coleta informações sobre uma ampla variedade de provedores, cenários específicos têm valor de aplicativo apenas em computadores ou pools específicos. Além disso, tome cuidado ao iniciar aleatoriamente uma sessão de registro em log sem antes entender o valor de um determinado cenário. Se você usar o cenário errado ou se usar um cenário apropriado para a tarefa e aplicar o cenário ao escopo errado (seja global, site, pool ou computador), poderá receber dados questionáveis e não muito úteis—como se não tivesse executado o cenário.

Para controlar as funções do Serviço de Log Centralizado usando o Shell de Gerenciamento do Lync Server, é necessário ser membro dos grupos de segurança RBAC (controle de acesso baseado em função) CsAdministrator ou CsServerAdministrator, ou de uma função RBAC personalizada que contém um desses dois grupos. Para retornar uma lista de todas as funções RBAC aos quais esse cmdlet foi atribuído (incluindo quaisquer funções RBAC personalizadas criadas por você), execute o seguinte comando a partir do prompt Shell de Gerenciamento do Lync Server ou Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

Por exemplo:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

## Para interromper uma sessão do Serviço de Log Centralizado em execução no momento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Consulte o Serviço de Log Centralizado para descobrir quais cenários estão atualmente em execução digitando o seguinte:
    
        Show-CsClsLogging
    
    ![Console do Windows PowerShell após a chamada a Show-CsCl](images/JJ687964.eb190c32-529c-4277-a731-52c47d22d8fa(OCS.15).jpg "Console do Windows PowerShell após a chamada a Show-CsCl")
    
    O resultado de Show-CsClsLogging é um resumo dos cenários em execução e em qual escopo eles estão em execução. Para obter detalhes, consulte [Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging).

3.  Para interromper uma sessão de registro em log atualmente em execução com um cenário específico, digite:
    
        Stop-CsClsLogging -Scenario <scenario name> -Computers <comma separated list of fully qualified computer names> -Pools <comma separated list of fully qualified pool names>
    
    Por exemplo:
    
        Stop-CsClsLogging -Scenario UserReplicator -Pools pool01.contoso.net
    
    Esse comando interromperá o registro em log com o cenário UserReplicatior em pool01.contoso.net.
    
    > [!NOTE]  
    > Os logs criados durante a sessão de registro em log usando o cenário UserReplicator não são excluídos. O registro em log ainda está disponível para execução de pesquisas usando o comando Search-CsClsLogging. Para obter detalhes, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Search-CsClsLogging">Search-CsClsLogging</a>.

Agindo como o comando acompanhante para Start-CsClsLogging, o cmdlet Stop-CsClsLogging encerra a sessão de registro em log, definida pelos cenários, e retém os logs criados pela sessão de registro em log. É possível executar dois cenários em um determinado computador a qualquer momento. O método de parar um cenário para coletar informações usando outro cenário é uma tarefa comum que pode ser executada durante grande parte das soluções de problemas de carga de trabalho.

## Consulte Também

#### Tarefas

[Usando Iniciar para o Serviço de Registro em Log para Capturar Logs](lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md)  

#### Conceitos

[Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### Outros Recursos

[Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging)  
[Start-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Start-CsClsLogging)  
[Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging)

