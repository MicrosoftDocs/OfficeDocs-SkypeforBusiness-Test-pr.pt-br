---
title: 'Lync Server 2013: Criar ou modificar uma fila'
TOCTitle: Criar ou modificar uma fila
ms:assetid: b9d6366a-839f-4651-a01d-9254546cadeb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205207(v=OCS.15)
ms:contentKeyID: 49307924
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma fila no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

Use um dos seguintes procedimentos para criar ou modificar uma fila.

## Usar o Painel de Controle do Lync Server para criar ou modificar uma fila

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.
    
    > [!NOTE]  
    > Se você for um dos Gerentes de grupo de resposta delegados para um fluxo de trabalho gerenciado, é possível criar ou modificar filas de grupo de resposta e atribuí-las aos fluxos de trabalho gerenciados.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Grupos de Resposta** e clique em **Fila**.

4.  Na página **Fila**, siga um destes procedimentos:
    
      - Para criar uma nova fila, clique em **Nova**. Em **Selecionar um serviço**, digite uma parte ou o nome inteiro do serviço do **ApplicationServer** onde deseja adicionar a fila no campo de pesquisa. Na lista resultante de serviços, clique no serviço que você deseja e clique em **OK**.
    
      - Para modificar uma fila existente, digite uma parte ou o nome inteiro da fila no campo de pesquisa. Na lista resultante de filas, clique na fila que você deseja, em **Editar** e em **Mostrar detalhes**.

5.  Em **Nome**, digite um nome identificador para a fila.

6.  Em **Descrição**, digite uma descrição para a fila.

7.  Em **Grupos**, especifique os grupos que você deseja atribuir à fila. Siga um destes procedimentos:
    
      - Para adicionar um grupo à fila, clique em **Selecionar**. No campo de pesquisa **Selecionar grupos**, digite o parte ou o nome inteiro do grupo de agentes que você deseja atribuir à fila, clique no grupo de agentes desejado e em **OK**.
    
      - Para remover um grupo da fila, na lista de grupos de agentes, clique no grupo que você deseja remover e em **Remover**.
    
      - Para alterar a ordem em que os agentes são pesquisados, na lista de grupos de agentes, clique em um grupo e na seta para cima ou para baixo.
        
        > [!NOTE]  
        > Quando o servidor pesquisa por um agente disponível para a fila, ele usa a ordem do grupo. Ou seja, o primeiro grupo da lista é pesquisado primeiro, seguido pelo segundo e assim sucessivamente.

