---
title: 'Lync Server 2013: Criar ou modificar um fluxo de trabalho de grupo de busca'
TOCTitle: Criar ou modificar um fluxo de trabalho de grupo de busca
ms:assetid: dcb9effb-5d12-4dee-80fc-ab9654222d5a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205321(v=OCS.15)
ms:contentKeyID: 49308322
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um fluxo de trabalho de grupo de busca no Lync Server 2013

 

_**Tópico modificado em:** 2013-09-11_

Use um dos seguintes procedimentos para criar ou modificar um fluxo de trabalho do grupo de busca.

> [!NOTE]  
> É possível usar o Shell de Gerenciamento do Lync Server ou o Ferramenta de Configuração de Grupo de Resposta para criar e modificar fluxos de trabalho do grupo de busca. É possível acessar o Ferramenta de Configuração de Grupo de Resposta do Painel de Controle do Lync Server ou abrindo a página da Web diretamente por um navegador da Web digitando a seguinte URL: <strong>https://</strong> <em>&lt;webPoolFqdn&gt;</em> <strong>/RgsConfig</strong> .

## Para usar o Ferramenta de Configuração de Grupo de Resposta para criar ou modificar um fluxo de trabalho do grupo de busca

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Grupos de Resposta** e em **Fluxo de Trabalho** .

4.  Na página **Fluxo de Trabalho** , clique em **Criar ou editar um fluxo de trabalho** .

5.  No campo de pesquisa **Selecione um Serviço** , digite parte ou todo o nome do serviço do **ApplicationServer** que hospeda o fluxo de trabalho que você deseja alterar ou criar. Na lista de serviços resultante, clique no serviço que deseja e clique em **OK** .
    
    > [!NOTE]  
    > O Ferramenta de Configuração de Grupo de Resposta abre. Você também pode abrir o Ferramenta de Configuração de Grupo de Resposta diretamente de um navegador digitando a seguinte URL: <strong>https://</strong> <em>&lt;webPoolFqdn&gt;</em> <strong>/RgsConfig</strong> .

6.  Siga um destes procedimentos:
    
      - Em **Criar um Novo Fluxo de Trabalho** , próximo ao **Grupo de busca, clique em Criar** .
    
      - Em **Gerenciar um Fluxo de Trabalho Existente** , localize o fluxo de trabalho que você deseja alterar e, em **Ação** , clique em **Editar** .

7.  Se estiver pronto para que os usuários comecem a fazer chamadas para o fluxo de trabalho, selecione **Ativar o fluxo de trabalho** .
    
    > [!NOTE]  
    > Se você estiver criando um fluxo de trabalho gerenciado, é necessário selecionar <strong>Ativar o fluxo de trabalho</strong> . Após salvar o fluxo de trabalho gerenciado ativo, é possível modificar e desativá-lo.

8.  Para permitir que usuários federados façam chamadas para o grupo, selecione a opção **Habilitar para federação** . Você também deve ter uma política de acesso externo aplicável ao Aplicativo Grupo de Resposta configurado para federação.
    
    > [!NOTE]  
    > A política de acesso externo global é aplicada ao Aplicativo Grupo de Resposta. É possível configurar a política global para federação do grupo de resposta usando o Painel de Controle do Lync Server ou o cmdlet <strong>Set-CsExternalAccessPolicy</strong> para definir o parâmetro EnableOutsideAccess para True. Lembre-se que as configurações de política global se aplicam a todos os usuários, a não ser que eles sejam atribuídos com uma política de usuário ou de site. Portanto, antes de alterar esta configuração para grupos de resposta, certifique-se de que as configurações de federação cumpre os requisitos da sua organização. Para obter detalhes sobre como as políticas são aplicadas aos usuários, consulte <a href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Gerenciar política de acesso externo no Lync Server 2013</a>. Para obter detalhes sobre as configurações de federação, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExternalAccessPolicy">Set-CsExternalAccessPolicy</a>.    
    > [!NOTE]  
    > Usuários hospedados em Lync Online não podem encaminhar chamadas para responder a grupos de resposta hospedados em outro ambiente local. Isso se aplica tanto para ambientes híbridos quanto para casos em que o ambiente local é federado com um ambiente Lync Online .

