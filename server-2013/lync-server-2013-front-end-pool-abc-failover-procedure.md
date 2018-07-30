---
title: 'Lync Server 2013: Procedimento de failover ABC do pool Front-End'
TOCTitle: Procedimento de failover ABC do pool Front-End
ms:assetid: 67763ad3-6796-45eb-a486-901f21ac1a95
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945635(v=OCS.15)
ms:contentKeyID: 52057630
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Procedimento de failover ABC do pool Front-End no Lync Server 2013

 

_**Tópico modificado em:** 2014-05-22_

Use as etapas a seguir para executar o procedimento de failover ABC. Esse procedimento contém uma descrição de alto nível de cada etapa, seguida por comandos e cmdlets a serem executados em cada etapa.

Para executar os cmdlets, abra um Shell de Gerenciamento do Lync Server usando Executar como administrador.

## Para executar um failover ABC

1.  Verifique se o pool A é o host do Servidor de Gerenciamento Central (CMS).
    
      - Execute o seguinte cmdlet:
        
            Get-CsService -CentralManagement
        
        Se o campo Identidade do CMS apontar para o nome de domínio totalmente qualificado (FQDN) do Pool A, use as etapas 2 e 3 desse procedimento para fazer failover do Servidor de Gerenciamento Central primeiro. Caso contrário, pule para a etapa 4.

2.  Faça failover do CMS do Pool B no modo de recuperação de desastres executando o seguinte cmdlet:
    
        Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Pool B BE FQDN> -BackupSqlInstanceName <Pool B BE instance name> [-BackupMirrorSqlServerFqdn <Pool B Mirror BE FQDN> -BackupMirrorSqlInstanceName <Pool B Mirror BE Instance name>] -Force -Verbose
    
    Após fazer isso, recomendamos que você mova o CMS do pool B para outro pool emparelhado existente para resiliência extra. Para obter detalhes, consulte [Move-CsManagementServer](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsManagementServer)..

3.  Se o Pool A contiver o CMS, importe a configuração do LIS a partir do banco de dados LIS do pool A para o pool B (Lis.mdf). Isso funcionará somente se você tiver feito backup dos dados do LIS regularmente. Para importar a configuração do LIS, execute os seguintes cmdlets:
    
        Import-CsLisConfiguration -FileName <String> 
        Publish-CsLisConfiguration

4.  Importe os fluxos de trabalho do serviço Grupo de resposta do Lync Server copiados em backup do pool A para o pool B.
    
    > [!NOTE]  
    > Atualmente, o cmdlet <strong>Import-CsRgsConfiguration</strong> requer que os nomes da fila e do fluxo de trabalho no pool A sejam are diferentes dos nomes da fila e do fluxo de trabalho no pool B. Se os nomes não forem diferentes, ocorrerá um erro na execução do cmdlet <strong>Import-CsRgsConfiguration</strong> e as filas e do fluxos de trabalho deverão ser renomeados no pool B antes de prosseguir com o cmdlet <strong>Import-CsRgsConfiguration</strong>.    
    Você tem duas opções para importar a configuração do Grupo de Resposta do pool A para o pool B. Qual opção você deve usar depende de se deseja sobrescrever as configurações em nível de aplicativo do pool B com as configurações em nível de aplicativo do pool A.
    
      - Se você deseja sobrescrever as configurações do Pool B, execute o cmdlet **Import-CsRgsConfiguration** com a opção **ReplaceExistingSettings** :
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - Se você não deseja sobrescrever as configurações do Pool B, use o cmdlet **Import-CsRgsConfiguration** sem a opção **ReplaceExistingSettings** .
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    

    > [!WARNING]
    > Tenha em mente que se você não quiser sobrescrever as configurações em nível de aplicativos do pool de backup (pool B) com as configurações pool primário (pool A), as configurações em nível de aplicativos do pool A serão perdidas, pois o aplicativo Grupo de Resposta pode somente armazenar um conjunto de configurações em nível de aplicativos por pool. Quando o pool C é implantado para substituir o pool A, as configurações em nível de aplicativos devem ser reconfiguradas, incluindo o arquivo de áudio de música em espera padrão.



5.  Verifique se a importação das configurações do Grupo de Resposta foi feita com sucesso executando os seguintes cmdlets para exibir os grupos de resposta importados. Observe que os grupos de resposta importados ainda são de propriedade do pool A.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"

