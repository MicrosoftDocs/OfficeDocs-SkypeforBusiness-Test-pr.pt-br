---
title: Configurando provedores do serviço de registro em log centralizado
TOCTitle: Configurando provedores do serviço de registro em log centralizado
ms:assetid: 6a197ecf-b56b-45e0-8e7c-f532ec5164ff
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688082(v=OCS.15)
ms:contentKeyID: 49886250
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando provedores do serviço de registro em log centralizado

 

_**Tópico modificado em:** 2014-03-19_

Os conceitos e a configuração de *provedores* no Serviço de Log Centralizado estão entre os mais importantes que devem ser compreendidos. Os *provedores* são mapeados diretamente para componentes de função de servidor do Lync Server no modelo de rastreamento do Lync Server. O provedor define os componentes de um Lync Server 2013 que serão rastreados, os tipos de mensagens (por exemplo, fatal, erro ou aviso) a serem coletados e os sinalizadores (por exemplo, TF\_Connection ou TF\_Diag). Os provedores são os componentes rastreáveis de cada função de servidor do Lync Server. Usando provedores, você define o nível e o tipo de rastreamento nos componentes (por exemplo, S4, SIPStack, mensagens instantâneas e presença). O provedor definido é usado em um cenário para agrupar todos os provedores de um determinado conjunto lógico que tratam de um problema específico.

Para executar as funções do Serviço de Log Centralizado usando o Shell de Gerenciamento do Lync Server, você precisa ser um membro dos grupos de segurança do RBAC (controle de acesso baseado em função) CsAdministrator ou CsServerAdministrator ou de uma função do RBAC personalizada que contenha um desses dois grupos. Para retornar uma lista de todas as funções do RBAC às quais este cmdlet foi atribuído (incluindo funções do RBAC personalizadas que você mesmo criou), execute o seguinte comando a partir do Shell de Gerenciamento do Lync Server ou do prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

Por exemplo:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

O restante deste tópico concentra-se em como definir provedores, modificar um provedor e no que uma definição de provedor contém para otimizar a solução de problemas. Há duas maneiras de emitir comandos do Serviço de Log Centralizado. Você pode usar o CLSController.exe, que está localizado por padrão no diretório C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent, ou pode usar o Shell de Gerenciamento do Lync Server para emitir comandos do Windows PowerShell. A distinção importante é que, quando você usa o CLSController.exe na linha de comando, há uma seleção finita de cenários disponíveis em que os provedores já são definidos e não podem ser alterados, mas é possível definir o nível de log. Usando o Windows PowerShell, você pode definir novos provedores para uso em suas sessões de registro em log e ter total controle sobre sua criação, o que coletam e em qual nível coletam os dados.

> [!IMPORTANT]  
> Como mencionado, os provedores são muito sofisticados. No entanto, os cenários são ainda mais sofisticados, pois incorporam todas as informações necessárias para definir e executar o rastreamento nos componentes que os provedores representam. Como os cenários são um conjunto de provedores, é possível fazer uma comparação livre com a execução de um arquivo de lote que contém centenas de comandos para coletar muitas informações e a emissão de centenas de comandos, um de cada vez, na linha de comando.<br />Em vez de exigir que você se aprofunde nos provedores, o Serviço de Log Centralizado fornece diversos cenários que já são definidos para você. Os cenários fornecidos cobrem a maioria dos possíveis problemas que você poderá encontrar. Raramente, você talvez precise criar e definir provedores e atribuí-los a cenários. Recomendamos que você se familiarize com cada um dos cenários fornecidos antes de investigar a necessidade de criar novos provedores e cenários. Embora este artigo traga informações sobre a criação de provedores para você se familiarizar com a maneira como os cenários usam os elementos de provedor para coletar informações de rastreamento, por enquanto, não serão fornecidos detalhes sobre os provedores em si.

