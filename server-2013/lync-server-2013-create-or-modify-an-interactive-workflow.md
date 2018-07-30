---
title: 'Lync Server 2013: Criar ou modificar um fluxo de trabalho interativo'
TOCTitle: Criar ou modificar um fluxo de trabalho interativo
ms:assetid: bc7bb1bc-bf6a-4636-ae93-c56fa22613fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205213(v=OCS.15)
ms:contentKeyID: 49307933
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um fluxo de trabalho interativo no Lync Server 2013

 

_**Tópico modificado em:** 2013-09-11_

Use um dos seguintes procedimentos para criar ou modificar um fluxo de trabalho interativo.

> [!NOTE]  
> Você pode usar o Shell de Gerenciamento do Lync Server ou o Ferramenta de Configuração de Grupo de Resposta para criar e modificar fluxos de trabalho interativos. É possível acessar o Ferramenta de Configuração de Grupo de Resposta do Painel de Controle do Lync Server ou abrindo a página da Web diretamente de um navegador digitando o seguinte URL: <strong>https://</strong> <em>&lt;webPoolFqdn&gt;</em> <strong>/RgsConfig</strong>.

## Usar Ferramenta de Configuração de Grupo de Resposta para criar ou modificar um fluxo de trabalho interativo

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Grupos de Resposta** e em **Fluxo de Trabalho**.

4.  Na página **Fluxo de Trabalho**, clique em **Criar ou editar um fluxo de trabalho**.

5.  No campo de pesquisa **Selecionar um serviço**, digite parte ou o nome inteiro do serviço **ApplicationServer** que hospeda o fluxo de trabalho que deseja criar ou modificar. Na lista resultante de serviços, clique no serviço que você deseja e clique em **OK**.
    
    > [!NOTE]  
    > O Ferramenta de Configuração de Grupo de Resposta abre. Você também pode abrir o Ferramenta de Configuração de Grupo de Resposta diretamente de um navegador digitando a seguinte URL: <strong>https://</strong> <em>&lt;webPoolFqdn&gt;</em> <strong>/RgsConfig</strong>.

6.  Siga um destes procedimentos:
    
      - Em **Criar um Novo Fluxo de Trabalho**, ao lado de **Interativo**, clique em **Criar**.
    
      - Em **Gerenciar um Fluxo de Trabalho Existente**, localize o fluxo de trabalho que você deseja alterar e, em **Ação**, clique em **Editar**.

7.  Se ainda não estiver tudo pronto para os usuários começarem a chamar o fluxo de trabalho, desmarque a caixa de seleção **Ativar o fluxo de trabalho**.
    
    > [!NOTE]  
    > Se você estiver criando um fluxo de trabalho gerenciado, é necessário selecionar <strong>Ativar o fluxo de trabalho</strong>. Após salvar o fluxo de trabalho gerenciado ativo, é possível modificar e desativá-lo.

8.  Para permitir que usuários federados façam chamadas para o grupo, selecione a opção **Habilitar para federação**. Você também deve ter uma política de acesso externo aplicável ao Aplicativo Grupo de Resposta configurado para federação.
    
    > [!NOTE]  
    > A política de acesso externo global se aplica ao Aplicativo Grupo de Resposta. Você pode configurar a política global para a federação do grupo de resposta usando o Painel de Controle do Lync Server ou usando o cmdlet <strong>Set-CsExternalAccessPolicy</strong> para definir o parâmetro EnableOutsideAccess como True. Lembre-se de que as configurações de política global se aplicam a todos os usuários a não ser que sejam atribuídos a um site ou uma política de usuário. Portanto, antes de alterar essa configuração para grupos de resposta, verifique se a configuração de federação atende aos requisitos da sua organização. Para obter detalhes sobre como as políticas se aplicam aos usuários, consulte <a href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Gerenciar política de acesso externo no Lync Server 2013</a>. Para obter detalhes sobre a configuração da federação, consulte <strong>Set-CsExternalAccessPolicy</strong> na documentação do Shell de Gerenciamento do Lync Server.    
    > [!NOTE]  
    > Usuários hospedados em Lync Online não podem encaminhar chamadas para responder a grupos de resposta hospedados em outro ambiente local. Isso se aplica tanto para ambientes híbridos quanto para casos em que o ambiente local é federado com um ambiente Lync Online .