6.  Para os intervalos de Números não atribuídos que estão usando "Comunicado" como o serviço de comunicado selecionado do pool A para o pool B. Faça isso:
    
      - Crie novamente todos os comunicados que foram implantados do pool A no pool B. Se quaisquer arquivos de áudio foram usados ao implantar os comunicados no pool A, esses arquivos precisaram criar novamente os comunicados no pool B. Para criar os comunicados novamente no pool B, use os cmdlets **New-CsAnnouncement**, com o pool B como Serviço Pai.
    
      - Redirecione todos os intervalos de Números não atribuídos que estão redirecionando um comunicado no pool A para os comunicados implantados recém-criados no pool B. Execute o seguinte cmdlet para cada intervalo de Números não atribuídos redirecionado um comunicado para do pool A:
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool B FQDN>" -AnnouncementName "<New Announcement in pool B>"
    
    > [!NOTE]  
    > Essa etapa não requer os intervalos de Números não atribuídos que usam &quot;UM do Exchange&quot; como serviço de comunicado selecionado.

7.  Faça failover do Pool A para o Pool B no modo de Recuperação de Desastres (DR), executando o seguinte cmdlet:
    
        Invoke-CsPoolFailover -PoolFqdn <Pool A FQDN> -DisasterMode

8.  Construa o pool C, mas não inicie qualquer serviço no pool C.
    
    Observe que essa etapa pode ser realizada ao mesmo tempo com as etapas 5 e 6.