8.  Para especificar um período máximo de tempo para um chamador aguardar em espera antes que um agente responda à chamada, marque a caixa de seleção **Habilitar o tempo limite da fila** e, em seguida, faça o seguinte:
    
    1.  Em **Período de tempo limite (segundos)**, especifique o número máximo de segundos que um chamador aguarda antes de um agente responder à chamada.
    
    2.  Em **Ação de Chamada**, selecione a ação que ocorre quando o tempo limite de uma chamada se esgota da seguinte maneira:
    
    <!-- end list -->
    
      - Para desconectar a chamada após o tempo limite, clique em **Desconectar**.
    
      - Para encaminhar a chamada para o correio de voz, clique em **Encaminhar para caixa postal** e no campo **Endereço SIP**, digite um endereço de caixa postal no formato sip: *\<username\>* @ *\<domainname\>* (por exemplo, sip:bob@contoso.com).
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e no campo **Endereço SIP**, digite o número de telefone no formato sip: *\<number\>* @ *\<domainname\>* (por exemplo, sip:+14255550121@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar endereço SIP** e no campo **Endereço SIP**, digite o URI para o usuário no formato sip: *\<username\>* @ *\<domainname\>* .
    
      - Para encaminhar a chamada para outra fila de espera, clique em **Encaminhar para outra fila** e, em seguida, procure na fila a ser usada.

9.  Para especificar um número máximo de chamadas que a fila de espera poderá conter, marque a caixa de seleção **Habilitar o estouro da fila** e faça o seguinte:
    
    1.  Em **Número máximo de chamadas**, selecione o número máximo de chamadas que a fila de espera conterá.
    
    2.  Em **Encaminhar a chamada**, selecione qual chamada será encaminhada quando a fila estiver cheia: **Chamada Mais Recente** ou **Chamada Mais Antiga**.
    
    3.  Em **Ação de chamada**, selecione a ação que ocorre quando o limite de excedente é atingido da seguinte forma:
    
    <!-- end list -->
    
      - Para desconectar a chamada após o tempo limite, clique em **Desconectar**.
    
      - Para encaminhar a chamada para o correio de voz, clique em **Encaminhar para caixa postal** e no campo **Endereço SIP**, digite um endereço de caixa postal no formato sip: *\<username\>* @ *\<domainname\>* (por exemplo, sip:bob@contoso.com).
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e no campo **Endereço SIP**, digite o número de telefone no formato sip: *\<number\>* @ *\<domainname\>* (por exemplo, sip:+14255550121@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar endereço SIP** e no campo **Endereço SIP**, digite o URI para o usuário no formato sip: *\<username\>* @ *\<domainname\>* .
    
      - Para encaminhar a chamada para outra fila de espera, clique em **Encaminhar para outra fila** e, em seguida, procure na fila a ser usada.

10. Clique em **Confirmar**.

## Usar o Windows PowerShell para criar ou modificar uma fila

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.
    
    > [!NOTE]  
    > Se você for um dos Gerentes do grupo de resposta designado para um fluxo de trabalho gerenciado, será possível criar grupos de agentes e filas, bem como atribuir grupos de agentes a filas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Crie o prompt para que seja reproduzido quando o limite de tempo da fila é atingido e salve-o em um variável. Na linha de comando, execute:
    
        $promptTO = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    Por exemplo:
    
        "All agents are currently busy. Please call back later."
    
    > [!NOTE]  
    > Para usar um arquivo de áudio no prompt, use o cmdlet <strong>Import-CsRgsAudioFile</strong>. Para obter detalhes, consulte <a href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</a>.

4.  Defina a ação que será executada quando o limite de tempo da fila for atingido e salve-o em um variável. Na linha de comando, execute:
    
        $actionTO = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    
    > [!NOTE]  
    > Para obter detalhes sobre ações possíveis e sua sintaxe, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsCallAction">New-CsRgsCallAction</a>.    
    Por exemplo:
    
        $action = New-CsRgsCallAction -Prompt $promptTO -Action Terminate

5.  Crie o prompt que será reproduzido quando o limite de excedente da fila for atingido e salve-o em uma variável. Na linha de comando, execute:
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    Por exemplo:
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "Too many calls are waiting. Please call back later."
    
    > [!NOTE]  
    > Para usar um arquivo de áudio no prompt, use o cmdlet <strong>Import-CsRgsAudioFile</strong>. Para obter detalhes, consulte <a href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</a>.

6.  Defina a ação que será executada quando o limite de excedente da fila for atingido e salve-o em uma variável. Na linha de comando, execute:
    
        $actionOV = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    
    > [!NOTE]  
    > Para obter detalhes sobre ações possíveis e sua sintaxe, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsCallAction">New-CsRgsCallAction</a>.    
    Por exemplo:
    
        $action = New-CsRgsCallAction -Prompt $promptOV -Action Terminate

7.  Recupere o nome do serviço do Grupo de Resposta e o atribua a uma variável. Na linha de comando, execute:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -Like "*RGS*"}).ServiceId;

8.  Obtenha a identidade do grupo de agente que será atribuído à fila. Na linha de comando, execute:
    
        $agid = (Get-CsRgsAgentGroup -Name "Help Desk").Identity;
    
    > [!NOTE]  
    > Para obter detalhes sobre como criar o grupo de agentes, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsAgentGroup">New-CsRgsAgentGroup</a>

9.  Crie a fila. Na linha de comando, execute:
    
        $q = New-CsRgsQueue -Parent <saved service ID from previous step> -Name "<name of queue>" [-Description "<description for queue>"] [-TimeoutThreshold <# seconds before call times out>] [-TimeoutAction <saved timeout action>] [-OverflowThreshold <# calls queue can hold>] [-OverflowCandidate <call to be acted on when overflow threshold met>] [-OverflowAction <saved overflow action>] [-AgentGroupIDList(<agent group identity>)];
    
    Por exemplo:
    
        $q = New-CsRgsQueue -Parent $serviceId -Name "Help Desk" -Description "Contoso Help Desk" -TimeoutThreshold 300 -TimeoutAction $actionTO -OverflowThreshold 10 -OverflowCandidate NewestCall -OverflowAction $actionOV -AgentGroupIDList($agid.Identity;

10. Confirme se a fila foi criada. Execute:
    
        Get-CsRgsQueue -Name "Help Desk"

## Consulte Também

#### Outros Recursos

[New-CsRgsQueue](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsQueue)  
[Set-CsRgsQueue](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsQueue)  
[New-CsRgsPrompt](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsPrompt)  
[New-CsRgsCallAction](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsCallAction)  
[Get-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsQueue)  
[Import-CsRgsAudioFile](https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile)  
[Remove-CsRgsQueue](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsRgsQueue)