9.  Para ocultar a identidade de operadores durante as chamadas, selecione a opção **Habilitar anonimato do operador** .
    
    > [!NOTE]  
    > Chamadas anônimas não podem ter início com sistemas de mensagens instantâneas (IM) ou vídeo, embora o operador ou chamadas possam adicionar IM e vídeo depois que a chamada estiver estabelecida. Um operador anônimo também pode colocar chamadas em espera, transferir (transferências ocultas e de consulta), estacionar e recuperar chamadas. Chamadas anônimas não oferecem suporte a conferência, compartilhamento de aplicativos, transferência de arquivos, whiteboarding e colaboração de dados e gravação de chamadas. Agentes utilizando o Plugin Lync VDI podem atender chamadas em entrada anonimamente, mas não podem realizar chamadas em saída anonimamente.

10. Sob **Insira o endereço do grupo que receberá as chamadas** , digite o endereço URI SIP primário do grupo que irá receber chamadas para o fluxo de trabalho.
    
    > [!NOTE]  
    > O URI primário para um fluxo de trabalho é como o fluxo de trabalho é identificado e referenciado. O URI SIP inserido é criado como um objeto de contato no Serviços de Domínio Active Directory. Para criar o URI, o objeto deve ser exclusivo no Active Directory.

11. Em **Nome de Exibição** , digite o nome que você deseja exibir para o fluxo de trabalho (por exemplo, Vendas do Grupo de Resposta).
    
    > [!NOTE]  
    > Não inclua os caracteres &quot;&lt;&quot; ou &quot;&gt;&quot; no nome de exibição. Não use os nomes de exibição a seguir, pois são reservados: <strong>Observador de Presença RG</strong> ou <strong>Serviço de Anúncio</strong> .

12. Sob **Número de telefone** , digite o URI de linha para o grupo de resposta (por exemplo, +14255550165).

13. Em **Número de Exibição** , digite o número conforme deseja que apareça para o grupo de resposta (por exemplo, +1 (425) 555-0165).

14. (Opcional) Em **Descrição** , digite uma descrição para o fluxo de trabalho conforme você deseja que apareça no cartão de visitas no cliente do Lync.

15. Em **Tipo de fluxo de trabalho** , selecione **Gerenciado** se este fluxo de trabalho será gerenciado por um Gerente o Grupo de Resposta. Faça o seguinte para atribuir Gerentes do Grupo de Resposta ao fluxo de trabalho:
    
    1.  Digite o URI SIP de um gerente para este fluxo de trabalho e clique em **Adicionar** .
    
    2.  Digite o URI SIP de gerentes adicionais para adicionar ao fluxo de trabalho e clique em **Adicionar** .
    
    > [!IMPORTANT]  
    > Cada usuário que é designado como um gerente de um grupo de resposta deve ser atribuído à função CsResponseGroupManager. Se os usuários não sã atribuídos com esta função, eles não podem gerenciar grupos de resposta.

16. Sob **Etapa 2 Selecione um Idioma** , clique no idioma que deseja usar para reconhecimento de fala e conversão de texto em fala.

17. Se você deseja configurar uma mensagem de boas vindas, sob **Etapa 3 Configure uma Mensagem de Boas Vindas** , selecione a opção **Reproduzir uma mensagem de boas vindas** e execute um dos seguintes procedimentos:
    
      - Para inserir uma mensagem de boas vindas como texto convertido para fala para os chamadores, clique em **Usar conversão de texto em fala** e digite a mensagem de boas vindas na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo de áudio wave (.wav) ou (.wma) do Windows Media para a mensagem de boas vindas, clique em **Selecionar uma gravação** . Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação** . Na janela do navegador, clique em **Procurar** , selecione o arquivo de áudio que deseja usar e clique em **Abrir** . Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivo com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