9.  Para ocultar a identidade de operadores durante as chamadas, selecione a opção **Habilitar anonimato do operador**.
    
    > [!NOTE]  
    > Chamadas anônimas não podem ter início com sistemas de mensagens instantâneas (IM) ou vídeo, embora o operador ou chamadas possam adicionar IM e vídeo depois que a chamada estiver estabelecida. Um operador anônimo também pode colocar chamadas em espera, transferir (transferências ocultas e de consulta), estacionar e recuperar chamadas. Chamadas anônimas não oferecem suporte a conferência, compartilhamento de aplicativos, transferência de arquivos, whiteboarding e colaboração de dados e gravação de chamadas. Agentes utilizando o Plugin Lync VDI podem atender chamadas em entrada anonimamente, mas não podem realizar chamadas em saída anonimamente.

10. Sob **Insira o endereço do grupo que receberá as chamadas**, digite o endereço URI SIP primário do grupo que irá receber chamadas para o fluxo de trabalho.

11. Em **Nome de exibição**, digite o nome que deseja exibir no fluxo de trabalho (por exemplo, Serviço de resposta IVR de vendas).
    
    > [!NOTE]  
    > Não inclua os caracteres &quot;&lt;&quot; ou &quot;&gt;&quot; no nome de exibição. Não use os nomes de exibição a seguir, pois são reservados: RGS Presence Watcher ou Announcement Service.

12. Em **Número de telefone**, digite o URI de linha para o grupo de resposta (por exemplo, +14255550165).

13. Em **Número de Exibição**, digite o número conforme deseja que apareça para o grupo de resposta (por exemplo, +1 (425) 555-0165).

14. (Opcional) Em **Descrição**, digite uma descrição do fluxo de trabalho que deseja no cartão de contato no cliente do Lync.

15. Em **Tipo de fluxo de trabalho**, selecione **Gerenciado** se este fluxo de trabalho será gerenciado por um Gerente o Grupo de Resposta. Faça o seguinte para atribuir Gerentes do Grupo de Resposta ao fluxo de trabalho:
    
    1.  Digite o URI SIP de um gerente deste fluxo de trabalho e clique em **Adicionar**..
    
    2.  Digite o URI SIP de gerentes adicionais para adicionar ao fluxo de trabalho e clique em **Adicionar**..
    
    > [!IMPORTANT]  
    > Cada usuário que é designado como um gerente de um grupo de resposta deve ser atribuído à função CsResponseGroupManager. Se os usuários não sã atribuídos com esta função, eles não podem gerenciar grupos de resposta.

16. Sob **Etapa 2 Selecione um Idioma**, clique no idioma a ser usado para o reconhecimento de fala e conversão de texto em fala.

17. Se você deseja configurar uma mensagem de boas vindas, sob **Etapa 3 Configure uma Mensagem de Boas Vindas**, selecione a opção **Reproduzir uma mensagem de boas vindas** e execute um dos seguintes procedimentos:
    
      - Para inserir uma mensagem de boas vindas como texto convertido para fala para os chamadores, clique em **Usar conversão de texto em fala** e digite a mensagem de boas vindas na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo Wave ou Windows Media Audio para a mensagem de boas vindas, clique em **Selecione uma gravação**. Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação**. Na janela do navegador, clique em **Procurar**, selecione o arquivo de áudio que deseja usar e clique em **Abrir**. Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivo com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

18. Sob **Etapa 4 Especifique seus Horários Comerciais**, na caixa **Seu fuso horário**, clique no fuso horário do fluxo de trabalho.
    
    > [!NOTE]  
    > O fuso horário é onde os chamadores e operadores do fluxo de trabalho residem. Ele é usado para calcular os horários de abertura e encerramento. Por exemplo, se o fluxo de trabalho está configurado para usar o fuso horário da costa leste norte-americana e o fluxo de trabalho estiver agendado para abrir às 7:00 A.M e fechar às 11:00 P.M., os horários de abertura e fechamento são assumidos como sendo 7:00 horário da costa leste e 11:00:00 horário da costa leste, respectivamente (você deve inserir os horários na notação de 24 horas).

