---
title: 'Lync Server 2013: Procedimento de recuperação de desastre do grupo de resposta'
TOCTitle: Procedimento de recuperação de desastre do grupo de resposta
ms:assetid: b49577b7-0ca3-4f20-b614-f3a2a0046b58
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205186(v=OCS.15)
ms:contentKeyID: 49307848
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Procedimento de recuperação de desastre do grupo de resposta no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Durante a fase de failover ou de recuperação de desastres, o grupo de resposta reside em vários pools: no pool principal (que está indisponível) e no de backup. Os grupos de resposta em ambos os pools têm o mesmo nome e proprietário (o pool principal), mas têm pais diferentes. Durante esse tempo, os cmdlets do Grupo de Resposta funcionam de forma diferente. Be sure to use parameters as specified in the following procedure. Certifique-se de usar parâmetros como especificado no seguinte procedimento. Para obter detalhes sobre como os cmdlets funcionam durante a fase de failover, consulte o artigo do blog NextHop "Lync Server 2013: Grupos de resposta de recuperação durante a recuperação de desastres" em [http://go.microsoft.com/fwlink/p/?LinkId=263957](http://go.microsoft.com/fwlink/p/?linkid=263957). Este artigo do blog também se aplica à versão lançada do Lync Server 2013.

Use as etapas no seguinte procedimento para preparar e executar a recuperação de desastres do Serviço Grupo de Resposta do Lync Server.

## Execução de failover e failback do grupo de resposta

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute backups de rotina. Na linha de comando, digite:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>"
    
    Por exemplo:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimary.zip"

3.  Durante uma falha, depois do failover do pool de backup, importe os grupos de resposta para o pool de backup. Na linha de comando, digite:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<backup pool FQDN>" -FileName "<backup path and file name>"
    
    Se deseja substituir as configurações de nível do aplicativo no pool de backup pelas configurações do pool principal, inclua o parâmetro –ReplaceExistingSettings. Por exemplo:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:backup.contoso.com" -FileName "C:\RgsExportPrimary.zip" -ReplaceExistingSettings
    

    > [!WARNING]
    > Se não substituir as configurações no pool de backup e não for possível recuperar o pool principal, então as configurações do pool principal serão perdidas. Para obter detalhes, consulte <A href="lync-server-2013-planning-for-response-group-disaster-recovery.md">Planejamento para recuperação de desastre de grupos de resposta no Lync Server 2013</A>.



4.  Verifique se a importação ocorreu exibindo os grupos de resposta importados. Os grupos de resposta importados ainda são de propriedade do pool principal. Faça o seguinte:
    
      - Visualize todos os fluxos de trabalho no pool de backup que são de propriedade do pool principal e verifique se todos os fluxos de trabalho do pool principal estão incluídos. Na linha de comando, digite:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        Por exemplo:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com"
    
      - Visualize todas as filas no pool de backup que são de propriedade do pool principal e verifique se todas as filas do pool principal foram incluídas. Na linha de comando, digite:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        Por exemplo:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Visualize todos os grupos de agentes no pool de backup que são de propriedade do pool principal e verifique se todos os grupos de agentes do pool principal foram incluídos. Na linha de comando, digite:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        Por exemplo:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Visualize todos os horários comerciais no pool de backup que são de propriedade do pool principal e verifique se todas as horas comerciais do pool principal foram incluídas. Na linha de comando, digite:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        Por exemplo:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Visualize todos os conjuntos de feriados no pool de backup que são de propriedade do pool principal e verifique se todos os conjuntos de feriados do pool principal estão incluídos. Na linha de comando, digite:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        Por exemplo:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
    Como alternativa, você pode exibir todos os grupos de resposta no pool de backup, incluindo os de propriedade do pool principal e os do pool de backup usando o parâmetro –ShowAll em vez de –Owner. Por exemplo:
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -ShowAll
    
    > [!IMPORTANT]  
    > Você deve usar o parâmetro –ShowAll ou –Owner. Se não usar nenhum deles, os grupos de resposta importados para o pool de backup não serão listados nos resultados retornados pelos cmdlets.

5.  Verifique se a importação teve êxito fazendo uma chamada para um grupo de resposta importado e verificando se a chamada foi manipulada corretamente.

6.  Solicite que agentes membros de grupos de agentes formais se conectem a seus grupos de agentes no pool de backup.

7.  Gerencie e modifique os grupos de resposta importados normalmente.
    
    > [!IMPORTANT]  
    > Enquanto os grupos de respostas estão no pool de backup, é necessário usar o Shell de Gerenciamento do Lync Server para gerenciá-los Não é possível usar o Painel de Controle do Lync Server para gerenciar os grupos de resposta importados para o pool de backup.

8.  Depois que o pool principal é restaurado e o failback for concluído, exporte os grupos de resposta de pool principal que foram importados para o pool de backup. Na linha de comando, digite:
    
        Export-CsRgsConfiguration -Source ApplicationServer:<backup pool FQDN> -Owner ApplicationServer:<primary pool FQDN> -FileName "<backup path and file name>"

9.  Importe os grupos de resposta para o pool principal. Na linha de comando, digite:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>"
    
    Por exemplo:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:primary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip"
    
    > [!NOTE]  
    > Se reconstruir um pool durante a recuperação, com o mesmo nome de domínio qualificado (FQDN) ou um diferente, será necessário usar o parâmetro –OverwriteOwner. Como regra, você sempre pode usar o parâmetro –OverwriteOwner ao importar grupos de resposta para o pool primário.    
    Se você implantou um novo pool (como um FQDN igual ou diferente) para substituir o pool principal e deseja usar as configurações de nível de aplicativo do pool de backup para o novo pool, inclua o parâmetro –ReplaceExistingSettings. Na linha de comando, digite:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<new primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>" -ReplaceExistingSettings
    
    Por exemplo:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:newprimary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip" -ReplaceExistingSettings
    
    > [!IMPORTANT]  
    > Se não deseja substituir as configurações de nível de aplicativo e o arquivo de música de espera padrão do novo pool pelas configurações do pool de backup, então o novo pool usará as configurações de aplicativo padrão.

10. Verifique se a importação para o pool principal teve êxito exibindo a configuração do grupo de resposta importado. Faça o seguinte:
    
      - Visualize todos os fluxos de trabalho no pool principal e verifique se todos os fluxos de trabalho importados foram incluídos. Na linha de comando, digite:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        Por exemplo:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer: primary.contoso.com" -ShowAll
    
      - Visualize todas as filas no pool principal e verifique se todas as filas importadas foram incluídas. Na linha de comando, digite:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        Por exemplo:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Visualize todos os grupos de agentes no pool principal e verifique se todos os grupos de agentes importados foram incluídos. Na linha de comando, digite:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer: <primary pool FQDN>" -ShowAll
        
        Por exemplo:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Visualize todas as horas comerciais no pool principal e verifique se todas as horas comerciais importadas foram incluídas. Na linha de comando, digite:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        Por exemplo:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Visualize todos os conjuntos de feriados no pool principal e verifique se todos os conjuntos de feriados importados foram incluídos. Na linha de comando, digite:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        Por exemplo:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll

11. Verifique se a importação teve êxito fazendo uma chamada para um grupo de resposta importado e verificando se a chamada foi manipulada corretamente.

12. Como opção, remova os grupos de resposta do pool principal do pool de backup. Na linha de comando, digite:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>" -RemoveExportedConfiguration
    
    Por exemplo:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration
    
    > [!NOTE]  
    > Esta etapa crie um novo arquivo com a configuração exportada e o remove do pool de backup.