18. Sob **Etapa 4 Especifique seu Horário Comercial** , em **Seu fuso horário** , clique no fuso horário para o fluxo de trabalho.
    
    > [!NOTE]  
    > O fuso horário é onde os chamadores e operadores do fluxo de trabalho residem. Ele é usado para calcular os horários de abertura e encerramento. Por exemplo, se o fluxo de trabalho está configurado para usar o fuso horário da costa leste norte-americana e o fluxo de trabalho estiver agendado para abrir às 7:00 A.M e fechar às 11:00 P.M., os horários de abertura e fechamento são assumidos como sendo 7:00 horário da costa leste e 23:00 horário da costa leste, respectivamente (você deve inserir os horários na notação de 24 horas).

19. Selecione o tipo de agenda de horário comercial que deseja usar executando um dos seguintes procedimentos:
    
      - Para usar uma agenda pré-definida de horário comercial, clique em **Usar uma agenda predefinida** e selecione a agenda que deseja usar na lista suspensa.
        
        > [!NOTE]  
        > Você deve ter definido no mínimo uma agenda predefinida anteriormente para selecionar esta opção. Defina agendas predefinidas usando o cmdlet <strong>New-CSRgsHoursOfBusiness</strong>. Para detalhes, consulte <a href="lync-server-2013-optional-define-response-group-business-hours.md">(Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013</a>.        
        > [!NOTE]  
        > Ao selecionar uma agenda predefinida, <strong>Dia</strong> , <strong>Abertura</strong> e <strong>Fechamento</strong> são automaticamente preenchidos com os dias e horas em que o grupo de resposta está disponível.    
      - Para usar uma agenda personalizada que se aplique somente a este fluxo de trabalho, clique em **Usar uma agenda personalizada** .

20. Se estiver criando uma agenda personalizada para este fluxo de trabalho, clique nas opções para os dias da semana em que o grupo de resposta estará disponível.

21. Se estiver criando uma agenda personalizada, digite as horas de **Abertura** e **Fechamento** para cada dia da semana em que o grupo de resposta estará disponível.
    
    > [!NOTE]  
    > As horas de <strong>Abertura</strong> e <strong>Fechamento</strong> devem estar na notação de 24 horas. Por exemplo, se seu escritório funciona em dias úteis das 9 às 5 e fecha ao meio dia para o almoço, o horário comercial é especificado como <strong>Abertura</strong> 9:00, <strong>Fechamento</strong> 12:00, <strong>Abertura</strong> 13:00 e <strong>Fechamento</strong> 17:00.

22. Se você desejar reproduzir uma mensagem quando o escritório não estiver aberto, selecione a opção **Reproduzir uma mensagem quando o grupo de resposta estiver fora do horário comercial** e especifique a mensagem a ser reproduzida executando um dos seguintes procedimentos:
    
      - Para inserir as mensagem como um texto a ser convertido para fala para o chamador, clique em **Usar conversão de texto para fala** e digite a mensagem na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo de áudio para a mensagem, clique em **Selecionar uma gravação** . Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação** . Na nova janela do navegador, clique em **Procurar** , selecione o arquivo que deseja usar e clique em **Abrir** . Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivos de áudio com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

23. Especifique como tratar chamadas após a reprodução da mensagem (se uma mensagem estiver configurada):
    
      - Para desconectar a chamada, clique em **Desconectar Chamada** .
    
      - Para encaminhar a chamada para a caixa postal, clique em **Encaminhar para caixa postal** e digite o endereço da caixa postal. O formato para o endereço da caixa postal é *\<nomedousuário\>* @ *\<nomedodomínio\>* (por exemplo, bob@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar para URI do SIP** e digite um endereço de usuário. O formato para o endereço do usuário é *\<nomedousuário\>* @ *\<nomedodomínio\>* .
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e digite o número de telefone. O formato para o número de telefone é *\<número\>* @ *\<nomedodomínio\>* (por exemplo, +14255550121@contoso.com). O nome do domínio é usado para encaminhar o chamador ao destino correto.

24. Sob **Etapa 5 Especifique seus Feriados** , clique nas opções para um ou mais conjuntos de feriados que definem quando o grupo de resposta estará fechado para negócios.
    
    > [!NOTE]  
    > É necessário definir feriados e conjuntos de feriados antes de configurar o fluxo de trabalho. Use os cmdlets <strong>New-CsRgsHoliday</strong> e <strong>New-CsRgsHolidaySet</strong> para definir feriados e conjuntos de feriados. Para detalhes, consulte <a href="lync-server-2013-optional-define-response-group-holiday-sets.md">(Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013</a>.

25. Se você deseja reproduzir uma mensagem nos feriados, selecione a opção **Reproduzir uma mensagem durante os feriados** e especifique a mensagem a ser executada realizado um dos seguintes procedimentos:
    
      - Para inserir as mensagem como um texto a ser convertido para fala para o chamador, clique em **Usar conversão de texto para fala** e digite a mensagem na caixa de texto.
        
        > [!NOTE]  
        > Não inclua tags HTML no texto digitado. Se você incluir tags HTML, receberá uma mensagem de erro.    
      - Para usar uma gravação de arquivo de áudio para a mensagem, clique em **Selecionar uma gravação** . Se você deseja carregar um novo arquivo de áudio, clique no link **uma gravação** . Na nova janela do navegador, clique em **Procurar** , selecione o arquivo que deseja usar e clique em **Abrir** . Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem estar de acordo com determinados requisitos. Para detalhes sobre formatos de arquivos de áudio com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

26. Especifique como tratar chamadas após a reprodução da mensagem (se uma mensagem estiver configurada):
    
      - Para desconectar a chamada, clique em **Desconectar Chamada** .
    
      - Para encaminhar a chamada para a caixa postal, clique em **Encaminhar para caixa postal** e digite o endereço da caixa postal. O formato para o endereço da caixa postal é *\<nomedousuário\>* @ *\<nomedodomínio\>* (por exemplo, bob@contoso.com).
    
      - Para encaminhar a chamada para outro usuário, clique em **Encaminhar para URI do SIP** e digite um endereço de usuário. O formato para o endereço do usuário é *\<nomedousuário\>* @ *\<nomedodomínio\>* .
    
      - Para encaminhar a chamada para outro número de telefone, clique em **Encaminhar para número de telefone** e digite o número de telefone. O formato para o número de telefone é *\<número\>* @ *\<nomedodomínio\>* (por exemplo, +14255550121@contoso.com). O nome do domínio é usado para encaminhar o chamador ao destino correto.

27. Sob **Etapa 6 Configure uma Fila** , em **Selecione a fila que receberá as chamadas** , selecione a fila que você deseja que segure as chamadas até que um operador torne-se disponível.

28. Sob **Etapa 7 Configure Música de Espera** , escolha a música que deseja que os chamadores ouçam enquanto esperam que um operador, executando um dos seguintes procedimentos:
    
      - Para usar a gravação padrão de música de espera, clique em **Usar padrão** .
    
      - Para usar uma gravação de arquivo de áudio para a música de espera, clique em **Selecionar um arquivo de música** . Se você deseja carregar um novo arquivo de áudio, clique no link **um arquivo de música** . Na nova janela do navegador, clique em **Procurar** , selecione o arquivo que deseja usar e clique em **Abrir** . Clique em **Carregar** para carregar o arquivo de áudio.
        
        > [!NOTE]  
        > Todos os arquivos de áudio fornecidos pelo usuário devem atender determinados requisitos. Para detalhes sobre formatos de arquivos de áudio com suporte, consulte <a href="lync-server-2013-technical-requirements-for-response-group.md">Requisitos técnicos do Grupo de Resposta no Lync Server 2013</a>.

29. Clique em **Implantar** .

## Para usar o Windows PowerShell para criar ou modificar um fluxo de trabalho do grupo de busca

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Crie o prompt a ser reproduzido na mensagem de boas-vindas e salve-o como uma variável. Na linha de comando, execute:
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    Por exemplo:
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to Contoso. Please wait for an available agent."
    
    > [!NOTE]  
    > Para usar um arquivo de áudio no prompt, use o cmdlet <strong>Import-CsRgsAudioFile</strong>. Para obter detalhes, consulte <a href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</a>.

4.  Obtenha a identidade da fila ou pergunta onde as chamadas serão direcionadas. Na linha de comando, execute:
    
        $qid = (Get-CsRgsQueue -Name "Help Desk").Identity
    
    Para detalhes sobre como criar filas, consulte [New-CsRgsQueue](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsQueue).

5.  Defina a ação padrão a ser realizada quando um fluxo de trabalho é aberto durante o horário comercial e salve-o em uma variável. Na linha de comando, execute:
    
        $actionWM = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken> -QueueID $qid
    
    > [!NOTE]  
    > Para fluxos de trabalho do grupo de busca, a ação padrão deve direcionar a chamada para uma fila. Este parâmetro é necessário para fluxos de trabalho ativos. Não é necessário para fluxos de trabalho inativos.    
    Por exemplo:
    
        $actionWM = New-CsRgsCallAction -Prompt $promptWM -Action TransferToQueue -QueueID $qid.Identity

6.  Se você deseja definir o horário comercial e feriados, é necessário criá-los antes de criar ou modificar o fluxo de trabalho. Para obter detalhes, consulte [(Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013](lync-server-2013-optional-define-response-group-business-hours.md) e [(Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013](lync-server-2013-optional-define-response-group-holiday-sets.md).

7.  Se você deseja ter prompts para chamadas recebidas fora do horário comercial ou em feriados, use o cmdlet **New-CsRgsPrompt** para definir o prompt e use o **New-CsRgsCallAction** para definir a ação a ser realizada após o prompt. Para obter detalhes, consulte [New-CsRgsPrompt](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsPrompt) e [New-CsRgsCallAction](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsCallAction).

8.  Recuperar o nome do serviço para o Serviço Grupo de Resposta do Lync Server e atribui-lo para uma variável. No comando, execute:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;

9.  Criar ou modificar o fluxo de trabalho Para criar um fluxo de trabalho, use o **New-CsRgsWorkflow**. Para modificar um fluxo de trabalho,use o **Set-CsRgsWorkflow**. Na linha de comando, digite:
    
        $workflowHG = New-CsRgsWorkflow -Parent <service ID for the Response Group service> -Name "<hunt group name>" [-Description "<hunt group description>"] -PrimaryUri "<SIP address for the workflow>" [-LineUri "<Phone number for the workflow>"] [-DisplayNumber "<Phone number displayed in Lync>"] [-Active <$true | $false>] [-Anonymous <$true | $false>] [-DefaultAction <variable from preceding step>] [-EnabledForFederation <$true | $false>] [-Managed <$true | $false>] [-MangersByUri <SIP addresses for Response Group Managers who can manage the workflow>]
    
    Por exemplo:
    
        $workflowHG = New-CsRgsWorkflow -Parent $serviceID -Name "Human Resources" -Description "Human Resources workflow" -PrimaryUri "sip:humanresources@contoso.com" -LineUri "TEL:+14255551219" -DisplayNumber "555-1219" -Active $true -Anonymous $true -DefaultAction $actionWM -EnabledForFederation $false -Managed $true -ManagersByUri "sip:bob@contoso.com", "mindy@contoso.com"
    
    > [!IMPORTANT]  
    > Todos os usuários que são gerentes para fluxos de trabalho devem ser atribuídos à função CsResponseGroupManager.    
    > [!NOTE]  
    > Para obter detalhes sobre parâmetros opcionais adicionais, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsWorkflow">New-CsRgsWorkflow</a> ou <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsWorkflow">Set-CsRgsWorkflow</a>

## Consulte Também

#### Tarefas

[(Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013](lync-server-2013-optional-define-response-group-holiday-sets.md)  

#### Conceitos

[(Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013](lync-server-2013-optional-define-response-group-business-hours.md)  

#### Outros Recursos

[New-CsRgsWorkflow](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsWorkflow)  
[Set-CsRgsWorkflow](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsWorkflow)  
[New-CsRgsPrompt](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsPrompt)  
[New-CsRgsCallAction](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsCallAction)