Introduzidos em [Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md), os principais elementos da definição de um provedor para uso em um cenário são:

  - **Provedores**   Se você já conhece o OCSLogger, os provedores são os componentes que você escolhe para informar ao OCSLogger do que o mecanismo de rastreamento deverá coletar logs. Os provedores são os mesmos componentes e, em muitos casos, têm o mesmo nome que os componentes do OCSLogger. Se você não está familiarizado com o OCSLogger, os provedores são componentes específicos de função de servidor dos quais o Serviço de Log Centralizado pode coletar logs. No caso do Serviço de Log Centralizado, o CLSAgent é a parte arquitetural do Serviço de Log Centralizado que realiza o rastreamento dos componentes definidos na configuração dos provedores.

  - **Níveis de registro**   O OCSLogger fornecia a opção de escolher diversos níveis de detalhamento dos dados coletados. Esse recurso é uma parte integral do Serviço de Log Centralizado e dos cenários e é definido pelo parâmetro **Type**. As seguintes opções estão disponíveis:
    
      - **All**   Coleta mensagens de rastreamento do tipo fatal, erro, aviso e informações no log do provedor definido.
    
      - **Fatal**   Coleta somente as mensagens de rastreamento que indicam uma falha do provedor definido.
    
      - **Error**   Coleta somente as mensagens de rastreamento que indicam um erro do provedor definido, bem como mensagens fatais.
    
      - **Warning**   Coleta somente as mensagens de rastreamento que indicam um aviso do provedor definido, bem como mensagens de erro e fatais.
    
      - **Info**   Coleta somente as mensagens de rastreamento que indicam uma mensagem informativa do provedor definido, bem como mensagens fatais, de erro e aviso.
    
      - **Verbose**   Coleta todas as mensagens de rastreamento do tipo fatal, erro, aviso e informações do provedor definido.

  - **Sinalizadores**   O OCSLogger fornecia a opção de escolher sinalizadores para cada provedor que definiam qual tipo de informação era possível recuperar dos arquivos de rastreamento. Você pode escolher os seguintes sinalizadores, com base no provedor:
    
      - **TF\_Connection**   Fornece entradas de log relacionadas à conexão. Esses logs incluem informações sobre as conexões estabelecidas com e a partir de um componente específico. Isso também pode incluir informações significativas no nível da rede (ou seja, para componentes sem o conceito de uma conexão).
    
      - **TF\_Security**   Fornece todos os eventos/entradas de log relacionados à segurança. Por exemplo, para SipStack, são eventos de segurança como falha na validação do domínio e falhas de autenticação/autorização do cliente.
    
      - **TF\_Diag**   Fornece eventos de diagnóstico que você pode usar para diagnosticar ou solucionar problemas com o componente. Por exemplo, para SipStack, são falhas de certificado e avisos/erros de DNS.
    
      - **TF\_Protocol**   Fornecem mensagens de protocolo como mensagens SIP e CCCP.
    
      - **TF\_Component**   Permite o registro em log dos componentes especificados como parte dos provedores.
    
      - **All**   Define todos os sinalizadores disponíveis para o provedor.

## Para exibir informações sobre os provedores de cenário do Serviço de Log Centralizado existentes

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para exibir a configuração dos provedores existentes, digite o seguinte:
    
        Get-CsClsScenario -Identity <scope and scenario name>
    
    Por exemplo, para exibir informações sobre o participante de conferência global, digite:
    
        Get-CsClsScenario -Identity "global/CAA"
    
    O comando exibe uma lista dos provedores com os sinalizadores, as configurações e os componentes associados. Se as informações exibidas não forem suficientes ou a lista for muito longa para o formato de lista padrão do Windows PowerShell, você poderá exibir informações adicionais definindo um método de saída diferente. Para isso, digite:
    
        Get-CsClsScenario -Identity "global/CAA" | Select-Object -ExpandProperty Provider
    
    A saída deste comando exibe cada provedor em um formato de cinco linhas com o nome do provedor, o tipo de log, o nível de log, os sinalizadores, o GUID e a função, cada um em uma linha separada.