19. Selecione o tipo de agenda de horário comercial que deseja usar executando um dos seguintes procedimentos:
    
      - Para usar uma agenda pré-definida de horário comercial, clique em **Usar uma agenda predefinida** e selecione a agenda que deseja usar na lista suspensa.
        
        > [!NOTE]  
        > Você deve ter definido no mínimo uma agenda predefinida anteriormente para selecionar esta opção. É possível definir agendamentos de predefinições usando o cmdlet <strong>New-CSRgsHoursOfBusiness</strong> . Para obter mais detalhes, consulte <a href="lync-server-2013-optional-define-response-group-business-hours.md">(Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013</a>. Ao selecionar uma agenda predefinida, <strong>Dia</strong>, <strong>Abertura</strong> e <strong>Fechamento</strong> são automaticamente preenchidos com os dias e horas em que o grupo de resposta está disponível.    
      - Para usar uma agenda personalizada que se aplique somente a este fluxo de trabalho, clique em **Usar uma agenda personalizada**.

20. Se estiver criando uma agenda personalizada para este fluxo de trabalho, clique nas opções para os dias da semana em que o grupo de resposta estará disponível.

21. Se estiver criando uma agenda personalizada, digite as horas de **Abertura** e **Fechamento** em que o grupo de resposta estará disponível.
    
    > [!NOTE]  
    > As horas de <strong>Abertura</strong> e <strong>Fechamento</strong> devem estar na notação de 24 horas. Por exemplo, se seu escritório funciona em dias úteis das 9 às 5 e fecha ao meio dia para o almoço, o horário comercial é especificado como <strong>Abertura</strong> 9:00, <strong>Fechamento</strong> 12:00, <strong>Abertura</strong> 13:00 e <strong>Fechamento</strong> 17:00.

22. Se você desejar reproduzir uma mensagem quando o escritório não estiver aberto, selecione a opção **Reproduzir uma mensagem quando o grupo de resposta estiver fora do horário comercial** e especifique a mensagem a ser reproduzida executando um dos seguintes procedimentos:
    
      - Para inserir as mensagem como um texto a ser convertido para fala para o chamador, clique em **Usar conversão de texto para fala** e digite a mensagem na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo de áudio para a mensagem, clique em **Selecionar uma gravação**. Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação**. Na nova janela do navegador, clique em **Procurar**, selecione o arquivo que deseja usar e clique em **Abrir**. Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivo com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

23. Especifique como tratar chamadas após a reprodução da mensagem (se uma mensagem estiver configurada):
    
      - Para desconectar a chamada, clique em **Desconectar Chamada**.
    
      - Para encaminhar a chamada para a caixa postal, clique em **Encaminhar para caixa postal** e digite o endereço da caixa postal. O formato para o endereço da caixa postal é *\<nomedousuário\>* @ *\<nomedodomínio\>* (por exemplo, bob@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar para URI do SIP** e digite um endereço de usuário. O formato para o endereço do usuário é *\<nomedousuário\>* @ *\<nomedodomínio\>* .
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e digite o número de telefone. O formato para o número de telefone é *\<número\>* @ *\<nomedodomínio\>* (por exemplo, +14255550121@contoso.com). O nome do domínio é usado para encaminhar o chamador ao destino correto.

24. Sob **Etapa 5 Especifique seus Feriados**, clique nas opções para um ou mais conjuntos de feriados que definem quando o grupo de resposta estará fechado para negócios.
    
    > [!NOTE]  
    > É necessário definir feriados e conjuntos de feriados antes de configurar o fluxo de trabalho. Use os cmdlets <strong>New-CsRgsHoliday</strong> e <strong>New-CsRgsHolidaySet</strong> para definir feriados e conjuntos de feriados. Para detalhes, consulte <a href="lync-server-2013-optional-define-response-group-holiday-sets.md">(Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013</a>.

25. Se você deseja reproduzir uma mensagem nos feriados, selecione a opção **Reproduzir uma mensagem durante os feriados** e especifique a mensagem a ser executada realizado um dos seguintes procedimentos:
    
      - Para inserir as mensagem como um texto a ser convertido para fala para o chamador, clique em **Usar conversão de texto para fala** e digite a mensagem na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo de áudio para a mensagem, clique em **Selecionar uma gravação**. Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação**. Na nova janela do navegador, clique em **Procurar**, selecione o arquivo que deseja usar e clique em **Abrir**. Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivos de áudio com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

26. Especifique como tratar chamadas após a reprodução da mensagem (se uma mensagem estiver configurada):
    
      - Para desconectar a chamada, clique em **Desconectar Chamada**.
    
      - Para encaminhar a chamada para a caixa postal, clique em **Encaminhar para caixa postal** e digite o endereço da caixa postal. O formato para o endereço da caixa postal é *\<nomedousuário\>* @ *\<nomedodomínio\>* (por exemplo, bob@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar para URI do SIP** e digite um endereço de usuário. O formato para o endereço do usuário é *\<nomedousuário\>* @ *\<nomedodomínio\>* .
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e digite o número de telefone. O formato para o número de telefone é *\<número\>* @ *\<nomedodomínio\>* (por exemplo, +14255550121@contoso.com). O nome do domínio é usado para encaminhar o chamador ao destino correto.

27. Sob **Etapa 6 Configure a Música de Espera**, escolha o que deseja que os chamadores ouçam enquanto esperam por um operador, executando um dos seguintes procedimentos:
    
      - Para usar a gravação padrão de música em espera, clique em **Usar padrão**.
    
      - Para usar uma gravação de arquivo de áudio como música de espera, clique em **Selecionar um arquivo de música**. Se você deseja carregar um novo arquivo de áudio, clique no link **um arquivo de música**. Na nova janela do navegador, clique em **Procurar**, selecione o arquivo que deseja usar e clique em **Abrir**. Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivo com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

28. Sob **Etapa 7 Configure a Resposta Interativa de Voz**, sob o cabeçalho **O usuário ouvirá o seguinte texto ou mensagem gravada**, especifique a pergunta a ser feita aos chamadores da seguinte forma:
    
      - Para digitar uma pergunta em formato de texto, clique em **Usar conversão de texto em fala** e digite a pergunta na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.        
        > [!NOTE]  
        > O símbolo &quot;#&quot; é traduzido pelo mecanismo de conversão de texto em fala como a palavra &quot;número&quot;. Se for necessário fazer referência à tecla #, use o nome da tecla no prompt, em vez do símbolo. Por exemplo, &quot;Para falar com vendas, pressione a tecla de cerquilha&quot;.    
      - Para usar um arquivo de áudio pré-gravado que contenha a pergunta, clique em **Selecionar uma gravação** e clique no link **uma gravação** para carregar o arquivo. Na nova janela do navegador, clique em **Procurar**, selecione o arquivo de áudio e clique em **Abrir**. Clique em **Carregar** para carregar o arquivo e, opcionalmente, você pode digitar a pergunta na caixa de texto (o que habilita a pergunta e a resposta do chamador a serem encaminhadas ao operador que atenderá).
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivo com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

29. Em **Resposta 1**, especifique a primeira resposta possível para a pergunta executando um dos seguintes procedimentos:
    
    > [!IMPORTANT]  
    > Não use aspas (&quot;) em qualquer resposta de voz. Aspas podem provocar falhas no IVR.    
    > [!NOTE]  
    > Você pode optar por permitir que os chamadores respondam usando a fala, entradas do teclado alfanumérico ou ambos.    
      - Se desejar permitir que o chamador responda usando a fala, insira a resposta em **Insira uma resposta de voz**.
    
      - Se você desejar permitir que o chamador responda pressionando uma tecla no teclado, em **Dígito**, clique no dígito do teclado.

30. Especifique se o chamador será encaminhado para uma fila ou se será feita outra pergunta, da seguinte maneira:
    
      - Para rotear o chamador para uma fila, clique em **Enviar para uma fila** e, em **Selecione uma fila**, clique na fila que deseja usar.
    
      - Para fazer outra pergunta, clique em **Fazer outra pergunta**, clique em **Use conversão de texto em fala** e digite a pergunta ou clique em **Selecione uma gravação**. Use os agrupamentos de resposta nesta seção para especificar até quatro possíveis respostas para a pergunta adicional e a fila a ser usada para cada resposta. Para especificar uma terceira ou quarta resposta possível, clique na opção **Resposta 3** ou **Resposta 4**.

31. Especifique até três mais respostas possíveis para a pergunta original, repetindo as etapas 28 e 29 para especificar as possíveis respostas e a ação para cada resposta. Para especificar uma terceira ou quarta resposta possível, clique na caixa de seleção **Resposta 3** ou **Resposta 4**.

32. Clique em **Implantar**.

## Usar Windows PowerShell para criar ou modificar um fluxo de trabalho interativo

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Recupere o nome do serviço do Grupo de Resposta e o atribua a uma variável. Na linha de comando, execute:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;

4.  Um fluxo de trabalho interativo requer duas ou mais filas e dois ou mais grupos de agentes. Primeiro, crie os grupos de agentes. Execute:
    
        $AGSupport = New-CsRgsAgentGroup -Parent $serviceId -Name "Technical Support" [-AgentAlertTime "20"] [-ParticipationPolicy "Informal"] [-RoutingMethod LongestIdle] [-AgentsByUri("sip:agent1@contoso.com", "sip:agent2@contoso.com")]
        $AGSales = New-CsRgsAgentGroup -Parent $serviceId -Name "Sales Team" [-AgentAlertTime "20"] [-ParticipationPolicy "Informal"] [-RoutingMethod LongestIdle] [-AgentsByUri("sip:bob@contoso.com", "sip:alice@contoso.com")]

5.  Crie as filas. Execute:
    
        $QSupport = New-CsRgsQueue -Parent $ServiceId -Name "Contoso Support" -AgentGroupIDList($AG-Support.Identity)
        $QSales = New-CsRgsQueue -Parent $ServiceId -Name "Contoso Sales" -AgentGroupIDList($AG-Sales.Identity)

6.  Crie o primeiro prompt de grupo de resposta. Execute:
    
        $SupportPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Please be patient while we connect you with Contoso Technical Support."

7.  Em seguida, crie a ação que será executada depois do prompt. Execute:
    
        $SupportAction = New-CsRgsCallAction -Prompt $SupportPrompt -Action TransferToQueue -QueueID $QSupport.Identity

8.  Crie a primeira resposta do grupo de resposta. Execute:
    
        $SupportAnswer = New-CsRgsAnswer -Action $SupportAction [-DtmfResponse 1]

9.  Agora crie o segundo prompt, a ação da chamada e a resposta. Primeiro crie o prompt. Execute:
    
        $SalesPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we connect you with Contoso Sales."

10. Crie a segunda ação de chamada. Execute:
    
        $SalesAction = New-CsRgsCallAction -Prompt $SalesPrompt -Action TransferToQueue -QueueID $QSales.Identity

11. Crie a segunda resposta do grupo de resposta. Execute:
    
        $SalesAnswer = New-CsRgsAnswer -Action $SalesAction [-DtmfResponse 2]

12. Crie o prompt do nível superior. Execute:
    
        $TopLevelPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Thank you for calling Contoso. For Technical Support, press 1. For a Sales Representative, press 2."

13. Crie a pergunta do nível superior. Execute:
    
        $TopLevelQuestion = New-CsRgsQuestion -Prompt $TopLevelPrompt [-AnswerList ($SupportAnswer, $SalesAnswer)]

14. Agora crie o fluxo de trabalho. Execute:
    
        $IVRAction = New-CsRgsCallAction -Action TransferToQuestion [-Question $Question]
        $IVRWorkflow = New-CsRgsWorkflow -Parent $ServiceId -Name "Contoso Helpdesk" [-Description "The Contoso Helpdesk line."] -PrimaryUri "sip:helpdesk@contoso.com" [-LineUri tel:+14255554321] [-DisplayNumber "+1 (425) 555-4321"] [-Active $true] [-Anonymous $true] [-DefaultAction $IVRAction] [-Managed $true] [-ManagersByURI ("sip:mindy@contoso.com", "sip:bob@contoso.com")]
    
    > [!NOTE]  
    > Todos os usuários que foram designados como gerentes de um grupo de resposta devem ter uma função CsResponseGroupManager. Se os usuário não têm essa função, não será possível gerenciar grupos de resposta.