9.  Force os usuários hospedados no pool A para serem movidos para o pool C executando o seguinte cmdlet:
    
        Get-csuser -Filter {RegistrarPool -eq "<Pool A FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force
    
    Neste ponto, os usuários hospedados no pool A começaram a experimentar uma interrupção do serviço. Essa interrupção continuará até a etapa 16, quando os serviços são iniciados no pool C.

10. Force o diretório de conferência do pool A para ser movido para o pool C executando o seguinte cmdlet:
    
        Move-CsConferenceDirectory -Identity <Conference Directory ID of Pool A> -TargetPool <Pool C FQDN> -Force

11. Force o Objeto de Contato do Atendedor Automático de Conferência (CAA) para ser movido do pool A para o pool C executando o seguinte cmdlet:
    
        Move-csApplicationEndpoint -Identity "<Pool A CAA Uri>" -targetApplicationPool <Pool C FQDN> -force

12. Copie o conteúdo da conferência do pool B para o pool C.

13. Exporte os dados do usuário do pool B e importe os dados do usuário para o pool C executando os seguintes cmdlets:
    
        Export-CsUserData -PoolFqdn <Pool B Fqdn> -FileName <String>
        Import-CsUserData -PoolFqdn <Pool C Fqdn> -FileName <String>

14. Restaure os dados do aplicativo Estacionamento de Chamada copiado em backup do pool A no pool C e atribua os intervalos de órbitas do Estacionamento de Chamada do pool A para o pool C.
    
      - Você pode atribuir novamente um intervalo de órbitas de Estacionamento de Chamada do pool A para o pool C por meio do Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server. Para o Shell de Gerenciamento do Lync Server, executando o seguinte cmdlet para cada intervalo de órbitas de Estacionamento de Chamada atribuído ao pool A (observe que o parâmetro Identity se refere aos Intervalo de órbitas de Estacionamento de Chamada além do pool A):
        
            Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Pool C FQDN>"
    
      - Se uma música em espera personalizada tiver sido configurada pelo Estacionamento de Chamada no pool A, restaure o arquivo da música em espera personalizada pelo Estacionamento de Chamada no pool C.
        
            Xcopy <Source> <Destination: Pool C CPS File Store Path>
        
        Por exemplo:
        
            Xcopy "Source Path" "<Pool C File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"
    
      - Finalmente, reconfigure as configurações do Estacionamento de Chamada no pool C usando o cmdlet **Set-CsCpsConfiguration**. O aplicativo Estacionamento de Chamada pode armazenar somente um conjunto de configurações e um arquivo de áudio de música em espera personalizado por pool, essas configurações não são copiadas em backup ou preservadas caso ocorra um desastre.

15. Se o pool do próximo salto do Chat Persistente estiver apontando para o pool A, faça e publique alterações na topologia, assim o servidor do próximo salto apontará para o pool C.
    
      - No Construtor de Topologias, altere o pool do Chat Persistente para apontar para o Pool C como o seu próximo salto. Para fazer isso, clique com o botão direito no pool do Chat Persistente,clique na guia **Geral** e insira o nome do Pool C em **Pool de próximo salto** .
    
      - Inicie os serviços no pool C executando o seguinte cmdlet:
        
            Start-csWindowsService
    
    Neste ponto, a interrupção do serviço termina para os usuários hospedados originalmente no pool A.

16. Exporte os fluxos de trabalho do serviço do Grupo de Resposta do Lync Server a partir do pool B que pertence ao pool A para importar para o pool C executando o seguinte cmdlet:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" 

17. Importe os fluxos de trabalho do serviço do Grupo de Resposta do Lync Server para o pool C a partir do pool B.
    
    Você tem duas opções para importar a configuração do Grupo de Resposta do pool B para o pool C. Qual opção você deve usar depende de se deseja sobrescrever as configurações em nível de aplicativo do pool C com as configurações em nível de aplicativo do pool B.
    
      - Se deseja sobrescrever as configurações em nível de aplicativo do Pool C, execute o cmdlet **Import-CsRgsConfiguration** com a opção **ReplaceExistingSettings** :
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool C FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - Se não desejar sobrescrever as configurações do Pool C, use o cmdlet **Import-CsRgsConfiguration** sem a opção **ReplaceExistingSettings** .
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    

    > [!WARNING]
    > Tenha em mente que se você não quiser sobrescrever as configurações em nível de aplicativos do Pool C com as configurações do pool de backup (pool B), as configurações em nível de aplicativos do pool B serão perdidas, pois o aplicativo Grupo de Resposta pode somente armazenar um conjunto de configurações em nível de aplicativos por pool.



18. Verifique se a importação das configurações do Grupo de Resposta foi feita com sucesso executando os seguintes cmdlets para exibir os grupos de resposta que foram importados para o Pool C.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
         Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll

19. Quando a configuração importada for verificada no pool C, remova os grupos de resposta que pertencem ao pool primário do pool B. Isso reduzirá o tempo de inatividade dos grupos de resposta.
    
    Essa etapa cria um novo arquivo com a configuração exportada e remove o arquivo do pool B.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration

20. Mova os intervalos do Número Não Atribuído do pool C que foram movidas do pool A para o pool B.
    
      - Recriar todos os comunicados no pool que foram recriados do pool A no pool B. Se quaisquer arquivos de áudio forem usados durante a implantação dos comunicados para serem movidos, será necessário usar esses arquivos para recriar os comunicados no pool C. Para recriar os comunicados no pool C, use o cmdlet **New-CsAnnouncement**, com o pool C como o Serviço Pai.
    
      - Redirecione todos os intervalos de Números não atribuídos do pool C que foram redirecionados do pool A para o pool B. Execute o seguinte cmdlet para cada intervalo de Números não atribuídos que precisam ser redirecionados:
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool C FQDN>" -AnnouncementName "<New Announcement in pool C>"
    
      - (Opcional) Remova do pool B os comunicados que foram recriados no pool C, se eles não forem mais usados no pool B. Para remover os comunicados, use o cmdlet **Remove-CsAnnouncement**.
        
        > [!NOTE]  
        > Essa etapa não requer os intervalos de Números não atribuídos que usam &quot;UM do Exchange&quot; como serviço de comunicado.

21. Limpe os dados do usuário do pool A no pool B executando o seguinte cmdlet:
    
        Remove-CsUserStoreBackupData -PoolFqdn <Pool B FQDN> -Verbose

22. Faça o seguinte no Construtor de Topologias:
    
      - Desemparelhe o pool A e o pool B. Emparelhe o pool B e o pool C. Então, remova o Pool A da topologia para publicá-la. Para fazer isso:
        
          - No Construtor de Topologias, clique com o botão direito no Pool B e clique em **Editar propriedades** .
        
          - Clique em **Resiliência** no painel esquerdo.
        
          - Na caixa abaixo **Pool de backup associado** , selecione o Pool C. Observe que a caixa de seleção do Pool de backup associado inicialmente exibirá o pool A, pois o pool B foi anteriormente associado a esse pool.
        
          - Selecione **Failover automático e failback para voz** e clique em **OK** .
            
            Ao exibir os detalhes sobre este pool, o pool associado agora aparece no painel direito em **Resiliência** .
        
          - Na árvore de console, clique com o botão direito no pool A e clique em Excluir.
        
          - Publique a topologia.

23. Execute o aplicativo de inicialização no pool C para instalar o aplicativo do serviço de backup e, então, iniciar o aplicativo do serviço de backup executando o seguinte a partir da pasta de implantação em uma máquina local no pool C:
    
        Run "%SYSTEMROOT%\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe"
        Start-CsWindowsService -name LyncBackup

24. Reinicie o aplicativo do serviço de backup no pool B executando os seguintes cmdlets:
    
        Stop-CsWindowsService -name LyncBackup
        Start-CsWindowsService -name LyncBackup

25. Se o pool C for um Pool do Standard Edition (SE) e o pool B possuir o CMS, instale o banco de dados do CMS manualmente no pool C executando o seguinte cmdlet:
    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <Pool C FQDN> -SqlInstanceName rtc

26. Execute o comando do serviço de backup para sincronizar o conteúdo de conferência antigo do pool B para o pool C que foi gerado antes de emparelhar o B e o C, e para sincronizar o novo conteúdo de conferência do pool C para o pool B que foi gerado após iniciar o pool C e antes do B e do C serem emparelhados. Para isso, execute os seguintes cmdlets:
    
        Invoke-CsBackupServiceSync -PoolFqdn <Pool C FQDN>
        Invoke-CsBackupServiceSync -PoolFqdn <Pool B FQDN>

27. Para cada Aparelho de Filial Persistente X associado ao pool A:
    
      - Desligue o SBA X executando o seguinte cmdlet:
        
            Stop-CsWindowsService
    
      - Crie um arquivo que contenha uma lista de usuários hospedados no SBA X. A lista deve ser necessária quando os usuários forem movidos de volta ao SBA X na etapa 30. Para fazer isso, execute o seguinte cmdlet:
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Export-Csv d:\sbaxusers.txt
    
      - Force os usuários hospedados no SBA X a serem movidos para o pool C executando o seguinte cmdlet:
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force -Verbose
    
      - Atualize os dados desses usuários, primeiro executando os seguintes cmdlets:
        
            Convert-csUserData -InputFile <Data file exported from PoolB> -OutputFile c:\Logs\ExportedUserData.xml -TargetVersionLync2010 
            $a=get-csuser -Filter {RegistrarPool -eq "FQDN of SBA X"} | select SipAddress
            foreach($x in $a) {$x.SipAddress.Substring(4) >> users.txt}
        
        E, então, execute este script:
        
            $users=gc c:\logs\users.txt
            foreach ($user in $users)
            {
            Update-CsUserData -FileName c:\logs\exportedUserDAta.xml -UserFilter $user - 
            }
        
        > [!NOTE]  
        > Uma interrupção do serviço ocorrerá para os usuários que estiverem hospedados nos SBAs que estiverem associados ao pool A até esses usuários serem movidos para o pool C.

28. No Construtor de Topologias , para cada SBA X anteriormente associado ao Pool A, faça o seguinte:
    
      - Altere a associação do Pool C. Para fazer isso, clique no site de filial, expanda os Aparelhos de Filial Persistente ou nó de servidores, e clique em **Aparelhos de Filial Persistente** . Selecione o **Pool de Front-End, Pool de Serviços do Usuário** com o qual o seu Aparelhos de Filial Persistente se conectará como Pool C, e clique em **Avançar** .
    
      - Publicar a topologia. Para fazer isso, na árvore de console, clique com o botão direito no novo **Aparelhos de Filial Persistente** , clique em **Topologia** e em **Publicar** .

29. Para cada SBA X agora associado ao pool C:
    
      - Inicie o SBA X executando o seguinte cmdlet no aparelho de filial persistente:
        
            Start-CsWindowsService
    
      - Mova os usuários que originalmente estavam hospedados no SBA X do pool C para o SBA X executando o seguinte cmdlet.
        
            Import-Csv d:\sbaxusers.txt | Move-CsUser -Target <SBA X FQDN> -Force