## Para definir um novo provedor de cenário do Serviço de Log Centralizado

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Um provedor de cenário consiste em um componente a ser rastreado, sinalizadores a serem usados e um nível de detalhamento a ser coletado. Para isso, digite:
    
        $<variableName> = New-CsClsProvider -Name <provider component> -Type <log type> -Level <log level detail type> -Flags <provider trace log flags>
    
    Por exemplo, uma definição de provedor de rastreamento que define o que será coletado e em qual nível de detalhamento do provedor Lyss seria semelhante ao seguinte:
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Info" -Flags "All"

–Level coleta mensagens fatais, de erro, aviso e informações. Os sinalizadores usados são todos aqueles definidos para o provedor Lyss e incluem TF\_Connection, TF\_Diag e TF\_Protocol.

Depois que a variável $LyssProvider for definida, você poderá usá-la com o cmdlet **New-CsClsScenario** para coletar rastreamentos do provedor Lyss. Para concluir a criação e a atribuição do provedor a um novo cenário, digite:

    New-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

Em que $LyssProvider é a variável que contém o cenário definido criado com **New-CsClsProvider**.

## Para alterar um provedor de cenário do Serviço de Log Centralizado existente

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para atualizar ou alterar a configuração de um provedor existente, digite:
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "TF_Connection, TF_Diag"
    
    Em seguida, você atualiza o cenário para atribuir o provedor digitando o seguinte:
    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

O resultado final do comando é que cenário site:Redmond/RedmondLyssInfo terá atualizado os sinalizadores e o nível do provedor atribuído a ele. Você pode exibir o novo cenário usando Get-CsClsScenario. Para obter detalhes, consulte [Get-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsScenario).


> [!WARNING]
> <STRONG>New-ClsCsProvider</STRONG> não faz uma verificação para determinar se os sinalizadores são válidos. Certifique-se de que os sinalizadores (por exemplo, TF_DIAG ou TF_CONNECTION) estejam grafados corretamente. Se os sinalizadores não estiverem grafados corretamente, o provedor não poderá retornar as informações de log esperadas.



Se você desejar adicionar mais provedores a esse cenário, digite o seguinte:

    Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Add=$ABSProvider, $CASProvider, S4Provider}

Em que cada provedor definido com a diretiva Add já foi definido com o uso do processo **New-CsClsProvider**.

## Para remover um provedor de cenário

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Os cmdlets fornecidos permitem que você atualize os provedores existentes e crie novos provedores. Para remover um provedor, você precisa usar a diretiva Replace do parâmetro Provider para **Set-CsClsScenario**. A única maneira de remover completamente um provedor é substituí-lo por um provedor redefinido com o mesmo nome e usar a diretiva Update. Por exemplo, nosso provedor LyssProvider está definido com o tipo de log WPP, o nível definido para Debug e os sinalizadores definidos como TF\_CONNECTION e TF\_DIAG. Você precisa alterar os sinalizadores para "All". Para alterar o provedor, digite o seguinte:
    
```
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "All"
```
```    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Replace=$LyssProvider}
```

3.  Se você desejar remover completamente um cenário e os provedores associados a ele, digite o seguinte:
    
        Remove-CsClsScenario -Identity <scope and name of scenario>
    
    Por exemplo:
    
        Remove-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo"
    

    > [!WARNING]
    > O cmdlet <STRONG>Remove-CsClsScenario</STRONG> não solicita sua confirmação. O cenário será excluído junto com os provedores atribuídos a ele. Você pode recriar o cenário executando novamente os comandos usados para criá-lo inicialmente. Não há um procedimento para recuperar cenários ou provedores removidos.



Quando você remove um cenário usando o cmdlet **Remove-CsClsScenario**, ele é completamente removido do escopo. Para usar os cenários que você criou e os provedores que faziam parte dele, crie novos provedores e atribua-os a um novo cenário.

## Consulte Também

#### Outros Recursos

[Get-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsScenario)  
[New-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsScenario)  
[Remove-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsScenario)  
[Set-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsScenario)  
[New-CsClsProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsProvider)

